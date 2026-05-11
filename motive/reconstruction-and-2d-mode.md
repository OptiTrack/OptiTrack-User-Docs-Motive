---
description: >-
  An in-depth explanation of the reconstruction process and settings that affect
  how 3D tracking data is obtained in Motive.
---

# Reconstruction and 2D Mode

## Overview

**Reconstruction** is the process of deriving 3D points from 2D coordinates obtained by captured camera images. When multiple synchronized images are captured, the 2D centroid locations of detected marker reflections are triangulated on each captured frame and processed through the solver pipeline to be tracked. This involves the **trajectorization** of detected 3D markers within the calibrated capture volume and the **booting** process for the tracking of defined assets.

* For real-time tracking in Live mode, settings are configured under the _Live-Pipeline_ tab in the [Application Settings](../motive-ui-panes/settings/settings-live-pipeline.md). Click the <img src="../.gitbook/assets/Settings button (3).png" alt="" data-size="line"> icon on the main toolbar to open the Settings panel.&#x20;
* When post-processing recorded _Takes_ in Edit mode, the solver settings are found under the corresponding [Take properties](../motive-ui-panes/properties-pane/properties-pane-take.md).&#x20;

The optimal configuration may vary depending on the capture application and environmental conditions. For most common applications, the default settings should work well.

![3D markers reconstructed from captured 2D images.](<../.gitbook/assets/image (877).png>)

In this page, we will focus on:

