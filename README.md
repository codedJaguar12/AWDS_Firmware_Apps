# Automated-Water-Distribution-System-Interface

AWDS is a IOT project which provides to regulates the water suply to homes, the process to install the system is simple a dedicated hardware ( soon available at my other repository)  is installed at the water output to the house.The project is IOT based so an android app is also available , one for Customer and other one for Office.

AWDS needs to link your AADHAR cards so that a better management of the water supply to area can be done.


## PLATFORM REQUIRED
* Linux 64 bit / Windows 7 SP1/8/8.1/10 64 Bit
* Android SDK
* iOS SDK
* Windows Phone 8.1/10 SDK
* Apache Cordova
* arm-g++-linux-eabi (ARM Cross Compiler for Debian Jessie)
* Apache Server with PHP 5.4 support
* PHP 5 with memcache support
* Atmel Studio 6 / 7
* Avrdude command line tool
* Domain name + Hosting

## COMPILING FIRMWARE FOR DEVICE 
* Install the Atmel Studio 7 then import or open the Firmware in the Project Folder as follows:

![alt_text](/screenshots/atmel_studio.png) 

![alt_text](/screenshots/compile_success.png)

* Above will be displayed when we will build the solution, to build the “Firmware Project” press F7.

![alt_text](/screenshots/file_tree.png)

* Check the file sketch_nov27.hex then burn it to device using avrdude command line utility
* Other files with same name are files for recording eeprom data on to the chip.
* Dependencies contain standard prototypes for eeprom read, eeprom write and eeprom clear.
* Dependencies also contain standard prototypes for interrupt in software mode and also external interrupts.
* Entire firmware size should be less than 256KB in case if modified in future.
* EEPROM is only 4KB so needs to be erased periodically for making space on device.


 
## Command Line via avrdude (Linux)

avrdude -v -p atmega2560 -c arduino -P /dev/ttyUSB0 -b 57600 -D -U flash:w: sketch_nov27.hex:i

1. -b This option sets the baud rate for communicating with the board
2. -p This specifies the target type. The configuration file for avrdude has a long list of supported targets, with all the important parameters for each. 
3. -P Specifies the communication port. As soon as the device is hooked up to your USB, it should be assigned a file in /dev/, and this is the string that needs to be passed to the -P option. The easiest way to find this is just
dmesg | grep ttyUSB*

## Command Line via avrdude (Windows)
avrdude -v -p -c arduino -P .COMxx -b 57600 -D -U flash:w: sketch_nov27.hex:i

where COMxx is port no. eg. COM34
