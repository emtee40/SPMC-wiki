You can now use the "RenderCapture" interface with Mediacodec Surface via Advanced Settings.
This interface is used by the various ambilight-like addons to capture what is displayed.

Before you ask, this is not enabled by default because it will popup a dialog asking for permission to "take screenshots" (i.e. capture) at startup. You can choose the hide the dialog forever, though.

As 99% of the users do not use ambilight, it was not proper to force this dialog on them.

In advancedsettings.xml 

    <advancedsettings>
    [...]
      <video>
        <usedroidprojectioncapture>true</usedroidprojectioncapture>
      </video>
    [...]
    </advancedsettings>
