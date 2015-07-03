touchPad
=====================================

An Arduino multitouch controller firmware for the MPR121 sensor.
It senses "touch down", "touch up" and "touch held" events on electrodes connected to the MPR121 pins and notifies them via serial communication (@9600 baud) using a compact 1 byte protocol.

Protocol
--------
Every time a new touch event is triggered, the software will send a new 1 byte packet formatted this way:

bit index:  1  2  3  4  5  6  7  8
use:       [P][P][P][P][P][P][T][T]

The 6 most significant bits are used to store the address of the pin that generated the event. This means the protocol allows 64 available addresses; a single MPR121 allows you to attach only 12 electrodes, so there is plenty of room for adding more sensors and/or incorporating new features into the protocol.

The 2 least significant bits store the event type:
0 means "touch down"
1 means "touch up"
2 means "touch held"

Since 2 bits are used and only 3 event types are implemented, it's possible to add a 4th event type.

Inspiration
-----------
All the MPR121 code is based on examples available on [Sparkfun](https://www.sparkfun.com/) and [Bildr](http://bildr.org/2011/05/mpr121_arduino/).

Wiring
------
Wiring the MPR121 to an Arduino is super simple:

MPR121		Arduino
GND_____________GND		
ADD_____________-
SDA_____________A4
SCL_____________A5
IRQ_____________D2
3.3V____________3.3V

Licence
-------
The code in this repository is available under the [MIT License](https://secure.wikimedia.org/wikipedia/en/wiki/Mit_license).  
Copyright (c) 2015 Enrico<naus3a>Viola
naus3a@gmail.com


