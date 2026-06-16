---
description: Detailed instructions for using the Continuous Calibration feature.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/calibration/continuous-calibration
---

# Continuous Calibration

## Overview

The Continuous Calibration feature ensures your OptiTrack camera system always remains optimally calibrated, requiring no user intervention to maintain the tracking quality. Continuous Calibration uses highly sophisticated algorithms to evaluate the quality of the calibration and the triangulated marker positions. Whenever the tracking accuracy degrades, Motive will automatically detect and update the calibration to provide the most globally optimized tracking system.

This page provides detailed information on using the Continuous Calibration feature, which can be enabled from the [Calibration pane](../../motive-ui-panes/calibration-pane.md). For additional Continuous Calibration features, please see the [Continuous Calibration pane](continuous-calibration-pane.md) page.

{% embed url="https://da8mv7i4lvduk.cloudfront.net/continuous-calibration-1920.mp4" %}

### Key Features

* **Ease of use.** This feature provides a much easier user experience because the capture volume will not have to be re-calibrated as often, which saves a lot of time. Simply enable this feature to have Motive maintain the calibration quality.
* **Optimal tracking quality.** Continuous Calibration maintains the best tracking solution for live camera systems. This ensures that your captured sessions retain the highest quality calibration. If the system receives inadequate information from the environment, the calibration will not update. This ensures the tracking quality is more robust over time in noisy environments.  A moderate increase in the number of real optical tracking markers in the volume and an increase in camera overlap improves the likelihood of a higher quality update.
* **Works with all camera types.** Continuous calibration works with all OptiTrack camera models.

### Requirements

For continuous calibration to work as expected, the following criteria must be met:

* **Live Mode Only.** Continuous calibration only works in [Live mode](../data-recording/).
* **Markers Must Be Tracked.** Continuous calibration looks at tracked reconstructions to assess and update the calibration. Therefore, at least some number of markers must be tracked within the volume.
* **Majority of Cameras Must See Markers.** A majority of cameras in a volume needs to receive some tracking data within a portion of their field of view in order to initiate the calibration process. Because of this, traditional perimeter camera systems typically work the best. Each camera should additionally see at least 4 markers for optimal calibration. If not all the cameras see the markers at the same time, anchor markers will need to be set up to improve the calibration updates.

<figure><img src="../../.gitbook/assets/image (717).png" alt="2 screenshots from Motive showing the convergence of rays on a marker both before and after a calibration update. "><figcaption><p>Whenever possible, continuous calibration seeks to maintain and improve convergence of the tracked rays throughout the volume.</p></figcaption></figure>

## Setup

To enable Continuous Calibration, calibrate the camera system first, then enable the Continuous Calibration setting at the bottom of the [Calibration pane](../../motive-ui-panes/calibration-pane.md).&#x20;

Once enabled, Motive continuously monitors the residual values in captured marker reconstructions. When the updated calibration is better than the existing one, Motive updates the calibration accordingly.&#x20;

Please note that at least four marker samples must be continuously tracked in the volume for the Continuous Calibration to work. More markers that are spread further apart will produce better results.

You will also be able to monitor the sampling progress and when the calibration has been last updated directly from the Calibration pane.&#x20;

{% hint style="warning" %}
Please see the [Continuous Calibration Pane](continuous-calibration-pane.md) page for additional features.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Calibration Pane - calibrated and CC enabled.png" alt="A screenshot of the Motive Calibration pane, showing a calibration loaded and Continuous Calibration enabled. "><figcaption><p>Continuous calibration enabled under the Calibration pane.</p></figcaption></figure>

## Anchor Markers

Anchor markers further improve the continuous calibration. When properly configured, anchor markers establish a known point-of-reference for continuous calibration updates, especially on systems that consists of multiple sets of cameras that are separated into different tracking areas, by obstructions or walls, without camera view overlap. Anchor markers provide extra assurance that the global origin will not shift during each update, which the continuous calibration feature checks for as well.

### Active Anchor Markers

Active markers are best to use for anchors due to their unique active IDs, which improve accuracy, remove ambiguity, and enhance continuous calibration all around.

