# pcb_redesign

AeroJudge PCB redesign to combine boards and third party sub boards.

The project is a conglomeration of parts that needs to be reworked and redesigned into ONE functional hat PCB for raspberry Pi4 use. 
the board size can grow to a larger footprint (dimensions TB) as needed to fit all these components. and could have components on both sides if needed, although no wired cnnections should be on the underside. 

on the main board 
- remove ENC 1 (keep ENC2)
- remove GPIO16, GPIO12, GPIO23, GPIO18
- remove all I2c conec

On the powerbord, we are using three sub boards mounted to this which is a pain!
the three boards are - 


The solder pads for the battery conection should be replaced with an appriate DC power connector / plug

* the power regular has a manual voltage settign and is not optimal for the final design - it can be completely replaced or redesigned for RPi4 with 5.1v DC and 4A output capabilities.
* Options for ideas are to clone the pololu 

these should be redesigned and consolidated to the main board - no sub assemblies - just one PCB that can be built as one part. such as using JLPCB-A.