* Key system-wide settings that directly impact the reconstruction outcome under the [Live Pipeline settings](../motive-ui-panes/settings/settings-live-pipeline.md);&#x20;
* [Camera Settings](../motive-ui-panes/devices-pane.md) that apply to individual cameras;&#x20;
* [Visual Aids](../motive-ui-panes/viewport.md#visual-aids) related to reconstruction and tracking;
* the Real-Time Solve process; and&#x20;
* Post-production Reconstruction. &#x20;

## Application Settings:  Live Pipeline

When a camera system captures multiple synchronized 2D frames, the images are processed through two filters before they are reconstructed into 3D tracking: first through the camera hardware then through a software filter. Both filters are important in determining which 2D reflections are identified as marker reflections and reconstructed into 3D data.&#x20;

The [Live Pipeline settings](../motive-ui-panes/settings/settings-live-pipeline.md) control tracking quality in Motive.  Adjust these settings to optimize the 3D data acquisition in both live-reconstruction and post-processing reconstruction of capture data.

To open the [Applications Settings](../motive-ui-panes/settings/) panel, click the <img src="../.gitbook/assets/Settings button (4).png" alt="" data-size="line"> button on the main toolbar to open. Click the Live Pipeline settings, which contains two tabs: _Solver_ and _Cameras_.&#x20;

### Solver Settings

Motive processes markers rays based on the camera system [calibration](calibration/) to reconstruct the respective markers. The solver settings determine how 2D data is trajectorized and solved into 3D data for tracking Rigid Bodies, Trained Markersets, and/or Skeletons. The solver combines marker ray tracking with pre-defined asset definitions to provide high-quality tracking.&#x20;

{% hint style="success" %}
The default solver settings work for most tracking applications. Users should not need to modify these settings.&#x20;
{% endhint %}

#### **Minimum Rays to Start / Minimum Rays to Continue**

These settings establish the minimum number of _tracked_ marker rays required for a 3D point to be reconstructed (_to Start_) or to continue being tracked (_to Continue_) in the _Take_. In other words, this is the minimum number of calibrated cameras that need to see the marker for it to be tracked.&#x20;

Increasing the Minimum Rays value may prevent extraneous reconstructions. Decreasing it may prevent marker occlusions from occurring in areas with limited camera coverage.&#x20;

In general, we recommend modifying these settings only for systems with either a high or very low camera count.

<img src="../.gitbook/assets/Settings - Live Pipeline Solver tab basic only.png" alt="Reconstruction settings are located under the Live Pipeline tab in the Application Settings." width="491">

**Additional Settings**

There are other reconstruction settings on the Solver tab that affect the acquisition of 3D data. For a detailed description of each setting, please see the [Application Settings: Live Pipeline](../motive-ui-panes/settings/settings-live-pipeline.md) page.

### Cameras Tab: Camera Filters - Software

The 2D camera filter is applied by the camera each time it captures a frame of an image. This filter examines the sizes and shapes of the detected reflections (IR illuminations) to determine which reflections are markers.&#x20;

{% hint style="info" %}
Camera filter settings apply to Live tracking only as the filter is applied at the hardware level when the 2D frames are captured. Modifying these settings will not affect a recorded _Take_ as the 2D data has already been filtered and saved.&#x20;

These values can be modified in a recorded _Take_ and the 3D data reconstructed during post-processing. See the section [Post-Processing Reconstruction](reconstruction-and-2d-mode.md#post-processing-reconstruction) for more information. &#x20;
{% endhint %}

**Minimum / Maximum Pixel Threshold**

The _Minimum_ and _Maximum Pixel Threshold_ settings determines the lower and upper boundaries of the size filter. Only reflections with pixel counts within the range of these thresholds are recognized as marker reflections, and reflections outside the range are filtered out.&#x20;

{% hint style="info" %}
_Maximum Pixel Threshold_ is an advanced setting. Click the <img src="../.gitbook/assets/Motive Context Menu (5).png" alt="" data-size="line"> button in the upper right corner of the Cameras tab and select _Show Advanced_ to access this setting.&#x20;
{% endhint %}

For common applications, the default range should suffice. In a close-up capture application, marker reflections appear bigger on the camera's view. In this case, you may need to adjust the maximum threshold value to allow reflections with more thresholded pixels to be considered as marker reflections.&#x20;

![2D Filter settings on the Cameras tab in the Live Pipeline Application Settings.](<../.gitbook/assets/Settings - Live Pipeline Camera settings.png>)

#### Circularity

The camera looks for circles when determining if a given reflection is a marker, as markers are generally spheres attached to an object. When captured at an angle, a circular object may appear distorted and less round than it actually is.&#x20;

The _Circularity_ value establishes the degree (as a percentage) to which a reflection can vary from circular for the camera to recognize it as a marker. Only reflections with circularity values greater than the defined threshold will be identified as marker reflections.

The valid range is between 0 and 1, with 0 being completely flat and 1 being perfectly round. The default value of .60 requires a reflection to be at least 60% circular to identify it as a marker.&#x20;

The default value is sufficient for most capture applications. This setting may require adjustment when tracking assets with alternative markers (such as reflective tape) or whose shape and/or movement creates distortion in the capture.&#x20;

## Camera Settings

In general, the overall quality of 3D reconstructions is determined by the quality of the captured camera images.&#x20;

* Ensure the cameras are [focused ](../hardware/aiming-and-focusing.md)on the tracking volume and markers are clearly visible in each camera view.&#x20;
* Adjust the [F-Stop](../hardware/aiming-and-focusing.md#how-to-change-focus) on the camera if necessary.&#x20;
* Check and optimize camera properties such as [Exposure ](../motive-ui-panes/properties-pane/properties-pane-camera.md#exposure)and [Threshold ](../motive-ui-panes/properties-pane/properties-pane-camera.md#threshold)values.

Camera settings are configured under the [Devices pane](../motive-ui-panes/devices-pane.md) or under the [Properties pane](../motive-ui-panes/properties-pane/properties-pane-camera.md) when one or more camera is selected. The following section highlights settings directly related to 3D reconstruction.

![](<../.gitbook/assets/image (299).png>)

### Enable Reconstruction

**Tracking mode vs. Reference mode:** Only cameras recording in _tracking mode_ (Object or Precision) contribute to reconstructions; Cameras in reference mode (MJPEG or Grayscale) do NOT contribute. For more information, please see the [Camera Video Types](camera-video-types.md) page.

There are three methods to switch between camera video types:

* Click the icon under _Mode_ for the desired camera in the [Devices pane](../motive-ui-panes/devices-pane.md) until the desired mode is selected.
* Right-click the camera in the [Cameras view](../motive-ui-panes/viewport.md#cameras-view) of the viewport and select _Video Type,_ then select the desired mode from the list.&#x20;
* Select the camera and use the _O, U,_ or _I hotkeys_ to switch to Object, Grayscale, or MJPEG modes, respectively.&#x20;

<figure><img src="../.gitbook/assets/Cameras View Context Menu - Video type (1).png" alt="" width="515"><figcaption><p>Cameras View: Select Video Type.</p></figcaption></figure>

**Object mode vs. Precision Mode**

[Object Mode](camera-video-types.md) and [Precision Mode](camera-video-types.md) deliver slightly different data to the host PC:

* In object mode, cameras capture 2D centroid location, size, and roundness of markers and transmit that data to the host PC.&#x20;
* In precision mode, cameras send the pixel data from the capture region to the host PC where  additional processing to determine the centroid location, size, and roundness of the reflections takes place .&#x20;

### Threshold Setting

The Threshold value determines the minimum brightness level required for a pixel to be tracked in Motive, when the camera is in tracking mode.&#x20;

Pixels with a brightness value that exceeds the configured threshold are referred to as **thresholded pixels** and only they are captured and processed in Motive. All other pixels that do not meet the brightness threshold are filtered out. Additionally, clusters of thresholded pixels are filtered through the 2D Object Filter to determine if any are possible marker reflections.

The Threshold setting is located in the [camera properties](../motive-ui-panes/properties-pane/properties-pane-camera.md).&#x20;

{% hint style="danger" %}
We do not recommend lowering the threshold below the default value of 200 as this can introduce noise and false reconstructions in the data.
{% endhint %}

## Visual Aids

The [Viewport ](../motive-ui-panes/viewport.md)has an array of Visual Aids for both the [3D Perspective](../motive-ui-panes/viewport.md#visual-aids) and [Cameras Views](../motive-ui-panes/viewport.md#visual-aids-1). This next section focuses on Visual Aids that display data relevant to reconstruction.&#x20;

To select a Visual Aid from either view, click the <img src="../.gitbook/assets/Motive Visual Options button (1).png" alt="" data-size="line"> button on the pane's toolbar. &#x20;

### Marker Rays

After the 2D camera filter has been applied, each 2D centroid captured by a camera forms a 3D vector ray, known as a Marker Ray in Motive. The Marker Ray connects the centroid to the 3D coordinates of the camera. Marker rays are critical to reconstruction and trajectorization.&#x20;

Trajectorization is the process of using 2D data to calculate 3D marker trajectories in Motive. When the minimum required number of rays (as defined in the [Minimum Rays](../motive-ui-panes/settings/settings-live-pipeline.md) setting) converge and intersect within the allowable maximum offset distance, trajectorization of the 3D marker occurs. The maximum offset distance is defined by the [3D Marker Threshold](../motive-ui-panes/settings/settings-live-pipeline.md#id-3d-marker-threshold) setting on the Solver tab of the Live Pipeline settings.&#x20;

Monitoring marker rays using the Visual Aids in the 3D Viewport is an efficient way of inspecting reconstruction outcomes by showing which cameras are contributing to the reconstruction of a selected marker.

There are two different types of marker rays in Motive:  tracked rays and untracked rays.&#x20;

#### **Tracked Ray (Green)**

Tracked rays are marker rays that contribute to 3D reconstructions within the volume.&#x20;

There are three Visual options for tracked rays:&#x20;

* **Show Selected:** Only the rays that contribute to the reconstruction of the selected marker(s) are visible, all others are hidden. If nothing is selected, no rays are shown.&#x20;
* **Show All:** All tracked rays are displayed, regardless of the selection.&#x20;
* **Hide All:**  No rays are visible.&#x20;

<img src="../.gitbook/assets/Viewport - tracked rays all.png" alt="the 3D Viewport with All Tracked Rays displayed." width="563">

**Untracked Ray (Red)**

An untracked ray does not contribute to the reconstruction of a 3D point. Untracked rays occurs when reconstruction requirements, such as the minimum ray count or the max residuals, are not met.

Untracked rays can occur from errant reflections in the volume or from areas with insufficient camera coverage.&#x20;

<img src="../.gitbook/assets/Viewport - Tracked and Untracked Rays All.png" alt="Untracked rays in a volume." width="563">

#### Marker Size

Click the [Visual Aids](../motive-ui-panes/viewport.md#visual-aids-1) button in the [Cameras View](../motive-ui-panes/viewport.md#cameras-view) to select the Marker Size visual. This will add a label to each centroid that shows the size, in pixels, and indicates whether it falls inside or outside the boundaries of the size filter (too small or too large).

* Markers that are within the minimum and maximum pixel threshold are marked with a yellow crosshair at the center. The size label is shown in White.
* Markers that are outside the boundaries of the size filter are shown with a small red X and the text _Size Filter_. The label is red.&#x20;

{% hint style="success" %}
Only markers that are close to the size boundaries but not within them will display in the Camera view in red. Markers with a significant size variance from the limits will be filtered out of the Camera view.&#x20;
{% endhint %}

<img src="../.gitbook/assets/Viewport - Cameras with Size visual.png" alt="Reflections accepted (white) or rejected (red) by the size filter." width="563">

**Circularity**

As noted above, the Camera Software Filter also identifies marker reflections based on their shape, specifically, the roundness. The filter assumes all marker reflections have circular shapes and filters out all non-circular reflections detected.&#x20;

The allowable circularity value is defined under the Circularity setting on the Cameras tab of the Live Pipeline settings in the Applications Setting panel.&#x20;

Click the [Visual Aids](../motive-ui-panes/viewport.md#visual-aids-1) button in the [Cameras View](../motive-ui-panes/viewport.md#cameras-view) to select the Circularity visual.&#x20;

* Markers that exceed the Circularity threshold are marked with a yellow crosshair at the center. The Circularity label is shown in White.
* Markers that are below the Circularity threshold are shown with a small red X and the text _Circle Filter_. The label is red.&#x20;

<img src="../.gitbook/assets/Viewport - Cameras View Circularity Visual.png" alt="Reflections accepted (white) or rejected (red) by the Circularity filter." width="563">

#### Pixel Inspector

Technically a mouse tool rather than a visual aid, the Pixel Inspector displays the x, y coordinates and, when in reference mode, the brightness value for individual pixels in the 2D camera view.&#x20;

To enable, click the <img src="../.gitbook/assets/Viewport - Mouse Actions Button.png" alt="" data-size="line"> button in the [Cameras View](../motive-ui-panes/viewport.md#cameras-view) to open the [Mouse Actions](../motive-ui-panes/viewport.md#mouse-actions) menu and select _Pixel Inspector_.

Drag the mouse to select a region in the 2D view for the selected camera, zooming in until the data is visible. Move the mouse over the region to display the values for the pixel directly below the cursor and the eight pixels surrounding it. Average values for each column and row are displayed at the top and bottom of the selected range.&#x20;

<img src="../.gitbook/assets/Viewport - Pixel Inspector.png" alt="Analyzing pixel brightness values using the pixel inspector." width="563">

{% hint style="info" %}
If the Brightness values display 0 for illuminated pixels, it means the camera is in tracking mode. Change the video mode to Grayscale or MJPEG to display the brightness.
{% endhint %}

## Real-time Solve

Motive performs _real-time_ reconstruction of 3D coordinates from 2D data in:

* Live mode (using live 2D data capture)
* 2D Edit mode (using recorded 2D data)

When Motive is processing in real-time, you can examine the marker rays and other visuals from the viewport, review and modify the Live-Pipeline settings, and otherwise optimize the 3D data acquisition.

### Live Mode

In [Live mode](data-recording/#live-mode-and-edit-mode), Any changes to the Live Pipeline settings (on either Solver or Camera tabs) are reflected immediately in the Live capture.

<img src="../.gitbook/assets/image (314).png" alt="The current mode is highlighted in Cyan on the control deck." width="563">

### 2D Edit Mode

When a capture is recorded in Motive, both 2D camera data and reconstructed 3D data are saved into the _Take_ file. By default, the 3D data is loaded when the recorded _Take_ file is opened.

Recorded 3D data contains the 3D coordinates that were live-reconstructed at the moment of capture and is independent of the 2D data once it's recorded. However, You can still view and edit the recorded 2D data to optimize the solver parameters and reconstruct a _fresh_ set of 3D data from it.&#x20;

2D Edit Mode is used in the post-processing of a captured _Take_. Playback in Edit 2D performs a live reconstruction of the 3D data, immediately reflecting changes made to settings or assets. These changes are not applied to the recording until the _Take_ is [reprocessed](reconstruction-and-2d-mode.md#applying-changes-to-3d-data) and saved.&#x20;

## Post-Processing Reconstruction

#### **Open 2D Edit mode**

Click the _Edit_ button in the Control Deck and select _EDIT 2D_ from the list.&#x20;

<figure><img src="../.gitbook/assets/Live or Edit mode - switch to 2D.png" alt=""><figcaption><p>Edit menu in the Control Deck.</p></figcaption></figure>

Alternately, you can click the <img src="../.gitbook/assets/Motive Context Menu (2).png" alt="" data-size="line"> button in the top right corner of the [Data pane](../motive-ui-panes/data-pane.md) to select 2D Mode.&#x20;

#### Update the Reconstruction Settings

Changes made to the Solver or Camera filter configurations in the Live Pipeline settings do not affect the recorded data. Instead, these values are adjusted in a recorded _Take_ from the [Take Properties](../motive-ui-panes/properties-pane/properties-pane-take.md). &#x20;

Select the _Take_ in the [Data pane](../motive-ui-panes/data-pane.md) to display the Camera Filter values and Solver properties that were in effect when the recording was made. These values can be adjusted and the 3D data reconstructed as part of the post-processing workflow.&#x20;

<figure><img src="../.gitbook/assets/Properties Pane - Take Camera and Solver only.png" alt=""><figcaption><p>Camera Filter and Solver settings in the <em>Take</em> Properties.</p></figcaption></figure>

To see additional settings not shown here, click the <img src="../.gitbook/assets/Motive Context Menu (3).png" alt="" data-size="line"> button in the top right corner of the pane and select _Show Advanced._&#x20;

#### **Applying changes to 3D data**

Once the reconstruction/solver settings are optimized for the recorded data, it's time to perform the post-processing reconstruction pipeline on the _Take_ to reconstruct a new set of 3D data.&#x20;

{% hint style="warning" %}
This step overwrites the existing 3D data and discards all of the post-processing edits completed on that data, including edits to the marker labels and trajectories.

Additionally, recorded Skeleton marker labels, which were intact during the live capture, may be discarded, and the reconstructed markers may not be auto-labeled correctly again **if the Skeletons are never in well-trackable poses during the captured&#x20;**_**Take**_**.** This is another reason to always start a capture with a good [calibration pose](skeleton-tracking.md#calibration-pose) (e.g., a T-pose).
{% endhint %}

Right-click the take in the Data Pane to open the menu. post-processing options are in the third section from the top.

<figure><img src="../.gitbook/assets/Data Pane - Take file menu - reconstruction only.png" alt=""><figcaption><p>Post-processing Options from the Data Pane menu.</p></figcaption></figure>

There are three options to Reconstruct 3D data:

* **Reconstruct:**  Creates a new 3D data set.&#x20;
* **Reconstruct and Auto-Label:**  Creates a new 3D data set and auto-labels markers in the _Take_ based on existing asset definitions. To learn more about the [auto-labeling process](labeling.md#auto-label), please see the [Labeling ](labeling.md)page.&#x20;
* **Reconstruct, Auto-Label and Solve:** Creates a new 3D data set, auto-labels and solves all assets in the _Take_. When an asset is solved, Motive stores the tracking data for the asset in the _Take_ then reads from that Solved data to recreate and track the asset in the scene.&#x20;

Post-processing reconstruction can be performed on the entire frame range in a _Take_ or applied to a specified frame range by selecting the range under the [Control Deck](../motive-ui-panes/control-deck.md) or in the [Graph pane](../motive-ui-panes/graph-view-pane.md). When nothing is selected, reconstruction is applied to all frames.

Multiple _Takes_ can be selected and processed together by holding the shift key while clicking the _Takes_ in the [Data pane](../motive-ui-panes/data-pane.md).  When multiple takes are selected, the reconstruction will apply to the entire frame range of every Takes in the selection . &#x20;
