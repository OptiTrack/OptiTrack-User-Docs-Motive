---
description: A guide to the functions available in the Motive API.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/developer-tools/motive-api/motive-api-function-reference
---

# Motive API: Function Reference

_Please use the table of contents to the right to navigate to categories of functions. Links to the specific functions in each category are contained in the section header._&#x20;

_Alternately, use Ctrl + F to search the page contents._&#x20;

{% hint style="danger" %}
**Important Note:**

Some functions are not yet included in the documentation. Please refer to the Motive API header file (MotiveAPI.h) for information on any functions that are not documented here.
{% endhint %}

***

## Licensing

<details>

<summary>LoadLicenseFromMemory</summary>

Loads a License file that was previously loaded into a memory block.

Licenses are automatically loaded from the OptiTrack license directory. This method is not needed except to accommodate use-cases where the license&#x20;file is located outside the license folder.&#x20;

{% hint style="warning" %}
When needed, call this function before the Initialize() function.
{% endhint %}

{% code overflow="wrap" %}
```cpp
eResult     LoadLicenseFromMemory( const unsigned char* buffer, int bufferSize );
```
{% endcode %}

**Description**

* This function loads a license file from the specified location in memory.  In order to do this, the program must have a saved license in memory.
* Assumes the pointer argument (unsigned char\*) points to a memory block where the license file is already stored. The address and size of the calibration buffer must be determined by the developer using the API.
* Returns an eRESULT value. When the function successfully loads the license, it returns 0 (or eRESULT\_SUCCESS).

**Function Input**

* Buffer (unsigned char\*)
* Size of the buffer (int)

**Function Output**

* eRESULT

</details>

## Startup / Shutdown

In this section:

