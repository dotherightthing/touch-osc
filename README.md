# Touch OSC
Experiments with TouchOSC

## Setup

---

### Interface Editor

#### MacOS

Download and install [TouchOSC app for Mac](https://hexler.net/touchosc). It's free but intermittently suggests that you [buy a license](https://hexler.net/touchosc#buy) (NZD 44.16).

The device apps also have built in editors, but for the purpose of keeping everything in sync use the Client-Server *Editor Network* instead:

Click the WiFi symbol (which means *Editor Network*) > Server > Enabled.

#### iOS

Download [TouchOSC app from the App Store](https://apps.apple.com/us/app/touchosc/id1569996730) (USD 9.99, NZD 16.99). One purchase enables the download for all of your iDevices.

Connect your device via USB if possible to reduce latency.

Open the app.

Click the WiFi symbol (which means *Editor Network*) > Client. Locate your Mac's name in the list and click the down arrow to see the address options.

Locate the address `192.xxx.x.xx:6666` and click *Connect* (I don't know what the other addresses represent and/or if one of them is the USB connection).

This puts your device into Control Surface mode. (This is usually accessed via the triangle / *Play* icon).

Click on an element in the desktop editor, change the *Color* then click away. The element color should update on all connected iDevices as well.

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

