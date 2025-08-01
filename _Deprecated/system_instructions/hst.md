# Instructions for HST

## Jetson Xavier
* Plug in Jetson Xavier to power
* Hit power button (left button)
* Connect USB hub w/ keyboard and mouse
* Connect tp-link to USB hub
* Connect tp-link to Jetson Xavier with ethernet
* Plug in TOGUARD monitor to power
* Connect TOGUARD monitor to Jetson Xavier with HDMI
* Set TOGUARD monitor to HDMI mode
* Login to Jetson (username: slamr01, password: slamr01)
* Disable wifi on Jetson
* Set ethernet network to TCPLink
* Disconnect TOGUARD monitor

## Laptop
* Plug in laptop to power
* Turn on laptop
* Login to laptop (username: slamro1, password: slamr01)
* Connect wifi to TP-Link_2E22

## Argus 2
* Connect HDMI2AV converter to USB Hub
* Connect HDMI from Jetson to HDMI2AV
* Connect AV cable from HDMI2AV to Argus2
* Make sure Argus2 system is running

## Run HST trial (On laptop)
* Open terminal 1
    * SSH into Jetson: ‘slamr01jxssh’
    * Setup ROS variables: ‘slamr01jxros’
    * Navigate to ros workspace: ‘cd slamr01_workspace/slamr01_ws’
    * Source ROS setup: ‘source devel/setup.bash’
    * Verify argus2 video resolution: ‘xrander’
    * If the current resolution is not 720 x 480:
    * Reset resolution: ‘xrandr —size 720x480’
* Open terminal 2
    * Setup ROS variables: ‘slamr01jxros’
    * Navigate to ros workspace ‘cd slamr01_workspace/slamr01_ws’
    * Source ROS setup: ‘source devel/setup.bash’
* Run argus and gui
    * First: In terminal 1, run: ‘roslaunch core_test argus_hst.launch’
    * Second: In terminal 2, run: ‘roslaunch core_test gui.launch’
    * Use GUI to run HST