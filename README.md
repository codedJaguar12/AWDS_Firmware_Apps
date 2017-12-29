# Automated-Water-Distribution-System

Note: AWDS needs to link your AADHAR cards so that a better management of the water supply to area can be done.


## PLATFORM REQUIRED
* Linux 64 bit , Windows 7 SP1/8/8.1/10 64 Bit
* Android SDK
* iOS SDK
* Windows Phone 8.1/10 SDK
* Apache Cordova
* arm-g++-linux-eabi (ARM Cross Compiler for Debian Jessie)
* Apache Server with PHP 5.4 support
* Atmel Studio 7
* Avrdude command line tool
* Domain name + Hosting

## COMPILING FIRMWARE FOR DEVICE 
* Install the Atmel Studio 7 then import or open the Firmware in the Project Folder as follows:

![Atmel Studio](/screenshots/atmel_studio.png) 

![compilation successfull](/screenshots/compile_success.png)

* Above will be displayed when we will build the solution, to build the “Firmware Project” press F7.

| - | - |
|---|---|
| ![compilation successfull](/screenshots/file_tree.png) | 

    * Check the file sketch_nov27.hex then burn it to device using avrdude command line utility. 
    * Other files with same name are files for recording eeprom data on to the chip. 
    * Dependencies contain standard prototypes for eeprom read, eeprom write and eeprom clear. 
    * Dependencies also contain standard prototypes for interrupt in software mode and also external interrupts. 
    * Entire firmware size should be less than 256KB in case if modified in future. 
    * EEPROM is only 4KB so needs to be erased periodically for making space on device.

|

## Command Line via avrdude (Linux)

avrdude -v -p atmega2560 -c arduino -P /dev/ttyUSB0 -b 57600 -D -U flash:w: sketch_nov27.hex:i

1. -b This option sets the baud rate for communicating with the board
2. -p This specifies the target type. The configuration file for avrdude has a long list of supported targets, with all the important parameters for each. 
3. -P Specifies the communication port. As soon as the device is hooked up to your USB, it should be assigned a file in /dev/, and this is the string that needs to be passed to the -P option. The easiest way to find this is just
dmesg | grep ttyUSB*

## Command Line via avrdude (Windows)

avrdude -v -p -c arduino -P .COMxx -b 57600 -D -U flash:w: sketch_nov27.hex:i

where COMxx is port no. eg. COM34

## How to build app

On command line do following

$ cordova create <app_name>

$ cd <app_name>

$ cordova build


## Please edit config.xml for this application

Below is a config.xml file, fill in your domain/server address on which app is hosted:
```
<?xml version='1.0' encoding='utf-8'?>
<widget id="io.cordova.iot" version="0.0.1" xmlns="http://www.w3.org/ns/widgets" xmlns:cdv="http://cordova.apache.org/ns/1.0">
  <name>IOTone</name>
  <description>
An IOT app
  </description>
  <author email="rohanverma2@acm.org" ">
IOTone team
  </author>
  <content src=”<YOUR_DOMAIN_NAME_ON_WHICH_APP_IS_HOSTED>” />
  <plugin name="cordova-plugin-whitelist" spec="1" />
  <access origin="*" />
  <allow-intent href="http://*/*" />
  <allow-intent href="https://*/*" />
  <allow-intent href="tel:*" />
  <allow-intent href="sms:*" />
  <allow-intent href="mailto:*" />
  <allow-intent href="geo:*" />
  <platform name="android">
      <allow-intent href="market:*" />
  </platform>
  <platform name="ios">
      <allow-intent href="itms:*" />
      <allow-intent href="itms-apps:*" />
  </platform>
</widget>
```


