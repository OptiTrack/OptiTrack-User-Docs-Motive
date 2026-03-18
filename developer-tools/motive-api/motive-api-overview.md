# Motive API Overview

{% hint style="danger" %}
**Important Note:**

Motive API wiki pages are being updated for 3.0 beta. Some of the functions may be missing in the documentation. Please refer to the MotiveAPI.h header file for information on functions that are not documented here.
{% endhint %}

## Overview

The Motive API allows control of, and access to, the backend software platform of Motive via C/C++ interface. In other words, the Motive API offers Motive functions without the graphical user interface on top. Using the API, you can employ several features of Motive in your custom applications, such as accessing 2D camera images, marker centroid data, unlabeled 3D points, labeled markers, and Rigid Body tracking data. When you install Motive, all of the required components for utilizing the API are installed within the Motive install directory. The key files for using the Motive API are listed in the below section.

### _**What it offers:**_

* Camera control
* Frame control
* Point Cloud reconstruction engine control
* Obtain and use reconstructed 3D Marker data
* Rigid body tracking
* Query results
* Stream results over the network

### _**What it doesn't offer**_

* In-depth hardware control (e.g. hardware sync customization). Use the Camera SDK instead.
* Direct support for data recording and playback.
* Control over peripheral devices (Force plates and NI-DAQ)
* Functionalities for Skeleton assets.

### _**Requirements**_

* The Motive API is supported in Windows only
* Must have a valid Motive license and a corresponding Hardware or Security key.

## Files List

When you install Motive, all of the required components of the Motive API will be placed within the installation directory, and by default, Motive is installed in `C:\Program Files\OptiTrack\Motive`. The following table lists all of the key files of the API and where they could be found.

| Filename               | Directory                                   | Description                                                                                                                                                                                                                                                                                                                    |
| ---------------------- | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| MotiveAPI.h            | \[Motive Install Directory]\inc\MotiveAPI.h | The header file **MotiveAPI.h** contains declarations for functions and classes of the API. Necessary functions and classes are thoroughly commented within this file. This header file must be #included in your source code for utilizing the Motive API functions.                                                          |
| lib folder             | \[Motive Install Directory]\lib             | This folder includes C++ 64-bit library files (.lib and .dll) for employing the Motive API. The library is compiled using Visual Studio 2013 with the dynamic run-time (\MD) library, so make sure the client application also uses the same settings. _32-bit NPTrackingTools library has been deprecated since version 2.1._ |
| Core (Sample projects) | \[Motive Install Directory]\inc\ Core       | This folder contains sample  projects (BuildConfig.h, Label.h, Marker.h, UID.h, Vector3.h) that use the Motive API for accessing cameras, markers, and Rigid Body tracking information. Refer to this folder to find out how the API could be used.                                                                            |
| Platforms folder       | \[Motive Install Directory]\plugins\\       | The platforms folder is located in the plugins folder and it contains _qwindows.dll_ which is required for running applications using the Motive API. Copy and paste this folder into the EXE directory.                                                                                                                       |
| Third-party libraries  | \[Motive Install Directory]                 | Third-party DLL libraries are required for all applications built against the API. Please see [Motive API: Quick Start Guide](motive-api-quick-start-guide.md) for more information                                                                                                                                            |

## API Guide / Function Reference

#### [**Quick Start Guide: Motive API**](motive-api-quick-start-guide.md)

This guide introduces some of the commonly used functions of the Motive API.

![](<../../.gitbook/assets/image (864).png>)

#### [**Motive API Function Reference**](motive-api-function-reference.md)

The following page provides a full list of the Motive API functions.

![](<../../.gitbook/assets/image (908).png>)

## eMotiveAPIResult & VIDEO TYPES

Many of the Motive API functions return their results as integer values defined _eMotiveAPIResult_. This value expresses the outcome of the result. Not only does it indicate whether the function operated successfully or not, but it also provides more detailed information on what type of error has occurred. When you get the eMotiveAPIResult output from a function, you can use the [TT\_GetResultString](motive-api-function-reference.md#tt_getresultstring) function to get the plain text result that corre sponds to the error message.

{% code overflow="wrap" %}
```
const char		*TT_GetResultString( eMotiveAPIResult result ); // Returns text of detail information on the result.
```
{% endcode %}

Also, camera video types, or image processing modes, are expressed as integer values as well. These values are listed below and are commented within the header file as well.

**eMotiveAPI Result Values**

```
    kApiResult_Success = 0,
```

**Camera Video Type Definitions**

```
    kVideoType_Segment = 0,
    kVideoType_Grayscale = 1,
    kVideoType_Object = 2,
    kVideoType_Precision = 4,
    kVideoType_MJPEG = 6,
    kVideoType_ColorH264 = 9
```
