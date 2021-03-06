# ZevaMonitorV3_SevconGen4

This project is based on the now open source Zeva EVMS Monitor V3 from Ian Hooper. It has an MIT license as does Ian's original source.

It retains all the existing EVMS Monitor V3 features, and adds an additional screen for monitoring live parameters from a Sevcon Gen 4 controller.

- Motor Temp
- Motor RPM
- Controller Temp
- Velocity
- Phase Amps
- ...

To build:

Install avr-gcc

From the Firmware directory, run 'make all'. The makefile supports 'make all', 'make clean', and 'make flash'


Status:

 WIP


ZEVA EVMS Monitor V3
  Ian Hooper, August 2021

This archive contains all the files needed to reproduce the ZEVA EVMS Monitor V3, a touchscreen interface device for the EVMS3. Files are provided under the open source MIT license, found at the end of this file. The short version is that you may use these files for any purpose, free of charge, but they don’t come with any warranty or support.

PCB and schematic (.sch) files can be opened in Autodesk Eagle. If you don’t need to modify the design, the Gerber files in the PCB Assembly folder can be sent as-is to a PCB manufacturer to get boards made. Files for PCB assembly are also included, such as a Bill of Materials, centroid files (for pick-and-place machines), and example photos for reference. Parts in the Eagle file may not match the BoM in some cases. If in doubt, trust the BoM.

The LCD panels can be purchased off Alibaba or AliExpress - just search for “3.2 TFT LCD”, and look for pictures that match the example supplied with this download. Some example vendors are TZT, YTF, EQV, HESAI, Roarkit.

The firmware is written is C and can be compiled using AVR-GCC, normally using an IDE such as AVR / Microchip Studio. No claims are made about the quality or readability of the code. (This Monitor code in particular may be a bit of an impenetrable monolith if you’re not familiar with it - my apologies.) A precompiled HEX file is also supplied, which can be loaded onto boards as-is if standard firmware is suitable.

You will need an AVRISP type programming device for transferring firmware to the board, such as AVRISP MK2, STK500 or USBASP. The programming port on the PCB is a row of 5 holes near the microcontroller, with pin order GND, MOSI, MISO, SCK, RESET (with GND end marked). It is different to the usual 3x2 or 5x2 pin port used by AVRISP programmers, so you will need to make an adapter using 5 wires and some 0.1” pin header. Normally the 5x1 pin header can be pressed against the PCB holes during programming (avoids the need to add any connector to the board). The board will need to be powered during programming via 12V supplied to the CAN bus port.

AVR microcontrollers use “fuses” for setting things like the clock speed and brownout detection. The required fuse settings are listed near the top of the C code file.

There is a PCB support bracket that should be 3D printed, which gets fitted between the LCD module and the control board, and fastened to the control board using an M3x6 machine screw. Then the control board can be soldered to the 34x interface pins on the LCD module to complete the internal assembly. There are two housing options supplied, one panel mount which gets attached to the assembly using 4x M3x10 machine screws, or an enclosed housing with foot which gets screwed together using 4x M3x16 countersunk machine screws, and the foot can be attached using an M3x20 machine screw plus M3 nyloc nut. The mating connector for the CAN bus port is Molex 39500-0005. Remember to also fit jumpers to the two 2-pin headers either side of the CAN port, for the CAN termination resistor and to disable settings lock.

Once assembled and programmed, the EVMS Monitor should be ready to use. Please review the EVMS3 user manual for further information about installation and operation.
