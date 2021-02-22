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
