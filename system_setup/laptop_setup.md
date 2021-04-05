# Laptop Setup Guide

## Description
This guide will walk you through setting up the laptop.

## 1) OS Environment
* Ensure laptop has Ubuntu 18.04 installed

## 2) Install Realsense
* Reference jetson_realsense.md

## 3) Install ROS
* Reference jetson_ros_python3.md

## 4) Setup Catkin Workspace
* Reference catkin_workspace.md

## 5) Ensure opencv for python 3 is installed
```bash
sudo apt-get install python3-opencv
```
Do not install opencv through pip3

## 6) ROS Network
* Disable firewall
    * sudo ufw disable
* Set static IPv4 for wifi
    * IP=192.168.3.201, NETMASK= 255.255.255.0, GATEWAY=192.168.30
* Add the following lines to ~/.bashrc
    * alias slamr01jxros="export ROS_MASTER_URI=http://192.168.3.101:11311 && export ROS_IP=192.168.3.201"
    * alias slamr01jxssh="ssh slamr01jx@192.168.3.101"
* Add the following to /etc/hosts
    * 192.168.3.101 jetson_hostname
* source ~/.bashrc