# For Visual3D Users

This page contains useful information for users who are outputting motion capture data from Motive into Visual3D.

For more information on Visual3D: [C-Motion wiki](http://www.c-motion.com/v3dwiki/index.php/Visual3D_Overview)

![Visual3D biomechanics analysis software provided by C-Motion.](<../.gitbook/assets/image (828).png>)

## C3D Export

Tracking data can be exported into the C3D file format. C3D (Coordinate 3D) is a binary file format that is widely used especially in biomechanics and motion study applications. Recorded data from external devices, such as force plates and NI-DAQ devices, will be recorded within exported C3D files. Note that common biomechanics applications use a Z-up right-hand coordinate system, whereas Motive uses a Y-up right-hand coordinate system. More details on coordinate systems are described in the later section. Find more about C3D files from [https://www.c3d.org](https://www.c3d.org/).

General Export Options

|               Option              | Description                                                                                                                                                                                                                                                                                                     |
| :-------------------------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|             Frame Rate            | Number of samples included per every second of exported data.                                                                                                                                                                                                                                                   |
|            Start Frame            | Start frame of the exported data. You can either set it to the recorded first frame of the exported _Take_ or to the start of the working range, or scope range, as configured under the [Control Deck](../motive-ui-panes/control-deck.md) or in the [Graph View pane](../motive-ui-panes/graph-view-pane.md). |
|             End Frame             | End frame of the exported data. You can either set it to the recorded end frame of the exported _Take_ or to the end of the working range, or scope range, as configured under the [Control Deck](../motive-ui-panes/control-deck.md) of in the [Graph View pane](../motive-ui-panes/graph-view-pane.md).       |
|               Scale               | Apply scaling to the exported tracking data.                                                                                                                                                                                                                                                                    |
|               Units               | Sets the length units to use for exported data.                                                                                                                                                                                                                                                                 |
|          Axis Convention          | Sets the axis convention on exported data. This can be set to a custom convention, or preset convetions for exporting to Motion Builder or Visual3D/Motion Monitor.                                                                                                                                             |
| <p>X Axis<br>Y Axis<br>Z Axis</p> | Allows customization of the axis convention in the exported file by determining which positional data to be included in the corresponding data set.                                                                                                                                                             |

C3D Specific Export Options

|           Options          | Descriptions                                                                                                                                                                                                                                                             |
| :------------------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Use Zero Based Frame Index | C3D specification defines first frame as index 1. Some applications import C3D files with first frame starting at index 0. Setting this option to true will add a start frame parameter with value zero in the data header.                                              |
|  Export Unlabeled Markers  | Includes unlabeled marker data in the exported C3D file. When set to False, the file will contain data for only labeled markers.                                                                                                                                         |
|  Export Finger Tip Markers | Includes virtual reconstructions at the finger tips. Available only with Skeletons that support finger tracking (e.g. Baseline + 11 Additional Markers + Fingers (54))                                                                                                   |
|        Use Timecode        | Includes timecode.                                                                                                                                                                                                                                                       |
| Rename Unlabeled As \_000X | Unlabeled markers will have incrementing labels with numbers \_000#.                                                                                                                                                                                                     |
|     Marker Name Syntax     | Choose whether the marker naming syntax uses ":" or "\_" as the name separator. The name separator will be used to separate the asset name and the corresponding marker name in the exported data (e.g. AssetName:MarkerLabel or AssetName\_MarkerLabel or MarkerLabel). |

## C3D Axes

**Common Conventions**

Since Motive uses a different coordinate system than the system used in common biomechanics applications, it is necessary to modify the coordinate axis to a compatible convention in the C3D exporter settings. For biomechanics applications using z-up right-handed convention (e.g. Visual3D), the following changes must be made under the custom axis.

* X axis in Motive should be configured to positive X
* Y axis in Motive should be configured to negative Z
* Z axis in Motive should be configured to positive Y.

This will convert the coordinate axis of the exported data so that the x-axis represents the anteroposterior axis (left/right), the y-axis represents the mediolateral axis (front/back), and the z-axis represents the longitudinal axis (up/down).

![C3D export setting for applications using z-up right-handed coordinate systems.](<../.gitbook/assets/image (1055) (1) (1) (1) (1) (1) (1) (2).png>)

**MotionBuilder Compatible Axis Convention**

This is a preset convention for exporting C3D files for use in Autodesk MotionBuilder. Even though Motive and MotionBuilder both use the same coordinate system, MotionBuilder assumes biomechanics standards when importing C3D files (negative X axis to positive X axis; positive Z to positive Y; positive Z to positive Y). Accordingly, when exporting C3D files for MotionBuilder use, set the Axis setting to **MotionBuilder Compatible**, and the axes will be exported using the following convention:

* Motive: X axis → Set to negative X → Mobu: X axis
* Motive: Y axis → Set to positive Z → Mobu: Y axis
* Motive: Z axis → Set to positive Y → Mobu: Z axis

![C3D export MotionBuilder compatible axis setting](<../.gitbook/assets/image (401).png>)

## Notes on Timecode Export

There is an known behavior where importing C3D data with timecode doesn't accurately show up in MotionBuilder. This happens because MotionBuilder sets the subframe counts in the timecode using the playback rate inside MotionBuilder instead of using the rate of the timecode. When this happens you can set the playback rate in MotionBuilder to be the same as the rate of the timecode generator (e.g. 30 Hz) to get correct timecode. This happens only with C3D import in MotionBuilder, FBX import will work fine without the change to the playback rate.

## Streaming to Visual3D

Streaming tracking data into the Visual3D requires 2-step pipelines. Motive streams tracking data first into the _Visual3D Server_, and then from this application the data is streamed into Visual3D.

![Data streaming settings of Motive for outputting data into Visual3D.](<../.gitbook/assets/image (1065).png>)

**On Motive**

When streaming into Visual3D Server, set the stream Visual3D Compatible to true in the [Data Streaming Pane](../motive/data-streaming.md). This will modify the axis of the streamed data. This setting is configured as the advanced setting by default. Click _Show Advanced_ to bring up this setting.

{% hint style="info" %}
**Advanced Settings**

The For Visual3D Users contains _advanced settings_ that are hidden by default. Access these settings by going to the menu on the top-right corner of the pane and clicking _Show Advanced_ and all of the settings, including the advanced settings, will be listed under the pane.

The list of advanced settings can also be customized to show only the settings that are needed specifically for your capture application. To do so, go the pane menu and click _Edit Advanced_, and uncheck the settings that you wish to be listed in the pane by default. One all desired settings are unchecked, click _Done Editing_ to apply the customized configurations.
{% endhint %}

![](<../.gitbook/assets/image (1007) (1) (1) (1) (1) (1) (1) (4).png>)

**On Visual3D Server/Visual3D**

Please refer to Visua3D docmentation for more information about the receiving streamed data in visual 3D. For more info: [Visual3D Server to Visual3D](http://www.c-motion.com/v3dwiki/index.php/Visual3D_Server_To_Visual3D).

## V3S: Correcting Sync Offset

The following pipeline commands can be used in Visual3D to accommodate systematic synchronization offset frames between recorded mocap tracking data and another data. Save and import these commands into the Visual3D pipeline dialogue to execute the commands. For more information on Visual3D pipeline commands, refer to the c-motion wiki ([https://www.c-motion.com/v3dwiki/index.php/Visual3D\_Pipeline](https://www.c-motion.com/v3dwiki/index.php/Visual3D_Pipeline)).

**For a Single C3D**

```
Prompt_For_Pipeline_Parameter_Value
/PIPELINE_PARAMETER_NAME=FRAME_OFFSET
/PROMPT=Please enter the frame offset, at POINT rate.
! /DATA_TYPE=
! /DEFAULT_VALUE=
! /USE_POSSIBLE_VALUES=FALSE
! /POSSIBLE_VALUES=
! /USE_UNITS=FALSE
! /DEFAULT_UNITS=
! /USE_POSSIBLE_UNITS=FALSE
! /POSSIBLE_UNITS=
! /CONVERSIONS=
;

Set_Use_Processed_Analog
 /USE_PROCESSED=TRUE
;

Shift_Frames
/SIGNAL_TYPES=ANALOG
! /SIGNAL_FOLDER=ORIGINAL
! /SIGNAL_NAMES=
! /RESULT_FOLDER=PROCESSED
! /RESULT_SUFFIX=
 /FRAME_SHIFT=-&::FRAME_OFFSET
 /REPLACEMENT_VALUE=0
;
Recalc
;
```

**For Multiple C3D Trials**

```
File_New

;

File_Open
! /FILE_NAME=
! /SUFFIX=
 /SET_PROMPT=File .C3D files with data offsets
 /FILTER=c3d
;

Set_Pipeline_Parameter_To_List_Of_Tagged_Files
/PARAMETER_NAME=FILE_LIST
/TAG_NAME=ALL_FILES
! /GET_CURRENT_SELECTED_FILES=false
! /USE_SHORT_FILENAMES=false
;

Set_Use_Processed_Analog
 /USE_PROCESSED=TRUE
;

Switch_to_Event_Processing_Mode

;

For_Each
/ITERATION_PARAMETER_NAME=FRAME_OFFSET_CYCLE
! /ITERATION_PARAMETER_COUNT_NAME=
 /ITEMS=::FILE_LIST
;

Select_Active_File
/FILE_NAME=::FRAME_OFFSET_CYCLE
! /QUERY=
;

Pipeline_Breakpoint
/PAUSE_MESSAGE=Confirm the exact number frame count offset between the POINT and ANALOG data for the current file.
Click "Resume Pipeline" when ready.
;

Prompt_For_Pipeline_Parameter_Value
/PIPELINE_PARAMETER_NAME=FRAME_OFFSET
/PROMPT=Please enter the frame offset, at POINT rate. NEGATIVE offset = Late ANALOG data
! /DATA_TYPE=
! /DEFAULT_VALUE=
! /USE_POSSIBLE_VALUES=FALSE
! /POSSIBLE_VALUES=
! /USE_UNITS=FALSE
! /DEFAULT_UNITS=
! /USE_POSSIBLE_UNITS=FALSE
! /POSSIBLE_UNITS=
! /CONVERSIONS=
;

Evaluate_Expression
/EXPRESSION=(PARAMETERS::ANALOG::RATE/PARAMETERS::POINT::RATE)
! /SIGNAL_TYPES=
! /SIGNAL_FOLDER=ORIGINAL
! /SIGNAL_NAMES=
! /RESULT_TYPES=DERIVED
! /RESULT_FOLDERS=PROCESSED
 /RESULT_NAME=RATE_RATIO
! /APPLY_AS_SUFFIX_TO_SIGNAL_NAME=FALSE
;

Shift_Frames
/SIGNAL_TYPES=ANALOG
! /SIGNAL_FOLDER=ORIGINAL
! /SIGNAL_NAMES=
! /RESULT_FOLDER=PROCESSED
! /RESULT_SUFFIX=
 /FRAME_SHIFT=::FRAME_OFFSET&*&DERIVED::PROCESSED::RATE_RATIO
 /REPLACEMENT_VALUE=0
;

Recalc

;
```
