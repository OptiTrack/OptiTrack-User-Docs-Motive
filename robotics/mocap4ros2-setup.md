---
description: Learn how to use an OptiTrack system to control a robotic arm.
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/robotics/mocap4ros2-setup
---

# MoCap4ROS2 Setup

## Arm Follower Demo Using the Hiwonder JetMax Arm

This demo uses the **mocap4ros2\_optitrack** package to configure the Hiwonder JetMax arm's end effector to follow an arbitrary rigid body using OptiTrack cameras and Motive software.

See our [OptiTrack Robot Applications](optitrack-robot-applications.md) document for robotics use case examples.

{% hint style="success" %}
The source code for this tutorial is located at [OptiTrack/mocap4ros2\_optitrack\_demos](https://github.com/OptiTrack/mocap4ros2_optitrack_demos).
{% endhint %}

### About this Demo

This demo provides an example workflow to use an OptiTrack system to control a robotic arm. The demo uses a 3DOF robot arm, the Hiwonder JetMax. This robot was selected for its affordability, desktop size, and ROS2 support, with minimal setup required to get up and going. The provided packages from [JetMaxRoboticArm](https://github.com/JetMaxRoboticArm) work well out of the box.

The package provided by Hiwonder to control the arm with a python package, [jetmax\_ebap](https://github.com/JetMaxRoboticArm/jetmax_ebap), can also be adapted into a ROS package fairly easily.

{% hint style="success" %}
While the scope of this example is limited to the specified hardware, similar concepts should work with other robotic arms.
{% endhint %}

## Setup Requirements

### Required Hardware

* A computer capable of running Motive and at least 3 OptiTrack cameras to serve as the Motive PC. Please see the [Host PC Requirements](../motive/installation-and-activation.md#host-pc-requirements) section of the [Installation and License Activation](../motive/installation-and-activation.md) page. &#x20;
* A second computer running Ubuntu 20.04 or greater (the Ubuntu companion computer). Use a separate PC rather than an instance of WSL2 on the Motive PC. For more information, please see the section [Unable to Use WSL2](mocap4ros2-setup.md#unable-to-use-wsl2), below.&#x20;
* &#x20;A [JetMax Hiwonder Robot](https://www.hiwonder.com/products/jetmax?variant=39645677125719).
* Two [rigid bodies](../motive/rigid-body-tracking/) and a [calibration square](../motive/calibration/calibration-squares.md).
* A router or switch with an internet connection, separate from the OptiTrack switch.
* A second Network Interface Card (NIC) for the Motive PC, to connect to the Arm Follower network.
* An ethernet cable to connect the JetMax to the internet-connected router.

### Required Software

Visit the [OptiTrack Downloads](https://optitrack.com/support/downloads/) page for the following software packages:

* Motive 3.1 (or above), installed on the Host PC.
* **jetmax\_optitrack\_feedback** package, installed on the JetMax's Jetson Nano.
* **mocap4ros2\_optitrack**, installed on the Ubuntu Companion computer (originally from https://github.com/OptiTrack/mocap4ros2\_optitrack).
* **mocap\_msgs**, installed on the Ubuntu Companion computer (originally from https://github.com/OptiTrack/mocap\_msgs).
* **tf\_repub**, installed on the Ubuntu Companion computer.

## Connect Hardware&#x20;

This system requires two separate networks, using independent switches, to function:

* One switch to network the JetMax, Ubuntu Companion Computer, and Motive PC. This switch can optionally be connected to the internet.&#x20;
* The OptiTrack camera network, with only the cameras and the Motive PC connected. For more details about configuring the camera network, please see the [Ethernet Camera Network Setup](../hardware/cabling-and-wiring/) chapter.&#x20;

The diagram below shows how to network the necessary devices together:

<figure><img src="../.gitbook/assets/MoCap4ROS2 Network configuration.png" alt=""><figcaption><p>Networking configuration.</p></figcaption></figure>

{% hint style="info" %}
The Ubuntu companion computer is required to pass data from the Motive PC to the JetMax.

Please see the section [Need for companion computer](mocap4ros2-setup.md#need-for-companion-computer), below, for more information.
{% endhint %}

### Ubuntu Companion Computer Configuration

We tested using Ubuntu 22.04 with ROS2 Iron. Ubuntu 20.04+ with ROS2 Foxy or newer should also work adequately.

Some familiarity with ROS will help in later steps. [Tutorials for using ROS2 Iron](https://docs.ros.org/en/iron/Tutorials.html) are available from the docs.ros.org website.&#x20;

{% hint style="warning" %}
**ROS2 versions are dependent on your OS so pay attention to the version you install.**&#x20;

For installation instructions for Ubuntu 22.04, please see [https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html ](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html)
{% endhint %}

#### Create Package and Setup Config Files

```bash
cd ~
git clone https://github.com/OptiTrack/robot_arm_follower_demo.git
mkdir -p ~/optitrack_companion_ws/src
cd ~/optitrack_companion_ws/src
# copy mocap_msgs, mocap4ros2_optitrack, and tf_repub to the src directory
cp -r ~/robot_arm_follower_demo/packages_on_ubuntu_companion/* ~/optitrack_companion_ws/src
cd ~/optitrack_companion_ws
source /opt/ros/<your-ros-distro>/setup.bash
colcon build
```

If the build was successful, the _optitrack\_companion\_ws_ will be populated with _build_, _install_, and _log_ directories.&#x20;

### JetMax Computer Configuration

There are two methods for operating the Jetson Nano on the JetMax robot:

1. Using the SD card image that ships with the JetMax, running Ubuntu 18.04.
2. Using an SD card image with a fresh install of [Ubuntu 18.04](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write) supported by NVIDIA.

{% hint style="warning" %}
While Ubuntu 18.04 is no longer a supported OS, it is the most recent Ubuntu version that NVIDIA supports for the JetMax. You may be able to run the JetMax using a more recent version of Ubuntu, however that configuration will not be supported by NVIDIA.&#x20;
{% endhint %}

If using the SD card image that ships with the JetMax, skip to the [Build the Code](mocap4ros2-setup.md#build-the-code) section.&#x20;

#### Install Ubuntu 18.04

1. Reflash the SD following the SD card Getting Started guide from Nvidia
2.  Download the jetson expansion board access package on the home directory and install:

    ```bash
    git clone https://github.com/JetMaxRoboticArm/jetmax_ebap.git
    cd jetmax_ebap
    python3 setup.py install
    ```
3. Test access to the board using the [jetmax\_ebap readme](https://github.com/JetMaxRoboticArm/jetmax_ebap). If you receive permissions errors, try using _sudo python3_ before running commands to see if this allows you to access the GPIO.
4. If permission errors persist, use the _chmod_ or _adduser_ commands to update or add access.&#x20;
5. Install ROS2 Foxy from [https://docs.ros.org/en/foxy/Installation.html](https://docs.ros.org/en/foxy/Installation.html).&#x20;

{% hint style="warning" %}
While ROS2 Foxy is no longer a supported version, it is the version required for Ubuntu 18.04.
{% endhint %}

For our testing, we flashed the SD card with the official [image for the Jetson Nano](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write), which contains Ubuntu 18.04, a version that is end of life and losing support. We installed ROS2 Dashing and, because it is losing support, transform (tf2) messages are not supported. We implemented a workaround to republish the tf2 messages with _tf\_repub_ package installed on the Ubuntu companion computer.

To run the entire system on the JetMax, either:

1. Update the OS
2. Develop a solution to use _tf2\_ros._ Perhaps use a C++ executable after building tf2 from source or figure out how to install the tf2\_ros python package.&#x20;
3. Rtun the system without using tf2 messages.

#### Build the Code

Create the package and setup configuration files.

```bash
cd ~
git clone https://github.com/OptiTrack/robot_arm_follower_demo.git
mkdir -p ~/optitrack_robot_ws/src
cd ~/optitrack_robot_ws/src
# copy mocap_msgs, mocap4ros2_optitrack, and tf_repub to the src directory
cp -r ~/robot_arm_follower_demo/packages_on_jetmax/* ~/optitrack_robot_ws/src
cd ~/optitrack_robot_ws
source /opt/ros/<your-ros-distro>/setup.bash
colcon build
```

### OptiTrack Configuration

Please see our [Quick Start Guide](https://docs.optitrack.com/quick-start-guides/quick-start-guide-getting-started) for detailed instructions to setup an OptiTrack camera system and install the Motive software.

For an easier setup process, keep track of the orientation of the calibration square during the initial configuration. The orientation of the JetMax should match the following image when using a calibration square:&#x20;

<figure><img src="../.gitbook/assets/JetMax Arm orientation2.png" alt="" width="563"><figcaption><p>JetMax oriented with the calibration square.</p></figcaption></figure>

#### Create Rigid Bodies

For instructions to create rigid bodies, please see the [Rigid Body Tracking](../motive/rigid-body-tracking/) page.&#x20;

Create two rigid bodies:

* _**end\_effector**_ - mount this to the end effector of the arm.
* _**base\_link**_ - place this near the robot arm. The exact position or how the rigid body is attached does not matter as long as it's secured and visible to the cameras.&#x20;

#### Enable NatNet Streaming

For a detailed overview of streaming, please see the pages in our [NatNet chapter](../developer-tools/natnet-sdk/).&#x20;

* Click the streaming button <img src="../.gitbook/assets/Control Deck - Streaming On SMALL (1).png" alt="" data-size="line"> in the lower right corner of the Motive Control Deck to open the [Applications Settings](../motive-ui-panes/settings/) panel to the [Streaming tab](../motive-ui-panes/settings/settings-streaming.md).&#x20;
* Click to enable NatNet streaming.&#x20;
* Set the local interface to an IP on the same network as the Ubuntu Companion computer.&#x20;

## Run the Program

With Motive streaming, **launch the Ubuntu Companion Computer:**

```bash
# terminal 1
cd ~/optitrack_companion_ws
source install/setup.bash
ros2 launch mocap_optitrack_driver optitrack2.launch.py
```

```bash
# terminal 2
cd ~/optitrack_companion_ws
source install/setup.bash
ros2 run tf_repub transform_republisher
```

**Launch the JetMax Arm.**&#x20;

We recommend using SSH to connect to the JetMax for this step.

```bash
# terminal 1
cd ~/optitrack_robot_ws
source install/setup.bash
ros2 run jetmax_optitrack_feedback jetmax_feedback_node
```

Ensure the _base\_link_ rigid body is near the robot.

```bash
# terminal 2
cd ~/optitrack_robot_ws
source install/setup.bash
ros2 topic pub /get_target_pos std_msgs/msg/Bool "data: True" --once
```

Start moving the base link rigid body to have the robot follow!

{% embed url="https://vimeo.com/996195390/a88a165fc0?share=copy" %}

#### What is going on?

In this demo, the JetMax maintains a static distance between its end effector and the target rigid body. This is done by constantly measuring the distance between the _end\_effector_ and _base\_link_ Rigid Bodies with OptiTrack. The robot sees the change in distance and adjusts its position to compensate.

The program issues a [cartesian control command](https://wiki.ros.org/ros_controllers_cartesian) to the robot, then an [inverse kinematics](https://en.wikipedia.org/wiki/Inverse_kinematics) engine computes the [target joint angles](https://wiki.ros.org/joint_state_controller) for the robot given a [description of the robot's mechanics](https://docs.ros.org/en/iron/Tutorials/Intermediate/URDF/URDF-Main.html).

Take a look at the links provided to learn more about locomotion for a robot arm using ROS.

A more comprehensive example of Standard ROS practice can be found here: [Universal\_Robots\_ROS2\_Gazebo\_Simulation](https://github.com/UniversalRobots/Universal_Robots_ROS2_Gazebo_Simulation)

## Issues and Possible Improvements

#### Need for Companion Computer

The Ubuntu companion computer is needed because the NatNet binary is not yet available for ARM devices. This means that the _mocap4ros2\_optitrack_ package had to run on a computer that did not have an ARM architecture.

When the ARM library for NatNet becomes available, _mocap4ros2\_optitrack_ will run on an ARM device and a companion computer will no longer be needed.&#x20;

#### Unable to use WSL2

The Ubuntu companion computer cannot be a WSL2 instance of the Windows host running Motive because it is difficult to network the WSL2 instance to be on the same LAN as the robot arm computer. By default, the network of the WSL2 instance is a NAT subset defined by the host windows machine. This link may be useful for giving a static IP on the same network as the Windows host, although this is untested: [assigning-static-ip-addresses-in-wsl2.md](https://gist.github.com/wllmsash/1636b86eed45e4024fb9b7ecd25378ce)

{% hint style="info" %}
The _mocap4ros2\_optitrack_ plugin could run on a WSL2 standalone PC because Motive and the WSL2 instance can easily exist on the network created by the windows host.
{% endhint %}

#### Orientation of the JetMax

The orientation of the JetMax should not need to be fixed. Ideally, in the future, a few markers placed on the base of the robot would allow the calculated target position to account for the orientation of the robot instead of assuming orientation.
