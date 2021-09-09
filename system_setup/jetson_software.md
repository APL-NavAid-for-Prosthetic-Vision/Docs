# Jetson Software

## Description
Guide for installing software onto Jetson

## 1) Create software directory (for non-ROS software)
```bash
cd ~/slamr01_workspace
mkdir Software
```

## 2) OpenAL
```bash
sudo apt-get install libopenal-dev
sudo apt-get install libalut-dev
pip3 install python-openal
```

## 3) Pulseaudio
```bash
sudo apt install pulseaudio
sudo apt install pavucontrol
```

## 4) PyQt
```bash
sudo apt-get install python3-pyqt5
```

## 5) OpenCV
```bash
sudo apt-get install python3-opencv
```
Do not install opencv through pip3

## 6) Realsense
* https://confluence.xrcs.jhuapl.edu/confluence/display/SLAMR01/Installation+on+Nvidia+family+platforms%3A+JetsonNote: 
* I downloaded librealsense to ~/slamr01_workspace/Software/
* Note, I also had to add the realsense library to LD_LIBRARY_PATH
    * Add this to .bashrc:
    * export LD_LIBRARY_PATH=/usr/local/realsense2_2.41.0/lib:$LD_LIBRARY_PATH
* Test Installation
    * plug in camera
    * cd ~/slamr01_workspace/Software/librealsense/build/tools/realsense-viewer/
    * ./realsense-viewer

## 7) RTAB_APL
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

## 8) RTK & PUMA
* https://confluence.xrcs.jhuapl.edu/confluence/pages/viewpage.action?pageId=78219191
* build in ~/slamr01_workspace/Software
* Checkout slamr01_dev branches of RTK & PUMA

## 9) Pytorch
* https://confluence.xrcs.jhuapl.edu/confluence/display/SLAMR01/PyTorch
* download pytorch wheel and torchvision repo in ~/slamr01_workspace/Software
* I did not install PyTorch-Encoding

## 10) Mycroft
* WARNING: This is pretty involved
* Reference jetson_mycroft.md

## 11) Additional Python3 Libraries
* pip3 install screeninfo, keyboard, gTTS