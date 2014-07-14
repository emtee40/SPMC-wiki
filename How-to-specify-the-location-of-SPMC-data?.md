SPMC supports a backdoor to specify the location of your SPMC/XBMC data.

To do so, create a file name **xbmc_env.properties** in the **root of your external storage** (normally, "/sdcard").
Its content is simply:
```
xbmc.data=<path to the xbmc data root>
```
e.g. xbmc.data=/storage/sdcard0/external_sdcard/xbmc_data

Inside this, a directory ".xbmc" will be created which contain the well-known xbmc structure ("addons", "userdata", ...)