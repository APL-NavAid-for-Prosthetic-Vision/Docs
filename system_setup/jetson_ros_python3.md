# Jetson ROS Python3

## Description
Guide for setting up ROS with Python3 on the Jetson AGX Xavier

## 1) Install ROS with Python3
https://confluence.xrcs.jhuapl.edu/confluence/pages/viewpage.action?pageId=67534937

## 2) Resolve CV Runtime Errors (if applicable)
* If you have runtime errors when importing cv2 in python, do the following
* Create the file /etc/ld.so.conf.d/opencv.conf
* Write /usr/local/opencv_v3.4.10/lib/ to file
* sudo ld config -v