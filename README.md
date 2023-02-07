# Touch OSC
Experiments with TouchOSC

## Setup

---

### Interface Editor

#### MacOS

Download and install [TouchOSC app for Mac](https://hexler.net/touchosc). It's free but intermittently suggests that you [buy a license](https://hexler.net/touchosc#buy) (NZD 44.16).

The device apps also have built in editors, but for the purpose of keeping everything in sync use the Client-Server *Editor Network* instead:

Click the WiFi symbol (which means *Editor Network*) > Server > Enabled.

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

Connect your device via USB if possible to reduce latency.

Open the app.

Click the WiFi symbol (which means *Editor Network*) > Client. Locate your Mac's name in the list and click the down arrow to see the address options.

Locate the address `192.xxx.x.xx:6666` and click *Connect* (I don't know what the other addresses represent and/or if one of them is the USB connection).

This puts your device into Control Surface mode. (This is usually accessed via the triangle / *Play* icon).

Click on an element in the desktop editor, change the *Color* then click away. The element color will update on all connected iDevices (regardless of whether they are connected via USB or WiFi).

---

### MIDI

#### Desktop

Download [TouchOSC Bridge](https://hexler.net/touchosc).

> TouchOSC Bridge is a standalone application that relays MIDI messages sent from TouchOSC to any MIDI capable application on your computer (and vice versa). TouchOSC Bridge is free to download and use. 

Install and open TouchOSC Bridge. *Enable USB Connections* is checked by default.

Download and install the [Protokol](https://hexler.net/protokol) test utility.

### OSC

#### Desktop

Download and install the [Protokol](https://hexler.net/protokol) test utility.

#### Ableton Live

1. Download the free [Connection Kit](https://www.ableton.com/en/packs/connection-kit/).
2. Open Ableton Live and drag *OSC TouchOSC.amxd* and *OSC Send.amxd* to the *User Library*
3. Drag *OSC TouchOSC* to a track
 * Port: Use the value from *TouchOSC app (any platform) > Connections > OSC > Send Port*. My desktop shows `6666` while my 3 connected iDevices show `8000`, so I entered `8000`

