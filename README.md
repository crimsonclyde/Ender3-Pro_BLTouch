# Ender3-Pro_BLTouch

!Do this on your own risk! I do not take responsibility. This is to find a way not the ultimate solution!

### Config for Ender3-Pro

* SKR Mini E3 V1.2
* BigTreeTec TFT35
* BLTouch (Creality)

BLTouch probe cabel is connected to Z-Endstop.
BLTouch power and signal is connected to "SERVOS" socket on SKR.

It is important to change the connectors to the board specifications.

Cable Color Code:
Yellow = Signal
Blue   = GND
Red    = VCC (5V)


### Know Problems:

* Steppers are getting hot
 70° Celsius.

### Manual sequenz to level BLTouch:

M502			// Factory Reset (last known firmware
M501			// Restore Settings
M500			// Save
G28			// Home the nozzle
M851 Z0			// Set the Z-Offset to Zero
M500			// Store settings to EEPROM
M501			// Load settings from EEPROM
M851			// Echo the current Z-Offset value. Z should be 0!
G28 X Y			// Home X and Y axis
G28 Z			// Home Z axis
G1 F60 Z0		// Move the nozzle down to the Z0
M211 S0			// Turn OFF the software endstop. Needs to be done to be able to make negative steps

Now use Marlin3DPrinterTool to lower the nozzle with 0.1mm steps just like with paper until the nozzle scratches very softly the paper.
Next, on your display you have a Z value mine was -2.5 this is the one we need to set now as the offset.

M851 Z-2.5		// Set the Z-Offset value
M211 S1			// Turn on the software endstops (security)
M500			// Store Settings
M501			// Load settings


### Update Ultimaker Cura

Open Printer -> Machine Settings -> Add a "G29" after "G28"
G29 is automatic bed leveling. No ""!

### Helpful articles:

* https://letsprint3d.net/guide-how-to-calibrate-an-auto-bed-leveling-sensor/
* https://locxess.de/3d/BLTouch_Anleitung_englisch.pdf
* https://github.com/bigtreetech/BIGTREETECH-SKR-mini-E3/tree/master/firmware/V1.2
