---
description: A guide to the functions available in the Motive API.
---

# Motive API: Function Reference

_Please use the table of contents to the right to navigate to specific functions or specific group of functions._

{% hint style="danger" %}
**Important Note:**

Some of the functions may be missing in the documentation. Please refer to the NPTrackingTools header file for any information that are not documented here.
{% endhint %}

## Project Management

### TT\_Initialize

Initializes the API and prepares all connected devices for capturing. Please note that TT\_Initialize also loads the default profile from the ProgramData directory: `C:\ProgramData\OptiTrack\MotiveProfile.motive`. When there is a need to load the profile from a separate directory, use TT\_LoadProfile function.

**Description**

* This function initializes the API library and prepares all connected devices for capturing.
* When using the API, this function needs to be called at the beginning of a program before using the cameras.
* Returns an eMotiveAPIResult value. When the function successfully updates the data, it returns 0 (or kApiResult\_Success).

**Function Input**

* None

**Function Output**

* eMotiveAPIResult

### TT\_Shutdown

Shuts down all of the connected devices.

**Description**

* This function closes down all connected devices and the camera library. To ensure that all devices properly shutdown, call this function before terminating an application.
* When the function successfully closes down the devices, it returns 0 (or kApiResult\_Success).
* When calling this function, currently configured camera calibration will be saved under the default System Calibration.cal file.

**Function Input**

* None

**Function Output**

* eMotiveAPIResult

### TT\_Update

Processes incoming frame data from the cameras.

**Description**

* This function updates frame information with the most recent data from the cameras and 3D processing engines.
* Another use of this function is to pick up newly connected cameras. Call this function at the beginning of a program in order to make sure that all of the new cameras are properly recognized.
* **TT\_Update vs. TT\_UpdateSingleFrame**: In the case when a client application stalls momentarily, the program may get behind on updating the frames. In this situation, the TT\_Update() function will disregard accumulated frames and service only the most recent frame data, but this also means that the client application will be missing the previous frames. On the other hand, the TT\_UpdateSingleFrame function ensures that always a consecutive frame is updated each time the function is called. In general, a user should always use TT\_Update(). Only in the case where a user wants to ensure their client application has access to every frame of tracking data and they are having problems calling TT\_Update() in a timely fashion, should they consider using TT\_UpdateSingleFrame(). If it is important for your program to obtain and process every single frame, use the TT\_UpdateSingleFrame() function for updating the data.
* Returns an eMotiveAPIResult integer value, depending on whether the operation was successful or not. Returns kApiResult\_Success when it successfully updates the frame data.

**Function Input**

* None

**Function Output**

* eMotiveAPIResult

### TT\_UpdateSingleFrame

Updates a single frame of camera data.

**Description**

* Every time this function is called, it updates frame information with the next frame of camera data.
* Using this function ensures that every frame of data is processed.
* **TT\_Update() vs. TT\_UpdateSingleFrame()**: In the case when a client application stalls momentarily, the program may get behind on updating the frames. In this situation, the TT\_Update() function will disregard accumulated frames and service only the most recent frame data, but this also means that the client application will be missing the previous frames. On the other hand, the TT\_UpdateSingleFrame function ensures that always a consecutive frame is updated each time the function is called. In general, a user should always use TT\_Update(). Only in the case where a user wants to ensure their client application has access to every frame of tracking data and they are having problems calling TT\_Update() in a timely fashion, should they consider using TT\_UpdateSingleFrame(). If it is important for your program to obtain and process every single frame, use the TT\_UpdateSingleFrame() function for updating the data.
* Returns an eMotiveAPIResult value. When the function successfully updates the data, it returns 0 (or kApiResult\_Success).

**Function Input**

* None

**Function Output**

* eMotiveAPIResult

### TT\_LoadCalibration, TT\_LoadCalibrationW

Loads a Motive camera calibration file.

**Description**

* These functions load a camera calibration file (CAL).
* Camera calibration files need to be exported from Motive.
* Returns an eMotiveAPIResult integer value. If the file was successfully loaded, it returns kApiResult\_Success.

**Function Input**

* Filename (const char, const wchar\_t)

**Function Output**

* eMotiveAPIResult

### TT\_LoadRigidBodies, TT\_LoadRigidBodiesW

Imports the profile file (.motive) and loads Rigid Body assets from it.

**Description**

* This function imports and loads Rigid Body assets from a saved profile file.
* Profile files (.motive) contain exported Rigid Body asset definitions from Motive.
* All existing assets in the project will be replaced with the Rigid Body assets from the profile file when this function is called. If you want to keep existing assets and only wish to add new Rigid Bodies, use TT\_AddRigidBodies function.
* Returns an eMotiveAPIResult integer value. It returns kApiResult\_Success when the file is successfully loaded.

**Function Input**

Filename (const char, const wchat\_t)

**Function Output**

eMotiveAPIResult

### TT\_SaveRigidBodies, TT\_SaveRigidBodiesW

Saves all of the Rigid Body asset definitions into a TRA file.

**Description**

* This function saves all of the Rigid Body assets from the project into the .MOTIVE profile file.&#x20;
* Returns an eMotiveAPIResult integer value. It returns 0 or kApiResult\_Success when successfully saving the file.

**Function Input**

Filename (const char, const wchar\_t)

**Function Output**

eMotiveAPIResult

### TT\_AddRigidBodies, TT\_AddRigidBodiesW

Loads a profile file (MOTIVE) and adds its Rigid Body assets onto the project.

**Description**

* This function adds Rigid Body assets from the imported profile file onto the existing list.
* Adds Rigid Bodies from imported profile files onto the asset list of the current project.
* Returns an eMotiveAPIResult integer value. If the Rigid Bodies have been added successfully, it returns 0 or kApiResult\_Success.

**Function Input**

Filename (const char, const wchat\_t)

**Function Output**

eMotiveAPIResult

### TT\_LoadProfile, TT\_LoadProfileW

Loads a Motive User Profile (.MOTIVE).

**Description**

* Loads the default application profile file (MOTIVE), which is located in the ProgramData directory: `C:\ProgramData\OptiTrack\MotiveProfile.motive`
* The MOTIVE files store software configurations as well as other software-wide settings.
* Profile files also loads trackable asset definitions.&#x20;
* Returns an eMotiveAPIResult integer value. If the project file was successfully loaded, it returns 0 (kApiResult\_Success).

**Function Input**

Filename (const char, const wchar\_t)

**Function Output**

eMotiveAPIResult

### TT\_SaveProfile, TT\_SaveProfileW

Saves current application setting into a Profile XML file.

**Description**

* This function saves the current configuration into an application Profile XML file.
* Attach \*.xml extension at the end of the filename.
* Returns an eMotiveAPIResult integer value. If the profile XML file was saved successfully, it returns 0 (kApiResult\_Success).

**Function Input**

Filename (const char, const wchar\_t)

**Function Output**

eMotiveAPIResult

### TT\_LoadCalibrationFromMemory

Loads calibration from memory.

**Description**

* This function loads camera calibration from memory. In order to do this, the program must have saved calibration memory.
* It assumes the pointer argument (unsigned char\*) points to a memory block where calibration data is already stored. The address and size of the calibration buffer must be determined by the developer using the API.

**Function Input**

* Buffer (unsigned char\*)
* Size of the buffer (int)

