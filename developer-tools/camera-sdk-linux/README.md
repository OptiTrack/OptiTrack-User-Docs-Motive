---
description: An overview of the Linux version of the Camera SDK.
---

# Camera SDK for Linux

## Overview

{% hint style="danger" %}
The Camera SDK for Linux currently does not include support for USB cameras.&#x20;
{% endhint %}

The Camera SDK for Linux provides hardware controls (cameras and hubs) and access to the most fundamental frame data, such as grayscale images and 2D object information, from each camera. Using the Camera SDK for Linux, you can develop your own image processing applications that utilize the capabilities of the OptiTrack cameras in either Ubuntu or Fedora.&#x20;

To download this free tool, visit the OptiTrack [download](https://optitrack.com/support/downloads/developer-tools.html) site.

{% hint style="warning" %}
**Note:** 3D tracking features are not directly supported with Camera SDK but they are featured via the Motive API. For more information on the Camera SDK, visit our [website](http://www.optitrack.com/products/camera-sdk/).
{% endhint %}

{% hint style="info" %}
The Camera SDK for Linux is compatible only with the same released version of Motive. For instance, if you are using Motive 3.4.0, download and use the Camera SDK version 3.4.0.&#x20;
{% endhint %}

### Features

* Camera hardware controls
* Receiving frame data and 2D object data from each camera
* Sample applications with source code

### Contents

Unzip the Camera SDK for Linux from the OptiTrack downloads site. The&#x20;

* **(\CameraSDK\lib)** Includes native C++ application library.
* **(\CameraSDK\include)** Includes header files for the SDK. Usage of each class is commented within the header files.
* **(\CameraSDK\samples)** Includes sample projects that employ the Camera SDK for Linux, including the CameraViewerApp. Source code for these applications are included for additional references.

## Installation

Install Qt, Cmake and libjpeg on the Linux computer.

**Ubuntu**

{% code overflow="wrap" %}
```
ubuntu: sudo apt update && sudo apt install -y libjpeg-dev cmake qt6-base-dev
```
{% endcode %}

**Fedora**

{% code overflow="wrap" %}
```
sudo dnf update && sudo dnf install -y libjpeg-turbo-devel cmake qt6-qtbase-devel
```
{% endcode %}

### Build the Executable

#### linuxBuild.sh

The sample file linuxBuild.sh is located in **\CameraSDK\samples\CameraViewerApp.**&#x20;

Change the mode of the file to allow the user to read, write, and execute the file:

```
chmod +x linuxBuild.sh
```

#### Network Settings

Set the network port used for the camera system to use link local only. Go to:&#x20;

_Settings > Network > Wired Settings (port for cameras) > IPv4 > Ipv4Method_.&#x20;

Set the value to _Link-Local Only._

### Color Camera Installation

Additional software is required to include Prime Color Camera functionality.&#x20;

**Ubuntu**

{% code overflow="wrap" %}
```
sudo apt install ffmpeg -y
```
{% endcode %}

**Fedora**

{% code overflow="wrap" %}
```
sudo dnf install ffmpeg ffmpeg-devel -y
```
{% endcode %}

{% hint style="warning" %}
Fedora users may be required to enable RPM fusion.&#x20;

**For the free version:**

{% code overflow="wrap" %}
```
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
```
{% endcode %}

**For the non-free version:**

{% code overflow="wrap" %}
```
sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```
{% endcode %}
{% endhint %}

### Run the Executable

Run the linuxBuild.sh file from the _CameraViewerApp_ directory.&#x20;

```
./linuxBuild.sh <Path-to-camera-sdk-path> 
```

To include Prime Color Cameras in the data capture, build using the flag _--ffmpeg_:&#x20;

{% code overflow="wrap" %}
```
./linuxBuild.sh <Path-to-camera-sdk-path> --ffmpeg 
```
{% endcode %}
