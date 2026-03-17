---
description: An in-depth look at the properties available for skeleton assets.
---

# Properties Pane: Skeleton

This page covers properties specific to skeletons. For general information on using and customizing the Properties pane, see the [Properties Pane](./) page. For detailed descriptions of properties for other asset types or devices, please see the following pages:

* [Properties: Take](properties-pane-take.md)
* [Properties: Trained Markerset](properties-pane-trained-markerset.md)
* [Properties: Rigid Body](properties-pane-rigid-body.md)
* [Properties: Camera](properties-pane-camera.md)
* [Properties: eSync](properties-pane-esync2.md)
* [Properties: Force Plates](properties-pane-force-plates.md)
* [Properties: NI-DAQ](properties-pane-ni-daq.md)

Skeleton properties determine how Skeleton assets are tracked and displayed in Motive. To view related properties, select a Skeleton asset in the [Assets pane](../assets-pane.md) or in the 3D viewport, and the corresponding properties will be listed under the [Properties pane](./). These properties can be modified both in Live and Edit mode. Default creation properties are listed under the [Application Settings](../settings/).

{% hint style="info" %}
**Advanced Settings**

The Properties pane contains advanced settings that are hidden by default. To access these settings, click the <img src="../../.gitbook/assets/Motive Context Menu (23).png" alt="A screenshot of the Motive Settings menu button." data-size="line"> button in the top right corner.&#x20;

Use the _Edit Advanced_ option to customize which settings are in the _Advanced Settings_ category and which appear in the standard view, to show only the settings that are needed specifically for your capture application.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Properties Pane - Show Advanced (2).png" alt="A screenshot of the Motive settings menu options: Show Advanced; Edit Advanced; Reset All"><figcaption></figcaption></figure>

## Skeleton Properties

