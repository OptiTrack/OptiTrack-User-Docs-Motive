---
description: An overview of common features available in the Calibration Pane.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/calibration-pane
---

# Calibration Pane

The Calibration pane is used to calibrate the capture volume for accurate tracking. This pane is typically open by default when Motive starts. It can also be opened by selecting _Calibration_ from the _View_ menu, or by clicking the ![](<../.gitbook/assets/image (1059).png>) icon.&#x20;

## Overview

Calibration is essential for high quality optical motion capture systems. During calibration, the system computes the position and orientation of each camera and number of distortions in captured images to construct a 3D capture volume in Motive. This is done by observing 2D images from multiple synchronized cameras and associating the position of known calibration markers from each camera through triangulation.

If there are any changes in a camera setup the system must be recalibrated to accommodate those changes. Additionally, calibration accuracy may naturally deteriorate over time due to ambient factors such as fluctuations in temperature. For this reason, we recommend recalibrating the system periodically.

This page will provide a brief overview of the options available on the Calibration Pane. For more detail on these functions and to learn more about calibration outside of the functionality of the Calibration pane, please read the [Calibration ](../motive/calibration/)page.&#x20;

## New Calibration

<img src="../.gitbook/assets/Calibration Pane - New Calibration (2).png" alt="The Calibration pane." width="306">

### Prepare the Volume

Before you begin the calibration process, ensure the volume is properly setup for the capture.&#x20;

* Place the cameras. Read more on the [Camera Placement](../hardware/camera-placement.md) page.
* Aim and focus the cameras. Read more on the [Aiming and Focusing](../hardware/aiming-and-focusing.md) page.
* Remove all extraneous reflections or markers in the volume. Cover any that cannot be removed.

{% hint style="info" %}
Need help? Click the ![](<../.gitbook/assets/image (215).png>) button on the Calibration pane to open the [Calibration ](../motive/calibration/)documentation page.
{% endhint %}

When you are ready to begin calibrating, click the _New Calibration_ button.&#x20;

### Masking

The first step in the system calibration process is to mask any reflections that cannot be removed from the volume or covered during calibration, such as the light from another camera.&#x20;

* During masking, the calibration pane will display the cameras in a grid. When a camera detects reflections in its view, a warning icon <img src="../.gitbook/assets/Calibration warning icon.png" alt="" data-size="line"> will display for that camera in the Calibration pane.&#x20;

{% hint style="success" %}
Prime series camera indicator LED rings will light up in white if reflections are detected.
{% endhint %}

* Check the corresponding camera view to identify where the reflection is coming from, and if possible, remove it from the capture volume or cover it for the calibration.
* In the [Calibration pane](calibration-pane.md), click _Mask_ to apply masks over all reflections in the view that cannot be removed or covered, such as other cameras.

<figure><img src="../.gitbook/assets/image (1548).png" alt="" width="563"><figcaption><p>Masking, Left: Visible objects detected; Right: No visible objects detected.</p></figcaption></figure>

#### Clear Masks

