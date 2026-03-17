# Data Export: C3D

## C3D Export

Tracking data can be exported into the C3D file format. C3D (Coordinate 3D) is a binary file format that is widely used especially in biomechanics and motion study applications. Recorded data from external devices, such as force plates and NI-DAQ devices, will be recorded within exported C3D files. Note that common biomechanics applications use a Z-up right-hand coordinate system, whereas Motive uses a Y-up right-hand coordinate system. More details on coordinate systems are described in the later section. Find more about C3D files from [https://www.c3d.org](https://www.c3d.org/).

{% hint style="info" %}
* Force plate data is displayed in Newtons (N).
* Force plate moments are measured in Newton Meters (N m)
{% endhint %}

General Export Options

|               Option              | Description                                                                                                                                                                                                                                                                                                                                                                                |
| :-------------------------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|             Frame Rate            | Number of samples included per every second of exported data.                                                                                                                                                                                                                                                                                                                              |
|            Start Frame            | Start frame of the exported data. You can set it to the recorded first frame of the exported _Take_ (the default option)_,_ to the start of the working range (or scope range), as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) or in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md), or select _Custom_ to enter a specific frame number.  |
|             End Frame             | End frame of the exported data. You can set it to the recorded end frame of the exported _Take_ (the default option)_,_ to the end of the working range (or scope range), as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) of in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md), or select _Custom_ to enter a specific frame number.        |
|               Scale               | Apply scaling to the exported tracking data.                                                                                                                                                                                                                                                                                                                                               |
|               Units               | Sets the length units to use for exported data.                                                                                                                                                                                                                                                                                                                                            |
|          Axis Convention          | Sets the axis convention on exported data. This can be set to a custom convention, or preset conventions for exporting to Visual3D/Motion Monitor (default) or MotionBuilder.                                                                                                                                                                                                              |
| <p>X Axis<br>Y Axis<br>Z Axis</p> | Allows customization of the axis convention in the exported file by determining which positional data to be included in the corresponding data set.                                                                                                                                                                                                                                        |

C3D Specific Export Options

|             Options            | Descriptions                                                                                                                                                                                                                                                             |
| :----------------------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|   Use Zero Based Frame Index   | C3D specification defines first frame as index 1. Some applications import C3D files with first frame starting at index 0. Setting this option to true will add a start frame parameter with value zero in the data header.                                              |
|        Unlabeled Markers       | Includes unlabeled marker data in the exported C3D file. When set to False, the file will contain data for only labeled markers.                                                                                                                                         |
|   Calculated Marker Positions  | Exports the asset's constraints as the marker data.                                                                                                                                                                                                                      |
| Interpolated Fingertip Markers | Includes virtual reconstructions at the fingertips. Available only with Skeletons that support finger tracking (e.g., Baseline + 11 Additional Markers + Fingers (54))                                                                                                   |
|          Use Timecode          | Includes timecode.                                                                                                                                                                                                                                                       |
|    Disable Timecode Subframe   | Export the timecode without using subframes.                                                                                                                                                                                                                             |
|   Rename Unlabeled As \_000X   | Unlabeled markers will have incrementing labels with numbers \_000#.                                                                                                                                                                                                     |
|       Marker Name Syntax       | Choose whether the marker naming syntax uses ":" or "\_" as the name separator. The name separator will be used to separate the asset name and the corresponding marker name in the exported data (e.g. AssetName:MarkerLabel or AssetName\_MarkerLabel or MarkerLabel). |

## C3D Axes

**Common Conventions**

Since Motive uses a different coordinate system than the system used in common biomechanics applications, it is necessary to modify the coordinate axis to a compatible convention in the C3D exporter settings. For biomechanics applications using z-up right-handed convention (e.g., Visual3D), the following changes must be made under the custom axis.

* X axis in Motive should be configured to positive X
* Y axis in Motive should be configured to negative Z
* Z axis in Motive should be configured to positive Y.

This will convert the coordinate axis of the exported data so that the x-axis represents the anteroposterior axis (left/right), the y-axis represents the mediolateral axis (front/back), and the z-axis represents the longitudinal axis (up/down).

![C3D export setting for applications using z-up right-handed coordinate systems.](<../../.gitbook/assets/image (1055) (1) (1) (1).png>)

**MotionBuilder Compatible Axis Convention**

This is a preset convention for exporting C3D files for use in Autodesk MotionBuilder. Even though Motive and MotionBuilder both use the same coordinate system, MotionBuilder assumes biomechanics standards when importing C3D files (negative X axis to positive X axis; positive Z to positive Y; positive Z to positive Y). Accordingly, when exporting C3D files for MotionBuilder use, set the Axis setting to **MotionBuilder Compatible**, and the axes will be exported using the following convention:

* Motive: X axis → Set to negative X → Mobu: X axis
* Motive: Y axis → Set to positive Z → Mobu: Y axis
* Motive: Z axis → Set to positive Y → Mobu: Z axis

![C3D export MotionBuilder compatible axis setting](<../../.gitbook/assets/image (1435).png>)

## Notes on Timecode Export

There is an known behavior where importing C3D data with timecode doesn't accurately show up in MotionBuilder. This happens because MotionBuilder sets the subframe counts in the timecode using the playback rate inside MotionBuilder instead of using the rate of the timecode. When this happens you can set the playback rate in MotionBuilder to be the same as the rate of the timecode generator (e.g. 30 Hz) to get correct timecode. This happens only with C3D import in MotionBuilder, FBX import will work fine without the change to the playback rate.
