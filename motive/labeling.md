# Labeling

This page provides basic description of marker labels and instructions on labeling workflow in Motive.

## Labeling: Basic Concept

**Marker Label**

Marker labels are basically software name tags that are assigned to **trajectories** of reconstructed 3D markers so that they can be referenced for tracking individual markers, Rigid Bodies, or Skeletons. Motive identifies marker trajectories using the assigned labels. Labeled trajectories can be exported individually, or combined together to compute positions and orientations of the tracked objects. In most applications, all of the target 3D markers will need to be labeled in Motive. There are two methods for labeling markers in Motive: **auto-labeling** and **manual labeling**, and both labeling methods will be covered in this page.

![](<../.gitbook/assets/image (472).png>)

{% hint style="danger" %}
**Solved Data:** After editing marker data in a recorded _Take_, corresponding [Solved Data](data-recording/data-types.md#solved-data) must be updated.
{% endhint %}

**Monitoring Labels**

Labeled or unlabeled trajectories can be identified and resolved from the following places in Motive:

* [**3D Perspective Viewport**](../motive-ui-panes/viewport.md#perspective-view): From the 3D viewport, check the _Marker Labels_ in the visual aids option to view marker labels for selected markers.
* [**Labels pane**](../motive-ui-panes/labels-pane.md): The Labels pane lists out all of the marker labels and corresponding percentage gap for each label. The color of the label also indicates whether if the label is present or missing at the current frame.
* [**Graph View pane**](../motive-ui-panes/graph-view-pane.md): For frames where the selected label is not assigned to any markers, the timeline scrubber gets highlighted in red. Also, the tracks view of this pane provides a list of labels and their continuity in a captured _Take_.

![Using the Graph View pane to view unlabeled trajectory gaps on labeled marker.](<../.gitbook/assets/image (404).png>) ![List of labeled markers for the selected Rigid Body (VCS) and unlabeled markers shown on the Labels pane. Click image to enlarge.](<../.gitbook/assets/image (394).png>)

## Labeling Methods

There are two approaches to labeling markers in Motive:

* **Auto-label pipeline:** Automatically label sets of Rigid Body markers and Skeleton markers using calibrated asset definitions.
* **Manual Label:** Manually label individual markers using the [Labels pane](../motive-ui-panes/labels-pane.md).

For tracking Rigid Bodies and Skeletons, Motive can use the [asset definitions](assets/) to automatically label associated markers both in real-time and post-processing. The auto-labeler uses references assets that are enabled, or assets that are checked in the [Assets pane](../motive-ui-panes/assets-pane.md), to search for a set of markers that matches with the definition and assign pre-defined labels throughout the capture.

![Active assets are checked on the Assets pane.](<../.gitbook/assets/image (395).png>) ![Performing Auto-labeling pipeline on a selected Take the Data pane.](<../.gitbook/assets/image (463).png>)

There are times, however, when it is necessary to **manually label** a section or all of a trajectory, either because the markers of a Rigid Body or a Skeleton were misidentified (or unidentified) during capture or because individual markers need to be labeled without using any tracking assets. In these cases, the [Labels pane](../motive-ui-panes/labels-pane.md) in Motive is used to perform manual labeling of individual trajectories. Manual labeling workflow is supported only in post-processing of capture when a _Take_ file (TAK) has been loaded with 3D data as its playback type. In case of [2D data](reconstruction-and-2d-mode.md#2d-mode) only capture, the _Take_ must be **Reconstructed** first in order to assign, or edit, the marker labels in its 3D data. This manual labeling process, along with [3D data editing](data-editing.md) is typically referred to as _post processing_ of mocap data.

![Auto-labeled Rigid Body markers.](<../.gitbook/assets/image (442).png>) ![Auto-labeled Skeleton markers.](<../.gitbook/assets/image (433).png>)

## Auto-label

Rigid body and Skeleton asset definitions contain information of marker placements on corresponding assets. This is recorded when the assets are first created, and the auto-labeler in Motive uses them to label a set of reconstructed 3D trajectories that resemble marker arrangements of active assets. Once all of the markers on active assets are successfully labeled, corresponding Rigid Bodies and Skeletons get tracked in the 3D viewport.

The auto-labeler runs in real-time during Live mode and the marker labels get saved onto the recorded TAKs. Running the auto-labeler again in post-processing will basically attempt to label the Rigid Body and Skeleton markers again from the 3D data.

### Auto-labeling Steps

**From Data pane**

1. Select _Takes_ from the [Data pane](../motive-ui-panes/data-pane.md)
2. Right-click to bring up the context menu
3. Click _reconstruct and auto-label'_ to process selected _Takes_. The this pipeline will create a new set of 3D data and auto-label the markers from it.
4. This will label all the markers that matches the corresponding asset definition.

![Auto-labeling a Take](<../.gitbook/assets/image (482).png>)

{% hint style="danger" %}
**Note:** Be careful when reconstructing a _Take_ again either by **Reconstruct** or **Reconstruct and Auto-label**, because it will overwrite the 3D data and any post-processing edits on trajectories and marker labels will be discarded. Also, for _Takes_ involving Skeleton assets, the recorded Skeleton marker labels, which were intact during the live capture, may be discarded, and reconstructed markers may not be auto-labeled again if the Skeletons are never in well-trackable poses throughout the captured _Take_. This is another reason why you want to start a capture with a calibration pose (e.g. [T-pose](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#calibration-pose)).
{% endhint %}

## Marker Sets

Marker Set is a list of labels, or marker names, that can be manually assigned to unlabeled markers. This can be created when there is a need to label individual markers in the scene that are not associated with a Rigid Body nor a Skeleton asset.

Labels in the Marker Set, Rigid Body, and Skeleton assets are managed using the Constraints pane. Please refer to the [Constraints pane](../motive-ui-panes/constraints-pane/) to see how to add and/or modify marker labels. Once the labels are added, the Labels pane can be used to assign them onto markers.

**Read more at** [**Constraints pane**](../motive-ui-panes/constraints-pane/) **page.**

\\

![Marker labels created in Constraints pane.](<../.gitbook/assets/image (484).png>)

## Labels pane

{% embed url="https://vimeo.com/167944428?embedded=true&owner=15736845&source=video_title" %}
Labeling Tutorial 2. Manual Labeling in Motive. **This video is based on older version of Motive. There maybe a few differences in Motive 2.0, but the general workflow still remains the same.**
{% endembed %}

The [Labels pane](../motive-ui-panes/labels-pane.md) is used to assign, remove, and edit marker labels in the [3D data](data-recording/data-types.md#3d-data). The **Tracks View** under the [Graph View pane](../motive-ui-panes/graph-view-pane.md) can be used in conjunction with the Labels pane to monitor which markers and gaps are associated. The Labels pane is also used to examine the number of occluded gaps in each label, and it can be used along with the [Editing Tools](data-editing.md) for complete post-processing.

Using the Labels pane, you can assign marker labels for each asset (Marker Set, Rigid Body, and Skeleton) via the QuickLabel Mode [![Label QuickLabelMode.png](https://v30.wiki.optitrack.com/images/b/be/Label_QuickLabelMode.png)](https://v30.wiki.optitrack.com/index.php?title=File:Label_QuickLabelMode.png). The Labels pane also shows a list of labels involved in the Take and their corresponding _percent completeness_ values. The _percent completeness_ values indicate frame percentages of a _Take_ for which the trajectory has been labeled. If the trajectory has no gaps (100% complete), no number will be shown. You can use this pane together with the [Graph View pane](../motive-ui-panes/graph-view-pane.md) to quickly locate gaps in a trajectory.

For a given frame, all labels are color-coded. For each frame of 3D data, assigned marker labels are shown in white, labels without reconstructions are shown in red, and unlabeled reconstructions are shown in orange; similar to how they are presented in the [3D View](../motive-ui-panes/viewport.md#perspective-view).

See the [Labels pane](../motive-ui-panes/labels-pane.md) page for detailed explanation on each option.

### QuickLabel Mode

![Use the Labels pane to quickly label markers. Click image to enlarge.](<../.gitbook/assets/image (470).png>) ![Re-labeling Skeleton markers using the QuickLabel Mode.](<../.gitbook/assets/image (596).png>)

The **QuickLabel** mode allows you to tag labels with single-clicks in the view pane, and it is a handy way to reassign or modify marker labels throughout the capture. When the QuickLabel mode is toggled, the mouse cursor switches to a finger icon with the selected label name attached next to it. Also, when the display label option is enabled in the [perspective view](../motive-ui-panes/viewport.md#perspective-view), all of assigned marker labels will be displayed next to each marker in the [3D viewport](../motive-ui-panes/viewport.md#perspective-view), as shown in the image below. Select the marker set you wish to label, and tag the appropriate labels to each marker throughout the capture.

When assigning labels using the Quick Label Mode, the labeling scope is configured from the labeling range settings. You can restrict the labeling operation to apply from the current frame backward, current frame forward, or both depending on the trajectory. You may also restrict labeling operations to apply the selected label to all frames in the _Take_, to a selected frame range, or to a trajectory 'fragment' enclosed by gaps or spikes. The fragment/spike setting is used by default and this best identifies mislabeled frame ranges and assigns marker labels. See the [Labels pane](../motive-ui-panes/labels-pane.md) page for details on each feature.

### Labeling using the QuickLabel Mode

1. Under the drop-down menu in the Labels pane, select an asset you wish to label.
2. All of the involved markers will be displayed under the columns.
3. From the label list, select unlabeled or mislabeled markers.
4. Inspect the behavior of the selected trajectory and decide whether you want to apply the selected label to frames forward or frames backward or both. This option can be selected from [labeling range settings](../motive-ui-panes/labels-pane.md#labeling-range-settings) on the Labels pane.
5. Switch to QuickLabeling Mode [![Label QuickLabelMode.png](https://v30.wiki.optitrack.com/images/b/be/Label_QuickLabelMode.png)](https://v30.wiki.optitrack.com/index.php?title=File:Label_QuickLabelMode.png) (Hotkey: D).
6. In the [Perspective View](../motive-ui-panes/viewport.md#perspective-view) pane. Assign the selected label to a marker. If the Increment Option ([![Label IncrementOptions 30.png](https://v30.wiki.optitrack.com/images/7/78/Label_IncrementOptions_30.png)](https://v30.wiki.optitrack.com/index.php?title=File:Label_IncrementOptions_30.png)) is set under the Labels pane, the label selection in the Labels pane will automatically advance each time you assign them.
7. After assigning all labels, switch back to normal Select Mode [![Label PointerMode.png](https://v30.wiki.optitrack.com/images/5/55/Label_PointerMode.png)](https://v30.wiki.optitrack.com/index.php?title=File:Label_PointerMode.png).

{% hint style="info" %}
**Hiding Marker Labels**

If the marker labels are set to visible in the [3D viewport](../motive-ui-panes/viewport.md#perspective-view), Motive will show all of the marker labels when entering the QuickLabel mode. To hide all of the marker labels from showing up in the viewport, you can click on the visual aids option in the perspective view, and uncheck marker labels.
{% endhint %}

![Hiding marker labels.](<../.gitbook/assets/image (475).png>)

## General Labeling Steps

The following section provides the general labeling steps in Motive. Note that the labeling workflow is flexible and alternative approaches to the steps listed in this section could also be used. Utilize the auto-labeling pipelines in combination with the [Labels pane](../motive-ui-panes/labels-pane.md) to best reconstruct and label the 3D data of your capture.

{% hint style="info" %}
**Labeling Tips**

* Use the [Graph View pane](../motive-ui-panes/graph-view-pane.md) to monitor occlusion gaps and labeling errors as you post-process capture _Takes_
* When using the [Labels pane](../motive-ui-panes/labels-pane.md), choose the most appropriate labeling range settings (all, selected, spike, or fragment) to efficiently label selected trajectories.
* [Motive Hotkeys](motive-hotkeys.md) can increase the speed of the workflow. Use Z and Shift+Z hotkeys to quickly find gaps in the selected trajectory.
* When working with Skeleton assets, label the hip segment first. The hip segment is the main parent segment, top of the segments hierarchy, where all other child segments are associated to. Manually assigning hip markers sometimes help the auto-labeler to label the entire asset.
* Show/Hide Skeleton visibility under the visual aids [![Viewport16.png](https://v30.wiki.optitrack.com/images/6/6d/Viewport16.png)](https://v30.wiki.optitrack.com/index.php?title=File:Viewport16.png) options in the [perspective view](../motive-ui-panes/viewport.md#perspective-view) to have a better view on the markers when assigning marker labels.
* Toggle Skeleton selectability under the selection option [![PerspectiveViewport5 30.png](https://v30.wiki.optitrack.com/images/f/f7/PerspectiveViewport5_30.png)](https://v30.wiki.optitrack.com/index.php?title=File:PerspectiveViewport5_30.png) in the [perspective view](../motive-ui-panes/viewport.md#perspective-view) to use the Skeleton as a visual aid without it getting in the way of marker data.
* Show/Hide Skeleton sticks and marker colors under the visual aids [![Viewport16.png](https://v30.wiki.optitrack.com/images/6/6d/Viewport16.png)](https://v30.wiki.optitrack.com/index.php?title=File:Viewport16.png) in the [perspective view](../motive-ui-panes/viewport.md#perspective-view) options for intuitive identification of labeled markers as you tag through Skeleton markers.
* For Skeleton assets, the [_Show Tracking Errors_](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive-ui-panes/properties-pane/properties-pane-Skeleton.md) property can be utilized to display tracking errors on Skeleton segments.
{% endhint %}

### Using Combined Reconstruction and Auto-label Pipeline

**Step 1.** In the [Data pane](../motive-ui-panes/data-pane.md), **Reconstruct and auto-label** the take with all of the desired assets enabled.

**Step 2.** In the [Graph View pane](../motive-ui-panes/graph-view-pane.md), examine the trajectories and navigate to the frame where labeling errors are frequent.

**Step 3.** Open the [Labels pane](../motive-ui-panes/labels-pane.md).

**Step 4.** Select an asset that you wish to label.

**Step 5.** From the label columns, Click on a marker label that you wish to re-assign.

**Step 6.** Inspect behavior of a selected trajectory and its labeling errors and set the appropriate labeling settings (allowable gap size, maximum spike and applied frame ranges).

**Step 7.** Switch to the QuickLabel mode (Hotkey: D).

**Step 8.** On the [Perspective View](../motive-ui-panes/viewport.md#perspective-view), assign the labels onto the corresponding marker reconstructions by clicking on them.

**Step 9.** When all markers have been labeled, switch back to the Select Mode.

### Using Standalone Reconstruction Pipeline and Auto-label Pipeline Separately

**Step 1.** Start with 2D data of a captured _Take_ with model assets (Skeletons and Rigid Bodies).

**Step 2.** **Reconstruct and Auto-Label**, or just **Reconstruct**, the _Take_ with all of the desired assets enabled under the [Assets pane](../motive-ui-panes/assets-pane.md). If you use reconstruct only, you can skip step 3 and 5 for the first iteration.

**Step 3.** Examine the reconstructed 3D data, and inspect the frame range where markers are mislabeled.

**Step 4.** Using the [Labels pane](../motive-ui-panes/labels-pane.md), manually fix/assign marker labels, paying attention to your label settings (direction, max gap, max spike, selected duration).

**Step 5.** Unlabel all trajectories you want to re-auto-label.

**Step 6.** **Auto-Label** the _Take_ again. Only the unlabeled markers will get re-labeled, and all existing labels will be kept the same.

**Step 7.** Re-examine the marker labels. If some of the labels are still not assigned correctly from any of the frames, repeat the steps 3-6 until complete.

### Labeling Error Fix

The general process for resolving labeling error is:

1. Identify the trajectory with the labeling error.
2. Determine if the error is a swap, an occlusion, or unlabeled.
3. Resolve the error with the correct tool.

* Swap: Use the Swap Fix tool ( Edit Tools ) or just re-assign each label ( Labels panel ).
  * When manually labeling markers to fix swaps, set appropriate settings for the labeling direction, max spike, and selected range settings.
* Occlusion: Use the Gap Fill tool ( Edit Tools ).
* Unlabeled: Manually label an unlabeled trajectory with the correct label ( Labels panel ).

For more data editing options, read through the [Data Editing](data-editing.md) page.

![Labeling an unlabeled marker.](../.gitbook/assets/Label.gif)
