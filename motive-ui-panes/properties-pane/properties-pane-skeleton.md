# Properties Pane: Skeleton

Skeleton properties determine how Skeleton assets are tracked and displayed in Motive.

To view related properties, select a Skeleton asset in the [Assets pane](../assets-pane.md) or in the 3D viewport, and the corresponding properties will be listed under the [Properties pane](./). These properties can be modified both in Live and Edit mode. Default creation properties are listed under the [Application Settings](../settings/).

{% hint style="info" %}
**Advanced Settings**

The Properties: Skeleton contains _advanced settings_ that are hidden by default. Access these settings by going to the menu on the top-right corner of the pane and clicking _Show Advanced_ and all of the settings, including the advanced settings, will be listed under the pane.

The list of advanced settings can also be customized to show only the settings that are needed specifically for your capture application. To do so, go the pane menu and click _Edit Advanced_, and uncheck the settings that you wish to be listed in the pane by default. One all desired settings are unchecked, click _Done Editing_ to apply the customized configurations.
{% endhint %}

![](<../../.gitbook/assets/image (1007) (1) (1) (1) (1) (1) (1) (9).png>)

## Skeleton Properties

![Properties of selected Skeleton asset.](<../../.gitbook/assets/image (953).png>)

### General Settings

#### **Name**

Shows the name of selected Skeleton asset.

#### **Enables**

Enables/disables both tracking of the selecting Skeleton and its visibility under the perspective viewport.

#### **Minimum Markers to Boot**

The minimum number of markers that must be tracked and labeled in order for a Rigid Body asset, or each Skeleton bone, to be booted or first tracked.

#### **Minimum Markers to Continue**

The minimum number of markers that must be tracked and labeled in order for a Rigid Body asset, or each Skeleton bone, to continue to be tracked after the initial boot.

#### **Rotation Order**

_\[Advanced]_ Euler angle rotation order used for calculating the bone hierarchy.

### Visuals

#### **Label**

Selects whether or not to display the Skeleton name in the 3D Perspective View.

#### **Visuals**

Selects how the Skeleton will be shown in the 3D perspective view.

* Segment: Displays Skeleton as individual Skeleton segments.
* Avatar (male): Displays Skeleton as a male avatar.
* Avatar (female): Displays Skeleton as a female avatar.

#### **Color**

Sets the color of the Skeleton.

#### **Quality Visual**

This feature is supported in Live mode and 2D mode only. When enabled, the color of the Skeleton segments will change whenever there are tracking errors.

#### **Bones**

Show or hide Skeleton bones.

#### **Bone Orientation**

_\[Advanced]_ Displays orientation axes of each segments in the Skeleton.

#### **Asset Model Markers**

_\[Advanced]_ Shows the Asset Model Markers as transparent spheres on each Skeleton segment. The asset mode markers are the expected marker locations according to the Skeleton solve.

#### **Asset Model Lines**

_\[Advanced]_ Draws lines between labeled Rigid Body or Skeleton markers and corresponding expected marker locations. This helps to visualize the offset distance between actual marker locations and the asset model markers.

#### **Marker Lines**

_\[Advanced]_ Displays lines between each Skeleton markers and their associated Skeleton segments.

### Smoothing and Damping

#### **Smoothing**

Applied double-exponential smoothing to translation and rotation of a Rigid Body or a skeletal bone. Disabled at 0.

#### **Forward Prediction**

Compensate for system latency by predicting bone movements into the future. For this feature to work best, smoothing needs to be applied as well. Disabled at 0.

#### **Damping**

_\[Advanced]_ When needed, you can damp down translational and/or rotational tracking of a Rigid Body or a Skeleton bone on selected axis.
