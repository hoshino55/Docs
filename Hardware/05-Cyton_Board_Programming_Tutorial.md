#Cyton Board Programming Tutorial

##Overview
The OpenBCI Cyton boards have powerful microcontrollers on them which ship with the latest OpenBCI firmware to interface with the on-board ADS1299, Accelerometer, and SD card. This tutorial explains how to program the firmware using the OpenBCI Dongle and you PC. If we come out with a firmware upgrade, or if your or someone comes up with a custom program, you should use the following method.


## Firmware Version 2.x.x (Fall 2016)
**You will need:**

* Computer running [Arduino v1.8.0](https://www.arduino.cc/en/Main/Software) or later
* OpenBCI Dongle connected to USB port
* OpenBCI Cyton Board with battery power

![OpenBCI Dongle](../assets/images/dongleConnection.png)

***Note***: Always plug the Dongle into the PC before powering the Board because the Host (RFduino on the Dongle) must be powered before the Device (RFduino on the Board).

1. install the Arduino IDE which can be found here:

		https://www.arduino.cc/en/Main/Software

**Note for Windows users** While installing Arduino 1.8, if the installer instructs you to uninstall 1.5.8, move the Arduino folder containing 1.5.8 from `Program Files (x86)` to your downloads folder. Rename this folder to `Arduino_1.5.8`. Open the `Change or remove program` app in control panel and uninstall the Arduino application. There will be a popup indicating that the files do not exist and asking if you want to remove the program from the files list, select yes. Then install 1.8.0 as normal. Navigate to back to your `Program Files (x86)` folder and locate the Arduino folder. Rename this folder to `Arduino_1.8.0`. Now drag and drop the `Arduino_1.5.8` back into `Program Files (x86)` folder.  

2. Download the [OpenBCI_32bit_Library Firmware](https://github.com/OpenBCI/OpenBCI_32bit_Library/tree/master) repo from our github.

3. Unzip the folder, and if it is named `OpenBCI_32bit_Library-master`, rename it to just `OpenBCI_32bit_Library`.

4. Now move the `OpenBCI_32bit_Library` folder from your downloads into:

  On Mac:
Documents/Arduino/libraries
  On Windows:
C:\Users\username\Documents\Arduino\libraries

If there is no 'libraries' folder in the sketch folder, create one.

5. Download the [OpenBCI_32bit_SD](https://github.com/OpenBCI/OpenBCI_32bit_SD/archive/master.zip) repo from our github.

6. Unzip the folder.

7. Now move the folder called `OBCI32_SD` and everything it contains to:

  On Mac:
/Documents/Arduino/libraries
  On Windows:
C:\Users\username\Documents\Arduino\libraries


8. Before you can upload code correctly to the PIC32 with Arduino, you need to add the chipKIT-core board files to your Arduino IDE. The folks at chipKIT have put together instructions on how to [Auto Install via URL from within Arduino](http://chipkit.net/wiki/index.php?title=ChipKIT_core#1.29_Auto_install_via_URL_from_within_Arduino_IDE_.28latest_version_chipKIT-core_v1.3.1.29). Follow the process in the previous link, and you will be able to select the OpenBCI board from the Tools >> Board >> dropdown menu!

![board_dropdown](../assets/images/OBCI32_Board_Dropdown.png)

9. In the Arduino IDE go `File-->Examples-->OpenBCI_32bit_Library-->DefaultBoard` which will launch the Host firmware.

10. Make sure that the slide switch on the OpenBCI Dongle is switched to the GPIO6 selection. If it's on the other side, it will try to program the Dongle-mounted RFduino! Now is a good time to plug your Dongle in and power down the Board.

![serial_port](../assets/images/PortSelect.png)

11. Select the correct serial port for your OpenBCI Dongle.

* On Macs, this will be named **/dev/tty.usbserial-DN00nnnn** where the nnnn is a combination of numbers and letters specific to your openBCI Dongle.

* On Windows, the serial port will be listed as a numbered COM port.

* On Linux, it will be different.

12. When you are happy with the code, you will have to put the 32bit board into bootloader mode. We don't have a way to remotely reset the chipKIT compatible IC, so you have to do it manually.

![reset_program](../assets/images/RST_PROG.png)

  1. Power OFF the OpenBCI Board.
  2. Press down both RST and PROG buttons at the same time.
  3. Power ON the OpenBCI Board.
  4. Release the RST button while still holding down the PROG button.
  5. Release the PROG button.

![Upload32](../assets/images/Upload32.png)

13. Verify that you see the blue LED on the 32bit board blinking pleasantly.

14. Press the upload button on the Arduino IDE.

That's it! You will see some blinky lights on the Dongle, and after a short while, the Arduino IDE will tell you that it's done. Happy Hacking!

## Firmware Version 1.x.x (2014 - Fall 2016)

**You will need:**

* Computer running [Arduino v1.8.0](https://www.arduino.cc/en/Main/Software) or later
* OpenBCI Dongle connected to USB port
* OpenBCI Cyton Board with battery power

![OpenBCI Dongle](../assets/images/dongleConnection.png)

***Note***: Always plug the Dongle into the PC before powering the Board because the Host (RFduino on the Dongle) must be powered before the Device (RFduino on the Board).

First, install the Arduino IDE which can be found here:

		https://www.arduino.cc/en/Main/Software

**Note for Windows users** While installing Arduino 1.8, if the installer instructs you to uninstall 1.5.8, move the Arduino folder containing 1.5.8 from `Program Files (x86)` to your downloads folder. Rename this folder to `Arduino_1.5.8`. Open the `Change or remove program` app in control panel and uninstall the Arduino application. There will be a popup indicating that the files do not exist and asking if you want to remove the program from the files list, select yes. Then install 1.8.0 as normal. Navigate to back to your `Program Files (x86)` folder and locate the Arduino folder. Rename this folder to `Arduino_1.8.0`. Now drag and drop the `Arduino_1.5.8` back into `Program Files (x86)` folder.  

You can find the previous OpenBCI firmware and libraries on our github repository.

	https://github.com/OpenBCI/OpenBCI_32bit

	https://github.com/OpenBCI/OpenBCI_32bit_Library/tree/maint/1.0.0

* OpenBCI_32bit
	* This is the firmware that runs on the OpenBCI 32bit Board
* OBCI_SD
	* Supports writing raw data to on-board SD card
* OpenBCI_32_Daisy
	* The OpenBCI 32bit Library

You will need to install the folders 'OpenBCI_32_Daisy' and 'OBCI_SD' from our Libraries repository into your Documents/Arduino/libraries folder. If there is no 'libraries' folder in the sketch folder, create one. Move the folder called 'OpenBCI_32bit' into your Documents/Arduino folder.

Before you can upload code correctly to the PIC32 with Arduino, you need to add the chipKIT-core board files to your Arduino IDE. The folks at chipKIT have put together instructions on how to [Auto Install via URL from within Arduino](http://chipkit.net/wiki/index.php?title=ChipKIT_core#1.29_Auto_install_via_URL_from_within_Arduino_IDE_.28latest_version_chipKIT-core_v1.3.1.29). Follow the process in the previous link, and you will be able to select the OpenBCI board from the Tools >> Board >> dropdown menu!

![board_dropdown](../assets/images/OBCI32_Board_Dropdown.png)

Open the OpenBCI_32bit sketch from the File -> Sketchbook dropdown. Then select OpenBCI 32 from the Board drop-down menu.

Make sure that the slide switch on the OpenBCI Dongle is switched to the GPIO6 selection. If it's on the other side, it will try to program the Dongle-mounted RFduino! Now is a good time to plug your Dongle in and power down the Board.

![serial_port](../assets/images/PortSelect.png)

Select the correct serial port for your OpenBCI Dongle.

* On Macs, this will be named **/dev/tty.usbserial-DN00nnnn** where the nnnn is a combination of numbers and letters specific to your openBCI Dongle.

* On Windows, the serial port will be listed as a numbered COM port.

* On Linux, it will be different.

When you are happy with the code, you will have to put the 32bit board into bootloader mode. We don't have a way to remotely reset the chipKIT compatible IC, so you have to do it manually.

![reset_program](../assets/images/RST_PROG.png)

* Power OFF the OpenBCI Board.
* Press down both RST and PROG buttons at the same time.
* Power ON the OpenBCI Board.
* Release the RST button while still holding down the PROG button.
* Release the PROG button.

![Upload32](../assets/images/Upload32.png)

Now you should see the blue LED on the 32bit board blinking pleasantly. Press the upload button on the Arduino IDE. That's it! You will see some blinky lights on the Dongle, and after a short while, the Arduino IDE will tell you that it's done. Happy Hacking!


##8bit Upload How-To
###NOTE: The 8bit Hardware is no longer in production
**You will need:**

* Computer running Arduino IDE
* OpenBCI Dongle connected to USB port
* OpenBCI 8bit Board with battery power

![OpenBCI Dongle](../assets/images/dongleConnection.png)

Make sure that the slide switch on the OpenBCI Dongle is switched to the GPIO6 selection. That way the DTR reset signal will get passed over-air to the ATmega328. If it's on the other side, it will try to program the Dongle-mounted RFduino!  
You can find the latest firmware and libraries on our github repository

https://github.com/OpenBCI/OpenBCI_8bit

You will need to install these files from our repository into your Documents/arduino/libraries folder

* SdFat
    * Supports writing raw data to on-board SD card
* OpenBCI_8
    * The OpenBCI 8bit Library


![ArduinoIDE](../assets/images/Arduino_IDE.png)

Move the file OpenBCI_8bit_SD.ino into your Documents/arduino folder, and start up the Arduino IDE. you should then see the sketch in your Sketch folder.

![selectBoardUno](../assets/images/BoardSelect.png)

Select Arduino UNO from the Board drop-down menu.

![selectSerialPort](../assets/images/SerialPortSelect.png)

Select the correct serial port for your OpenBCI Dongle.

* On Macs, this will be named **/dev/tty.usbserial-DN00nnnn** where the nnnn is a combination of numbers and letters specific to your openBCI Dongle.

* On Windows, the serial port will be listed as a COM port.

* On Linux, it will be different.

![Upload](../assets/images/Upload.png)

When you are happy with the code, simply press upload to program the OpenBCI 8bit target. That's it! You will see some blinky lights on the Dongle, and after a short while, the Arduino IDE will tell you that it's done.

## Troubleshooting

If you're having an issue with `Board_Defs.h` and you're uploading using Linux, you must move ALL files located in: <br/> `/Arduino/hardware/chipkit-core/pic32/variants/openbci/` to `/Arduino/hardware/chipkit-core/pic32/cores/pic32/`<br/> This should fix any issues you're having compiling.


If the upload fails with `No Target Found`:

1. Unplug the Dongle and Device.
2. Plug the Dongle into your computer.
3. Plug the Device into your computer.
4. Put the device into bootloader mode.
5. Try upload again.

If the upload fails with `Program Flash Failed` it's due to the Arduino IDE not being able to read from the serial port fast enough possibly do to resource starvation or overall computer power. We recommend taking the following actions:

* Keep the Board and Dongle physically close to each other during the upload.
* Keep the Arduino IDE open, front and center and don't use any other programs during the upload.
* Close all open programs such as (Google Chrome, MS Word, etc...) and only have the Arduino 1.6.5 IDE open during upload.
* Restart your computer and don't open any other programs other than the Arduino 1.6.5 IDE used for programming.
* If all else fails, find a friend with a more powerful computer and do the uploading from their computer.

In extreme conditions, if you have tried all five of the above methods and still can't upload, then you can try to increase the Device's polling time [in the RFduino Device firmware code](https://github.com/OpenBCI/OpenBCI_Radios/blob/master/OpenBCI_32bit_Device/OpenBCI_32bit_Device.ino#L41). Increase `pollTime` incrementally (by about 5ms) until the upload succeeds. Upload the new radio code to the Device ([see tutorial](http://docs.openbci.com/tutorials/03-Upload_Code_to_OpenBCI_Dongle#uploading-device-firmware-to-openbci-boards-program-device-radio-with-openbci-dongle)). After you are satisfied with the uploaded code. You should set the Device's `pollTime` back to 60mS to remain compatible with existing drivers.   
