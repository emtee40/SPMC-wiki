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
* adjust display refresh rate = **always**
* sync playback to display = **off**

## Videos > Acceleration
* allow hardware acceleration - Mediacodec (Surface) = **on**
* allow hardware acceleration - Mediacodec = **on**
* accelerate MPEG2 = **always**
* accelerate MPEG4 = **always**
* accelerate h264 = **always**

## System > Video Output
* set GUI resolution limit = **1080**
* vertical blank sync = **always enabled**

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

With Shield Android TV software v3.2 and 3.3, refresh rate switching defaults to RGB. It overrides the color space setting (YCbCr, RGB). 

Refresh rate switching may not work properly if the AVR is HDMI 2.0/HDCP 2.2 and the display is HDMI/HDCP 1.4. 