Select a skeleton asset in the [Assets pane](../assets-pane.md) or in the [3D viewport](../viewport.md#perspective-view), and the skeleton's properties will display in the [Properties pane](./). These properties can be modified both in Live and Edit mode. Default creation properties are listed under the [Assets Settings](../settings/settings-assets.md).

<figure><img src="../../.gitbook/assets/Skeleton with General Properties.png" alt="A screenshot of the Motive Viewport and Properties pane, with a skeleton selected and its properties displayed. "><figcaption><p>Properties of the selected Skeleton asset.</p></figcaption></figure>

### General Settings

The following items are available in the General Properties section. Properties are Standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/Skeleton Props - General with Advanced.png" alt="A screenshot of the Motive properties pane, general properties for a Skeleton asset. "><figcaption><p>Skeleton General Properties</p></figcaption></figure>

<details>

<summary><strong>Asset Name</strong></summary>

Display the name of selected Skeleton asset in an editable field.

</details>

<details>

<summary><strong>Enable</strong></summary>

Enable or Disable tracking of the selected Skeleton. A disabled Skeleton will not be tracked, and its data will not be included in the exported or streamed tracking data or displayed in the 3D Viewport.

{% hint style="info" %}
To hide the markers associated with a disabled asset in the [3D Viewport](../viewport.md):&#x20;

* Click <img src="../../.gitbook/assets/Viewport Visual Options button (2).png" alt="" data-size="line"> to open the _Visuals_ menu.&#x20;
* Select _Markers -> Hide for Disabled Assets_.&#x20;
{% endhint %}

</details>

<details>

<summary><strong>Minimum Markers to Boot</strong></summary>

The minimum number of markers that must be tracked and labeled in order for a Skeleton, or each Skeleton bone, to be booted or first tracked.

</details>

<details>

<summary><strong>Minimum Markers to Continue</strong></summary>

The minimum number of markers that must be tracked and labeled in order for a Skeleton, or each Skeleton bone, to continue to be tracked after the initial boot.

</details>

<details>

<summary><strong>Asset Scale </strong><em><strong>(Advanced)</strong></em></summary>

Increase or decrease the size of the Skeleton by scaling the asset. By default, the Asset Scale is set to 100%.&#x20;

</details>

<details>

<summary><strong>Deflection Ratio </strong><em><strong>(Advanced)</strong></em></summary>

Allows the asset to deform more or less to accommodate markers that don't fit the model. High values will allow assets to fit onto markers that don't match the model as well.

</details>

### Visuals

The following items are available in the Visuals section. Properties are Standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/Skeleton Props - Visuals.png" alt="A screenshot of the Motive properties pane, Visuals properties for a Skeleton asset. "><figcaption><p>The Visuals Section of the Skeleton Properties pane.</p></figcaption></figure>

<details>

<summary><strong>Bone Major Axis </strong><em><strong>(Advanced)</strong></em></summary>

Set the axis with which the skeleton should be aligned. The default value is Y-Axis.

</details>

<details>

<summary><strong>Default Bone Length </strong><em><strong>(Advanced)</strong></em></summary>

Set the offset (in mm) from the bone to the end effector, along the major axis, for bones that do not have child bones.&#x20;

</details>

<details>

<summary><strong>Bone Diameter </strong><em><strong>(Advanced)</strong></em></summary>

Set the diameter of the bone (in mm).&#x20;

</details>

<details>

<summary><strong>Label</strong></summary>

Display the Skeleton name in the [3D Perspective View](../viewport.md). When selected, a small label will appear over the asset.

</details>

<details>

<summary><strong>Visual</strong></summary>

Select how the Skeleton will be shown in the 3D perspective view.

* None: Displays only constraints and marker sticks.
* Segment: Displays Skeleton as individual Skeleton segments.
* Avatar (male): Displays Skeleton as a male avatar.
* Avatar (female): Displays Skeleton as a female avatar.

</details>

<details>

<summary><strong>Color</strong></summary>

Set the color of the selected Skeleton in the 3D Perspective View. Click the box to bring up the color picker:

<figure><img src="../../.gitbook/assets/image (1541).png" alt="A screenshot of the Color Selection tool in Motive. " width="193"><figcaption><p>Changing the color of a Skeleton.</p></figcaption></figure>

</details>

<details>

<summary><strong>Bones</strong></summary>

Show or hide Skeleton bones. The bones will display on top of the _Visual_ selection.

</details>

<details>

<summary><strong>Bone Color</strong></summary>

This field is available whenever the _Bones_ visual is toggled on and allows you to change the color of the skeleton bones.&#x20;

</details>

<details>

<summary><strong>Bone Orientation </strong><em><strong>(Advanced)</strong></em></summary>

Displays orientation axes of each segments in the Skeleton.

</details>

<details>

<summary>Bone Degree of Freedom <em><strong>(Advanced)</strong></em></summary>

Display degrees of freedom, position and orientation, for each bone.

</details>

<details>

<summary><strong>Marker Constraints</strong> </summary>

Show the Marker Constraints as transparent spheres on the Skeleton. Marker Constraints are the expected marker locations according to the skeleton solve.

</details>

<details>

<summary>Marker to Constraint Lines <em><strong>(Advanced)</strong></em></summary>

Show lines between labeled Skeleton markers and corresponding expected marker locations. This helps to visualize the offset distance between actual marker locations and the Marker Constraints.

</details>

<details>

<summary>Bone to Constraint Line <em><strong>(Advanced)</strong></em></summary>

Display a dotted line to connect each Skeleton bone to its respective Marker Constraints. &#x20;

</details>

<details>

<summary><strong>Quality Visual</strong></summary>

When enabled, the color of the Skeleton segments will change whenever there are tracking errors.

* **Red** indicates there are no visible markers contributing to the reconstruction in the current frame.
* **Blue** indicates a bone has reached its degree of freedom limit.

</details>

<details>

<summary><strong>Geometry (Advanced)</strong></summary>

Skeleton assets use the Bone Segment geometry, which is selected by default. To use your own geometric model, select _Custom Model_. This will open the _Attached Geometry_ field.

<figure><img src="../../.gitbook/assets/Properties - Geometry for Skeletons.png" alt="A screenshot of the selection options when attaching Geometry to a skeleton bone segment. " width="278"><figcaption><p>Geometry Options for Skeletons.</p></figcaption></figure>

Attach a valid geometric model to the segment to display in the the 3D Viewport. Sphere, box, cylinder, and bone segment shapes are built-in.

</details>

<details>

<summary><strong>Attached Geometry  (Advanced)</strong></summary>

The Attached Geometry field becomes available whenever _Custom Model_ is selected for the Rigid Body geometry.&#x20;

<figure><img src="../../.gitbook/assets/Asset Properties - Attach custom geometry (2).png" alt="A screenshot of the property in Motive that allows the user to attach a custom geometry model to the asset. "><figcaption><p>Attach a Custom Geometry Model. </p></figcaption></figure>

Click the folder to the right of the field to browse to the OBJ or FBX file to replace the Skeleton. Properties configured in the corresponding MTL files alongside the OBJ file will be loaded as well.

</details>

<details>

<summary>Geometry Settings <strong>(Advanced)</strong></summary>

Settings to adjust the scale, location, and orientation (Pitch, Yaw, and Roll) are available.&#x20;

</details>

### **Bones (Advanced)**

Skeleton templates include pre-defined bones and bone chains that mirror the human body. The _Bones_ properties display data specific to the selected bone. If multiple bones are selected, properties that differ will display _Mixed_ for the value.&#x20;

To view and update properties for a specific bone, select just that bone in the 3D Viewport.&#x20;

All properties in the Bones section are Advanced properties.&#x20;

<div><figure><img src="../../.gitbook/assets/Properties Pane - Skeleton Bones - hip bone.png" alt="A screenshot of the Motive properties pane, Bones properties for a Skeleton asset&#x27;s Hip (or root) bone. "><figcaption><p>Skeleton Bones properties for a hip bone. <br>The hip bone is the root of the skeleton. </p></figcaption></figure> <figure><img src="../../.gitbook/assets/Properties Pane - Skeleton Bones - other bone.png" alt="A screenshot of the Motive properties pane, Bones properties for a Skeleton asset&#x27;s left thigh bone. "><figcaption><p>Skeleton Bone properties for the left thigh bone.</p></figcaption></figure></div>

<details>

<summary>Bone Name (Advanced)</summary>

An editable field that shows the name of the selected bone. When more than one bone is selected, the field will display _Mixed_.&#x20;

The hip bone is the root of the skeleton and does not display a _Bone Name_ when selected.&#x20;

{% hint style="warning" %}
It is not recommended to rename Skeleton bones.
{% endhint %}

</details>

<details>

<summary>Parent (Advanced)</summary>

The Parent bone is the first bone in a Bone Chain. This property shows which bone in the Skeleton is the parent of the currently selected bone.&#x20;

* When the selected bone is the hip (or root bone), the Parent field will display _None_.&#x20;
* When the selected bone is directly attached to the hip (root bone), this field will display the name of the Asset.&#x20;
* When more than one bone is selected and they do not share the same Parent bone, the field will display _Mixed._

</details>

<details>

<summary>Children (Advanced)</summary>

A Child bone connects to the parent bone in a Bone Chain. This property shows which bone in the Skeleton is the child to the currently selected bone. When the selected bone is the end of the chain, or if there is no bone chain, the Child field will display _None_.

</details>

<details>

<summary>Segment Type (Advanced)</summary>

Identifies the Skeleton bone segment for the selected bone.&#x20;

</details>

<details>

<summary><strong>Degrees of Freedom</strong> (Advanced)</summary>

Identifies how the selected bone segment can move. The Skeleton's root, the hip bone, has both translational and rotational Degrees of Freedom (DoF) while child bones are restricted to rotational DoF due to their attachment to their parent bone. A child bone may also specify a limited DoF due to the nature of the joint, e.g., a shin bone can only rotate on the X axis (R:X).&#x20;

</details>

<details>

<summary><strong>Rotation Order</strong> (Advanced)</summary>

Euler angle rotation order used for calculating the bone hierarchy.

</details>

<details>

<summary>Rotation Offset (Advanced)</summary>

Modifies the orientation of the selected bone.&#x20;

</details>

<details>

<summary>Translation Offset (Advanced)</summary>

Modifies the location of the pivot point of the selected bone.&#x20;

</details>

### Solver (Advanced)

Solver properties allow for the adjustment of normal shrinkage and stretching that can occur in the human spine and shoulder.&#x20;

<figure><img src="../../.gitbook/assets/Properties Pane - Skeleton Solver.png" alt="A screenshot of the Motive properties pane, Solver properties for a Skeleton asset. "><figcaption><p>The Solver Section of the Skeleton Properties pane.</p></figcaption></figure>

{% hint style="danger" %}
The default values are sufficient for most mocap applications and we recommend NOT changing them. Change these values only if you encounter issues with the solver such as shoulder popping or hand misalignment when an actor is pushing the typical limits, such as hanging by their arms, for example.&#x20;
{% endhint %}

<details>

<summary><strong>Spring Weight Scale</strong> (Advanced)</summary>

Adjust the influence of default joint angles on solved pose for calibrated Skeletons. Lower values can result in a better match between the skeleton pose and the marker positions.

</details>

<details>

<summary><strong>Spine Shrink/Stretch Limit</strong> (Advanced)</summary>

The maximum amount of stretch (or shrinkage) permitted across all four of the bones that comprise the spine: Abdomen, chest, neck, and head. This property allows for the adjustment of stretch and shrinkage that can occur normally in the human spine.&#x20;

{% hint style="danger" %}
#### **Shrink and Stretch Limits: A Warning**

The default values are sufficient for most mocap applications and we recommend NOT changing them. Change these values only if you encounter issues with the solver such as shoulder popping or hand misalignment when an actor is pushing the typical limits, such as hanging by their arms, for example.
{% endhint %}

</details>

<details>

<summary><strong>Shoulder Shrink/Stretch Limit</strong> (Advanced)</summary>

Set the maximum amount of stretch (or shrinkage) permitted in the shoulder width. This property allows for the adjustment of shrinkage that can occur normally in the human shoulders. This property can be changed for individual Skeletons through the [Solver settings](https://docs.optitrack.com/motive-ui-panes/properties-pane/properties-pane-skeleton#solver-advanced-settings) in the [Skeleton's Properties pane](https://docs.optitrack.com/motive-ui-panes/properties-pane/properties-pane-skeleton).

{% hint style="danger" %}
#### **Shrink and Stretch Limits: A Warning**

The default values are sufficient for most mocap applications and we recommend NOT changing them. Change these values only if you encounter issues with the solver such as shoulder popping or hand misalignment when an actor is pushing the typical limits, such as hanging by their arms, for example.
{% endhint %}

</details>

### Refinement (Advanced)

The Refinement section shows the quality and date of the last Range of Motion (ROM) calibration, if one has been completed.&#x20;

<figure><img src="../../.gitbook/assets/Properties Pane - Skeleton Refinement Not Done (2).png" alt="A screenshot of the Motive properties pane, Refinement properties for a Skeleton asset, prior to completing a Range of Motion calibration."><figcaption><p>The Refinement Section of the Skeleton <br>Properties pane prior to completing the ROM. </p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Properties Pane - Skeleton Refinement Completed v2.png" alt="A screenshot of the Motive properties pane, Refinement properties for a Skeleton asset, after completing a Range of Motion calibration."><figcaption><p>The Refinement Section of the Skeleton <br>Properties pane after a successful ROM. </p></figcaption></figure>

<details>

<summary>Time Stamp</summary>

The date and time of the last Range of Motion (ROM) calibration of the Skeleton. If no ROM has been completed, the time stamp field will show "Never."&#x20;

</details>

<details>

<summary>Quality</summary>

Displays the quality of the last Range of Motion (ROM) calibration of the Skeleton. If no ROM has been completed, the Quality field will show "N/A."&#x20;

</details>

<details>

<summary>Constraint Error</summary>

The average distance of the constraint position to the marker position during the Range of Motion (ROM).&#x20;

</details>

### Sensor Fusion&#x20;

Sensor Fusion properties relate to active devices. They are only applicable to skeletons when using the 6 Rigid Body skeleton template with active devices.&#x20;

{% hint style="info" %}
For more information on these properties, please see the [Sensor Fusion](properties-pane-rigid-body.md#sensor-fusion) section of the [Properties Pane: Rigid Body](properties-pane-rigid-body.md) page.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Properties Pane - Skeleton Sensor Fusion Settings.png" alt="A screenshot of the Motive properties pane, Sensor Fusion properties for a Skeleton asset. "><figcaption><p>Sensor Fusion properties.</p></figcaption></figure>

### Smoothing and Damping

Smoothing and damping properties improve the solve by reducing noise and jitter. &#x20;

<figure><img src="../../.gitbook/assets/Properties - Skeleton Smoothing and Damping.png" alt="A screenshot of the Motive properties pane, Smoothing and Damping properties for a Skeleton asset. "><figcaption></figcaption></figure>

<details>

<summary><strong>Smoothing</strong></summary>

Apply double exponential smoothing to translation and rotation of the Skeleton. Increasing this setting may help smooth out noise in the Skeleton tracking, but excessive smoothing can introduce latency. The default value is 0 (disabled).

</details>

<details>

<summary><strong>Forward Prediction</strong></summary>

Compensate for system latency when tracking the corresponding Skeleton by predicting its movement into the future. For this feature to work best, smoothing needs to be applied as well. Please note that using higher values may impact the tracking stability. The default value is 0 (disabled).

</details>

<details>

<summary><strong>Translation Damping (Advanced)</strong></summary>

When needed, you can damp down translational tracking of a Skeleton bone on the selected axis.

</details>

<details>

<summary>Rotation Damping <strong>(Advanced)</strong></summary>

You can also damp down rotational tracking of a Skeleton.&#x20;

</details>

<details>

<summary>Rotation Damping Axis <strong>(Advanced)</strong></summary>

When using Rotation Damping, select whether to apply changes to a selected axis or to all.&#x20;

</details>
