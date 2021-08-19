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
sudo apt-get install libalut-dev
pip3 install python-openal
```

## 3) Set up pulseaudio
```bash
sudo apt install pulseaudio
sudo apt install pavucontrol
```

## 4) Ensure PyQt is installed
```bash
sudo apt-get install python3-pyqt5
```

## 5) Ensure opencv for python 3 is installed
```bash
sudo apt-get install python3-opencv
```
Do not install opencv through pip3

## 6) Create software directory
```bash
cd ~/slamr01_workspace
mkdir Software
```
## 7) Install RTAB_APL in Software folder
* https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/rtabmap_apl/browse
* build in ~/slamr01_workspace/Software
* instead of using "./install_octomap.sh build", install RTK compatible OctoMap
    * build in ~/slamr01_workspace/Software
    * https://bitbucket.xrcs.jhuapl.edu/projects/RTK/repos/octomap/browse
    * checkout v1.9.6 branch
    * Use these commands instead of the ones in the readme
        * cmake .. -DOCTOMAP_OMP=ON -DBUILD_OCTOVIS_SUBPROJECT=0 -DBUILD_DYNAMICETD3D_SUBPROJECT=0
        * make -j10 && sudo make install
        * cmake .. -DOCTOMAP_OMP=ON -DBUILD_OCTOVIS_SUBPROJECT=1 -DBUILD_DYNAMICETD3D_SUBPROJECT=1
        * make -j10 && sudo make install
* Install without TOOLS and APPS
* close/open terminal

## 8) Install RTK/PUMA
* https://confluence.xrcs.jhuapl.edu/confluence/pages/viewpage.action?pageId=78219191
* build in ~/slamr01_workspace/Software
* Checkout octomap_v1.9.6 branch of RTK

## 9) Install Pytorch
* https://confluence.xrcs.jhuapl.edu/confluence/display/SLAMR01/PyTorch
* download pytorch wheel and torchvision repo in ~/slamr01_workspace/Software
* I did not install PyTorch-Encoding