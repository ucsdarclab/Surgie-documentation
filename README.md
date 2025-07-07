# G1 Robot Operation Document
*Teleoperation and G1 handling guide.*

---

## Table of Contents
1.  [G1 Humanoid Robot Guide](#g1-humanoid-robot-guide)
2.  [Installation](#installation)
3.  [Usage](#usage)
4.  [Network Configuration](#network-configuration)
5.  [Safety](#safety)
6.  [Troubleshooting](#troubleshooting)

---

## G1 Humanoid Robot Guide

This guide covers the essential setup and operation of the **Unitree G1 Humanoid Robot**.

### Prerequisites

#### Required Skills
-   **Linux:** Basic command line skills.
-   **ROS2:** Familiarity with ROS 2 concepts (nodes, topics).
-   **Programming:** Python or C++ for custom development.

#### PC Minimum Requirements
-   **RAM:** 8 GB+
-   **Storage:** 50 GB free
-   **GPU:** no GPU requirement unless adding some 3rd party policies
-   **OS:** Ubuntu 22.04 LTS

### Remote & App Control
For assistance with the remote controller or mobile app, contact **Soofiyan**.

---

## Installation

Follow these steps to set up the control environment and necessary software packages.

### 1.1. Inverse Kinematics dependencies
First, create and activate a new Conda environment. Then, install the required packages.

```bash
$ conda create -n tv python=3.10
$ conda activate unitree
(unitree) $ conda install pinocchio -c conda-forge
(unitree) $ pip install meshcat
(unitree) $ pip install casadi
````

### 1.2. Unitree SDK

Next, clone and install the `unitree_sdk2_python` library.

```bash
# Install unitree_sdk2_python.
(unitree) $ git clone [https://github.com/unitreerobotics/unitree_sdk2_python.git](https://github.com/unitreerobotics/unitree_sdk2_python.git)
(unitree) $ cd unitree_sdk2_python
(unitree) $ pip install -e .
```

### 1.3. Teleoperation Dependencies Setup

Finally, clone the g1 teleoperation repository and install its specific requirements.

```bash
(unitree) $ cd ~
(unitree) $ git clone git@github.com:Soofiyan/g1_teleoperate.git
(unitree) $ cd ~/g1_teleoperate
(unitree) $ pip install -r requirements.txt
(unitree) $ pip install empy==3.3.4
(unitree) $ pip uninstall typing
```

### 1.4. (Optional) ROS2 install

Go through the README.md file of this repository: [unitree\_ros2](https://github.com/unitreerobotics/unitree_ros2).

-----

## Usage

### How to run the robot ik on meshcat

```bash
# Go to the g1_teleoperate root folder
(unitree) $ cd g1_teleoperate/teleop/robot_control
(unitree) $ python robot_arm_ik_og.py
```

-----

## Network Configuration

This section explains how to establish a direct network connection between your computer and the robot.

### Configuration Steps

1.  Connect a network cable from the robot to your computer.
2.  Enable USB Ethernet on your computer.
3.  The robot's IP address is fixed at **192.168.123.161**. You must set your computer's USB Ethernet IP to the same subnet.
    *Set your computer's IP to **192.168.123.222**.*

![Network configuration example](Images/network_first.jpg)

### Testing the Connection

To verify the connection, ping the robot from your computer's terminal:

```bash
ping 192.168.123.161
```

![Successful ping example](Images/ping.png)

A successful reply indicates the connection is working.

### Identify Your Network Device

You need to find the network card name assigned to this connection. Use the `ifconfig` command.

In the example below, the network card name for the IP **192.168.123.222** is `enxf8e43b808e06`. Note this name, as it's required to run the control examples.

![ifconfig output showing network device name](Images/network_check.png)
-----

## Safety

*(This section is under development.)*

-----

## Troubleshooting

*(This section is under development.)*

-----

© ARClab. All Rights Reserved.
