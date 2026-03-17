---
description: An overview of the Continuous Calibration pane and its functions.
---

# Continuous Calibration Pane

## Overview

The Continuous Calibration pane is used to manage and monitor the Continuous Calibration process. This pane is accessed under the [View tab](https://docs.optitrack.com/motive-ui-panes/toolbar-command-bar#view) in Motive or by clicking the ![A screenshot of the Continuous Calibration button from the Motive toolbar. ](<../../.gitbook/assets/Continuous Calibration Button (1).png>) icon on the main toolbar.

{% hint style="success" %}
The Continuous Calibration feature can be enabled from either the Calibration pane or the Continuous Calibration pane.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Continuous Calibration Pane - all OK.png" alt="A screenshot of the Motive Continuous Calibration pane, with 4 Anchor Markers and 1 partition. "><figcaption></figcaption></figure>

## Camera Samples

The Camera Samples section provides a visual aid to show which cameras need more marker samples or a better distribution of marker samples for Continuous Calibration to work.

### More Markers

A minimum of four markers are required for continuous calibration to work. The _More Markers_ section displays the cameras that require additional markers in their field of view to meet the minimum.&#x20;

<figure><img src="../../.gitbook/assets/CC - Camera Samples needed - multi.png" alt="A screenshot of the Camera Samples section of the Continuous Calibration pane in Motive, showing that 4 cameras need More Markers, but none need better distribution."><figcaption></figcaption></figure>

Click any of the camera buttons within the _Camera Samples_ section to select the camera. This will also select the camera in the _2D Camera Viewport_ and _Devices_ pane.&#x20;

If a camera appears under _More Markers_:

1. Select the camera under _More Markers_.
2. Navigate to the _2D Viewport_ and from the top left dropdown select _From Camera x_.&#x20;
3. The Viewport will show the camera's field of view and any markers it can see within the cyan box.&#x20;
4. Add additional markers within the camera's view until the camera button is removed from _More Markers_.

<figure><img src="../../.gitbook/assets/CC - Camera Perspective - more markers needed.png" alt="A screenshot of the 2D camera view from a selected camera, showing the camera&#x27;s field of view, with 2 markers recognized and 2 markers just outside of the Field of View."><figcaption></figcaption></figure>

{% hint style="info" %}
* Markers within the field of view that are receiving good tracking rays will appear with a <mark style="color:green;">green</mark> diamond encompassing the marker.&#x20;
* Markers outside of the FOV will appear standard white.&#x20;
* Markers within FOV that have untracked rays will appear with a <mark style="color:red;">red</mark> diamond encompassing the marker.&#x20;
{% endhint %}

### Better Distribution

You may have enough markers so that there are no cameras listed under _More Markers,_ but still see cameras under _Better Distribution._

1. Select a camera listed under _Better Distribution_.
2. Navigate to the _2D Viewport_ and from the top left dropdown select _From Camera x_.
3. This will show the camera's field of view and any markers that it can see within the cyan box.&#x20;
4. Add additional markers that are more evenly distributed within the camera's view.&#x20;

<figure><img src="../../.gitbook/assets/image (1440).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
For Better Distribution, oftentimes all you need is a single additional marker separated from another cluster of markers, as seen in the image above.&#x20;
{% endhint %}

## Anchor Markers

Anchor markers can further improve continuous calibration. When properly configured, anchor markers improve continuous calibration updates, especially on systems that consists of multiple sets of cameras that are separated into different tracking areas, by obstructions or walls, without camera view overlap.&#x20;

Anchor Markers also provide extra assurance that the global origin will not shift during each Continuous Calibration update, although the Continuous Calibration feature itself already checks for this.

<figure><img src="../../.gitbook/assets/CC - with Active IDs displayed.png" alt="A screenshot of the Anchor Markers section of the Continuous Calibration pane in Motive. The section shows the Name of the Anchor marker, the Active ID, Tracked status, and Distance. "><figcaption></figcaption></figure>

The _Anchor Markers_ section allows you to add/remove and import/export Anchor markers. It also shows the mean error under the Distance column for each individual Anchor marker and the overall in the top right in millimeters.&#x20;

Right click the header to add or remove columns, such as the Active ID column.

* When the icon in the top right is a <mark style="color:green;">green</mark> circle with a check, all Anchor markers are visible by at least one camera.&#x20;
* When the icon is a <mark style="color:red;">red</mark> circle with an x, at least one Anchor marker is occluded from all cameras.&#x20;

{% hint style="info" %}
For additional information regarding Anchor markers, please see this [page](continuous-calibration.md#anchor-markers).&#x20;
{% endhint %}

## Partitions

<figure><img src="../../.gitbook/assets/image (1442).png" alt=""><figcaption></figcaption></figure>

For multi-room setups, it is useful to group cameras into partitions. This allows for Continuous Calibration to run in each individual room without the need for camera view overlap.&#x20;

The Partitions section directly corresponds with Partitions created in the _Properties_ pane for each individual camera. This section displays the status of Continuous Calibration for each partition.&#x20;

{% hint style="info" %}
For more information, please see the Partitions section [here](continuous-calibration.md#camera-partitions).&#x20;
{% endhint %}

{% hint style="warning" %}
If a Partition or Partitions are not receiving enough marker data to validate or update, they will appear magenta in the table and a <mark style="color:red;">red</mark> circle with an x icon will appear in the top right of the section.&#x20;
{% endhint %}

### Partition Table Columns

#### No.

This is the Partition ID assigned via the camera's Properties pane. By default this value is 1.&#x20;

#### Status

* **Idle** - Continuous Calibration is either turned off or there are not enough markers for Continuous Calibration to begin sampling.&#x20;
* **Sampling** - Continuous Calibration is collecting marker samples.&#x20;
* **Evaluating** - Continuous Calibration is determining if the latest samples are better than the previous and will update if necessary.&#x20;
* **Processing** - Processing will occur when an update is processing.&#x20;

#### Last Validated

Last Validated will update the timestamp to 0h 0m 0s when the samples have been collected and the calibration solution was not deemed to be better than the solution already in place.&#x20;

#### Last Updated

Last Updated will update the timestamp to 0h 0m 0s when good samples were collected and the calibration solution was deemed better than the solution in place.&#x20;

#### Error

This is the mean ray error for each partition in millimeters. The overall mean ray error will be displayed in the top right corner of the section.&#x20;

#### Anchors

This column denotes the number of Anchor markers that are visible within a partition.&#x20;

### Partitions Settings

Click the <img src="../../.gitbook/assets/Pane Settings toggled OFF (1).png" alt="A screenshot of the Motive Pane Settings button, in a toggle OFF state. " data-size="line"> button at the bottom of the Continuous Calibration pane to open the Settings panel.&#x20;

<figure><img src="../../.gitbook/assets/image (1443).png" alt=""><figcaption></figcaption></figure>

The Partitions settings establish the thresholds that determine the quality of the partition's calibration. If a partition fails to meet any of the set thresholds, the row will turn magenta in the _Partitions_ list.&#x20;

<figure><img src="../../.gitbook/assets/image (1444).png" alt=""><figcaption></figcaption></figure>

#### Maximum Error

If the ray error for a Partition exceeds the Maximum Error value, the text in the Partition's row will change to magenta and the icon on the top right of the Partition section will display a red circle with an 'x'.&#x20;

This setting can be changed to any positive decimal.&#x20;

#### Maximum Last Updated

Maximum Last Updated dictates how long Continuous Calibration can go without an update before the user is alerted (by a magenta text and a red circle with an 'x' icon) that Continuous Calibration has not been updated.&#x20;

## Bumped Cameras

The Bumped Cameras features corrects a camera's position in Motive if it is physically bumped in the real 3D space.&#x20;

<figure><img src="../../.gitbook/assets/image (1445).png" alt=""><figcaption></figcaption></figure>

### Quick Start Guide

{% hint style="danger" %}
Bumped Cameras needs to be enabled in the Info pane when initializing Continuous Calibration for any fixes to be applied. If it is NOT enabled and a camera is physically displaced, you will need to run a full Calibration to ensure accurate tracking.&#x20;
{% endhint %}

1. Create Anchor markers from the [Anchor Markers](continuous-calibration-pane.md#anchor-markers) section or add Active markers.&#x20;
2. Enable Bumped Cameras from the Bumped Cameras Settings:
   1. Select Camera Samples for _Mode._
   2. Select either Anchor Markers, Active Markers, or Both from _Marker Type_.
3. Bumped Cameras is now able to correct physical camera movement without needing a full Calibration.&#x20;

To see the results of Bumped Cameras steps above you can do the following:

{% hint style="info" %}
The steps below are not necessary, but something you can do to see Bumped Cameras work in action.&#x20;
{% endhint %}

1. Select the camera's view you intend to physically move in the 2D Camera Viewport.&#x20;
2. Make sure Tracked and Untracked Rays are visible from the 'eye' icon in the 2D Camera Viewport.&#x20;
3. Physically move the camera so that the markers appear with a red diamond around them (untracked).
4. Wait a few seconds and notice the camera's view shift to correct in the 2D Camera Viewport.&#x20;
5. The red diamonds should now be green.&#x20;

<figure><img src="../../.gitbook/assets/image (1446).png" alt=""><figcaption><p>Before Bumped Camera Correction (left), After Bumped Camera Correction (right). </p></figcaption></figure>

### Bumped Cameras Settings

<figure><img src="../../.gitbook/assets/image (1447).png" alt=""><figcaption></figcaption></figure>

#### Mode

* **Disabled** - When Mode is set to Disabled, Bumped Camera correction will not apply.&#x20;
* **Camera Samples** - When Mode is set to Camera Samples, Bumped Camera correction will correct based on the Camera Samples data. If Camera Samples is populated with cameras this will trigger Bumped Cameras to correct any cameras that may have moved. If a camera has NOT moved, this camera will remain idle in the Bumped Camera section until Camera Samples is clear of needed samples or distribution.&#x20;
* **Selected Cameras** - When Mode is set to Selected Cameras, this will ONLY correct the camera that is selected by the user from either the Devices, 3D or 2D viewport, or Camera Samples.&#x20;

{% hint style="warning" %}
A camera MUST be selected during a bump for Selected Cameras mode to correct the camera's position.&#x20;

It must also be de-selected after the camera posistion has been corrected, else the feature will continue to consume high CPU resources and left long term could have a negative effect in quality tracking.&#x20;
{% endhint %}

#### Marker Type

* **Anchor Markers** - ONLY Anchor Markers will be used to collect data for Bumped Cameras to correct a camera's position.&#x20;
* **Active Markers**  - ONLY Active Markers will be used to collect data for Bumped Cameras to correct a camera's position.&#x20;
* **Anchor and Active**  - BOTH Anchor and Active Markers will be used to collect data for Bumped Cameras to correct a camera's position.&#x20;

#### Max Camera Count

If you only wish to have a few cameras corrected you can lower the count of the Max Camera Count. By default this is set to 20.&#x20;
