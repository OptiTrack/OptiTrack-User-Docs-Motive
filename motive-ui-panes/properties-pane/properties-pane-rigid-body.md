---
description: An in-depth look at the properties available for Rigid Bodies.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/properties-pane/properties-pane-rigid-body
---

# Properties Pane: Rigid Body

Rigid body properties determine how the corresponding [Rigid Body asset](../../motive/rigid-body-tracking/) is tracked and displayed in the [3D Viewport](../viewport.md). This page covers the properties specific to Rigid Bodies. For general information on using and customizing the Properties pane, see the [Properties Pane](./) page. For detailed descriptions of properties for other asset types or devices, please see the following pages:

* [Properties: Take](properties-pane-take.md)
* [Properties: Trained Markerset](properties-pane-trained-markerset.md)
* [Properties: Skeleton](properties-pane-skeleton.md)
* [Properties: Camera](properties-pane-camera.md)
* [Properties: eSync](properties-pane-esync2.md)
* [Properties: Force Plates](properties-pane-force-plates.md)
* [Properties: NI-DAQ](properties-pane-ni-daq.md)
* [Properties: OptiHub2](properties-pane-optihub2.md)
* [Properties: eSync2](properties-pane-esync2.md)

## Rigid Body Properties

Select a Rigid Body asset in the [Assets pane](../assets-pane.md) or in the [3D viewport](../viewport.md#perspective-view), and the corresponding properties will be listed under the [Properties pane](./). These properties can be modified both in Live and Edit mode. Default creation properties are listed under the [Assets Settings](../settings/settings-assets.md).

<figure><img src="../../.gitbook/assets/Rigid Body with Assets Pane and Properties Pane.png" alt="The Motive Viewport with a rigid body displayed, alongside the Assets pane and the Properties pane."><figcaption><p>A Rigid Body with Properties.</p></figcaption></figure>

{% hint style="info" %}
**Advanced Settings**

The Properties pane contains advanced settings that are hidden by default. To access these settings, click the <img src="../../.gitbook/assets/Motive Context Menu (24).png" alt="the Motive 3-dot settings menu button. " data-size="line"> button in the top right corner.&#x20;

Use the _Edit Advanced_ option to customize which settings are in the _Advanced Settings_ category and which appear in the standard view, to show only the settings that are needed specifically for your capture application.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Properties Pane - Show Advanced (3).png" alt="The menu to Show Advanced or Edit Advanced settings in Motive. "><figcaption><p>Show or Edit Advanced Settings.</p></figcaption></figure>

### General Properties

The following items are available in the General Properties section. Properties are Standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/RB Properties - General Advanced 3.2.png" alt="The General section of the Rigid Body Properties pane, with standard and advanced properties displayed. "><figcaption><p>Rigid body properties:  General.</p></figcaption></figure>

<details>

<summary>Asset Name</summary>

Enter a custom name for the Rigid Body. The default name is "Rigid Body X," where X is the Rigid Body ID. The Asset Name can also be changed by right-clicking the Rigid Body in the Assets pane.

</details>

<details>

<summary>Enable</summary>

Enable or Disable tracking of the selected Rigid Body. A disabled Rigid Body will not be tracked, and its data will not be included in the exported or streamed tracking data or displayed in the 3D Viewport.

{% hint style="info" %}
To hide the markers associated with a disabled asset in the [3D Viewport](../viewport.md):&#x20;

* Click <img src="../../.gitbook/assets/Viewport Visual Options button (3).png" alt="The button to display the Visuals menu from the 3D Viewport." data-size="line"> to open the _Visuals_ menu.&#x20;
* Select _Markers -> Hide for Disabled Assets_.&#x20;
{% endhint %}

</details>

<details>

<summary>Notes</summary>

An optional text field for storing additional information about the Rigid Body. The data in the Notes field is not included when exporting the asset to a CSV file.&#x20;

</details>

<details>

<summary>Minimum Markers to Boot</summary>

Sets the minimum number of markers that must be tracked and labeled in order for a Rigid Body asset, or each Skeleton bone, to be booted or first tracked.

</details>

<details>

<summary>Minimum Markers to Continue</summary>

Sets the minimum number of markers that must be tracked and labeled in order for a Rigid Body asset, or each Skeleton bone, to continue to be tracked after the initial boot.

</details>

<details>

<summary>Minimum Active Markers to Boot <em>(Advanced Setting)</em></summary>

Sets the minimum number of active markers that must be tracked and labeled for Rigid Bodies to be booted or first tracked. For more information on working with Active Markers, see the pages [Active Marker Tracking](../../active-classic/active-marker-tracking/) and [IMU Sensor Fusion](../../motive/imu-sensor-fusion.md).&#x20;

</details>

<details>

<summary>Asset Scale <em>(Advanced Setting)</em></summary>

Increase or decrease the size of the Rigid Body bone by scaling the asset. By default, the Asset Scale is set to 100%.&#x20;

</details>

<details>

<summary>Deflection Ratio <em>(Advanced Setting)</em></summary>

Allows the asset to deform more or less to accommodate markers that don't fit the model. High values will allow assets to fit onto markers that don't match the model as well.

</details>

<details>

<summary>Streaming ID</summary>

User definable ID for the selected Rigid Body. When working with capture data in the external pipeline, this value can be used to address specific Rigid Bodies in the scene.

</details>

### Visuals

The following items are available in the Visuals section. Properties are Standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/RB Properties - Visuals.png" alt="The Visuals section of the Rigid Body Properties pane, with standard and advanced properties displayed. "><figcaption><p>Rigid body properties:  Visuals section.</p></figcaption></figure>

<details>

<summary>Bone Major Axis <em>(Advanced Setting)</em></summary>

Set the axis with which the bone should be aligned. The coordinate at the end of the bone is expected to be on this axis.

</details>

<details>

<summary>Default Bone Length <em>(Advanced Setting)</em></summary>

Set the offset (in mm) from the bone to the end effector, along the major axis, for bones that do not have child bones.&#x20;

</details>

<details>

<summary>Bone Diameter <em>(Advanced Setting)</em></summary>

Set the diameter of the bone (in mm).&#x20;

</details>

<details>

<summary>Label</summary>

Display the Rigid Body name in the [3D Perspective View](../viewport.md). When selected, a small label in the same color as the Rigid Body will appear over the centroid.

</details>

<details>

<summary>Visual</summary>

Display the marker sticks and bone constraint lines in the 3D Perspective View.&#x20;

</details>

<details>

<summary>Color</summary>

Set the color of the selected Rigid Body in the 3D Perspective View. Click the box to bring up the color picker:

<figure><img src="../../.gitbook/assets/image (1542).png" alt="" width="193"><figcaption><p>Choosing a color for a Rigid Body.</p></figcaption></figure>

</details>

<details>

<summary>Bones</summary>

Display a visual of the bone, or pivot point, of the Rigid Body in the 3D Viewport. The shape of the bone indicates whether the asset is solved or unsolved.&#x20;

<div><figure><img src="../../.gitbook/assets/Rigid Body Bone - Unsolved (1).png" alt="" width="263"><figcaption><p>The bone of an unsolved Rigid Body.</p></figcaption></figure> <figure><img src="../../.gitbook/assets/Rigid Body Bone - Solved.png" alt="" width="263"><figcaption><p>The bone of a solved Rigid Body.</p></figcaption></figure></div>

</details>

<details>

<summary>Bones Color</summary>

Set the color of the bone in the 3D Perspective View. By default, the bone uses the same color as the Rigid Body asset.

</details>

<details>

<summary>Bone Orientation <em>(Advanced Setting)</em></summary>

Display the Rigid Body's local coordinate axes. This option can be useful in visualizing the orientation of the Rigid Body, and for setting orientation offsets. The setting is enabled in the images above.

</details>

<details>

<summary>Bone Position History</summary>

Show the history of the Rigid Body’s position in the Perspective view. When enabled, the option to set the history length becomes available.&#x20;

<figure><img src="../../.gitbook/assets/RB - Bone Position History in Viewport.png" alt="" width="250"><figcaption><p>Position history setting enabled <br>on a Rigid Body.</p></figcaption></figure>

</details>

<details>

<summary>Bone Degrees of Freedom <em>(Advanced Setting)</em></summary>

Display degrees of freedom, position and orientation, for each bone pivot.

</details>

<details>

<summary>Marker Constraints</summary>

Show the Marker Constraints as transparent spheres on the Rigid Body. Marker Constraints are the expected marker locations according to the Rigid Body solve.

</details>

<details>

<summary>Marker to Constraint Lines <em>(Advanced Setting)</em></summary>

Show lines between labeled Rigid Body markers and corresponding expected marker locations. This helps to visualize the offset distance between actual marker locations and the Marker Constraints.

</details>

<details>

<summary>Bone to Constraint Line <em>(Advanced Setting)</em></summary>

Display a dotted line to connect each Marker Constraint to the Rigid Body bone pivot.&#x20;

</details>

<details>

<summary>Opacity</summary>

Sets the opacity of an attached object. An OBJ file typically comes with a corresponding MTL file which defines its properties, and the transparency of the object is defined within these MTL files. The _Opacity_ value under the Rigid Body properties rescales the loaded property. In other words, you can set the transparency in the MTL file and rescale it using the Opacity property in Motive.

</details>

<details>

<summary>Geometry <em>(Advanced Setting)</em></summary>

<figure><img src="../../.gitbook/assets/Rigid Body Properties - Geometry options (1).png" alt="Options to attach Geometry files to rigid body assets. "><figcaption><p>Geometry Options for Rigid Bodies.</p></figcaption></figure>

Attach a valid geometric model to the rigid body to display in the the 3D Viewport. Sphere, box, cylinder, and bone segment shapes are built-in; to use your own geometric model, select _Custom Model_. This will open the _Attached Geometry_ field.

</details>

<details>

<summary>Attached Geometry (Advanced Setting)</summary>

The Attached Geometry field becomes available whenever _Custom Model_ is selected for the Rigid Body geometry.&#x20;

<figure><img src="../../.gitbook/assets/Asset Properties - Attach custom geometry (1).png" alt="The control to attach a custom geometry file to a Rigid Body asset."><figcaption><p>Attach a Custom Geometry Model. </p></figcaption></figure>

Click the folder to the right of the field to browse to the OBJ, FBX, or STL file to replace the Rigid Body. Properties configured in the corresponding MTL files alongside the OBJ file will be loaded as well.

</details>

<details>

<summary>Geometry Settings</summary>

Whenever a geometric model is attached, settings to adjust the scale, location, and orientation (Pitch, Yaw, and Roll) are available.&#x20;

<figure><img src="../../.gitbook/assets/RB Properties - Geometry scale location orentation and .png" alt="Geometry settings for attached geometry files in Motive: Scale, Location, and Orientation " width="313"><figcaption><p>Geometry Settings in the Properties Pane.</p></figcaption></figure>

</details>

<details>

<summary>Geometry Tips and Examples</summary>

<figure><img src="../../.gitbook/assets/image (106).png" alt="A OBJ file of a basketball attached to a Rigid Body asset."><figcaption><p>A OBJ file of a basketball attached to a Rigid Body.</p></figcaption></figure>

{% hint style="warning" %}
If you are exporting an OBJ file from Maya, make sure the Ambient Color setting is set to white upon export. If this color is set to black, it will remove textures when the Rigid Body is deselected.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/image (450).png" alt="An OBJ file of the OptiTrack Active Classic puck in Maya."><figcaption><p>Common Material Attributes in Maya with Ambient Color selected.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (813).png" alt="Examples of an Attached Geometry file with the Ambient color set to Black (left) or White (right)."><figcaption><p>Attached Geometry models with Ambient color set to Black (left) or White (right).</p></figcaption></figure>

</details>

### Bones _(Advanced Setting)_

The Bone is the pivot point of a Rigid Body. Unlike Skeletons or Trained Markersets, Rigid Bodies are comprised of a single bone.&#x20;

<figure><img src="../../.gitbook/assets/RB Properties - Bones.png" alt="The Bones properties for a Rigid Body, standard and advanced properties shown." width="308"><figcaption><p>Bone Properties for a Rigid Body.</p></figcaption></figure>

<details>

<summary>Parent</summary>

The Parent bone is the first bone in a Bone Chain, as used in Skeleton and Trained Markerset assets.&#x20;

</details>

<details>

<summary>Children</summary>

A Child bone connects to the parent bone in a Bone Chain, as used in Skeleton and Trained Markerset assets. For Rigid Bodies, Motive displays one of the asset's marker labels.&#x20;

</details>

<details>

<summary>Segment Type</summary>

Used for Skeleton and Trained Markerset assets to identify bone segments. For Rigid Bodies, this value is set to _None_.

</details>

<details>

<summary>Rotation Order</summary>

Euler angle rotation order used for calculating the bone hierarchy.

</details>

<details>

<summary>Rotation Offset</summary>

Enter values along one of the axis to reorient the Rigid Body coordinate axis.

</details>

<details>

<summary>Translation Offset</summary>

Enter values along one of the axis to move the Rigid Body pivot point.

</details>

### Sensor Fusion

Active devices such as CinePucks and Pucks are often equipped with an Inertial Measurement Unit (IMU) that increases the accuracy of tracking when fused with the rigid body. Sensor Fusion properties affect how Motive corrects drift that can occur between data from the IMU and data from the active markers.&#x20;

To learn more about pairing IMUs to Rigid Bodies, see the [IMU Sensor Fusion](../../motive/imu-sensor-fusion.md) page.&#x20;

{% hint style="warning" %}
Sensor Fusion settings do not apply to devices (active or passive) that do not contain IMUs.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/RB Properties - Sensor Fusion.png" alt="The Sensor Fusion properties for a Rigid Body, standard and advanced properties shown."><figcaption><p>Sensors Fusion properties for a Rigid Body. </p></figcaption></figure>

<details>

<summary>Min Alignment Count <em>(Advanced)</em></summary>

The minimum number of measurements required for the IMU to auto-align. A higher number may result in a better outcome in a suboptimal environment. For example, if the CinePuck isn't being detected as expected, adjusting this value may obtain better results.&#x20;

</details>

<details>

<summary>Drift Correction Frames <em>(Advanced)</em></summary>

The number of frames over which drift correction can apply.&#x20;

IMUs will drift over time from their correct value without the value actually changing. Motive counters this by using the optical data as a source of truth, however optical data can be noisy and less precise than IMU data. Drift correction is the process by which the optical data is used to correct the IMU data.&#x20;

</details>

<details>

<summary>Drift Correction Angle <em>(Advanced)</em></summary>

Determines the angle (in degrees) between the calculated drift correction and the current drift correction that will trigger correction.&#x20;

When this value is exceeded, Motive will immediately correct the sensor fusion rotation to optical. This can help in circumstances where the IMU is physically impacted, such as when it is attached to an object with recoil.&#x20;

</details>

<details>

<summary>Max Drift Correction <em>(Advanced)</em></summary>

The rate of drift correction.&#x20;

This changes how heavily the optical data is weighted or trusted in calculating the drift correction. A drift correction of 1 will look much like the optical data, whereas a drift correction close to 0 will more closely match the IMU data.&#x20;

</details>

<details>

<summary>IMU Label</summary>

Display a label with the status of the Rigid Body's IMU in the 3D Perspective View. If the asset Label is enabled, the IMU state is appended to the asset name.&#x20;

* **None** - No visual is displayed.&#x20;
* **Text** - Descriptive text provides detailed information about the IMU state.
* **Icon** - An icon-only visual is used.&#x20;

The text label includes the following information:&#x20;

* **Tag Name.**
* The status of **Sensor Fusion:**
  * **Rotate to Align (##/100)**: this status indicates that more rotations are required to align the IMU with the Rigid Body.
  * **Fused:** Sensor Fusion completed successfully.&#x20;
* The **Optical** status indicates whether the Minimum Markers to Continue threshold has been met (Optical) or not (no optical). The status _Optical Good_ means that most of the markers can be seen and tracked.&#x20;
* The **%** status denotes the percentage of IMU packets that an IMU Tag is successfully delivering for every 100 frames.&#x20;

</details>

### Smoothing and Damping

Smoothing and damping settings adjust for noise and jitter.&#x20;

<figure><img src="../../.gitbook/assets/RP Properties - Smoothing and Damping.png" alt="The Smoothing and Damping properties for a Rigid Body, standard and advanced properties shown."><figcaption><p>Smoothing and Damping properties for a Rigid Body.</p></figcaption></figure>

<details>

<summary>Smoothing</summary>

Apply double exponential smoothing to translation and rotation of the Rigid Body. Increasing this setting may help smooth out noise in the Rigid Body tracking, but excessive smoothing can introduce latency. The default value is 0 (disabled).

</details>

<details>

<summary>Forward Prediction</summary>

Compensate for system latency when tracking the corresponding Rigid Body by predicting its movement into the future. Please note that using higher values may impact the tracking stability. The default value is 0 (disabled).

</details>

<details>

<summary>Translation Damping (Advanced)</summary>

When needed, you can damp down translational tracking of a Rigid Body bone on the selected axis.

</details>

<details>

<summary>Rotation Damping (Advanced)</summary>

When needed, you can damp down rotational tracking of a Rigid Body.&#x20;

</details>

<details>

<summary>Rotation Damping Axis (Advanced)</summary>

When using Rotation Damping, select whether to apply changes to a selected axis or to all.&#x20;

</details>

### Deadband Filter

Deadband Filter settings establish a threshold for tracking the movement of the device so the device will appear static despite minor adjustments that would otherwise create jitter in the scene. This is helpful for camera tracking in ICVFX or when tracking long distances.

<figure><img src="../../.gitbook/assets/Properties - Rigid Body Deadband Filter.png" alt="The Deadband Filter properties for a Rigid Body, standard and advanced properties shown."><figcaption><p> Deadband Filter properties for a Rigid Body.</p></figcaption></figure>

<details>

<summary>Translation Threshold</summary>

The minimum distance, in mm, a device marker needs to move for Motive to adjust its location.&#x20;

</details>

<details>

<summary>Rotation Threshold</summary>

The minimum rotation, in degrees, a device marker needs to move for Motive to adjust its location.&#x20;

</details>

## Active Tag Properties

Active devices such as CinePucks and Pucks are often equipped with an Inertial Measurement Unit (IMU) that increases the accuracy of tracking when fused with the rigid body. To learn more about pairing IMUs to Rigid Bodies, read the [IMU Sensor Fusion](../../motive/imu-sensor-fusion.md) page.&#x20;

To view properties related to the IMU, select the Active Tag paired to the Rigid Body in the [Devices pane](../devices-pane.md).&#x20;

{% hint style="warning" %}
The properties shown are for ActiveIO devices. Not all are available for Active Classic devices.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/ActiveIO Standard Properties and Devices Pane.png" alt="The Properties Pane and Devices Pane for an ActiveIO Puck, paired to a Rigid Body."><figcaption><p>Properties Pane for an Active Tag (IMU) paired to a Rigid Body. Standard Properties only. </p></figcaption></figure>

### Details

The Details section displays basic information about the device and IMU.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO Adv Properties - Details.png" alt="The Details section of the ActiveIO device properties, standard and advanced properties shown."><figcaption><p>Standard and Advanced properties in the Details section of the Active Tag properties.</p></figcaption></figure>

<details>

<summary>Device Name</summary>

Identifies the type of device in which the IMU is installed.&#x20;

</details>

<details>

<summary>Tag Type</summary>

Identifies the type of tag in terms of Connection type, number of LEDs, and IMU type, if available.&#x20;

</details>

<details>

<summary>Serial Number</summary>

The serial number of the IMU.&#x20;

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Model (Advanced)</summary>

The internal model number for the IMU.

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Firmware Version <em>(Advanced)</em></summary>

The Firmware version currently installed on the IMU.&#x20;

{% hint style="success" %}
The Firmware will update automatically if necessary when the device connects to Motive.&#x20;
{% endhint %}

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Notes <em>(Advanced)</em></summary>

An open text field for storing custom device information, such as asset tag, location, etc. &#x20;

</details>

### General

The General IMU properties vary depending on the IMU type.&#x20;

<figure><img src="../../.gitbook/assets/Properties - RB IMU General Adv (1).png" alt="The General section of the ActiveIO device properties, standard and advanced properties shown."><figcaption><p>Standard and Advanced properties in the General section of the Active Tag properties.</p></figcaption></figure>

<details>

<summary>Enabled</summary>

When enabled, the device is available for tracking in Motive.&#x20;

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Connected LEDs <em>(Advanced)</em></summary>

The number of LED active markers on the device.

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Marker State</summary>

* **Off** turns off the LED pulse so the markers are lit continuously.&#x20;
* **ActiveIO** sets the LEDs to pulse on and off according to a preset pattern.&#x20;
* **Synchronized** sets the LEDs to illuminate every frame.&#x20;

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Pattern Group</summary>

A preset collection of LED patterns that ensures a unique id for each active marker in the device. Pattern groups also make it easier to assign a different set of patterns to each device in the volume.&#x20;

* Pattern groups each specify 8 marker patterns. Devices with more than 8 markers will occupy the selected pattern group and part of the next group.
* Motive will attempt to prevent overlapping patterns with ActiveIO active tags, but can not directly read or change the pattern group values of Active Classic devices.
* <mark style="background-color:$primary;">If running an ActiveIO tag and an Active Classic tag concurrently, confirm that the markers are in different pattern groups by selecting them in the 3D view and reading the label that appears.</mark>&#x20;
* Motive will also notify users when it detects duplicate active patterns in the scene.

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Illumination</summary>

Indicates the amount of time, in microseconds, that the active LEDs will illuminate per frame when the [Marker State](properties-pane-rigid-body.md#marker-state) is set to _Synchronized_ or _ActiveIO_.

By Default, this property is set to match the camera frame rate.

</details>

<details>

<summary>Battery Level</summary>

Indicates the amount of battery power available, in percent.

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Signal Strength</summary>

The strength of the RF signal, in decibel-milliwatts (dBm).&#x20;

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Packet Error Rate</summary>

Displays the percentage of:

The number of frames where device data is received / number of frames (over the past 3 seconds)

The rate is updated about every 3 seconds.

</details>

<details>

<summary>BaseStation <em>(Advanced)</em></summary>

The serial number of the BaseStation where the active device is connected.&#x20;

This property is available only for wireless devices that connect to a BaseStation.&#x20;

</details>

<details>

<summary>RF Channel <em>(Advanced)</em></summary>

The Radio frequency communication channel used to communicate with the BaseStation for wireless devices.&#x20;

This property is available only for wireless devices that connect to a BaseStation.&#x20;

</details>

<details>

<summary>Quality of Service</summary>

The Quality of Service property allows the device to send the IMU packet multiple times on redundant RF channels to reduce dropped packets in difficult RF environments.

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Device State</summary>

Indicates whether or not the device is connected to the instances of Motive:&#x20;

* Advertising: the device is available but not connected to Motive.&#x20;
* Claimed: the device is connected to Motive.&#x20;

For more information on connecting an ActiveIO device, see the [ActiveIO Configuration](../../activeio/activeio-configuration.md) page.&#x20;

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

### IMU

The IMU section of the Active device properties contains information about the status of the IMU.&#x20;

Please see the [IMU Sensor Fusion](../../motive/imu-sensor-fusion.md) page for more information on pairing an IMU to a Rigid Body.&#x20;

<figure><img src="../../.gitbook/assets/Properties - RB IMU IMU Adv.png" alt="The IMU section of the ActiveIO device properties, standard and advanced properties shown."><figcaption><p>Standard properties in the IMU section of the Active Tag properties.</p></figcaption></figure>

<details>

<summary>IMU Type</summary>

Identifies the type of IMU in the device.

</details>

<details>

<summary>Paired</summary>

Identifies the rigid body currently paired to the IMU. Lists _None_ if the IMU is currently unpaired.&#x20;

</details>

<details>

<summary>Aligned</summary>

Displays the current state of the IMU pairing.&#x20;

* Unpaired&#x20;
* Paired
* Aligned

</details>

<details>

<summary>Uplink ID <em>(Active Classic devices only)</em></summary>

For Active Classic devices, the Uplink ID is a number programmed to a tag that allows its paired base station to identify it uniquely from other tags. This number should be unique for each device associated with a base station. For wireless devices, the Uplink ID is the second component of the Active Tag name in the Devices Pane.&#x20;

</details>
