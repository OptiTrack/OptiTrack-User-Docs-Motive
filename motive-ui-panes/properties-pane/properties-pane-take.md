# Properties Pane: Take

When a [_Take_](../../motive/motive-basics.md#file-management) is selected from the [Data pane](../data-pane.md), related information will be displayed in the [Properties pane](./).

From the Properties pane, you can get the general information about the _Take_, including the total number of recorded frames, capture data/time, and the list of assets involved in the recording. Also, when needed, the solver settings that were used in the recorded TAK can be modified, and these changes will be applied when performing post-processing reconstruction.

## General

![Take properties listed under the Properties pane.](<../../.gitbook/assets/image (974).png>)

#### **Name**

Take name

#### **Frame Rate**

The camera frame rate in which the take was captured. The Take file will contain the corresponding number of frames for each second.

#### **Start Frame**

The frame ID of the first frame saved on the _Take_.

#### **End Frame**

**T**he frame ID of the last frame saved on the _Take_.

#### **Start Time**

A timestamp of when the recording was first captured started.

#### **End Time**

A timestamp of when the recording was ended.

#### **Assets**

Names of assets that are included in the _Take_

#### **Notes**

Comments regarding the take can be noted here for additional information.

#### **Best**

Marks the best take. Takes that are marked as best can also be accessed via [Motive Batch Processor](../../motive/motive-batch-processor.md) scripts.

#### **Capture Data/Time**

Date and time when the capture was recorded.

#### **Captured in Version**

The version of Motive which the _Take_ was recorded in. (This applies only to _Takes_ that were captured in versions 1.10 or above)

#### **Captured in Build**

The build of Motive which the _Take_ was recorded in.

#### **Health State**

The data quality of the _Take_ which can be flagged by users.

#### **Progress**

Progress indicator for showing how into the post-processing workflow that this Take has made.

## Calibration Info

Camera system calibration details for the selected _Take_. _Takes_ recorded in older versions of Motive may not contain this data.

#### **Calibration Time Stamp**

Shows when the cameras were calibrated.

#### **Residual Mean Error**

Shows mean [residual](../../motive/reconstruction-and-2d-mode.md) offset value during calibration.

#### **Residual 50/95/99 Percentile Error**

Displays percentile distribution of the [residual](../../motive/reconstruction-and-2d-mode.md) errors.

#### **Wand Mean Error**

Displays a mean error value of the detected wand length samples throughout the wanding process.

#### **Wand 50/95/99**

Displays percentile distribution of the wand errors.

#### **Calibration Wand**

Shows what type of wand was used: Standard, Active, or Micron series.

#### **Wand Length**

Displays the length of the calibration wand used for the capture.

#### **Wand Center Offset**

Distance from one of the end markers to the center marker, specifically the shorter segment.

## Camera Filters - Software

The camera filter settings in the _Take_ properties determine which IR lights from the recorded 2D camera data contributes to the [post-processing reconstruction pipeline](../../motive/reconstruction-and-2d-mode.md#post-processing-reconstruction) when re-calulating the 3D data when needed.

{% hint style="info" %}
For more information on these settings in Live mode, please refer to the [Application Settings: Live Pipeline](../settings/settings-live-pipeline.md) page.
{% endhint %}

## Solver/Reconstruction Settings

The Solver/Reconstruction settings under the _Take_ properties are the 3D data solver parameters that were used to obtain the [3D data](../../motive/data-recording/data-types.md) saved in the _Take_ file. In Edit mode, you can change these parameters and perform the [post-processing reconstruction pipeline](../../motive/reconstruction-and-2d-mode.md#post-processing-reconstruction) to obtain a new set of 3D data with the modified parameters.

{% hint style="info" %}
For more information on these settings in Live mode, please refer to the [Application Settings: Live Pipeline](../settings/settings-live-pipeline.md) page.
{% endhint %}
