SPMC supports a backdoor to specify the location of your SPMC/XBMC data.

To do so, create a file name **spmc_env.properties** in the **root of your external storage** (normally, "/sdcard").
Its content is simply:
```
xbmc.data=<path to the xbmc data root>
```
e.g. xbmc.data=/storage/sdcard0/external_sdcard/xbmc_data

Inside this, a directory ".spmc" will be created which contain the well-known xbmc/kodi structure ("addons", "userdata", ...).  
Currently, the specified path must be an android one, i.e. no "smb://" or "nfs://", but you can specify any directory mounted on the android FS, including samba or NFS ones.

Note that the standard Kodi **xbmc_env.properties** is also supported.
If spmc_env.properties is not found, SPMC will look for xbmc_env.properties as a fallback.