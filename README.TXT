----------------------------------------------------------------------------
ROM board for Atari STM
(c)2020, Anders Granlund
----------------------------------------------------------------------------
Tested on a C070243 Rev.I motherboard, your mileage may vary.
----------------------------------------------------------------------------

This board does not perform TOS2.x decoding but it has provisions to hook
it up to an external decoder.

pin CEO is the original chip select output
pin CEI is chip select input from external decoder

Bridge the CEO/CEI pins if you're not using an external TOS decoder.


----------------------------------------------------------------------------
TOS select header
----------------------------------------------------------------------------
The leftmost pin header can be used to select TOS when using EEPROMs big
enough to fit multiple TOSs on them.

Upper two pins controls A18 and the lower two controls A19.
Jumper to pull the signal low.

For example:
39SF010 fits one TOS (A18+A19 are ignored)
39SF020 fits two TOS's (A18 is used to select, A19 is ignored)
39SF040 fits four TOS's (both A18 and A19 are used to select)


----------------------------------------------------------------------------
ROM size mode:
----------------------------------------------------------------------------
If your motherboard has the 256K/1M rom size jumpers and has already been
adjusted to work in 1M mode then you need only to bridge the three
solder jumpers on the rom board to the 1M position.

If the motherboard is in 256K mode, or if it lacks rom jumpers,
then you need to do the following:
- Bridge the three solder jumpers to the 256K position.
- Fit the 74LS11
- Fit the 100nF capacitor next to the 74LS11
- Solder wires from A16+A17 from the CPU to the A16+A17 headers
  on the rom board.


----------------------------------------------------------------------------
Realtime clock:
----------------------------------------------------------------------------
It takes a Dallas DS1315 chip and drivers can be found here:
https://github.com/agranlund/rtc

If you don't fit the DS1315 you need to bridge the "disable"
solder jumper.



----------------------------------------------------------------------------
BOM:
----------------------------------------------------------------------------
- Pin headers and sockets
- R1+R2: pullup resistors. The value is not terribly important, I used 3K3's

- Dallas DS1315 realtime clock
- 32.768Khz occilator for DS1315
- C1: 100nf capacitor for DS1315
- Battery holder for DS1315. I am using this one:
https://www.electrokit.com/en/product/battery-holder-cr2016-2025-2032-plastic/

- 74LS11N for motherboards in 256K mode
- C2: 100nf capacitor 74LS11N



