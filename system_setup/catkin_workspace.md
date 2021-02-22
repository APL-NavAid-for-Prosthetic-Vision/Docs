# Catkin Workspace

## Description
Guide for setting up the project catkin workspace

## Create workspace
```bash
cd Documents
mkdir slamr01_ws && cd slamr01_ws
mkdir src
sudo catkin config --init -DCMAKE_BUILD_TYPE=Release -DPYTHON_EXECUTABLE=/usr/bin/python3 --extend /opt/ros/melodic --blacklist audio_3D_ros2
sudo catkin build
```

## Project Directory Structure
Clone the following repositories following this directory structure
~~~
|-- slamr01_ws
    |-- build
    |-- devel
    |-- logs
    |-- src
        |-- core (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/core/browse)
        |-- docs (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/docs/browse)
        |-- vr (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/vr/browse)
        |-- navmap (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/navmap/browse)
        |-- spatialsound (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/spatialsound/browse)
        |-- voiceinterface (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/voiceinterface/browse)
        |-- extern
            |-- realsense-ros (https://github.com/IntelRealSense/realsense-ros)
            |-- ddynamic_reconfigure (https://github.com/pal-robotics/ddynamic_reconfigure)
~~~

## Build workspace
```bash
sudo catkin build
```