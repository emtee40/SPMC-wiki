# Overview
SPMC supports decoding of many audio formats to uncompressed PCM, which can be processed by most TVs, soundbars, and AV receivers. If SPMC supports PCM decoding of a desired audio codec, there is no sonic difference between PCM output (where SPMC is doing the decoding) and bitstream output (where your AVR is doing the decoding).

If you have a recent AV receiver or soundbar, it may support native hardware decoding of advanced audio codecs such as DD+/DTS, DTS-HD MA, Dolby TrueHD, Dolby Atmos, and DTS:X. SPMC can passthrough bitstream audio to your AVR or soundbar with an advanced Android TV settop such as the NVIDIA Shield TV. In addition to freeing up settop device resources, the advantage of using passthrough is to playback audio codecs that SPMC does not support. 

# Hardware Configuration
Even if your AVR or soundbar  supports DTS-HD MA or Dolby TrueHD, the method that you are using to send audio to your AVR may limit available hardware codecs.

Make sure you connect your Nvidia Shield TV directly to your AV Receiver using an HDMI 2.0 port. Then connect your TV to your AVR. If you connect your settop box directly to your TV instead and use the HDMI 1.4 Audio Return Channel, then you will only see DTS or Dolby Digital, not DTS-HD MA or Dolby TrueHD.

Finally, make sure you are using Shield Android TV software v3.1 or later.

# SPMC Settings
* Audio output device = **Android, RAW Passthrough**
* Number of channels = **7.1** [your receiver should be able to handle this input regardless of your actual speaker configuration]
* Output configuration = **Best Match** 
* Stereo upmix = **off**
* Maintain original volume on downmix = **on**
* Boost centre channel when downmixing = **0 dB**
* Resample quality = **High**
* Keep audio devices alive = **10 Minutes** [this will prevent your AVR from going to sleep]
* Enable audio DSP processing = **off**
* Enable passthrough = **on**
* Passthrough output device = **Android, RAW Passthrough**

Check your AVR receiver's user manual to confirm that it supports each of the following audio codecs and enable them accordingly:

* Dolby Digital (AC3) capable receiver = **on**
* Dolby Digital Plus (E-AC) capable receiver = **on**
* DTS capable receiver = **on**
* TrueHD capable receiver = **on**
* DTS-HD capable receiver = **on**


# Other
Videos > Playback > sync playback to display should always be set to **off** when using passthrough audio.
