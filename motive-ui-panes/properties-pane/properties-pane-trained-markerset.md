---
description: An in-depth look at the properties available for Trained Markersets.
---

# Properties Pane:  Trained Markerset

Trained Markerset properties determine how the corresponding [Trained Markerset ](../../motive/trained-markersets.md)asset is tracked and displayed in the [3D Viewport](../viewport.md). This page covers the properties specific to Trained Markersets. For general information on using and customizing the Properties pane, see the [Properties Pane](./) page. For detailed descriptions of properties for other asset types or devices, please see the following pages:

* [Properties: Take](properties-pane-take.md)
* [Properties: Rigid Body](properties-pane-rigid-body.md)
* [Properties: Skeleton](properties-pane-skeleton.md)
* [Properties: Camera](properties-pane-camera.md)
* [Properties: eSync](properties-pane-esync2.md)
* [Properties: Force Plates](properties-pane-force-plates.md)
* [Properties: NI-DAQ](properties-pane-ni-daq.md)

## Trained Markerset Properties

Select a Trained Markerset asset in the [Assets pane](../assets-pane.md) or in the [3D viewport](../viewport.md#perspective-view), and the corresponding properties will be listed under the [Properties pane](./). These properties can be modified both in Live and Edit mode. Default creation properties are listed under the [Assets Settings](../settings/settings-assets.md).

<figure><img src="../../.gitbook/assets/MS with Assets Pane and Properties General.png" alt=""><figcaption><p>A Trained Markerset with standard properties displayed.</p></figcaption></figure>

{% hint style="info" %}
**Advanced Settings**

The Properties pane contains advanced settings that are hidden by default. To access these settings, click the <img src="../../.gitbook/assets/Motive Context Menu (25).png" alt="" data-size="line"> button in the top right corner.&#x20;

Use the _Edit Advanced_ option to customize which settings are in the _Advanced Settings_ category and which appear in the standard view, to show only the settings that are needed specifically for your capture application.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Properties Pane - Show Advanced (4).png" alt=""><figcaption></figcaption></figure>

### General Properties

The following items are available in the General Properties section. Properties are Standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/TM Properties - General.png" alt="" width="313"><figcaption></figcaption></figure>

#### **Asset Name**

Enter a custom name for the Trained Markerset. The default name is "Markerset." The Asset Name can also be changed by right-clicking the Trained Markerset in the Assets pane.

#### **Enable**

Enables or Disables tracking of the selected asset. A disabled Trained Markerset will not be tracked, and its data will not be included in the exported or streamed tracking data or displayed in the 3D Viewport.

{% hint style="info" %}
To hide the markers associated with a disabled asset in the [3D Viewport](../viewport.md):&#x20;

* Click <img src="../../.gitbook/assets/Viewport Visual Options button (5).png" alt="" data-size="line"> to open the _Visuals_ menu.&#x20;
* Select _Markers -> Hide for Disabled Assets_.&#x20;
{% endhint %}

#### **Notes**

An optional text field for storing additional information about the Rigid Body. The data in the Notes field is not included when exporting the asset to a CSV file.&#x20;

#### **Minimum Markers to Boot**

Sets the minimum number of markers that must be tracked and labeled in order for the asset to be booted or first tracked.

#### **Minimum Markers to Continue**

Sets the minimum number of markers that must be tracked and labeled in order for the asset to continue to be tracked after the initial boot.

**Asset Scale&#x20;**_**(Advanced Setting)**_

Increase or decrease the size of the Trained Markerset bone by scaling the asset. By default, the Asset Scale is set to 100%.&#x20;

**Deflection Ratio&#x20;**_**(Advanced Setting)**_

Allows the asset to deform more or less to accommodate markers that don't fit the model. High values will allow assets to fit onto markers that don't match the model as well.

### Visuals

The following items are available in the Visuals section. Properties are Standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/TM Properties - All Visuals.png" alt="" width="310"><figcaption><p>Properties Pane:  Trained Markerset Visuals.</p></figcaption></figure>

#### **Geometry&#x20;**_**(Advanced Setting)**_

<figure><img src="../../.gitbook/assets/Rigid Body Properties - Geometry options (2).png" alt="" width="272"><figcaption><p>Geometry Options for Trained Markersets.</p></figcaption></figure>

Attach a valid geometric model to the Trained Markerset to display in the the 3D Viewport. Sphere, box, cylinder, and bone segment shapes are built-in; to use your own geometric model, select _Custom Model_. This will open the _Attached Geometry_ field.

#### **Attached Geometry**

The Attached Geometry field becomes available whenever _Custom Model_ is selected for the Rigid Body geometry.&#x20;

{% hint style="info" %}
See the section [Attaching and Modifying Geometry](properties-pane-trained-markerset.md#attaching-and-modifying-geometry-advanced-setting) for information on Geometry settings.&#x20;
{% endhint %}

#### **Bone Major Axis&#x20;**_**(Advanced Setting)**_

Set the axis with which the bone should be aligned. The coordinate at the end of the bone is expected to be on this axis.

**Default Bone Length&#x20;**_**(Advanced Setting)**_

Set the offset (in mm) from the bone to the end effector, along the major axis, for bones that do not have child bones.&#x20;

**Bone Diameter&#x20;**_**(Advanced Setting)**_

Set the diameter of the bone (in mm).&#x20;

#### **Label**

Display the Trained Markerset name in the [3D Perspective View](../viewport.md). When selected, a small label will appear over the asset.

#### **IMU State**

This property is not applicable to Trained Markersets.&#x20;

#### **Visual**

Display the marker sticks and bone constraint lines in the 3D Perspective View.&#x20;

#### **Color**

Set the color of the selected Trained Markerset in the 3D Perspective View. Click the box to bring up the color picker:

<figure><img src="../../.gitbook/assets/image (1546).png" alt="" width="193"><figcaption><p>Choosing a color.</p></figcaption></figure>

#### **Bones**

Bones are optional for Trained Markersets and are [added manually](../../motive/trained-markersets.md#adding-bones) when needed. The _Bones_ property toggles on the display of a visual of any bones present in the Markerset in the 3D Viewport.

The shape of the bones indicates whether the asset is solved or unsolved:&#x20;

<div><figure><img src="../../.gitbook/assets/TM Bone - Unsolved CROPPED (1).png" alt=""><figcaption><p>Unsolved Bone in a Trained Markerset.</p></figcaption></figure> <figure><img src="../../.gitbook/assets/TM Bone - solved CROPPED.png" alt=""><figcaption><p>Solved Bone in a Trained Markerset.</p></figcaption></figure></div>

#### **Bones Color**

Set the color of the bone(s) in the 3D Perspective View.&#x20;

#### Bone Degrees of Freedom _**(Advanced Setting)**_

Display degrees of freedom, position and orientation, for each bone.

#### Marker Constraints

Show the Marker Constraints as transparent spheres on the Trained Markerset. Marker Constraints are the expected marker locations according to the Rigid Body solve.

#### Marker to Constraint Lines _**(Advanced Setting)**_

Show lines between labeled Trained Markerset markers and corresponding expected marker locations. This helps to visualize the offset distance between actual marker locations and the Marker Constraints.

#### Bone to Constraint Line _**(Advanced Setting)**_

Display a dotted line to connect each Marker Constraint to the Trained Markerset bone.&#x20;

### Bones _(Advanced Setting)_

Bones are optional for Trained Markersets and are added manually when needed. Please refer to the [Trained Markersets ](../../motive/trained-markersets.md)page for instructions on adding bones and creating Bone Chains.&#x20;

To view and update properties for a specific bone, select just the bone in the 3D Viewport.&#x20;

<div><figure><img src="../../.gitbook/assets/TM Properties - Bones yet no bones.png" alt="" width="309"><figcaption><p>Bone Properties for a Trained Markerset<br> that does not have bones.</p></figcaption></figure> <figure><img src="../../.gitbook/assets/TM Properties - Bones with single bone.png" alt="" width="311"><figcaption><p>Bone Properties for a Trained Markerset<br> with a single bone and no bone chains.</p></figcaption></figure></div>

#### Bone Name

An editable field that shows the name of the selected bone. When more than one bone is selected, the field will display _Mixed_.&#x20;

This field does not display if the Trained Markerset does not have any bones.

#### Parent

The Parent bone is the first bone in a Bone Chain. This property shows which bone in the Trained Markerset is the parent of the currently selected bone. When the selected bone is the root of the chain, or if there is no bone chain, the Parent field will display the name of the Trained Markerset asset.

When more than one bone is selected, the field will display _Mixed_.&#x20;

<figure><img src="../../.gitbook/assets/TM Properties - Bones with Parent selected.png" alt="" width="313"><figcaption><p>Bone Properties for a Trained Markerset<br>bone that is the Parent in a bone chain.</p></figcaption></figure>

#### Children

A Child bone connects to the parent bone in a Bone Chain. This property shows which bone in the Trained Markerset is the child to the currently selected bone. When the selected bone is the end of the chain, or if there is no bone chain, the Child field will display _None_.

<figure><img src="../../.gitbook/assets/TM Properties - Bones with Child selected.png" alt="" width="314"><figcaption><p>Bone Properties for a Trained Markerset<br>bone that is the Child in a bone chain.</p></figcaption></figure>

#### Segment Type

Used for Skeleton and Trained Markerset assets to identify bone segments. The list includes all standard skeleton segments and is not required.&#x20;

#### Rotation Order

Euler angle rotation order used for calculating the bone hierarchy.

#### Rotation Offset

Enter values along one of the axis to reorient the coordinate axis of the selected bone.

#### Translation Offset

Enter values along one of the axis to move the selected bone.

### Smoothing and Damping

#### **Smoothing**

Apply double exponential smoothing to translation and rotation of the Trained Markerset. Increasing this setting may help smooth out noise in the Trained Markerset tracking, but excessive smoothing can introduce latency. The default value is 0 (disabled).

#### **Forward Prediction**

Compensate for system latency when tracking the corresponding Trained Markerset by predicting its movement into the future. Please note that using higher values may impact the tracking stability. The default value is 0 (disabled).

#### **Translation Damping (Advanced)**

When needed, you can damp down translational tracking of the selected bone on the selected axis.

#### Rotation Damping **(Advanced)**

You can also damp down rotational tracking of the selected bone.&#x20;

#### Rotation Damping Axis **(Advanced)**

When using Rotation Damping, select whether to apply changes to a selected axis or to all.&#x20;

### **Attaching and Modifying Geometry&#x20;**_**(Advanced Setting)**_

#### **Geometry&#x20;**_**(Advanced Setting)**_

<figure><img src="../../.gitbook/assets/Rigid Body Properties - Geometry options (3).png" alt="" width="272"><figcaption><p>Geometry Options for Trained Markersets.</p></figcaption></figure>

Attach a valid geometric model to the Trained Markerset to display in the the 3D Viewport. Sphere, box, cylinder, and bone segment shapes are built-in; to use your own geometric model, select _Custom Model_. This will open the _Attached Geometry_ field.

#### **Attached Geometry**

The Attached Geometry field becomes available whenever _Custom Model_ is selected for the Rigid Body geometry.&#x20;

<figure><img src="../../.gitbook/assets/Asset Properties - Attach custom geometry (3).png" alt=""><figcaption><p>Attach a Custom Geometry Model. </p></figcaption></figure>

Click the folder to the right of the field to browse to the OBJ or FBX file to replace the Rigid Body. Properties configured in the corresponding MTL files alongside the OBJ file will be loaded as well.

#### Geometry Settings

Whenever a geometric model is attached, settings to adjust the scale, location, and orientation (Pitch, Yaw, and Roll) are available.&#x20;

<figure><img src="../../.gitbook/assets/RB Properties - Geometry.png" alt="" width="292"><figcaption><p>Geometry Settings in the Properties Pane.</p></figcaption></figure>

#### Geometry Tips and Examples

![Geometry Properties for a standard Cylinder object attached to a bone in a Trained Markersets.](<../../.gitbook/assets/TM with Geometry Added with Viewport.png>)

{% hint style="warning" %}
If you are exporting an OBJ file from Maya, make sure the Ambient Color setting is set to white upon export. If this color is set to black, it will remove textures when the Trained Markerset is deselected.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/image (449).png" alt=""><figcaption><p>Common Material Attributes in Maya with Ambient Color selected.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (813).png" alt=""><figcaption><p>Attached Geometry models with Ambient color set to Black (left) or White (right).</p></figcaption></figure>
