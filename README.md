# AMBE3003USB

This is a homebrew evaluation board for AMBE3000 and AMBE3003 Chips. It can be used as a replacement for USB-3003 devices to work as a transcoder for [XLX](https://github.com/LX3JL/xlxd) reflectors.

## Version 1.0

This is the initial version. Apparently it has two errors: The power supply is faulty due to R42 being to small in value. Bypassing the resistor works basically. The 1v9 rail draws to much power resulting in U5 running hot. 
The second issue is that this revision does not support hardware reset of the AMBE3003 CPU. Soft reset does not work 100% reliably. In this case only un- and re-plugging the device works.

*This version is not recommended for (re-)production!*

## Version 1.1

The power supply has been redesigned. An additional transistor has been added to allow for a hardware reset using the DTR pin of the FT-232RL. This needs code changes in the XLX code. Additionally there have been added some more pins to the pin header that allow for configuring parity for AMBE3000 chips by jumper.

This version is currently under test and will be merged into the master branch when testing the boards reveals success.

# Contributors

This is the list of contributors. Thank you for your additions:

* Mathis, DB9MAT
