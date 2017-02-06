**Updated as of Shield Experience 5.0.2 and SPMC 16.5.5.** 

**Note: with SPMC 16.5.x, you must disable MediaCodec (Surface) to use upscaling or deinterlacing. However, if you disable MediaCodec (Surface), then HDR content will not be displayed in HDR.**

# Overview
SPMC supports rendering of both the graphical user interface and video in up to 4K (2160p) resolution if you have a high-end Android TV settop box like the NVIDIA Shield TV and a UHD (4K) TV. 

If you have a UHD TV, you should configure the Shield TV settop for the maximum 4K output. With the configuration below, you can then view the SPMC GUI at 2160p. In addition to SPMC, you can watch 4K content in other apps such as Netflix, VUDU, and YouTube. 

The tradeoff is that the Kodi app--not your UHD TV--will upsample videos below 2160p. As of SPMC 16.4.1 and Shield Android TV software v3.2, new HQ scalers are an option to improve video quality. _"Lanczos3 - optimised"_ is the best video scaling method. 

_"Yadif (2x)"_ is the best deinterlacing available on the Shield TV but, because it is not hardware accelerated, it is best for SD resolution videos.  For HD videos, _"Bob Inverted"_ is the best deinterlacing for HD videos because it is hardware accelerated.

As of Shield Android TV software v3.2, you can also watch HDR videos in SPMC. HDR is active only for 4K 50/59.94/60Hz.

# UHD TV Settings
Confirm whether your UHD TV supports the HDMI 2.0 specifications and can accept UHD (50P/60P 4:4:4, 4:2:2 and 4:2:0) signals. The default setting of many UHD TVs may be configured for HD/FHD signals with limited range of RGB (16-235). You may need to change the HDMI UHD Color setting to **on** for the full range of RGB (0-255).

Depending on your TV, the specific HDMI port may make a difference. Double-check your user manual to confirm that you have plugged your NVIDIA Shield into a HDMI 2.0 port supporting HDCP 2.2.


# AV Receiver Settings
If you are using an AV receiver, make sure that your AVR is configured to support 4K signal passthrough but is not modifying the video resolution.


# Android TV Settings
Confirm that your Shield TV is configured to permit the highest possible video output resolution:
```
Settings > Display & Sound > Resolution > 4K 59.940Hz (Recommended)
```

Additionally, Dynamic Range should be set to **auto**. If you UHD TV can be set to the full range of RGB, then you should set the Shield to the **full** range. The newest displays may benefit from tweaking the Shield's color space settings. If available, you should set your display for YCbCr 4:2:2 12-bit Rec.2020. 


# SPMC Settings
Enable 'expert' in the settings menu. Then, make the following changes:

## Videos > Playback
* adjust display refresh rate = **on start / stop**
* pause during refresh change = *3.0 seconds*
* sync playback to display = **off**

## Videos > Acceleration
* enable HQ scalers = **low**
* allow hardware acceleration - Mediacodec (Surface) = **off**
* allow hardware acceleration - Mediacodec = **on**
* accelerate MPEG2 = **HD and up**
* accelerate MPEG4 = **HD and up**
* accelerate h264 = **HD and up**
* accelerate hevc = **HD and up**

## System > Video Output
* set GUI resolution limit = **unlimited**
* vertical blank sync = **always enabled**

## OSD Video Settings
While playing a video, go to the OSD > Video Settings
* deinterlace video = **auto**
* deinterlace method (SD/software) = **yadif (2x)**
* deinterlace method (HD/hardware accelerated) = **bob inverted**
* video scaling method = **lanczos3 - optimised**

Be sure to set these as the **default for all media**! Certain options, such as yadif, will not be visible unless you are watching a video using software decoding.

## advancedsettings.xml
Finally, add the following lines to your advancedsettings.xml. The fanart and imageres elements are optional but enable higher quality jacket art and wallpapers, depending on your source images.

```
<advancedsettings>
<video>
<enablehighqualityhwscalers>true</enablehighqualityhwscalers>
</video>
<fanartres>2160</fanartres>
<imageres>2160</imageres>
</advancedsettings>

```


# Other / Known Issues
Videos > Playback > sync playback to display should always be set to **off** when using passthrough audio.

If your video is choppy or pausing, it may be due to another Android program. For example, certain popular Android FTP utilities appear to cause this issue. You may be better off using the Shield's native SMB service instead. Similar issues have been seen with Live Channels and popular tuner plugins. With Shield Experience 5.0.1, you can double-click O to go to the recent apps page and close problematic apps.

Additionally, we now recommend adding a delay between 2.5 and 4 seconds during a refresh rate change.  

With Shield Experience v3.2, refresh rate switching defaults to RGB. It overrides the color space setting (YCbCr, RGB). This appears to be fixed in Shield Experience v5.0.1.

With Shield Experience v3.2, refresh rate switching doesn't work if the AVR is HDMI 2.0/HDCP 2.2 and the display is HDMI/HDCP 1.4. This appears to be fixed in Shield Experience v5.0.1.

HDR modes will default to 10-bit Rec. 2020 YCbCr 4:2:0 (provided your display supports that). As of Shield Experience 5.0.1, HDR-10 HDR is supported but not DolbyVision. You may separately need to update your display firmware. For example, early Vizio Smartcast display firmware versions supported DolbyVision and not HDR-10.