**Function Output**

* eMotiveAPIResult

### TT\_CameraExtrinsicsCalibrationFromMemory

Gets camera extrinsics from a calibration file in memory.

**Description**

* This allows for acquiring camera extrinsics for cameras not connected to system.
* It simply returns the list of details for all cameras contained in the calibration file.

**Function Input**

* Buffer (unsigned char\*)
* Size of the buffer (int)
* Result

**Function Output**

* eMotiveAPIResult

## Calibration

### TT\_StartCalibrationWanding

Start a new calibration wanding for all cameras.

**Description**

* This will cancel any existing calibration process.

**Function Input**

* None

**Function Output**

* eMotiveAPIResult

### TT\_CalibrationState

Returns the current calibration state.

**Description**

* Returns the current calibration state.

**Function Input**

* None

**Function Output**

* eMotiveAPIResult

### TT\_CalibrationCamerasLackingSamples

During calibration wanding, this will return a vector of camera indices that are lacking the minimum number of calibration samples to begin calculation.

**Description**

* When the returned vector for this method goes to zero size, you can call TT\_StartCalibrationCalculation() to begin calibration calculations.
* Wanding samples will continue to be collected until TT\_StartCalibrationCalculation() is called.

**Function Input**

* None

**Function Output**

* Vector (int)

### TT\_CameraCalibrationSamples

During calibration wanding.

**Description**

* This will return the number of wand samples collected for the given camera.
* Return 0 otherwise.

**Function Input**

* Camera index (int)

**Function Output**

* Number of samples (int)

### TT\_CancelCalibration

Cancels wanding or calculation and resets calibration engine.

**Description**

* Cancels wanding or calculation
* Resets calibration engine

**Function Input**

* none

**Function Output**

* Exits either TT\_StartCalibrationWanding() or TT\_StartCalibratoinCalculation()

### TT\_StartCalibrationCalculation

Once wanding is complete, call this to begin the calibration calculations.

**Description**

* Starts calibration calculations after wanding.

**Function Input**

* Boolean value

**Function Output**

* Starts calculation

### TT\_CurrentCalibrationQuality

During calibration calculation.

**Description**

* This method will return the current calibration quality in the range \[0-3], with 3 being best.
* Returns zero otherwise

**Function Input**

* none

**Function Output**

* Quality on scale of 0-3 (int)

### TT\_ApplyCalibrationCalculation

Run once TT\_CalibrationState() returns "Complete".

**Description**

* Call this method to apply the calibration results to all cameras.

**Function Input**

* none

**Function Output**

* Apply calibration results

### TT\_SetGroundPlane

Set the ground plane using a standard or custom ground plane template.

**Description**

* If true then this function will use a custom ground plane.

**Function Input**

* Boolean value of useCustomGroundPlane

**Function Output**

* Either applies custom or preset ground plane to calibration.

### TT\_TranslateGroundPlane

Translate the existing ground plane (in mm).

**Description**

* Takes float variables to alter existing ground plane.

**Function Input**

* X, Y, and Z values (float)

**Function Output**

* Applies new values to existing ground plane.

## Data Streaming

### TT\_StreamNP

Enables/disables the NatNet streaming of the Natural Point tracking data.

**Description**

* This function enables/disables NaturalPoint data stream.
* This is equivalent to the Broadcase Frame Data in the Data Streaming panel in Motive.
* Returns an eMotiveAPIResult integer value. If the operation was successful, it returns 0 (kApiResult\_Success).

**Function Input**

* Boolean argument enabled (true) / disabled (false)

**Function Output**

* eMotiveAPIResult

### TT\_StreamTrackd

Enables/disables streaming frame data into trackd.

**Description**

* This function enables/disables streaming data into trackd.
* Returns an eMotiveAPIResult integer value. If the operation was successful, it returns 0 (kApiResult\_Success).

**Function Input**

* True for enabling and false for disabling (bool)

**Function Output**

* eMotiveAPIResult

### TT\_StreamVRPN

