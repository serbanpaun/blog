# How to remove Android popup for Anydesk remote connection

This is the most annoying thing once with the latest Android versions... Whenever I want to remotely connect to a device using Anydesk - even if I am actually using a password! - I get this popup asking the remote user to approve if screen recording may start.

Since I am aiming for *unattended access*, I do not want to be locked out because of this popup. Therefore... there is a fix!

First you need to enable **Developer Options** on your phone/tablet, then enable **Enable USB debugging**. Once you have these enabled, connect your device to a computer and make sure you have installed the **Android SDK Platform Tools**.
Open a command prompt and first type:

```
adb devices
```

A prompt will appear on your device to always trust that connection. If it is your own computer, you are safe to allow it.
On your computer, in command prompt, you will see the ID of the device - and that is a good sign telling you that the connection between computer and device is working!

Now type this command in the command prompt - which will actually allow `PROJECT_MEDIA` permissions for the Anydesk app:

```
adb shell appops set com.anydesk.anydeskandroid permission PROJECT_MEDIA allow
```

And that's it! You can now connect automatically to the device, without the popup showing to confirm the connection!
