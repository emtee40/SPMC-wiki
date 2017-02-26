**Updated as of Shield Experience 5.0.2 and SPMC 16.5.5 and the 16.6 beta**

# Overview
# UHD TV Settings
Because your content is limited to 1080p, your TV should be configured with limited range of RGB (16-235). You should be able to use both HDMI 1.4 and HDMI 2.0 ports though users have reported a few issues due to HDMI 1.4 devices.


# Android TV Settings
Confirm that your Fire TV is configured to limit the video output resolution to "auto":
```
PATH NEEDED
```


codec \ device | AFTV2 | AFTV1 | FireStick1
-------------- | ----- | ----- | ----------
H.263 | S | H | H
H.264 | H | H | H
H.265 | H | X | X
MPEG2 (SD) | S | S | S
MPEG2 (HD) | X | X | X
VC-1 (SD) | S | S | S
VC-1 (HD) | X | X | X


# SPMC Settings
Enable 'expert' in the settings menu. Then, make the following changes:

## Videos > Playback
* adjust display refresh rate = **on start / stop**
* pause during refresh change = **3.0 seconds**
* sync playback to display = **off**

## Videos > Acceleration
* allow hardware acceleration - Mediacodec (Surface) = **on**
* allow hardware acceleration - Mediacodec = **on**
* accelerate MPEG4 = **HD and up**
* accelerate h264 = **HD and up**

## System > Video Output
* set GUI resolution limit = **1080**
* vertical blank sync = **always enabled**

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


# Other / Known Issues
Videos > Playback > sync playback to display should always be set to **off** when using passthrough audio.

Refresh rate switching doesn't work if the AVR is HDMI 2.0/HDCP 2.2 and the display is HDMI/HDCP 1.4. 
