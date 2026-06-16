---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/measurement-probe-kit-guide
---

# Measurement Probe Kit Guide

This page provides information and instructions on how to utilize the Probe Measurement Kit.

## Overview

Measurement probe tool utilizes the precise tracking of OptiTrack mocap systems and allows you to measure 3D locations within a capture volume. A probe with an attached Rigid Body is included with the purchased measurement kit. By looking at the markers on the Rigid Body, Motive calculates a precise x-y-z location of the probe tip, and it allows you to collect 3D samples in real-time with sub-millimeter accuracy. For the most precise calculation, a probe calibration process is required. Once the probe is calibrated, it can be used to sample single points or multiple samples to compute distance or the angle between sampled 3D coordinates.

**Measurement kit includes:**

* Measurement probe
* Calibration block with 4 slots, with approximately 100 mm spacing between each point.

![Measurement probe.](<../.gitbook/assets/image (1394).png>) ![Calibration block with slots for the probe tip.](<../.gitbook/assets/image (1363).png>)

## Using the Probe

This section provides detailed steps on how to create and use the measurement probe. Please make sure the camera volume has been [calibrated](calibration/) successfully before creating the probe. System calibration is important on the accuracy of marker tracking, and it will directly affect the probe measurements.

### Step 1: Probe Calibration

**Creating a probe using the Builder pane**

1. Open the [Builder pane](../motive-ui-panes/builder-pane.md) under [View tab](../motive-ui-panes/toolbar-command-bar.md#view) and click _Rigid Bodies_.
2. Bring the probe out into the tracking volume and create a [Rigid Body](rigid-body-tracking/) from the markers.
3. Under the _Type_ drop-down menu, select _Probe_. This will bring up the options for defining a Rigid Body for the measurement probe.
4. Select the Rigid Body created in step 2.
5. Place and fit the tip of the probe in one of the slots on the provided calibration block.
6. Note that there will be two steps in the calibration process: refining Rigid Body definition and calibration of the pivot point. Click _Create_ button to initiate the probe refinement process.
7. Slowly move the probe in a circular pattern while keeping the tip fitted in the slot; making a cone shape overall. Gently rotate the probe to collect additional samples.
8. After the refinement, it will automatically proceed to the next step; the pivot point calibration.
9. Repeat the same movement to collect additional sample data for precisely calculating the location of the pivot or the probe tip.
10. When sufficient samples are collected, the pivot point will be positioned at the tip of the probe and the _Mean Tip Error_ will be displayed. If the probe calibration was unsuccessful, just repeat the calibration again from step 4.
11. Once the probe is calibrated successfully, a probe asset will be displayed over the Rigid Body in Motive, and live x/y/z position data will be displayed under the [Probe pane](../motive-ui-panes/probe-pane.md).

![Creating measurement probe in Motive](<../.gitbook/assets/image (469).png>)

{% hint style="danger" %}
**Caution**

* The probe tip _MUST_ remain fitted securely in the slot on the calibration block during the calibration process.
* Also, do not press in with the probe since the deformation from compressing could affect the result.
{% endhint %}

{% hint style="info" %}
**Note: Custom Probes**

It's highly recommended to use the Probe kit when using this feature. With that being said, you can also use any markered object with a pivot arm to define a custom probe in Motive, but when a custom probe is used, it may have less accurate measurements; especially if the pivot arm and the object are not rigid and/or if any slight translation occurs during the probe calibration steps.
{% endhint %}

### Step 2: Sample Collection

**Using the Probe pane for sample collection**

1. Under the _Tools_ tab, open the [Probe pane](../motive-ui-panes/probe-pane.md).
2. Place the probe tip on the point that you wish to collect.
3. Click _Take Sample_ on the Measurement pane.
4. A Virtual Reference point is constructed at the location and the coordinates of the point are displayed in the [Probe Pane](../motive-ui-panes/probe-pane.md). The points location can be [exported from the Probe Pane](measurement-probe-kit-guide.md#export-samples) as a .CSV file.
5. Collecting additional samples will provide distance and angles between collected samples.

![Sampling 3D points using the measurement probe.](<../.gitbook/assets/image (302).png>)

![Probe pane displaying live 3D position of
&#x20;the probe tip, and position, distance, and&#x20;
angle of the previously collected points.](<../.gitbook/assets/image (470).png>)

## Export Samples

As the samples are collected, their coordinate data will be written out into the CSV files automatically into the OptiTrack documents folder which is located in the following directory: **C:\Users\\**_**\[Current User]**_**\Documents\OptiTrack**. 3D positions for all of the collected measurements and their respective RMSE error values along with distances between each consecutive sample point will be saved in this file.

Also, If needed, you can trigger Motive to export the collected sample coordinate data into a designated directory. To do this, simply click on the export option on the Probe pane.

![Exporting sampled points from the Probe pane.](<../.gitbook/assets/image (1359).png>)

## Real-time Streaming

The location of the probe tip can also be streamed into another application in real-time. You can do this by [data-streaming](data-streaming.md) the probe Rigid Body position via [NatNet](../developer-tools/natnet-sdk/natnet-4.5.md). Once calibrated, the pivot point of the Rigid Body gets positioned precisely at the tip of the probe. The location of a pivot point is represented by the corresponding Rigid Body x-y-z position, and it can be referenced to find out where the probe tip is located.
