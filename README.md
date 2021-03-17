# Z80-Card for Commodore C64

I'm currently working on a Z80 card for the Commodore C64 to be able to use CP/M 2.2. The whole thing is based on a CPLD and a 8MHz Z80 processor.

![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_design_pcb.jpg)



Currently, the project is in beta phase. I would personally classify the stability as quite high, at least with the computers I tested.

## Description

Based on the old Commodore CP/M cartridge, I hooked the Z80 processor directly to the 8MHz dot clock of the C64. 

However, at least if you don't switch off the VIC, the rest of the C64 still works with only 1MHZ, so the access to RAM, floppy drive, etc. is still limited in speed.

A big other problem was the compatibility of the old original module. I have the following boards in which I could test my Z80 cartridge:

- ASSY-NO.250407 / ARTWORK-NO.251137 / REV.B
- ASSY-NO.250407 / ARTWORK-NO.251137 / REV.C
- ASSY-NO.250469 / PCB-NO.252311 / REV.4
- ASSY-NO.250469 / PCB-NO.252311 / REV.B
- SX-64 (I would have to unscrew it to check the revision)

(All PAL models)

I have changed the dependencies of the signals in some places, so that the VIC and the Z80 card should not get in each other's way. I also didn't use a counter for the waitstates, but determine in which cycle the Z80 is currently and then set the corresponding waitstates depending on the VIC. 

This has increased the stability enormously. Also now the version/revision of the VIC seems to play no role. At least I couldn't find any difference in the stability of my different versions.



## Assembly



There is actually not much to consider when assembling. First I would solder the XIlinx CPLD. Then the voltage regulator, followed by the SMD capacitors.

The rest of the other parts can then be applied from small to large. So the capacitors first, then the ferrite beads and then the 40 pin IC socket. At the end then the electrolytic capacitor. It is probably more practical to mount it horizontally, because it is comparatively high and could be torn off quickly.



## Flash firmware

The firmware is available as JED file. This can be flashed with a JTAG programming adapter.

The easiest way is to use the tool "xc3sprog" and a small FT232H adapter board. You can get the latter for a small amount of money.

A very well described tutorial how to do this can be found here: https://github.com/1c3d1v3r/neatPLA/tree/master/programming

The pinout of the JTAG connector of my board is on the backside.

![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_JTAG.jpg)



I would not solder a male or female header here. For the short flash process it is sufficient to simply insert the small Dupont connectors of the FT232H board into the solder contacts and hold them slightly tilted.

Once the firmware has been installed, the cartridge is ready for use.



## CP/M Disk

My Z80 cartridge uses the same CP/M system disk as the original module from Commodore. I have a D64 image of the standard system disk in the repository.

Otherwise, http://biosrhythm.com/?p=1220 is a good place to go for more disk images, which include Wordstar, Turbo Pascal, Zork and some other CP/M programs.

On these images a software emulation for 80 characters is also integrated. This does not replace a real 80 character card as hardware, but it is much more fun than with the standard 40 characters of the C64.

But you can find some other tools and programs on the internet. 



## Parts list

Many parts are not needed for this project. So far I had tested the card only with the NMOS version of the Z80 (The CMOS version is ordered, but has not been delivered yet). 

