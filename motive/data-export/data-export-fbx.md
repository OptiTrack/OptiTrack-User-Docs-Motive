---
description: An overview of the data export options for FBX.
---

# Data Export: FBX

A Motive Body license can export tracking data into FBX files for use in other 3D pipelines. There are two types of FBX files: **Binary FBX** and **ASCII FBX**.

{% hint style="info" %}
**Notes for MotionBuilder Users**

* When exporting tracking data into MotionBuilder in the FBX file format, make sure the exported frame rate is supported in MotionBuilder (Mobu). In Mobu, there is a select set of playback frame rates that are supported, and the rate of the exported FBX file must agree in order to play back the data properly.
* If there is a non-standard frame rate selected that is not supported, the closest supported frame rate is applied.
{% endhint %}

![Mobu supported playback framerates.](<../../.gitbook/assets/image (947).png>)

For more information, please visit [Autodesk Motionbuilder's Documentation Support](https://download.autodesk.com/global/docs/motionbuilder2014/en-us/index.html?url=files/Selecting_time_Custom_frame_rates.htm,topicNumber=d30e40804) site.

## FBX ASCII

{% hint style="danger" %}
Autodesk has discontinued support for FBX ASCII import in MotionBuilder 2018 and above. For alternatives when working in MotionBuilder, please see the [Autodesk MotionBuilder: OptiTrack Optical Plugin](../../plugins/autodesk-motionbuilder/autodesk-motionbuilder-optitrack-optical-plugin.md) page.
{% endhint %}

Exported FBX files in ASCII format can contain reconstructed marker coordinate data as well as 6 Degree of Freedom data for each involved asset depending on the export setting configurations. ASCII files can also be opened and edited using text editor applications.

![](<../../.gitbook/assets/image (920).png>) ![](<../../.gitbook/assets/image (338).png>) ![](<../../.gitbook/assets/image (1412).png>)

### FBX ASCII Export Options

<figure><img src="../../.gitbook/assets/Data Export - FBX ASCII General Options.png" alt=""><figcaption><p>FBX ASCII Format export - General options.</p></figcaption></figure>

#### Frame Rate

Number of samples included per every second of exported data.

#### Start Frame

Start frame of the exported data. You can set it to the recorded first frame of the exported _Take_ (the default option)_,_ to the start of the working range (or scope range), as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) or in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md), or select _Custom_ to enter a specific frame number.&#x20;

#### End Frame

End frame of the exported data. You can set it to the recorded end frame of the exported _Take_ (the default option)_,_ to the end of the working range (or scope range), as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) of in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md), or select _Custom_ to enter a specific frame number.&#x20;

#### Scale

Apply scaling to the exported tracking data

#### Units

Set the unit in exported files.

<figure><img src="../../.gitbook/assets/Data Export - FBX ASCII Specific Options.png" alt=""><figcaption><p>FBX ASCII Format export - Specific options.</p></figcaption></figure>

#### Use Timecode

Includes timecode.

#### Export FBX Actors

Includes FBX Actors in the exported file. Actor is a type of asset used in animation applications (e.g. MotionBuilder) to display imported motions and connect to a character. In order to animate exported actors, associated markers will need to be exported as well.

#### Skeleton Names

Select which skeletons will be exported:  All skeletons, selected skeletons, or custom. The custom option will populate the selection field with the names of all the skeletons in the _Take_. Remove the names of the skeletons you do not wish to include in your export. Names must match the names of actual skeletons in the _Take_ to export. **Note:  This field is only visible if Export FBX Actors is selected.**&#x20;

#### Optical Marker Name Space

Overrides the default name spaces for the optical markers.

#### Name Separator

Choose ":" or "\_" for marker name separator. The name separator will be used to separate the asset name and the corresponding marker name when exporting the data (e.g. AssetName:MarkerLabel or AssetName\_MarkerLabel). When exporting to **Autodesk MotionBuilder**, use "\_" as the separator.

#### Markers

Exports each marker's coordinates.

#### Unlabeled Markers

Includes unlabeled markers.

#### Calculated Marker Positions

Export asset's constraint marker positions as the optical marker data.

#### Interpolated Fingertips

Includes virtual reconstructions at the fingertips. Available only with Skeletons that support finger tracking.

#### Marker Nulls

Exports the location of each marker.

#### Export Skeleton Nulls

