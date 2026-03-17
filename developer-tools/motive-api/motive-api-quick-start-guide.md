---
description: An overview of the Motive API.
---

# Motive API: Quick Start Guide

## Overview

{% hint style="danger" %}
**SDK/API Support Disclaimer**

We provide developer tools to enable OptiTrack customers across a broad set of applications to utilize their systems in the ways that best suit them. Our Motive API through the NatNet SDK and Camera SDK is designed to enable experienced software developers to integrate data transfer and/or system operation with their preferred systems and pipelines. Sample projects are provided alongside each tool, and we strongly recommend the users to reference or use the samples as reliable starting points. The following list specifies the range of support that will be provided for the SDK tools:

* Using the SDK tools requires background knowledge on software development; therefore, we do not provide support for basic project setup, compiling, and linking when using the SDK/API to create your own applications.
* Although we ensure the SDK tools and their libraries work as intended, we do not provide support for custom developed applications that have been programmed or modified by users using the SDK tools.
* Ticketed support will be provided for licensed Motive users using the Motive API and/or the NatNet SDK tools from the included libraries and sample source codes only.
* The Camera SDK is a free product, and therefore we do not provide free ticketed support for it.
* For other questions, please check out the [NaturalPoint forums](https://forums.naturalpoint.com/). Very often, similar development issues get reported and solved there.
{% endhint %}

This guide provides detailed instructions for commonly used functions of the Motive API for developing custom applications. For a full list of functions, refer to the [Motive API: Function Reference](motive-api-function-reference.md) page. For a sample use case of the API functions, please check out the provided [_marker_](motive-api-overview.md#files-list) project.&#x20;

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

Motive API libraries (.lib and .dll) are in the _lib_ folder within the Motive install directory, located by default at `C:\Program Files\OptiTrack\Motive\lib`. This folder contains library files for both 64-bit (MotiveAPI.dll and MotiveAPI.lib) platforms.&#x20;

When using the API library, all of the required DLL files must be located in the executable directory. If necessary, copy and paste the MotiveAPI.dll file into the folder with the executable file.

**Third-party Libraries**

* Additional third-party libraries are required for Motive API, and most of the DLL files for these libraries can be found in the Motive install directory `C:\Program Files\OptiTrack\Motive\`. Copy and paste all of the DLL files from the Motive installation directory into the directory of the Motive API project to use them. Highlighted items in the below image are all required DLL files.
* Lastly, copy the `C:\Program Files\OptiTrack\Motive\plugins\platforms` folder and its contents into the EXE folder since those libraries will also be used.

![Library files required to run a Motive API application.](<../../.gitbook/assets/image (1034).png>)

### Header Files

Function declarations and classes are contained in the header file MotiveAPI.h, located in the folder `C:\Program Files\OptiTrack\Motive\inc\`.&#x20;

Always include the directive syntax for adding the MotiveAPI.h header file for all programs that are developed against the Motive API.&#x20;

**Note:** You can define this directory by using the MOTIVEAPI`_INC`, `MOTIVEAPI_LIB` environment variables. Check the project properties (Visual Studio) of the provided [_marker_](motive-api-overview.md#files-list) project for a sample project configuration.

### Motive Files

Motive API, by default, loads the default calibration (MCAL) and Application profile (MOTIVE) files from the program data directory unless otherwise specified. Motive also loads these files at startup. They are located in the following folders:

* Default System Calibration: C:\ProgramData\OptiTrack\Motive\System Calibration.mcal
* Default Application Profile: C:\ProgramData\OptiTrack\MotiveProfile.motive

Both files can be exported and imported into Motive as needed for the project:

* The [application profile](../../motive/motive-basics.md#motive-user-profile-.motive) can be imported using the [LoadProfile ](motive-api-function-reference.md#loadprofile)function to obtain software settings and trackable asset definitions.&#x20;
* The Calibration file can be imported using the [LoadCalibration ](motive-api-function-reference.md#loadcalibration)function to ensure reliable 3D tracking data is obtained.&#x20;

## Initialization and Shutdown

When using the API, connected devices and the Motive API library need to be properly initialized at the beginning of a program and closed down at the end.&#x20;

### Initialization

To initialize all of the connected cameras, call the [Initialize ](motive-api-function-reference.md#initialize)function. This function initializes the API library and gets the cameras ready to capture data, so always call this function at the beginning of a program. If you attempt to use the API functions without initializing first, you will get an error.

```
Initialize(); // Initializing all connected cameras
```

{% hint style="info" %}
**Motive Profile Load**

[Initialize ](motive-api-function-reference.md#initialize)loads the default Motive profiles (MOTIVE) from the ProgramData directory during the initialization process. To load a Motive profile from a different directory, use the [LoadProfile](motive-api-function-reference.md#loadprofile) function.
{% endhint %}

### Update

The [Update ](motive-api-function-reference.md#update)function is primarily used for updating captured frames, but it can also be called to update a list of connected devices. Call this function after initialization to make sure all of the newly connected devices are properly initialized in the beginning.

```
Initialize(); // Initializing all connected cameras

Update();     // Update for newly arrive cameras
```

### Shutdown

When exiting out of a program, call the [Shutdown ](motive-api-function-reference.md#shutdown)function to completely release and close all  connected devices. Cameras may fail to shut down completely if this function is not called.

```
Shutdown(); // Closing down all of the connected cameras
```

## Setup the Project

### Motive Application Profile

The Motive application profile (MOTIVE) stores the following critical information:

* All the trackable assets involved in a capture;
* Software configurations including [application settings](../../motive-ui-panes/settings/) and [data streaming settings](../../motive/data-streaming.md).&#x20;

When using the API, we recommend first configuring settings and defining the trackable assets in Motive, then exporting the profile MOTIVE file, to load by calling the [LoadProfile ](motive-api-function-reference.md#loadprofile)function. This allows you to adjust the settings for your needs in advance without having to configure individual settings through the API.

{% code overflow="wrap" %}
```
LoadProfile("UserProfile.motive"); // Loading application profile, UserProfile.motive
```
{% endcode %}

### Camera Calibration

Cameras must be calibrated to track in 3D space. Because camera calibration is a complex process, it's easier to calibrate the camera system from Motive, export the camera calibration file (MCAL), then load the exported file into custom applications that are developed against the API.&#x20;

Once the calibration data is loaded, the 3D tracking functions can be used. For detailed instructions on camera calibration in Motive, please read through the [Calibration](../../motive/calibration/) page.

{% code overflow="wrap" %}
```
LoadCalibration("CameraCal.mcal"); // Loading MCAL file
```
{% endcode %}

**Loading Calibration**

* In Motive, calibrate the camera system using the Calibration pane. Follow the [Calibration](../../motive/calibration/) page for details.
* After the system has been calibrated, [export the calibration file (MCAL)](../../motive/calibration/.mcal-xml-calibration-files.md#export-for-opencv-use) from Motive.
* Using the API, Import the calibration to your custom application by calling the [LoadCalibration ](motive-api-function-reference.md#loadcalibration)function.
* When successfully loaded, you will be able to obtain 3D tracking data using the API functions.

{% embed url="https://www.youtube.com/watch?t=136s&v=aK1cpr6ShPE" %}
Camera calibration overview.
{% endembed %}

{% hint style="info" %}
* _**Calibration Files:**_ When using an exported calibration file, make sure it remains a valid calibration. The file will no longer be valid if any aspect of the system setup has been altered after the calibration, including any quality degradation that can over time due to environmental factors. For this reason, we recommend re-calibrating the system routinely to guarantee the best tracking quality.
* _**Tracking Bars:**_ camera calibration is not required for tracking 3D points.&#x20;
{% endhint %}

## Camera Settings

Connected cameras are accessible by index numbers, which are assigned in the order the cameras are initialized. Most API functions for controlling cameras require the camera's index value.&#x20;

When processing all of the cameras, use the [CameraCount ](motive-api-function-reference.md#cameracount)function to obtain the total camera count and process each camera within a loop. To point to a specific camera, use the [CameraID](motive-api-function-reference.md#cameraid) function to check and use the camera with its given index value.&#x20;

This section covers Motive API functions to check and configure camera frame rate, camera video type, camera exposure, pixel brightness threshold, and IR illumination intensity.

### Fetching Camera Settings

Camera settings are also located in the Devices pane of Motive. For more information on each of these camera settings, refer to the [Devices pane](../../motive-ui-panes/devices-pane.md) page.

{% code overflow="wrap" %}
```
CameraProperty( int cameraIndex, const std::wstring& propertyName );
```
{% endcode %}

### Configuring Settings

Use the SetCameraProperty function to configure properties outlined below.

{% code overflow="wrap" %}
```
SetCameraProperty( int cameraIndex, const std::wstring& propertyName, const sPropertyValue& value );
```
{% endcode %}

<details>

<summary>CameraNodeCameraEnabled</summary>

A Boolean value to indicate whether the camera is enabled (true) or disabled (false).&#x20;

Corresponds to the [Enabled ](../../motive-ui-panes/properties-pane/properties-pane-camera.md#enabled)setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).&#x20;

</details>

<details>

<summary>CameraNodeReconstructionEnabled</summary>

A Boolean value to indicate whether the selected camera will contribute to the real-time reconstruction of 3D data. Set the value to true to enable or false to disable.&#x20;

Corresponds to the [Reconstruction ](../../motive-ui-panes/properties-pane/properties-pane-camera.md#reconstruction)setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).&#x20;

</details>

<details>

<summary>CameraNodeImagerPixelSize</summary>

Length and width (in pixels) of the camera imager.&#x20;

Corresponds to the [Pixel Dimensions](../../motive-ui-panes/properties-pane/properties-pane-camera.md#pixel-dimensions-advanced) value in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

</details>

<details>

<summary>CameraNodeCameraVideoMode</summary>

An Integer value that sets the video mode for the selected camera.

| Video Mode  | Value |
| ----------- | ----- |
| Segment     | 0     |
| Grayscale   | 1     |
| Object      | 2     |
| Precision   | 4     |
| MJPEG       | 6     |
| Color Video | 9     |

</details>

<details>

<summary>CameraNodeCameraExposure</summary>

An integer value that sets the exposure for the selected camera.&#x20;

Corresponds to the [Exposure ](../../motive-ui-panes/properties-pane/properties-pane-camera.md#exposure)setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

</details>

<details>

<summary>CameraNodeCameraThreshold</summary>

An integer value that sets the minimum brightness threshold for pixel detection for the selected camera. Valid threshold range is 0 - 255.

Corresponds to the [Threshold ](../../motive-ui-panes/properties-pane/properties-pane-camera.md#threshold)setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

</details>

<details>

<summary>CameraNodeCameraLED</summary>

A Boolean value to indicate whether the camera's LED light are enabled (true) or disabled (false).&#x20;

Corresponds to the [LED ](../../motive-ui-panes/properties-pane/properties-pane-camera.md#led)setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

</details>

<details>

<summary>CameraNodeCameraIRFilterEnabled</summary>

A Boolean value to indicate whether the camera's IR filter is enabled (true) or disabled (false).&#x20;

Corresponds to the [IR Filter](../../motive-ui-panes/properties-pane/properties-pane-camera.md#ir-filter) setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

</details>

<details>

<summary>CameraNodeCameraGain</summary>

An integer value that sets the imager gain for the selected camera.&#x20;

Corresponds to the [Gain ](../../motive-ui-panes/properties-pane/properties-pane-camera.md#gain)setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

</details>

<details>

<summary>CameraNodeCameraFrameRate</summary>

An integer value that sets the frame rate for the selected camera.&#x20;

Applicable values vary based on camera models. Refer to the hardware specifications for the selected camera type to determine the frame rates at which it can record.

Corresponds to the [Frame Rate](../../motive-ui-panes/properties-pane/properties-pane-camera.md#rate) setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

</details>

<details>

<summary>CameraNodeCameraMJPEGQuality</summary>

An integer value that sets the video quality level of MJPEG mode for the selected camera.&#x20;

| MJPEG Quality    | Value |
| ---------------- | ----- |
| Minimum Quality  | 0     |
| Low Quality      | 1     |
| Standard Quality | 2     |
| High Quality     | 3     |

Corresponds to the MJPEG Quality setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

</details>

<details>

<summary>CameraNodeCameraMaximizePower</summary>

A Boolean value to indicate whether High Power mode is enabled (true) or disabled (false) for the Slim 3U and Flex 3 cameras only. &#x20;

Corresponds to the Maximize Power setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

</details>

<details>

<summary>CameraNodeBitrate</summary>

An integer value that sets the bitrate for the selected camera.&#x20;

Corresponds to the Bitrate setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

</details>

<details>

<summary>CameraNodePartition</summary>

An integer value that sets the bitrate for the selected camera.&#x20;

Corresponds to the Bitrate setting in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

</details>

<details>

<summary>CameraNodeFirmwareVersion</summary>

A string value that displays the Firmware version of the selected camera.&#x20;

Corresponds to the [Firmware Version](../../motive-ui-panes/properties-pane/properties-pane-camera.md#firmware-version-advanced) property in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

{% code overflow="wrap" %}
```
/// <item><description>CameraNodeFirmwareVersion (std::wstring)</description></item>
```
{% endcode %}

</details>

<details>

<summary>CameraNodeLogicVersion</summary>

A string value that displays the Logic version of the selected camera.&#x20;

Corresponds to the Logic Version property in Motive's [Camera Properties](../../motive-ui-panes/properties-pane/properties-pane-camera.md).

{% code overflow="wrap" %}
```
/// <item><description>CameraNodeLogicVersion (std::wstring)</description></item>
```
{% endcode %}

</details>

### Other Settings

There are other camera settings, such as imager gain, that can be configured using the Motive API. Please refer to the [Motive API: Function Reference](motive-api-function-reference.md) page for descriptions of other functions.

## Updating the frames

To process multiple consecutive frames, call the functions [Update](motive-api-function-reference.md#update) or [UpdateSingleFrame](motive-api-function-reference.md#updatesingleframe) repeatedly within a loop. In the example below, the Update function is called within a while loop as the frameCounter variable is incremented:

{% code overflow="wrap" %}
```
int main()
{
        Initialize();
	int frameCounter = 0; // Frame counter variable
 	while (!_kbhit())
	{
		if(Update() == eRESULT_SUCCESS)
		{
			// Each time the Update function successfully updates the frame,
			// the frame counter is incremented, and the new frame is processed.
			frameCounter++;

			////// PROCESS NEW FRAME //////
		}
	}
}
```
{% endcode %}

#### Update vs. UpdateSingleFrame

At the most fundamental level, these two functions both update the incoming camera frames, but  may act differently in certain situations. When a client application stalls momentarily, it can get behind on updating the frames and the unprocessed frames may accumulate. In this situation, these two functions behave differently.

* The [**Update**](motive-api-function-reference.md#update) function disregards accumulated frames and services only the most recent frame data. The client application will not receive the previously missed frames to process.
* The [**UpdateSingleFrame**](motive-api-function-reference.md#updatesingleframe) function ensures only one frame is processed each time the function is called. If there are significant stalls in the program, using this function may result in accumulated processing latency.

In general, we recommend using the Update function. Only use UpdateSingleFrame in the case when you need to ensure the client application has access to every frame of tracking data and you are not able to call Update in a timely fashion.&#x20;

```
Update()            // Process all outstanding frames of data.
UpdateSingleFrame() // Process one outstanding frame of data.
```

### 3D Marker Tracking

After loading a valid [camera calibration](../../motive/calibration/), you can use API functions to track retroreflective markers and get their 3D coordinates. Since marker data is obtained for each frame, always call the [Update](motive-api-function-reference.md#update) or the [UpdateSingleFrame ](motive-api-function-reference.md#updatesingleframe)function each time newly captured frames are received.

You can use the [MarkerCount ](motive-api-function-reference.md#markercount)function to obtain the total marker count and use this value within a loop to process all of the reconstructed markers.&#x20;

**Marker Index**

In a given frame, each reconstructed marker is assigned a marker index number, which is used to point to a particular reconstruction within a frame. Marker index values may vary between different frames, but unique identifiers always remain the same.&#x20;

**Marker Position**

For obtaining 3D position of a reconstructed marker, use the MarkerXYZ function

<pre><code>int totalMarker = MarkerCount();
printf("Frame #%d: (Markers: %d)\n", framecounter, totalMarker);

int x = 0;
int y = 0;
int z = 0;

//== Use a loop to access every marker in the frame ==//
for (int i = 0 ; i &#x3C; totalMarker; i++) {
<strong>        MarkerXYZ(i,x,y,z);
</strong>        printf("\tMarker #%d:\t(%.2f,\t%.2f,\t%.2f)\n\n", 
		i, x, y, z);
}
</code></pre>

## Rigid Body Tracking

This section covers functions for tracking Rigid Bodies using the Motive API.

![Retroreflective markers placed on a quadrocopter.](<../../.gitbook/assets/Quadrocopter Live and MoCap.png>)

To track the 6 degrees of freedom (DoF) movement of an undeformable object, attach a set of reflective markers to it and use the markers to create a trackable Rigid Body asset.&#x20;

{% hint style="info" %}
Please read the [Rigid Body Tracking](../../motive/rigid-body-tracking/) page for detailed instructions on creating and working with Rigid Body assets in Motive.
{% endhint %}

There are two methods for obtaining Rigid Body assets when using the Motive API:&#x20;

* Import existing Rigid Body data.&#x20;
* Define new Rigid Bodies using the [CreateRigidBody](motive-api-function-reference.md#createrigidbody) function.&#x20;

Once Rigid Body assets are defined, Rigid Body tracking functions can be used to obtain the 6 DoF tracking data.&#x20;

### Importing Rigid Body Assets

Let's go through importing RB assets into a client application using the API. In Motive, Rigid Body assets can be created from three or more reconstructed markers, and all of the created assets can be exported out into either application profile (MOTIVE) Each Rigid Body asset saves marker arrangements when it was first created. As long as the marker locations remain the same, you can use saved asset definitions for tracking respective objects.

**Exporting all RB assets from Motive:**

* Exporting application profile: _File → Save Profile_

**Exporting individual RB asset:**

* Exporting Rigid Body file (profile): Under the [Assets pane](../../motive-ui-panes/assets-pane.md), right-click on a RB asset and click _Export Rigid Body_

When using the API, you can load exported assets by calling the [LoadProfile](motive-api-function-reference.md#tt_loadprofile-tt_loadprofilew) function for application profiles and the [LoadRigidBodies](motive-api-function-reference.md#tt_loadrigidbodies-tt_loadrigidbodiesw) or [AddRigidBodes](motive-api-function-reference.md#tt_addrigidbodies-tt_addrigidbodiesw) function. When importing profiles, the LoadRigidBodies function will entirely replace the existing Rigid Bodies with the list of assets from the loaded profile. On the other hand, AddRigidBodes will add the loaded assets onto the existing list while keeping the existing assets. Once Rigid Body assets are imported into the application, the API functions can be used to configure and access the Rigid Body assets.

{% code overflow="wrap" %}
```
LoadProfile("UserProfile.motive"); 	// Loading application profile
```
{% endcode %}

{% code overflow="wrap" %}
```
LoadRigidBodies("asset1.motive"); 	// Replaces RBs with RBs from "asset1.motive"  AddRigidBodies("asset1.motive");        // Adds RBs from file to already existing RBs
SaveRigidBodies("asset1.motive");       // Saves RBs from RB list to file
```
{% endcode %}

### Creating New Rigid Body Assets

Rigid body assets can be defined directly using the API. The CreateRigidBody function defines a new Rigid Body from given 3D coordinates. This function takes in an array float values which represent x/y/z coordinates or multiple markers in respect to Rigid Body pivot point. The float array for multiple markers should be listed as following: {x1, y1, z1, x2, y2, z2, …, xN, yN, zN}. You can manually enter the coordinate values or use the MarkerXYZ function to input 3D coordinates of tracked markers.

When using the MarkerXYZ function, you need to keep in mind that these locations are taken in respect to the RB pivot point. To set the pivot point at the center of created Rigid Body, you will need to first compute pivot point location, and subtract its coordinates from the 3D coordinates of the markers obtained by the MarkerXYZ function. This process is shown in the following example.

{% code overflow="wrap" %}
```
CreateRigidBody(const wchar_t* name, int id, int markerCount, float* markerList);
```
{% endcode %}

**Example: Creating RB Assets**

{% code overflow="wrap" %}
```
int markerCount = MarkerCount;
vector<float> markerListRelativeToGlobal(3*markerCount);

// add markers to markerListRelativeToGlobal using MarkerXYZ, etc
int x = 0;
int y = 0;
int z = 0;

for (int i = 0; i < markerCount; ++i)
{
        MarkerXYZ(i, x, y, z);
    	markerListRelativeToGlobal.push_back(x);
    	markerListRelativeToGlobal.push_back(y);
	markerListRelativeToGlobal.push_back(z);
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

CreateRigidBody("Rigid Body New", 1, markerCount, markerListRelativeToPivotPoint);
```
{% endcode %}

### Rigid Body 6 DoF Tracking Data

6 DoF Rigid Body tracking data can be obtained using the RigidBodyTransform function. Using this function, you can save 3D position and orientation of a Rigid Body into declared variables. The saved position values indicate location of the Rigid Body pivot point, and they are represented in respect to the global coordinate axis. The Orientation is saved in both Euler and Quaternion orientation representations.

{% code overflow="wrap" %}
```
RigidBodyTransform(int rbIndex, 				//== RigidBody Index
			float *x, float *y, float *z, 			//== Position
			float *qx, float *qy, float *qz, float *qw, 	//== Quaternion
			float *yaw, float *pitch, float *roll);   	//== Euler
```
{% endcode %}

**Example: RB Tracking Data**

{% code overflow="wrap" %}
```
//== Declared variables ==//
float	x, y, z;
float 	qx, qy, qz, qw;
float	yaw, pitch, roll;
int rbcount = RigidBodyCount();

for(int i = 0; i < rbcount; i++)
{
	//== Obtaining/Saving the Rigid Body position and orientation ==//
	RigidBodyTransform( i, &x, &y, &z, &qx, & qy, &qz, &qw, &yaw, &pitch, &roll );
	
	if( IsRigidBodyTracked( i ) )
	{
		wchar_t name[ 256 ];
		RigidBodyName( i, name, 256 );
		wprintf( L"\n%s: Pos (%.3f, %.3f, %.3f) Orient (%.1f, %.1f, %.1f)\n", name, x, y, z, yaw, pitch, roll );
	}
}
```
{% endcode %}

### Rigid Body Properties

In Motive, Rigid Body assets have [Rigid Body properties](../../motive-ui-panes/properties-pane/properties-pane-rigid-body.md) assigned to each of them. Depending on how these properties are configured, display and tracking behavior of corresponding Rigid Bodies may vary.

For detailed information on individual Rigid Body settings, read through the [Properties: Rigid Body](../../motive-ui-panes/properties-pane/properties-pane-rigid-body.md) page.

{% code overflow="wrap" %}
```
RigidBodyProperty(int rbIndex, const std::wstring& propertyName);
```
{% endcode %}

{% code overflow="wrap" %}
```
SetRigidBodyProperty(int rbIndex, const std::wstring& propertyName, const sPropertyValue& value);
```
{% endcode %}

```
    /// <list type="bullet">
    ///<item><description> NodeName                 (String) </description></item>
    ///<item><description> AssetName                (String) </description></item>
    ///<item><description> GeometryYawPitchRoll     (eVector3f) </description></item>
    ///<item><description> BoneMajorAxis            (Int) </description></item>
    ///<item><description> DefaultBoneLength        (double) </description></item>
    ///<item><description> DefaultBoneDiameter      (double) </description></item>
    ///<item><description> JointName                (String) </description></item>
    ///<item><description> ParentInfo               (String) </description></item>
    ///<item><description> ChildInfo                (String) </description></item>
    ///<item><description> JointVisible             (Bool) </description></item>
    ///<item><description> JointType                (String) </description></item>
    ///<item><description> DegreesOfFreedom         (Int) </description></item>
    ///<item><description> RotationOrder            (Int) </description></item>
    ///<item><description> RotationOffset           (eRotationf) </description></item>
    ///<item><description> TranslationOffset        (eVector3f) </description></item>
    ///<item><description> TipOffset                (eVector3f) </description></item>
    ///<item><description> AssetVisible             (Bool) </description></item>
    ///<item><description> Comment                  (String) </description></item>
    ///<item><description> MinimumBootingLabels     (Int) </description></item>
    ///<item><description> MinimumMarkerCount       (Int) </description></item>
    ///<item><description> MinimumBootingActive     (Int) </description></item>
    ///<item><description> Scale                    (double) </description></item>
    ///<item><description> SyntheticLabelGraphScale (double) </description></item>
    ///<item><description> ShowLabel                (Bool) </description></item>
    ///<item><description> ShowIMUState             (Int) </description></item>
    ///<item><description> DisplayTracked           (Bool) </description></item>
    ///<item><description> Color                    (Int) </description></item>
    ///<item><description> ShowBones                (Bool) </description></item>
    ///<item><description> BoneColor                (Int) </description></item>
    ///<item><description> ShowAxis                 (Bool) </description></item>
    ///<item><description> DisplayPositionHistory   (Bool) </description></item>
    ///<item><description> DisplayHistoryLength     (Int) </description></item>
    ///<item><description> ShowDOF                  (Bool) </description></item>
    ///<item><description> ShowMarkerSet            (Bool) </description></item>
    ///<item><description> ShowTargetMarkerLines    (Bool) </description></item>
    ///<item><description> ShowMarkerLines          (Bool) </description></item>
    ///<item><description> Smoothing                (double) </description></item>
    ///<item><description> PredictionTime           (double) </description></item>
    ///<item><description> PositionDamping          (eVector3f) </description></item>
    ///<item><description> RotationDamping          (double) </description></item>
    ///<item><description> RotationDampingAxis      (Int) </description></item>
    ///<item><description> ModelAlpha               (double) </description></item>
    ///<item><description> GeometryType             (Int) </description></item>
    ///<item><description> GeometryFile             (String) </description></item>
    ///<item><description> GeometryScale            (eVector3f) </description></item>
    ///<item><description> GeometryOffset           (eVector3f) </description></item>
    ///<item><description> GeometryPitchYawRoll     (eVector3f) </description></item>
    ///<item><description> Name                     (String) </description></item>
    ///<item><description> UserData                 (Int) </description></item>
    ///<item><description> ActiveTagID              (Int) </description></item>
    ///<item><description> ActiveTagRfChannel       (Int) </description></item>
    ///<item><description> TrackingAlgorithmLevel   (Int) </description></item>
    ///<item><description> ShareMarkers             (Bool) </description></item>
    ///<item><description> MarkerID                 (Int) </description></item>
    ///<item><description> MarkerLocation           (eVector3f) </description></item>
```

## Data Streaming

Once the API is successfully initialized, there are two methods of data streaming available.&#x20;

#### Stream over NatNet

The  [StreamNP](motive-api-function-reference.md#streamnp) function enables/disables data streaming via the [NatNet SDK](../natnet-sdk/). This client/server networking SDK is designed for sending and receiving OptiTrack data across networks, and can be used to stream tracking data from the API to client applications from various platforms.&#x20;

Once the data streaming is enabled, connect the NatNet client application to the server IP address to start receiving the data.

```
StreamNP(true);	// Enabling NatNet Streaming.
```

The StreamNP function is equivalent to Broadcast Frame Data from the [Data Streaming](../../motive/data-streaming.md) pane in Motive.

#### Stream over VRPN

Mocap data can be livestreamed through the Virtual Reality Peripheral Network (VRPN) using the [StreamVRPN ](motive-api-function-reference.md#streamvrpn)function.&#x20;

```
StreamVRPN(true); // Enabling VRPN Streaming.
```

Please see the [VRPN Sample](../vrpn-sample.md) page for information on working with the OptiTrack VRPN sample.&#x20;

### Data Streaming Settings

The Motive API does not support data streaming configuration directly from the API. These properties must be set in Motive.&#x20;

* In Motive, configure the streaming server IP address and other data streaming settings. See the [Data Streaming](../../motive/data-streaming.md) page for more information.&#x20;
* Export the Motive profile (MOTIVE file) that contains the desired configuration.&#x20;
* Load the exported profile through the API.&#x20;
