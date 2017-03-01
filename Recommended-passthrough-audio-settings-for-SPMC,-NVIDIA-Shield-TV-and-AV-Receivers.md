**Updated as of Shield Experience 5.1 and SPMC 16.6**

**After you have upgraded to Shield Experience 5.1 and SPMC 16.6, you should switch your audio passthrough settings to IEC, as described below. Similarly, we recommend that you adjust your display refresh rate = on start / stop, and pause during refresh change = 3.0 seconds to avoid related passthrough audio issues**

# Overview
SPMC supports decoding of many audio formats to uncompressed PCM, which can be processed by most TVs, soundbars, and AV receivers. If SPMC supports PCM decoding of a desired audio codec, there is no sonic difference between PCM output (where SPMC is doing the decoding) and bitstream output (where your AVR is doing the decoding).

If you have a recent AV receiver or soundbar, it may support native hardware decoding of advanced audio codecs such as DD+/DTS, DTS-HD MA, Dolby TrueHD, Dolby Atmos, and DTS:X. SPMC can passthrough bitstream audio to your AVR or soundbar with an advanced Android TV settop such as the NVIDIA Shield TV. 

In addition to freeing up settop device resources, the advantages of using passthrough are (1) to playback audio codecs that SPMC does not support and (2) to use your AVR to apply different effects to different codecs or channel inputs. For example, your AVR might be configured to apply multi-dimensional processing to a 2-channel PCM source (e.g. DTS Neo:6 Music creates a 5.1 channel output) while not processing DTS-HD MA, Dolby TrueHD, or other surround sounds codecs (i.e. passing them directly).

# Hardware Configuration
Even if your AVR or soundbar  supports DTS-HD MA or Dolby TrueHD, the method that you are using to send audio to your AVR may limit available hardware codecs.

Make sure you connect your Nvidia Shield TV directly to your AV Receiver using an HDMI 2.0a port. Then connect your TV to your AVR. If you connect your settop box directly to your TV instead and use the HDMI 1.4 Audio Return Channel, then you will only see DTS or Dolby Digital, not DTS-HD MA or Dolby TrueHD.

# SPMC Settings
Enable 'expert' in the settings menu. Then, make the following changes:

* Audio output device = **IEC**
* Number of channels = **7.1** [your receiver should be able to handle this input regardless of your actual speaker configuration. This number will be disregarded for any codec that your receiver supports for passthrough]
* Output configuration = **Best Match** 
* Stereo upmix = **off**
* Maintain original volume on downmix = **on**
* Boost centre channel when downmixing = **0 dB**
* Resample quality = **High**
* Keep audio devices alive = **10 Minutes** [this will prevent your AVR from going to sleep]
* Enable audio DSP processing = **off**
* Enable passthrough = **on**
* Passthrough output device = **IEC**

Check your AVR receiver's user manual to confirm that it supports each of the following audio codecs and enable them accordingly:

* Dolby Digital (AC3) capable receiver = **on**
* Dolby Digital Plus (E-AC) capable receiver = **on**
* DTS capable receiver = **on**
* TrueHD capable receiver = **on**
* DTS-HD capable receiver = **on**

# Audio Return Channel (ARC)
As noted above, you should use your AVR, not your TV, for HDMI input switching. One use case where this isn't feasible is if you wish to play 4K content and your AVR doesn't support either 4K or HDCP 2.2 but your TV does. In that instance, you can use Audio Return Channel to send the audio back to your AVR. You must connect your devices through ARC-enabled HDMI ports. 

However, many TVs are two-channel (2.0) only via ARC. And some TVs will send 5.1 if the TV is the source of the audio but won't pass 5.1 from other sources like a Blu-ray players or Android settop boxes. You may also need to configure the audio settings in your TV for "auto" or "direct". Finally, ARC only supports PCM, Dolby Digital, and DTS soundtracks that will pass over the SPDIF output, not Dolby TrueHD and DTS-HD. 

# Other
Videos > Playback > sync playback to display should always be set to **off** when using passthrough audio.

Additionally, we recommend adding a delay between 2.5 and 4 seconds during a refresh rate change. 

```
adjust display refresh rate = on start / stop
pause during refresh change = 3.0 seconds 
```