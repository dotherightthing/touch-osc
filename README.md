# Touch OSC
Experiments with TouchOSC

## Setup

---

### Interface Editor

#### MacOS

Download and install [TouchOSC app for Mac](https://hexler.net/touchosc). It's free but intermittently suggests that you [buy a license](https://hexler.net/touchosc#buy) (NZD 44.16).

The device apps also have built in editors, but for the purpose of keeping everything in sync use the Client-Server *Editor Network* instead:

Click on *Editor Network* (WiFi icon) > Server > Enabled.

**Note: this comes with some quirks.** Repeatedly toggling the *Editor Network* off and on seems to open a new tab on the client iDevice. With multiple copies open, it's difficult to know which one is synced to the macOS server - some of them? all of them? none of them?

In the menubar, click `+` > *Fader*.

Locate the *Control* panel on the right hand side of the editor. The *Name* is *fader1*.

Locate the *Messages* panel below this. The *Address* is `/name`. This means that the OSC address of this control is `./fader1`.

To change the name:

1. Click on `name` and click Delete.
2. To the right of *Address*, click `+` > Constant.
3. Delete `constant` and type something else, e.g. `myfader`.
4. Click away and the *Address* changes to `/myfader`. The *Control* name is still `fader1`. This means that the OSC address of the `fader1` control is now `./myfader`.

#### iOS

Download [TouchOSC app from the App Store](https://apps.apple.com/us/app/touchosc/id1569996730) (USD 9.99, NZD 16.99). One purchase enables the download for all of your iDevices.

Connect your device via USB and disable WiFi. This minimises latency and reduces the complexity of network connections!

Open the app.

Tap on *Editor Network* (WiFi icon) > Client. Locate your Mac's name in the list and tap the down arrow to see the address options.

Locate the address `169.xxx.xxx.xx` (this appears at the top of the list and is currently `169.254.248.82`) and click *Connect*.

This forces your device into Control Surface mode. (This is normally accessed via the triangle / *Play* icon).

**In the desktop editor,** change the *Color* then click away. The element color will update on all *Client* iDevices (regardless of whether they are connected via USB or WiFi).

---

### OSC

> Please note the wired USB connection only passes MIDI through (which is the purpose of the TouchOSC Bridge), as OSC itself requires a network protocol to function and therefore does require a network connection.
> 
> More information on wired connection with TouchOSC can be found here: https://hexler.net/blog/post/uncut-the-wire
>
> [Source](https://forum.cockos.com/showpost.php?s=2ec6a5eec3cf68ef01881e65ae863ad9&p=2113867&postcount=4)

But [Wired USB Connection To TouchOSC](https://osculator.net/forum/forum/support/mobile-apps-ios-android/1882-wired-usb-connection-to-touchosc) suggests that a wired connection supports both MIDI and OSC.


#### macOS

Download and install the [Protokol](https://hexler.net/protokol) test utility.

#### iOS

Tap on *Connections* (link icon)

*Connection 1*:
   * UDP
   * Host: Tap *Browse* and select the Mac, then select `169.xxx.xxx.xx:xxxx` (this appears at position 3 on the list and is currently `169.254.248.82:6667`.
   * Send Port: `6667` (as per the selected host)
   * Receive Port: `6668` (arbitrary - this (just) needs to be [different from the Send port](https://support.etcconnect.com/HES/Consoles/Hog_4/Networking/How_To_Setup_Touch_OSC_and_Hog_4)). Tap the `(i)` to the right to see the IP address of the iDevice - `en2 169.254.77.91`.
   * Enable by checking the checkbox

#### Ableton Live

1. Download the free [Connection Kit](https://www.ableton.com/en/packs/connection-kit/).
2. Open Ableton Live and drag *OSC TouchOSC.amxd* and *OSC Send.amxd* to the *User Library*

##### Input

Drag *OSC TouchOSC.amxd* to a track

1. *Port*: This is the Mac's 'in' port, corresponding to the iOS device's 'out' port - so enter the iOS *Send Port* number (`6666`)
2. Click *Learn* > Move the slider on an iOS device > `/myfader` appears under *OSC Address* > click *Learn* again to deactivate learn mode
3. Click *Map* > Move a control in Live > The control's name appears under the *Parameter* box
4. Move the slider on an iOS device > The mapped control moves.

* Note: this is uni-directional, so the other connected iDevices won't update to match, and you'll need to configure each device to have a matching UDP connection in order for them to also have uni-directional control.
* Note: The mapped control cannot be moved with the mouse anymore.

##### Output

Disable the *OSC TouchOSC* device

Drag *OSC Send.amxd* to the same (or another) track

1. *Host*: Enter the IP Address of the iDevice (`192.168.1.21`) - this means that it's impossible to update all connected iDevices at the same time. Alternatively enter the IP Address of the Mac (`192.168.1.24`) - but this won't affect the connected iDevices, even if they are connected to the *Editor Network* server
2. *Port*: Enter the *Receive Port* of the iDevice (`6667`)

Click *Map* > Move a control in Live (which is why *OSC TouchOSC.amxd* is disabled).

Enter `/myfader` into *OSC Address*.

Move the slider in Live > The control will update on the iDevice.

Enable the *OSC TouchOSC* device.

**Now** adjusting the control on an iDevice will mirror the changes in the Mac editor - but not vice versa. Changing the *OSC Send* Host to `192.168.1.21` (the Mac) allows the Mac editor to control the iDevice, but again not vice versa.

---

### MIDI

#### Desktop

Download [TouchOSC Bridge](https://hexler.net/touchosc).

> TouchOSC Bridge is a standalone application that relays MIDI messages sent from TouchOSC to any MIDI capable application on your computer (and vice versa). TouchOSC Bridge is free to download and use. 

Install and open TouchOSC Bridge. *Enable USB Connections* is checked by default.

Download and install the [Protokol](https://hexler.net/protokol) test utility.
