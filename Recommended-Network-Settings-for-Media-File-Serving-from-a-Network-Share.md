# Assumptions
The following recommendations assume:

* that you are using SPMC 17 or later and
* that your media files are stored on a central server like a Linux-based NAS (including SAMBA 4) or Windows-based PC (preferably running Windows 10).


# Background
SPMC 17 for Android introduces support for SMBv2 and SMBv3 files sharing protocols. 

SMBv1 is decades old, slow, complex, and has security holes. It should be disabled on your server, if possible.

SMBv2 (introduced ten years ago with Vista and Server 2008) is a complete rewrite that simplifies the protocol and is better suited, performance-wise to video file serving (including large reads and pipelining). SMB 2.1 supports large MTU.

SMBv3 adds more performance improvements and end-to-end encryption. Samba4 and Windows 10 both support SMBv3. SMBv3 speed is comparable to or better than NFS. And, SMB supports user-based authentication, which should always be enabled for security reasons.


# Configuration for a Synology NAS running DSM 6.1 (or later)
Synology DSM 6.1 is running samba 4.4.13. 

Under advanced SMB settings:
* Maximum SMB protocol = SMB3
* Minimum SMB protocol = SMB2 (which results is a range of SMB2, SMB2 and large MTU, SMB3)
* Transport encryption mode = auto
* Enable opportunistic locking
* Enable SMB2 lease
* Enable DirSort VFS module
* Enable wildcard search cache
* Enable SMB durable handles

Under Advanced (SSDP):

* Enable Windows network discovery

Create a username and password specifically for SPMC on your NAS. **Do not reuse your administrator or another user account**. Make sure that it is given read-only permissions for the shared folders where your media is stored. 

In SPMC, define your media sources including the folders, username and password for your NAS.

For more Synology NAS configuration recommendations, [please read here](https://www.synology.com/en-us/knowledgebase/DSM/help/DSM/AdminCenter/file_winmacnfs_win).


# Configuration for a Windows 10 PC

* Create a username and password specifically for SPMC on your Windows PC (limited user account). **Do not reuse your administrator or another user account**. For instructions on creating Windows 10 limited User accounts, [please read here](https://www.laptopmag.com/articles/limited-user-accounts-windows-10).
* Make sure Homegroup is disabled.
* Ensure your Network Location = Private Network.
* Check your Advanced Sharing Settings. Ensure "Turn on Password Protected Sharing" is on.
* Check your share to ensure that the SPMC user account has read-only permissions for the shared folders where your media is stored.
* In SPMC, define your media sources including the folders, username and password for your NAS.


# Notes
There is no way to browse for SMB servers when SMB3 is activated, only with SMB1. When using SMB2/3, you have to enter the server address.


# Additional Reading Resources
For SMB3 v NFS4 performance, particularly reading large files, [please read here (starting pg 28)](http://2016.texaslinuxfest.org/sites/default/files/slides/Texas-Linux-Fest-2016-Future-of-NAS-draft5.pdf).


