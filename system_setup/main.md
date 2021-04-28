# System Setup Guide

## Description
This guide will walk you through setting up the Jetson AGX Xavier system.

## 0) Acquire necessary hardware
* Reference harware_list.md

## 1) Flash Jetson AGX Xavier
* Reference jetson_flash.md

## 2) Prepare Jetson AGX Xavier with dependencies
* Reference jetson_prep.md

## 3) Install Realsense
* Reference jetson_realsense.md

## 4) Install Mycroft
* Reference jetson_mycroft.md

## 5) Install ROS with Python3
* Reference jetson_ros_python3.md

## 6) Setup Oculus Go App
* Reference oculus_go.md

## 7) Setup Catkin Workspace
* Reference catkin_workspace.md

## 8) ROS Network
* Disable firewall
    * sudo ufw disable
* Set static IPv4 for wifi
    * IP=192.168.3.101, NETMASK= 255.255.255.0, GATEWAY=192.168.30
* Add the following lines to ~/.bashrc
    * alias slamr01jxros="export ROS_MASTER_URI=http://jetson_hostname:11311 && export ROS_IP=192.168.3.101 && export DISPLAY=:1"
* Add the following to /etc/hosts
    * 192.168.3.201 laptop_hostname
* source ~/.bashrc

## 9) Laptop
* Reference laptop_setup.md