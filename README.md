# Purchase Links
- [Apple ADB Mouse (original 80's wedge design)](https://www.tindie.com/products/ttdesign/apple-desktop-bus-adb-optical-mouse-retro-board/)
- [Apple ADB Mouse II (rounded 90's design)](https://www.tindie.com/products/ttdesign/apple-desktop-bus-adb-ii-optical-mouse-retro-board/)
# Project Info

This DIY install project is for a series of optical sensor replacement boards that update the original Apple Desktop Bus Mouse (I and II) for Macintosh computers. The boards utilize the original ADB port/protocol which was introduced with the Apple IIGS, Macintosh SE and Macintosh II and was used until the late 90s. If you want to modernize your mouse or If your mouse has lost its ball or it has stopped working, this board will help get it back into service. 

Apple produced several variations of the mice, so before purchasing a board, please open your mouse and check if its internal board matches the general shape shown in this listing. 

The product is **not a USB device**. It is intended to be used with vintage machines, though it could be used with ADB to USB adapters if you want a classic ADB mouse with an optical sensor paired with your battle station.

**Note:** The ADB cable from your mouse is required, and you will need to **desolder and solder 4 wires or a 4 pin connector** to the new board.

### Original ADB Mouse Shell Compatibility

  ✅ **Model G5431** (Made in Taiwan) - Tested and fits
  ✅ **Model G5431** (Made in Ireland) - Tested and fits
  ❌ **Model G5431** (Made in USA) - Does not fit
  ❓ **Model A9M0331** (Made in Taiwan) - Compatibility TBD
  ❓ **Model A9M0331** (Made in USA) - Compatibility TBD

### ADB Mouse II Shell Compatibility

  ✅ **Model M2706** (Made in Malaysia, Manufactured by Mitsumi) - Tested and fits

### Features

- Fully compatible with the  **ADB protocol** as a mouse input device
- High-quality **optical sensor** set to 100 counts per inch (CPI) by default for vintage systems (like the original spec)
- Ability to change the CPI (counts per inch or resolution) via host machine or USB-C serial port
- Ability to change the apparent mouse speed
- Smooth mouse movements
- Tested with **SE/30**, **Iici**, **Quadra 800**, and **NeXTStation Turbo with ADB port**
- **Omron switch** for mouse button
- Easy firmware updates through **drag-and-drop** of firmware files
- **In-house developed device firmware**

Note: If you are using a MacEffects clear mouse shell, the optical lens needs to be filed or sanded down around the perimeter so it fits inside the circular recess at the bottom of the shell.

# Installation Instructions

### Original Apple ADB Mouse

To install the new board, use a soldering iron and tweezers or needle-nose pliers:

1. Open the mouse by removing the 4 exposed screws on the bottom side and remove the original board
2. Heat the bottom board side of the wire.
2. Pull the wire out once the solder melts.
3. Clean off any excess solder from the wire ends before attaching them to the new board. It may be necessary to trim and strip the wires.
4. Insert the wire gland into the notch, note there is a curved side that is oriented toward the lower shell.

The new bottom cover installs the same way as the original mouse ball retainer.

### Apple ADB Mouse II

To install the new board, use a soldering iron and tweezers or needle-nose pliers. The original board uses a connector soldered to the board which makes the installation a bit more challenging.

1. Open the mouse by removing the 2 hidden screws on the bottom side under the label and remove the original board. You may be able to keep the label intact if you carefully and partially peel the left and right sides of the label.
2. Add extra solder to the bottom board side of the wire connector. A low melt solder like Chip Quik is helpful for removing components like this one.
2. Pull the wire out once the solder melts.
3. Clean off any excess solder from the connector end before attaching them to the new board. It may be necessary to trim and strip the wires.
4. Insert the wire gland into the notch, note there is a curved side that is oriented toward the lower shell.

### Wire Color Coding

| Code | Wire Color | Description  |
|------|------------|--------------|
| RD   | Red        | ADB Data     |
| BL   | Blue       | 5 V Power    |
| BK   | Black      | Ground       |
| SH   | Black      | Shield       |

# Changing the CPI (Resolution) and Speed Settings

The CPI can be changed in increments of 100 counts from 100 to 1500. The default setting is 100 CPI like the original mouse.

Adjusting the CPI is probably not typically necessary. Increasing the CPI makes the mouse pointer move faster/longer distances on the screen for a given amount of physical movement. It is added as a feature in case someone has a large high resolution display.

There are currently two ways to change the CPI setting:

1. With the Macintosh [ADB Parser](http://macintoshgarden.org/apps/adb-parser) application. Input the hex value (0x01 to 0x10) via Listen Register 1 command for the mouse address (usually 3). See below for setting the speed if you have firmware v0.3.3 or later.
2. Connect via USB-C serial connection to your computer and input the number and press return (100-1600). An easy way to connect is to go to [Huhn Serial Web Terminal](https://serial.huhn.me/) on a Chrome compatible browser to connect to the mouse.

#### Speed Setting

For firmware versions 0.3.3 and higher, the speed setting, 1-6 is applied in a similar way to the CPI. *A speed setting of 1 is not really a usable setting at this time, it results in unnatural movements. 5 is the default setting.* 
- In the serial console, just type a number 1-6. 
-  With ADB Parser, you need to enter the speed along with the CPI since it's stored in the lower byte of the 16-bit register 1. 
  -  So the default setting would be hex value 0x51 (entered as '0051' in ADB Parser) for speed = 5 and CPI of 100
  -  As another example, hex value 0x32 (entered as '0032' in ADB Parser) for speed = 3 and CPI of 200.

# Firmware Update Instructions

To get the device into update mode:

- Connect the board to a computer via USB-C.
- Getting the device into reset mode:
  - Press and hold the “B” button on the microcontroller board.
  - Tap the other button and then unpress/let go of the “B” button.
  - The board will appear as a USB drive “RPI-RP2”.
- Drop the file in the drive.
- The update is complete. The green LED should be slowly pulsatin.

Update mode can be accessed (with firmware starting at v0.3.3) with the serial command ‘update’.

# Cosmetic Restoration

Consider using this time to **restore the original color** of your mouse shell. A simple method involves placing the shell in an open mason jar with **sodium percarbonate aka OxiClean or hydrogen peroxide** and leaving it in the sun for a few hours or possibly a few days.

# Project Background

This project began several years ago, initially tinkering with an Apple USB Optical Mouse that can output quadrature signals connected to an ADB mouse with wires, followed by an Arduino Mega. Eventually, the focus shifted to mastering the ADB protocol via a USB to ADB project using a USB host shield. Then development circled back to designing an ADB optical mouse solution based on the **RP2040**, which made interfacing with the 3.3V optical sensor more efficient.
