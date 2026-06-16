---
description: Motive's Live Pipeline Settings defined.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/settings/settings-live-pipeline
---

# Settings: Live Pipeline

## Overview

Use the Application Settings panel to customize Motive and set default values. This page will cover the items available on the Live Pipeline tab. Properties are Standard unless noted otherwise.&#x20;

{% hint style="info" %}
**Solver settings for recorded captures:**

Please note that these settings apply only to Live 3D data. To optimize the solver settings for captures that are already recorded, adjust the solver values from the [properties](../properties-pane/properties-pane-take.md) of the corresponding TAK file.
{% endhint %}

Live Pipeline settings contain camera filter and solver settings for obtaining 3D data in Motive. These settings are optimized by default to provide high-quality tracking for most applications.&#x20;

Please see the following pages for descriptions of the settings on other tabs:

* [Settings: General](settings-general.md)
* [Settings: Assets](settings-assets.md)
* [Settings: Streaming](settings-streaming.md)
* [Settings: Views](settings-views.md)
* [Settings: Mouse and Keyboard](settings-mouse-and-keyboard.md)
* [Settings: Audio](settings-audio.md)

Application Settings can be accessed from the [View menu](../toolbar-command-bar.md#view) or by clicking the <img src="../../.gitbook/assets/Settings button (10).png" alt="A screenshot of the Settings button in Motive. " data-size="line"> icon on the main toolbar.&#x20;

{% hint style="info" %}
**Advanced Settings**

The Settings panel contains advanced settings that are hidden by default. To access these settings, click the <img src="../../.gitbook/assets/Motive Context Menu (25).png" alt="A screenshot of the Menu button in Motive. " data-size="line"> button in the top right corner.&#x20;

Use the _Edit Advanced_ option to customize which settings are in the _Advanced Settings_ category and which appear in the standard view, to show only the settings that are needed specifically for your capture application.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Settings - Show or Edit advanced (2).png" alt="A screenshot of the Settings menu options in Motive. "><figcaption><p>Show or Edit Advanced Settings.</p></figcaption></figure>

{% hint style="info" %}
To restore all settings to their default values, select _Reset Settings_ from the Edit menu.
{% endhint %}

## Solver Settings

Solver settings control how each marker's trajectory is reconstructed into the 3D space and how Rigid Bodies, Skeletons, and Trained Markersets track. The solver is designed to work for most applications using the default settings. However, in some instances, changing settings will lead to better tracking results.&#x20;

The standard settings are those most likely to be customized by the user. We recommend exercising caution before making adjustments to any Solver advanced settings.&#x20;

<figure><img src="../../.gitbook/assets/Settings - Live Pipeline Solver Standard.png" alt="A screenshot of the Motive Settings panel showing the standard Live Pipeline settings, with the Solver properties displayed. "><figcaption><p>Basic Live Pipeline Solver settings.</p></figcaption></figure>

### General Solver Settings

<figure><img src="../../.gitbook/assets/Settings - Live Pipeline General Advanced.png" alt="A screenshot of the standard and advanced settings available in the General section of the Live Pipeline settings. "><figcaption><p>Basic and Advanced General settings on the Live Pipeline Solver tab.</p></figcaption></figure>

<details>

<summary>Live Pipeline Presets</summary>

Live Pipeline Presets provide an easy way to switch between the default (Motive) and custom solver settings, such as the _High Camera Count Volume Presets (_&#x69;ncluded as a Beta feature).&#x20;

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - preset options.png" alt="A screenshot of the Live Pipeline Preset solver options from the Motive Settings panel, Live Pipeline settings. "><figcaption></figcaption></figure>

Click the drop down to select a new preset or to _Import, Save,_ or _Delete_ existing configurations. Presets are saved as .MOTIVE files in:

&#x20;C:\ProgramData\OptiTrack\Motive\LiveReconstructionSettings

* **Import Preset:** Allows the user to browse to a previously-saved preset .MOTIVE file in another location on the local computer or on a network drive.&#x20;
* **Save Preset:** Saves the current configuration as a new .MOTIVE file. If the file is saved in the Presets folder, it will appear in the top section of the drop down list.&#x20;
* **Delete Preset:** Removes obsolete presets from the list and deletes the .MOTIVE file.&#x20;
* **Open Presets Folder:** Opens the Presets folder in an Explorer window for direct file management. Use this option if you wish to move files in bulk or to save old presets in an alternate location.

</details>

<details>

<summary>Marker Type</summary>

Determines which marker types will be included in the solve:

* **Active + Passive:** includes both Active and Passive markers in the solve. This is the default setting.&#x20;
* **Passive Only:** includes only Passive markers in the solve and excludes Active markers.
* **Active Only:** includes only Active markers in the solve and excludes Passive markers.&#x20;

</details>

<details>

<summary>Enable Solver <em>(Advanced)</em></summary>

Enables or disables the solver to run while in Live mode.&#x20;

{% hint style="warning" %}
This setting should always be Enabled. Disable it only when the capture volume contains a large number of cameras and solver processing time is slowing down the take recordings, causing frame drops.
{% endhint %}

</details>

<details>

<summary>DoF Prediction Percent <em>(Advanced)</em></summary>

Controls the deceleration of the asset joint angles in the absence of other evidence. For example, a setting of 60% will reduce the velocity by 99% in 8 frames; whereas 80% will take 21 frames to get to the same velocity reduction.

</details>

<details>

<summary>IK Iterations</summary>

Sets the number of inverse kinematic (IK) solve iterations to perform for a skeleton to get to the final pose in each frame when the skeleton is tracking continuously. Note that larger numbers increase the CPU usage and increase batch processing times.&#x20;

See the advanced property [Boot IK Iterations](settings-live-pipeline.md#boot-ik-iterations-advanced) to set the number of iterations when the skeleton is booting.&#x20;

{% hint style="success" %}
In recorded captures, this property may need to be changed, under the [TAK properties](../properties-pane/properties-pane-take.md), if the recording starts with actors who are not in standing-up positions or if any are difficult to solve. When this is the case, Skeletons may not solve in the first couple of frames. Increasing this value will allow the Skeletons to converge on the first frame.
{% endhint %}

</details>

<details>

<summary>Residual Threshold <em>(Advanced)</em></summary>

The residual is the distance between a Marker Constraint and its assigned trajectory. If the residual exceeds this threshold, then that assignment will be broken. A larger value helps catch rapid acceleration of limbs, for example.

</details>

<details>

<summary>Frame Queue Size <em>(Advanced)</em></summary>

Sets the number of incoming frames that can be queued for the solver at a time.&#x20;

Adjust this value if you are experiencing skipped 3D marker or bone animation frames in recordings. Note that larger values may result in lag time in the display.&#x20;

{% hint style="warning" %}
Whenever you make changes to this setting, you must restart Motive to apply the new value.&#x20;
{% endhint %}

</details>

### Reconstruction Bounds

These properties are only available when Advanced settings are displayed.&#x20;

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - solver advanced Reconstruction Bounds.png" alt="A screenshot of the advanced settings available in the Reconstruction Bounds section of the Live Pipeline settings. "><figcaption><p>Advanced Reconstruction Bounds settings on the Live Pipeline Solver tab.</p></figcaption></figure>

<details>

<summary>Enable</summary>

Ignores reconstructed 3D points outside of the reconstruction bounds.

</details>

<details>

<summary>Show Bounds</summary>

Adds a visual display to the 3D Viewport that shows the limits of the reconstruction bounds.&#x20;

</details>

<details>

<summary>Shape</summary>

This setting establishes the general shape of the reconstruction bounds. Options are:

* Cuboid
* Cylinder
* Spherical
* Ellipsoid

</details>

<details>

<summary>Additional Reconstruction Bound Settings</summary>

The rest of the settings in this section can be modified in relation to center, width, radius, and height.

</details>

### Ray Length Limits

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - Ray Length Limits.png" alt="A screenshot of Motive Settings Panel, Live Pipeline settings, showing the Ray Length Limits section of the Solver tab. "><figcaption><p>Ray Length settings on Live Pipeline Solver tab. </p></figcaption></figure>

<details>

<summary>Enable Ray Length Limits</summary>

This setting allows you to excludes long rays from the 3D reconstruction. This can help reduce  jitter and improve tracking stability in large tracking environments.&#x20;

</details>

<details>

<summary>Maximum Ray Length</summary>

When the Enable Ray Length Limits setting is enabled, this setting allows you to set the value, in meters, for the desired maximum ray length. &#x20;

</details>

The Trajectorizer settings control how the 2D marker data is converted into 3D points in the calibrated volume. The Trajectorizer performs reconstruction of 2D data into 3D data, and these settings control how markers are created in the 3D scene over time.

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - Trajectorizer Advanced.png" alt="A screenshot of the standard and advanced settings available in the Trajectorizer section of the Live Pipeline settings. "><figcaption><p>Basic and Advanced Trajectorizer settings on the Live Pipeline Solver tab.</p></figcaption></figure>

<details>

<summary>3D Acceleration Threshold</summary>

* **What it does:** This setting controls the maximum distance between a marker trajectory and its predicted position.
* **When to change:** This setting may need to be increased when tracking extra fast assets. The default setting should track most applications. Attempt to track with default settings first, and if there are any gaps in the marker trajectories, you can incrementally increase the distance until stable tracking is achieved.

</details>

<details>

<summary>3D Marker Threshold</summary>

This setting controls the maximum distance between a ray and the marker origin.

</details>

<details>

<summary>3D Merge Threshold (Advanced)</summary>

Two marker trajectories discovered within this distance are merged into a single trajectory.

</details>

<details>

<summary>2D Threshold (Advanced)</summary>

A marker trajectory is predicted on a new frame and then projected in all the cameras. To be assigned to a marker detection in a particular camera, the distance (in pixels) must not exceed this threshold.

</details>

<details>

<summary>2D Marker Threshold (Advanced)</summary>

The maximum number of pixels between a camera detection and the projection of its marker.

</details>

<details>

<summary>Angle Threshold (Advanced)</summary>

The new marker trajectory is generated at the intersection of two rays through detections in different cameras. Each detection must be the only candidate within this many pixels of the projection of the other ray.

</details>

<details>

<summary>Marker Prediction Percent (Advanced)</summary>

Marker trajectories are predicted on the next frame to have moved with this percentage of their velocity on the previous frame.

</details>

<details>

<summary>Skeleton Reversion Percent (Advanced)</summary>

When a Skeleton marker trajectory is not seen, its predicted position reverts towards its assigned Marker Constraints by this percentage.

</details>

<details>

<summary>Rigid Body Reversion Percent (Advanced)</summary>

When a Rigid Body marker trajectory is not seen, its predicted position reverts towards its assigned Marker Constraints by this percentage.

</details>

<details>

<summary>Minimum Rays to Start</summary>

* **What it does:** This sets the minimum number of [tracked rays](../../motive/reconstruction-and-2d-mode.md#marker-rays) that need to converge on one location to create a new marker in 3D. This is also the minimum number of calibrated cameras that see the same target marker within the 3D threshold value for them to initially get trajectorized into a 3D point.
* **When to change:** For large volumes with high camera counts, increasing this value may provide more accurate and robust tracking. The default value of 3 works well with most medium and small-sized volumes. For volumes that only have two cameras, the trajectorizer will use a value of 2 even when it's not explicitly set.

</details>

<details>

<summary>Minimum Rays to Continue</summary>

* **What it does:** This sets the minimum number of rays that need to converge on one location to continue tracking a marker that already initialized near that location. A value of 1 will use asset definitions to continue tracking markers even when a 3D marker could not have been created from the camera data without the additional asset information.
* **When to change:** This is set to 1 by default. It means that Motive will continue the 3D data trajectory as long as at least one ray is obtained and the asset definition matches. When single ray tracking is not desired or for volumes with a large number of cameras, change this value to 2 to utilize camera overlaps in the volume.

</details>

<details>

<summary>Active Pattern Depth</summary>

* **What it does:** This setting is used for tracking active markers only. It sets the number of frames of motion capture data used to uniquely identify the ID value of an active marker.
* **When to change:** When using a large number of active tags or active pucks, this setting may need to be increased. We recommend using the active batch programmer when configuring multiple active components, and when each batch of active devices has been programmed, the programmer will provide a minimum active pattern depth value that should be used in Motive.

</details>

<details>

<summary>Minimum Active Count (Advanced)</summary>

* **What it does:** The total number of rays that must contribute to an active marker before it is considered active and given an ID value.
* **When to change:** Change this setting to increase the confidence in the accuracy of active marker ID values (not changed very often).

</details>

<details>

<summary>Maximum Fill Frames</summary>

* What it does: The number of frames of data that the solver will attempt to fill if a marker goes missing for some reason. This value must be at least 1 if you are using active markers.
* When to change: If you would like more or fewer frames to be filled when there are small gaps.

</details>

### Booter

The Booter settings control when the assets start tracking, or boot, on the trajectorized 3D markers in the scene, which determine when Rigid Bodies and/or Skeletons track on a set of markers.

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - solver Advanced Booter.png" alt="A screenshot of the standard and advanced settings available in the Booter section of the Live Pipeline settings. "><figcaption><p>Basic and Advanced Booter settings on the Live Pipeline Solver tab.</p></figcaption></figure>

<details>

<summary>Missing Marker Penalty Value <em>(Advanced)</em></summary>

The penalty for leaving Marker Constraints unassigned (per label graph edge).

</details>

<details>

<summary>Boot Residual Threshold <em>(Advanced)</em></summary>

The maximum average distance between the marker trajectory and the Marker Constraints before the asset is rebooted.

* **What it does:** This controls the maximum distance between a pair of Marker Constraints to be considered as an edge in the label graph.
* **When to change:** The default settings should work for most applications. This value may need to be increased to track large assets with markers that are far apart.

</details>

<details>

<summary>Boot Skeleton Label Percent</summary>

* **What it does:** This sets the percentage of Skeleton markers that need to be trajectorized in order to track the corresponding Skeleton(s). If needed, this setting can also be configured per each asset from the corresponding asset properties using the [Properties pane](../properties-pane/).
* **When to change:** The default settings should work for most applications. Set this value to about 75% to help keep Skeletons from booting on other markers in the volume if there are similar Skeleton definitions or lots of loose markers in the scene. If you would like Skeletons to boot faster when entering the volume, then you can set this value lower.

</details>

<details>

<summary>Boot Residual Percent <em>(Advanced)</em></summary>

This value controls how willing an asset is to boot onto markers. A higher value will make assets boot faster when entering the volume. A lower value will stop assets from booting onto other markers when they leave the volume.

</details>

<details>

<summary>Boot IK Iterations <em>(Advanced)</em></summary>

Sets the number of inverse kinematic (IK) solve iterations to perform for a skeleton to get to the final pose when the skeleton is booting or has been occluded or otherwise left and re-entered the scene. Note that larger numbers increase the CPU usage and increase batch processing times.&#x20;

See the standard property [IK Iterations](settings-live-pipeline.md#ik-iterations) to set the number of iterations when the skeleton is already tracking.&#x20;

{% hint style="success" %}
In recorded captures, this property may need to be changed, under the [TAK properties](../properties-pane/properties-pane-take.md), if the recording starts with actors who are not in standing-up positions or if any are difficult to solve. When this is the case, Skeletons may not solve in the first couple of frames. Increasing this value will allow the Skeletons to converge on the first frame.
{% endhint %}

</details>

<details>

<summary>Boot Max Assets <em>(Advanced)</em></summary>

The maximum number of assets to boot per frame.

</details>

## Cameras Settings

This Cameras tab of the Live Pipeline settings is used to configure the filter properties for all the cameras in the system.&#x20;

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - Camera Basic Settings.png" alt="A screenshot of the Motive Settings panel showing the standard Live Pipeline settings, with the Cameras properties displayed. "><figcaption><p>Basic Live Pipeline Cameras settings.</p></figcaption></figure>

### General Cameras Settings

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - cameras Advanced General.png" alt="A screenshot of the standard and advanced settings available in the General section of the Cameras settings. "><figcaption><p>Basic and Advanced General settings on the Live Pipeline Cameras tab.</p></figcaption></figure>

<details>

<summary>Live Pipeline Presets</summary>

Live Pipeline Presets provide an easy way to switch between the default (Motive) and custom solver settings, such as the _High Camera Count Volume Presets (_&#x69;ncluded as a Beta feature).&#x20;

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - preset options.png" alt="A screenshot of the Live Pipeline Preset solver options from the Motive Settings panel, Live Pipeline settings. "><figcaption></figcaption></figure>

Click the drop down to select a new preset or to _Import, Save,_ or _Delete_ existing configurations. Presets are saved as .MOTIVE files in:

&#x20;C:\ProgramData\OptiTrack\Motive\LiveReconstructionSettings

* **Import Preset:** Allows the user to browse to a previously-saved preset .MOTIVE file in another location on the local computer or on a network drive.&#x20;
* **Save Preset:** Saves the current configuration as a new .MOTIVE file. If the file is saved in the Presets folder, it will appear in the top section of the drop down list.&#x20;
* **Delete Preset:** Removes obsolete presets from the list and deletes the .MOTIVE file.&#x20;
* **Open Presets Folder:** Opens the Presets folder in an Explorer window for direct file management. Use this option if you wish to move files in bulk or to save old presets in an alternate location.

</details>

<details>

<summary>Mask Padding <em>(Advanced)</em></summary>

Changes the padding around masks by pixels.

</details>

<details>

<summary>Shutter Offset <em>(Advanced)</em></summary>

Delay this group from sync pulse by this amount.

</details>

<details>

<summary>Synchronizer Control <em>(Advanced)</em></summary>

Controls how the synchronizer operates. Options include:

* Force Timely Delivery
* Favor Timely Delivery
* Force Complete Delivery

</details>

### **Camera Filters - Software**

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - cameras Advanced Camera Filters.png" alt="A screenshot of the standard and advanced settings available in the Camera Filters - Software section of the Cameras settings. "><figcaption><p>Basic and Advanced Camera Filters - Software settings on the Live Pipeline Cameras tab.</p></figcaption></figure>

<details>

<summary>Filter Type <em>(Advanced)</em></summary>

Choose the filter type. Options include:

* Size and Roundness
* None

</details>

<details>

<summary>Minimum Pixel Threshold</summary>

Establishes the minimum pixel size of a 2D object (a collection of pixels grouped together) for the object to be included in the Point Cloud reconstruction.&#x20;

All pixels must first meet the brightness threshold defined in the Cameras pane in order to be grouped as a 2D object. This setting can be used to filter out small reflections that are flickering in the view. The default value for the minimum pixel size is 4, which means that there must be 4 or more pixels in a group for a ray to be generated.

</details>

<details>

<summary>Maximum Pixel Threshold <em>(Advanced)</em></summary>

The maximum allowable size of the 2D object (pixels over threshold).

</details>

<details>

<summary>Circularity</summary>

This property sets the threshold of the circularity filter. Valid range is between 0 and 1; with 1 being a perfectly round reflection and 0 being flat.&#x20;

Using this 2D object filter, the software identifies marker reflections based on the shape, specifically the roundness, of the group of thresholded pixels. A higher circularity setting will filter out all other reflections that are not circular. We recommend optimizing this setting so that extraneous reflections are efficiently filtered out while true marker reflections are not.

When using lower resolution cameras to capture smaller markers at a long distance, the marker reflection may appear to be more pixelated and non-circular. In this case, you may need to lower the circularity filter value for the reflection to be considered a 2D object from the camera view. This setting may also need to be lowered when tracking non-spherical markers in order to avoid filtering those reflections.

![The circle filter omitting non-circular reflections from a 2D camera view.](<../../.gitbook/assets/image (320) (1) (1) (1).png>)

</details>

### Camera Filters - Hardware

The Camera Filters - Hardware section is shown only when the advanced settings are displayed.&#x20;

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - cameras Advanced Filters Hardware.png" alt="A screenshot of the standard and advanced settings available in the Camera Filters - Hardware section of the Cameras settings. "><figcaption><p>Basic and Advanced Camera Filters - Hardware settings on the Live Pipeline Cameras tab.</p></figcaption></figure>

<details>

<summary>Intrusion Band</summary>

The size of the guard region beyond the object margin for neighbor detection.

</details>

<details>

<summary>Grayscale Floor</summary>

The pixel intensity of the grayscale floor (pixel intensity).

</details>

<details>

<summary>Object Margin Diameter</summary>

The minimum space (in pixels) between objects before they begin to overlap.

</details>

<details>

<summary>Object Skew</summary>

The number of pixels a 2D object is allowed to lean.

</details>

<details>

<summary>Max Aspect Tolerance</summary>

The maximum allowable aspect tolerance to process a 2D object (width:height).

</details>

<details>

<summary>Aspect Base</summary>

The allowable aspect tolerance for very small objects.

</details>

<details>

<summary>Aspect Step Size</summary>

The rate at which the aspect tolerance relaxes as object size increases.

</details>

## Recording Settings

Settings on the Recording tab determine what data is recorded by the cameras in the system.

<figure><img src="../../.gitbook/assets/Settings - Live Pipeline Recording Standard.png" alt="A screenshot of the Motive Settings panel showing the standard Live Pipeline settings, with the Recording properties displayed. "><figcaption><p>Basic Live Pipeline Recording settings.</p></figcaption></figure>

### General Recording Settings

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - recording Advanced General.png" alt="A screenshot of the standard and advanced settings available in the General section of the Recording settings. "><figcaption><p>Basic and Advanced General settings on the Live Pipeline Recording tab.</p></figcaption></figure>

<details>

<summary>Live Pipeline Presets</summary>

Live Pipeline Presets provide an easy way to switch between the default (Motive) and custom solver settings, such as the _High Camera Count Volume Presets (_&#x69;ncluded as a Beta feature).&#x20;

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - preset options.png" alt="A screenshot of the Live Pipeline Preset solver options from the Motive Settings panel, Live Pipeline settings. "><figcaption></figcaption></figure>

Click the drop down to select a new preset or to _Import, Save,_ or _Delete_ existing configurations. Presets are saved as .MOTIVE files in:

&#x20;C:\ProgramData\OptiTrack\Motive\LiveReconstructionSettings

* **Import Preset:** Allows the user to browse to a previously-saved preset .MOTIVE file in another location on the local computer or on a network drive.&#x20;
* **Save Preset:** Saves the current configuration as a new .MOTIVE file. If the file is saved in the Presets folder, it will appear in the top section of the drop down list.&#x20;
* **Delete Preset:** Removes obsolete presets from the list and deletes the .MOTIVE file.&#x20;
* **Open Presets Folder:** Opens the Presets folder in an Explorer window for direct file management. Use this option if you wish to move files in bulk or to save old presets in an alternate location.

</details>

<details>

<summary>Labeled Markers</summary>

Enables the recording of labeled markers.&#x20;

</details>

<details>

<summary>Active Markers</summary>

Enables the recording of Active markers.&#x20;

</details>

<details>

<summary>Unlabeled Markers</summary>

Enables the recording of unlabeled markers.&#x20;

</details>

<details>

<summary>Bone Animations <em>(Advanced)</em></summary>

Enables the recording of the bone or rigid body positions and orientations for each frame. When enabled, each asset will have a _Solved_ check mark on in the Assets pane in the recording.

</details>

<details>

<summary>Active Tags <em>(Advanced)</em></summary>

Enables the recording of Active tags.&#x20;

</details>

<details>

<summary>External Devices <em>(Advanced)</em></summary>

Enables the recording of external devices, such as NI-DAQ and force plates.&#x20;

</details>

### Memory Allocation Settings

<figure><img src="../../.gitbook/assets/Settings Live Pipeline - Recording Memory Alloc.png" alt="A screenshot of the Motive Settings Panel, Live Pipeline settings, Recording tab, memory allocation section. "><figcaption></figcaption></figure>

<details>

<summary>Preallocate Frames (sec)</summary>

Preallocates memory at the start of the recording, in seconds, to reduce the chance of frame drops. Set this to a value equal to or greater than your expected recording time, in seconds.&#x20;

</details>

<details>

<summary>Conserve Unlabeled Markers</summary>

This setting causes Motive to recycle inactive unlabeled markers rather than generating new while recording. This reduces the number of unlabeled markers created overall in the take.

</details>
