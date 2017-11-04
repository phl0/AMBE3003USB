# AMBE3003USB

This is a homebrew evaluation board for AMBE-3000 and AMBE-3003 Chips. It can be used as a replacement for USB-3003 devices to work as a transcoder for [XLX](https://github.com/LX3JL/xlxd) reflectors. This board is supported by the AMBEd daemon from version 1.2 onwards.

## Version 1.0

This is the initial version. Apparently it has two errors: The power supply is faulty due to R42 being to small in value. Bypassing the resistor works basically. The 1v9 rail draws to much power resulting in U5 running hot. 
The second issue is that this revision does not support hardware reset of the AMBE-3003 CPU. Soft reset does not work 100% reliably. In this case only un- and re-plugging the device works.

*This version is not recommended for (re-)production!*

## Version 1.1

The power supply has been redesigned. An additional transistor has been added to allow for a hardware reset using the DTR pin of the FT-232RL. This needs code changes in the XLX code. Additionally there have been added some more pins to the pin header that allow for configuring parity for AMBE-3000 chips by jumper.

This version is currently under test and will be merged into the master branch when testing the boards reveals success.

# Usage

## Flashing FT232

After building the board you have to flash the onboard FT-232 USB converter. The AMBEd expects to find this device with product ID "DF2ET-3003". The product ID can be flashed with the original FTprog by FTDI or using [ft232r_prog](http://rtr.ca/ft232r/) (command is ./ft232r_prog --product "DF2ET2-3003").

## Setting Jumpers

* VSET has to be set to 1v9 for an AMBE-3003 chip (1v8 for AMBE-3000).
* SEQ needs to be LDO2, LDO1
* PARITY_ENABLE is ignored by an AMBE-3003 (disabled for AMBE-3000)
* IF_SELECT has to be set to UART (being IF_SELECT0 and IF_SELECT2 enabled, IF_SELECT1 disabled)
* DTX_ENABLE disabled
* NS_ENABLE disabled
* CP_ENABLE disabled
* CP_SELECT disabled
* SCOM_RATE has to be configured for 921,600 bit/s (which is SCOM_RATE0 and SCOM_RATE2 enabled, SCOM_RATE1 disabled)
* RATE settings are ignored in UART mode. No need for jumpers though

* HARD_RESET can be enabled by setting J5. Otherwise the code relies on a software reset only

* SK_ENABLE not used by AMBE-3003
* ES_ENABLE not used by AMBE-3003
* EC_ENABLE not used by AMBE-3003

## Drivers

If using in combination with XLX/AMBEd make sure that the operating system does not load the commonly used ftdi_sio kernel module to provide an USB-serial interface. The AMBEd makes use of the ft2xx direct access driver by FTDI with does not work if the kernel module is loaded. Hints on how this can be accomplished can be found in my [Blog](https://www.florian-wolters.de/blog/2017/08/18/excluding-ft-232-from-ftdi-sio-driver/).

# Contributors

This is the list of contributors. Thank you for your additions:

* Mathis, DB9MAT
