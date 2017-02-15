**Updated as of SPMC 16.5.5 and the 16.6 beta**

# Overview
SPMC runs on Android-based settops and TVs. The settings below permit you to watch content in up to 4K (2160p) resolution if you have a UHD (4K) TV. However, the GUI will be limited to 1920 × 1080 resolution. 

If you have an Nvidia Shield TV, you should use [these instructions for 4K GUI](https://github.com/koying/SPMC/wiki/Recommended-video-settings-for-SPMC%2C-NVIDIA-Shield-TV-and-UHD-%284K%29-TVs-with-4K-GUI) or [these instructions for 1080 GUI](https://github.com/koying/SPMC/wiki/Recommended-video-settings-for-SPMC-and-NVIDIA-Shield-TV-with-1080p-GUI) instead.

These settings are intended for lower-powered devices and therefore do not make use of SPMC's HQ scalers. If you have a UHD (4K) TV, its internal upscalers may improve your video quality.


# TV Settings
Because your content is limited to 1080p, your TV should be configured with limited range of RGB (16-235). You should be able to use both HDMI 1.4 and HDMI 2.0 ports though users have reported a few issues due to HDMI 1.4 devices.

# SPMC Settings
Enable 'expert' in the settings menu. Then, make the following changes:

## Videos > Playback
* adjust display refresh rate = **on start / stop**
* pause during refresh change = **3.0 seconds**
* sync playback to display = **off**

## Videos > Acceleration
* allow hardware acceleration - Mediacodec (Surface) = **on**
* allow hardware acceleration - Mediacodec = **on**
* accelerate MPEG4 = **always**
* accelerate h264 = **always**

## System > Video Output
* set GUI resolution limit = **1080**
* vertical blank sync = **always enabled**

# Other
Videos > Playback > sync playback to display should always be set to **off** when using passthrough audio.

Philips and Sony TVs do not support refresh rate adjustment