| #    | Quantity | Designator                 | Manufacturer | Manufacturer Part Number | Description                                                  |
| ---- | -------- | -------------------------- | ------------ | ------------------------ | ------------------------------------------------------------ |
| 1    | 6        | FB1 - FB6                  | Fair-Rite    | 2743005112               | Ferrite Beads  Axial 91Ohm 100MHz T/R                        |
| 2    | 6        | C2, C3, C10, C13, C14, C15 | KEMET        | C315C100J3G5TA           | CAP  CER 10PF 25V C0G/NP0 RADIAL                             |
| 3    | 6        | C4, C5, C6, C7, C8, C9     | KEMET        | C0603C104J3RACTU         | KEMET     C0603C104J3RACTU       SMD Multilayer Ceramic  Capacitor, 0603 [1608 Metric], 0.1 F, 25 V,   5%, X7R, C Series |
| 4    | 2        | C16, C17                   | KEMET        | C0805C106K8RACTU         | KEMET  - C0805C106K8RACTU - CAP, 10µF, 10V, 10%, X7R, 0805   |
| 5    | 1        | C1                         | KEMET        | C320C104K5R5TA7305       | Ceramic Disc  Capacitors 100nF -20%~+80% 50V Through Hole,P=2.54mm RoHS |
| 6    | 1        | U5                         | Exar         | SPX5205M5-L-3-3/TR       | LDO Regulator  Pos 3.3V 0.15A 5-Pin SOT-23 T/R               |
| 7    | 1        | CP1                        | Nichicon     | UMF1C470MDD1TP           | Aluminum  Electrolytic Capacitors - Leaded 47uF 105c         |
| 8    | 1        | U1                         | Xilinx       | XC95144XL-7TQ100C        | IC CPLD 144MC  7.5NS 100TQFP                                 |
| 9    | 1        | U2                         | Ixys  Zilog  | Z84000HPS                | IC  CPU Z80 8MHZ 40DIP                                       |



# Status

### Status as of 16 March 2021

I have decided to start an open beta phase. I have published everything necessary to build the map. Currently the version is 0.3. 

There is a kind of discussion board at GitHub by now. You can find it in the menu bar at the top of this project.

Perhaps this could be used for suggestions and questions, while the Issues section is reserved for bug reports.

For this board I had the fun to work a little bit on the design and to add the lettering CP/M to the board. 

I would be interested if others like this or if I should make a "normal" board without any embellishments. 

I would be particularly interested to know on which hardware you test. So which board, revision, kernal, any conversions, etc.? The more feedback, the better. 



------

### Old entries

### Status as of 15 March 2021

Today I made a small breakthrough. I now have the firmware in a fairly stable state. First tests look very good so far. 



![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_first_alpha_release.jpg)



I have tested so far in an old 407 board, as well as a C64G with 469 board. Also with original DOS, SpeedDOS and JiffyDOS. With the original DOS it is not so much fun, because the loading is very slow, but with a floppy speeder it works very well.

