# Settings: Assets

## **Overview**

The Assets tab in the application settings panel is where you can configure the creation properties for Rigid Body and Skeleton assets. In other words, all of the settings configured in this tab will be assigned to the Rigid Body and Skeleton that are newly created in Motive.

![Assets tab in Application Settings.](<../../.gitbook/assets/image (317).png>)

## Rigid Bodies Basic Settings

A list of the default Rigid Body creation properties is listed under the _Rigid Bodies_ tab. These properties are applied to only Rigid Bodies that are newly created after the properties have been modified. For descriptions of the Rigid Body properties, please read through the [Properties: Rigid Body](../properties-pane/properties-pane-rigid-body.md) page.

{% hint style="info" %}
Note that this is the default _creation_ properties. Asset specific Rigid Body properties are modified directly from the [Properties pane](../properties-pane/properties-pane-rigid-body.md).
{% endhint %}

### Rigid Body Creation Properties

#### Default Name (Default: RigidBody)

You can change the naming convention of Rigid Bodies when they are first created. For instance, if it is set to RigidBody, the first Rigid Body will be named RigidBody when first created. Any subsequent Rigid Bodies will be named RigidBody 001, RigidBody 002, and so on.

#### Streaming ID

User definable ID. When streaming tracking data, this ID can be used as a reference to specific Rigid Body assets.

#### Minimum Markers to Boot

The minimum number of markers that must be labeled in order for the respective asset to be booted.

#### Minimum Markers to Continue

The minimum number of markers that must be labeled in order for the respective asset to be tracked.

#### Smoothing

Applies double exponential smoothing to translation and rotation. Disabled at 0.

#### Forward Prediction

Compensate for system latency by predicting movement into the future.

{% hint style="info" %}
For this feature to work best, smoothing needs to be applied as well.
{% endhint %}

### Visuals

#### Label

Toggle 'On' to enable. Displays asset's name over the corresponding skeleton in the 3D viewport.

#### Creation Color

Select the default color a Rigid Body will have upon creation. Select 'Rainbow' to cycle through a different color each time a new Rigid Body is created.

#### Bone Position History

When enabled this shows a visual trail behind a Rigid Body's pivot point. You can change the History Length, which will determine how long the trail persists before retracting.

#### Visual

Shows a Rigid Body's visual overlay. This is by default Enabled. If disabled, the Rigid Body will only appear as individual markers with the Rigid Body's color and pivot marker.

#### Bones

When enabled for Rigid Bodies, this will display the Rigid Body's pivot point.

#### Marker Constraints

Shows the transparent sphere that represents where an asset first searches for markers, i.e. the Marker Constraints.

#### Replace Geometry

When enabled and a valid geometric model is loaded, the model will draw instead of the Rigid Body.

## Rigid Bodies Advanced Settings

### Rigid Body Creation Properties

#### Deflection Ratio

Allows the asset to deform more or less to accommodate markers that don't fix the model. High values will allow assets to fit onto markers that don't match the model as well.

## Skeletons Basic Settings

A list of the default Skeleton display properties for newly created Skeletons is listed under the _Skeletons_ tab. These properties are applied to only Skeleton assets that are newly created after the properties have been modified. For descriptions of the Skeleton properties, please read through the [Properties: Skeleton](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive-ui-panes/properties-pane/properties-pane-Skeleton.md) page.

{% hint style="info" %}
Note that this is the default _creation_ properties. Asset-specific Skeleton properties are modified directly from the [Properties pane](../properties-pane/).
{% endhint %}

### Skeleton Creation Properties

#### **Straight Arms**

Creates the Skeleton with arms straight even when arm markers are not straight.

#### **Straight Legs**

Creates the Skeleton with straight knee joints even when leg markers are not straight.

#### **Feet On Floor**

Creates the Skeleton with feet planted on the ground level.

#### **Head Upright**

Creates the Skeleton with heads upright irrespective of head marker locations.

#### **Height Marker**

Force the solver so that the height of the created Skeleton aligns with the top head marker.

#### **Vertical Hand Adjustment**

Height offset applied to hands to account for markers placed above the write and knuckle joints.

### Visuals

Same as the Rigid Body visuals above:

* Label
* Creation Color
* Bones
* Marker Constraints

#### Quality Visual

Changes the color of the skeleton visual to red when there are no markers contributing to a joint.

## Skeleton Advanced Settings

### Visuals

#### Bone Orientation

Display Coordinate axes of each joint.

#### Marker Constraints

Displays the lines between labeled skeleton markers and corresponding expected marker locations.

#### Marker Lines

Displays lines between skeleton markers and their joint locations.
