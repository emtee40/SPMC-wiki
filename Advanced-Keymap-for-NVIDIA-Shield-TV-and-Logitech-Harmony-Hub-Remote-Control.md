# Overview
If you are using SPMC on the NVIDIA Shield TV along with a Logitech Harmony Hub based remote control, then the following custom keymap may be useful. This keymap is adapted from Amazon Fire TV custom keymaps for Kodi

Its key advantages:
* video will stop playing when you go back a screen
* subtitles can be quickly toggled by pressing up on your remote navigation pad during video playback
* codecinfo can be quickly toggled by pressing down on your remote navigation pad during video playback

Data from codecinfo is useful for submitting bug reports. It can confirm video and audio codecs in use, frame rate, hardware acceleration, buffer size and CPU utilization.

The default NVIDIA Shield TV profile for the Logitech Harmony hub remote controls uses IR. If you configure your Shield TV to connect with your Harmony via Bluetooth, then key responses will be faster. IP control of the Shield TV is not currently an option via the Logitech Harmony.

Note: certain keys such as 0-9 number keys do not work via the Logitech Harmony remote with the Shield TV.


# SPMC Settings
```

<?xml version="1.0" encoding="UTF-8"?>
<keymap>
  <Home>
    <keyboard>
      <menu>XBMC.ActivateWindow(Favourites)</menu>
    </keyboard>
  </Home>
  <FullscreenVideo>
    <keyboard>
      <menu>seek(-7)</menu>
      <backspace>Stop</backspace>
      <browser_back>Stop</browser_back>
      <up>ShowSubtitles</up>
      <down>CodecInfo</down>
    </keyboard>
  </FullscreenVideo>
  <VideoMenu>
    <keyboard>
      <backspace>Stop</backspace>
      <browser_back>Stop</browser_back>
    </keyboard>
  </VideoMenu>
  <MyFiles>
    <keyboard>
      <play_pause>Highlight</play_pause>
    </keyboard>
  </MyFiles>
  <virtualkeyboard>
    <keyboard>
      <menu>shift</menu>
      <play_pause>enter</play_pause>
      <rewind>backspace</rewind>
      <fastforward>number0</fastforward>
      <backspace>Stop</backspace>
      <browser_back>Stop</browser_back>
    </keyboard>
  </virtualkeyboard>
<Visualisation>
<keyboard>
<browser_back>Stop</browser_back>
<backspace>Stop</backspace>
</keyboard>
</Visualisation>
  <Favourites>
    <keyboard>
      <browser_back>close</browser_back>
    </keyboard>
  </Favourites>
  <NumericInput>
    <keyboard>
      <browser_back>Close</browser_back>
    </keyboard>
  </NumericInput>
  <PVROSDChannels>
    <keyboard>
      <browser_back>Close</browser_back>
    </keyboard>
  </PVROSDChannels>
  <PVROSDGuide>
    <keyboard>
      <browser_back>Close</browser_back>
    </keyboard>
  </PVROSDGuide>
  <PVROSDDirector>
    <keyboard>
      <browser_back>Close</browser_back>
    </keyboard>
  </PVROSDDirector>
  <PVROSDCutter>
    <keyboard>
      <browser_back>Close</browser_back>
    </keyboard>
  </PVROSDCutter>
  <MyTVSettings>
    <keyboard>
      <browser_back>PreviousMenu</browser_back>
    </keyboard>
  </MyTVSettings>
</keymap>
```