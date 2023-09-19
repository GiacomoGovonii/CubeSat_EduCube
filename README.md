# ERC Remote Navigation Simulation

This repository provides a Gazebo simulation of the Navigation and Science Task for the EuropeanRoverChallenge Remote competition. \
For the dockerized version, skip to the [Using Docker](#using-docker) section.

## Table of Contents
1. [Prerequisites](#prerequisites)
1. [Building](#building)
1. [Updating](#updating)
1. [Launching](#launching)
1. [Using Docker](#using-docker)
1. [ROS API](#ros-api)
    1. [Subscribed Topics](#subscribed-topics)
    1. [Published Topics](#published-topics)
    1. [Services](#services)
    1. [Parameters Set](#parameters-set)
1. [Troubleshooting](#troubleshooting)

## Prerequisites

The current version of the simulation targets [ROS Noetic Ninjemys](http://wiki.ros.org/noetic/Installation/) distribution and was mainly developed and tested on [Ubuntu 20.04 Focal Fossa](https://releases.ubuntu.com/20.04/).

The tools necessary to build this project can be installed with apt:
```sh
sudo apt install python3-rosdep python3-catkin-tools
```

## Building
This repository uses git submodules to link external repositories that contain the ROS packages. \
When cloning this repository, add the `--recurse-submodules` flag to recursively pull the submodules:
```sh
git clone --recurse-submodules https://github.com/EuropeanRoverChallenge/ERC-Remote-Navigation-Sim.git
```
or if you have already cloned the repository without this option, clone the submodules using:
```sh
git submodule update --init
```
Use the `rosdep` tool to install any missing dependencies. If you are running `rosdep` for the first time, you might have to run:
```sh
sudo rosdep init
```
first. Then, to install the dependencies, type:
```sh
rosdep update
sudo apt update
rosdep install --rosdistro noetic --from-paths src -iy
```
Now, use the `catkin` tool to build the workspace:
```sh
catkin config --extend /opt/ros/noetic
catkin build
```