Enables/disables data stream into [VRPN](https://github.com/vrpn/vrpn/wiki).

**Description**

* This function enables/disables data streaming into VRPN.
* To stream onto VRPN, the port address must be specified. VRPN server applications run through 3883 port, which is default port for the VRPN streaming.
* Returns an eMotiveAPIResult integer value. If streaming was successfully enabled, or disabled, it returns 0 (kApiResult\_Success).

**Function Input**

* True for enabling and false for disabling (bool)
* Streaming port address (int)

**Function Output**

* eMotiveAPIResult

### 3D Frame Data

### TT\_FrameMarkerCount

Gets total number of reconstructed markers in a frame.

**Description**

* This function returns a total number of reconstructed 3D markers detected in current capture frame.
* Use this function to count a total number of markers, access every markers, and obtain the marker index values.

**Function Input**

* None

**Function Output**

* Total number of reconstructed markers in the frame (int)

### TT\_FrameMarkerX

Returns x-position of a reconstructed marker.

**Description**

* This function returns X coordinate of a reconstructed 3D marker in respect to the global coordinate system, in meters.
* It requires a marker index value.

**Function Input**

* Marker index (int)

**Function Output**

* X-position of the 3D marker (float)

### TT\_FrameMarkerY

Returns y-position of a reconstructed marker.

**Description**

* This function returns Y coordinate of a reconstructed 3D marker in respect to the global coordinate system, in meters.
* It requires a marker index value.

**Function Input**

* Marker index (int)

**Function Output**

* Y-position of the 3D marker (float)

### TT\_FrameMarkerZ

Returns z-position of a reconstructed marker.

**Description**

* This function returns Z coordinate of a reconstructed 3D marker in respect to the global coordinate system, in meters.
* It requires a marker index value.

**Function Input**

* Marker index (int)

**Function Output**

* Z-position of the 3D marker (float)

### TT\_FrameMarkerResidual

Returns residual value of a marker.

**Description**

* This function returns a residual value for a given marker indicated by the marker index.
* Unit of the returned value is in millimeters.
* The marker index value may change between frames, but the unique identifier will always remain the same.

**Function Input**

* Marker index (int)

**Function Output**

* Residual value (float)

### TT\_FrameMarkerLabel

Returns a unique identifier of a marker.

**Description**

* This function returns a unique identifier (cUID) for a given marker.
* Markers have an index from 0 to \[totalMarkers -1] for a given frame. In order to access unique identifier of any marker, it's index must be inputted.
* The marker index value may change between frames, but the unique identifier will always remain the same.

**Function Input**

* Marker index (int)

**Function Output**

* Marker label (cUID)

### TT\_FrameTimeStamp

Returns a timestamp value for the current frame.

**Description**

* This function returns a timestamp value of the current frame.

**Function Input**

* None

**Function Output**

* Frame timestamp (double)

### TT\_FrameCameraCentroid

Checks whether a camera is contributing to reconstruction of a 3D marker, and saves corresponding 2D location as detected in the camera's view.

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

### TT\_FlushCameraQueues

Flushes out the camera queues.

**Description**

* This function flushes camera queues.
* In an event when you are tracking a very high number (hundreds) of markers and the application has accumulated data processing latency, you can call TT\_FlushCameraQueues() to refresh the camera queue before calling TT\_Update() for processing the frame. After calling this function, avoid calling it again until the TT\_Update() function is called and kApiResult\_Success is returned.

**Function Input**

* None

**Function Output**

* Void

## Rigid Bodies

### TT\_IsRigidBodyTracked

Checks whether Rigid Body is tracked or not.

**Description**

* Checks whether the Rigid Body is being tracked in the current frame.
* Returns true if the Rigid Body is tracked.

**Function Input**

* Rigid body index (int)

**Function Output**

* True / False (bool)

### TT\_RigidBodyLocation

Obtains and saves 3D position, quaternion orientation, and Euler orientation of a Rigid Body

**Description**

* This function saves position and orientation of a Rigid Body. Specifically, position and orientation at the Rigid Body pivot point is obtained.
* 3D coordinates of the Rigid Body will be assigned in declared variable addresses (\*x, \*y, \*z).
* Orientation of the Rigid Body will be saved in two different formats; Euler and quaternion rotations. Yaw, pitch, and roll values for Euler representation will be saved in the declared variable addresses (\*yaw, \*pitch, \*roll), and qx, qy, qz, and qw values for the quaternion rotation will be saved in declared variable addresses (\*qx, \*qy, \*qz, and \*qw).

**Function Input**

* Rigid body index (int)
* Declared variable (float) addresses for:
  * 3D coordinates (x,y,z)
  * Quaternion Rotation (qx, qy, qz, qw)
  * Euler Rotation ( yaw, pitch, roll)

**Function Output**

* Void

### TT\_ClearRigidBodyList

Clears and removes all Rigid Body assets.

**Description**

* This function clears all of existing Rigid Body assets in the project.

**Function Input**

* None

**Function Output**

* Void

### TT\_RemoveRigidBody

Removes a Rigid Body from the project

**Description**

* This function removes a single Rigid Body from a project.
* Returns an eMotiveAPIResult integer value. If the operation was successful, it returns 0 (kApiResult\_Success).

**Function Input**

* Rigid body index (int)

**Function Output**

* eMotiveAPIResult

### TT\_RigidBodyCount

Returns a total number of Rigid Bodies.

**Description**

* This function returns a total count of Rigid Bodies involved in the project.
* This can be used within a loop to set required number iterations and access each of the Rigid Bodies.

**Function Input**

* None

**Function Output**

* Total Rigid Body count (int)

### TT\_RigidBodyUserData

Returns the User Data ID value of a Rigid Body.

**Description**

* This function returns the User Data ID number of a Rigid Body.
* User ID is a user definable ID for the Rigid Body. When working with capture data in external pipelines, this value can be used to address specific Rigid Bodies in the scene.

**Function Input**

* Rigid body index (int)

**Function Output**

* User Data ID (int)

### TT\_SetRigidBodyUserData

Assigns a User Data ID number to a Rigid Body.

**Description**

* Assigns a User Data ID number to a Rigid Body.
* The User Data ID numbers can be used to point to particular assets when processing the data in external applications.

**Function Input**

* Rigid body index (int)
* Desired User Data ID (int)

**Function Output**

* Void

### TT\_RigidBodyMeanError

Returns a mean error of the Rigid Body tracking data.

**Description**

* Returns a mean error value of the respective Rigid Body data for the current frame.

**Function Input**

* Rigid body index (int)

**Function Output**

* Mean error (meters)

### TT\_RigidBodyName, TT\_RigidBodyNameW

Returns the name for the Rigid Body.

**Description**

* These functions are used to obtain name of a Rigid Body.
* Returns the assigned name of the Rigid Body.

**Function Input**

* Rigid body index (int)

**Function Output**

* Rigid body name (const char\*, const w\_chart\*)

### TT\_SetRigidBodyEnabled

Enables/disables tracking of a Rigid Body.

**Description**

* This function enables, or disables, tracking of the selected Rigid Body.
* All Rigid Bodies are enabled by default. Disabled Rigid Bodies will not be tracked, and no data will be received from it.

**Function Input**

* Rigid body index (int)
* Tracking status (bool)

**Function Output**

* Void

### TT\_RigidBodyEnabled

Checks whether a Rigid Body is enabled.

**Description**

* This function checks whether tracking of the Rigid Body is enabled or not.
* The function returns true is the tracking is enabled.

**Function Input**

* Rigid body index (int)

**Function Output**

* True / False (bool)

### TT\_RigidBodyTranslatePivot

Translates the pivot point of a Rigid Body.

**Description**

* This function translates a Rigid Body.
* 3D position of a Rigid Body will be displaced in x/y/z directions by inputted amount (meters).
* Translation is applied in respect to the local Rigid Body coordinate axis, not the global axis.
* Returns an eMotiveAPIResult integer value. If the operation was successful, it returns 0 (kApiResult\_Success).

**Function Input**

* Rigid body index (int)
* Translation along x-axis, in meters. (float)
* Translation along y-axis, in meters. (float)
* Translation along z-axis, in meters. (float)

**Function Output**

* eMotiveAPIResult

### TT\_RigidBodyResetOrientation

Resets orientation of a Rigid Body.

**Description**

* This function resets orientation of the Rigid Body and re-aligns its orientation axis with the global coordinate system.
* _Additional Note:_ When creating a Rigid Body, its zero orientation is set by aligning its axis with the global axis at the moment of creation. Calling this function essentially does the same thing on an existing Rigid Body asset.
* Returns true if the Rigid Body orientation was reset.

**Function Input**

* Rigid body index (int)

**Function Input**

* True / False (bool)

### TT\_RigidBodyMarkerCount

Gets total number of markers in a Rigid Body.

**Description**

* This function returns total number of markers involved in a Rigid Body.

**Function Input**

* Rigid body index (int)

**Function Output**

* Total number of marker in the Rigid Body (int)

### TT\_RigidBodyMarker

Saves 3D coordinates of a solved Rigid Body marker in respect to respective Rigid Body's local space.

**Description**

* This function gets 3D position of a solved Rigid Body marker and saves them in designated addresses. Rigid body marker positions from this function represents solved (or expected) location of the Rigid Body markers. For actual reconstructed marker positions, use the TT\_RigidBodyPointCloudMarker function.
* Note that the 3D coordinates obtained by this function is represented in respect to Rigid Body's local coordinate axis. For obtaining 3D coordinate in respect to global coordinates, use TT\_RigidBodyPointCloudMarker function.

**Function Input**

* Rigid body index (int)
* Marker index (int)
* Three declared variable addresses for saving x, y, z coordinates of the marker (float)

**Function Output**

* Void

### TT\_RigidBodyUpdateMarker

Changes and updates the Rigid Body marker positions.

**Description**

* This function is used to change the expected positions of a single Rigid Body marker.
* Rigid body markers are expected marker positions. Read about marker types in Motive.

**Function Input**

* Rigid body index (int)
* Marker index (int)
* New x-position of the Rigid Body marker in respect to the local coordinate system.
* New y-position of the Rigid Body marker in respect to the local coordinate system.
* New z-position of the Rigid Body marker in respect to the local coordinate system.

**Function Output**

* Returns true if marker locations have been successfully updated.

### TT\_RigidBodyPointCloudMarker

Saves 3D coordinates of a Rigid Body marker in respect to the global space.

**Description**

* This function saves 3D coordinates of each Rigid Body marker in designated addresses.
* 3D coordinates are saved in respect to global coordinate system.

**Function Input**

* Rigid body index (int)
* Marker index (int)
* Tracked status, True or False (bool)
* Three declared variable addresses for saving x, y, z coordinates of the marker (float).

**Function Output**

* Void

### TT\_RigidBodyPlacedMarker

Saves 3D coordinates of a Rigid Body solved marker positions in respect to the global space. Unlike TT\_RigidBodyPointCloudMarker function, it does not report point cloud solved positions, but it reports the expected marker positions in respect to Rigid Body position and orientation.

**Description**

* This function saves 3D coordinates of each expected Rigid Body marker positions in designated variable addresses.
* 3D coordinates are saved in respect to global coordinate system.

**Function Input**

* Rigid body index (int)
* Marker index (int)
* Tracked status, True or False (bool)
* Three declared variable addresses for saving x, y, z coordinates of the marker (float).

**Function Output**

* Void

### TT\_RigidBodyID

This function is used for obtaining unique identifiers for a specific Rigid Body indicated by the Rigid Body index number.

**Function Input**

* Rigid body index (int)

**Function Output**

* Rigid body unique ID (Core::cUID)

### TT\_CreateRigidBody

Creates a Rigid Body asset from a set of reconstructed 3D markers.

**Description**

* This functions creates a Rigid Body from the marker list and marker count provided in its argument.
* The marker list is expected to contain a list of marker coordinates in the following order: (x1, y1, z1, x2, y2, z2, …, xN, yN, zN). The x/y/z coordinates must be in respect to the Rigid Body pivot point, in meters.
* Inputted 3D locations are taken as Rigid Body marker positions about the Rigid Body pivot point. If you are using TT\_FrameMarkerX/Y/Z functions to obtain the marker coordinates, you will need to subtract the pivot point location from the global marker locations when creating a Rigid Body. If this is not done, created Rigid Body will have its pivot point at the global origin.
* Returns an eMotiveAPIResult integer value. If the Rigid Body was successfully created, it returns 0 or kApiResult\_Success.

**Function Input**

* Rigid body name (char)
* User Data ID (int)
* Marker Count (int)
* Marker list (float list)

**Function Output**

* eMotiveAPIResult

### TT\_RigidBodySettings

Obtains Rigid Body settings for a given asset, and saves them in a cRigidBodySettings instance.

**Description**

* This function obtains Rigid Body settings for a given Rigid Body asset and saves them into a declared cRigidBodySetting instance address.
* Rigid body settings are saved into an instance of the cRigidBodySettings class.
* For detailed information on member function and variables in the cRigidBodySettings class, refer to its declaration in the MotiveAPI.h header file.
* Returns an eMotiveAPIResult integer value.

**Function Input**

* Rigid body index (int)
* declared instance address (cRigidBodySettings)

**Function Output**

* eMotiveAPIResult

### TT\_SetRigidBodySettings

Changes property settings of a Rigid Body.

**Description**

* This function assigns a set of Rigid Body settings to a Rigid Body asset.
* An instance of cRigidBodySettings will be attached to the provided Rigid Body.
* Returns an eMotiveAPIResult integer value. If the marker was successfully created, it returns 0 (kApiResult\_Success).

**Function Input**

* Rigid body index (int)

**Function Output**

* eMotiveAPIResult

### TT\_RigidBodyRefineStart

Initiates the Rigid Body refinement process. Input the number of samples and the ID of the Rigid Body you wish to refine. After starting the process, TT\_RigidBodyRefineSample bust be called on everyframe in order to collect samples.

**Description**

* This function is used to start Rigid Body refinement.

**Function Input**

* Target Rigid Body ID
* Sample count (int)

**Function Output**

* Returns true if the refinement process has successfully initiated.

### TT\_RigidBodyRefineSample

This function collects samples for Rigid Body refinement by calling the TT\_RigidBodyRefineStart function. Call this function for every frame within the update loop. You can check the progress of calibration by calling the TT\_RigidBodyRefineProgress function.

**Description**

* This function collects sample Rigid Body tracking data for refining the definition of corresponding Rigid Body.

**Function Input**

* None. Samples frames for the initialized refine process.

**Function Output**

* Returns true if the refinement process has successfully collected a sample. This function does not collect samples if Rigid Body is not tracked on the frame.

### TT\_RigidBodyRefineState

This function inquiries the state of the refinement process. It returns TT\_RigidBodyRefineStates enum as a result.

**Description**

* This function queries the state of the Rigid Body refinement process. It returns an enum value for indicating whether the process is initialized, sampling, solving, complete, or uninitialized.

**Function Input**

* None. Checks the state on the ongoing refinement process.

**Function Output**

* Returns TT\_RigidBodyRefineStates enum value.

### TT\_RigidBodyRefineProgress

This function inquiries the progress of the refinement sampling process.

**Description**

* When the refinement process is under the _sampling_ state, calling this function returns the sampling progress. It will return a percentage value representing the sampling progress in respect to the total number of samples given in the TT\_RigidBodyRefineStart parameter.

**Function Input**

* None. Checks the progress on the ongoing refinement process.

**Function Output**

* Returns percentage completeness of the sampling process (float).

### TT\_RigidBodyRefineInitialError / TT\_RigidBodyRefineResultError

These two functions returns error values of the Rigid Body definition before and after the refinement.

**Description**

* Once the refinement process has reached _complete_ stage, these two functions can be called to compare the error values from corresponding Rigid Body definition before and after the refinement.

**Function Input**

* None.

**Function Output**

* Average error value of the target Rigid Body definition prior (TT\_RigidBodyRefineInitialError) and after (TT\_RigidBodyRefineResultError) the refinement.

### TT\_RigidBodyRefineApplyResult

This function applies the refined result to the corresponding Rigid Body definition.

**Description**

* This function applies the refined Rigid Body definition. After comparing the error values before and after the refinement using _TT\_RigidBodyRefineInitialError_ and _TT\_RigidBodyRefineResultError_ functions, use this function to apply if the results are satisfying.

**Function Input**

* None.

**Function Output**

* Returns true if the refined results have been successfully applied.

### TT\_RigidBodyRefineReset

This function discards the final refinement result and resets the refinement process.

**Description**

* If the final refinement result from the TT\_RigidBodyRefineResultError call is not satisfying, you can call this function to discard the result and start over from the sampling process again.

**Function Input**

* None.

**Function Output**

* Returns true if the refined results have been successfully reset.

## Camera Group

### TT\_GetCameraManager

Returns pointer to the CameraManager instance.

**Description**

* This function returns a pointer to the **CameraManager** instance from the Camera SDK.
* Camera SDK must be installed to use this function.
* The version number of Motive and the Camera SDK must match.
* Corresponding headers and libraries must be included in the program.

**Function Input**

* None

**Function Output**

* Pointer to the CameraManager instance (CameraLibrary::CameraManager\*)

### TT\_BuildNumber

Returns Motive build number.

**Description**

* This function returns corresponding Motive build number.

**Function Input**

* None

**Function Output**

* Build number (int)

### TT\_CameraGroupCount

Returns camera group count.

**Description**

* This function returns total count of camera groups that are involved in the project.

**Function Input**

* None

**Function Output**

* Camera group count (int)

### TT\_CreateCameraGroup

Creates a new camera group.

**Description**

* This function adds an additional camera group (empty) to a project.
* **Note:** Creating an additional camera group is unnecessary for most applications. Most common case is to group cameras to set them as a reference group for recording grayscale videos.

**Function Input**

* None

**Function Output**

* True/False (bool)

### TT\_RemoveCameraGroup

Removes a camera group.

**Description**

* This function removes a camera group, specified by its index number.
* The camera group must contain no cameras in order to be removed.
* Returns true if the group was successfully removed.

**Function Input**

* Camera group index (int)

**Function Output**

* True/False (bool)

### TT\_CamerasGroup

Returns an index value of a camera group that a camera is involved in.

**Description**

* This function takes an index value of a camera and returns corresponding camera group index which the camera is involved in.

**Function Input**

* Camera index (int)

**Function Output**

* Camera group index (int)

### TT\_SetGroupShutterDelay

Introduces shutter delay to a camera group.

**Description**

* This function sets a shutter delay (in microseconds) to a camera group, which is designated by its index number.
* After assigning the delay, all of the cameras involved in the camera group will shutter at a delayed timing when recording.

**Function Input**

* Camera group index (int)
* Delay in microseconds (int)

**Function Output**

* Void

### TT\_SetCameraGroup

Moves a camera to a different camera group.

**Description**

* This function assigns/moves a camera to a different camera group

**Function Input**

* Camera index (int)
* Camera group index (int)

**Function Output**

* Void

### TT\_CameraGroupFilterSettings

Obtains the camera group's filter settings.

**Description**

* This function fetches configured 2D filter settings from a camera group and saves the settings in the declared cCameraGroupFilterSettings instance.
* Returns an eMotiveAPIResult integer value. When the function successfully assigns the filter settings, it returns 0 (or kApiResult\_Success).

**Function Input**

* Camera group index (int)
* Group filter settings instance (cCameraGroupFilterSettings)

**Function Output**

* eMotiveAPIResult

### TT\_SetCameraGroupFilterSettings

Assigns camera group filter settings to a camera group.

**Description**

* This function assigns inputted filter settings (cCameraGroupFilterSettings) instance to a camera group designated by its index number.
* Returns an eMotiveAPIResult integer value. When the function successfully assigns the filter settings, it returns 0 (or kApiResult\_Success).

**Function Input**

* Camera group index (int)
* Filter settings instance (cCameraGroupFilterSettings)

**Function Output**

* eMotiveAPIResult

### TT\_CameraGroupPointCloudSettings / TT\_SetCameraGroupPointCloudSettings

### TT\_CameraGroupMarkerSize

Obtains marker size settings of a camera group

**Description**

* This function fetches currently configured marker size settings from a camera group, and saves them onto a declared cCameraGroupMarkerSizeSettings class instance.
* The marker size settings determine display properties of the 3D markers reconstructed from a specific group of cameras.
* Returns an eMotiveAPIResult integer value. When the function successfully obtains the settings, it returns 0 (or kApiResult\_Success).

**Function Input**

* Camera group index (int)
* Marker size settings (cCameraGroupMarkerSizeSettings)

**Function Output**

* eMotiveAPIResult

### TT\_SetCameraGroupMarkerSize

Applies given marker size settings to a camera group.

**Description**

* This function applies an instance cCameraGroupMarkerSizeSettings to a camera group.
* The marker size settings determine display properties of 3D markers reconstructed from a specific group of cameras.
* Marker sizes are represented by corresponding diameter in millimeters.
* Returns an eMotiveAPIResult integer value. When the function successfully applies the settings, it returns 0 (or kApiResult\_Success).

**Function Input**

* Camera group index (int)
* Marker size settings (cCameraGroupMarkerSizeSettings)

**Function Output**

* eMotiveAPIResult

### TT\_SetCameraGroupReconstruction

Enables or disables marker reconstruction contribution from a camera group.

**Description**

* Enables or disables marker reconstruction contribution from a camera group.
* Input TRUE for enable argument in order to allow the camera group to reconstruct markers.
* Returns an eMotiveAPIResult integer value. When the function successfully enables/disables the reconstruction, it returns 0 (or kApiResult\_Success).

**Function Input**

* Camera group index (int)
* Boolean argument for enabling (true) and disabling (false) the mode.

**Function Output**

* eMotiveAPIResult

### TT\_SetEnabledFilterSwitch

Enables or disables filter switchers.

**Description**

* This function enables or disables filter switches for all of the connected cameras.
* Returns an eMotiveAPIResult integer value. When the function successfully changes the setting, it returns 0 (or kApiResult\_Success).

**Function Input**

* Boolean argument for enabling (true) or disabling (false) the filter.

**Function Output**

* eMotiveAPIResult

### TT\_IsFilterSwitchEnabled

Checks whether filter switches are enabled or not.

**Description**

* This function checks whether filter switch is enabled in all of the cameras,
* It returns true if the switches are enabled.

**Function Input**

* Void

**Function Output**

* Enabled/disabled (bool)

## Camera

### TT\_CameraCount

Returns a total number of cameras connected to the system.

**Description**

* This function returns a total camera count.

**Function Input**

* None

**Function Output**

* Total number of cameras (int)

### TT\_CameraXLocation

Returns x-position of a camera.

**Description**

* This function returns camera's X position in respect to the global coordinate system

**Function Input**

* Camera index (int)

**Function Output**

* Camera's X position. Measured in meters with reference to global coordinate system. (float)

### TT\_CameraYLocation

Returns y-position of a camera.

**Description**

* This function returns camera's Y position in respect to the global coordinate system

**Function Input**

* Camera index (int)

**Function Output**

* Camera Y-position. Measured in meters with reference to global coordinate system. (float)

### TT\_CameraZLocation

Returns z-position of a camera.

**Description**

* This function returns camera's Z position in respect to the global coordinate system

**Function Input**

* Camera index (int)

**Function Output**

* Camera's Z position. Measured in meters with reference to global coordinate system. (float)

### TT\_CameraOrientationMatrix

Gets a components of the camera's orientation matrix.

Sample output from a program displaying the rotation matrix.

**Description**

* This function returns a single constant from camera's orientation matrix in respect to the global coordinate axis.
* The camera index input (int) determines which camera to obtain the matrix from.
* The matrix index determines which component of the rotation matrix to return.

**Function Input**

* Camera index (int)
* Matrix index (int)

**Function Output**

* Single component of the rotation matrix (float)

### TT\_CameraName

Returns corresponding camera's model name and serial number

**Description**

* This function returns corresponding camera's name and serial number.

**Function Input**

* Camera index (int)

**Function Output**

* Camera name and serial number (const char)

### TT\_CameraSerial

Returns corresponding camera's serial number as an integer.

**Description**

* This function returns corresponding camera's serial number.

**Function Input**

* Camera index (int)

**Function Output**

* Camera serial number (int)

### TT\_CameraMarkerCount

Returns a total number of centroids detected by a camera.

**Description**

* This function returns a total number of _centroids_ detected by a camera.
* A centroid is defined for every group of contiguous pixels that forms a shape that encloses the thresholded pixels.
* Size and roundness filter (cCameraGroupFilterSettings) is not applied in this data.

**Function Input**

* Camera index (int)

**Function Output**

* Number of centroids (int)

### TT\_CameraMarker

Returns 2D location of the centroid as seen by a camera.

**Description**

* This function saves 2D location of the centroid as detected by a camera's imager.
* Returns true if the function successfully saves the x and y locations.

**Function Input**

* Camera index (int)
* Centroid index (int)
* Declared variables for saving x and y (float)

**Function Output**

* True/False (bool)

### TT\_CameraPixelResolution

Saves camera's pixel resolution.

**Description**

* This function saves camera's pixel resolutions (width x height) into declared integer variables.
* Returns true when successfully saving the values.

**Function Input**

* Camera index (int)
* Declared integer variable for saving width (int)
* Declared integer variable for saving height (int)

**Function Output**

* True/False (bool)

### TT\_CameraMarkerPredistorted

Saves predistorted 2D location of a centroid.

**Description**

* This function saves predistorted 2D location of a centroid.
* This data is basically where the camera would see a marker if there were no effects from lens distortions. For most of our cameras/lenses, this location is only a few pixels different from the distorted position obtained by the [TT\_CameraMarker](https://github.com/OptiTrack/GitBook-Wiki/blob/main/developer-tools/motive-api/broken-reference/README.md) function.
* Returns true when successfully saving the values.

**Function Input**

* Camera index (int)
* Marker (centroid) index (int)
* Declared variable for saving x location (float)
* Declared variable for saving y location (float)

**Function Output**

* True/False (bool)

### TT\_SetCameraSettings

Configures camera settings.

**Description**

* This function sets camera settings for a camera device specified by its index number.
* Input setting parameters must agree with the supported ranges (or video types) of the camera model.
* A negative return value indicates the function did not complete the task.
* Each of the video types is indicated with the following integers. Supported video types may vary for different camera models. Please check the Data Recording page for more information on which image processing modes are available in different models.
* Segment Mode: 0
* Raw Grayscale Mode: 1
* Object Mode: 2
* Precision Mode: 4
* MJPEG Mode: 6
* Valid exposure ranges depend on the framerate settings:
* Prime series and Flex 13: 1 \~ maximum time gap between the frames, which is approximately (1 / framerate) - 200 microseconds with about 200 microseconds gap for protection.
* Flex3 and Duo/Trio tracking bars: 1 \~ 480 scanlines.
* Valid threshold ranges: 0 - 255
* Valid intensity ranges: 0 - 15

**Function Input**

* Camera index (int)
* Video type (int)
* Camera exposure (int)
* Pixel threshold (int)
* IR light intensity (int)
* For more information on the camera settings, refer to the Devices pane page.

**Function Output**

* True/False (bool)

### TT\_SetCameraFrameRate

Sets camera frame rate.

**Description**

* This function sets the frame rate of a camera.
* Returns true if it successfully adjusts the settings.
* Note that this function may assign a frame rate setting that is out of the supported range. Check to make sure inputted frame rates are supported.

**Function Input**

* Camera index (int)
* Frame rate (int)

**Function Output**

* True/False (bool).

### TT\_CameraFrameRate

Gets configured frame rate of a camera.

**Description**

* This function returns frame rate of a camera.

**Function Input**

* Camera index (int)

**Function Output**

* Camera frame rate (int)

### TT\_CameraVideoType

Gets configured video type of a camera.

**Description**

* This function checks and returns configured video type (image processing mode) of a camera.
* It returns an integer value which represents a video type.

**Function Input**

* Camera index (int)

**Function Output**

* Video type (int)

### TT\_CameraExposure

Gets exposure setting of a camera.

**Description**

* This function returns exposure setting of a camera.
* Exposure values are measured in microseconds in Prime series and Flex 13 camera models, and they are measured in scanlines for the Duo/Trio tracking bars and Flex 3 cameras.
* To change exposure setting, use the [TT\_SetCameraSettings](https://github.com/OptiTrack/GitBook-Wiki/blob/main/developer-tools/motive-api/broken-reference/README.md) function.
* For more information on camera settings in Motive, read through the Devices pane page.

**Function Input**

* Camera index (int)

**Function Output**

* Camera exposure (int)

### TT\_CameraThreshold

Gets configured threshold (THR) setting of a camera.

**Description**

* This function returns pixel brightness threshold setting of a camera.
* When processing the frames, pixels with brightness higher than the configured threshold will be processed, and pixels with lower brightness will be discarded.
* To change the threshold setting, use the [TT\_SetCameraSettings](motive-api-function-reference.md#tt_setcamerasettings) function.
* For more information on camera settings in Motive, read through the Devices pane page.
* Valid range: 1 - 255.

**Function Input**

* Camera index (int)

**Function Output**

* Pixel brightness threshold (int)

### TT\_CameraIntensity

Gets configured intensity (LED) setting of a camera.

**Description**

* This function returns configured IR illumination intensity setting of a camera.
* To change the intensity setting, use the [TT\_SetCameraSettings](motive-api-function-reference.md#tt_setcamerasettings) function.
* For more information on camera settings in Motive, read through the Devices pane page.
* Valid range: 1 - 15.

**Function Input**

* Camera index (int)

**Function Output**

* Camera IR intensity (int)

### TT\_CameraTemperature

Measures image board temperature of a camera.

**Description**

* This function returns temperature (in Celsius) of a camera's image board.
* Temperature sensors are featured only in Prime series camera models.

**Function Input**

* Camera index (int)

**Function Output**

* Image board temperature (float)

### TT\_CameraRinglightTemperature

Measures IR LED board temperature of a camera.

**Description**

* This function returns temperature (in Celsius) of a camera's IR LED board.
* Temperature sensors are featured only in Prime series camera models.

**Function Input**

* Camera index (int)

**Function Output**

* IR LED board temperature (float)

### TT\_CameraGrayscaleDecimation

Gets configured grayscale image frame rate decimation ratio of a camera.

**Description**

* This feature is available only in Flex 3 and Trio/Duo tracking bars, and it has been deprecated for other camera models.
* This function returns grayscale frame rate decimation ratio of a camera.
* Valid decimation ratios are 0, 2, 4, 8. (e.g. When the decimation setting is set to 4, a camera will capture one grayscale frame for four frames of the tracking data)
* To set the decimation ratio, use the [TT\_SetCameraGrayscaleDecimation](https://github.com/OptiTrack/GitBook-Wiki/blob/main/developer-tools/motive-api/broken-reference/README.md) function.
* Grayscale images require more load on data processing. For this reason, you may want to decimate the grayscale frame images and capture the frames at a lower frame rate.

**Function Input**

* Camera index (int)

**Function Output**

* Decimation ratio (int)

### TT\_SetCameraGrayscaleDecimation

Sets frame rate decimation ratio for processing grayscale images.

**Description**

* This feature is available only in Flex 3 and Trio/Duo tracking bars, and it has been deprecated for other camera models.
* This functions sets the frame decimation ratio for processing grayscale images in a camera.
* Depending on the decimation ratio, a fewer number of grayscale frames will be captured. This can be beneficial when reducing the processing loads.
* Supported decimation ratios: 0, 2, 4, 6, 8. (e.g. When the decimation setting is set to 4, a camera will capture one grayscale frame for 4 frames of the tracking data)
* Returns true when it successfully sets the decimation value

**Function Input**

* Camera index (int)
* Decimation value (int)

**Function Output**

* True/False (bool)

### TT\_SetCameraFilterSwitch

Enables or disables IR filter switch of a camera.

**Description**

* This function enables, or disables, integrated camera filter switch for detecting IR lights.
* Different camera models may have different filter switches. Refer to the camera model specifications for detailed information on the type and allowed wavelengths for the filter switch.
* Returns true when it successfully enables/disables the filter switch.

**Function Input**

* Camera index (int)
* A boolean argument for enabling (true) or disabling (false) the filter.

**Function Output**

* True/False (bool)

### TT\_SetCameraAGC

Enables and disables automatic gain control.

**Description**

* This function enables/disables automatic gain control (AGC).
* Automatic Gain Control feature adjusts the camera gain level automatically for best tracking.
* AGC is only available in Flex 3's and Duo/Trio tracking bars.
* Returns true when the operation was done successfully.

**Function Input**

* Camera index (int)
* Enabled (true) / disabled (false) status (bool)

**Function Output**

* True/False (bool)

### TT\_SetCameraAEC

Enables or disables automatic exposure control.

**Description**

* This function enables, or disables, Automatic Exposure Control (AEC) for featured camera models.
* This feature is only available in Flex 3 and Duo/Trio tracking bars.
* It allows cameras to automatically adjust its exposure setting by looking at the properties of the incoming frames.
* Returns true if the operation was successful.

**Function Input**

* Camera index (int)
* A boolean argument for enabling (true) or disabling (false) the filter.

**Function Output**

* True/false (bool)

### TT\_SetCameraHighPower

Enables or disables the high power IR illumination mode.

**Description**

* This function enables or disables, the high power mode for featured cameras.
* The high power mode allows brighter IR LED illumination using more power source.
* Returns true if the function successfully enables/disables the feature.

**Function Input**

* Camera index (int)
* A boolean argument for enabling (true) or disabling (false) the filter.

**Function Output**

* True/False (bool)

### TT\_SetCameraMJPEGHighQuality

Sets compression quality of MJPEG images.

**Description**

* This function sets the quality of MJPEG images captured by a camera. More specifically, it changes the compression quality of MJPEG frames.
* Compression quality is indicated by an integer number between 0 - 100 (no loss).
* Lower MJPEG compression quality setting can reduce the processing load for the cameras and reduce latency, but doing so will result in low-quality images.
* Returns true when the function successfully enables or disables, the mode.

**Function Input**

* Camera index (int)
* MJPEG compression quality (int)

**Function Output**

* True/false (bool)

### TT\_CameraImagerGain

Gets configured imager gain setting of a camera.

**Description**

* This function is used to check the imager gain setting of a camera.
* It returns configured gain setting as an integer value.

**Function Input**

* Camera index (int)

**Function Output**

* Gain setting (int)

### TT\_CameraImagerGainLevels

Gets total number of gain levels available in a camera.

**Description**

* This function returns a total number of available gain levels in a camera.
* Different camera models may have different gain level settings. This function can be used to check the number of available gain levels.

**Function Input**

* Camera index (int)

**Function Output**

* Number of gain levels available (int)

### TT\_SetCameraImagerGain

Sets the imager gain level.

**Description**

* This function sets the gain level of a camera's imager.
* Using high gain levels may be beneficial for long range tracking. However, note that increasing gain levels may also result in amplified noise signal, which can result in false reconstructions.
* Check available gain levels for the camera model using the TT\_CameraImagerGainLevels function.

**Function Input**

* Camera index (int)

**Function Output**

* Void

### TT\_IsContinuousIRAvailable

Checks if the continuous IR mode is supported.

**Description**

* This function checks whether the continuous IR illumination mode is available in the camera model.
* In the continuous IR mode, the IR LEDs will not strobe but will illuminate continuously instead.
* Continuous IR modes are available only in the Flex 3 camera model and the Duo/Trio tracking bars.
* Returns true if continuous IR mode is available.

**Function Input**

* Camera index (int)

**Function Output**

* True / False (bool)

### TT\_ContinuousIR

Checks if the continuous IR mode is enabled.

**Description**

* This function checks if the continuous IR mode is enabled or disabled in a camera.
* Returns true if the continuous IR mode is already enabled.

**Function Input**

* Camera index (int)

**Function Output**

* True / False (bool)

### TT\_SetContinuousIR

Enables/disables continuous IR.

**Description**

* This function enables, or disables, continuous IR illumination in a camera.
* Continuous IR mode outputs less light when compared to Strobed (non-continuous) illumination, but this mode could be beneficial in situations where there are extraneous IR reflections in the volume.
* Use TT\_IsContinuousIRAvailable function to check whether if this mode is supported.

**Function Input**

* Camera index (int)
* A Boolean argument for enabling (true) or disabling (false)

**Function Output**

* Void

### TT\_ClearCameraMask

Clears masking from camera's 2D view.

**Description**

* This function clears existing masks from the 2D camera view.
* Returns true when it successfully removes pixel masks.

**Function Input**

* Camera index (int)

**Function Output**

* True / False (bool)

### TT\_SetCameraMask

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

### TT\_CameraMask

**Description**

* This function returns memory block of the mask.
* One bit per a pixel of the mask.
* Masking pixels are rasterized from left to right and from top to bottom of the camera's view.

**Function Input**

* Camera index (int)
* Buffer
* Buffer size

**Function Output**

* True / False (bool)

### TT\_CameraMaskInfo

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

### TT\_AutoMaskAllCameras

**Description**

* Auto-mask all cameras.
* This is additive to any existing masking.
* To clear masks on a camera, call TT\_ClearCameraMask prior to auto-masking.

**Function Input**

* none

**Function Output**

* Auto masks all cameras

### TT\_SetCameraState

Sets camera state of a camera.

**Description**

* This function configures camera state of a camera. Different camera states are defined in the **eCameraStates** enumeration.
* Returns true when it successfully sets the camera state.

**Function Input**

* Camera index (int)
* Camera state (eCameraStates)

**Function Output**

* True / False (bool)

### TT\_CameraState

Checks camera states.

| Enumerator                            | Value |
| ------------------------------------- | ----- |
| Camera\_Enabled                       | 0     |
| Camera\_Disabled\_For\_Reconstruction | 1     |
| Camera\_Disabled                      | 2     |
| CameraStatesCount                     | 3     |

**Description**

* This function obtains and saves the camera state of a camera onto the declared variables.
* Returns true if it successfully saves configured state.

**Function Input**

* Camera index (int)
* Declared variable for camera state (eCameraState)

**Function Output**

* True / False (bool)

### TT\_CameraID

Returns the Camera ID.

**Description**

* This function takes in a camera index number and returns the camera ID number.
* Camera ID numbers are the numbers that get displayed on the devices.
* The Camera ID number is different from the camera index number. On Prime camera systems, Camera IDs are assigned depending on where the cameras are positioned within the calibrated volume. On Flex camera systems, Camera IDs are assigned according to the order in which devices connected to the OptiHub(s).

**Function Input**

* Camera index (int)

**Function Output**

* Camera ID (int)

### TT\_CameraFrameBuffer

Fills a buffer with image from camera's view.

**Description**

* This function fetches raw pixels from a single frame of a camera and fills the provided memory block with the frame buffer.
* The resulting image depends on what video mode the camera is in. For example, if the camera is in grayscale mode, a grayscale image will be saved from this function call.
* For obtaining buffer pixel width and height, you can use [TT\_CameraPixelResolution](motive-api-function-reference.md#tt_camerapixelresolution) function to obtain respective camera resolution.
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

### TT\_CameraFrameBufferSaveAsBMP

Saves image buffer of a camera into a BMP file.

**Description**

* This function saves image frame buffer of a camera into a BMP file.
* Video type of the saved image depends on configured camera settings
* Attach \*.bmp at the end of the filename.
* Returns true if it successfully saves the file.

**Function Input**

* Camera index (int)
* Filename (const char\*)

**Function Output**

* True / False (bool)

### TT\_CameraBackproject

Obtains 2D position, of a 3D marker as seen by one of the cameras.

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

### TT\_CameraUndistort2DPoint

Removes lens distortion.

**Description**

* This function removes the effect of the lens distortion filter and obtains undistorted raw x and y coordinates (as seen by the camera) and saves in the declared variables.
* Lens distortion is measured during the camera calibration process.
* If you want to apply the lens distortion filter back again, you can use the [TT\_CameraDistort2DPoint](motive-api-function-reference.md#tt_cameradistort2dpoint).

**Function Input**

* Camera index (int)
* Declared variables for x and y position in respect to camera's view (float)

**Function Output**

* Void

### TT\_CameraDistort2DPoint

Reapplies lens distortion model.

**Description**

* This function restores the effect of default model for accommodating effects of the camera lens.
* Note all reported 2D coordinates are already distorted to accommodate for effects of the camera lens. Apply this function to coordinates that are _undistorted_ by using the TT\_CameraUndistort2DPoint function.
* This can be used to obtain raw data for 2D points that have been undistorted using the TT\_CameraUndistort2DPoint function.

**Function Input**

* Camera index (int)
* Declared variables for x and y position in respect to camera's view (float)

**Function Input**

* Void

### TT\_CameraRay

Obtains 3D vector from a camera to a 3D point.

**Description**

* This function takes in an undistorted 2D centroid location seen by a camera's imager and creates a 3D vector _ray_ connecting the point and the camera.
* Use [TT\_CameraUndistort2DPoint](motive-api-function-reference.md#tt_cameraundistort2dpoint) to undistort the 2D location before obtaining the 3D vector.
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

### TT\_CameraModel

Gets camera parameters for the OpenCV intrinsic model.

**Description**

* This function sets camera's extrinsic (position & orientation) and intrinsic (lens distortion) parameters with values compatible with the OpenCV intrinsic model.
* For retaining the extrinsic parameters, you can use the [TT\_CameraXLocation](motive-api-function-reference.md#tt_cameraxlocation), [TT\_CameraYLocation](motive-api-function-reference.md#tt_cameraylocation), [TT\_CameraZLocation](motive-api-function-reference.md#tt_camerazlocation), and [TT\_CameraOrientationMatrix](motive-api-function-reference.md#tt_cameraorientationmatrix) functions.
* Returns true if the operation was successful.

**Function Input**

* Camera index (int)
* Three arguments for camera x,y,z-position, in mm, within the global space (float)
* Camera orientation (float)
* Lens center location, principleX and principleY, in pixels (float)
* Lens focal length, in pixels. (float)
* Barrel distortion coefficients: kc1, kc2, kc3 (float)
* Tangential distortion (float)

**Function Output**

* True / False (bool)

### TT\_GetCamera

Gets pointer to the camera object from Camera SDK.

**Description**

* This function returns a pointer to the Camera SDK's camera pointer.
* While the API takes over the data path which prohibits fetching the frames directly from the camera, it is still very useful to be able to communicate with the camera directly for setting camera settings or attaching modules.
* The Camera SDK must be installed to use this function.
* Camera SDK libraries and the camera library header file (cameralibrary.h) must be included.
* Returns Camera SDK Camera.

**Function Input**

* Camera index (int)

**Function Output**

* Camera SDK camera pointer (CameraLibrary::Camera\*)

## Additional Features

### TT\_OrientTrackingBar

Changes position and orientation of the tracking bars.

**Description**

* This function makes changes to the position and orientation of the tracking bar within the global space.
* Note that this function will shift or rotate the entire global space, and the effects will be reflected in other tracking data as well.
* By default, center location and orientation of a Tracking bar (Duo/Trio) determines the origin of the global coordinate system. Using this function, you can set a Tracking Bar to be placed in a different location within the global space instead of origin.

**Function Input**

* X position (float)
* Y position (float)
* Z position (float)
* Quaternion orientation X (float)
* Quaternion orientation Y (float)
* Quaternion orientation Z (float)
* Quaternion orientation W (float)

**Function Output**

* eMotiveAPIResult

### TT\_AttachCameraModule / TT\_DetachCameraModule

Attaches/detaches cCameraModule instance to a camera object.

**Description**

* This function attaches/detaches the cCameraModule class to a camera defined by its index number.
* This function requires the project to be compiled against both the Motive API and the Camera SDK.
* The cCameraModule class is inherited from the Camera SDK, and this class is used to inspect raw 2D data from a camera. Use this function to attach the module to a camera. For more details on the cCameraModule class, refer to the _cameramodulebase.h_ header file from the Camera SDK.
* The Camera SDK must be installed.

**Function Input**

* Camera index (int)
* cCameraModule instance (CameraLibrary::cCameraModule)

**Function Output**

* Void

### TT\_AttachRigidBodySolutionTest / TT\_DetachRigidBodySolutionTest

Attaches/detaches cRigidBodySolutionTest class to a Rigid Body.

**Description**

* This function attaches/detaches the cRigidBodySolutionTest class onto a Rigid Body.
* Once an instance of cRigidBodySolutionTest to a Rigid Body, it will evaluate the Rigid Body solution and return false if the solution does not qualify the provided condition.
* The cRigidBodySolutionTest class uses the C++ inheritance design model. Inherit this class into your project with same function and class names, then attach the inherited class.

**Function Input**

* Rigid body index (int)
* Rigid body test module (cRigidBodySolutionTest\*)

**Function Output**

* Void

### TT\_AttachListener / TT\_DetachListener

Attaches/detaches cTTAPIListener onto a TTAPI project.

**Description**

* This function attaches/detaches a cTTAPIListener inherited class onto a TTAPI project.
* The cTTAPIListener class uses the C++ inheritance design model. Inherit this class into your project with the same function and class names, then attach the inherited class.
* This listener class includes useful callback functions that can be overrided. Including TTAPIFrameAvailable, TTAPICameraConnected, TTAPICameraDisconnected, InitialPointCloud, ApplyContinuousCalibrationResult.

**Function Input**

* cTTAPIListener

**Function Output**

* Void

### TT\_GetResultString

Returns plain text message that corresponds to an eMotiveAPIResult value.

**Description**

* Returns plain text message that corresponds to a result that an eMotiveAPIResult value indicates.

**Function Input**

* eMotiveAPIResult

**Function Output**

* Result text (const char)

### TT\_TestSoftwareMutex

Checks whether there is another OptiTrack software using the devices.

**Description**

* Checks whether there is another OptiTrack software using the devices. Only one software should be occupying the devices at a time.

**Function Input**

* None

**Function Output**

* eMotiveAPIResult
