# Overview
SPMC supports rendering of both the graphical user interface and video in up to 4K (2160p) resolution if you have a high-end Android TV settop box like the NVIDIA Shield TV and a UHD (4K) TV. If you have a UHD TV and you watch 2160p (4K) content, then you should use [these instructions instead](https://github.com/koying/SPMC/wiki/Recommended-video-settings-for-SPMC%2C-NVIDIA-Shield-TV-and-UHD-%284K%29-TVs-with-4K-GUI).

However, if you only have a Full HD (1080p) TV or if you have a UHD TV but only watch 1080p content in any of your apps on your Shield, then you should use the settings below. 

If you have a UHD TV, you will have the added benefit of using your UHD TV's upscalers. These may provide better video quality of 1080p content displayed at 4K resolution than SPMC's upscalers. Additionally, content below 1080p such as 480i and 720p will be upscaled to 1080p by SPMC using the HQ scalers.  _"Lanczos3 - optimised"_ is the best video scaling method. 

_"Yadif (2x)"_ is the best deinterlacing available on the Shield TV but, because it is not hardware accelerated, it is best for SD resolution videos.  For HD videos, _"Bob Inverted"_ is the best deinterlacing for HD videos because it is hardware accelerated.


# UHD TV Settings
Because your content is limited to 1080p, your TV should be configured with limited range of RGB (16-235). You should be able to use both HDMI 1.4 and HDMI 2.0 ports though users have reported a few issues due to HDMI 1.4 devices.


# Android TV Settings
Confirm that your Shield TV is configured to limit the video output resolution to 1080p:
```
Settings > Device > HDMI > 1080p
```


# SPMC Settings
Enable 'expert' in the settings menu. Then, make the following changes:

## Videos > Playback
* adjust display refresh rate = **always**
* sync playback to display = **off**

## Videos > Acceleration
* enable HQ scalers = **low**
* allow hardware acceleration - Mediacodec (Surface) = **off**
* allow hardware acceleration - Mediacodec = **on**
* accelerate MPEG2 = **HD and up**
* accelerate MPEG4 = **HD and up**
* accelerate h264 = **HD and up**

## System > Video Output
* set GUI resolution limit = **1080**
* vertical blank sync = **always enabled**

## OSD Video Settings
While playing a video, go to the OSD > Video Settings
* deinterlace video = **auto**
* deinterlace method (SD/software accelerated) = **yadif (2x)**
* deinterlace method (HD/hardware accelerated) = **bob inverted**
* video scaling method = **lanczos3 - optimised**

Be sure to set these as the **default for all media**!

## advancedsettings.xml
Finally, add the following lines to your advancedsettings.xml. The fanart and imageres elements are optional but enable higher quality jacket art and wallpapers, depending on your source images.

```
<advancedsettings>
<video>
<enablehighqualityhwscalers>true</enablehighqualityhwscalers>
</video>
<fanartres>1080</fanartres>
<imageres>1080</imageres>
</advancedsettings>

```


# Other
Videos > Playback > sync playback to display should always be set to **off** when using passthrough audio.

Refresh rate switching doesn't work if the AVR is HDMI 2.0/HDCP 2.2 and the display is HDMI/HDCP 1.4. 

HDR10 is active only in 4K at 40/59.94/60Hz [see these instructions](https://github.com/koying/SPMC/wiki/Recommended-video-settings-for-SPMC%2C-NVIDIA-Shield-TV-and-UHD-%284K%29-TVs-with-4K-GUI).