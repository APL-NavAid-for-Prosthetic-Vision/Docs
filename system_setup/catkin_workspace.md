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
Clone the following repositories following this directory structure (links included below are not the clone links, they are the website links).  Where possible, checkout melodic branches
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
        |-- voiceinterface (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/voiceinterface/browse)
        |-- rtabmap_ros (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/rtabmap_ros/browse)
        |-- capra (https://bitbucket.xrcs.jhuapl.edu/projects/RAR/repos/capra/browse)
        |-- rtk_ros (https://bitbucket.xrcs.jhuapl.edu/projects/RAR/repos/rtk_ros/browse)
        |-- semantic_seg_ros (https://gitlab.jhuapl.edu/slamr01/semantic_seg_ros)
        |-- gui_hst (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/gui_hst/browse)
        |-- haptic (https://bitbucket.xrcs.jhuapl.edu/projects/SLAMR01/repos/haptic/browse)
        |-- extern
            |-- aruco_ros (https://github.com/pal-robotics/aruco_ros)
            |-- realsense-ros (https://github.com/IntelRealSense/realsense-ros)
            |-- ddynamic_reconfigure (https://github.com/pal-robotics/ddynamic_reconfigure)
            |-- image_pipeline (https://github.com/ros-perception/image_pipeline) (remove image_view package)
            |-- octomap_msgs (https://github.com/OctoMap/octomap_msgs)
            |-- octomap_ros (https://github.com/OctoMap/octomap_ros)
            |-- octomap_rviz_plugins (https://github.com/OctoMap/octomap_rviz_plugins)
            |-- perception_pcl (https://github.com/ros-perception/perception_pcl/tree/melodic-devel)
            |-- robot_state_publisher (https://github.com/ros/robot_state_publisher.git) (melodic-devel)
~~~

# semantic_seg_ros
* You must be on the internal APL network to download/clone this repo, so you won't be able to clone it onto the jetson directly
* On a computer connected to the internal network, download the repo. Transfer it to the jetson with a flashdrive

# pylibi2c
* pylibi2c must be installed for the haptics interface
    * cd slamr01_ws/src/haptic/libi2c-master
    * sudo python setup.py install

## Build workspace
```bash
catkin config --cmake-args -DCMAKE_BUILD_TYPE=Release -DPYTHON_EXECUTABLE=/usr/bin/python3
sudo catkin build --cmake-args -DOPENCV_CUDA=ON -DWITH_YAMLCPP=ON -DRTABMAP_GUI=OFF
```