If masks were previously applied during another calibration or manually via the [2D viewport](viewport.md#camera-masking-settings) and they are no longer needed, click _Clear Masks_ to remove them.

#### Cancel

Cancels the calibration process and returns to the Calibration pane's initial window.

#### Mask

Applies masks to all detected objects in the capture volume.

#### Skip

This button bypasses the masking process and is not recommended.&#x20;

#### Continue

This button will move to the next phase of the Calibration process with the masks applied.

### Wand the Volume

![](<../.gitbook/assets/image (250).png>)

#### Calibration Type

* **Full:**  Calibrate all the cameras in the volume from scratch, discarding any prior known position of the camera group or lens distortion information. A full calibration will also take the longest time to run.
* **Refine:**  Adjusts slight changes in the calibration of the cameras based on prior calibrations. This will solve faster than a full calibration. Use this only if the cameras have not moved significantly since they were last calibrated. A refine calibration will allow minor modifications in camera position and orientation, which can occur naturally from the environment, such as due to mount expansion.

{% hint style="warning" %}
Refinement cannot run if a full calibration has not been completed previously on the selected cameras.
{% endhint %}

#### Wand

Select the wand to use to calibrate the volume. Please refer to the [Wand Types](../motive/calibration/#wand-types) section on the [Calibration ](../motive/calibration/)page for more detail.

#### Cancel

This button moves back one step to the masking window.&#x20;

#### Start Wanding

The _Start Wanding_ button begins the calibration process. Please see [Wanding Steps](../motive/calibration/#wanding-steps) in the Calibration page for more information on wanding.

* The Calibration pane will display a table of the wanding status to monitor the progress. For best results, wand evenly and comprehensively throughout the volume, covering both low and high elevations.&#x20;
* Continue wanding until the camera squares in the Calibration pane turn from dark green (insufficient number of samples) to light green (sufficient number of samples). Once all the squares have turned light green the _Start Calculating_ button will become active.
* Press _Start Calculating_. Generally, 1,000-4,000 samples per camera are enough. Samples above this threshold are unnecessary and can be detrimental to a calibration's accuracy.

![Camera squares changing from grey (no samples taken)&#x20;
to dark green (some samples taken) to&#x20;
light green (sufficient samples taken).](<../.gitbook/assets/image (212).png>)

#### Show list

Displays the number of samples each camera has captured. Between 1,000-4,000 samples is ideal.&#x20;

![Adequate samples collected for 3 cameras.](<../.gitbook/assets/image (205).png>)

#### Start Calculating

The _Start Calculati&#x6E;_&#x67; button stops the collection of samples and begins calculating the calibration based on the samples taken during the wanding stage.&#x20;

* Camera squares will start out red, and change color based on the calibration results:
  * **Red:**  Calibration samples are Poor and have a high Mean Ray Error.
  * **Light Red:** Calibration samples are fair.
  * **Gray:**  Calibration samples are Good.
  * **Dark Cyan:** Calibration samples are Excellent.
  * **Light Cyan:**  Calibration samples are Exceptional.

![An exceptional calibration in Motive.](<../.gitbook/assets/image (225).png>)

* If the results are acceptable, press _Continue_ to apply the calibration. If not, press _Cancel_ and repeat the wanding process.&#x20;
* In general, if the results are anything less than Excellent, we recommend you adjust the camera settings and/or wanding techniques and try again.

### Setting the Ground Plane

The final step in the calibration process is to set the ground plane.&#x20;

<figure><img src="../.gitbook/assets/Set Ground Plane - all options (1).png" alt=""><figcaption><p>Set Ground Plane options, from left:  Auto, Custom, and Rigid Body.</p></figcaption></figure>

#### Ground Plane Selection

* **Auto (default setting):** Automatically detect the ground plane once it's in the volume.
* **Custom:**  Create your own custom ground plane by positioning three markers that form a right-angle with one arm longer than the other, like the shape of the calibration square. Measure the distance from the midpoint of the marker to the ground and enter that value in the vertical offset field.&#x20;
* **Rigid Body:**  Select a rigid body and set the ground plane to the rigid body's pivot point.&#x20;

Once you have selected the appropriate ground plane, click _Set Ground Plane_ to complete the calibration process.&#x20;

## Change Ground Plane

On the main Calibration pane, Click _Change Ground Plane..._ for additional tools to further refine your calibration. Use the page selector <img src="../.gitbook/assets/Tab - page through screens.png" alt="" data-size="line"> at the bottom of the pane to access the various pages.&#x20;

<figure><img src="../.gitbook/assets/Change Ground Plane - 3 pages (3).png" alt=""><figcaption><p>Change Ground Plane Tools, from left: Refine Ground Plane, Translate and Rotate, and Scale Volume.</p></figcaption></figure>

### Refine Ground Plane

The Ground Plane Refinement feature improves the leveling of the coordinate plane. This is useful when establishing a ground plane for a large volume, because the surface may not be perfectly uniform throughout the plane.

To use this feature, place several markers with a known radius on the ground, and adjust the vertical offset value to the corresponding radius. Select these markers in Motive and press _Refine Ground Plane._ This will adjust the leveling of the plane using the position data from each marker.&#x20;

### Translate and Rotate

To adjust the position and orientation of the global origin after the capture has been taken, use the capture volume translation and rotation tool.

To apply these changes to recorded _Takes_, you will need to reconstruct the 3D data from the recorded 2D data after the modification has been applied.

### Scale Volume

To rescale the volume, place two markers a known distance apart. Enter the distance, select the two markers in the 3D Viewport, and click _Scale Volume_.&#x20;

## Load Calibration

To load a previously completed calibration, click _Load Calibration,_ which will open to the Calibrations folder. Select the Calibration (\*.cal) file you wish to load and click OK.&#x20;

## Open Calibrations Folder

Calibration files are automatically saved in the default Calibrations folder every time a calibration is completed. Click _Open Calibration Folder_ to manage calibration files using Windows File Explorer. Calibration files cannot be opened or loaded into Motive from this window.&#x20;

![Motive's Calibrations Folder in Windows File Explorer.](<../.gitbook/assets/image (223).png>)

## Continuous Calibration

The continuous calibration feature continuously monitors and refines the camera calibration to its best quality. When enabled, _minor_ distortions to the camera system setup can be adjusted automatically without wanding the volume again. For detailed information, read the [Continuous Calibration](../motive/calibration/continuous-calibration.md) and the [Continuous Calibration Pane](../motive/calibration/continuous-calibration-pane.md) pages.

* **Enabled:** Turns on [Continuous Calibration](../motive/calibration/continuous-calibration.md).
* **Status:** Displays the current status of Continuous Calibration:
  * **Sampling:** Motive is sampling the position of at least four markers.
  * **Evaluating:** Motive is calculating the newly acquired samples.

![Continuous Calibration status.](<../.gitbook/assets/image (207).png>)

### Anchor Markers

Anchor markers can be used to further improve continuous calibration updates, especially on systems that consists of multiple sets of cameras that are separated into different tracking areas, by obstructions or walls, with limited or no camera view overlap.&#x20;

<figure><img src="../.gitbook/assets/Anchor markers CROPPED (1).png" alt="" width="307"><figcaption></figcaption></figure>

Click the right dot <img src="../.gitbook/assets/Tab - Page through 2 screens.png" alt="" data-size="line"> at the bottom of the Calibration pane to view the anchor marker window.

For more information regarding anchor markers, visit the [Anchor Marker Setup](../motive/calibration/continuous-calibration.md#anchor-marker-setup) section of the Continuous Calibration page.