Can only be exported when [solved data](../data-recording/data-types.md#solved-data) is recorded for exported Skeleton assets. Exports 6 Degree of Freedom data for every bone segment in selected Skeletons.

#### Rigid Body Nulls

Can only be exported when [solved data](../data-recording/data-types.md#solved-data) is recorded for exported Rigid Body assets. Exports 6 Degree of Freedom data for selected Rigid Bodies. Orientation axes are displayed on the geometrical center of each Rigid Body.

## FBX Binary

Binary FBX files are more compact than ASCII FBX files. Reconstructed 3D marker data is not included within this file type, but selected Skeletons are exported by saving corresponding joint angles and segment lengths. For Rigid Bodies, positions and orientations at the defined Rigid Body origin are exported.

![Exported skeletons.](<../../.gitbook/assets/image (1413).png>)

### Tips for Exporting Skeletons

* Make sure _Individual Assets_ is selected when using the _Remove Bone Name Prefixes_ option to export multiple skeletons, otherwise only one skeleton will be exported.

<figure><img src="../../.gitbook/assets/hand bones.png" alt=""><figcaption><p>A hand with tracked bones.</p></figcaption></figure>

* To include **fingertips** as nulls (Locators) in the export, the skeleton must contain hand bones. Select the following export options to export this data:
  * Marker Nulls&#x20;
  * Unlabeled Markers
  * Interpolated Finger Tips

### FBX Binary Export Options

<figure><img src="../../.gitbook/assets/Data Export - FBX  Binary General Options.png" alt=""><figcaption></figcaption></figure>

#### Frame Rate

Number of samples included per every second of exported data.

#### Start Frame

Start frame of the exported data. You can set it to the recorded first frame of the exported _Take_ (the default option)_,_ to the start of the working range (or scope range), as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) or in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md), or select _Custom_ to enter a specific frame number.&#x20;

#### End Frame

End frame of the exported data. You can set it to the recorded end frame of the exported _Take_ (the default option)_,_ to the end of the working range (or scope range), as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) of in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md), or select _Custom_ to enter a specific frame number.&#x20;

#### Scale

Apply scaling to the exported tracking data.

#### Units

Sets the unit for exported segment lengths.

<figure><img src="../../.gitbook/assets/Data Export - FBX  Binary Specific Options.png" alt=""><figcaption></figcaption></figure>

#### Use Timecode

Includes timecode.

#### Export Skeletons

Export Skeleton nulls. Please note that the [solved data](../data-recording/data-types.md#solved-data) must be recorded for Skeleton bone tracking data to be exported. It exports 6 Degree of Freedom data for every bone segment in exported Skeletons.

#### Skeleton Names

Select which skeletons will be exported:  All skeletons, selected skeletons, or custom. The custom option will populate the selection field with the names of all the skeletons in the _Take_. Remove the names of the skeletons you do not wish to include in your export. Names must match the names of actual skeletons in the _Take_ to export.

#### Name Separator

Choose ":" or "\_" for marker name separator. The name separator will be used to separate the asset name and the corresponding marker name when exporting the data (e.g. AssetName:MarkerLabel or AssetName\_MarkerLabel). When exporting to **Autodesk Motion Builder**, use "\_" as the separator.

#### Bone Naming Convention

Select Motive, FBX, or UnrealEngine.

#### Rigid Body Nulls

Can only be exported when [solved data](../data-recording/data-types.md#solved-data) is recorded for exported Rigid Body assets. Exports 6 Degree of Freedom data for selected Rigid Bodies. Orientation axes are displayed on the geometrical center of each Rigid Body.

#### Rigid Body Names

Names of the Rigid Bodies to export into the FBX binary file as 6 DoF nulls.

#### Markerset Nulls

Can only be exported when [solved data](../data-recording/data-types.md#solved-data) is recorded for exported trained markerset assets. Exports 6 Degree of Freedom data for selected assets. Orientation axes are displayed on the geometrical center of each markerset.

#### Markerset Names

Select which markersets will be exported:  All markersets, selected markersets, or custom. The custom option will populate the selection field with the names of all the markersets in the _Take_. Remove the names of the markersets you do not wish to include in your export. Names must match the names of actual markersets in the _Take_ to export.

#### Markers

Markers can be exported as Opticals or Nulls. The export of Markers must be enabled to export interpolated finger tip data.&#x20;

* **Opticals** exports marker data in a format that includes animation data such as constraints information. Select this option when exporting for animation in MotionBuilder.&#x20;
* **Nulls** exports the location of each marker.&#x20;

When either option is selected, additional options become available:&#x20;

<figure><img src="../../.gitbook/assets/Data Export - FBX Binary Export Markers Opticals.png" alt=""><figcaption></figcaption></figure>

#### Unlabeled Markers

Includes unlabeled markers. This setting must be enabled to export interpolated finger tip data.&#x20;

#### Move Gaps to Origin

MotionBuilder interpolates marker gaps, which includes unwanted frame data in some pipelines. This option facilitates the removal of gaps by moving them to the origin, where the user simply deletes any marker in every frame where it is at the origin of the world.

#### Interpolated Fingertips

Includes virtual reconstructions at the fingertips. Available only with Skeletons that support finger tracking. Both Marker Nulls and Unlabeled Markers must be enabled also.

#### Exclude Fingers

When set to true, exported skeletons will not include the fingers, if they are tracked in the _Take_ file.&#x20;

#### Cameras

Select the cameras to include in your export. Options are _All Color Cameras_, _All Cameras_, or _none_ (default).&#x20;

#### Skeleton Stick Mesh

Select this option if exporting to a game engine that requires an FBX mesh asset to apply tracked skeletons to other characters for retargeting purposes.&#x20;

#### Individual Assets

Exports the data for each asset into a separate file.

#### Remove Bone Name Prefixes

Removes the skeleton name prefix from the bones to create skeletons that are easily retargetable and interchangeable. Use when exporting into Unreal Engine.
