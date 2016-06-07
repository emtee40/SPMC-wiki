# Overview
The following sample advancedsettings.xml showcases a number of advanced SPMC capabilities. 

**You should only use the settings appropriate for your needs. All of these settings are optional!**

Sample settings include:

* hiding the splash screen
* disabling the double back on home to minimize
* using UHD (4K) resolution jacket art (thumbnails) and wallpaper (only valuable if also running GUI in 4K resolution)
* auto-removing a video from "in progress" after it's 90% complete
* hiding references to DVDs
* enabling high quality scalers for higher quality video output
* using regular expressions to hide certain files (e.g. NAS indexing files) from SPMC
* using advanced networking settings for a larger local buffer
* using multi-room video playback (including SQL settings and resume points)
* tweaking certain UX settings such as "all items" and "empty series"
* automatically cleaning the library after every library update
* silently ignoring scanner errors


# SPMC Settings
Create a text file called _advancedsettings.xml_ and place it in your _userdata_ folder.

Replace the _host_, _user_ and _pass_ field sample information below with your personal configuration.

```

<advancedsettings>
	<splash>no</splash>
    <disableminimize>true</disableminimize>
    <fanartres>2160</fanartres>
	<imageres>2160</imageres>
	<playcountminimumpercent>90</playcountminimumpercent>
	<nodvdrom>true</nodvdrom>
	<video>
	    <enablehighqualityhwscalers>true</enablehighqualityhwscalers>
		<excludefromscan> <!-- Excludes Synology index files from scan  -->
			<regexp>@eaDir</regexp>
			<regexp>@EADIR</regexp>
		</excludefromscan>
		<excludefromlisting> <!-- Excludes Synology index files from listing  -->
			<regexp>@eaDir</regexp>
			<regexp>@EADIR</regexp>
		</excludefromlisting>
	</video>
	<audio>
		<excludefromscan> <!-- Excludes Synology index files from scan  -->
			<regexp>@eaDir</regexp>
			<regexp>@EADIR</regexp>
		</excludefromscan>
		<excludefromlisting> <!-- Excludes Synology index files from listing  -->
			<regexp>@eaDir</regexp>
			<regexp>@EADIR</regexp>
		</excludefromlisting>
	</audio>
	<network>
   		<buffermode>1</buffermode> <!-- Buffer all filesystems (including local)  -->
   		<cachemembuffersize>209715200</cachemembuffersize> --> <!-- 200MB buffer  -->
	    <readbufferfactor>20</readbufferfactor>
	</network>
    <videodatabase>
        <type>mysql</type>
        <host>xxxx</host>
        <port>3306</port>
        <user>yyyy</user>
        <pass>zzzz</pass>
    </videodatabase> 
    <musicdatabase>
        <type>mysql</type>
        <host>xxxx</host>
        <port>3306</port>
        <user>yyyy</user>
        <pass>zzzz</pass>
    </musicdatabase>
	<videolibrary>
		<importwatchedstate>true</importwatchedstate>
		<importresumepoint>true</importresumepoint>
  		<cleanonupdate>true</cleanonupdate> <!-- Also clean library during library update -->
		<hideallitems>true</hideallitems> <!-- removes the "*All" items from the video library -->
   		<hideemptyseries>true</hideemptyseries>  <!-- hide empty series in the video library -->
	</videolibrary>
	<videoscanner>
   		<ignoreerrors>true</ignoreerrors> <!-- Silently ignore errors while scanning videos. -->
	</videoscanner>
</advancedsettings>
```