The Z80 runs with the DOT CLK frequency of the C64, which is about 8MHz. So far I have only tested on PAL machines (I don't have an NTSC version). Theoretically this shouldn't make any difference, at least I hope so.

For testing I have mainly used a small Pascal program which calculates the Mandelbrot set. I compiled this with Turbo Pascal 3.01 under CP/M:

By the way, you can see a clear difference between the original Commodore module and my version. 



![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_Mandelbrot.jpg)



I think sooner or later we will do a first beta test...



### Status as of 12 March 2021

Since I've always wanted to experiment with more unusual PCB outlines, I tried my hand at something like this:



![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_design_pcb.jpg)



Is there any interest in something like this? So that on circuit boards so small gags are attached? 



### Status as of 06 March 2021

Today I built the whole thing on a real board.

![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/z80-card-first_pcb.jpg)



Don't be surprised that there are still unpopulated components. They are no longer needed. Everything is now in the CPLD.

Yesterday I was still thinking whether the 8MHz mode makes sense at all. Today I ask myself, why I still tinker at the 4MHz mode or if necessary install both.

Is actually nonsense. The 8MHz mode doesn't speed up the load times and access to the RAM in the C64 (because of the bottleneck expansion port and RAM), but as far as pure CPU work is concerned, the whole thing is much faster.

And whether 4MHz or 8MHz, the CP/M version doesn't change. Also the user must consider there nothing or configure.

Therefore I will stop the work on the 4MHz version and concentrate on the 8MHz version.

The current status looks like that, that everything works so far. Also actually quite stable. Very rarely the boot does not work directly at the first time. 

Currently I still have the problem that he sometimes messes with the waitstates. I still have to work on the routine. But the rest looks so far already quite good.



### Status as of 05 March 2021

Meanwhile the 4MHz mode runs quite stable. Now and then it hangs when booting. However, the boards have not arrived yet, so I am still testing on my breadboard model.

The 8MHz mode I would see times so 90%. There are still some minor problems here and there. But basically it works.

Today I compiled an old Pascal program for the Mandelbrot set and ran it on 4MHZ and 8MHz. 

While you don't feel any difference when loading programs (booting takes 9-10 seconds with JiffyDOS at 4, as well as 8MHz) there are differences in mathematical calculations.

With the 4MHz version, a run takes just under 7 minutes and 16 seconds (measured with the smartphone). In the 8MHz mode, it then only took 3 minutes and 58 seconds. 

I'll see if I can install both modes, possibly with DIP switch switchable or so.



### Status as of 03 March 2021

In the meantime the whole thing runs quite stable, at least as long as it is worked with. I have now provided an additional 50MHz oscillator to make the cycling more accurate.

The boot process seems to be stable, at least I couldn't detect any problems there so far.

As long as you work with the CP/M, there seems to be no more problems.

Only if the CP/M has nothing to do, then it crashes abruptly sometimes. Unfortunately not predictable, concerning the time. This makes the search a bit more difficult. But I am in good hope to find this bug as well.

First attempts with the 8MHZ mode look quite successful, but a real speed increase in normal operation is not felt. The main problem is that the communication with the C64 (i.e. RAM, floppy, etc) is still subject to the C64 conventions. The Z80 therefore has to wait most of the time.

Currently the whole thing runs at 4MHz, just like the original module. If you use SpeedDOS, JiffyDOS or a comparable floppy speeder, the loading times are quite bearable.



### Status as of 22 February 2021

For now, I have developed and ordered a circuit board. With it I hope to get the signal problems under control. After that I can continue with the CPLD code development.

![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_PCB_Prototype.jpg)

Then, when the card is running stable, the next step is tuning. The goal should be to run the card at a higher clock rate. The Z80 CPU could run 8MHZ. Let's see if this can be implemented cleanly. 

Since the C64 doesn't have the cleanest timing, and this differs slightly from model to model, it's not so easy to find a happy medium.

By the way, I cannot confirm the assumption that the problems with CP/M are due to the VIC. I have tried various VICs in a 407 board and always got an original Commodore CP/M cartridge running.

Also I have by exchange of different TTL components against other types (S or LS against ALS or HCT, etc.) in the Cartridge the module even in a 469er board to run brought. Even the manufacturer of the respective component has a partial influence on it. 

But which VIC was in use, apparently played no role. It seems to be rather minimal timing differences that play a role, but they are extremely tiny.



### First Entry

I have already created a first prototype on a breadboard with a CPLD. I put a small DevBoard piggyback on the breadboard. I soldered the whole thing with enamelled copper wire.

![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_first_prototype_1.jpg)



![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_first_prototype_2.jpg)



The whole thing is unfortunately not perfect and of course I have some signal problems because of the "flying wiring". But at least I could run the board with 2MHz. It doesn't run perfectly yet and I still have to work on some timings.

But an original Commodore CP/M 2.2 can be booted. And it works so far, even if not quite stable yet. But it even runs in newer Commodore models, which is not possible with the old original CP/M cartridge from Commodore.

![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_first_prototype_3.jpg)

------



If you liked my project, I would be very happy about a small coffee donation.

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/R6R62T6RN)





# License

The contents of this repository, with the exception of the Docs and Software directories, are released under the following license:

- the "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License" (CC BY-NC-SA 4.0) full text of this license is included in the [LICENSE.CC-NC-BY-SA-4.0](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/LICENSE.CC-NC-BY-SA) file and a copy can also be found at https://creativecommons.org/licenses/by-nc-sa/4.0/
