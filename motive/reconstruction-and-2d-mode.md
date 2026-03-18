# Reconstruction and 2D Mode

This page provides an explanation on some of the settings that affect how the 3D tracking data is obtained. Most of the related settings can be found under the Live Pipeline tab in the [Application settings](../motive-ui-panes/settings/). A basic understanding of this process will allow you to fully utilize Motive for analyzing and optimizing captured 3D tracking data. With that being said, we do not recommend changing these settings as the default settings should work well for most tracking applications.

## Reconstruction: Basic Concept

**Reconstruction** is a process of deriving 3D points from 2D coordinates obtained by captured camera images. When multiple synchronized images are captured, 2D centroid locations of detected marker reflections are triangulated on each captured frame and processed through the solver pipeline in order to be tracked. This process involves **trajectorization** of detected 3D markers within the calibrated capture volume and the **booting** process for the tracking of defined assets.

For real-time tracking in Live mode, the settings for this pipeline can be configured from the Live-Pipeline tab in the [Application Settings](../motive-ui-panes/settings/). For post-processing recorded files in Edit mode, the solver settings can be accessed under corresponding [Take properties](../motive-ui-panes/properties-pane/properties-pane-take.md). Note that optimal configurations may vary depending on capture applications and environmental conditions, but for most common applications, default settings should work well.

In this page, we will focus on the [Live Pipeline settings](../motive-ui-panes/settings/settings-live-pipeline.md) and the [Camera Settings](../motive-ui-panes/devices-pane.md), which are the key settings that have direct effects on the reconstruction outcome.

![3D markers reconstructed from captured 2D images.](<../.gitbook/assets/image (422).png>)

## Camera Settings

Camera settings can be configured under the [Devices pane](../motive-ui-panes/devices-pane.md). In general, the overall quality of 3D reconstructions is affected by the quality of captured camera images. For this reason, the camera lens must be focused on the tracking volume, and the settings should be configured so that the markers are clearly visible in each camera view. Thus, the camera settings, such as camera exposure and IR intensity values, must always be checked and optimized in each setup. The following sections highlight additional settings that are directly related to 3D reconstruction.

### Enable Reconstruction

* **Tracking mode vs. Reference mode:** Only the cameras that are configured in the _tracking mode_ (Object or Precision) will contribute to reconstructions. Cameras in the reference mode (MJPEG or Grayscale) will NOT contribute to reconstructions. See [Camera Video Types](camera-video-types.md) page for more information.
* To oscillate between camera video types in Motive, click the camera video type icon under Mode in the Devices pane.

![](<../.gitbook/assets/image (337).png>)

### Threshold Setting

The THR setting is located in the [camera properties](../motive-ui-panes/properties-pane/properties-pane-camera.md) in Motive. When cameras are set to tracking mode, only the pixels with brightness values greater than the configured threshold setting are captured and processed. The pixels brighter than the threshold are referred to as **thresholded pixels**, and all other pixels that do not satisfy the brightness get filtered out. Only the clusters of thresholded pixels are then filtered through the 2D Object Filter to be potentially considered as marker reflections.

{% hint style="danger" %}
We do not recommend lowering the THR value (default:200) for the cameras since lowering THR settings can introduce false reconstructions and noise in the data.
{% endhint %}

{% hint style="info" %}
To inspect brightness values of the pixels, set the Pixel Inspection to true under the View tab in the [Application Settings](../motive-ui-panes/settings/).
{% endhint %}

![Threshold setting in Properties pane.](<../.gitbook/assets/image (386).png>) ![Analyzing pixel brightness values using the pixel inspector.](<../.gitbook/assets/image (301).png>)

## Live Pipeline Settings

The [Live Pipeline settings](../motive-ui-panes/settings/settings-live-pipeline.md) under application settings control the tracking quality in Motive. When a camera system captures multiple synchronized 2D frames, the images are processed through two main stages before getting reconstructed into 3D tracking. The first filter is on the camera hardware level and the other filter is on the software level, and both of them are important in deciding which 2D reflections get identified as marker reflections and be reconstructed into 3D data. Adjust these settings to optimize the 3D data acquisition in both live-reconstruction and post-processing reconstruction of capture data.

### Camera Filter - Software

