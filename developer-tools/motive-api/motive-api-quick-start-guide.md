# Motive API: Quick Start Guide

## Overview

{% hint style="danger" %}
**SDK/API Support Disclaimer**

OptiTrack provides developer tools to enable our customers across a broad set of applications to utilize their systems in the ways that best suit them. Our Motive API through the NatNet SDK and Camera SDK is designed to enable experienced software developers to integrate data transfer and/or system operation with their preferred systems and pipelines. Sample projects are provided with each tool, and we strongly recommend users reference or use the samples as reliable starting points.

The following list specifies the range of support OptiTrack provides for the SDK and API tools:

* Using the SDK/API tools requires background knowledge of software development. We do not provide support for basic project setup, compiling, and linking when using the SDK/API to create your own applications.
* We ensure the SDK tools and their libraries work as intended. We do not provide support for custom developed applications that have been programmed or modified by users using the SDK tools.
* Ticketed support will be provided for licensed Motive users using the Motive API and/or the NatNet SDK tools from the included libraries and sample source codes only.
* The Camera SDK is a free product. We do not provide free ticketed support for it.
* For other questions, please check out the [NaturalPoint forums](https://forums.naturalpoint.com/). Very often, similar development issues are reported and solved there.

Documentation is written to the latest build of the specified version.&#x20;
{% endhint %}

This guide provides detailed instructions for commonly used functions of the Motive API for developing custom applications. For a full list of functions, refer to the [Motive API: Function Reference](https://docs.optitrack.com/v3.1/developer-tools/motive-api/motive-api-function-reference) page. For a sample use case of the API functions, please check out the provided [_marker_](https://docs.optitrack.com/v3.1/developer-tools/motive-api/motive-api-overview#files-list) project.

In this guide, the following topics will be covered:

* Library files and header files
* Initialization and shutdown
* Capture setup (Calibration)
* Configuring camera settings
* Updating captured frames
* 3D marker tracking
* Rigid body tracking
* Data streaming

## Environment Setup

### Library Files

When developing a Motive API project, the linker needs to know where to find the required library files. Do this either by specifying its location within the project or by copying these files to the project folder.

**MotiveAPI.h**

Motive API libraries (.lib and .dll) are in the _lib_ folder within the Motive install directory, located by default at `C:\Program Files\OptiTrack\Motive\lib`. This folder contains library files for both 64-bit (MotiveAPI.dll and MotiveAPI.lib) platforms.

When using the API library, all of the required DLL files must be located in the executable directory. If necessary, copy and paste the MotiveAPI.dll file into the folder with the executable file.

**Third-party Libraries**

* Additional third-party libraries are required for Motive API, and most of the DLL files for these libraries can be found in the Motive install directory `C:\Program Files\OptiTrack\Motive\`. Copy and paste all of the DLL files from the Motive installation directory into the directory of the Motive API project to use them. Highlighted items in the below image are all required DLL files.
* Lastly, copy the `C:\Program Files\OptiTrack\Motive\plugins\platforms` folder and its contents into the EXE folder since those libraries will also be used.

![Library files required to run a Motive API application.](<../../.gitbook/assets/image (921).png>)

### Header Files

Function declarations and classes are contained in the header file MotiveAPI.h, located in the folder `C:\Program Files\OptiTrack\Motive\inc\`.

Always include the directive syntax for adding the MotiveAPI.h header file for all programs that are developed against the Motive API.

**Note:** You can define this directory by using the MOTIVEAPI`_INC`, `MOTIVEAPI_LIB` environment variables. Check the project properties (Visual Studio) of the provided [_marker_](https://docs.optitrack.com/v3.1/developer-tools/motive-api/motive-api-overview#files-list) project for a sample project configuration.

### Motive Files

Motive API, by default, loads the default calibration (CAL) and Application profile (MOTIVE) files from the program data directory unless otherwise specified. Motive also loads these files at startup. They are located in the following folders:

* Default System Calibration: C:\ProgramData\OptiTrack\Motive\System Calibration.cal
* Default Application Profile: C:\ProgramData\OptiTrack\MotiveProfile.motive

Both files can be exported and imported into Motive as needed for the project:

* The [application profile](../../motive/motive-basics.md#motive-user-profile-.motive) is imported using the [TT\_LoadProfile](motive-api-function-reference.md#tt_loadprofile-tt_loadprofilew) function to obtain software settings and trackable asset definitions.
* The calibration files can be loaded using the [TT\_LoadCalibration](motive-api-function-reference.md#tt_loadcalibration-tt_loadcalibrationw) function to ensure reliable 3D tracking data is obtained.

## Initialization and Shutdown

When using the API, connected devices and the Motive API library need to be properly initialized at the beginning of a program and closed down at the end.

### Initialization

To initialize all of the connected cameras, call the [TT\_Initialize](motive-api-function-reference.md#tt_initialize) function. This function initializes the API library and gets the cameras ready for capturing data, so always call this function at the beginning of a program. If you attempt to use the API functions without the initialization, you will get an error.

```
// Initializing all connected cameras
TT_Initialize();
```

{% hint style="info" %}
**Motive Profile Load**

Please note that TT\_Initialization loads the default Motive profiles (MOTIVE) from the ProgramData directory during the initialization process. To load Motive profile, or settings, from a specified directory, use TT\_LoadProfile.
{% endhint %}

### Update

The [TT\_Update](motive-api-function-reference.md#tt_update) function is primarily used for updating captured frames, which will be covered later, but there is another use. The TT\_Update can also be called to update a list of connected devices, and you can call this function after the initialization to make sure all of the newly connected devices are properly initialized in the beginning.

```
// Initializing all connected cameras
TT_Initialize();

//Update for newly arrive cameras
TT_Update();
```

### Shutdown

When exiting out of a program, make sure to call the [TT\_Shutdown](motive-api-function-reference.md#tt_shutdown) function to completely release and close down all of the connected devices. Cameras may fail to shut down completely when this function is not called.

```
// Closing down all of the connected cameras
TT_Shutdown();
return 0;
```

## Setup the Project

### Motive Application Profile

The Motive application profile (MOTIVE) stores all the trackable assets involved in a capture and software configurations including [application settings](../../motive-ui-panes/settings/) and [data streaming settings](../../motive/data-streaming.md). When using the API, it is strongly recommended to first configure all of the settings and define trackable assets in Motive, export a profile MOTIVE file, and then load the file by calling the [TT\_LoadProfile](motive-api-function-reference.md#tt_loadprofile-tt_loadprofilew) function. This way, you can adjust the settings for your need in advance and apply them to your program without worrying about configuring individual settings.

{% code overflow="wrap" %}
```
TT_LoadProfile("UserProfile.motive"); 	// Loading application profile, UserProfile.motive
```
{% endcode %}

### Camera Calibration

Cameras must be calibrated in order to track in 3D space. However, since camera calibration is a complex process, and because of this, it's easier to have the camera system calibrated from Motive, export the camera calibration file (CAL), and the exported file can be loaded into custom applications that are developed against the API. Once the calibration data is loaded, the 3D tracking functions can be used. For detailed instructions on camera calibration in Motive, please read through the [Calibration](../../motive/calibration/) page.

```
TT_LoadCalibration("CameraCal.cal"); 	// Loading CAL file
```

**Loading Calibration**

1. Open Motive.
2. _\[Motive] Calibrate:_ Calibrate camera system using the Calibration panel. Read through the [Calibration](../../motive/calibration/) page for details.
3. _\[Motive] Export:_ After the system has been calibrated, export [the calibration file (CAL)](../../motive/motive-basics.md#file-management) from Motive.
4. Close out of Motive.
5. _\[API] Load:_ Import calibration onto your custom application by calling the [TT\_LoadCalibration](motive-api-function-reference.md#tt_loadcalibration-tt_loadcalibrationw) function to import CAL files.
6. When successfully loaded, you will be able to obtain 3D tracking data using the API functions.

{% embed url="https://www.youtube.com/watch?t=136s&v=aK1cpr6ShPE" %}
Camera calibration overview.
{% endembed %}

{% hint style="info" %}
**Note:**

* _Calibration Files:_ When using the exported calibration files, make sure to use only valid calibration. Exported calibration file can be used again as long as the system setup remains unchanged. Note that the file will no longer be valid if any of the system setups have been altered after the calibration. Also, calibration quality may degrade over time due to environmental factors. For these reasons, we recommend re-calibrating the system routinely to guarantee the best tracking quality.
* _Tracking Bars:_ If you are using a tracking bar, camera calibration is not required for tracking 3D points.
{% endhint %}

## Camera Settings

Connected cameras are accessible by index numbers. The camera indexes are assigned in the order the cameras are initialized. Most of the API functions for controlling cameras require an index value. When processing all of the cameras, use the [TT\_CameraCount](motive-api-function-reference.md#tt_cameracount) function to obtain the total camera count and process each camera within a loop. For pointing to a specific camera, you can use the [TT\_CameraID](motive-api-function-reference.md#tt_cameraid) or [TT\_CameraName](motive-api-function-reference.md#tt_cameraname) functions to check and use the camera with given its index value. This section covers Motive API functions for checking and configuring camera frame rate, camera video type, camera exposure, pixel brightness threshold, and IR illumination intensity.

### Fetching Camera Settings

The following functions return integer values for the configured settings of a camera specified by its index number. Camera video type is returned as an integer value that represents a image processing mode, as listed in the [VIDEOTYPE](motive-api-overview.md#npresult-and-video-types).

These camera settings are equivalent to the settings that are listed in the Devices pane of Motive. For more information on each of the camera settings, refer to the [Devices pane](../../motive-ui-panes/devices-pane.md) page.

```
TT_CameraVideoType(int cameraIndex)      // Returns Video Type
TT_CameraExposure (int cameraIndex)      // Returns Camera Exposure
TT_CameraThreshold(int cameraIndex)      // Returns Pixel Threshold
TT_CameraIntensity(int cameraIndex)      // Returns IR Illumination Intensity
TT_CameraFrameRate(int cameraIndex)      // Returns Camera Frame Rate
```

### Configuring Settings

Now that we have covered functions for obtaining configured settings, now let's modify some of them. There are two main functions for adjusting the camera settings: [TT\_SetCameraSettings](https://v30.wiki.optitrack.com/index.php?title=Motive_API:_Function_Reference#TT_SetCameraSettings) and [TT\_SetCameraFramerate](motive-api-function-reference.md#tt_setcameraframerate). The TT\_SetCameraSettings function configures video type, exposure, threshold, and intensity settings of a camera which is specified by its index number. The TT\_SetCameraFrameRate is used for configuring frame rate of a camera. Supported frame rate range may vary for different camera models. Check the device specifications and apply the frame rates only within the supported range.

{% code overflow="wrap" %}
```
TT_SetCameraSettings(int cameraIndex, int videoType, int exposure, int threshold, int intensity);
```
{% endcode %}

```
TT_SetCameraFrameRate(int cameraIndex, int framerate);
```

If you wish to keep part of the current camera settings, you can use the above functions to obtain the configured settings (e.g. TT\_CameraVideoType, TT\_CameraFrameRate, TT\_CameraExposure, etc.) and use them as input arguments for the TT\_SetCameraSettings function. The following example demonstrates modifying frame rate and IR illumination intensity for all of the cameras, while keeping the other settings constant.

```
//== Changing exposure and threshold settings for all of the cameras ==//
int cameraCount = TT_CameraCount();
int intensity = 10;
int framerate = 100;

for (int i = 0; i < cameraCount; i++)
{
	TT_SetCameraSettings(i, TT_CameraVideoType(i), TT_CameraExposure(i),
					TT_CameraThreshold(i), intensity);

	TT_SetCameraFrameRate(i, framerate);

	//== Outputting the Settings ==//
	printf("Camera #%d:\n", i);
	printf("\tFPS: %d\n\tIntensity: %d\n\tExposure: %d\n\tIntensity: %d\n\tVideo Type:%d\n", 
			TT_CameraFrameRate(i), TT_CameraIntensity(i), TT_CameraExposure(i), 
			TT_CameraIntensity(i),TT_CameraVideoType(i));
}
```

![Sample output.](<../../.gitbook/assets/image (889).png>)

### Camera Setting Ranges

_**Camera Settings**_

* Valid frame rate values: Varies depending on camera models, refer to the respective hardware specifications.
* Valid exposure values: Depends on camera model and frame rate settings.
* Valid threshold values: 0 - 255
* Valid intensity values: 0 - 15

_**Video Types**_

* Video Type: see the [Data Recording](../../motive/data-recording/) page for more information on image processing modes.
* Segment Mode: 0
* Grayscale Mode: 1
* Object Mode: 2
* Precision Mode: 4
* MJPEG Mode: 6

### Other Settings

There are other camera settings, such as imager gain, that can be configured using the Motive API. Please refer to the [Motive API: Function Reference](motive-api-function-reference.md) page for descriptions on other functions.

## Updating the frames

In order to process multiple consecutive frames, you must update the camera frames using the following API functions: TT\_Update or TT\_UpdateSingleFrame. Call one of the two functions repeatedly within a loop to process all of the incoming frames. In the 'marker sample', TT\_Update function is called within a while loop as the frameCounter variable is incremented, as shown in the example below.

{% code overflow="wrap" %}
```
// marker.cpp sample project

int main()
{
        TT_Initialize();
	int frameCounter = 0; // Frame counter variable
 	while (!_kbhit())
	{
		if(TT_Update() == eMotiveAPIResult_SUCCESS)
		{
			// Each time the TT_Update function successfully updates the frame,
			// the frame counter is incremented, and the new frame is processed.
			frameCounter++;

			////// PROCESS NEW FRAME //////
		}
	}
}
```
{% endcode %}

### TT\_Update() vs. TT\_UpdateSingleFrame()

There are two functions for updating the camera frames: TT\_Update and TT\_UpdateSingleFrame. At the most fundamental level, these two functions both update the incoming camera frames. However, they may act differently in certain situations. When a client application stalls momentarily, it could get behind on updating the frames and the unprocessed frames may be accumulated. In this situation, each of these two functions will behave differently.

* The **TT\_Update()** function will disregard accumulated frames and service only the most recent frame data, but it also means that the client application will not be processing the previously missed frames.
* The **TT\_UpdateSingleFrame()** function ensures that only one frame is processed each time the function is called. However, when there are significant stalls in the program, using this function may result in accumulated processing latency.

In general, a user should always use TT\_Update(). Only in the case where a user wants to ensure their client application has access to every frame of tracking data and they are having problems calling TT\_Update() in a timely fashion, should they consider using TT\_UpdateSingleFrame(). If it is important for your program to obtain and process every single frame, use the TT\_UpdateSingleFrame() function for updating the data.

```
TT_Update() 		// Process all outstanding frames of data.
```

```
TT_UpdateSingleFrame() // Process one outstanding frame of data.
```

### 3D Marker Tracking

After loading valid [camera calibration](../../motive/calibration/), you can use the API functions to track retroreflective markers and get their 3D coordinates. The following section demonstrates using the API functions for obtaining the 3D coordinates. Since marker data is obtained for each frame, always call the [TT\_Update](motive-api-function-reference.md#tt_update), or the [TT\_UpdateSingleFrame](motive-api-quick-start-guide.md#tt_update-vs.-tt_updatesingleframe), function each time newly captured frames are received.

**Marker Index**

In a given frame, each reconstructed marker is assigned a marker index number. Marker indexes are used for pointing to a particular reconstruction within a frame. You can also use the [TT\_MarkerCount](motive-api-function-reference.md#tt_framemarkercount) function to obtain the total marker count and use this value within a loop to process all of the reconstructed markers. Marker index values may vary between different frames, but unique identifiers will always remain the same. Use the [TT\_MarkerLabel](motive-api-function-reference.md#tt_framemarkerlabel) function to obtain the individual marker labels if you wish to access same reconstructions for multiple frames.

```
int totalMarker = TT_MarkerCount();
printf("Frame #%d: (Markers: %d)\n", framecounter, totalMarker);

//== Use a loop to access every marker in the frame ==//
for (int i = 0 ; i < totalMarker; i++) {
        printf("\tMarker #%d:\t(%.2f,\t%.2f,\t%.2f)\n\n", 
		i, TT_MarkerXYZ(i));
}
```

**Marker Position**

For obtaining 3D position of a reconstructed marker, use the TT\_MarkerXYZ function.

This function returns 3D coordinates (X/Y/Z) of a marker in respect to the global coordinate system, which was defined during the calibration process. You can further analyze 3D movements directly from the reconstructed 3D marker positions, or you can create a Rigid Body asset from a set of tracked reconstructions for 6 Degrees of Freedom tracking data. Rigid body tracking via the API will be explained in the later section.

```
int totalMarker = TT_MarkerCount();
printf("Frame #%d: (Markers: %d)\n", framecounter, totalMarker);

//== Use a loop to access every marker in the frame ==//
for (int i = 0 ; i < totalMarker; i++) {
        printf("\tMarker #%d:\t(%.2f,\t%.2f,\t%.2f)\n\n", 
		i, TT_FrameMarkerXYZ(i));
}
```

![Sample 3D marker coordinate output using the API functions.](<../../.gitbook/assets/image (838).png>)

## Rigid Body Tracking

![Retroreflective markers placed on a quadrocopter.](<../../.gitbook/assets/image (872).png>) ![The corresponding Rigid Body defined in Motive.](<../../.gitbook/assets/image (847).png>)

For tracking 6 degrees of freedom (DoF) movement of a Rigid Body, a corresponding Rigid Body (RB) asset must be defined. A RB asset is created from a set of reflective markers attached to a rigid object which is assumed to be undeformable. There are two main approaches for obtaining RB assets when using Motive API; you can either import existing Rigid Body data or you can define new Rigid Bodies using the [TT\_CreateRigidBody](motive-api-function-reference.md#tt_createrigidbody) function. Once RB assets are defined in the project, Rigid Body tracking functions can be used to obtain the 6 DoF tracking data. This section covers sample instructions for tracking Rigid Bodies using the Motive API.

{% hint style="info" %}
We strongly recommend reading through the [**Rigid Body Tracking**](../../motive/rigid-body-tracking/) page for more information on how Rigid Body assets are defined in Motive.
{% endhint %}

### Importing Rigid Body Assets

Let's go through importing RB assets into a client application using the API. In Motive, Rigid Body assets can be created from three or more reconstructed markers, and all of the created assets can be exported out into either application profile (MOTIVE) Each Rigid Body asset saves marker arrangements when it was first created. As long as the marker locations remain the same, you can use saved asset definitions for tracking respective objects.

**Exporting all RB assets from Motive:**

* Exporting application profile: _File → Save Profile_

**Exporting individual RB asset:**

* Exporting Rigid Body file (profile): Under the [Assets pane](https://docs.optitrack.com/v3.1/motive-ui-panes/assets-pane), right-click on a RB asset and click _Export Rigid Body_

When using the API, you can load exported assets by calling the [TT\_LoadProfile](motive-api-function-reference.md#tt_loadprofile-tt_loadprofilew) function for application profiles and the [TT\_LoadRigidBodies](motive-api-function-reference.md#tt_loadrigidbodies-tt_loadrigidbodiesw) or [TT\_AddRigidBodes](motive-api-function-reference.md#tt_addrigidbodies-tt_addrigidbodiesw) function. When importing profiles, the TT\_LoadRigidBodies function will entirely replace the existing Rigid Bodies with the list of assets from the loaded TRA file. On the other hand, TT\_AddRigidBodes will add the loaded assets onto the existing list while keeping the existing assets. Once Rigid Body assets are imported into the application, the API functions can be used to configure and access the Rigid Body assets.

```
TT_LoadProfile("UserProfile.motive"); 	// Loading application profile
```

{% code overflow="wrap" %}
```
TT_LoadRigidBodies("asset1.motive");    // Replaces RBs with RBs from "asset1.motive"  TT_AddRigidBodies("asset1.motive");     // Adds RBs from file to already existing RBs
TT_SaveRigidBodies("asset1.motive");    // Saves RBs from RB list to file
```
{% endcode %}

### Creating New Rigid Body Assets

Rigid body assets can also be defined directly using the API. The [TT\_CreateRigidBody](motive-api-function-reference.md#tt_createrigidbody) function defines a new Rigid Body from given 3D coordinates. This function takes in an array float values which represent x/y/z coordinates or multiple markers in respect to Rigid Body pivot point. The float array for multiple markers should be listed as following: {x1, y1, z1, x2, y2, z2, …, xN, yN, zN}. You can manually enter the coordinate values or use the TT\_MarkerXYZ function to input 3D coordinates of tracked markers.

When using the TT\_MarkerXYZ functions, you need to keep in mind that these locations are taken in respect to the RB pivot point. To set the pivot point at the center of created Rigid Body, you will need to first compute pivot point location, and subtract its coordinates from the 3D coordinates of the markers obtained by the TT\_FrameMarkerX/Y/Z functions. This process is shown in the following example.

{% code overflow="wrap" %}
```
TT_CreateRigidBody( const wchar_t* name, int id, int markerCount, float *markerList );
```
{% endcode %}

**Example: Creating RB Assets**

{% code overflow="wrap" %}
```
int markerCount = TT_MarkerCount;
vector<float> markerListRelativeToGlobal(3*markerCount);

// add markers to markerListRelativeToGlobal using TT_FrameMarkerX, etc
for (int i = 0; i < markerCount; ++i)
{
    	markerListRelativeToGlobal.push_back(TT_FrameMarkerX(i));
    	markerListRelativeToGlobal.push_back(TT_FrameMarkerY(i));
	markerListRelativeToGlobal.push_back(TT_FrameMarkerZ(i));
}

// then average the locations in x, y and z
for (int i = 0; i < markerCount; ++i)
{
    	float sx += markerListRelativeToGlobal[3*i];
    	float sy += markerListRelativeToGlobal[3*i + 1];
    	float sz += markerListRelativeToGlobal[3*i + 2];
}


float ax = sx/markerCount;
float ay = sy/markerCount;
float az = sz/markerCount;
vector<float> pivotPoint = {ax, ay, az};
vector<float> markerListRelativeToPivotPoint(3*markerCount);

// subtract the pivot point location from the marker location
for (int i = 0; i < markerCount; ++i)
{
    markerListRelativeToPivotPoint.push_back(markerListRelativeToGlobal[3*i] - ax);
    markerListRelativeToPivotPoint.push_back(markerListRelativeToGlobal[3*i + 1] - ay);
    markerListRelativeToPivotPoint.push_back(markerListRelativeToGlobal[3*i + 2] - az);
}

TT_CreateRigidBody("Rigid Body New", 1, markerCount, markerListRelativeToPivotPoint);
```
{% endcode %}

### Rigid Body 6 DoF Tracking Data

6 DoF Rigid Body tracking data can be obtained using the [TT\_RigidBodyLocation](motive-api-function-reference.md#tt_rigidbodylocation) function. Using this function, you can save 3D position and orientation of a Rigid Body into declared variables. The saved position values indicate location of the Rigid Body pivot point, and they are represented in respect to the global coordinate axis. The Orientation is saved in both Euler and Quaternion orientation representations.

{% code overflow="wrap" %}
```
bool TT_RigidBodyLocation( int rbIndex,
    float* x, float* y, float* z,                           // Position
    float* qx, float* qy, float* qz, float* qw,             // Quaternion orientation
    float* yaw, float* pitch, float* roll );                // Euler orientation
```
{% endcode %}

**Example: RB Tracking Data**

{% code overflow="wrap" %}
```
//== Declared variables ==//
float	x, y, z;
float 	qx, qy, qz, qw;
float	yaw, pitch, roll;
int rbcount = TT_RigidBodyCount();

for(int i = 0; i < rbcount; i++)
{
	//== Obtaining/Saving the Rigid Body position and orientation ==//
	TT_RigidBodyLocation( i, &x, &y, &z, &qx, & qy, &qz, &qw, &yaw, &pitch, &roll );
	
	if( TT_IsRigidBodyTracked( i ) )
	{
		printf( "%s: Pos (%.3f, %.3f, %.3f) Orient (%.1f, %.1f, %.1f)\n", 
					TT_RigidBodyName( i ), x, y, z, yaw, pitch, roll );
	}
}
```
{% endcode %}

### Rigid Body Properties

In Motive, Rigid Body assets have [Rigid Body properties](../../motive-ui-panes/properties-pane/properties-pane-rigid-body.md) assigned to each of them. Depending on how these properties are configured, display and tracking behavior of corresponding Rigid Bodies may vary. When using the API, Rigid Body properties are configured and applied using the cRigidBodySettings class which is declared within the **RigidBodySetting.h** header file.

Within your program, create an instance of cRigidBodySettings class and call the API functions to obtain and adjust Rigid Body properties. Once desired changes are made, use the [TT\_SetRigidBodySettings](motive-api-function-reference.md#tt_setrigidbodysettings) function to assign the properties back onto a Rigid Body asset.

For detailed information on individual Rigid Body settings, read through the [Properties: Rigid Body](../../motive-ui-panes/properties-pane/properties-pane-rigid-body.md) page.

{% code overflow="wrap" %}
```
NPRESULT	TT_RigidBodySettings(int rbIndex, RigidBodySolver::cRigidBodySettings &settings);
```
{% endcode %}

{% code overflow="wrap" %}
```
NPRESULT	TT_SetRigidBodySettings(int rbIndex, RigidBodySolver::cRigidBodySettings &settings);
```
{% endcode %}

## Data Streaming

Once the API has been successfully initialized, data streaming can be enabled, or disabled, by calling either the [TT\_StreamNP](motive-api-function-reference.md#tt_streamnp) or [TT\_StreamVRPN](motive-api-function-reference.md#tt_streamvrpn) function. The TT\_StreamNP function enables/disables data streaming via the NatNet. The [NatNet SDK](../natnet-sdk/) is a client/server networking SDK designed for sending and receiving NaturalPoint data across networks, and tracking data from the API can be streamed to client applications from various platforms via the NatNet protocol. Once the data streaming is enabled, connect the NatNet client application to the server IP address to start receiving the data.

```
TT_StreamNP(true);	//Enabling NatNet Streaming.
```

The TT\_StreamNP function is equivalent to Broadcast Frame Data from the [Data Streaming](../../motive/data-streaming.md) pane in Motive.

### Data Streaming Settings

The Motive API does not currently support configuring data streaming settings directly from the API. To configure the streaming server IP address and the data streaming settings, you will need to use Motive and save an application profile MOTIVE file that contains the desired configuration. Then, the exported profile can be loaded when using the API. Through this way, you will be able to set the interface IP address and decide which data to be streamed over the network.

For more information on data streaming settings, read through the [Data Streaming](../../motive/data-streaming.md) page.

![Output lines from the marker sample, indicating that it is starting a NatNet server.](<../../.gitbook/assets/image (849).png>)

![Streaming from the marker sample (API) onto the NatNet WinFormTestApp sample. Click image to enlarge.](<../../.gitbook/assets/image (891).png>)
