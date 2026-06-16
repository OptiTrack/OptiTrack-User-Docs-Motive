---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/data-editing
---

# Data Editing

Labeling Pane in Motive\
The [Edit Tools](../motive-ui-panes/edit-tools-pane.md) in Motive enables users to post-process tracking errors from recorded capture data. There are multiple editing methods available, and you need to clearly understand them in order to properly fix errors in captured trajectories. Tracking errors are sometimes inevitable due to the nature of marker-based motion capture systems. Thus, understanding the functionality of the editing tools is essential. Before getting into details, note that the post-editing of the motion capture data often takes a lot of time and effort. All captured frames must be examined precisely and corrections must be made for each error discovered. Furthermore, some of the editing tools implement mathematical modifications to marker trajectories, and these tools may introduce discrepancies if misused. For these reasons, we recommend [optimizing the capture setup](../hardware/) so that tracking errors are prevented in the first place.

\
Common tracking errors include marker occlusions and labeling errors. Labeling errors include **unlabeled markers**, **mislabeled markers**, and **label swaps**. Fortunately, label errors can be corrected simply by reassigning proper labels to markers. Markers may be hindered from camera views during capture. In this case, the markers will not be reconstructed into 3D space and introduce a gap in the trajectory, which are referred to as marker occlusions. **Marker occlusions** are critical because the trajectory data is not collected at all, and retaking the capture could be necessary if the missing marker is significant to the application. For these occluded markers, Edit Tools also provide interpolation pipelines to model the occluded trajectory using other captured data points. Read through this page to understand each of data editing methods in detail.

Steps in Editing

***

**General Steps**

1. Skim through the overall frames in a Take to get an idea of which frames and markers need to be cleaned up.
2. Refer to the [Labels pane](../motive-ui-panes/labels-pane.md) and inspect gap percentages in each marker.
3. Select a marker that is often occluded or misplaced.
4. Look through the frames in the [Graph pane](../motive-ui-panes/graph-view-pane.md), and inspect the gaps in the trajectory.
5. For each gap in frames, look for an unlabeled marker at the expected location near the solved marker position. Re-assign the proper marker label if the unlabeled marker exists.
6. Use Trim Tails feature to trim both ends of the trajectory in each gap. It trims off a few frames adjacent to the gap where tracking errors might exist. This prepares occluded trajectories for Gap Filling.
7. Find the gaps to be filled, and use the Fill Gaps feature to model the estimated trajectories for occluded markers.
8. Re-Solve assets to update the solve from the edited marker data

## Deleting Frames

In some cases, you may wish to delete 3D data for certain markers in a _Take_ file. For example, you may wish to delete corrupt 3D reconstructions or trim out erroneous movements from the 3D data to improve the data quality. In the [Edit mode](../motive-ui-panes/control-deck.md), reconstructed 3D markers can be deleted for selected range of frames. To delete a 3D marker, first select 3D markers that you wish to delete, and press the **Delete key**, and they will be completely erased from the 3D data. If you wish to delete 3D markers for a specific frame range, open the [Graph Pane](../motive-ui-panes/graph-view-pane.md) and select the frame ranges that you wish to delete the markers from, and press the **Delete key**. The 3D trajectory for the selected markers will be erased for the highlighted frame range.

**Note:** Deleted 3D data can be recovered by [reconstructing and auto-labeling](reconstruction-and-2d-mode.md#post-processing-reconstruction) new 3D data from recorded 2D data.

## Trimming Captured Takes

The trimming feature can be used to crop a specific frame range from a Take. For each round of trim, a copied version of the Take will be automatically achieved and backed up into a separate session folder.

**Steps for trimming a Take**

**1)** Determine a frame range that you wish to extract.

