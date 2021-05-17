# Compilation procedure for WSPR-TX 0.90

## Install Arduino IDE

[Getting started with the Arduino Desktop IDE](https://create.arduino.cc/projecthub/Arduino_Genuino/getting-started-with-the-arduino-desktop-ide-623be4)

## Before compilation

In the Arduino IDE with macOS 10.14.6, do the following:

* Set board to `Arduino Pro or Pro Mini`
* Set processor to `ATMega328P (3.3V, 8MHz)`
* Install library `NeoGPS by Slash Devin` at yhe library manageri
* locate and modify the file `NMEAGPS_cfg.h`. It is a part of the NeoGPS library. The path on macOS is: `~/Documents/Arduino/libraries/NeoGPS/src`
* Enable the following flags in `NMEAGPS_cfg.h` by uncommenting them:

```c
#define NMEAGPS_PARSE_GSV
#define NMEAGPS_PARSE_SATELLITE_INFO
#define NMEAGPS_PARSE_SATELLITES
```

## How to compile and write the result

* Open the file "WSPR-TX0.90.ino" (Arduino IDE will move the file and create a skecth directory calles WSPR-TX0.90)
* Export compiled binary
* Use the following avrdude command to write the compiled binary to WSPR Transmitter:

```
avrdude -p m328p -b 57600 -P /dev/cu.usbserial-devicename -c stk500v1 -U flash:w:WSPR-TX0.90.ino.with_bootloader.eightanaloginputs.hex
```

