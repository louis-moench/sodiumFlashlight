I'm using some NLA Cree LEDs rated for 300mA constant, 600mA peak at 3.8V:
https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/843/CLN6A-WKW%2CMKW.pdf

I will underdrive them around 3.6V for longevity.

What transistor to use is unclear so far, but I can use Diodes, Inc.'s AL8860, which in MSOP-8EP can push up to 1.5A. This means i could conceivably use three series Sriko cells feeding multiple AL8860s into some FETs and then parallel LEDs. I'll shoot for a single converter, single fet, and maybe two LEDs at first.
