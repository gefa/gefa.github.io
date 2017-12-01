---
layout: post
title: "Generating PAL Video Signal"
date: 2012-07-6
---

What this device does is receive text from UART on PD0 pin 14 and displays it on the TV through RCA connector. In order to encode the text into analog video signal it uses PAL standard. 16MHz crystal is critical but fast enough. An interesting trick has been used to shift out the bits through PB5. Instead of torturing GPIO with bit banging, bits that make composite video are shifted out using SPI peripheral. Neat feature lies in the fact that CPU takes only one (or a few) cycles to write to SPI transmit register and SPI peripheral takes care about shifting those 8 bits (kill 8 flies with one hit). Schematic (adopted from magazine [infoelektronika](https://www.infoelektronika.net/)) has lot of discrete components dedicated to smoothing out the 5V power supply. My eagle board and schematic files as well as modified source code in C can be found [here](https://docs.google.com/file/d/0B09AKq-XVGSoSFVHblVlRWNEVGc/edit) (note that VGA functions are not used). Original C code for this project is little old for up-to-date WinAVR compiler. The original project is [here](http://www.vga-avr.narod.ru/). One of the useful references I found for generating a video from a microcontroller is actually [Cornell University lab exercise](http://people.ece.cornell.edu/land/courses/ece4760/).

![Alt text](/assets/pal-video-schematic.png "Schematic done in Eagle"){:height="600px" width="800px"}

![Alt text](/assets/pal-video-pcb-bottom.jpg "Etching was not that terrible"){:height="600px" width="800px"}

![Alt text](/assets/pal-video-pcb-top.jpg "Component layout"){:height="600px" width="800px"}

<strong>Use of mercury bulb for PCB photo transfer method</strong>

I used photo resist coated FR4 board. Lighting of the board is done with 160W mercury bulb. It is much easier to use one that does not need a ballast in series. That means it can be connected directly to power socket as a normal bulb. Lampholder for ordinary bulb has the same size. Mercury bulb is used since it emits lots of UV radiation. It is strongly recomended not to look at the bulb directly for a long time due to high UV radiation. There is small trick with this kind of bulbs. The one I have, that is 160W, is rated to work only in vertical position plus/minus 30 degrees, although for me it worked in every position. On the other hand, more powerfull mercury bulbs are rated to work in any position. Also it is important to note that mercury bulb need 2 to 3 minutes to achive its working point ( to worm up I guess). All in all illumination of the board for me lasted around 6 minutes. Distance from bulb to board was around 30 centimeters. Time of illumination will depend on the thickness of the photo resist coat, bulb-board distnce, power of the bulb. One should determine proper time empirically. If 6 minutes is too long for you, there is an option where you remove the outer balloon of the bulb. However, the stronger the ultra violet radiation the worse it is for eyes and skin. For more information on this topic go [here](http://www.elitesecurity.org/t23768-33), but you will probably have to use google translate.

<strong>Etching method</strong>

Etching is done with 30% solution of hydrogen peroxide (H2O2) and 18% muriatic acid (HCl). Note that both are toxic and dangerous for eyes and skin. For high speed etching (lot of poisonous fumes) use mix of 33% H2O2 and 66% HCl (etches in tenths of seconds). However, it is too fast and etches away tiny traces so I actually use mix of 20% of H2O2; 40% of HCl and 40% of H2O. This way it took me few minutes to etch this board. Percentage of water (H2O) could be reduced and is there just to slow down the reaction. Interesting thing I observed is that H2O2 dissolves over time (H2O2 = water + oxigen), especially on higher temperatures. Therefore, if the solution is too weak you may consider buying new hydrogen peroxide. For more about this visit [instructables](http://www.instructables.com/id/Stop-using-Ferric-Chloride-etchant!--A-better-etc/).
