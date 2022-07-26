# Hacking a Camera onto Weather Balloons

In the San Diego area, a number of folks have been recovering radiosondes the
National Weather Service (NWS) flies.  Hacked FW re-tunes to an amateur radio
band has for hobbyist and educational re-flying.  And one radio amateur,
WB9COY, has hacked on a digital camera and FW to take and transmit pictures in
flight.

[Vaisala's RS41-SGP](https://www.vaisala.com/en/products/weather-environmental-sensors/upper-air-radiosondes-rs41) radiosonde is the model flown by the SD
NWS office.  GPS, pressure, temperature, and humidity sensor readings are
telemetered via UHF radio.  Weather agencies around the world take upper
atmosphere readings twice a day at the same time for snapshots to feed
atmospheric models.  This is also the source of those wonderful skew-T plots
useful for knowing if it is going to be a good day to fly a sailplane, if
thunderstorms are likely to bubble up in the afternoon, or if there is a long
range radio propagation enhancing tropospheric duct.


The GPS telemetry makes finding and recovering weather balloons interesting.
It's something between geocaching and radio direction finding.
[tracker.sondehub.org](https://tracker.sondehub.org/), a sister site of the
high altitude balloon hobbyist site [habhub](http://habhub.org/), is the
place to start.  A network of SDR receivers feeds this aggregating and mapping
server, just like the aircraft tracking with ADS-B.  Raspberry Pi with RTL-SDR
is one popular RX called
[autorx](https://github.com/projecthorus/radiosonde_auto_rx/wiki) and is used
for this.  A radiosonde kilometers high is LOS and is easy to receive, but
when it approaches the ground, terrain blockage is a problem.  Locally hams
have placed autorx receivers on a couple of strategic mountaintops to help
track the sondes into valleys and closer to their final landing spots.  This
has helped recovery efforts!

Another cool RX is the DL9RDZ's
[rdzTTGOsonde](https://github.com/dl9rdz/rdz_ttgo_sonde).  This firmware on
a TTGO LoRa ESP32 board provides a small handheld tracking receiver.  A wifi
server to an external display device will even show the location on a real-time
map.

A group of mentors that works with a local high school amateur radio club has
been recovering radiosondes, reprogramming them for the 440 MHz amateur radio
band, and re-flying them.  Modified FW to re-tune and use other modulation
modes was available.  Mentor and FW guru WB9COY used the 
[Happysat RS41](https://github.com/happysat/Vaisala-RS-41-SGP-Modification/blob/main/README.md)
project as a starting point.

Re-flying the sondes on an amateur band with an amateur radio callsign is cool,
but what else can be done with these?  Could more sensors be added?  The RS41
sonde has a serial port for peripherals!  One of the mentors found an
interesting
[TTL serial JPEG camera module](https://www.ebay.com/itm/284309055541)
that looked promising.  Sure, it's a VGA resolution still camera, but it can
be directly interfaced to the existing RS41 peripheral port and images from
near space are always cool!

[TODO:  used other open projects to get a start on camera software?]

WB9COY hacked the FW to incorporate the camera module and transmit pictures
back to the ground.  Early estimates suggested about 22 images possible during
a typical 90 minute fight.

FW:  https://github.com/wb9coy/RS41cam
