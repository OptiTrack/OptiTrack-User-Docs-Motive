# Data Export: FBX

A Motive Body license can export tracking data into FBX files for use in other 3D pipelines. There are two types of FBX files: **Binary FBX** and **ASCII FBX**.

{% hint style="info" %}
**Notes for MotionBuilder Users**

* When exporting tracking data into MotionBuilder in the FBX file format, make sure the exported frame rate is supported in MotionBuilder (Mobu). In Mobu, there is a select set of playback frame rate that are supported, and the rate of the exported FBX file must agree in order to play back the data properly.
* If there is a non-standard frame rate selected that is not supported, the closest supported frame rate is applied.
{% endhint %}

![Mobu supported playback framerates.](<../../.gitbook/assets/image (411).png>)

For more information, please visit [Autodesk Motionbuilder's Documentation Support](https://download.autodesk.com/global/docs/motionbuilder2014/en-us/index.html?url=files/Selecting_time_Custom_frame_rates.htm,topicNumber=d30e40804) site.

## FBX ASCII

{% hint style="danger" %}
Autodesk has discontinued support for FBX ASCII import in MotionBuilder 2018 and above. For alternatives when working in MotionBuilder, please see the [Autodesk MotionBuilder: OptiTrack Optical Plugin](../../plugins/autodesk-motionbuilder/autodesk-motionbuilder-optitrack-optical-plugin.md) page.
{% endhint %}

Exported FBX files in ASCII format can contain reconstructed marker coordinate data as well as 6 Degree of Freedom data for each involved asset depending on the export setting configurations. ASCII files can also be opened and edited using text editor applications.

![](<../../.gitbook/assets/image (479).png>) ![](<../../.gitbook/assets/image (351).png>) ![](<../../.gitbook/assets/image (360).png>)

FBX ASCII Export Options

|           Options           | Description                                                                                                                                                                                                                                                                                                           |
| :-------------------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|          Frame Rate         | Number of samples included per every second of exported data.                                                                                                                                                                                                                                                         |
|         Start Frame         | Start frame of the exported data. You can either set it to the recorded first frame of the exported _Take_ or to the start of the working range, or scope range, as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) or in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md). |
|          End Frame          | End frame of the exported data. You can either set it to the recorded end frame of the exported _Take_ or to the end of the working range, or scope range, as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) of in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md).       |
|            Scale            | Apply scaling to the exported tracking data.                                                                                                                                                                                                                                                                          |
|            Units            | Set the unit in exported files.                                                                                                                                                                                                                                                                                       |
|         Use Timecode        | Includes timecode.                                                                                                                                                                                                                                                                                                    |
|      Export FBX Actors      | Includes FBX Actors in the exported file. Actor is a type of asset used in animation applications (e.g. MotionBuilder) to display imported motions and connect to a character. In order to animate exported actors, associated markers will need to be exported as well.                                              |
|  Optical Marker Name Space  | Overrides the default name spaces for the optical markers.                                                                                                                                                                                                                                                            |
|    Marker Name Separator    | Choose ":" or "\_" for marker name separator. The name separator will be used to separate the asset name and the corresponding marker name when exporting the data (e.g. AssetName:MarkerLabel or AssetName\_MarkerLabel). When exporting to **Autodesk Motion Builder**, use "\_" as the separator.                  |
|           Markers           | Export each marker coordinates.                                                                                                                                                                                                                                                                                       |
|      Unlabeled Markers      | Includes unlabeled markers.                                                                                                                                                                                                                                                                                           |
| Calculated Marker Positions | Export asset's constraint marker positions as the optical marker data.                                                                                                                                                                                                                                                |
|   Interpolated Fingertips   | Includes virtual reconstructions at the finger tips. Available only with Skeletons that support finger tracking.                                                                                                                                                                                                      |
|         Marker Nulls        | Exports locations of each marker.                                                                                                                                                                                                                                                                                     |
|    Export Skeleton Nulls    | Can only be exported when [solved data](../data-recording/data-types.md#solved-data) is recorded for exported Skeleton assets. Exports 6 Degree of Freedom data for every bone segment in selected Skeletons.                                                                                                         |
|       Rigid Body Nulls      | Can only be exported when [solved data](../data-recording/data-types.md#solved-data) is recorded for exported Rigid Body assets. Exports 6 Degree of Freedom data for selected Rigid Bodies. Orientation axes are displayed on the geometrical center of each Rigid Body.                                             |

## FBX Binary

Binary FBX files are more compact than ASCII FBX files. Reconstructed 3D marker data is not included within this file type, but selected Skeletons are exported by saving corresponding joint angles and segment lengths. For Rigid Bodies, positions and orientations at the defined Rigid Body origin are exported.

![](<../../.gitbook/assets/image (303).png>)

FBX Binary Export Options

|      Options     | Descriptions                                                                                                                                                                                                                                                                                                          |
| :--------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|    Frame Rate    | Number of samples included per every second of exported data.                                                                                                                                                                                                                                                         |
|    Start Frame   | Start frame of the exported data. You can either set it to the recorded first frame of the exported _Take_ or to the start of the working range, or scope range, as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) or in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md). |
|     End Frame    | End frame of the exported data. You can either set it to the recorded end frame of the exported _Take_ or to the end of the working range, or scope range, as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) of in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md).       |
|       Scale      | Apply scaling to the exported tracking data.                                                                                                                                                                                                                                                                          |
|       Units      | Sets the unit for exported segment lengths.                                                                                                                                                                                                                                                                           |
|   Use Timecode   | Includes timecode.                                                                                                                                                                                                                                                                                                    |
| Export Skeletons | Export Skeleton nulls. Please note that the [solved data](../data-recording/data-types.md#solved-data) must be recorded for Skeleton bone tracking data to be exported. It exports 6 Degree of Freedom data for every bone segment in selected Skeletons.                                                             |
|  Skeleton Names  | Names of Skeletons that will be exported into the FBX binary file.                                                                                                                                                                                                                                                    |
|  Name Separator  | Choose ":" or "\_" for marker name separator. The name separator will be used to separate the asset name and the corresponding marker name when exporting the data (e.g. AssetName:MarkerLabel or AssetName\_MarkerLabel). When exporting to **Autodesk Motion Builder**, use "\_" as the separator.                  |
| Rigid Body Nulls | Can only be exported when [solved data](../data-recording/data-types.md#solved-data) is recorded for exported Rigid Body assets. Exports 6 Degree of Freedom data for selected Rigid Bodies. Orientation axes are displayed on the geometrical center of each Rigid Body.                                             |
| Rigid Body Names | Names of the Rigid Bodies to export into the FBX binary file as 6 DoF nulls.                                                                                                                                                                                                                                          |
|   Marker Nulls   | Exports locations of each marker.                                                                                                                                                                                                                                                                                     |
