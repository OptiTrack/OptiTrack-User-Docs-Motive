---
description: An introduction to the Motive API.
---

# Motive API Overview

{% hint style="danger" %}
**Important Note:**

The Motive API documentation is being updated for 3.1 and some of the functions may not yet be in the documentation. Please refer to the _MotiveAPI_ header file for any information that is not included in the online user guide.
{% endhint %}

## Overview

The Motive API allows access to and control of the backend software platform for Motive via a C/C++ interface, performing Motive functions without the graphical user interface on top. With the API, users can employ several features of Motive in custom applications, such as accessing 2D camera images, marker centroid data, unlabeled 3D points, labeled markers, and Rigid Body tracking data.&#x20;

All of the required components for utilizing the API are included in the Motive install directory when the application is installed. The key files for using the Motive API are listed in the below section.

### _**What it offers:**_

* Camera control
* Frame control
* Point Cloud reconstruction engine control
* Ability to obtain and use reconstructed 3D Marker data
* Rigid body tracking
* Query results
* Ability to stream results over the network

### _**What it doesn't offer**_

* In-depth hardware control (e.g. hardware sync customization). Use the Camera SDK for this.
* Direct support for data recording and playback.
* Control over peripheral devices (Force plates and NI-DAQ).
* Functionality for Skeleton assets.

### _**Requirements**_

* The Motive API is supported in Windows only
* Must have a valid Motive license and a corresponding Hardware or Security key.

## Files List

When Motive is installed, all of the required components of the Motive API are placed in folders within the installation directory. By default, this directory is `C:\Program Files\OptiTrack\Motive`.&#x20;

The following section describes the key files of the API and where each is located.

***

#### MotiveAPI.h

\[Motive Install Directory]\inc\MotiveAPI.h

The header file MotiveAPI.h contains declarations for functions and classes of the API. Necessary functions and classes are thoroughly commented within this file. This header file must be included in the source code for utilizing the Motive API functions.

***

#### lib folder

\[Motive Install Directory]\lib

This folder includes C++ 64-bit library files (.lib and .dll) for employing the Motive API.&#x20;

{% hint style="info" %}
The library is compiled using Visual Studio 2019 with the dynamic run-time (\MD) library, so make sure the client application also uses the same settings.
{% endhint %}

***

#### Samples project

\[Motive Install Directory]\Samples\MotiveAPI\\

Samples in a Visual Studio project (samples.sln)  for accessing Motive functionality such as cameras, markers, and Rigid Body tracking information. Refer to this folder to find out how the API can be used.

***

#### Platforms folder

\[Motive Install Directory]\plugins

The platforms folder contains _qwindows.dll,_ which is required for running applications using the Motive API. Copy and paste this folder into the EXE directory.

***

#### Third-party libraries

\[Motive Install Directory]

Third-party DLL libraries are required for all applications built against the API. Please see [Motive API: Quick Start Guide](motive-api-quick-start-guide.md) for more information.&#x20;

***

## API Guide / Function Reference

#### [**Quick Start Guide: Motive API**](motive-api-quick-start-guide.md)

This guide introduces some of the commonly used functions of the Motive API.

#### [**Motive API Function Reference**](motive-api-function-reference.md)

The following page provides a full list of the Motive API functions.

## eResult & Video Types

Many of the Motive API functions return their results as integer values defined as an eResult. This value expresses the outcome of the result. eResult values indicate if the function operated successfully, and if not, they provide detailed information on the type of error that occurred.&#x20;

When you get the eResult output from a function, you can use the MapToResultString function to get the plain text result that corresponds to the error message.

{% code overflow="wrap" %}
```
MOTIVE_API const std::wstring MapToResultString( eResult result ); // Returns text of detail information on the result.
```
{% endcode %}

Camera video types, or image processing modes, are expressed as integer values as well. These values are listed below and are also commented within the header file.

**eResult Values**

```
enum eResult
{
    kApiResult_Success = 0,
    kApiResult_Failed,
    kApiResult_FileNotFound,
    kApiResult_LoadFailed,
    kApiResult_SaveFailed,
    kApiResult_InvalidFile,
    kApiResult_InvalidLicense,
    kApiResult_NoFrameAvailable,
    kApiResult_TooFewMarkers,
    kApiResult_ToManyMarkers,
    kApiResult_UnableToFindGroundPlane,
    kApiResult_UnableGetGroundPlane,
    kApiResult_RemoveCalibrationSquare
};
```

**Camera Video Type Definitions**

```
enum eVideoType
{
    kVideoType_Segment = 0,
    kVideoType_Grayscale = 1,
    kVideoType_Object = 2,
    kVideoType_Precision = 4,
    kVideoType_MJPEG = 6,
    kVideoType_ColorH264 = 9
};
```
