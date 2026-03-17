# Edit Tools Pane

In Motive, the Edit Tools pane can be accessed under the [View tab](toolbar-command-bar.md#view) or by clicking [![Tb19.png](https://v30.wiki.optitrack.com/images/0/07/Tb19.png)](https://v30.wiki.optitrack.com/index.php?title=File:Tb19.png) icon on the main toolbar.

The Edit Tools pane contains the functionality to modify 3D data. Four main functions exist: trimming trials, filling gaps, smoothing trajectories and swapping data points. Trimming trials refers to the clearing of data points before and after a gap. Filling gaps is the process of filling in a markers trajectory for each frame that has no data. Smoothing trajectories filters out unwanted noise in the signal. Swapping allows two markers to swap their trajectories.

Read through the [Data Editing](../motive/data-editing.md) page to learn about utilizing the edit tools.

## Tails

![Trim Tails section on the Edit Tools pane.](<../.gitbook/assets/image (1138).png>)

#### **Leading/Trailing Frames**

Default: 3 frames. The Trim Size Leading/Trailing defines how many data points will be deleted before and after a gap.

#### **Smart Trim**

Default: OFF. The Smart Trim feature automatically sets the trimming size based on trajectory spikes near the existing gap. It is often not needed to delete numerous data points before or after a gap, but there are some cases where it's useful to delete more data points in case jitters are introduced from the occlusion. When enabled, this feature will determine whether each end of the gap is suspicious with errors, and delete an appropriate number of frames accordingly. Smart Trim feature will not trim more frames than the defined Leading and Trailing value.

#### **Minimum segment size**

Default: 5 frames. The Minimum Segment Size determines the minimum number of frames required by a trajectory to be modified by the trimming feature. For instance, if a trajectory is continuous only for a number of frames less than the defined minimum segment size, this segment will not be trimmed. Use this setting to define the smallest trajectory that gets.

#### **Gap size threshold**

Default: 2 frames. The Gap Size Threshold defines the minimum size of a gap that is affected by trimming. Any gaps that are smaller than this value are untouched by the trim feature. Use this to limit trimming to only the larger gaps. In general it is best to keep this at or above the default, as trimming is only effective on larger trajectories.

## Gaps

![Gaps section under the Edit Tools pane.](<../.gitbook/assets/image (409).png>)

#### **Previous**

Automatically search through the selected trajectory and highlights the range and moves the cursor to the center of a gap before the current frame.

#### **Next**

Automatically search through the selected trajectory and highlights the range and moves the cursor to the center of a gap after the current frame.

#### **Fill All**

Fills all gaps in the current TAK. If you have a specific frame range selected in the timeline, only the gaps within the selected frame range will be filled.

#### **Interpolation Type**

Sets which interpolation method to be used. Available patterns are constant, linear, cubic, pattern-based, and model-based. For more information, read [Data Editing](../motive/data-editing.md) page

#### **Maximum Gap Size**

The maximum size, in frames, that a gap can be for Motive to fill. Raising this will allow larger gaps to be filled. However, larger gaps may be more prone to incorrect interpolation.

#### **Target**

When using the [_pattern-base_](../motive/data-editing.md) interpolation to fill gaps on a marker's the trajectory, Other reference markers are selected alongside the target marker to interpolate. This _Fill Target_ drop-down menu specifies which marker among the selected markers to set as the target marker to perform the pattern-base interpolation.

## Curves

![Curves function under Edit Tools.](<../.gitbook/assets/image (422).png>)

#### **Smooth All**

Applies smoothing to all frames on all tracks of the current selection in the timeline.

#### **Max. Freq (Hz)**

Determines how strongly your data will be smoothed. The lower the setting, the more smoothed the data will be. High frequencies are present during sharp transitions in the data, such as footplants, but can also be introduced by noise in the data. Commonly used ranges for Filter Cutoff Frequency are 6-12 Hz, but you may want to adjust that up for fast, sharp motions to avoid softening transitions in the motion that need to stay sharp.

## Fragments

![Editor Tools showing fragments method.](<../.gitbook/assets/image (358).png>)

#### **Delete**

Delete all trajectories within the selected frame range that have frames less then the percentage defined in the settings.

#### **Marker with less than**

For all trajectories that have frames shorter than the percentage defined in this setting will be deleted.

## Swaps

![Editor Tools showing Swap Fix Tab.](<../.gitbook/assets/image (387).png>)

#### **Previous**

Jumps to the most recent detected marker swap.

#### **Next**

Jumps to the next detected marker swap.

#### **Marker1 and Marker2**

Select the markers to be swapped.

#### **Swap Direction**

Choose the direction, from the current frame, to apply the swap

#### **Swap**

Swaps the two markers selected in the _Markers to Swap_