[Initialize ](motive-api-function-reference.md#initialize)| [IsInitialized](motive-api-function-reference.md#isinitialized) | [Shutdown ](motive-api-function-reference.md#shutdown)| [CanConnectToDevices](motive-api-function-reference.md#canconnecttodevices) | [BuildNumber](motive-api-function-reference.md#buildnumber)

<details>

<summary>Initialize</summary>

Initializes the API and prepares all connected devices for capturing. `Initialize` also loads the default profile `C:\ProgramData\OptiTrack\MotiveProfile.motive`. When there is a need to load the profile from a separate directory, use the `LoadProfile` function.

{% code overflow="wrap" %}
```cpp
eRESULT		Initialize();
```
{% endcode %}

**Description**

* This function initializes the API library and prepares all connected devices for capturing.
* When using the API, this function needs to be called at the beginning of a program before using the cameras.
* Returns an eRESULT value. When the function successfully updates the data, it returns 0 (or eRESULT\_SUCCESS).

**Function Input**

* None

**Function Output**

* eResult

**C++ Example**

{% code overflow="wrap" %}
```cpp
// Initializing all connected cameras
Initialize();
```
{% endcode %}

</details>

<details>

<summary>IsInitialized</summary>

Determines if the API has been initialized.&#x20;

{% code overflow="wrap" %}
```cpp
bool		IsInitialized();
```
{% endcode %}

**Description**

* This function determines if the [Initialize](motive-api-function-reference.md#initialize) function has been called and the [Shutdown ](motive-api-function-reference.md#shutdown)function has not been called.&#x20;
* This function returns True if the [Initialize](motive-api-function-reference.md#initialize) function has been called and the [Shutdown ](motive-api-function-reference.md#shutdown)function has not been called.&#x20;

**Function Input**

* None

**Function Output**

* eRESULT

</details>

<details>

<summary>Shutdown</summary>

Shuts down all of the connected devices.

**Description**

* This function closes down all connected devices and the camera library. To ensure that all devices properly shutdown, call this function before terminating an application.
* When the function successfully closes down the devices, it returns 0 (or kApiResult\_Success).
* When calling this function, the currently configured camera calibration will be saved under the default System Calibration .mcal file.

**Function Input**

* None

**Function Output**

* eRESULT

**C++ Example**

{% code overflow="wrap" %}
```cpp
// Close down all of the connected cameras
Shutdown();
return 0;
```
{% endcode %}

</details>

<details>

<summary>CanConnectToDevices</summary>

Determines if this instance of the API can connect to OptiTrack devices.

{% code overflow="wrap" %}
```cpp
bool		CanConnectToDevices();
```
{% endcode %}

**Description**

* This function returns true if there are no other instances of Motive running on the host PC, consuming device connections.&#x20;

**Function Input**

* None

**Function Output**

* Boolean

</details>

<details>

<summary>BuildNumber</summary>

Retrieves the specific build number of the API. This is correlated with the software /// release version, but the software release version is not encoded in this value.

**Description**

* This function returns the corresponding Motive build number.

**Function Input**

* None

**Function Output**

* Build number (int)

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== Printing Motive Build Number ==//

printf("Motive Build: %d\n", BuildNumber());
```
{% endcode %}

</details>

## User Profile Interface

In this section:

[LoadProfile ](motive-api-function-reference.md#loadprofile)| [SaveProfile ](motive-api-function-reference.md#saveprofile)

<details>

<summary>LoadProfile</summary>

Loads a Motive User Profile (.MOTIVE).

{% code overflow="wrap" %}
```cpp
eRESULT		LoadProfile(const wchar_t* filename);
```
{% endcode %}

**Description**

* Loads the default application profile file (MOTIVE), which is located in the ProgramData directory: `C:\ProgramData\OptiTrack\MotiveProfile.motive`
* The MOTIVE file stores software configurations as well as other application-wide settings.
* Returns an eRESULT integer value. If the project file was successfully loaded, it returns 0 (kApiResult\_Success).

**Function Input**

Filename (const wchar\_t)

**Function Output**

eRESULT

</details>

<details>

<summary>SaveProfile</summary>

Saves the current application settings into a Profile XML file.

{% code overflow="wrap" %}
```cpp
eRESULT		SaveProfile(const wchar_t* filename);
```
{% endcode %}

**Description**

* This function saves the current configuration into an application Profile XML file.
* Attaches the \*.xml extension at the end of the filename.
* Returns an eRESULT integer value. If the profile XML file was saved successfully, it returns 0 (kApiResult\_Success).

**Function Input**

Filename (const wchar\_t)

**Function Output**

eRESULT

</details>

## Frame Processing

In this section:

[Update ](motive-api-function-reference.md#update)| [UpdateSingleFrame ](motive-api-function-reference.md#updatesingleframe)| [FlushCameraQueues](motive-api-function-reference.md#flushcameraqueues)

<details>

<summary>Update</summary>

Processes incoming frame data from the cameras.

**Description**

* This function updates frame information with the most recent data from the cameras and 3D processing engines.
* Another use of this function is to pick up newly connected cameras. Call this function at the beginning of a program in order to make sure that all of the new cameras are properly recognized.

{% hint style="info" %}
**Update vs. UpdateSingleFrame**:&#x20;

In general, the `Update()` function is sufficient to capture frames lost when a client application stalls momentarily. This function disregards accumulated frames and serves only the most recent frame data, which means the client application will miss the previous frames.&#x20;

For situations where it is critical to ensure every frame is captured and the Update() cannot be called in a timely fashion, use the`UpdateSingleFrame()`function ensures that the next consecutive frame is updated each time the function is called.&#x20;
{% endhint %}

* Returns an eRESULT integer value, depending on whether the operation was successful or not. Returns kApiResult\_Successwhen it successfully updates the frame data.

**Function Input**

* None

**Function Output**

* eRESULT

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== Update to pick up recently-arrived cameras ==/
Update();

//== Frame Processing: Polling the frame data ==//
while( programRunning ){
	if( Update() == kApiResult_Success){
		frameNumber++;
		//== Process Frame Data ==//
	}
} 
```
{% endcode %}

</details>

<details>

<summary>UpdateSingleFrame</summary>

Updates a single frame of camera data.

{% code overflow="wrap" %}
```cpp
eRESULT		UpdateSingleFrame();
```
{% endcode %}

**Description**

* Every time this function is called, it updates frame information with the next frame of camera data.
* Using this function ensures that every frame of data is processed.

{% hint style="info" %}
**Update vs. UpdateSingleFrame**:&#x20;

In general, the `Update()` function is sufficient to capture frames lost when a client application stalls momentarily. This function disregards accumulated frames and serves only the most recent frame data, which means the client application will miss the previous frames.&#x20;

For situations where it is critical to ensure every frame is captured and the Update() cannot be called in a timely fashion, use the`UpdateSingleFrame()`function ensures that the next consecutive frame is updated each time the function is called.&#x20;
{% endhint %}

* Returns an eRESULT value. When the function successfully updates the data, it returns 0 (or kApiResult\_Success).

**Function Input**

* None

**Function Output**

* eRESULT

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== Update to pick up recently-arrived cameras ==/
Update();

//== Frame Processing: Polling the frame data ==//
while( programRunning ){
	if( UpdateSingleFrame() == kApiResult_Success){
		frameNumber++;
		//== Process Frame Data ==//
	}
}
```
{% endcode %}

</details>

<details>

<summary>FlushCameraQueues</summary>

Flushes out the camera queues.

{% code overflow="wrap" %}
```cpp
void		FlushCameraQueues();
```
{% endcode %}

**Description**

* This function flushes all queued camera frames.
* In an event when you are tracking a very high number (hundreds) of markers and the application has accumulated data processing latency, you can call `FlushCameraQueues()` to refresh the camera queue before calling `Update()` for processing the frame. After calling this function, avoid calling it again until the `Update()` function is called and kApiResult\_Success is returned.

**Function Input**

* None

**Function Output**

* Void

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== Flush Camera Queues to remove accumulated latency. ==//
FlushCameraQueues();

//== Update the incoming camera data after. ==//
Update();
```
{% endcode %}

</details>

## Camera Calibration Interface

In this section:

[LoadCalibration](motive-api-function-reference.md#loadcalibration) | [LoadCalibrationFromMemory](motive-api-function-reference.md#loadcalibrationfrommemory) | [SaveCalibration](motive-api-function-reference.md#savecalibration) | [CameraExtrinsicsCalibrationFromMemory](motive-api-function-reference.md#cameraextrinsicscalibrationfrommemory) | [StartCalibrationWanding](motive-api-function-reference.md#startcalibrationwanding) | [CalibrationState](motive-api-function-reference.md#calibrationstate) | [CalibrationCamerasLackingSamples](motive-api-function-reference.md#calibrationcameraslackingsamples) | [CameraCalibrationSamples](motive-api-function-reference.md#cameracalibrationsamples) | [CancelCalibration](motive-api-function-reference.md#cancelcalibration) | [StartCalibrationCalculation](motive-api-function-reference.md#startcalibrationcalculation) |[CurrentCalibrationQuality](motive-api-function-reference.md#currentcalibrationquality) |  [ApplyCalibrationCalculation](motive-api-function-reference.md#applycalibrationcalculation) | [SetGroundPlane](motive-api-function-reference.md#setgroundplane) | [TranslateGroundPlane](motive-api-function-reference.md#translategroundplane)  | [AutoDetectCalibrationSquare](motive-api-function-reference.md#autodetectcalibrationsquare) | [GetGroundPlaneMarkers](motive-api-function-reference.md#getgroundplanemarkers)&#x20;

<details>

<summary>LoadCalibration</summary>

Loads a Motive camera calibration file.

{% code overflow="wrap" %}
```cpp
eRESULT		LoadCalibration(const wchar_t* filename, int* cameraCount = nullptr);
```
{% endcode %}

**Description**

* Loads a camera calibration file (.MCAL).
* Camera calibration files need to be exported from Motive.
* Returns an eRESULT integer value. If the file was successfully loaded, it returns kApiResult\_Success.

**Function Input**

* Filename (const wchar\_t)

**Function Output**

* eRESULT

**C++ Example**

<pre class="language-cpp" data-overflow="wrap"><code class="lang-cpp">const wchar_t* calibrationFile = L"C:\\ProgramData\\OptiTrack\\Motive\\System Calibration.mcal";
int calibrationCameraCount = 0; 
<strong>
</strong><strong>eRESULT fileload = LoadCalibration( calibrationFile, &#x26;calibrationCameraCount );
</strong>if (fileload == kApiResult_Success)
{
	printf("%ls successfully loaded.\n", calFileName);
}
else
{
	printf("Error: %ls\n", MapToResultString(fileload));
}
</code></pre>

</details>

<details>

<summary>LoadCalibrationFromMemory</summary>



</details>

<details>

<summary>SaveCalibration</summary>

Saves the current calibration to a file.

{% code overflow="wrap" %}
```cpp
eResult SaveCalibration( const wchar_t* filename );
```
{% endcode %}

**Description**

* Saves the current calibration using the specified file name.

**Function Input**

* File name (const wchar\_t\*)

**Function Output**

* Returns an eRESULT integer value. If the file was successfully saved, it returns kApiResult\_Success.

</details>

<details>

<summary>CameraExtrinsicsCalibrationFromMemory</summary>

Gets camera extrinsics from a calibration file in memory.&#x20;

{% code overflow="wrap" %}
```cpp
std::vector<sCameraInfo> CameraExtrinsicsCalibrationFromMemory( unsigned char* buffer, int bufferSize,
        eResult& result );
```
{% endcode %}

**Description**

* This allows for acquiring camera extrinsics for cameras not connected to system.
* It returns the list of details for all cameras contained in the calibration file.

**Function Input**

* Buffer (unsigned char\*)
* Size of the buffer (int)
* Result

**Function Output**

* eRESULT

</details>

<details>

<summary>StartCalibrationWanding</summary>

Start a new calibration wanding for all cameras.

{% code overflow="wrap" %}
```cpp
void		StartCalibrationWanding();
```
{% endcode %}

**Description**

* This will cancel any existing calibration process.

**Function Input**

* None

**Function Output**

* Changes the CalibrationState to Wanding.&#x20;

</details>

<details>

<summary>CalibrationCamerasLackingSamples</summary>

During calibration wanding, this will return a vector of camera indices that are lacking the minimum number of calibration samples to begin calculation.

{% code overflow="wrap" %}
```cpp
std::vector<int>		CalibrationCamerasLackingSamples();
```
{% endcode %}

**Description**

* When the returned vector for this method goes to zero, call `StartCalibrationCalculation()` to begin calibration calculations.
* Wanding samples will be collected until `StartCalibrationCalculation()` is called.

**Function Input**

* None

**Function Output**

* Vector (int)

**C++ Example**

{% code overflow="wrap" %}
```cpp
// If calibrating, print out some state information.
eCalibrationState state = CalibrationState();
if( state == eCalibrationState::Wanding )
{
	std::vector<int> neededCameras( CalibrationCamerasLackingSamples() );
	if( !neededCameras.empty() )
	{
		printf( "\nNeed more samples for %d cameras:", (int) neededCameras.size() );
		for( int cameraIndex:neededCameras )
		{
			int cameraSamples = CameraCalibrationSamples( cameraIndex );
			printf( "\n%d (%d)", CameraID( cameraIndex ), cameraSamples );
		}
		printf( "\n" );
	}
}
// If completed calibration wanding, print the quality
else if( state >= eCalibrationState::PreparingSolver && state <= eCalibrationState::Complete )
{
	PrintCalibrationQuality();
}
```
{% endcode %}

</details>

<details>

<summary>CameraCalibrationSamples</summary>

Returns the number of wand samples collected for the given camera during calibration wanding.

{% code overflow="wrap" %}
```cpp
int		CameraCalibrationSamples(int cameraIndex);
```
{% endcode %}

**Description**

* This will return the number of wand samples collected for the given camera.
* Returns 0 otherwise.

**Function Input**

* Camera index (int)

**Function Output**

* Number of samples (int)

**C++ Example**

{% code overflow="wrap" %}
```cpp
// If calibrating, print out some state information.
eCalibrationState state = CalibrationState();
if( state == eCalibrationState::Wanding )
{
	std::vector<int> neededCameras( CalibrationCamerasLackingSamples() );
	if( !neededCameras.empty() )
	{
		printf( "\nNeed more samples for %d cameras:", (int) neededCameras.size() );
		for( int cameraIndex:neededCameras )
		{
			int cameraSamples = CameraCalibrationSamples( cameraIndex );
			printf( "\n%d (%d)", CameraID( cameraIndex ), cameraSamples );
		}
		printf( "\n" );
	}
}
// If completed calibration wanding, print the quality
else if( state >= eCalibrationState::PreparingSolver && state <= eCalibrationState::Complete )
{
	PrintCalibrationQuality();
}
```
{% endcode %}

</details>

<details>

<summary>CancelCalibration</summary>

Cancels wanding or calculation and resets the calibration engine.

{% code overflow="wrap" %}
```cpp
void		CancelCalibration();
```
{% endcode %}

**Description**

* Cancels wanding or calculation
* Resets calibration engine

**Function Input**

* none

**Function Output**

* Exits either `StartCalibrationWanding()` or `StartCalibrationCalculation()`

</details>

<details>

<summary>StartCalibrationCalculation</summary>

Once wanding is complete, call this function to begin the calibration calculations.

{% code overflow="wrap" %}
```cpp
bool		StartCalibrationCalculation();
```
{% endcode %}

**Description**

* Starts calibration calculations after wanding.

**Function Input**

* Boolean value

**Function Output**

* Starts calculation

**C++ Example**

{% code overflow="wrap" %}
```cpp
// Start calculation and it will return false if it fails (likely due to not wanding first)
if( !StartCalibrationCalculation() )
{
	printf( "ERROR - Please wand the volume first by calling StartCalibrationWanding()\n" );
}
```
{% endcode %}

</details>

<details>

<summary>CurrentCalibrationQuality</summary>

Retrieves the current calibration quality.

{% code overflow="wrap" %}
```cpp
int		CurrentCalibrationQuality();
```
{% endcode %}

**Description**

* This method will return the current calibration quality in the range \[0-3], with 3 being best.
* Returns zero otherwise

**Function Input**

* none

**Function Output**

* Quality on scale of 0-3 (int)

**C++ Example**

{% code overflow="wrap" %}
```cpp
int quality = CurrentCalibrationQuality();

printf( "Current calibration quality: " );
switch( quality )
{
case 0:
	printf( "Fair\n" );
	break;
case 1:
	printf( "Good\n" );
	break;
case 2:
	printf( "Great\n" );
	break;
case 3:
	printf( "Excellent\n" );
	break;
}
```
{% endcode %}

</details>

<details>

<summary>ApplyCalibrationCalculation</summary>

Call this function once `CalibrationState()` returns "Complete" to apply the calibration results to all cameras.

{% code overflow="wrap" %}
```cpp
bool		ApplyCalibrationCalculation();
```
{% endcode %}

**Description**

* Call this method to apply the calibration results to all cameras.

**Function Input**

* none

**Function Output**

* Apply calibration results

**C++ Example**

{% code overflow="wrap" %}
```cpp
// Apply calibration to all cameras and if it fails, it will return false (likely due to not wanding)
if( !ApplyCalibrationCalculation() )
{
	printf( "ERROR - Please wand the volume first by calling StartCalibrationWanding()\n" );
}
```
{% endcode %}

</details>

<details>

<summary>SetGroundPlane</summary>

Set the ground plane using a standard or custom ground plane template.

{% code overflow="wrap" %}
```cpp
eRESULT		SetGroundPlane(bool useCustomGroundPlane);
```
{% endcode %}

**Description**

* Applies a standard or custom ground plane to the calibration.

**Function Input**

* Boolean value of useCustomGroundPlane

**Function Output**

* Either applies custom or preset ground plane to calibration.

</details>

<details>

<summary>TranslateGroundPlane</summary>

Translate the existing ground plane (in mm).

{% code overflow="wrap" %}
```cpp
void		TranslateGroundPlane(float x, float y, float z);
```
{% endcode %}

**Description**

* Takes float variables to alter existing ground plane.

**Function Input**

* X, Y, and Z values (float)

**Function Output**

* Applies new values to existing ground plane.

</details>

<details>

<summary>AutoDetectCalibrationSquare</summary>

Returns the Calibration Square in the volume if one is detected.

{% code overflow="wrap" %}
```cpp
eCalibrationSquareType AutoDetectCalibrationSquare();
```
{% endcode %}

**Description**

* Detects pre-defined Calibration Squares in the volume and returns a corresponding value. See [Calibration Squares](../../motive/calibration/calibration-squares.md) for more information on the different types available.&#x20;

**Function Input**

* None.

**Function Output**

* Returns eCalibrationSquareType: kNone, kCS400, kClassicLFrame, kCS200, or kCS100.&#x20;

</details>

<details>

<summary>GetGroundPlaneMarkers</summary>

Returns the marker count and list of markers found on the ground plane.

{% code overflow="wrap" %}
```cpp
eResult GetGroundPlaneMarkers( std::vector<Core::cMarker>& markers );
```
{% endcode %}

**Description**

* Returns the marker count and list of markers found on the ground plane.

**Function Input**

* Vector of references to marker structures to load with ground plane markers.

**Function Output**

* Returns an eRESULT integer value. If the marker data was retrieved, it returns kApiResult\_Success with the data. Otherwise, an error code is returned.&#x20;

</details>

## Data Streaming

In this section:

[StreamNP ](motive-api-function-reference.md#streamnp)| [StreamVRPN](motive-api-function-reference.md#streamvrpn)

<details>

<summary>StreamNP</summary>

Enables or disables the NatNet streaming of the OptiTrack data.

{% code overflow="wrap" %}
```cpp
eRESULT		StreamNP(bool enable);
```
{% endcode %}

**Description**

* This function enables/disables the OptiTrack data stream.
* This is equivalent to the Broadcast Frame Data in the Data Streaming panel in Motive.
* If the operation was successful, it returns 0 (kApiResult\_Success), or an error code otherwise.

**Function Input**

* Boolean argument enabled (true) / disabled (false)

**Function Output**

* eRESULT

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== Enable NP Streaming ==/
StreamNP(true);
```
{% endcode %}

</details>

<details>

<summary>StreamVRPN</summary>

Enables or disables data stream into [VRPN](https://github.com/vrpn/vrpn/wiki).

{% code overflow="wrap" %}
```cpp
eRESULT		StreamVRPN(bool enable, int port);
```
{% endcode %}

**Description**

* This function enables or disables data streaming into VRPN.
* To stream onto VRPN, the port address must be specified. VRPN server applications run through 3883 port, which is the default port for the VRPN streaming.
* Returns an eRESULT integer value. If streaming was successfully enabled, or disabled, it returns 0 (kApiResult\_Success).

**Function Input**

* True to enable and false to disable (bool)
* Streaming port address (int)

**Function Output**

* eRESULT

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== Enable Streaming into VRPN ==/
StreamVRPN(true);
```
{% endcode %}

</details>

## Frame Info

In this section:

[FrameID](motive-api-function-reference.md#frameid) | [FrameTimeStamp](motive-api-function-reference.md#frametimestamp) | [FrameTimeCode](motive-api-function-reference.md#frametimecode)

<details>

<summary>FrameID</summary>

Returns the Frame ID of the current current frame.

{% code overflow="wrap" %}
```cpp
int FrameID();
```
{% endcode %}

**Description**

Retrieves the Frame ID of the current frame.&#x20;

**Function Input**

None.

**Function Output**

Returns an Integer for the current Frame ID.&#x20;

</details>

<details>

<summary>FrameTimeStamp</summary>

Returns a timestamp value for the current frame.

{% code overflow="wrap" %}
```cpp
double		FrameTimeStamp();
```
{% endcode %}

**Description**

* This function returns a timestamp value of the current frame.

**Function Input**

* None

**Function Output**

* Frame timestamp (double)

**C++ Example**

{% code overflow="wrap" %}
```cpp
int frameNumber = 0;

//== Display Frame number and Time stamp ==//
while( !_kbhit() )
{
	if( !Update() ){
		frameNumber++;	// increment frame number each time a frame is processed.

		printf("Frame #%d: (Timestamp: %f)\n", frameNumber, FrameTimeStamp());
	}
}
```
{% endcode %}

</details>

<details>

<summary>FrameTimeCode</summary>

Retrieves the timecode information for the current frame in a human-readable format.&#x20;

{% code overflow="wrap" %}
```cpp
bool FrameTimeCode( sTimecode& tc );
```
{% endcode %}

**Description**

* This function returns a timecode value for the current frame.&#x20;

**Function Input**

* None

**Function Output**

* Returns true if timecode is available and the timecode structure was filled. Returns isDropFrame if no data is available.&#x20;

</details>

## Marker Interface

In this section:

[MarkerCount](motive-api-function-reference.md#markercount) | [MarkerAverageSize](motive-api-function-reference.md#markeraveragesize) | [Marker](motive-api-function-reference.md#marker) | [MarkerXYZ](motive-api-function-reference.md#markerxyz) | [MarkerID](motive-api-function-reference.md#markerid) | [MarkerResidual](motive-api-function-reference.md#markerresidual) | [MarkerContributingRaysCount](motive-api-function-reference.md#markercontributingrayscount) | [MarkerAverageRayLength](motive-api-function-reference.md#markeraverageraylength) | [MarkerCameraCentroid](motive-api-function-reference.md#markercameracentroid)&#x20;

<details>

<summary>MarkerCount</summary>

Retrieves the total number of reconstructed markers in the current frame.

{% code overflow="wrap" %}
```cpp
int		MarkerCount();
```
{% endcode %}

**Description**

* This function returns a total number of reconstructed 3D markers detected in the current capture frame.
* Use this function to count a total number of markers, access every markers, and obtain the marker index values.

**Function Input**

* None

**Function Output**

* Total number of reconstructed markers in the frame (int)

**C++ Example**

{% code overflow="wrap" %}
```cpp
//Obtaining total marker count
int totalMarker = MarkerCount();
printf("Total number of markers: %d", totalMarker);
```
{% endcode %}

</details>

<details>

<summary>MarkerAverageSize</summary>

Returns the average marker diameter, in meters.

{% code overflow="wrap" %}
```cpp
float MarkerAverageSize();
```
{% endcode %}

**Description**

* This function calculates and returns the average marker diameter, in meters.

**Function Input**

* None.

**Function Output**

* The average marker diameter, in meters.

</details>

<details>

<summary>Marker</summary>

Retrieves a specific marker in the current frame.

{% code overflow="wrap" %}
```cpp
bool Marker( int markerIndex, Core::cMarker& marker );
```
{% endcode %}

**Description**

* This function determines if a specific marker is located in the current frame.&#x20;

**Function Input**

* Index of the marker to retrieve.
* Reference to the marker to load with marker info.

**Function Output**

* Returns true if the referenced marker index is available in the frame, otherwise returns false.

</details>

<details>

<summary>MarkerXYZ</summary>

Retrieves the 3D reconstructed position of a specific marker in the current frame.

{% code overflow="wrap" %}
```cpp
bool MarkerXYZ( int markerIndex, float& x, float& y, float& z );
```
{% endcode %}

**Description**

* This function determines if a specific marker is located in the current frame at the specified coordinates.

**Function Input**

* Index of the marker to retrieve.
* Reference to x/y/z coordinate to load with marker coordinate info.

**Function Output**

* Returns true if the referenced marker index is valid, otherwise returns false.

</details>

<details>

<summary>MarkerID</summary>

Returns the unique identifier of a specific marker in the current frame.

{% code overflow="wrap" %}
```cpp
Core::cUID		MarkerID(int markerIndex);
```
{% endcode %}

**Description**

* This function returns a unique identifier (cUID) for a given marker.
* Markers have an index from 0 to \[totalMarkers -1] for a given frame. In order to access unique identifier of any marker, it's index must be inputted.
* The marker index value may change between frames, but the unique identifier will always remain the same.

**Function Input**

* Index of the marker to retrieve.

**Function Output**

* Marker label (cUID)

**C++ Example**

{% code overflow="wrap" %}
```cpp
int totalMarkers = MarkerID();
vector<Core::cUID> unique_Marker_ID(totalMarkers);

for (int i = 0; i < totalMarkers; ++i)
{
    unique_Marker_ID[i] = MarkerID(int markerIndex); 
}
```
{% endcode %}

</details>

<details>

<summary>MarkerResidual</summary>

Returns the residual value of a specific marker in the current frame.

{% code overflow="wrap" %}
```cpp
float		MarkerResidual(int markerIndex);
```
{% endcode %}

**Description**

* This function returns the residual value for a given marker indicated by the marker index.
* The returned value is in millimeters.
* The marker index value may change between frames, but the unique identifier will always remain the same.

**Function Input**

* Index of the marker to retrieve.

**Function Output**

* Residual value (float).

</details>

<details>

<summary>MarkerContributingRaysCount</summary>

Retrieves the number of rays that contributed to the reconstruction of a specific marker in the current frame.

{% code overflow="wrap" %}
```cpp
int MarkerContributingRaysCount( int markerIndex );
```
{% endcode %}

**Description**

Returns the number of rays that contributed to the reconstruction of a specific marker in the current frame.

**Function Input**

* Index of the marker to retrieve.

**Function Output**

* Returns an integer value.&#x20;

</details>

<details>

<summary>MarkerAverageRayLength</summary>

Retrieves the average ray length for all rays contributing to a specific marker in the current frame.

{% code overflow="wrap" %}
```cpp
float MarkerAverageRayLength( int markerIndex );
```
{% endcode %}

**Description**

Returns the average length of the rays that contributed to the reconstruction of a specific marker in the current frame.

**Function Input**

* Index of the marker to retrieve.

**Function Output**

* Returns the average value (float).&#x20;

</details>

<details>

<summary>MarkerCameraCentroid</summary>

Checks whether a camera is contributing to reconstruction of a 3D marker, and saves the corresponding 2D location as detected in the camera's view.

{% code overflow="wrap" %}
```cpp
bool		MarkerCameraCentroid(int markerIndex, int cameraIndex, float &x, float &y);
```
{% endcode %}

**Description**

* This function evaluates whether the specified camera (cameraIndex) is contributing to point cloud reconstruction of a 3D point (markerIndex).
* It returns true if the camera is contributing to the marker.
* After confirming that the camera contributes to the reconstruction, this function will save the 2D location of the corresponding marker centroid in respect to the camera's view.
* The 2D location is saved in the declared variable.

**Function Input**

* 3D reconstructed marker index (int)
* Camera index (int)
* Reference variables for saving x and y (floats).

**Function Output**

* True / False (bool)

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== Getting 2D location of marker centroids from a camera.==//
float x, y;
int targetcam = 1;
int frameMarkercount = MarkerCount();

for (int i = 0; i < frameMarkercount; i++) // For each detected markers
{
	bool result = MarkerCameraCentroid(i, targetcam, x, y)

	if (result)
	{
		printf("Marker %d location in camera #%d: %f, %f\n", i, targetcam, x, y);
	}
}
```
{% endcode %}

</details>

## Rigid Body Interface

In this section:

[RigidBodyCount](motive-api-function-reference.md#rigidbodycount) | [CreateRigidBody](motive-api-function-reference.md#createrigidbody) | [RigidBodyPropertyNames](motive-api-function-reference.md#rigidbodypropertynames) | [RigidBodyProperty](motive-api-function-reference.md#rigidbodyproperty) | [RigidBodyPropertyType](motive-api-function-reference.md#rigidbodypropertytype) | [SetRigidBodyProperty](motive-api-function-reference.md#setrigidbodyproperty) | [ClearRigidBodies](motive-api-function-reference.md#clearrigidbodies) | [LoadRigidBodies](motive-api-function-reference.md#loadrigidbodies) | [AddRigidBodies](motive-api-function-reference.md#addrigidbodies) | [SaveRigidBodies](motive-api-function-reference.md#saverigidbodies)  | [RigidBodyID](motive-api-function-reference.md#rigidbodyid) | [RigidBodyName](motive-api-function-reference.md#rigidbodyname) | [IsRigidBodyTracked](motive-api-function-reference.md#isrigidbodytracked) | [RigidBodyTransform](motive-api-function-reference.md#rigidbodytransform) | [RemoveRigidBody](motive-api-function-reference.md#removerigidbody) | [SetRigidBodyEnabled](motive-api-function-reference.md#setrigidbodyenabled) | [RigidBodyEnabled](motive-api-function-reference.md#rigidbodyenabled) | [RigidBodyTranslatePivot](motive-api-function-reference.md#rigidbodytranslatepivot) | [RigidBodyResetOrientation](motive-api-function-reference.md#rigidbodyresetorientation) | [RigidBodyMarkerCount](motive-api-function-reference.md#rigidbodymarkercount) | [RigidBodyMarker](motive-api-function-reference.md#rigidbodymarker) | [RigidBodyUpdateMarker](motive-api-function-reference.md#rigidbodyupdatemarker) | [RigidBodyReconstructedMarker](motive-api-function-reference.md#rigidbodyreconstructedmarker) | [RigidBodyMeanError](motive-api-function-reference.md#rigidbodymeanerror) |

<details>

<summary>RigidBodyCount</summary>

Returns the total number of Rigid Bodies.

{% code overflow="wrap" %}
```cpp
int		RigidBodyCount();
```
{% endcode %}

**Description**

* This function returns a total count of Rigid Bodies defined in the project, including all tracked and untracked assets.
* This function can be used within a loop to set required number of iterations and access each of the Rigid Bodies.

**Function Input**

* None

**Function Output**

* Total Rigid Body count (int)

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== Getting names of all Rigid Bodies ==//
int rigidBodyCount = RigidBodyCount();

for( int i = 0; i < rigidBodyCount; i++ )
{
	wchar_t name[ 256 ];
	RigidBodyName( i, name, 256 );
	printf( L"\t%ls\n", name );
}
```
{% endcode %}

</details>

<details>

<summary>CreateRigidBody</summary>

Creates a Rigid Body asset from a set of reconstructed 3D markers.

{% code overflow="wrap" %}
```cpp
eRESULT		CreateRigidBody(const wchar_t* name, int id, int markerCount, float* markerList);
```
{% endcode %}

**Description**

* This functions creates a Rigid Body from the marker list and marker count provided in its argument.
* The marker list is expected to contain a list of marker coordinates in the following order: (x1, y1, z1, x2, y2, z2, …, xN, yN, zN). The x/y/z coordinates must be in respect to the Rigid Body pivot point, in meters.
* Inputted 3D locations are taken as Rigid Body marker positions about the Rigid Body pivot point. If you are using MarkerX/Y/Z functions to obtain the marker coordinates, you will need to subtract the pivot point location from the global marker locations when creating a Rigid Body. This is shown in the below example. If this is not done, the created Rigid Body will have its pivot point at the global origin.
* Returns an eRESULT integer value. If the Rigid Body was successfully created, it returns 0 or kApiResult\_Success.

**Function Input**

* Rigid body name (wchar\_t)
* User Data ID (int)
* Marker Count (int)
* Marker list (float list)

**Function Output**

* eRESULT

</details>

<details>

<summary>RigidBodyPropertyNames</summary>

Returns a list of property names for all properties associated with a given rigid body.

{% code overflow="wrap" %}
```cpp
bool RigidBodyPropertyNames(int rbIndex, std::vector<std::wstring>& propertyNames);
```
{% endcode %}

**Description**

* This function retrieves a list of property names.&#x20;
* Returns true if the list was successfully created.

**Function Input**

* Rigid body index (int)

**Function Output**

* Bool
* List of rigid body properties.

</details>

<details>

<summary>RigidBodyProperty</summary>

Returns the value for the specified rigid body property.&#x20;

{% code overflow="wrap" %}
```cpp
sPropertyValue RigidBodyProperty(int rbIndex, const std::wstring& propertyName);
```
{% endcode %}

**Description**

* This function retrieves the value of a rigid body property.&#x20;
* Returns eInvalid if the property is not found.

**Function Input**

* Rigid body index (int)
* Name of the property to retrieve (std::wstring)

**Function Output**

| Property Name            | Output Type |
| ------------------------ | ----------- |
| NodeName                 | String      |
| AssetName                | String      |
| GeometryYawPitchRoll     | eVector3f   |
| BoneMajorAxis            | Int         |
| DefaultBoneLength        | Double      |
| DefaultBoneDiameter      | Double      |
| JointName                | String      |
| ParentInfo               | String      |
| ChildInfo                | String      |
| JointVisible             | Bool        |
| JointType                | String      |
| DegreesOfFreedom         | Int         |
| RotationOrder            | Int         |
| RotationOffset           | eRotationf  |
| TranslationOffset        | eVector3f   |
| TipOffset                | eVector3f   |
| AssetVisible             | Bool        |
| Comment                  | String      |
| MinimumBootingLabels     | Int         |
| MinimumMarkerCount       | Int         |
| MinimumBootingActive     | Int         |
| Scale                    | Double      |
| SyntheticLabelGraphScale | Double      |
| ShowLabel                | Bool        |
| ShowIMUState             | Int         |
| DisplayTracked           | Bool        |
| Color                    | Int         |
| ShowBones                | Bool        |
| BoneColor                | Int         |
| ShowAxis                 | Bool        |
| DisplayPositionHistory   | Bool        |
| DisplayHistoryLength     | Int         |
| ShowDOF                  | Bool        |
| ShowMarkerSet            | Bool        |
| ShowTargetMarkerLines    | Bool        |
| ShowMarkerLines          | Bool        |
| Smoothing                | Double      |
| PredictionTime           | Double      |
| PositionDamping          | eVector3f   |
| RotationDamping          | Double      |
| RotationDampingAxis      | Int         |
| ModelAlpha               | Double      |
| GeometryType             | Int         |
| GeometryFile             | String      |
| GeometryScale            | eVector3f   |
| GeometryPitchYawRoll     | eVector3f   |
| Name                     | String      |
| UserData                 | Int         |
| ActiveTagID              | Int         |
| ActiveTagRfChannel       | Int         |
| TrackingAlgorithmLevel   | Int         |
| ShareMarkers             | Bool        |
| MarkerID                 | Int         |
| MarkerLocation           | eVector3f   |

</details>

<details>

<summary>RigidBodyPropertyType</summary>

Returns the property type for a rigid body property.&#x20;

{% code overflow="wrap" %}
```cpp
ePropertyDataType RigidBodyPropertyType(int rbIndex, const std::wstring& propertyName);
```
{% endcode %}

**Description**

* This function retrieves the type of property (int, string, etc.) for a rigid body property.&#x20;
* Returns eInvalid if an invalid rigid body property name is entered.

**Function Input**

* Rigid body index (int)
* Name of the property (std::wstring)&#x20;

**Function Output**

* Data type of the rigid body property.

</details>

<details>

<summary>SetRigidBodyProperty</summary>

Changes property settings of a Rigid Body.

{% code overflow="wrap" %}
```cpp
bool		SetRigidBodyProperty(int rbIndex, const std::wstring& propertyName, const sPropertyValue& value);
```
{% endcode %}

**Description**

* This function sets the value of a rigidbody property.
* True if the property was found and the value was set

**Function Input**

* Rigid body index (int)
* Name of the property to set (std::wstring)
* Value to set the property to (sPropertyValue)

**Function Output**

* bool

</details>

<details>

<summary>ClearRigidBodies</summary>

Clears and removes all Rigid Body assets.

{% code overflow="wrap" %}
```cpp
void		ClearRigidBodies();
```
{% endcode %}

**Description**

* This function clears all of existing Rigid Body assets in the project.

**Function Input**

* None

**Function Output**

* Void

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== Clear all Rigid Bodies ==//
ClearRigidBodies();
```
{% endcode %}

</details>

<details>

<summary>LoadRigidBodies</summary>

Imports .motive files and loads Rigid Body assets from it.

{% code overflow="wrap" %}
```cpp
eRESULT		LoadRigidBodies(const wchar_t* filename);
```
{% endcode %}

**Description**

* This function imports and loads Rigid Body assets from a saved .motive file.
* .motive file contain exported Rigid Body asset definitions from Motive.
* All existing assets in the project will be replaced with the Rigid Body assets from the .motive file when this function is called. If you want to keep existing assets and only wish to add new Rigid Bodies, use the `AddRigidBodies` function.
* Returns an eRESULT integer value. It returns kApiResult\_Success when the file is successfully loaded.

**Function Input**

Filename (const wchat\_t)

**Function Output**

eRESULT

</details>

<details>

<summary>AddRigidBodies</summary>

Loads a .motive file and adds its Rigid Body assets onto the project.

{% code overflow="wrap" %}
```cpp
eRESULT		AddRigidBodies(const wchar_t* filename);
```
{% endcode %}

**Description**

* This function adds Rigid Body assets from the imported .motive file to the asset list of the current project. Existing assets are not deleted.
* Returns an eRESULT integer value. If the Rigid Bodies have been added successfully, it returns 0 or kApiResult\_Success.

**Function Input**

Filename (const wchar\_t)

**Function Output**

eRESULT

</details>

<details>

<summary>SaveRigidBodies</summary>

Saves all of the Rigid Body asset definitions into a .motive file.

{% code overflow="wrap" %}
```cpp
eRESULT		SaveRigidBodies(const wchar_t* filename);
```
{% endcode %}

**Description**

* This function saves all of the Rigid Body assets from the project into a .motive file.
* Returns an eRESULT integer value. It returns 0 or kApiResult\_Success when successfully saving the file.

**Function Input**

Filename (const wchar\_t)

**Function Output**

eRESULT

</details>

<details>

<summary>RigidBodyID</summary>

Returns the unique ID of a Rigid Body at the given index.

{% code overflow="wrap" %}
```cpp
Core::cUID		RigidBodyID(int rbIndex);
```
{% endcode %}

**Description**

* This function returns the unique ID number of a Rigid Body.
* This is different from User ID, which is a user definable ID for the Rigid Body. When working with capture data in external pipelines, this value can be used to address specific Rigid Bodies in the scene.

**Function Input**

* Rigid body index (int)

**Function Output**

* Unique ID number for Rigid Body

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== unique ID for all Rigid Bodies ==//
for ( int i = 0 ; i < RigidBodyCount(); i++ )
{
	Core::cUID rbID = RigidBodyID();
	std::wstring ID = 
		std::to_wstring(rbID.HighBits()) + L", " +
		std::to_wstring(rbID.LowBits());
 	printf("ID for RigidBody %d : %ls", i, ID);
}
```
{% endcode %}

</details>

<details>

<summary>RigidBodyName</summary>

Returns the name for the Rigid Body at the given index.

{% code overflow="wrap" %}
```cpp
const wchar_t*		RigidBodyName(int rbIndex, wchar_t* buffer, int bufferSize);
```
{% endcode %}

**Description**

* These functions are used to obtain the name of a Rigid Body.
* Returns the assigned name of the Rigid Body.

**Function Input**

* Rigid body index (int)

**Function Output**

* Rigid body name (wconst char\_t\*)

**C++ Example**

{% code overflow="wrap" %}
```cpp
int totalRB = RigidBodyCount();

//== Printing Rigid Body Names ==//
for( int i = 0; i < totalRB; i++ )
{
	printf("Rigid Body: %ls", RigidBodyName(i)); 
}
```
{% endcode %}

</details>

<details>

<summary>IsRigidBodyTracked</summary>

Checks whether Rigid Body is tracked or not.

{% code overflow="wrap" %}
```cpp
bool		IsRigidBodyTracked(int rbIndex);
```
{% endcode %}

**Description**

* Checks whether the Rigid Body is being tracked in the current frame.
* Returns true if the Rigid Body is tracked.

**Function Input**

* Rigid body index (int)

**Function Output**

* True / False (bool)

**C++ Example**

{% code overflow="wrap" %}
```cpp
int totalRB = RigidBodyCount();

//== Checking if the Rigid Body is tracked or not ==//
for(int i = 0; i < totalRB)
{
	If(IsRigidBodyTracked(i))
	{
		// Process Rigid Body
	}
}
```
{% endcode %}

</details>

<details>

<summary>RigidBodyTransform</summary>

Returns the world-space transform of the requested rigid body in the current frame.

{% code overflow="wrap" %}
```cpp
bool RigidBodyTransform( int rbIndex,
        float* x, float* y, float* z,
        float* qx, float* qy, float* qz, float* qw,
        float* yaw, float* pitch, float* roll );
```
{% endcode %}

**Description**

* This function returns the transform in the current world-space for a single Rigid Body.
* Returns True if the operation was successful, along with the transform coordinates, otherwise returns False.

**Function Input**

* Rigid body index (int)

**Function Output**

* Bool
* Transform position (xyz)
* Transform rotation/orientation (both quaternions and Euler angles)

</details>

<details>

<summary>RemoveRigidBody</summary>

Removes a Rigid Body at the given index.

{% code overflow="wrap" %}
```cpp
eRESULT		RemoveRigidBody(int rbIndex);
```
{% endcode %}

**Description**

* This function removes a single Rigid Body from a project.
* Returns an eRESULT integer value. If the operation was successful, it returns 0 (kApiResult\_Success).

**Function Input**

* Rigid body index (int)

**Function Output**

* eRESULT

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== Removing Rigid Bodies that are not tracked in the scene ==//
int totalRB = RigidBodyCount();

for (int i = 0; i < totalRB; i++)
{
	if(!IsRigidBodyTracked(i))
	{
 		RemoveRigidBody(i);
	}
}
```
{% endcode %}

</details>

<details>

<summary>SetRigidBodyEnabled</summary>

Enables or disables tracking of a Rigid Body.

{% code overflow="wrap" %}
```cpp
void		SetRigidBodyEnabled(int rbIndex, bool enabled);
```
{% endcode %}

**Description**

* This function enables or disables tracking of the selected Rigid Body.
* All Rigid Bodies are enabled by default. Disabled Rigid Bodies will not be tracked, and no data will be received from it.

**Function Input**

* Rigid body index (int)
* Tracking status (bool)

**Function Output**

* Void

**C++ Example**

{% code overflow="wrap" %}
```cpp
int totalRB = RigidBodyCount();

//== Disabling all Rigid Bodies ==//
for(int i = 0; i < totalRB; i++)
{
	SetRigidBodyEnabled(i, FALSE);
} 
```
{% endcode %}

</details>

<details>

<summary>RigidBodyEnabled</summary>

Checks whether a Rigid Body is enabled.

{% code overflow="wrap" %}
```cpp
bool		RigidBodyEnabled(int rbIndex);
```
{% endcode %}

**Description**

* This function checks whether tracking of the Rigid Body is enabled or not.
* The function returns true is the tracking is enabled.

**Function Input**

* Rigid body index (int)

**Function Output**

* True / False (bool)

**C++ Example**

{% code overflow="wrap" %}
```cpp
int totalRB = RigidBodyCount();

for (int i = 0; i < totalRB; i++)
{
	if (RigidBodyEnabled(i))
	{
 		//== Disabling all enabled Rigid Bodies ==//
		SetRigidBodyEnabled(i, FALSE);
	}
}
```
{% endcode %}

</details>

<details>

<summary>RigidBodyTranslatePivot</summary>

Translates the pivot point of a Rigid Body.

{% code overflow="wrap" %}
```cpp
eRESULT		RigidBodyTranslatePivot(int rbIndex, float x, float y, float z);
```
{% endcode %}

**Description**

* This function translates a Rigid Body.
* 3D position of a Rigid Body will be displaced in x/y/z directions by inputted amount (meters).
* Translation is applied in respect to the local Rigid Body coordinate axis, not the global axis.
* Returns an eRESULT integer value. If the operation is successful, returns 0 (kApiResult\_Success).

**Function Input**

* Rigid body index (int)
* Translation along x-axis, in meters. (float)
* Translation along y-axis, in meters. (float)
* Translation along z-axis, in meters. (float)

**Function Output**

* eRESULT

**C++ Example**

{% code overflow="wrap" %}
```cpp
int rbIndex = 1;

//== Translating a Rigid Body 2 cm in positive x-direction ==//
RigidBodyTranslatePivot(rbIndex, 0.02, 0, 0);
```
{% endcode %}

</details>

<details>

<summary>RigidBodyResetOrientation</summary>

Resets the orientation of a Rigid Body.

{% code overflow="wrap" %}
```cpp
bool		RigidBodyResetOrientation(int rbIndex);
```
{% endcode %}

**Description**

* This function resets the orientation of the Rigid Body and re-aligns its orientation axis with the global coordinate system.
* _Note:_ When creating a Rigid Body, its zero orientation is set by aligning its axis with the global axis at the moment of creation. Calling this function essentially does the same thing on an existing Rigid Body asset.
* Returns true if the Rigid Body orientation was reset.

**Function Input**

* Rigid body index (int)

**Function Input**

* True / False (bool)

**C++ Example**

{% code overflow="wrap" %}
```cpp
int rbcount = RigidBodyCount();

//== Resetting orientation of each Rigid Body. ==//
for( int i = 0; i < rbcount i++ )
{
	if(RigidBodyResetOrientation(i))
	{
		printf("Rigid body (%ls) orientation reset", RigidBodyName(i));
	}
}
```
{% endcode %}

</details>

<details>

<summary>RigidBodyMarkerCount</summary>

Gets total number of markers in a Rigid Body.

{% code overflow="wrap" %}
```cpp
int		RigidBodyMarkerCount(int rbIndex);
```
{% endcode %}

**Description**

* This function returns the total number of markers involved in a Rigid Body.

**Function Input**

* Rigid body index (int)

**Function Output**

* Total number of marker in the Rigid Body (int)

**C++ Example**

{% code overflow="wrap" %}
```cpp
int rbcount = RigidBodyCount();

//== Listing out all of the Rigid Body markers ==// 
for(int i = 0; i < rbcount; i++)
{
	printf("Rigid Body:%ls\t Marker Count: %d", RigidBodyName(i), RigidBodyMarkerCount(i));
}
```
{% endcode %}

</details>

<details>

<summary>RigidBodyMarker</summary>

Retrieves the positional offset of a marker constraint from a defined rigid body.

{% code overflow="wrap" %}
```cpp
bool		RigidBodyMarker(int rbIndex, int markerIndex, float* x, float* y, float* z);
```
{% endcode %}

**Description**

* This function gets the 3D position of a solved Rigid Body marker and saves them in designated addresses. Rigid body marker positions from this function represents solved (or expected) location of the Rigid Body markers.&#x20;
* Note that the 3D coordinates obtained by this function are represented in respect to Rigid Body's local coordinate axis.&#x20;

**Function Input**

* Rigid body index (int)
* Marker index (int)
* Three declared variable addresses for saving the  x, y, z coordinates of the marker (float)

**Function Output**

* True / False (bool)

**C++ Example**&#x20;

{% code overflow="wrap" %}
```cpp
//== Listing out all of the Rigid Body markers and its respective position. ==//
int rbcount = RigidBodyCount();

for(int i = 0; i < rbcount; i++)
{
	float	x,y,z;

	for(int j = 0; j < RigidBodyMarkerCount(i); j++)
	{
		wchar_t name[ 256 ];
		RigidBodyName( i, name, 256 );
		printf("Rigid Body:%ls\t Marker #%d\n", RigidBodyName(i), j);
		
		//== Marker Locations ==//
		RigidBodyMarker(i, j, &x, &y, &z);
		printf("Local: (%f, %f, %f)\n", x, y, z);
	}
}
```
{% endcode %}

</details>

<details>

<summary>RigidBodyUpdateMarker</summary>

Changes and updates the Rigid Body marker constraint positions.

{% code overflow="wrap" %}
```cpp
bool     RigidBodyUpdateMarker( int rbIndex, int markerIndex, float x, float y, float z );
```
{% endcode %}

**Description**

* This function is used to change the expected positions of a single Rigid Body marker.
* Rigid body markers are expected marker positions. Read about marker types in Motive.

**Function Input**

* Rigid body index (int)
* Marker index (int)
* New x-position of the Rigid Body marker in relation to the local coordinate system.
* New y-position of the Rigid Body marker in relation to the local coordinate system.
* New z-position of the Rigid Body marker in relation to the local coordinate system.

**Function Output**

* Returns true if marker locations have been successfully updated.

</details>

<details>

<summary>RigidBodyReconstructedMarker</summary>

Retrieves the reconstructed marker location for a marker constraint on a defined rigid body in the current frame.

{% code overflow="wrap" %}
```cpp
bool	RigidBodyReconstructedMarker( int rbIndex, int markerIndex, bool& tracked,       float& x, float& y, float& z );
```
{% endcode %}

**Description**

* This function retrieves 3D coordinates of each expected Rigid Body marker positions in designated variable addresses.
* 3D coordinates are saved in respect to global coordinate system.

**Function Input**

* Rigid body index (int)
* Marker index (int)
* Tracked status, True or False (bool)
* Three declared variable addresses for saving x, y, z coordinates of the marker (float).

**Function Output**

* Returns true if marker locations were found and successfully returned.

**C++ Example**

{% code overflow="wrap" %}
```cpp
//== Listing out all of the Rigid Body markers and its respective position. ==//
int rbcount = RigidBodyCount();

for(int i = 0; i < rbcount; i++)
{
	float	gx, gy, gz;
	bool	tracked;

	for(int j = 0; j < RigidBodyMarkerCount(i); j++)
	{
		printf("Rigid Body:%ls\t Marker #%d\n", RigidBodyName(i), j);
		 
		//== Expected Rigid Body marker positions. ==//
		RigidBodyReconstructedMarker(i, j, tracked, gx, gy, gz);
		printf("Global: (%f, %f, %f)\n", x, y, z);
	}
}
```
{% endcode %}

</details>

<details>

<summary>RigidBodyMeanError</summary>

Returns a mean error of the Rigid Body tracking data.

{% code overflow="wrap" %}
```cpp
float		RigidBodyMeanError(int rbIndex);
```
{% endcode %}

**Description**

* Returns the average distance between the constraint location and the corresponding reconstructed marker, for all constraints.&#x20;

**Function Input**

* Rigid body index (int)

**Function Output**

* Mean error (meters)

</details>

## Rigid Body Refinement

In this section:

[RigidBodyRefineStart ](motive-api-function-reference.md#rigidbodyrefinestart)| [RigidBodyRefineSample](motive-api-function-reference.md#rigidbodyrefinesample) | [RigidBodyRefineState ](motive-api-function-reference.md#rigidbodyrefinestate)| [RigidBodyRefineProgress ](motive-api-function-reference.md#rigidbodyrefineprogress)| [RigidBodyRefineInitialError ](motive-api-function-reference.md#rigidbodyrefineinitialerror)| [RigidBodyRefineResultError ](motive-api-function-reference.md#rigidbodyrefineresulterror)| [RigidBodyRefineApplyResult ](motive-api-function-reference.md#rigidbodyrefineapplyresult)| [RigidBodyRefineReset ](motive-api-function-reference.md#rigidbodyrefinereset)|&#x20;

***

#### RigidBodyRefineStart

Initiates the Rigid Body refinement process. Input the number of samples and the ID of the Rigid Body you wish to refine. After starting the process, `RigidBodyRefineSample` must be called on every frame  to collect samples.

```
bool     RigidBodyRefineStart( Core::cUID rigidBodyID, int sampleCount );
```

**Description**

* This function is used to start Rigid Body refinement.

**Function Input**

* Target Rigid Body ID
* Sample count (int)

**Function Output**

* Returns true if the refinement process has successfully initiated.

***

#### RigidBodyRefineSample

This function collects samples for Rigid Body refinement after calling the `RigidBodyRefineStart` function. Call this function for every frame within the update loop. You can check the progress of calibration by calling the `RigidBodyRefineProgress` function.

```
bool     RigidBodyRefineSample();
```

**Description**

* This function collects Rigid Body tracking data for refining the definition of the corresponding Rigid Body.

**Function Input**

* None. Samples frames for the initialized refine progress.

**Function Output**

* Returns true if the refinement process has successfully collected a sample. This function does not collect samples if the Rigid Body is not tracked on the frame.

***

#### RigidBodyRefineState

This function inquiries the state of the refinement process. It returns `eRigidBodyRefineState` enum as a result.

```
eRigidBodyRefineState     RigidBodyRefineState();
```

**Description**

* This function queries the state of the Rigid Body refinement process. It returns an enum value for indicating whether the process is initialized, sampling, solving, complete, or uninitialized.

```
   <source> enum eRigidBodyRefineState {
   RigidBodyRefine_Initialized = 0,
   RigidBodyRefine_Sampling,
   RigidBodyRefine_Solving,
   RigidBodyRefine_Complete,
   RigidBodyRefine_Uninitialized
   };
   </source>
```

**Function Input**

* None. Checks the state on the ongoing refinement process.

**Function Output**

* Returns `eRigidBodyRefineState` enum value.

***

#### RigidBodyRefineProgress

This function retrieves the overall sampling progress of the rigid body refinement solver.

```
float     RigidBodyRefineProgress();
```

**Description**

* When the refinement process is under the _sampling_ state, calling this function returns the sampling progress. It will return a percentage value representing the sampling progress with respect to the total number of samples given in the `RigidBodyRefineStart` parameter.

**Function Input**

* None. Checks the progress on the ongoing refinement process.

**Function Output**

* Returns percentage completeness of the sampling process (float).

***

#### RigidBodyRefineInitialError

This function returns the error value of the Rigid Body definition before the refinement and is typically called in conjunction with `RigidBodyRefineResultError`.&#x20;

```
float     RigidBodyRefineInitialError();
```

**Description**

* Once the refinement process has reached _complete_ stage, this function can be called along with `RigidBodyRefineResultError` to compare the error values from the corresponding Rigid Body definition before and after the refinement.

**Function Input**

* None.

**Function Output**

* Average error value of the target Rigid Body definition prior (`RigidBodyRefineInitialError`) and after (RigidBodyRefineResultError) the refinement.

***

#### RigidBodyRefineResultError

This function returns the error value of the Rigid Body definition after the refinement.

```
float     RigidBodyRefineResultError();
```

**Description**

* Once the refinement process has reached _complete_ stage, this function can be called along with `RigidBodyRefineInitialError` to compare the error values from the corresponding Rigid Body definition before and after the refinement.

**Function Input**

* None.

**Function Output**

* Average error value of the target Rigid Body definition prior (`RigidBodyRefineInitialError`) and after (`RigidBodyRefineResultError`) the refinement.

***

#### RigidBodyRefineApplyResult

This function applies the refined result to the corresponding Rigid Body definition.

```
bool     RigidBodyRefineApplyResult();
```

**Description**

* This function applies the refinement to the Rigid Body definition. Call this function after comparing the error values before and after the refinement using the  `RigidBodyRefineInitialError` and `RigidBodyRefineResultError` functions.

**Function Input**

* None.

**Function Output**

* Returns true if the refined results have been successfully applied.

***

#### RigidBodyRefineReset

This function discards the final refinement result and resets the refinement process.

```
bool     RigidBodyRefineReset();
```

**Description**

* If the final refinement result from the `RigidBodyRefineResultError` call is not satisfying, you can call this function to discard the result and start over from the sampling process again.

**Function Input**

* None.

**Function Output**

* Returns true if the refined results have been successfully reset.

***

## Camera Interface

In this section:&#x20;

[CameraCount ](motive-api-function-reference.md#cameracount)| [CameraGroupCount](motive-api-function-reference.md#cameragroupcount) | [CameraGroup ](motive-api-function-reference.md#cameragroup)| [CameraSerial ](motive-api-function-reference.md#cameraserial)| [CameraObjectCount ](motive-api-function-reference.md#cameraobjectcount)| [CameraObject ](motive-api-function-reference.md#cameraobject)| [CameraObjectPredistorted ](motive-api-function-reference.md#cameraobjectpredistorted)| [SetCameraProperty](motive-api-function-reference.md#setcameraproperty)

***

#### CameraCount

Returns the total number of cameras connected to the system.

```
int		CameraCount();
```

**Description**

* This function returns a total camera count.

**Function Input**

* None

**Function Output**

* Total number of cameras (int)

**C++ Example**

```
//== Printing Frame rate of the cameras ==//
int totalCamera = CameraCount();
for( int i = 0; i < totalCamera; i++)
{
 	printf("%d frame rate: %d\n", CameraSerial(i), CameraFrameRate(i));
}
```

***

#### CameraGroupCount

Returns the camera group count.

```
int		CameraGroupCount();
```

**Description**

* This function returns the total count of camera groups that are involved in the project.
* This will generally return a value of two: one for the tracking cameras and one for reference cameras.&#x20;

**Function Input**

* None

**Function Output**

* Camera group count (int)

**C++ Example**

```
int groupcount = CameraGroupCount();

//== Processing Camera Groups ==//
for(int i = 0; i < groupcount; i++)
{
	//== Process each camera group ==//
}
```

***

#### CameraGroup

Returns an index value of a camera group that a camera is in.

```
int		CameraGroup(int cameraIndex);
```

**Description**

* This function takes an index value of a camera and returns the corresponding camera group index that the camera is in.

**Function Input**

* Camera index (int)

**Function Output**

* Camera group index (int)

**C++ Example**

```
//== Listing out all of the cameras and their associate group index ==//
int cameracount = CameraCount();

for(int i = 0; i < cameracount; i ++)
{
	printf("Camera: %d\t CameraGroup: #%d", CameraSerial(i), CameraGroup(i));
}
```

***

#### CameraSerial

Returns the corresponding camera's serial number as an integer.

```
int		CameraSerial(int cameraIndex);
```

**Description**

* This function returns the corresponding camera's serial number.

**Function Input**

* Camera index (int)

**Function Output**

* Camera serial number (int)

**C++ Example**

```
//== Displaying all connected cameras ==//
int totalCamera = CameraCount();

printf("Detected Cameras Serial Numbers:\n"); 
for (int i = 0; i < totalCamera; i++)
{
	printf("\t%d\n", CameraSerial(i));
}
```

***

#### CameraObjectCount

Returns a total number of objects detected by a camera in the current frame.

```
int		CameraObjectCount( int cameraIndex );
```

**Description**

* This function returns a total number of _centroids_ detected by a camera.
* A centroid is defined for every group of contiguous pixels that forms a shape that encloses the thresholded pixels.
* The size and roundness filter (cCameraGroupFilterSettings) is not applied in this data.

**Function Input**

* Camera index (int)

**Function Output**

* Number of centroids (int)

**C++ Example**

```
for (int i = 0; i < CameraCount(); i++)
{
	int centroidcount = CameraObjectCount(i);
	printf("Camera #%d detected centroids: %d\n", i, centroidcount);
}
```

***

#### CameraObject

Returns 2D location of the centroid as seen by a camera.

{% code overflow="wrap" %}
```
bool     CameraObject( int cameraIndex, int objectIndex, float& x, float& y );
```
{% endcode %}

**Description**

* This function saves 2D location of the centroid as detected by a camera's imager.
* Returns true if the function successfully saves the x and y locations.

**Function Input**

* Camera index (int)
* Object index (int)
* Declared variables for saving x and y (float)

**Function Output**

* True/False (bool)

**C++ Example**

```
int cameracount = CameraCount();

for (int i = 0; i < cameracount; i++)
{
	float x, y;
	int centroidcount = CameraObjectCount(i);
	printf("Camera #%d detected centroids: %d\n", i, centroidcount);

	for (int j = 0; j < centroidcount; j++)
	{
		if ( CameraObject(i, j, x, y) )
		{
			printf("\t#%d\t(%.2f, %.2f)\n", j, x, y);
		}
	}
}
```

***

#### CameraObjectPredistorted

Retrieve the pre-distorted object location in the view of the camera.

{% code overflow="wrap" %}
```
bool	CameraObjectPredistorted( int cameraIndex, int objectIndex, float& x, float& y );
```
{% endcode %}

**Description**

* This function saves the predistorted 2D location of a centroid.
* This data indicates where the camera would see a marker if there were no effects from lens distortions. For most of our cameras/lenses, this location is only a few pixels different from the distorted position obtained by the CameraObject function.
* Returns true when the values are successfully saved.

**Function Input**

* Camera index (int)
* Object (centroid) index (int)
* Declared variable for saving x location (float)
* Declared variable for saving y location (float)

**Function Output**

* True/False (bool)

**C++ Example**

{% code overflow="wrap" %}
```
for (int i = 0; i < CameraCount(); i++)
{
	float x, y, pdx, pdy;

	int centroidcount = CameraObjectCount(i);
	printf("Camera #%d detected centroids: %d\n", i, centroidcount);

	for (int j = 0; j < centroidcount; j++)
	{
		CameraObject(i, j, x, y);
		CameraObjectPredistorted(i, j, pdx, pdy);
		printf("\t#%d\t(%.2f, %.2f)\tPredistorted:\t(%.2f, %.2f)\n", j, x, y, pdx, pdy);
	}
}
```
{% endcode %}

***

#### SetCameraProperty

Configures the value of a camera property.

{% code overflow="wrap" %}
```
bool		SetCameraProperty( int cameraIndex, const std::wstring& propertyName, const sPropertyValue& value );
```
{% endcode %}

**Description**

* This function sets camera properties for a camera device specified by its index number.
* A false return value indicates the function did not complete the task.
* Each of the video types is indicated with the following integers. Supported video types may vary for different camera models. Please check the Data Recording page for more information on which image processing modes are available in different models.
* Segment Mode: 0
* Raw Grayscale Mode: 1
* Object Mode: 2
* Precision Mode: 4
* MJPEG Mode: 6
* Valid exposure ranges depend on the framerate settings:
* Prime series and Flex 13: 1 \~ maximum time gap between the frames, which is approximately (1 / framerate) - 200 microseconds with about 200 microseconds gap for protection.
* Valid threshold ranges: 0 - 255

**Function Input**

* Camera index (int)
* Name of the propety to set (const std::wstring&)
* For more information on the camera settings, refer to the Devices pane page.

**Function Output**

* True/False (bool)

***

### Full Frame Grayscale Decimation

In this section:&#x20;

[SetCameraGrayscaleDecimation](motive-api-function-reference.md#setcameragrayscaledecimation) | [CameraGrayscaleDecimation ](motive-api-function-reference.md#cameragrayscaledecimation)| [CameraIsContinuousIRAvailable ](motive-api-function-reference.md#cameraiscontinuousiravailable)| [CameraSetContinuousIR ](motive-api-function-reference.md#camerasetcontinuousir)| [CameraContinuousIR ](motive-api-function-reference.md#cameracontinuousir)| [SetCameraSystemFrameRate ](motive-api-function-reference.md#setcamerasystemframerate)| [CameraSystemFrameRate](motive-api-function-reference.md#camerasystemframerate) |

***

#### SetCameraGrayscaleDecimation

Sets frame rate decimation ratio for processing grayscale images.

```
bool		SetCameraGrayscaleDecimation(int cameraIndex, int value);
```

**Description**

* This feature is available only in Flex 3 and Trio/Duo tracking bars, and has been deprecated for other camera models.
* This functions sets the frame decimation ratio for processing grayscale images in a camera.
* Depending on the decimation ratio, a fewer number of grayscale frames will be captured. This can be beneficial when looking to reduce the processing loads.
* Supported decimation ratios: 0, 2, 4, 6, 8. When the decimation setting is set to 4, for example, a camera will capture one grayscale frame for 4 frames of the tracking data.
* Returns true when it successfully sets the decimation value.

**Function Input**

* Camera index (int)
* Decimation value (int)

**Function Output**

* True/False (bool)

**C++ Example**

```
//== Introducing frame decimation to reference cameras ==//
for (int i = 0; i < CameraCount(); i++)
{
	if (CameraVideoType(i) == 1 ||CameraVideoType(i) == 6)
	{
		SetCameraGrayscaleDecimation(i, 2);
		printf("Camera #%d grayscale video frame decimation: %d\n",
					i, CameraGrayscaleDecimation(i));
	}
}
```

***

#### CameraGrayscaleDecimation

Retrieves the configured grayscale image frame rate decimation ratio of a camera.

```
int		CameraGrayscaleDecimation(int cameraIndex);
```

**Description**

* This feature is available only in Flex 3 and Trio/Duo tracking bars, and it has been deprecated for other camera models.
* This function returns grayscale frame rate decimation ratio of a camera.
* Valid decimation ratios are 0, 2, 4, 8. When the decimation setting is set to 4, for example, a camera will capture one grayscale frame for 4 frames of the tracking data.
* To set the decimation ratio, use the [SetCameraGrayscaleDecimation](motive-api-function-reference.md#setcameragrayscaledecimation) function.
* Grayscale images require more load on data processing. Decimate the grayscale frame images and capture the frames at a lower frame rate to reduce the volume of data.

**Function Input**

* Camera index (int)

**Function Output**

* Decimation ratio (int)

**C++ Example**

```
//== Checking grayscale decimation ==//
for (int i = 0; i < CameraCount(); i++)
{
	if (CameraVideoType(i) == 1 ||CameraVideoType(i) == 6)
	{
		printf("Camera #%d grayscale video frame decimation: %d\n",
					i, CameraGrayscaleDecimation(i));
	}
}
```

***

#### CameraIsContinuousIRAvailable

Checks if the continuous IR mode is supported.

```
bool		CameraIsContinuousIRAvailalbe(int cameraIndex);
```

**Description**

* This function checks whether the continuous IR illumination mode is available in the camera model.
* In the continuous IR mode, the IR LEDs will not strobe but will illuminate continuously instead.
* Continuous IR modes are available only in the Flex 3 camera model and the Duo/Trio tracking bars.
* Returns true if continuous IR mode is available.

**Function Input**

* Camera index (int)

**Function Output**

* True / False (bool)

**C++ Example**

```
//== Configuring Continuous IR ==//
int totalCamera = CameraCount();

for (int i = 0; i < totalCamera; i++)
{
	//== Checking if the mode is available ==//
	if (CameraIsContinuousIRAvailable(i))
	{
		if (CameraContinuousIR(i))
		{
			printf("Continuous IR enabled already\n");
		}
		else
		{
			printf("Enabling continuous IR\n");
			CameraSetContinuousIR(i, true);
		}
	}
	else
	{
		printf("Continuous IR is not available\n");
	}
}
```

***

#### CameraSetContinuousIR

Enables or disables continuous IR, if the camera supports it.

```
bool		CameraSetContinuousIR(int cameraIndex, bool enable);
```

**Description**

* This function enables, or disables, continuous IR illumination in a camera.
* Continuous IR mode outputs less light when compared to Strobed (non-continuous) illumination, but this mode could be beneficial in situations where there are extraneous IR reflections in the volume.
* Use the `CameraIsContinuousIRAvailable` function to check if the camera supports this mode.

**Function Input**

* Camera index (int)
* A Boolean argument for enabling (true) or disabling (false)

**Function Output**

* True / False (bool)

**C++ Example**

```
int totalCamera = CameraCount();

//== Configuring Continuous IR ==// 
for (int i = 0; i < totalCamera; i++)
{
	if (CameraIsContinuousIRAvailable(i))
	{
		//== Checking if already enabled ==//
		if (CameraContinuousIR(i))
		{
			printf("Coninuous IR enabled already\n");
		}
		else
		{
			printf("Enabling continuous IR\n");
			CameraSetContinuousIR(i, true);
		}
	}
	else
	{
		printf("Continuous IR is not available\n");
	}
}
```

***

#### CameraContinuousIR

Checks if the continuous IR mode is enabled.

```
bool		CameraContinuousIR(int cameraIndex);
```

**Description**

* This function checks if the continuous IR mode is enabled or disabled in a camera.
* Returns true if the continuous IR mode is already enabled.

**Function Input**

* Camera index (int)

**Function Output**

* True / False (bool)

**C++ Example**

```
int totalCamera = CameraCount();

//== Configuring Continuous IR ==// 
for (int i = 0; i < totalCamera; i++)
{
	if (CameraIsContinuousIRAvailable(i))
	{
		//== Checking if already enabled ==//
		if (CameraContinuousIR(i))
		{
			printf("Continuous IR enabled already\n");
		}
		else
		{
			printf("Enabling continuous IR\n");
			CameraSetContinuousIR(i, true);
		}
	}
	else
	{
		printf("Continuous IR is not available\n");
	}
}
```

***

#### SetCameraSystemFrameRate

Sets the camera frame rate.

```
bool		SetCameraSystemFrameRate(int framerate);
```

**Description**

* This function sets the master frame rate for the camera system.
* Returns true if it successfully adjusts the settings.
* Note that this function may assign a frame rate setting that is out of the supported range. Check to make sure the desired frame rates are supported.

**Function Input**

* Frame rate (frames/sec)

**Function Output**

* True/False (bool).

**C++ Example**

```
//== Changing frame rate of all cameras ==//
int framerate = 120;

for (int i = 0; i < CameraCount(); i++)
{
	SetCameraSystemFrameRate(i, framerate);
	printf("\t%d\tFrame Rate: %d", CameraSerial(i), CameraSystemFrameRate(i));
}
```

***

#### CameraSystemFrameRate

Retrieves the the current master system frame rate.

```
int		CameraSystemFrameRate();
```

**Description**

* This function returns the master frame rate of a camera system.

**Function Input**

* none

**Function Output**

* Camera frame rate (int)

**C++ Example**

{% code overflow="wrap" %}
```
//== Checking camera settings ==//
int totalCamera = CameraCount();

for (int i = 0; i < totalCamera; i++)
{
	printf("Camera #%d:\tFPS: %d\n",
		i, CameraSystemFrameRate(i) );
}
```
{% endcode %}

***

### Measured Camera System Frame Rate

In this section:

[CameraTemperature ](motive-api-function-reference.md#cameratemperature)| [CameraRinglightTemperature ](motive-api-function-reference.md#cameraringlighttemperature)| [SetCameraAGC ](motive-api-function-reference.md#setcameraagc)| [SetCameraAEC ](motive-api-function-reference.md#setcameraaec)| [CameraImagerGainLevels](motive-api-function-reference.md#cameraimagergainlevels)

***

#### CameraTemperature

Measures the image board temperature of a camera.

```
float		CameraTemperature(int cameraIndex);
```

**Description**

* This function returns the temperature (in Celsius) of a camera's image board.
* Temperature sensors are featured only in Prime series camera models.

**Function Input**

* Camera index (int)

**Function Output**

* Image board temperature (float)

**C++ Example**

```
//== Temperature settings ==//
for (int i = 0; i < CameraCount(); i++)
{
	printf("Camera #%d:\n",i);
	printf("\tImage Board Temperature: %.2f\n", CameraTemperature(i));
	printf("\tIR Board Temperature: %.2f\n", CameraRinglightTemperature(i));
	printf("\n");
}
```

***

#### CameraRinglightTemperature

Measures the IR LED board temperature of a camera.

```
float		CameraRinglightTemperature(int cameraIndex);
```

**Description**

* This function returns temperature (in celsius) of a camera's IR LED board.
* Temperature sensors are featured only in Prime series camera models.

**Function Input**

* Camera index (int)

**Function Output**

* IR LED board temperature (float)

**C++ Example**

```
//== Temperature settings ==//
for (int i = 0; i < CameraCount(); i++)
{
	printf("Camera #%d:\n",i);
	printf("\tImage Board Temperature: %.2f\n", CameraTemperature(i));
	printf("\tIR Board Temperature: %.2f\n", CameraRinglightTemperature(i));
	printf("\n");
}
```

***

#### SetCameraAGC

Enables or disables automatic gain control.

```
bool		SetCameraAGC(int cameraIndex, bool enable);
```

**Description**

* This function enables or disables automatic gain control (AGC).
* Automatic Gain Control feature adjusts the camera gain level automatically for best tracking.
* AGC is only available in Flex 3 cameras and Duo/Trio tracking bars.
* Returns true when the operation completed successfully.

**Function Input**

* Camera index (int)
* Enabled (true) / disabled (false) status (bool)

**Function Output**

* True/False (bool)

**C++ Example**

```
//== Setting the Automatic Exposure Control ==//
int totalCamera = CameraCount();

for(int i = 0; i < totalCamera; i++)
{
	if(SetCameraAGC(i, true))
	{
		printf("Camera #%d AGC enabled");
	}
	else
	{
		printf("AGC not set properly. Check if this is supported.");
	}
}
```

***

#### SetCameraAEC

Enables or disables automatic exposure control.

{% code overflow="wrap" %}
```
bool		SetCameraAEC(int cameraIndex, bool enable);
```
{% endcode %}

**Description**

* This function enables or disables Automatic Exposure Control (AEC) for featured camera models.
* This feature is only available in Flex 3 cameras and Duo/Trio tracking bars.
* AEC allows a camera to automatically adjust its exposure setting by looking at the properties of the incoming frames.
* Returns true if the operation was successful.

**Function Input**

* Camera index (int)
* A Boolean argument for enabling (true) or disabling (false) the filter.

**Function Output**

* True/false (bool)

**C++ Example**

```
//== Setting the Automatic Exposure Control ==//
int totalCamera = CameraCount();

for(int i = 0; i < totalCamera; i++)
{
	if(SetCameraAEC(i, true))
	{
		printf("Camera #%d AEC enabled");
	}
	else
	{
		printf("AEC not set properly. Check if this is supported.");
	}
}
```

***

#### CameraImagerGainLevels

Retrieves the total number of gain levels available in a camera.

```
int		CameraImagerGainLevels(int cameraIndex);
```

**Description**

* This function returns a total number of available gain levels in a camera.
* Different camera models may have different gain level settings. This function can be used to check the number of available gain levels.

**Function Input**

* Camera index (int)

**Function Output**

* Number of gain levels available (int)

**C++ Example**

{% code overflow="wrap" %}
```
//== Checking number of gain levels ==//
for (int i = 0; i < CameraCount(); i++)
{
	printf("%ls camera has %d gain levels\n", CameraSerial(i),CameraImagerGainLevels(i));
}
```
{% endcode %}

***

### Camera Masking

In this section:&#x20;

[ClearCameraMask ](motive-api-function-reference.md#clearcameramask)| [SetCameraMask ](motive-api-function-reference.md#setcameramask)| [CameraMask ](motive-api-function-reference.md#cameramask)| [CameraMaskInfo ](motive-api-function-reference.md#cameramaskinfo)| [AutoMaskAllCameras ](motive-api-function-reference.md#automaskallcameras)| [SetCameraState ](motive-api-function-reference.md#setcamerastate)| [CameraState](motive-api-function-reference.md#camerastate) | [CameraID ](motive-api-function-reference.md#cameraid)| [CameraFrameBuffer](motive-api-function-reference.md#cameraframebuffer) | [CameraFrameBufferSaveAsBMP ](motive-api-function-reference.md#cameraframebuffersaveasbmp)| [CameraBackproject](motive-api-function-reference.md#camerabackproject) | [CameraUndistort2DPoint ](motive-api-function-reference.md#cameraundistort2dpoint)| [CameraDistort2DPoint ](motive-api-function-reference.md#cameradistort2dpoint)| [CameraRay](motive-api-function-reference.md#cameraray) | [SetCameraPose ](motive-api-function-reference.md#setcamerapose)| [GetCamera](motive-api-function-reference.md#getcamera)

***

#### ClearCameraMask

Clears masking from camera's 2D view.

```
bool		ClearCameraMask(int cameraIndex);
```

**Description**

* This function clears existing masks from the 2D camera view.
* Returns true when it successfully removes pixel masks.

**Function Input**

* Camera index (int)

**Function Output**

* True / False (bool)

**C++ Example**

```
//== Clearing existing masks for all cameras ==//
int totalCamera = CameraCount();

for (int i = 0; i < totalCamera; i++)
{
    ClearCameraMask(i);
}
```

***

#### SetCameraMask

{% code overflow="wrap" %}
```
bool	SetCameraMask( int cameraIndex, unsigned char* buffer, int bufferSize );
```
{% endcode %}

**Description**

* This function allows a user-defined image mask to be applied to a camera.
* A mask is an array of bytes, one byte per mask pixel block.
* Returns true when masks are applied.

**Function Input**

* Camera index (int)
* Buffer
* BufferSize

**Function Output**

* True / False (bool)

**C++ Example**

```
unsigned char* maskBuffer = nullptr;
int bufferSize = 0;
int cameraCount = CameraCount();

// Retrieve the mask for each camera, perform a simple edit on it, then set it.
for( int i = 0; i < cameraCount; ++i )
{
   int maskWidth;
   int maskHeight;
   int maskGrid;

   // Mask dimensions for the camera.
   CameraMaskInfo( i, maskWidth, maskHeight, maskGrid );

   int newBufferSize = maskWidth * maskHeight;
   if( bufferSize < newBufferSize )
   {
       delete[] maskBuffer;
       maskBuffer = new unsigned char[newBufferSize];
       bufferSize = newBufferSize;
   }

   // Retrieve the mask now that the receiving buffer is correctly sized.
   CameraMask( i, maskBuffer, bufferSize );

   // Add a mask 'pixel' in the approximate center of the image.
   // Each pixel is actually a grid of maskGrid size.
   int pixelIndex = ( maskHeight / 2 ) * maskWidth + ( maskWidth / 2 );
   maskBuffer[pixelIndex] = 1; // Any non-zero value for the byte will do.

   // Set the mask image on the camera.
   SetCameraMask( i, maskBuffer, bufferSize );
}
```

***

#### CameraMask

{% code overflow="wrap" %}
```
bool		CameraMask(int cameraIndex, unsigned char* buffer, int bufferSize);
```
{% endcode %}

**Description**

* This function returns the memory block of the mask.
* One bit per a pixel of the mask.
* Masking pixels are rasterized from left to right and from top to bottom of the camera's view.

**Function Input**

* Camera index (int)
* Buffer
* Buffer size

**Function Output**

* True / False (bool)

**C++ Example**

```
unsigned char* maskBuffer = nullptr;
int bufferSize = 0;
int cameraCount = CameraCount();

// Retrieve the mask for each camera, perform a simple edit on it, then set it.
for( int i = 0; i < cameraCount; ++i )
{
   int maskWidth;
   int maskHeight;
   int maskGrid;

   // Mask dimensions for the camera.
   CameraMaskInfo( i, maskWidth, maskHeight, maskGrid );

   int newBufferSize = maskWidth * maskHeight;
   if( bufferSize < newBufferSize )
   {
       delete[] maskBuffer;
       maskBuffer = new unsigned char[newBufferSize];
       bufferSize = newBufferSize;
   }

   // Retrieve the mask now that the receiving buffer is correctly sized.
   CameraMask( i, maskBuffer, bufferSize );

   // Add a mask 'pixel' in the approximate center of the image.
   // Each pixel is actually a grid of maskGrid size.
   int pixelIndex = ( maskHeight / 2 ) * maskWidth + ( maskWidth / 2 );
   maskBuffer[pixelIndex] = 1; // Any non-zero value for the byte will do.

   // Set the mask image on the camera.
   SetCameraMask( i, maskBuffer, bufferSize );
}
```

***

#### CameraMaskInfo

{% code overflow="wrap" %}
```
bool		CameraMaskInfo(int cameraIndex, int& blockingMaskWidth, int& blockingMaskHeight, int& blockingMaskGrid);
```
{% endcode %}

**Description**

* This function retrieves the width, height, and grid size of the mask for the camera at the given index.
* One byte per pixel of the mask. Masking width \* masking height gives the required size of the buffer.
* Returns true when the information is successfully obtained and saved.

**Function Input**

* Camera index (int)
* Declared variables:
  * Masking width (int)
  * Masking height (int)
  * Masking grid (int)

**Function Output**

* True / False (bool)

**C++ Example**

```
unsigned char* maskBuffer = nullptr;
int bufferSize = 0;
int cameraCount = CameraCount();

// Retrieve the mask for each camera, perform a simple edit on it, then set it.
for( int i = 0; i < cameraCount; ++i )
{
   int maskWidth;
   int maskHeight;
   int maskGrid;

   // Mask dimensions for the camera.
   CameraMaskInfo( i, maskWidth, maskHeight, maskGrid );

   int newBufferSize = maskWidth * maskHeight;
   if( bufferSize < newBufferSize )
   {
       delete[] maskBuffer;
       maskBuffer = new unsigned char[newBufferSize];
       bufferSize = newBufferSize;
   }

   // Retrieve the mask now that the receiving buffer is correctly sized.
   CameraMask( i, maskBuffer, bufferSize );

   // Add a mask 'pixel' in the approximate center of the image.
   // Each pixel is actually a grid of maskGrid size.
   int pixelIndex = ( maskHeight / 2 ) * maskWidth + ( maskWidth / 2 );
   maskBuffer[pixelIndex] = 1; // Any non-zero value for the byte will do.

   // Set the mask image on the camera.
   SetCameraMask( i, maskBuffer, bufferSize );
}
```

***

#### AutoMaskAllCameras

Auto-mask all cameras with additional masking data.

```
void		AutoMaskAllCameras();
```

**Description**

* Auto-mask all cameras.
* This is additive to any existing masking.
* To clear masks on a camera, call ClearCameraMask prior to auto-masking.

**Function Input**

* none

**Function Output**

* Auto masks all cameras

***

#### SetCameraState

Sets the state for a camera.

```
bool		SetCameraState(int cameraIndex, eCameraState state);
```

**Description**

* This function configures the camera state of a camera. Different camera states are defined in the **eCameraState** enumeration.
* Returns true when it successfully sets the camera state.

```
enum eCameraState
{
    Camera_Enabled = 0,
    Camera_Disabled_For_Reconstruction = 1,
    Camera_Disabled = 2,
   };
```

**Function Input**

* Camera index (int)
* Camera state (eCameraState)

**Function Output**

* True / False (bool)

**C++ Example**

```
int totalCamera = CameraCount();

//== Disabling all of the cameras from contributing to reconstruction ==//
for (int i = 0; i < totalCamera; i++)
{
	SetCameraState(i, Camera_Enabled);
}
```

***

#### CameraState

Retrieves the current participation state of a camera.

```
bool		CameraState(int cameraIndex, eCameraState& currentState);
```

| Enumerator                            | Value |
| ------------------------------------- | ----- |
| Camera\_Enabled                       | 0     |
| Camera\_Disabled\_For\_Reconstruction | 1     |
| Camera\_Disabled                      | 2     |

**Description**

* This function obtains and saves the camera state of a camera onto the declared variables.
* Returns true if it successfully saves configured state.

**Function Input**

* Camera index (int)
* Declared variable for camera state (eCameraState)

**Function Output**

* True / False (bool)

**C++ Example**

```
//== Checking Camera Status ==//
int totalCamera = CameraCount();
eCameraStates cameraState;

for (int i = 0; i < totalCamera; i++)
{
	//== Checking the Camera Status ==//
	CameraState(i, cameraState);

	if (cameraState == 0) {
		printf("Camera #%d State: Camera_Enabled\n", i);
	}
	else if (cameraState == 1)
	{
		printf("Camera #%d State: Camera_Disabled_For_Reconstruction\n",i );
	}
	else if (cameraState == 2)
	{
		printf("Camera #%d State: Camera_Disabled\n", i);
	}	
}
```

***

#### CameraID

Returns the Camera ID.

```
int		CameraID(int cameraIndex);
```

**Description**

* This function takes in a camera index number and returns the camera ID number.
* Camera ID numbers are the numbers that are displayed on the devices.
* The Camera ID number is different from the camera index number.&#x20;
  * On Prime camera systems, Camera IDs are assigned depending on where the cameras are positioned within the calibrated volume.&#x20;
  * On Flex camera systems, Camera IDs are assigned according to the order in which devices connected to the OptiHub(s).

**Function Input**

* Camera index (int)

**Function Output**

* Camera ID (int)

**C++ Example**

{% code overflow="wrap" %}
```
int totalCamera = CameraCount();

for(int i = 0; i < totalCamera; i++){
	// Listing Camera Serial, index, and ID
	printf("Camera %d:\tIndex:%d\tID:%d\n", CameraSerial(i), i, CameraID(i)); 
}
```
{% endcode %}

***

#### CameraFrameBuffer

Fills a buffer with images from camera's view.

{% code overflow="wrap" %}
```
bool	CameraFrameBuffer(int cameraIndex, int bufferPixelWidth, int bufferPixelHeight, int bufferByteSpan, int bufferPixelBitDepth, unsigned char* buffer);
```
{% endcode %}

**Description**

* This function fetches raw pixels from a single frame of a camera and fills the provided memory block with the frame buffer.
* The resulting image depends on which video mode the camera is in. For example, if the camera is in grayscale mode, a grayscale image will be saved from this function call.
* For obtaining buffer pixel width and height, you can use the CameraNodeImagerPixelSize property to obtain respective camera resolution.
* Byte span: Byte span is the number of bytes for each row of the frame. In a case of 8-bit pixel images (one byte per pixel), the number of pixels in the frame width will equal to the byte size of the span.
* Buffer pixel bit depth: Pixel bit size for the image buffer that will be stored in the memory. If the imagers on the OptiTrack cameras capture 8-bit grayscale pixels, you will need to input 8 for this input.
* Buffer: make sure enough memory is allocated for the frame buffer. A frame buffer will require memory of at least (Byte span \* pixel height \* Bytes per pixel) bytes. For example, on a 640 x 480 image with 8-bit black and white pixels, you will need (640 \* 480 \* 1) bytes allocated for the frame buffer.
* Returns true if it successfully saves the image in the buffer.

**Function Input**

* Camera index (int)
* Buffer pixel width (int)
* Buffer pixel height (int)
* Buffer byte span (int)
* Buffer pixel bit depth (int)
* Buffer address (unsigned char\*)

**Function Output**

* True / False (bool)

**C++ Example**

{% code overflow="wrap" %}
```
// Sample code for saving frame buffer from a camera (index 0)
int cameraIndex = 0;
int reswidth;
int resheight;
int bytespan;

// Obtaining pixel resolution
CameraPixelResolution(cameraIndex, reswidth, resheight);
printf("Camera #%d:\tWidth:%d\tHeight:%d\n", i, reswidth, resheight);

// Defining span size of the buffer
bytespan = reswidth;

// Allocating memory block for the buffer
unsigned char* frameBuffer = (unsigned char*)std::malloc(bytespan*resheight*1);

bool result = CameraFrameBuffer(cameraIndex, reswidth, resheight, bytespan, 8, frameBuffer);

if (result == true)
{
	printf("Frame Buffer Saved.");
}
```
{% endcode %}

***

#### CameraFrameBufferSaveAsBMP

Saves image buffer of a camera into a BMP file.

```
bool		CameraFrameBufferSaveAsBMP(int cameraIndex, const wchar_t* filename);
```

**Description**

* This function saves image frame buffer of a camera into a BMP file.
* Video type of the saved image depends on configured camera settings
* Attaches \*.bmp at the end of the filename.
* Returns true if it successfully saves the file.

**Function Input**

* Camera index (int)
* Filename (const wchar\_t\*)

**Function Output**

* True / False (bool)

**C++ Example**

```
int cameraCount = CameraCount();
std::vector<std::string> filenames(cameraCount);

for (int i = 0; i < cameraCount; ++i)
{
	filenames[i] = "camera" + std::to_string(i) + ".bmp";
	CameraFrameBufferSaveAsBMP(i, filenames[i].c_str());
}
```

***

#### CameraBackproject

Obtains the 2D position of a 3D marker as seen by one of the cameras.

{% code overflow="wrap" %}
```
void		CameraBackproject(int cameraIndex, float x, float y, float z, float& cameraX, float& cameraY);
```
{% endcode %}

**Description**

* This function reverts 3D data into 2D data. If you input a 3D location (in meters) and a camera, it will return where the point would be seen from the 2D view of the camera (in pixels) using the calibration information. In other words, it locates where in the camera's FOV a point would be located.
* If a 3D marker is reconstructed outside of the camera's FOV, saved 2D location may be beyond the camera resolution range.
* Respective 2D location is saved in the declared X-Y address, in pixels.

**Function Input**

* Camera index (int)
* 3D x-position (float)
* 3D y-position (float)
* 3D z-position (float)
* Declared variable for x and y location from camera's 2D view (float)

**Function Output**

* Void

***

#### CameraUndistort2DPoint

Removes lens distortion.

```
void		CameraUndistort2DPoint(int cameraIndex, float& x, float& y);
```

**Description**

* This function removes the effect of the lens distortion filter and obtains undistorted raw x and y coordinates (as seen by the camera) and saves the data in the declared variables.
* Lens distortion is measured during the camera calibration process.
* If you want to re-apply the lens distortion filter, use the `CameraDistort2DPoint` function.

**Function Input**

* Camera index (int)
* Declared variables for x and y position in respect to camera's view (float)

**Function Output**

* Void

**C++ Example**

```
// Reflection detected at (125, 213) from 2D view of a camera 1.
int x = 125;
int y = 213;
int cameraIndex = 1;

// Saving raw, undistorted, coordinates as seen by the imager
CameraUndistort2DPoint(cameraIndex, x, y);
```

***

#### CameraDistort2DPoint

Reapplies the lens distortion model.

```
void		CameraDistort2DPoint(int cameraIndex, float& x, float& y);
```

**Description**

* This function restores the default model for accommodating effects of the camera lens.
* Note all reported 2D coordinates are already distorted to accommodate for effects of the camera lens. Use the `CameraUndistort2DPoint` function when working with coordinates that are _undistorted_ .
* This can be used to obtain raw data for 2D points that have been undistorted using the CameraUndistort2DPoint function.

**Function Input**

* Camera index (int)
* Declared variables for x and y position in respect to camera's view (float)

**Function Input**

* Void

**C++ Example**

```
// Reflection detected at (125, 213) from 2D view of a camera 1.
int x = 125;
int y = 213;
int cameraIndex = 1;

// Saving raw, undistorted, coordinates as seen by the imager.
CameraUndistort2DPoint(cameraIndex, x, y);

// Process undistorted x y coordinates..

// Apply the distortion back again
CameraDistort2DPoint(cameraIndex, x, y);
```

***

#### CameraRay

Obtains 3D vector from a camera to a 3D point.

{% code overflow="wrap" %}
```
bool		CameraRay(int cameraIndex, float x, float y, 
				float& rayStartX, float& rayStartY, float& rayStartZ, 
				float& rayEndX, float& rayEndY, float& rayEndZ);
```
{% endcode %}

**Description**

* This function takes in an undistorted 2D centroid location seen by a camera's imager and creates a 3D vector _ray_ connecting the point and the camera.
* Use `CameraUndistort2DPoint` to undistort the 2D location before obtaining the 3D vector.
* XYZ locations of both the start point and end point are saved into the referenced variables.
* Returns true when it successfully saves the ray vector components.

**Function Input**

* Camera index (int)
* x location, in pixels, of a centroid (float)
* y location, in pixels, of a centroid (float)
* Three reference variables for X/Y/Z location, in meters, of the start point (float)
* Three reference variables for X/Y/Z location, in meters, of the end point (float)

**Function Output**

* True / False (bool)

**C++ Example**

{% code overflow="wrap" %}
```
//== Obtaining a 3D vector for centroid detected at (100, 300) on a camera's 2D imager ==//
int targetcam = 0;
float  rayStartX, rayStartY, rayStartZ; //meters
float  rayEndX, rayEndY, rayEndZ; //meters
float x = 100; //pixels
float y = 300; //pixels
CameraUndistort2DPoint(targetcam, x, y);

CameraRay(targetcam, x, y, rayStartX, rayStartY, rayStartZ, rayEndX, rayEndY, rayEndZ);
```
{% endcode %}

***

#### SetCameraPose

Sets the camera's extrinsics for the OpenCV intrinsic model.

{% code overflow="wrap" %}
```
bool		SetCameraPose (int cameraIndex, float x, float y, float z, const float* orientation);
```
{% endcode %}

**Description**

* This function sets camera's extrinsic (position & orientation) and intrinsic (lens distortion) parameters with values compatible with the OpenCV intrinsic model.
* Returns true if the operation was successful.

**Function Input**

* Camera index (int)
* Three arguments for camera x,y,z position, in meters, within the global space (float)
* Camera orientation (3x3 orientation matrix)

**Function Output**

* True / False (bool)

***

#### GetCamera

Retrieves a CameraLibrary camera object from Camera SDK.

{% code overflow="wrap" %}
```
std::shared_ptr<CameraLibrary::Camera>		GetCamera(int cameraIndex);
```
{% endcode %}

**Description**

* This function returns a pointer to the Camera SDK's camera pointer.
* While the API takes over the data path which prohibits fetching the frames directly from the camera, it is still very useful to be able to communicate with the camera directly for setting camera settings or attaching modules.
* The Camera SDK must be installed to use this function.
* Camera SDK libraries and the camera library header file (cameralibrary.h) must be included.
* Returns Camera SDK Camera.

**Function Input**

* Camera index (int)

**Function Output**

* Camera SDK camera pointer (CameraLibrary::Camera)

**C++ Example**

{% code overflow="wrap" %}
```
CameraLibrary::Camera *cam = GetCameraManager();
// cam is declared as a pointer to a camera object used in conjuction with the Camera SDK
```
{% endcode %}

***

## Additional Functionality

In this section:

[AttachCameraModule / DetachCameraModule](motive-api-function-reference.md#attachcameramodule-detachcameramodule) | [OrientTrackingBar ](motive-api-function-reference.md#orienttrackingbar)|

***

#### AttachCameraModule / DetachCameraModule

Attaches/detaches cCameraModule instance to a camera object.

{% code overflow="wrap" %}
```
bool		AttachCameraModule(int cameraIndex, CameraLibrary::cCameraModule *module);
```
{% endcode %}

{% code overflow="wrap" %}
```
bool		DetachCameraModule(int cameraIndex, CameraLibrary::cCameraModule* module);
```
{% endcode %}

**Description**

* This function attaches/detaches the cCameraModule class to a camera defined by its index number.
* This function requires the project to be compiled against both the Motive API and the Camera SDK.
* The cCameraModule class is inherited from the Camera SDK, and this class is used to inspect raw 2D data from a camera. Use this function to attach the module to a camera. For more details on the cCameraModule class, refer to the _cameramodulebase.h_ header file from the Camera SDK.
* The Camera SDK must be installed.

**Function Input**

* Camera index (int)
* cCameraModule instance (CameraLibrary::cCameraModule)

**Function Output**

* Returns true if successful

***

#### OrientTrackingBar

Changes position and orientation of the tracking bars.

{% code overflow="wrap" %}
```
eRESULT		OrientTrackingBar(float positionX, float positionY, float positionZ,
float orientationX, float orientationY, float orientationZ, float orientationW);
```
{% endcode %}

**Description**

* This function makes changes to the position and orientation of the tracking bar within the global space.
* Note that this function will shift or rotate the entire global space, and the effects will be reflected in other tracking data as well.
* By default, the center location and orientation of a Tracking bar (Duo/Trio) determines the origin of the global coordinate system. Using this function, you can set a Tracking Bar to be placed in a different location within the global space instead of origin.

**Function Input**

* X position (float)
* Y position (float)
* Z position (float)
* Quaternion orientation X (float)
* Quaternion orientation Y (float)
* Quaternion orientation Z (float)
* Quaternion orientation W (float)

**Function Output**

* eRESULT

**C++ Example**

{% code overflow="wrap" %}
```
//== Changing position and orientation of a tracking bar within the global space. ==//
OrientTrackingBar(10, 10, 10, 0.5, 0.5, 0.5, 0.5);
```
{% endcode %}

***

## Camera Manager Access

In this section:

[CameraManager](motive-api-function-reference.md#cameramanager)

***

#### CameraManager

When using the Motive API in conjunction with the Camera SDK, this method will provide access to the manager class that owns all Camera instances. From here, many system state properties can be set or queried, cameras can be queried or edited, etc.

```
CameraLibrary::CameraManager*		CameraManager();
```

**Description**

* This function returns a pointer to the **CameraManager** instance from the Camera SDK.
* If a CameraManager instance is not found, MotiveAPI will create a new one.
* Camera SDK must be installed to use this function.
* The version number of Motive and the Camera SDK must match.
* Corresponding headers and libraries must be included in the program.

**Function Input**

* None

**Function Output**

* Pointer to the CameraManager instance (CameraLibrary::CameraManager\*)

**C++ Example**

{% code overflow="wrap" %}
```
// cameraManager is declared as a pointer to a CameraLibrary::CameraManager
// used in conjuction with the Camera SDK

CameraLibrary::CameraManager *cameraManager = CameraManager();
```
{% endcode %}

***

## API Callbacks

In this section:

[AttachListener / DetachListener](motive-api-function-reference.md#attachlistener-detachlistener)

***

#### AttachListener / DetachListener

Attaches/detaches `cAPIListener` onto an API project.&#x20;

```
void		AttachListener(cAPIListener* listener);
```

```
void		DetachListener();
```

**Description**

* This function attaches/detaches a `cAPIListener` inherited class onto an API project.
* The `cAPIListener` class uses the C++ inheritance design model. Inherit this class into your project with the same function and class names, then attach the inherited class.
* This listener class includes useful callback functions that can be overridden. Including APIFrameAvailable, APICameraConnected, APICameraDisconnected, InitialPointCloud, ApplyContinuousCalibrationResult.

**Function Input**

* cAPIListener

**Function Output**

* Void

***

## Result Processing

In this section:

[MapToResultString](motive-api-function-reference.md#maptoresultstring)

***

#### MapToResultString

Returns the plain text message that corresponds to an eRESULT value.

```
const 		std::wstring MapToResultString( eResult result );
```

**Description**

* Returns the plain text message that corresponds to a result that an eRESULT value indicates.

**Function Input**

* eRESULT

**Function Output**

* Result text (const std::wstring)

**C++ Example**

{% code overflow="wrap" %}
```
//== Sample Check Result Function (marker.cpp) ==//
void CheckResult( eRESULT result )
{
	if( result != kApiResult_Success )
	{
		//== Treat all errors as failure conditions. ==//
		printf( "Error: %ls\n\n(Press any key to continue)\n", MapToResultString(result) );
 
		Sleep(20);
		exit(1);
	}
}
```
{% endcode %}
