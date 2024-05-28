KeDei-rpi-touch-screen-HDMI 
How to install driver
---
    1. Burn OS system (Raspberry Pi OS) in a TF card/micro SD card, and insert this card in your raspberry Pi
Note:

The Raspberry Pi must be connected to the network, or else the program won’t be successfully installed. You can remotely control Raspberry Pi via ssh, vnc or remote desktop tools, or directly control Raspberry Pi with other HDMI monitor with keyboard and mouse All following steps are tested on OS: 2021-05-07-raspios-buster-armhf, there may be some differences with other OS 2) Run the following commands in terminal to switch user permission as administrator

run code
---
```shell
#first
sudo apt-get update
#dowload file
git clone https://github.com/kedei/LCD_driver
```
# Run the following command in terminal to change the executable permissions of file and go to 'LCD_driver'
```shell
sudo chmod -R 777 LCD_driver

cd LCD_driver
```
# run the file
```shell
sudo ./LCD35_hdmi
```
Wait for about 2 minutes, the driver would be installed and reset automatically, insert the 3.5″ HDMI screen and turn on.
---
calibration app (If you want to install,you can continue.If you don't . you are completely your install)
---
#install app
```shell
sudo apt-get install xinput-calibrator
```
clieck menu than Preferences -> Calibrate Touchscreen
If you want to save the value
```shell
sudo nano /etc/X11/xorg.conf.d/99-calibration.conf
```
Save the touch parameters to 99-calibration.conf
the code same as in the image
keyborad
---
```shell
sudo apt-get install matchbox-keyboard
sudo nano /usr/bin/toggle-matchbox-keyboard.sh

#copy to this file toggle-matchbox-keyboard.sh

#!/bin/bash
#This script toggle the virtual keyboard
PID=`pidof matchbox-keyboard`
if [ ! -e $PID ]; then
killall matchbox-keyboard
else
matchbox-keyboard &
fi
```