**2)** Set the [working range](../motive-ui-panes/graph-view-pane.md#working-range-playback-range) (also called as the view range) on the Graph View pane. All other frames outside of this range will be trimmed out. You can set the working range through the following approaches:

* Specify the starting frame and ending frame from the navigation bar on the [Graph Pane](../motive-ui-panes/graph-view-pane.md).
* Highlight, or select, the desired frame range in the [Graph pane](../motive-ui-panes/graph-view-pane.md), and zoom into it using the zoom-to-fit hotkey (F) or the [![Timeline Recenter.png](https://v30.wiki.optitrack.com/images/f/f1/Timeline_Recenter.png)](https://v30.wiki.optitrack.com/index.php?title=File:Timeline_Recenter.png) icon.
* Set the working range from the [Control Deck](../motive-ui-panes/control-deck.md) by inputting start and end frames on the [![ControlDeck WorkingRange 20.png](https://v30.wiki.optitrack.com/images/2/20/ControlDeck_WorkingRange_20.png)](https://v30.wiki.optitrack.com/index.php?title=File:ControlDeck_WorkingRange_20.png) field.

**3)** After zooming into the desired frame range, click _Edit_ > _Trim Current Range_ to trim out the unnecessary frames.

**4)** A dialog box will pop up asking to confirm the data removal. If you wish to reset the frame numbers upon trimming the take, select the corresponding check box on the pop-up dialog.

![](<../.gitbook/assets/image (381).png>)

## Labeling Errors

The first step in the post-processing is to check for labeling errors. Labels can be lost or mislabeled to irrelevant markers either momentarily or entirely during capture. Especially when the marker placement is not optimized or when there are extraneous reflections, labeling errors may occur. As mentioned in other pages, marker labels are vital when tracking a set of markers, because each label affects how the overall set is represented. Examine through the recorded capture and spot the labeling errors from the perspective view, or by checking the trajectories on the [Graph pane](../motive-ui-panes/graph-view-pane.md) for suspicious markers. Use the [Labels pane](../motive-ui-panes/labels-pane.md) or the _Tracks View_ mode from the [Graph pane](../motive-ui-panes/graph-view-pane.md) to monitor unlabeled markers in the Take.

When a marker is unlabeled momentarily, the color of tracked marker switches between white (labeled) and orange (unlabeled) by the default color setting. Mislabeled markers may have large gaps and result in a crooked model and trajectory spikes. First, explore captured frames and find where the label has been misplaced. As long as the target markers are visible, this error can easily be fixed by reassigning the correct labels. Note that this method is preferred over editing tools because it conserves the actual data and avoids approximation.

Read more about labeling markers from the [Labeling](labeling.md) page.

![Labeling Pane in Motive](<../.gitbook/assets/image (932).png>)

## Edit Tools

The [Edit Tools](../motive-ui-panes/edit-tools-pane.md) provide functionality to modify and clean-up 3D trajectory data after a capture has been taken. multiple post-processing methods are featured in the Edit Tools for different purposes: **Trim Tails**, **Fill Gaps**, **Smooth**, and **Swap Fix**. The Trim Tails method is used to remove data points in few frames before and after a gap. The Fill Gaps method calculates the missing marker trajectory using interpolation methods. The Smoothing method filters out unwanted noise in the trajectory signal. Finally, the Swapping method switches marker labels for two selected markers. Remember that modifying data using Edit Tools changes the raw trajectories, and an overuse of Edit Tools is not recommended. Read through each method and familiarize yourself with the Editing Tools. Note that you can undo and redo all changes made using Edit Tools.

{% hint style="info" %}
**Frame Range:** If you have a certain frame range selected from the timeline, data edits will be applied to the selected range only.
{% endhint %}

![Editing tools for post-processing of the capture 3D data.](<../.gitbook/assets/image (872).png>)

### Tails

The Tails method trims, or removes, a few data points before and after a gap. Whenever there is a gap in a marker trajectory, slight tracking distortions may be present on each end. For this reason, it is usually beneficial to trim off a small segment (\~3 frames) of data. Also, if these distortions are ignored, they may interfere with other editing tools which rely on existing data points. Before trimming trajectory tails, check all gaps to see if the tracking data is distorted. After all, it is better to preserve the raw tracking data as long as they are relevant. Set the appropriate trim settings, and trim out the trajectory on selected or all frame. Each gap must satisfy the **gap size threshold** value for it to be considered for trimming. Each trajectory segment also needs to satisfy the **minimum segment size**, otherwise, it will be considered as a gap. Finally, the Trim Size value will determine how many leading and trailing trajectory frames are removed from a gap.

**Smart Trim**

The Smart Trim feature automatically sets the trimming size based on trajectory spikes near the existing gap. It is often not needed to delete numerous data points before or after a gap, but there are some cases where it's useful to delete more data points than others. This feature determines whether each end of the gap is suspicious with errors, and deletes an appropriate number of frames accordingly. Smart Trim feature will not trim more frames than the defined Leading and Trailing value.

### Gaps

Gap filling is the primary method in the data editing pipeline, and this feature is used to remodel the trajectory gaps with interpolated marker positions. This is used to accommodate the occluded markers in the capture. This function runs mathematical modeling to interpolate the occluded marker positions from either the existing trajectories or other markers in the asset. Note that interpolating a large gap is not recommended because approximating too many data points may lead to data inaccuracy.

New to Motive 3.0; For Skeletons and Rigid Bodies only Model Asset Markers can be used to fill individual frames where the marker has been occluded. Model Asset markers must be first enabled on the Properties Pane when the desired asset is selected and then they must be enabled for selection in the Viewport. Now when frames are encountered where the marker is lost from camera view, select the associated Model Asset Marker in the 3D view; right click for the context menu and select 'Set Key'.

First of all, set the **Max. Gap Size** value and define the maximum frame length for an occlusion to be considered as a gap. If a gap size has a longer frame length, it will not be affected by the filling mechanism. Set a reasonable maximum gap size for the capture after looking through the occluded trajectories. In order to quickly navigate through the trajectory graphs on the [Graph Pane](../motive-ui-panes/graph-view-pane.md) for missing data, use the **Find Gap** features (Find Previous and Find Next) and automatically select a gap frame region so the data could be interpolated. Then, apply the Fill Gaps feature while the gap region is selected. Various interpolation options are available in the setting including Constant, Linear, Cubic, Pattern-based, and Model-based.

#### Interpolation options

There are four different interpolation options offered in Edit Tools: constant, linear, cubic and pattern-based. First three interpolation methods (constant, linear, and cubic) look at the single marker trajectory and attempt to estimate the marker position using the data points before and after the gap. In other words, they attempt to model the gap via applying different degrees of polynomial interpolations. The other two interpolation options (pattern-based and model-based) reference visible markers and models to the estimate occluded marker position.

**Constant**

Applies zero-degree approximation, assumes that the marker position is stationary and remains the same until the next corresponding label is found.

**Linear**

Applies first-degree approximation, assuming that the motion is linear, to fill the missing data. Only use this when you are sure that the marker is moving at linear motion.

**Cubic**

Applies third-degree polynomial interpolation, cubic spline, to fill the missing data in the trajectory.

**Pattern based**

This refers to trajectories of selected reference markers and assumes the target marker moves along in a similar pattern. The _Fill Target_ marker is specified from the drop-down menu under the Fill Gaps tool. When multiple markers are selected, a Rigid Body relationship is established among them, and the relationship is used to fill the trajectory gaps of the selected _Fill Target_ marker as if they were all attached to a same Rigid Body. The following list is the general workflow for using the Pattern Based interpolation:

1. Select both reference markers and the target marker to fill.
2. Examine the trajectory of the target marker from the [Graph Pane](../motive-ui-panes/graph-view-pane.md): Size, range, and a number of gaps.
3. Set an appropriate Max. Gap Size limit.
4. Select the Pattern Based interpolation option.
5. Specify the _Fill Target_ marker in the drop-down menu.
6. When interpolating for only a specific section of the capture, select the range of frames from [Graph pane](../motive-ui-panes/graph-view-pane.md).
7. Click the Fill Selected/Fill All/Fill Everything.

### Curves

The curves tool applies a noise filter (low-pass Butterworth, 4th degree) to trajectory data, and this modifies the marker trajectory smoother. This is a bi-directional filter that does not introduce phase shifts. Using this tool, any vibrating or fluttering movements are filtered out. First, set the cutoff frequency for the filter and define how strongly your data will be smoothed. When the cutoff frequency is set high, only high-frequency signals are filtered. When the cutoff frequency is low, trajectory signals at a lower frequency range will also be filtered. In other words, a low cutoff frequency setting will smooth most of the transitioning trajectories, whereas high cutoff frequency setting will smooth only the fluttering trajectories. High-frequency data are present during sharp transitions, and this can also be introduced by signal noise. Commonly used ranges for Filter Cutoff Frequency are between 7 Hz to 12 Hz, but you may want to adjust the value higher for fast and sharp motions to avoid softening motion transitions need to stay sharp.\\

![Smoothing a 3D trajectories.](<../.gitbook/assets/image (390).png>)

### Fragments

This tool is used for quickly deleting any marker trajectories that exist only for a few frames. Markers that appear only momentarily are likely happening due to noise in the data. If you wish to clean up these short-lived trajectories to further clean up the data, the fragments tool can be used. You will just need to set the minimum frame percentage under the settings. Then, when you click delete, individual marker trajectories that are shorter than the percentage defined will be deleted.

### Swaps

In some cases, marker labels may be swapped during capture. Swapped labels can result in erratic orientation changes, or crooked Skeletons, but they can be corrected by re-labeling the markers. The Swap Fix feature in the [Edit Tools](../motive-ui-panes/edit-tools-pane.md) can be used to correct obvious swaps that persist through the capture. Select two markers that have their labels swapped, and select the frame range that you wish to edit. Find Previous and Find Next buttons allow you to navigate to the frame where their position have been changed. If a frame range is not specified, the change will be applied from current frame forward. Finally, switch the marker labels by clicking on the Apply Swap button. As long as both labels are present in the frame and only correction needed is to change the labels, the Swap Fix tool could be utilized to make corrections.

## Solve

{% hint style="danger" %}
**Solved Data:** After editing marker data in a recorded _Take_, corresponding [Solved Data](data-recording/data-types.md#solved-data) must be updated.
{% endhint %}
