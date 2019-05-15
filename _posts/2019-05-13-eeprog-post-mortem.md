---
layout: post
title: "Post-mortem and future: eeprog"
---

As of revision C of my project [eeprog](https://hackaday.io/project/4543-eeprog), I now have a
working EEPROM programmer in the form of an Arduino Uno shield.

<img src="https://cdn.hackaday.io/images/6487911557815361636.jpg" width="200">

So let's have a short post-mortem of things I've learned.

## Simpler is probably better

The 28C64 EEPROM has 8 data pins and 13 address pins, but the Arduino Uno only has 14 digital pins.
My earliest design was based on a shift-register design, but when producing my first PCB I wanted to use an [8-bit I/O expander](https://www.microchip.com/wwwproducts/en/MCP23008) for the data bus and a [16-bit I/O expander](https://www.microchip.com/wwwproducts/en/MCP23016).

<img src="https://cdn.hackaday.io/images/6530291548584538749.png" width="400">

While this made sense at the time, introducing two new programmable devices in the end seemed to complicate things for than simplify. To make a long story short, I couldn't get this design to work even after many hours of debugging so I reverted back to my simpler design.

<img src="https://cdn.hackaday.io/images/1413691557815861341.png" width="400">

While I still had problems with my new design, the hardware was easier to debug because of the simpler design and I could quickly find that the problem was in the software. *Simpler is probably better*.

## Don't be afraid to experiment

When starting this project I was hoping to make a single revision of the board and be done, but boy was I wrong. Turns out though, this is not an issue.

Prices of making PCBs have come down significantly in the past few years, at least when comparing the manafactures I used to use and the new one I use. If you can accept month-long delivery times from China, you can get away with less than €20 for a batch of 5 two-layer PCBs. Therefore I feel that I *don't have to be afraid to experiment* in future design.

## You're never really done

There are still tons of improvements I could do to speed up the programming, and as was pointed out by a friendly commenter my design could easily be extended to support up to the much larger 28C256 EEPROM.
A stretch-goal would be to make a standalone version of the programmer, i.e. not an Arduino shield.

Obviously there are a lot of more things that could be said. I'm happy to have this project completed and have a very useful working tool that I can use for future projects.