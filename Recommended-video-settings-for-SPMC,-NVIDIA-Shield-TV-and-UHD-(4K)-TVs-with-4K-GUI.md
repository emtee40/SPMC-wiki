**Updated as of Shield Experience 6.1 and SPMC 17** 

**Note: with SPMC 17, you must disable MediaCodec (Surface) to use upscaling or deinterlacing. However, if you disable MediaCodec (Surface), then HDR content will not be displayed in HDR.**

# Overview
SPMC supports rendering of both the graphical user interface and video in up to 4K (2160p) resolution if you have a high-end Android TV settop box like the NVIDIA Shield TV and a UHD (4K) TV. 

If you have a UHD TV, you should configure the Shield TV settop for the maximum 4K output. With the configuration below, you can then view the SPMC GUI at 2160p. In addition to SPMC, you can watch 4K (and potentially HDR) content in other apps such as Netflix, Amazon, VUDU, and YouTube. 

The tradeoff is that the Kodi app--not your UHD TV--will upsample videos below 2160p. SPMC has HQ scalers that can be enabled to improve video quality. **"Lanczos3 - optimised"** is the best HQ video scaling method. 

**"Yadif (2x)"** is the best deinterlacing available on the Shield TV but, because it is not hardware accelerated, it is best for SD resolution videos. _"Bob Inverted"_ is the best deinterlacing for HD videos because it is hardware accelerated.


# UHD TV Settings
Depending on your TV vendor, you may need to change the HDMI UHD Color setting to **on** _(Samsung)_, Input > 'HDMI Color Subsampling' to **on** _(Vizio)_ or 'Enhanced HDMI' to **on** _(Sony)_ for a given HDMI input.

The specific HDMI port may make a difference on your TV. Double-check your user manual to confirm that you have plugged your NVIDIA Shield into a HDMI 2.0 port supporting HDCP 2.2. 

In addition to the HDMI ports on your TV, AVR, and Shield, the type (HDMI 1.4 v 2.0) and the length of HDMI cable will impact your available options. HDR requires HDMI 2.0a.

# AV Receiver Settings
If you are using an AV receiver, make sure that your AVR is configured to support 4K signal passthrough and is not modifying the video resolution (disable upscaling). You should use an HDMI 2.0a port supporting HDCP 2.2 on your AVR.


# Android TV Settings
Confirm that your Shield TV is configured to permit the highest possible video output resolution:
```
Settings > Display & Sound > Resolution > 4K 59.940Hz (Recommended)
```

**RGB output:** *Dynamic Range* should be set to **auto**. If your UHD TV can be set to the full range of RGB, then you should set the Shield to the **full** range. 

**YCbCr output**: the newest UHD displays may benefit from tweaking the Shield's color space settings. You should set your display to the highest available setting, listed below:

* YCbCr 4:2:2 12-bit Rec.2020
* YCbCr 4:2:0 10-bit Rec.2020
* YCbCr 4:2:2 12-bit Rec.709
* YCbCr 4:2:0 10-bit Rec.709
* YCbCr 4:4:4 8-bit Rec.709
* YCbCr 4:2:0 8-bit Rec.709

UHD sources may be up to 10-bit Rec.2020. Blu-ray sources are 8-bit. Online streaming sources are probably 8-bit. Higher bit rates have more color values and are less susceptible to banding. 

4:4:4 is a full bandwidth signal, with full (Cb, Cr) vertical and horizontal resolution. 4:2:2 needs 2/3rds the bandwidth, with ½ horizontal resolution and full vertical resolution. 4:2:0 needs ½ the bandwidth, with ½ horizontal resolution and
½ vertical resolution. 


# SPMC Settings
Enable 'expert' in the settings menu. Then, make the following changes:

## Videos > Playback
* adjust display refresh rate = **on start / stop**
* pause during refresh change = **3.0 seconds**
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

If your video is choppy or pausing, it may be due to another Android program. For example, certain popular Android FTP utilities appear to cause this issue. You are better off using the Shield's native SMB service instead. Similar issues have been seen with Live Channels and popular TV tuner plugins. With Shield Experience 5.1, you can double-click O to go to the recent apps page and close problematic apps. Additionally, we now recommend adding a delay between 2.5 and 4 seconds during a refresh rate change.  

HDR modes will default to 10-bit Rec. 2020 YCbCr 4:2:0 (provided your display supports that). As of Shield Experience 6.1, HDR-10 HDR is supported but not DolbyVision. You may separately need to update your display firmware. For example, early Vizio Smartcast display firmware versions supported DolbyVision and not HDR-10.