* Active markers allow bumped cameras to update faster and more accurately, and to recover from larger disturbances than passive markers.
* Cameras will always correctly identify an active marker even when no other markers are visible or after an occlusion. This helps the system calibrate more frequently, and to quickly adjust after more significant disturbances.&#x20;
* In a partitioned volume, anchor markers are critical to maintaining a single calibration. Active markers ensure that the cameras can correctly identify each anchor marker location.

{% hint style="info" %}
For continuous calibration to work, It's important to have multiple markers visible to each camera, dispersed across a significant portion of that camera's field of view. This allows the system to more accurately determine the position and angle of the camera. This is true whether using active or passive markers.&#x20;
{% endhint %}

### Anchor Marker Setup

1. First, make sure the entire camera volume is fully [calibrated](./) and prepared for marker tracking.
2. Place any number of markers in the volume to assign them as the anchor markers.
3. Make sure these markers are securely fixed in place within the volume. It's important that the distances between these markers do not change throughout the continuous calibration updates.
4. Open the [Calibration pane](../../motive-ui-panes/calibration-pane.md) and click the right dot on the bottom to access the page with the anchor marker feature.

<figure><img src="../../.gitbook/assets/Calibration Pane - Anchor Markers 1.png" alt="A screenshot of the bottom portion of the Motive Calibration pane, with the Anchor Markers feature  open. "><figcaption></figcaption></figure>



5. In the 3D viewport, select the markers that are going to be assigned as anchors.
6. Click _Add_ to add the selected markers as anchor markers.
7. Once markers are added as anchor markers, magenta spheres will appear around the markers indicating the anchors have been set.
8. Add more anchors as needed.&#x20;

<figure><img src="../../.gitbook/assets/Continuous Calibration - Anchor Markers.png" alt="A screenshot of Motive with the Calibration pane, the 3D viewport, and Cameras view all open. Each pane shows 4 anchor markers that were added to the volume for Continuous Calibration. "><figcaption><p>Anchor markers assigned in Motive.</p></figcaption></figure>

#### Working Anchor Marker&#x20;

* It's critical to Continuous Calibration that anchor markers do not move throughout the tracking process.&#x20;
* If anchor markers do need to be reset, such as when a marker is displaced, clear the existing anchor markers and reassign them.

## Camera Partitions

For multi-room setups, it is useful to group cameras into partitions. This allows Continuous Calibration to run in each individual room without the need for camera view overlap.&#x20;

### Properties Pane: Camera

From the Properties pane of a camera you can assign a Partition ID from the advanced settings.&#x20;

<figure><img src="../../.gitbook/assets/Camera Properties 3-4 General Advanced MARKED UP.png" alt="A screenshot of the Motive camera properties pane, Advanced General settings, with the Partition ID setting highlighted. "><figcaption><p>Change Partition ID under Threshold in the <br>Advanced Settings within the Properties pane. </p></figcaption></figure>

You'll want to assign all the cameras in the same room the same Partition ID. Once assigned these cameras will all contribute to Continuous Calibration for their particular space. This will help ensure the accuracy of Continuous Calibration for each individual space that is a part of the whole system.&#x20;

## Editing Camera Positions with the Gizmo Tool

To manually adjust cameras in the 3D view, enable the advanced setting _Editable in 3D View_ in [General Settings](../../motive-ui-panes/settings/settings-general.md) tab on the [Applications Settings panel](../../motive-ui-panes/settings/).&#x20;

To access advanced settings, click the ![A screenshot of the Motive three-dot menu button.](<../../.gitbook/assets/Motive Context Menu (32).png>) button in the upper right corner and select _Show Advanced_.&#x20;

<figure><img src="../../.gitbook/assets/image (299).png" alt="A screenshot of the Motive Settings panel menu options: Show Advanced and Edit Advanced.  "><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Settings - General Advanced - middle MARKED UP.png" alt="A screenshot of the Motive Application settings panel, General tab, with the Advanced Calibration settings show. The setting &#x22;Editable in 3D View:&#x22; is highlighted. "><figcaption></figcaption></figure>

This allows you to use the [Gizmo Tools](../assets/gizmo-tool-translate-rotate-and-scale.md) to Translate, Rotate, and Scale cameras to their desired locations.&#x20;
