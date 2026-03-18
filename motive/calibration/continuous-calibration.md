# Continuous Calibration

This page provides detailed information on the continuous calibration feature, which can be enabled from the [Calibration pane](../../motive-ui-panes/calibration-pane.md).

## Overview

The Continuous Calibration feature ensures your system always remains optimally calibrated, requiring no user intervention to maintain the tracking quality. It uses highly sophisticated algorithms to evaluate the quality of the calibration and the triangulated marker positions. Whenever the tracking accuracy degrades, Motive will automatically detect and update the calibration to provide the most globally optimized tracking system.

{% embed url="https://da8mv7i4lvduk.cloudfront.net/continuous-calibration-1920.mp4" %}

### Key Features

* **Ease of use.** This feature provides much easier user experience because the capture volume will not have to be re-calibrated as often, which will save a lot of time. You can simply enable this feature and have Motive maintain the calibration quality.
* **Optimal tracking quality.** Always maintains the best tracking solution for live camera systems. This ensures that your captured sessions retain the highest quality calibration. If the system receives inadequate information from the environment, the calibration with not update and your system never degrades based on sporadic or spurious data. A moderate increase in the number of real optical tracking markers in the volume and an increase in camera overlap improves the likelihood of a higher quality update.
* **Works with all camera types.** Continuous calibration works with all OptiTrack camera models.

### Requirements

For continuous calibration to work as expected, the following criteria must be met:

* **Live Mode Only.** Continuous calibration only works in [Live mode](../data-recording/).
* **Markers Must Be Tracked.** Continuous calibration looks at tracked reconstructions to assess and update the calibration. Therefore, at least some number of markers must be tracked within the volume.
* **Majority of Cameras Must See Markers.** A majority of cameras in a volume needs to receive some tracking data within a portion of their field of view in order to initiate the calibration process. Because of this, traditional perimeter camera systems typically work the best. Each camera should additionally see at least 4 markers for optimal calibration. If not all the cameras see the markers at the same time, anchor markers will need to be set up to improve the calibration updates.

![Whenever possible, continuous calibration seeks to maintain and improve convergence of the tracked rays throughout the volume.](<../../.gitbook/assets/image (136).png>)

## How to Use

To enable Continuous Calibration, calibrate the camera system first and enable the Continuous Calibration setting at the bottom of the [Calibration pane](../../motive-ui-panes/calibration-pane.md). Once enabled, Motive continuously monitors the residual values in captured marker reconstructions, and when the updated calibration is better than the existing one, it will get updated automatically. Please note that at least four (default) marker samples must be being tracked in the volume for the continuous calibration to work. You will also be able to monitor the sampling progress and when the calibration has been last updated.

![Continuous calibration enabled under the Calibration pane.](<../../.gitbook/assets/image (115).png>)

## Anchor Markers

Anchor markers can be set up in Motive to further improve continuous calibration. When properly configured, anchor markers improve continuous calibration updates, especially on systems that consists of multiple sets of cameras that are separated into different tracking areas, by obstructions or walls, without camera view overlap. It also provides extra assurance that the global origin will not shift during each updates; although the continuous calibration feature itself already checks for this.

### Anchor Marker Setup

Follow the steps below for setting up the anchor marker in Motive:

**Adding Anchor Markers in Motive**

1. First, make sure the entire camera volume is fully [calibrated](./) and prepared for marker tracking.
2. Place any number of markers in the volume to assign them as the anchor markers.
3. Make sure these markers are securely fixed in place within the volume. It's important that the distances between these markers do not change throughout the continuous calibration updates.
4. Open the [Calibration pane](../../motive-ui-panes/calibration-pane.md) and select the second page at the bottom to access the anchor marker feature.
5. In the 3D viewport, select the markers that are going to be assigned as anchors.
6. Click on _Add_ to add the selected markers as anchor markers.
7. Once markers are added as anchor markers, magenta spheres will appear around the markers indicating the anchors have been set.
8. Add more anchors as needed, again, it's important that these anchor markers do not move throughout the tracking. Also when the anchor markers need to be reset, whether if the marker was displaced, you can clear the anchor markers and reassign them.

<div><img src="../../.gitbook/assets/image (785).png" alt="Access the second page at the bottom to show anchor marker feature."> <figure><img src="../../.gitbook/assets/image (12) (1) (1).png" alt=""><figcaption><p>Anchor markers assigned in Motive.</p></figcaption></figure></div>

## Camera Partitions

For multi-room setups, it is useful to group cameras into partitions. This allows for Continuous Calibration to run in each individual room without the need for camera view overlap.&#x20;

### Properties Pane: Camera

From the Properties pane of a camera you can assign a Partition ID from the advanced settings.&#x20;

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Change Partition ID under Threshold in the Advanced Settings within the Properties pane. </p></figcaption></figure>

You'll want to assign all the cameras in the same room the same Partition ID. Once assigned these cameras will all contribute to Continuous Calibration for their particular space. This will help ensure the accuracy of Continuous Calibration for each individual space that is a part of the whole system.&#x20;

## Editing Camera Positions with Gizmo Tool

In the event that you need to manually adjust cameras in the 3D view, you can enable Editable in 3D View in [General Settings](../../motive-ui-panes/settings/settings-general.md). To access this setting, you'll need to select Show Advanced from the 3-dot more options dropdown at the top. This will populate a Calibration section on this window.&#x20;

<figure><img src="../../.gitbook/assets/image (14) (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>

This allows you to use the [Gizmo Tools](../assets/gizmo-tool-translate-rotate-and-scale.md) to Translate, Rotate, and Scale cameras to their desired locations.&#x20;

## Log Pane Status for Continuous Calibration

For a full list of Log pane Continuous Calibration statuses, please see the [Log pane](../../motive-ui-panes/log-pane.md#status-messages) page.

### Need More Samples

This notice indicates the need for more markers to be visible by a particular camera. For instance, if camera 2 is not seeing enough markers in its camera view, the Log pane will inform you that you need more markers for that particular camera.

<figure><img src="../../.gitbook/assets/image (18) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Need More Distributed Samples

<figure><img src="../../.gitbook/assets/image (46) (2).png" alt=""><figcaption></figcaption></figure>

This indicates the need for more markers to be spread in more areas of the camera view.&#x20;

<figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption><p>Markers that only fill a small section of the camera's view vs. cameras more spread across the camera's view. </p></figcaption></figure>
