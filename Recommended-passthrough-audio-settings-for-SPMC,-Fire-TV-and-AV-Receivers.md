**THIS DOCUMENT IS A WORK IN PROGRESS. IT NEEDS TO BE UPDATED FOR BOTH FTV1 and FTV2, RESPECTIVELY**

# Overview

SPMC supports decoding of many audio formats to uncompressed PCM, which can be processed by most TVs, soundbars, and AV receivers. If SPMC supports PCM decoding of a desired audio codec, there is no sonic difference between PCM output (where SPMC is doing the decoding) and bitstream output (where your AVR is doing the decoding).

If you have a recent AV receiver or soundbar, it may support native hardware decoding of advanced audio codecs such as DD+/DTS, DTS-HD MA, Dolby TrueHD, Dolby Atmos, and DTS:X. SPMC can passthrough bitstream audio to your AVR or soundbar with an advanced Android TV settop such as the Amazon Fire TV. 

In addition to freeing up settop device resources, the advantages of using passthrough are (1) to playback audio codecs that SPMC does not support and (2) to use your AVR to apply different effects to different codecs or channel inputs. For example, your AVR might be configured to apply multi-dimensional processing to a 2-channel PCM source (e.g. DTS Neo:6 Music creates a 5.1 channel output) while not processing DTS-HD MA, Dolby TrueHD, or other surround sounds codecs (i.e. passing them directly).

# Hardware Configuration
Even if your AVR or soundbar  supports DTS-HD MA or Dolby TrueHD, the method that you are using to send audio to your AVR may limit available hardware codecs.

Make sure you connect your Amazon Fire TV directly to your AV Receiver using an HDMI 2.0 port. Then connect your TV to your AVR. If you connect your settop box directly to your TV instead and use the HDMI 1.4 Audio Return Channel, then you will only see DTS or Dolby Digital, not DTS-HD MA or Dolby TrueHD.

Finally, make sure you are using Fire TV software v________ or later.

codec \ device | AFTV2 | AFTV1 | FireStick1
-------------- | ----- | ----- | ----------
DD (AC3) | P | P | 1
DD-EX |  P  |  1  |  1
DD+ (E-AC) |  1  |  1  |  1
TrueHD |  N  |  N  |  N
Atmos |  N  |  N  |  N
DTS |  P  |  P  |  P
DTS 96/24 |  P  |  P  |  P
DTS-ES Discrete |  P  |  P  |  P
DTS-ES Matrix |  P  |  P  |  P
DTS-HD |  N  |  N  |  N
DTS:X |  2  |  2  |  2

P. Passthrough
N. Passthrough not available, PCM software decoded
1. Passthrough did not work, no audio. Need debug
2. My AVR does not support DTS:X

Although there is no option for DTS-HD passthrough, it follows the DTS flag and passes through as DTS 5.1. So to use the proper 7.1 decoding, disable DTS passthrough and enable Support 8 channel DTS-HD audio decoding instead.

Atmos is decoded as 7.1 PCM.

DD-EX uses the DD passthrough flag. DTS 96/24 and both DTS-ES use the DTS passthrough flag.


# SPMC Settings
Enable 'expert' in the settings menu. Then, make the following changes:

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
* TrueHD capable receiver = **off**
* DTS-HD capable receiver = **on**


# Audio Return Channel (ARC)
As noted above, you should use your AVR, not your TV, for HDMI input switching. One use case where this isn't feasible is if you wish to play 4K content and your AVR doesn't support either 4K or HDCP 2.2 but your TV does. In that instance, you can use Audio Return Channel to send the audio back to your AVR. You must connect your devices through ARC-enabled HDMI ports. 

However, many TVs are two-channel (2.0) only via ARC. And some TVs will send 5.1 if the TV is the source of the audio but won't pass 5.1 from other sources like a Blu-ray players or Android settop boxes. You may also need to configure the audio settings in your TV for "auto" or "direct". Finally, ARC only supports PCM, Dolby Digital, and DTS soundtracks that will pass over the SPDIF output, not Dolby TrueHD and DTS-HD. 

# Other
Videos > Playback > sync playback to display should always be set to **off** when using passthrough audio.
