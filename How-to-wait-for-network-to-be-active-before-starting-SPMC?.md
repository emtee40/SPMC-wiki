SPMC supports a backdoor to wait for network before starting.

To do so, create a file name **xbmc_env.properties** (if not existing) in the **root of your external storage** (normally, "/sdcard").
Add:
```
xbmc.waitnetwork=yes
```
