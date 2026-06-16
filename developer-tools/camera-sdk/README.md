---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/developer-tools/camera-sdk
---

# Camera SDK

## Overview

The Camera SDK provides hardware (cameras and hubs) controls and access to the most fundamental frame data, such as grayscale images and 2D object information, from each camera. Using the Camera SDK, you can develop your own image processing applications that utilize the capabilities of the OptiTrack cameras. The Camera SDK is a free tool that can be downloaded from our website.

{% hint style="warning" %}
**Note:** 3D tracking features are not directly supported with Camera SDK but they are featured via the Motive API. For more information on the Camera SDK, visit our [website](https://www.optitrack.com/software/camera-sdk).
{% endhint %}

{% hint style="info" %}
The Camera SDK is compatible only with the same released version of Motive. For instance, if you are using Motive 3.1.1, download and use the Camera SDK version 3.1.1.&#x20;
{% endhint %}

### Features

* Camera hardware controls
* Receiving frame data and 2D object data from each camera
* Device synchronization controls
* Sample applications with source code

### Contents

After you install the Camera SDK, there will be a folder in your OptiTrack installation directory. This folder can also be accessed from `Windows start menu → OptiTrack → Camera SDK`:

* **(\OptiTrack\CameraSDK\bin)** Includes an executable sample application, visualtest.exe, which was developed using the Camera SDK. This sample application allows you to configure camera settings and monitor captured 2D frames from each camera.
* **(\OptiTrack\CameraSDK\lib)** Includes native C++ application construction library.
* **(\OptiTrack\CameraSDK\include)** Includes header files for the SDK. Usage of each class is commented within the header files.
* **(\OptiTrack\CameraSDK\doc)** Includes topic specific instructions on how to utilize the Camera SDK.
* **(\OptiTrack\CameraSDK\samples)** Includes sample projects that employ the Camera SDK. Source code for these applications are included for additional references.