When a frame of image is captured by a camera, the 2D camera filter is applied. This filter works by judging on the sizes and shapes of the detected reflections or IR illuminations, and it determines which ones can be accepted as markers. Please note that the camera filter settings can be configured in Live mode only because this filter is applied at the hardware level when the 2D frames are first captured. Thus, you will not be able to modify these settings on a recorded _Take_ as the 2D data has already been filtered and saved; however, when needed, you can increase the threshold on the filtered 2D data and perform post-processing reconstruction to recalculate 3D data from the 2D data.

**Min/Max Thresholded Pixels**

The _Min/Max Thresholded Pixels_ settings determine lower and upper boundaries of the size filter. Only reflections with pixel counts within the boundaries will be considered as marker reflections, and any other reflections below or above the defined boundary will be filtered out. Thus, it is important to assign appropriate values to the minimum and maximum thresholded pixel settings.

For example, in a close-up capture application, marker reflections appear bigger on camera's view. In this case, you may want to lower the maximum threshold value to allow reflections with more thresholded pixels to be considered as marker reflections. For common applications, however, the default range should work fine.

![2D Filter section of the cameras tab in the Application Settings.](<../.gitbook/assets/image (308).png>)

{% hint style="info" %}
Enable **Marker Size** under the visual aids ([![Viewport16.png](https://v30.wiki.optitrack.com/images/6/6d/Viewport16.png)](https://v30.wiki.optitrack.com/index.php?title=File:Viewport16.png)) in the [Camera Preview](../motive-ui-panes/viewport.md#cameras-view) viewport to inspect which reflections are accepted, or omitted, by the size filter.
{% endhint %}

![Reflections accepted (white) or rejected (red) by the size filter.](<../.gitbook/assets/image (396).png>)

**Circularity**

In addition to the size filter, the 2D Object Filter also identifies marker reflections based on their shape; specifically, the roundness. It assumes that all marker reflections have circular shapes and filters out all non-circular reflections detected by each camera. The allowable circularity value is defined under the [Marker Circularity](markers.md#circularity) settings in the Reconstruction pane. The valid range is between 0 and 1, with 0 being completely flat and 1 being perfectly round. Only reflections with circularity values bigger than the defined threshold will be considered as marker reflections.

{% hint style="info" %}
Enable **Marker Circularity** under the visual aids [![Viewport16.png](https://v30.wiki.optitrack.com/images/6/6d/Viewport16.png)](https://v30.wiki.optitrack.com/index.php?title=File:Viewport16.png) in the [Camera Preview](../motive-ui-panes/viewport.md#cameras-view) viewport to inspect which reflections are accepted, or omitted, by the circularity filter.
{% endhint %}

![Reflections accepted (white) or rejected (red) by the size filter.](<../.gitbook/assets/image (320) (1) (1) (1) (1) (1) (2) (1).png>)

**Object mode vs. Precision Mode**

The [Object Mode](camera-video-types.md) and [Precision Mode](camera-video-types.md) deliver slightly different data to the host PC. In the object mode, cameras capture 2D centroid location, size, and roundness of markers and deliver to the host PC. In precision mode, cameras send the pixel data that would have been used by object mode to Motive for processing. Then, this region is delivered to the host PC for additional processing to determine the centroid location, size, and roundness of the reflections. Read more about [Video Types](camera-video-types.md).

### Marker Rays

After the 2D camera filter has been applied, each of the 2D centroids captured by each camera forms a **marker ray**, which is basically a 3D vector ray that connects a detected centroid to a 3D coordinate in a capture volume; from each calibrated camera. When a minimum required number of rays, as defined in the [Minimum Rays](../motive-ui-panes/settings/settings-live-pipeline.md)) converge and intersect within the allowable maximum offset distance (defined by [3D Threshold](../motive-ui-panes/settings/settings-live-pipeline.md#trajectorizer) settings) trajectorization of a 3D marker occurs. Trajectorization is a process of using 2D data to calculate respective 3D marker trajectories in Motive.

Monitoring marker rays is an efficient way of inspecting reconstruction outcomes. The rays show up by default, but if not, they can be enabled for viewing under the visual aids [![Viewport16.png](https://v30.wiki.optitrack.com/images/6/6d/Viewport16.png)](https://v30.wiki.optitrack.com/index.php?title=File:Viewport16.png) options under the toolbar in [3D viewport](../motive-ui-panes/viewport.md#perspective-view). There are two different types of marker rays in Motive: tracked rays and untracked rays. By inspecting these marker rays, you can easily find out which cameras are contributing to the reconstruction of a selected marker.

**Tracked Ray (Green)**

Tracked rays are marker rays that represent detected 2D centroids that are contributing to 3D reconstructions within the volume. Tracked Rays will be visible only when reconstructions are selected from the viewport.

![Tracked rays and respective marker marked on the two of the cameras that are selected.](<../.gitbook/assets/image (342).png>)

**Untracked Ray (Red)**

An untracked ray is a marker ray that fails to contribute to a reconstruction of a 3D point. Untracked rays occurs when reconstruction requirements, usually the ray count or the max residuals, are not met.

![Untracked ray from a camera.](<../.gitbook/assets/image (489).png>) ![Respective marker, that's causing the untracked ray, shown in the camera view.](<../.gitbook/assets/image (388).png>)

### Software Filter: Solver Settings

Motive processes markers rays with the camera [calibration](calibration/) to reconstruct respective markers, and the solver settings determine how 2D data gets trajectories and solved into 3D data for tracking the Rigid Bodies and/or Skeletons. The solver not only tracks from the marker rays but additionally utilizes pre-defined asset definitions to provide high-quality tracking. The default solver settings work for most tracking applications, and the users should not need to modify these settings. With that being said, some of the basic settings which can be modified are summarized below.

**Minimum Rays to Start / Minimum Rays to Continue**

This setting sets a minimum number of _tracked_ marker rays required for a 3D point to be reconstructed. In other words, this is the required number of calibrated cameras that need to see the marker. Increasing the minimum ray count may prevent extraneous reconstructions, and decreasing it may prevent marker occlusions from not enough cameras seeing markers. In general, modifying this is recommended only for high camera count setups.

![Reconstruction settings are located under the Live Pipeline tab in the Application Settings.](<../.gitbook/assets/image (311).png>)

**More Settings**

The Live Pipeline settings doesn't have to be modified for most tracking applications. There are other reconstruction setting that can be adjusted to improve the acquisition of 3D data. For detailed description of each setting, read through the [Application Settings: Live Pipeline](../motive-ui-panes/settings/settings-live-pipeline.md) page or refer to the corresponding tooltips.

## Real-time Solve

Motive performs _real-time_ reconstruction of 3D coordinates directly from either captured or recorded 2D data. When Motive is live-processing the data, you can examine the marker rays from the viewport, inspect the Live-Pipeline settings, and optimize the 3D data acquisition.

There are two modes where Motive is reconstructing 3D data in real-time:

* Live mode (Live 2D data capture)
* 2D mode (Recorded 2D data)

### Live Mode

In the [Live Mode](data-recording/#live-mode-and-edit-mode), Motive is Live processing the data from captured 2D frames to obtain 3D tracking data in real-time, and you can inspect and monitor the marker rays from the [3D viewport](../motive-ui-panes/viewport.md#perspective-view). Any changes to the Live Pipeline (Solver/Camera) settings under the [Application Settings](../motive-ui-panes/settings/) will be reflected immediately in the Live mode.

![](<../.gitbook/assets/image (323).png>)

### 2D Mode

The 2D Mode is used to monitor 2D data in the post-processing of a captured _Take_. When a capture is recorded in Motive, both 2D camera data and reconstructed 3D data are saved into a _Take_ file, and by default, the 3D data gets loaded first when a recorded _Take_ file is opened.

Recorded 3D data contains only the 3D coordinates that were live-reconstructed at the moment of capture; in other words, this data is completely independent of the 2D data once recording has been made. You can still, however, view and use the recorded 2D data to optimize the solver parameters and reconstruct a _fresh_ set of 3D data from it. To do so, you need to switch into the **2D Mode** in the [Data pane](../motive-ui-panes/data-pane.md).

In 2D Mode, Motive is reconstructing in real-time from recorded 2D data; using the reconstruction/solver settings that were configured in the [Application Settings](../motive-ui-panes/settings/) at the time of recording; Settings are saved under the properties of the corresponding TAK file. Please note that reconstruction/solver settings from the [TAK properties](../motive-ui-panes/properties-pane/properties-pane-take.md) get applied for post-processing, instead of the settings from the [application settings](../motive-ui-panes/settings/) panel. When in 2D Mode while editing a TAK file, any changes to the reconstruction/solver settings under TAK properties will be reflected in how the 3D reconstructions are solved, in real-time.

**Switching to 2D Mode**

Under the [Data pane](../motive-ui-panes/data-pane.md), click [![ContextMenu dotdotdot.png](https://v30.wiki.optitrack.com/images/c/c4/ContextMenu_dotdotdot.png)](https://v30.wiki.optitrack.com/index.php?title=File:ContextMenu_dotdotdot.png) to access the menu options and check the **2D Mode** option.

![](<../.gitbook/assets/image (299).png>)

{% hint style="info" %}
**Applying changes to 3D data**

Once the reconstruction/solver settings have been adjusted and optimized on recorded data, the post-processing reconstruction pipeline needs to be performed on the _Take_ in order to reconstruct a new set of 3D data. Here, note that the existing 3D data will get overwritten and all of the post-processing edits on it will be discarded.
{% endhint %}

## Post-Processing Reconstruction

The post-processing reconstruction pipeline allows you to convert 2D data from _recorded Take_ into 3D data. In other words, you can obtain a fresh set of 3D data from recorded 2D camera frames by performing reconstruction on a _Take_. Also, if any of the Point Cloud reconstruction parameters have been optimized post-capture, the changes will be reflected on the newly obtained 3D data.

* **Performing post-processing reconstruction.** To perform post-processing reconstruction, open the [Data pane](../motive-ui-panes/data-pane.md), select desired _Takes_, Right-click on the _Take_ selection, and use either the **Reconstruct** pipeline or the **Reconstruct and Auto-label** pipeline from the context menu.
* **Camera Filter Settings** In Edit mode, 2D camera filters can still be modified from the tracking group properties in the [Devices pane](../motive-ui-panes/devices-pane.md). Modified filter settings will change which markers in the recorded 2D data gets processed through the Live Pipeline engine.
* **Solver/Reconstruction Settings** When you perform post-processing reconstruction on a recorded _Take(s)_, a new set of 3D data will be reconstructed from the filtered 2D camera data. In this step, the solver settings defined under corresponding _Take properties_ in the [Properties pane](../motive-ui-panes/properties-pane/) will be used. Note that the reconstruction properties under the [Application Settings](../motive-ui-panes/settings/) are for the Live capture systems only.
* **Reconstruct and Auto-label**, will additionally apply the [auto-labeling](labeling.md#auto-label) pipeline on the obtained 3D data and label any markers that associate with existing asset (Rigid Body or Skeleton) definitions. The auto-labeling pipeline will be explained more on the [Labeling](labeling.md) page.

![Performing Reconstruct and Auto-label pipeline on a selected TAK to obtain a new set of 3D data.](<../.gitbook/assets/image (341).png>) ![When applying post-processing reconstruction, the reconstruction settings configured under the Properties pane will be applied. Click image to enlarge.](<../.gitbook/assets/image (348).png>)

{% hint style="info" %}
* Post-processing reconstruction can be performed either on an entire _Take_ frame range or only within desired frame range by selecting the range under the [Control Deck](../motive-ui-panes/control-deck.md) or in the [Graph pane](../motive-ui-panes/graph-view-pane.md). When nothing is selected, reconstruction will be applied to all frames.
* Entire frames of multiple _Takes_ can be selected and processed altogether by selecting desired _Takes_ under the [Data pane](../motive-ui-panes/data-pane.md).
{% endhint %}

{% hint style="danger" %}
* Reconstructing recorded _Takes_ again either by **Reconstruct** or **Reconstruct and Auto-label** pipeline will completely overwrite existing 3D data, and any post-processing edits on trajectories and marker labels will be discarded.
* Also, for _Takes_ involving Skeleton assets, if the Skeletons are never in well-trackable poses throughout the captured Take, the recorded Skeleton marker labels, which were intact during the live capture, may be discarded, and reconstructed markers may not be auto-labeled again. This is another reason why you want to start a capture with a calibration pose (e.g. T-pose).
{% endhint %}
