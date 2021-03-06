# Z80-Card for Commodore C64

I'm currently working on a Z80 card for the Commodore C64 to be able to use CP/M 2.2. The whole thing is based on a CPLD and a Z80 processor.



## Introduction

I have already created a first prototype on a breadboard with a CPLD. I put a small DevBoard piggyback on the breadboard. I soldered the whole thing with enamelled copper wire.

![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_first_prototype_1.jpg)



![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_first_prototype_2.jpg)



The whole thing is unfortunately not perfect and of course I have some signal problems because of the "flying wiring". But at least I could run the board with 2MHz. It doesn't run perfectly yet and I still have to work on some timings.

But an original Commodore CP/M 2.2 can be booted. And it works so far, even if not quite stable yet. But it even runs in newer Commodore models, which is not possible with the old original CP/M cartridge from Commodore.

![](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/Images/Z80-Card_first_prototype_3.jpg)



## Status

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



------

### Old entries

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



------



If you liked my project, I would be very happy about a small coffee donation.

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/R6R62T6RN)





# License

The contents of this repository, with the exception of the Docs and Software directories, are released under the following license:

- the "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License" (CC BY-NC-SA 4.0) full text of this license is included in the [LICENSE.CC-NC-BY-SA-4.0](https://github.com/DL2DW/Z80-Card_for_Commodore_C64/blob/main/LICENSE.CC-NC-BY-SA) file and a copy can also be found at https://creativecommons.org/licenses/by-nc-sa/4.0/
