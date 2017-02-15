# Overview

SPMC supports decoding of many audio formats to uncompressed PCM, which can be processed by most TVs, soundbars, and AV receivers. If SPMC supports PCM decoding of a desired audio codec, there is no sonic difference between PCM output (where SPMC is doing the decoding) and bitstream output (where your AVR is doing the decoding).

If you have a recent AV receiver or soundbar, it may support native hardware decoding of advanced audio codecs such as DD and DTS. SPMC can passthrough bitstream audio to your AVR or soundbar on the Fire TV. 

In addition to freeing up settop device resources, the advantages of using passthrough are (1) to playback audio codecs that SPMC does not support and (2) to use your AVR to apply different effects to different codecs or channel inputs. For example, your AVR might be configured to apply multi-dimensional processing to a 2-channel PCM source (e.g. DTS Neo:6 Music creates a 5.1 channel output) while not processing other surround sounds codecs (i.e. passing them directly).

# Hardware Configuration
Even if your AVR or soundbar  supports DTS-HD MA or Dolby TrueHD, the Fire TV OS may limit your AVR's ability to process available hardware codecs. Following is a list of codecs that are supported using either passthrough (P) or software (S) decoding to PCM.


codec \ device | AFTV2 | AFTV1 | FireStick1
-------------- | ----- | ----- | ----------
DD (AC3) | P | P | S
DD-EX |  P  |  S  |  S
DD+ (E-AC) |  S  |  S  |  S
TrueHD |  S  |  S  |  S
Atmos |  S  |  S  |  S
DTS |  P  |  P  |  P
DTS 96/24 |  P  |  P  |  P
DTS-ES Discrete |  P  |  P  |  P
DTS-ES Matrix |  P  |  P  |  P
DTS-HD |  S  |  S  |  S
DTS:X |  S  |  S  |  S

P. Passthrough
S. Software decoded to PCM


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

* Dolby Digital (AC3) capable receiver = **on** (off for Fire Stick)
* Dolby Digital Plus (E-AC) capable receiver = **off**
* DTS capable receiver = **on**
* TrueHD capable receiver = **off**
* DTS-HD capable receiver = **off**

# Other
Videos > Playback > sync playback to display should always be set to **off** when using passthrough audio.

Additionally, we recommend adding a delay between 2.5 and 4 seconds during a refresh rate change. 

```
adjust display refresh rate = on start / stop
pause during refresh change = 3.0 seconds 
```