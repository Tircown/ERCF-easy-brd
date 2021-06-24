# ERCF EASY BRD

![ERCF front picture](/images/ercf-easy-brd_front.jpg)

**Be careful not to invert polarity in the screw terminal or it may damage the board and even more.**

**Do not use the servo connector as an input or do it at your own risk.  
Voltage input connected to general I/O pins may cause chip damage if it' higher than 3.3V .**

## BOM
Component | Position
------------ | -------------
Resistor 10K | R1, R2, R3, R4
Capacitor ceramic 0.33uF 25V | C1
Capacitor ceramic 0.1uF 25V | C2
Capacitor 100uF 25V | C3, C4
2P Screw terminal P=5.08 | J5
3P JST-XH male P=2.54 | J1, J2, J3, J4
4P JST-XH male P=2.54 | J6, J7
8P Header socket P=2.54 | *4x for U4 and U3*
2P Header socket P=2.54 | *1x for U4*
5P Header pin P=2.54 | J6
7P Header socket female P=2.54 | *(optionnal) 2x for Seeeduino XIAO*
Seeeduino XIAO or Adafruit QT Py (same footprint & pinout)| U1
Voltage regulator L7805CP | U2
SilentStepStick TMC220X | U3, U4
Jumper P=2.54 | *2x for J6*

## Configure the MCU - Seeeduino XIAO
* Install bossac (version ≥1.8)
```
sudo apt install libreadline-dev libwxgtk3.0-*
git clone https://github.com/shumatech/BOSSA.git
cd BOSSA
make
sudo cp bin/bossac /usr/local/bin
```
* Prepare the firmware
```
cd ~/klipper
make menuconfig
```
![Menuconfig instructions](/images/flashing.jpg)
```
make clean
make
```
* Flashing the Seeeduino XIAO
Connect the Seeeduino XIAO to your raspberry if it's not already done.
Get the port of the XIAO, i.e. `ls /dev/tty*`, and modify the default `/dev/ttyACM1` in the command line bellow.
Use tweezers or short lines to short the RST pins in the diagram twice. The orange LED lights flicker on and light up. Then send in the next few seconds this command line matching your port.
```
sudo /usr/local/bin/bossac -i -d -p /dev/ttyACM1 -e -w -v -R --offset=0x2000 out/klipper.bin
```

More informations on how to reset for flashing:  
https://wiki.seeedstudio.com/Seeeduino-XIAO/#enter-bootloader-mode

## Klipper configuration
See [ercf_hardware.cfg](ercf_hardware.cfg)

## Get the PCB Board
If you want to support my work: https://www.pcbway.com/project/shareproject/ERCF_EASY_BRD.html  
*note: default setting is "HASL lead free" but if it doesn't matter to you, just change this option to get more affordable boards.*

Or just download the Gerber files and upload it to the manufacturer of your choice.

## Dimensions
![ERCF dimensions picture](/images/dimensions.jpg)

## More pictures
![ERCF back picture](/images/ercf-easy-brd_back.jpg)
![ERCF front picture](/images/ercf-easy-brd_front_2.jpg)
