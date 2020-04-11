# Ender3-Pro_BLTouch

!!!!! DONT USE !!!!!
STEPPERS OVERHEATING >100°C


!Do this on your own risk! I do not take responsibility. This is to find a way not the ultimate solution!

### Ender3-Pro Hardware Mod List

* SKR Mini E3 V1.2
* BigTreeTec TFT35
* BLTouch (Creality)

### BLTouch Setup
BLTouch probe cabel is connected to Z-Endstop.
BLTouch power and signal is connected to "SERVOS" socket on SKR.
It is important to change the connectors to your board specifications!

Cable Color Code on my BLTouch from Creality was:
Yellow = Signal
Blue   = GND
Red    = VCC (5V)

### Know Problems:

* Steppers are getting hot
 70° Celsius.

### Manual sequenz to level BLTouch:

|GCODE   | Description   |
|---|---|
|M502|Factory Reset (last known firmware)|
|M501|Restore Settings|
|M500|Save to EEPROM |
|G28 | Home the nozzle |
|M851 Z0|Set the Z-Offset to Zero|
|M500|Save to EEPROM |
|M501|Restore Settings|
|M851|Echo the current Z-Offset value. Z should be 0!|
|G28 X Y|Home X and Y axes (needed in Pronterface not in Marlin3DPrinterTool)|
|G28 Z|Home Z axis|
|G1 F60 Z0|Move the nozzle down to the Z0|
|M211 S0|Turn OFF the software endstop. Needs to be done to be able to make negative steps|

Now a two manuel steps:

1. Lower the nozzle manual  
   0.1mm steps! Be careful!  
   You can do this directly with your printer or with Marlin3DPrinterTool or Pronterface
   Same process like it is with manuel bed leveling, move down until the nozzle gently scratches the paper.
2. Note the Z value  
   Should be negative like -0.5


|GCODE| Description|
|---|---|
|M851 Z-2.5|Set the Z-Offset value|
|M211 S1|Turn software endstops back on (Don't forget this! To not crash your nozzle into the bed)|
|M502|Factory Reset (last known firmware)|
|M501|Restore Settings|



### Update Ultimaker Cura

Open Printer -> Machine Settings -> Add a "G29" after "G28"
G29 is automatic bed leveling. No ""!

### Helpful articles:

* https://letsprint3d.net/guide-how-to-calibrate-an-auto-bed-leveling-sensor/
* https://locxess.de/3d/BLTouch_Anleitung_englisch.pdf
* https://github.com/bigtreetech/BIGTREETECH-SKR-mini-E3/tree/master/firmware/V1.2
