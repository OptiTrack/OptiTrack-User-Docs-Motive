# Properties Pane: Rigid Body

Rigid body properties determine how the corresponding Rigid Body asset is tracked and displayed in the viewport.

To view related properties, select a Rigid Body asset in the [Assets pane](../assets-pane.md) or in the [3D viewport](../viewport.md#perspective-view), and the corresponding properties will be listed under the [Properties pane](./). These properties can be modified both in Live and Edit mode. Default creation properties are listed under the [Application Settings](../settings/).

{% hint style="info" %}
**Advanced Settings**

The Properties: Rigid Body contains _advanced settings_ that are hidden by default. Access these settings by going to the menu on the top-right corner of the pane and clicking _Show Advanced_ and all of the settings, including the advanced settings, will be listed under the pane.

The list of advanced settings can also be customized to show only the settings that are needed specifically for your capture application. To do so, go the pane menu and click _Edit Advanced_, and uncheck the settings that you wish to be listed in the pane by default. One all desired settings are unchecked, click _Done Editing_ to apply the customized configurations.
{% endhint %}

![](<../../.gitbook/assets/image (1007) (1) (1) (1) (1) (1) (1) (3).png>)

## Rigid Body Properties

### General

![Rigid body properties listed under the Properties pane.](<../../.gitbook/assets/image (934).png>)

#### **Name**

Allows a custom name to be assigned to the Rigid Body. Default is "Rigid Body X" where x is the Rigid Body ID.

#### **Enable**

Enables/Disables tracking of the selected Rigid Body. Disabled Rigid Bodies will not be tracked, and its data will not be included in the exported or streamed tracking data.

#### **Streaming ID**

User definable ID for the selected Rigid Body. When working with capture data in the external pipeline, this value can be used to address specific Rigid Bodies in the scene.

#### **Minimum Markers to Boot**

The minimum number of markers that must be tracked and labeled in order for a Rigid Body asset, or each Skeleton bone, to be booted or first tracked.

#### **Minimum Markers to Continue**

The minimum number of markers that must be tracked and labeled in order for a Rigid Body asset, or each Skeleton bone, to continue to be tracked after the initial boot.

#### **Rotation Order**

\_\[Advanced]\_The order of the Euler axis used for calculating the orientation of the Rigid Body and Skeleton bones. Motive computes orientations in Quaternion and converts them into an Euler representation as needed. For exporting specific Euler angles, it's recommended to configure it from the Exporter settings, or for streaming, convert Quaternion into Euler angles on the client-side.

### Visuals

![Rigid body asset display properties.](<../../.gitbook/assets/image (915).png>) ![Choosing color for a Rigid Body.](<../../.gitbook/assets/image (899).png>) ![Position history setting enabled on a Rigid Body.](<../../.gitbook/assets/image (869).png>)

#### **Label**

Selects whether or not to display the Rigid Body name in the 3D Perspective View. If selected, a small label in the same color as the Rigid Body will appear over the centroid in the 3D Perspective View.

#### **Visual**

Show the corresponding Rigid Body in the 3D viewport when it is tracked by the camera system.

#### **Color**

Color of the selected Rigid Body in the 3D Perspective View. Clicking on the box will bring up the color picker for selecting the color.

#### **Bones**

For Rigid Bodies, this property shows, or hides, visuals of the Rigid Body pivot point.

#### **Bone Orientation**

_\[Advanced]_ Enables the display of a Rigid Body's local coordinate axes. This option can be useful in visualizing the orientation of the Rigid Body, and for setting orientation offsets.

#### **Bone Position History**

Shows a history of the Rigid Body’s position. When enabled, you can set the history length and the tracking history will be drawn in the Perspective view.

#### Marker Constraints

Shows the Marker Constraints as transparent spheres on the Rigid Body. Asset mode markers are the expected marker locations according to the Rigid Body solve.

#### Marker Constraints **Sticks**

Draws lines between labeled Rigid Body or Skeleton markers and corresponding expected marker locations. This helps to visualize the offset distance between actual marker locations and the Marker Constraints.

#### **Untracked Markers**

_\[Advanced]_ When enabled, all markers that are part of the Rigid Body definition will be dimmed, but still visible, when not present in the point cloud.

#### **Replace Geometry**

When a valid geometric model is loaded in the Attached Geometry section, the model will be displayed instead of a Rigid Body when this entry is set to true.

#### **Attached Geometry**

Attached Geometry setting will be visible if the Replace Geometry setting is enabled. Here, you can load an OBJ file to replace the Rigid Body. Scale, positions, and orientations of the attached geometry can be configured under the following section also. When a OBJ file is loaded, properties configured in the corresponding MTL files alongside the OBJ file will be loaded as well.

{% hint style="info" %}
**Attached Geometry Settings**

When the Attached Geometry is enabled, you can attach a 3D model to a Rigid Body and the following setting will be available also.

* **Pivot Scale:** Adjusts the size of the Rigid Body pivot point.
* **Scale:** Rescales the size of attached object.
* **Yaw (Y):** Rotates the attached object in respect to the Y-axis of the Rigid Body coordinate axis.
* **Pitch (X):** Rotates the attached object in respect to the X-axis of the Rigid Body coordinate axis.
* **Roll (Z):** Rotates the attached object in respect to the Z-axis of the Rigid Body coordinate axis.
* **X:** Translate the position of attached object in x-axis in respect to the Rigid Body coordinate.
* **Y:** Translate the position of attached object in y-axis in respect to the Rigid Body coordinate.
* **Z:** Translate the position of attached object in z-axis in respect to the Rigid Body coordinate.
* **Opacity:** Sets the opacity of an attached object. An OBJ file typically comes with a corresponding MTL file which defines its properties, and the transparency of the object is defined within these MTL files. The _Opacity_ value under the Rigid Body properties applies a factor between 0 \~ 1 in order to rescale the loaded property. In other words, you can set the transparency in the MTL file and rescale them using the Opacity property in Motive.
{% endhint %}

![A OBJ file of a basketball attached to a Rigid Body.](<../../.gitbook/assets/image (852).png>)

{% hint style="warning" %}
If you are exporting an OBJ file from Maya, you will need to make sure the Ambient Color setting is set to white upon export. If this color is set to black, it will result in removing textures when a Rigid Body is deselected.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/image (1) (3) (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (49) (2).png" alt=""><figcaption></figcaption></figure>

### IMU

{% hint style="danger" %}
IMU feature is not fully supported in Motive 3.x. Please use Motive 2.3 for using IMU active components.
{% endhint %}

#### **IMU Active Tags/Pucks:** IMU settings are applicable only to Active Tags and Pucks that are equipped with IMU sensors. This feature is not fully supported in Motive 3.x; please use Motive 2.3 version. Please refer to the [Motive 2.3 wiki](https://v23.wiki.optitrack.com/index.php?title=Active_Marker_Tracking:_IMU_Setup) page for more details on how to set up the IMU active components

#### **Uplink ID**

Uplink ID assigned to the Tag or Puck using the Active Batch Programmer. This ID must match with the Uplink ID assigned to the Active Tag or Puck that was used to create the Rigid Body.

#### **RF Channel**

Radio frequency communication channel configured on the Active Tag, or Puck, that was used to define the corresponding Rigid Body. This must match the RF channel configured on the active component; otherwise, IMU data will not be received.

### Smoothing and Damping

#### **Smoothing**

Applies double exponential smoothing to translation and rotation of the Rigid Body. Increasing this setting may help smooth out noise in the Rigid Body tracking, but excessive smoothing can introduce latency. Default is 0 (disabled).

#### **Forward Prediction**

Compensate for system latency when tracking of the corresponding Rigid Body by predicting its movement into the future. Please note that predicting further into the future may impact the tracking stability.

#### **Damping**

_\[Advanced]_ When needed, you can damp down translational and/or rotational tracking of a Rigid Body or a Skeleton bone on selected axis.
