# Jetson Preparation

## Description
Guide for preparing Jetson

## 1) Enable Bluetooth Audio
* Navigate to this file:
    * /lib/systemd/system/bluetooth.service.d/nv-bluetooth-service.conf
* Use a text editor to change this line ...
    * ExecStart=/usr/lib/bluetooth/bluetoothd -d --noplugin=audio,a2dp,avrcp
* ... to this: 
    * ExecStart=/usr/lib/bluetooth/bluetoothd -d 
* Enter these commands to update the apt-get package list and install the pulse audio package:
    * sudo apt-get update
    * sudo apt-get install pulseaudio-module-bluetooth
* Enter this command to reboot the Jetson device:
    * sudo reboot
* When the reboot is complete, pair and connect any Bluetooth headset.
* Source: https://docs.nvidia.com/jetson/l4t/index.html#page/Tegra%20Linux%20Driver%20Package%20Development%20Guide/hw_setup.html#wwpID0E0KN0HA 

## 2) Ensure OpenAL is installed
```bash
sudo apt-get install libopenal-dev
```

## 3) Set up pulseaudio
```bash
sudo apt install pulseaudio
sudo apt install pavucontrol
```

## 4) Create software directory
```bash
cd
mkdir Software
```
