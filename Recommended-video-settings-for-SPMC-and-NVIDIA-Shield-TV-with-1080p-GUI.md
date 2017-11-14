**Updated as of Shield Experience 6.1 and SPMC 17**

# Overview
SPMC supports rendering of both the graphical user interface and video in up to 4K (2160p) resolution if you have a high-end Android TV settop box like the NVIDIA Shield TV and a UHD (4K) TV. If you have a UHD TV and you watch 2160p (4K) content (e.g. HDR content in SPMC, 4K in YouTube app, or 4K in the Netflix app), then you should use [these instructions instead](https://github.com/koying/SPMC/wiki/Recommended-video-settings-for-SPMC%2C-NVIDIA-Shield-TV-and-UHD-%284K%29-TVs-with-4K-GUI).

However, if you only have a Full HD (1080p) TV or if you have a UHD TV but only watch 1080p content in all of your apps on your Shield, then you should use the settings below. If you have a UHD TV, this will have the added advantage of using your TV's upscalers, which may be better than SPMC's.


# UHD TV Settings
Because your content is limited to 1080p, your TV should be configured with limited range of RGB (16-235). You should be able to use both HDMI 1.4 and HDMI 2.0 ports though users have reported a few issues due to HDMI 1.4 devices.


# Android TV Settings
Confirm that your Shield TV is configured to limit the video output resolution to 1080p:
```
Settings > Display & Sound > Resolution > 1080p 59.940Hz
```


# SPMC Settings
Enable 'expert' in the settings menu. Then, make the following changes:

## Videos > Playback
* adjust display refresh rate = **on start / stop**
* pause during refresh change = **3.0 seconds**
* sync playback to display = **off**

## Videos > Acceleration
* allow hardware acceleration - Mediacodec (Surface) = **on**
* allow hardware acceleration - Mediacodec = **on**
* accelerate MPEG2 = **HD and up**
* accelerate MPEG4 = **HD and up**
* accelerate h264 = **HD and up**
* accelerate hevc = **HD and up**

## System > Video Output
* set GUI resolution limit = **1080**
* vertical blank sync = **always enabled**

## OSD Video Settings
While playing a video, go to the OSD > Video Settings
* deinterlace video = **auto**
* deinterlace method (SD/software) = **yadif (2x)**
* deinterlace method (HD/hardware accelerated) = **bob inverted**

Be sure to set these as the **default for all media**! Certain options, such as yadif, will not be visible unless you are watching a video using software decoding.

## advancedsettings.xml
Finally, add the following lines to your advancedsettings.xml. The fanart and imageres elements are optional but enable higher quality jacket art and wallpapers, depending on your source images.

```
<advancedsettings>
<fanartres>1080</fanartres>
<imageres>1080</imageres>
</advancedsettings>

```


# Other / Known Issues
Videos > Playback > sync playback to display should always be set to **off** when using passthrough audio.

If your video is choppy or pausing, it may be due to another Android program. For example, certain popular Android FTP utilities appear to cause this issue. You are better off using the Shield's native SMB service instead. Similar issues have been seen with Live Channels and popular TV tuner plugins. With Shield Experience 5.1, you can double-click O to go to the recent apps page and close problematic apps. Additionally, we now recommend adding a delay between 2.5 and 4 seconds during a refresh rate change.  


