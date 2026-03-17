# Data Types

This page explains different types of captured data in Motive. Understanding these types is essential in order to fully utilize the data-processing pipelines in Motive.

## Overview

There are three different types of data: 2D data, 3D data, and Solved data. Each type of data will be covered in detail throughout this page, but basically, _2D Data_ is the captured camera frame data, _3D Data_ is the reconstructed 3-dimensional marker data, and _Solved_ data is the calculated positions and orientations of [Rigid Bodies](../rigid-body-tracking/) and [Skeleton](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md) segments.

Motive saves tracking data into a _Take_ file (TAK extension), and when a capture is initially recorded, all of the 2D data, real-time reconstructed 3D data, and solved data are saved onto a _Take_ file. Recorded 3D data can be post-processed further in [Edit mode](../../motive-ui-panes/control-deck.md), and when needed, a new set of 3D data can be re-obtained from saved 2D data by performing the reconstruction pipelines. From the 3D data, Solved data can be derived.

Available data types are listed on the [Data pane](../../motive-ui-panes/data-pane.md). When you open up a _Take_ in [Edit mode](../../motive-ui-panes/control-deck.md), the loaded data type will be highlighted at the top-left corner of the 3D viewport. If available, 3D Data will be loaded first by default, and the 2D data can be accessed by entering the [2D Mode](../../motive-ui-panes/viewport.md#cameras-view) from the Data pane.

![3D data is loaded from a recorded Take.](<../../.gitbook/assets/image (434).png>)

## Data Types

### 2D data

2D data is the foundation of motion capture data. It mainly includes the 2D frames captured by each camera in a system.

Images in recorded 2D data depend on the [image processing mode](../camera-video-types.md#video-types), also called the video type, of each camera that was selected at the time of the capture. Cameras that were set to reference modes (MJPEG grayscale images) record reference videos, and cameras that were set to tracking modes (object, precision, segment) record _2D object images_ which can be used in the reconstruction process. The latter 2D object data contains information on x and y centroid positions of the captured reflections as well as their corresponding sizes (in pixels) and roundness, as shown in the below images.

Using the 2D object data along with the camera calibration information, 3D data is computed. Extraneous reflections that fail to satisfy the 2D object filter parameters (defined under [application settings](../../motive-ui-panes/settings/)) get filtered out, and only the remaining reflections are processed. The process of converting 2D centroid locations into 3D coordinates is called **Reconstruction**, which will be covered in the later section of this page.

![2D object image of a single camera from the 2D camera preview.](<../../.gitbook/assets/image (404).png>) ![Size and circularity information displayed from the 2D camera preview.](<../../.gitbook/assets/image (883).png>)

3D data can be reconstructed either in real-time or in post-capture. For real-time capture, Motive processes captured 2D images on a per-frame basis and streams the 3D data into external pipelines with extremely low processing latency. For recorded captures, the saved 2D data can be used to create a fresh set of 3D data through [post-processing reconstruction](../reconstruction-and-2d-mode.md#post-processing-reconstruction), and any existing 3D data will be overwritten with the newly reconstructed data.

* Contains 2D frames, or 2D object information captured by each camera in a system. 2D data can be monitored from the [Camera Preview](../../motive-ui-panes/viewport.md#cameras-view) pane.
* Recorded 2D data can be reconstructed and auto-labeled to derive the 3D data.
* 3D tracking data is not computed yet. The tracking data can be exported only after reconstructing the 3D data.
* In playback of recorded 2D data, 3D data will be Live-reconstructed into 3D data and reported in the 3D viewport.

### 3D data

3D data contains 3D coordinates of reconstructed markers. 3D markers get reconstructed from 2D data and shows up the perspective view. Each of their trajectories can be monitored in the [Graph pane](../../motive-ui-panes/graph-view-pane.md). In recorded 3D data, marker _labels_ can be assigned to reconstructed markers either through the [auto-labeling](../labeling.md#auto-label) process using asset definitions or by manually assigning it. From these labeled markers, Motive solves the position and orientation of Rigid Bodies and Skeletons.

Recorded 3D data is editable. Each frame of the trajectory can be deleted or modified. The post-processing [edit tools](../data-editing.md) can be used to interpolate the missing trajectory gaps or apply the smoothing, and the [labeling tools](../labeling.md) can be used to assign or reassign the marker labels.

Lastly, from a recorded 3D data, its tracking data can be [exported](../data-export/) into various file formats — CSV, C3D, FBX, and more.

* Reconstructed 3D marker positions.
* Marker labels can be assigned.
* Assets are modeled and the tracking information is available.
* [Edit tools](../data-editing.md) can be used to fill the trajectory gaps.

![Reconstructed 3D data shown in the Perspective View pane.](<../../.gitbook/assets/image (915).png>)

### Solved Data

Solved data is positional and rotational, 6 degrees of freedom (DoF), tracking data of [Rigid Bodies](../rigid-body-tracking/) and [Skeletons](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md).  After a take has been recorded, you will need either select **Solve all Assets** by right clicking on a Take in the [Data pane](../../motive-ui-panes/data-pane.md), or right click on the asset in the [Assets ](../../motive-ui-panes/assets-pane.md)pane and select **Solve** while in **Edit** mode. Takes that contain solved data will be indicated under the solved column.

![Solving data in Assets pane.](<../../.gitbook/assets/image (641).png>) ![Solving data in Data pane.](<../../.gitbook/assets/image (100) (1).png>)

![Solved Rigid Body tracking data in Motive.](<../../.gitbook/assets/image (865).png>)

## Deleting Data

### Deleting 2D/Video/Audio data

Recorded [2D data](data-types.md#2d-data), audio data, and reference videos can be deleted from a _Take_ file. To do this, open the [Data pane](../../motive-ui-panes/data-pane.md), right-click on a recorded _Take(s)_, and click the _Delete 2D Data_ from the context menu. Then, a dialogue window will pop-up, asking which types of data to delete. After removing the data, a backup file will be archived into a separate folder.

Deleting 2D data will significantly reduce the size of the _Take_ file. You may want to delete recorded 2D data when there is already a final version of reconstructed 3D data recorded in a _Take_ and the 2D data is no longer needed. However, be aware that deleting [2D data](data-types.md#2d-data) removes the most fundamental data from the _Take_ file. After 2D data has been deleted, the action cannot be reverted, and without 2D data, 3D data cannot be [reconstructed](../reconstruction-and-2d-mode.md#reconstruction-basic-concept) again.

![Delete 2D data dialog window.](<../../.gitbook/assets/image (905).png>) ![Data pane context menu.](<../../.gitbook/assets/image (354).png>)

### Deleting 3D Data

Recorded 3D data can be deleted from the context menu in the [Data pane](../../motive-ui-panes/data-pane.md). To delete 3D data, right-click on selected _Takes_ and click _Delete 3D data_, and all reconstructed 3D information will be removed from the Take. When you delete the 3D data, all edits and labeling will be deleted as well. Again, a new 3D data can always be reacquired by reconstructing and auto-labeling the _Take_ from 2D data.

**Deleting 3D data for a single \_Take**\_

When frame range is not selected, it will delete 3D data from the entire frame. When a frame range is selected from the Timeline Editor, this will delete 3D data in the selected ranges only.

**Deleting 3D data for multiple \_Takes**\_

When multiple _Takes_ are selected from the [Data pane](../../motive-ui-panes/data-pane.md), deleting 3D data will remove 3D data from all of the selected _Takes_. This will remove 3D data from the entire frame ranges.

![Data pane: Deleting 3D data from a recorded Take.](<../../.gitbook/assets/image (388).png>)

### Deleting Solved Data

When a Rigid Body or Skeleton exists in a _Take_, Solved data can be recorded. From the Assets pane, right-click one or more asset and select **Solve** from the context menu to calculate the solved data. To delete, simply click _Remove Solve_.

![](<../../.gitbook/assets/image (861).png>)

### Deleting Marker Labels

Assigned marker labels can be deleted from the context menu in the [Data pane](../../motive-ui-panes/data-pane.md). The _Delete Marker Labels_ feature removes all marker labels from the 3D data of selected _Takes_. All markers will become unlabeled.

**Deleting labels for a single \_Take**\_

When no frame range is selected, it will unlabel all markers from all Takes. When a frame range is selected from the Timeline Editor, this will unlabel markers in the selected ranges only.

**Deleting labels for multiple \_Takes**\_

Even when a frame range is selected from the timeline, it will unlabel all markers from all frame ranges of the selected _Takes_.
