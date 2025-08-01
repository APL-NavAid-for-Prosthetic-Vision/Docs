# Laptop Setup Guide

## Description
This guide will walk you through setting up an additional laptop that can be used to ssh into the jetson.

## 1) OS Environment
* Ensure laptop has Ubuntu 18.04 installed

## 2) Install Software Dependencies
* Reference jetson_software.md
* NOTE: only need to set up PyQt, RTAB_APL, RTK & PUMA, and Additional Python3 Libraries

## 3) Install ROS
* Reference jetson_ros.md

## 4) Setup Catkin Workspace
* Reference catkin_workspace.md

## 5) Jetson: ROS Network Config
* Disable firewall
    * sudo ufw disable
* Set static IPv4 for wifi
    * IP=192.168.3.101, NETMASK= 255.255.255.0, GATEWAY=192.168.30
* Add the following lines to ~/.bashrc
    * alias slamr01jxros="export ROS_MASTER_URI=http://jetson_hostname:11311 && export ROS_IP=192.168.3.101 && export DISPLAY=:1"
* Add the following to /etc/hosts
    * 192.168.3.201 laptop_hostname
* source ~/.bashrc

## 6) Laption: ROS Network Config
* Disable firewall
    * sudo ufw disable
* Set static IPv4 for wifi
    * IP=192.168.3.201, NETMASK= 255.255.255.0, GATEWAY=192.168.3.0
* Add the following lines to ~/.bashrc
    * alias slamr01jxros="export ROS_MASTER_URI=http://192.168.3.101:11311 && export ROS_IP=192.168.3.201"
    * alias slamr01jxssh="ssh slamr01jx@192.168.3.101"
* Add the following to /etc/hosts
    * 192.168.3.101 jetson_hostname
* source ~/.bashrc