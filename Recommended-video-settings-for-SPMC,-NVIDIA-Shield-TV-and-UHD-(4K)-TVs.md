# Overview
SPMC supports rendering of both the graphical user interface and video in up to 4K (2160p) resolution if you have a high-end Android TV settop box like the NVIDIA Shield TV and a UHD (4K) TV. 

If you have a UHD TV, you should configure the Shield TV settop for the maximum 4K output. In addition to SPMC, you can watch 4K content in other apps such as Netflix and Youtube. 

The tradeoff is that the Shield TV settop--not the your TV--will upsample videos below 2160p. As of SPMC 16.3 and Shield Android TV software v3.1, new HQ scalers are an option to improve video quality. "Lanczos3 - optimised" is the best video scaling method and Bob is the best deinterlacing available in SPMC on the Shield TV.


# UHD TV Settings
Confirm whether your UHD TV supports the HDMI 2.0 specifications and can accept UHD (50P/60P 4:4:4 and 4:2:2) signals. The default setting of many UHD TVs may be configured for HD/FHD signals. You may need to change the HDMI UHD Color setting to 'On'. 

Depending on your TV, the UHD HDMI port may make a difference. Double-check your user manual to confirm that you have plugged your NVIDIA Shield into a HDMI 2.0 port.


# AV Receiver Settings
If you are using an AV receiver, make sure that your AVR is configured to support 4K signal passthrough but is not modifying the video.


# Android TV Settings
Confirm that your Android TV is configured to permit the highest possible video output:
```
Settings > Device > HDMI > 4K 60Hz (Recommended)
```

# SPMC Settings
Make the following changes:

## Videos > Playback
* adjust display refresh rate = **always**
* pause during refresh rate change = **off**
* sync playback to display = **off**

## Videos > Acceleration
* enable HQ scalers = **low**
* allow hardware acceleration - Mediacodec (Surface) = **off**
* allow hardware acceleration - Mediacodec = **on**
* accelerate MPEG2 = **always**
* accelerate MPEG4 = **always**
* accelerate h264 = **always**

## System > Video Output
* set GUI resolution limit = **unlimited**
* vertical blank sync = **always enabled**

## OSD Video Settings
While playing a video, go to the OSD > Video Settings
* deinterlace video = **auto**
* deinterlace method = **bob**
* video scaling method = **lanczos3 - optimised**

Be sure to set these as the **default for all media**!

## advancedsettings.xml
Finally, add the following lines to your advancedsettings.xml

```
<advancedsettings>
<video>
<enablehighqualityhwscalers>true</enablehighqualityhwscalers>
</video>
<fanartres>2160</fanartres>
<imageres>2160</imageres>
</advancedsettings>`
