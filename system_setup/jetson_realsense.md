# Jetson Realsense

## Description
Guide for preparing realsense sensors on Jetson AGX Xavier

## 1) Install from source
* https://confluence.xrcs.jhuapl.edu/confluence/display/SLAMR01/Installation+on+Nvidia+family+platforms%3A+JetsonNote: 
* I downloaded librealsense to ~/slamr01_workspace/Software/
* Note, I also had to add the realsense library to LD_LIBRARY_PATH
    * Add this to .bashrc:
    * export LD_LIBRARY_PATH=/usr/local/realsense2_2.41.0/lib:$LD_LIBRARY_PATH

## 2) Test Installation
* plug in camera
* cd ~/slamr01_workspace/Software/librealsense/build/tools/realsense-viewer/
* ./realsense-viewer