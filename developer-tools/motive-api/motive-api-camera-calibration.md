# Motive API Camera Calibration

***

## Calibration Functions

***

The following functions are used to complete the calibration process using the Motive API, and are presented in the order in which they would be performed. For details on specific functions, please refer to the [Motive API: Function Reference](motive-api-function-reference.md) page.

### Masking

**Auto-Masking**

Auto-Masking is done directly using the [TT\_AutoMaskAllCameras](motive-api-function-reference.md#tt_automaskallcameras) function. When this function is called, Motive will sample for a short amount of time and apply a mask to the camera imagers where light was detected.

**Camera Mask**

The [TT\_CameraMask](motive-api-function-reference.md#tt_cameramask) function returns the memory block of the mask, with one bit per each pixel of the mask. Masking pixels are rasterized from left to right and from top to bottom of the camera's view.

**Clear Masks**

The [TT\_ClearCameraMask](motive-api-function-reference.md#tt_clearcameramask) function is used to clear existing masks from the 2D camera view. It returns true when it successfully removes pixel masks.&#x20;

{% hint style="info" %}
Masking is always additive through the API unless preceded by the _TT\_ClearCameraMask_ command.
{% endhint %}

**Set Camera Mask**

The [TT\_SetCameraMask](motive-api-function-reference.md#tt_setcameramask) function is used to replace the existing camera mask for any camera. A mask is an array of bytes, one byte per mask pixel block. Returns true when masks are applied.

### Calibration State

The [TT\_CalibrationState](motive-api-function-reference.md#tt_calibrationstate) function is used to report the current state and is typically tracked throughout the calibration process. In addition to providing status information to the operator, the Calibration state is used to determine if and when other calibration functions should be run.&#x20;

### Wanding

OptiTrack Calibration Wands are configured with preset distances between the markers to ensure precision when calculating the position of the marker in the 3D space.&#x20;

{% hint style="warning" %}
Version 3.0 of the API uses the CW-500 (500mm) Calibration Wand only. To use an alternate Wand size, complete the calibration in Motive and use the [TT\_LoadCalibration](motive-api-function-reference.md#tt_loadcalibration-tt_loadcalibrationw) function to import the calibration file (.CAL) into your application.&#x20;
{% endhint %}

#### Start Wanding

The [TT\_StartCalibrationWanding](motive-api-function-reference.md#tt_startcalibrationwanding) function begins the calibration wanding process, collecting samples until the [TT\_StartCalibrationCalculation](motive-api-function-reference.md#tt_startcalibrationcalculation) function is called.&#x20;

The [TT\_CalibrationCamerasLackingSamples](motive-api-function-reference.md#tt_calibrationcameraslackingsamples) function shows which cameras need more samples to obtain the best calibration. When this function returns an empty vector, then there are sufficient samples to begin calculating the calibration.

#### Start Calculation

The [TT\_StartCalibrationCalculation](motive-api-function-reference.md#tt_startcalibrationcalculation) function ends the wanding phase and begins calculating the calibration from the samples collected.

#### Calibration State

Use the [TT\_CalibrationState](motive-api-function-reference.md#tt_calibrationstate) function to monitor progress through the following states:&#x20;

* **Initialized:** the calibration process has started.&#x20;
* **Wanding:** the system is collecting samples.
* **WandingComplete:** the system has finished collecting samples. This state is set automatically when the [TT\_StartCalibrationCalculation](motive-api-function-reference.md#tt_startcalibrationcalculation) function is called. &#x20;
* **PreparingSolver:** the system is setting up the environment for the solver.
* **EstimatingFocals:** the system is estimating the camera focal lengths.&#x20;
* **CalculatingInitial:** the system is setting up the environment to calculate the calibration.&#x20;
* **Phase1 - 3:** the system is calculating the calibration.&#x20;
* **Phase4:** the calibration calculation is finished and ready for the user to either apply or cancel.&#x20;
* **Complete:** the calibration has been applied to the cameras and the process is finished.&#x20;
* **CalibrationError:** this state occurs either when the calibration has not been started (or reset) or when an error occurs during the calibration process.&#x20;

#### Apply Calibration

Once the Calibration State is "Phase4," use the [TT\_ApplyCalibrationCalculation](motive-api-function-reference.md#tt_applycalibrationcalculation) function to apply the newly calculated calibration to the cameras.&#x20;

#### Cancel Calibration

The [TT\_CancelCalibration](motive-api-function-reference.md#tt_cancelcalibration) function stops the calibration process. Use this when a calibration error occurs or any other time you wish to stop the calibrating.

#### Evaluate Calibration

Use the [TT\_CurrentCalibrationQuality](motive-api-function-reference.md#tt_currentcalibrationquality) function to score the calibration quality on a scale from 0-5, with 5 being the highest quality.&#x20;

### Ground Plane

Set the ground plane by calling the [TT\_SetGroundPlane](motive-api-function-reference.md#tt_setgroundplane) function. When called, the camera system will search for 3-markers that resemble a calibration square. Once found, the system will use the inputted vertical offset value to configure the ground plane.
