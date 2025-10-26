# pcb_redesign

AeroJudge PCB redesign to combine boards and third party sub boards.

The project is a conglomeration of parts that needs to be reworked and redesigned into ONE functional hat PCB for raspberry Pi4 use. 
the board size can grow to a larger footprint (dimensions TB) as needed to fit all these components. and could have components on both sides if needed, although no wired cnnections should be on the underside. 

on the main board 
- remove ENC 1 (keep ENC2)
- remove GPIO16, GPIO12, GPIO23, GPIO18
- remove all I2c conectors, only 12c-1 was in use and that will now all be on the pcb
- remove the pads on the backside for poweroff select and shutdown select - those will be direct to GPIO24 and GPIO25 (as was connected by a trace)


On the powerbord, we are using three sub boards mounted to this which is a pain!
the three boards are - 
  - INA226_Sensor
  - Pololu 2810 Switch (see additianl PDF to simplify this circuit)
  - Voltage Regulator* See note below
The solder pads for the battery in conection should be replaced with an appriate DC power connector / plug

* the cuurent power regular has a manual voltage settign and is not optimal for the final design - it can be completely replaced or redesigned for RPi4 with 5.1v DC and 3+Amp output capabilities.
* Options for ideas are to clone the pololu 4892 (5V, 3.4A Step-Down Voltage Regulator D30V30F) or create a similar regulator

these should be redesigned and consolidated to the main board - no sub assemblies - just one PCB that can be built as one part. such as using JLPCB-A.

The LED connector should also be duplicated with a connector for a 3v3 LED so that i could use either. 

Of course the other connectors (i2c, power/shutoff, and 5v batt) all go away as they bomcome traces on the new single board)


New Main (single) board will have aerojudge logo, website link and be marked as board rev 3.0 - Size can be adjusted as needed. 
Imac logo on rear can stay if it fits somewhere but is not important. 

All plugs are 90 degree connectors as there is not room in the case (without a redesign) for components to be much taller than the 5mm connector height. The case can be redesgined if necessary. 
