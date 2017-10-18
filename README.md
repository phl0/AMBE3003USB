# AMBE3003USB

This is a homebrew evaluation board for AMBE3000 and AMBE3003 Chips. It can be used as a replacement for USB-3003 devices to work as a transcoder for [XLX](https://github.com/LX3JL/xlxd) reflectors.

## Version 1.0

This is the initial version. Apparently it has two errors: The power supply is faulty due to R42 being to small in value. Bypassing the resistor works basically. The 1v9 rail draws to much power resulting in U5 running hot. 
The second issue is that this revision does not support hardware reset of the AMBE3003 CPU. Soft reset does not work 100% reliably. In this case only un- and re-plugging the device works.

*This version is not recommended for (re-)production!*

## Version 1.1

The power supply has been redesigned. An additional transistor has been added to allow for a hardware reset using the DTR pin of the FT-232RL. This needs code changes in the XLX code. Additionally there have been added some more pins to the pin header that allow for configuring parity for AMBE3000 chips by jumper.

Testing this version revealed an issue with missing pull-up resistor on the PWREN signal. That results in the voltage regulator not beeing activated. Quick fix is to add a 10k SMD resistor from bottom pin of R4 to anode of C5 (5v0). This is going to be fixed in revision 1.2.

*This version is not recommended for (re-)production!*

## Version 1.2

A 10k resistor (R22) was added to the schematics and board layout. 

This version has not been tested yet. Use at your own risk.

# Contributors

This is the list of contributors. Thank you for your additions:

* Mathis, DB9MAT

# License

This project is released under the Creative Commons Attribution-NonCommercial-ShareAlike 3.0 (CC-BY-NC-SA 3.0, https://creativecommons.org/licenses/by-nc-sa/3.0/) license. You may edit and share it as you like, as long as credit is given and the license is not changed. You can build as many boards for you and your friends as you like and you can even sell it to them to cover your costs, **however it is strictly forbidden to turn this into a commercial product! You are not allowed to build and sell these boards for profit!**
