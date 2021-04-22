# Catkin Workspace

## Description
Guide for setting up the project catkin workspace

## Create workspace
```bash
cd ~/slamr01_workspace
mkdir slamr01_ws && cd slamr01_ws
mkdir src
sudo catkin config --init -DCMAKE_BUILD_TYPE=Release -DPYTHON_EXECUTABLE=/usr/bin/python3 --extend /opt/ros/melodic --blacklist audio_3D_ros2
sudo catkin build
```

## Project Directory Structure
Clone the following repositories following this directory structure.  Where applicable, checkout melodic branches
~~~
|-- slamr01_ws
    |-- build
    |-- devel
    |-- logs
    |-- src
        |-- core (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/core/browse)
        |-- docs (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/docs/browse)
        |-- vr (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/vr/browse)
        |-- navmap (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/navmap/browse) (set enable_semanticSegmentation to false in launch files)
        |-- spatialsound (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/spatialsound/browse)
        |-- voiceinterface (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/voiceinterface/browse)
        |-- rtabmap_ros (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/rtabmap_ros/browse) (comment out all references to and usage of objectrecognition)
        |-- extern
            |-- realsense-ros (https://github.com/IntelRealSense/realsense-ros)
            |-- ddynamic_reconfigure (https://github.com/pal-robotics/ddynamic_reconfigure)
            |-- image_pipeline (https://github.com/ros-perception/image_pipeline) (remove image_view package)
            |-- octomap_msgs (https://github.com/OctoMap/octomap_msgs)
            |-- octomap_ros (https://github.com/OctoMap/octomap_ros)
            |-- octomap_rviz_plugins (https://github.com/OctoMap/octomap_rviz_plugins)
~~~

## Build workspace
```bash
sudo catkin build
```