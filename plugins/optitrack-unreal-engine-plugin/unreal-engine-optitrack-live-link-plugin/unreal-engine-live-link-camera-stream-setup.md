---
description: >-
  Setup guide to stream video cameras from Motive using the Camera Role in
  Unreal Engine.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/plugins/optitrack-unreal-engine-plugin/unreal-engine-optitrack-live-link-plugin/unreal-engine-live-link-camera-stream-setup
---

# Unreal Engine: Live Link Camera Stream Setup

## Overview

Motive’s Live Link plug-in for Unreal Engine includes the ability to stream tracked rigid bodies for Virtual Production and InCamera VFX (ICVFX).&#x20;

Motive tracks video cameras using a CinePuck, an active device equipped with an IMU. The CinePuck  mounts directly to the video camera and, when aligned with the camera lens as a Rigid Body, tracks the camera's focal point so it can be replicated virtually in the Unreal Engine environment.&#x20;

The Camera Role in Unreal Engine can now be used for the Tracked Camera Rigid Body. This means that you can now connect a lens file with the associated Live Link Camera Role Asset. In Unreal Engine, users can calibrate for lens distortion and nodal offset, and use the camera with a Lens Encoder, if desired.&#x20;

This document provides instructions to setup and link a Rigid Body in Motive to a Live Link Camera Role in Unreal Engine. For information on ICVFX production in general, please see the page [Unreal Engine: OptiTrack InCamera VFX](../../../virtual-production/unreal-engine-optitrack-incamera-vfx.md).&#x20;

{% hint style="info" %}
We used the standard _InCameraVFX_ template in Unreal Engine for our sample project. The template includes all the necessary macros and assets needed for virtual production.&#x20;

This template is located under _Film / Video & Live Events_ in the Unreal Project Browser. &#x20;
{% endhint %}

## Create Camera Asset in Motive

Motive will stream the camera as a Live Link Rigid Body asset.&#x20;

#### Connect the CinePuck and BaseStation

* Plug the [BaseStation](../../../active-classic/active-classic-hardware/basestation.md) into one of the Power over Ethernet (PoE) switches on the OptiTrack camera network.&#x20;
* Firmly attach the [CinePuck](../../../active-classic/active-classic-hardware/cinepuck.md) to the Studio Camera using the SmallRig NATO Rail and Clamps on the cage of the camera.
* The CinePuck can be mounted anywhere on the camera. For best results, put the puck closer to the lens.
* Power on the CinePuck, and let it calibrate the IMU bias. The lights will flash red and orange during calibration and change to green when done.

{% hint style="info" %}
We recommend powering the CinePuck with a USB cable while filming to avoid running out of battery power. A light on the CinePuck will indicate when the power is connected.
{% endhint %}

![CinePuck mounted via SmallRig NATO rig.](<../../../.gitbook/assets/CinePuck mouted to NATO rig.png>)

#### Create a Rigid Body

A CinePuck is tracked in Motive as a Rigid Body asset. For detailed instructions on creating a [rigid body asset](../../../motive-ui-panes/builder-pane.md#rigid-body-create), Please see the [Builder pane](../../../motive-ui-panes/builder-pane.md) page. For instructions on pairing the IMU, please see the [IMU Sensor Fusion](../../../motive/imu-sensor-fusion.md) page.&#x20;

## Attach the Camera Role in Unreal Engine

* In Unreal Engine, click the <img src="../../../.gitbook/assets/UE Add Source Button (1).png" alt="" data-size="line"> button on the Live Link tab to add a new Live Link source.
* Select _OptiTrack Source_, check _Connect Automatically_, enter the IP address for the Motive PC in the _Server Address_ field, the IP address for the Unreal PC in the _Client Address_ field, and click _Create_. Enter 127.0.0.1 in both fields if running both on the same PC. Leave the Connection Type as Multicast and click create.

<figure><img src="../../../.gitbook/assets/UE - LiveLink Connect to Source.png" alt=""><figcaption><p>Add a Live Link source in Unreal Engine.</p></figcaption></figure>

* This will display a list of assets streaming from Motive. Note that the rigid body camera, named _HandCam2_, is currently in the Transform role.
* Click _OptiTrack_ in the Subject list to display the OptiTrack Live Link Properties.&#x20;

<figure><img src="../../../.gitbook/assets/Live Link Select OptiTrack.png" alt=""><figcaption><p>Unreal Engine Properties for the OptiTrack Live Link plug-in.</p></figcaption></figure>

* In the _Live Link Roles_ section, click the _Live Link Subject_ dropdown. This will open the list of Assets streaming from Motive.&#x20;
* Select the camera asset, _HandCam2_ in this example.

<figure><img src="../../../.gitbook/assets/Live Link Select LL Subject.png" alt=""><figcaption><p>Select a Live Link Subject in Unreal Engine.</p></figcaption></figure>

* Directly below the Live Link Subject field is a check box to _Stream as Camera (Rigid Bodies Only)_. Check this box to apply the Camera Role to the camera rigid body (HandCam2).&#x20;

<figure><img src="../../../.gitbook/assets/Live Link Stream as Camera setting.png" alt=""><figcaption><p>Stream as Camera setting in Unreal Engine.</p></figcaption></figure>

## Configure Camera for Streaming

### Add OptiTrack LiveLinkDisplay

Click the <img src="../../../.gitbook/assets/Unreal Engine Quick Add button.png" alt="" data-size="line"> Quick Add button and start typing _OptiTrack_ over the menu to activate the search function.  Select the OptiTrack Live Link Display from the list of available options.

<figure><img src="../../../.gitbook/assets/Live Link Add OptiTrackNDisplay.png" alt=""><figcaption><p>Searching from the UE Quick Add button.</p></figcaption></figure>

Move all the NDisplay assets to nest under _OptitrackLiveLinkDisplay &#x69;_&#x6E; the Outliner pane.

### Add the LiveLinkController

* Select the video camera, now nested under _OptitrackLiveLinkDisplay &#x69;_&#x6E; the Outliner pane..&#x20;
* In the Details pane, click the <img src="../../../.gitbook/assets/Live Link Add Component button (5).png" alt="" data-size="line"> Add button to add a new component to the camera.

<figure><img src="../../../.gitbook/assets/Live Link Camera Add Component.png" alt=""><figcaption><p>Camera Details in Unreal Engine: Add a new component.</p></figcaption></figure>

* Search for and select the _Live Link Controller_ component.&#x20;

<figure><img src="../../../.gitbook/assets/Live Link - Add component search results.png" alt=""><figcaption></figcaption></figure>

* Properties for the new Controller will display in the Camera details pane.&#x20;
* Click the dropdown next to _Subject Representation_ and select the camera Rigid Body.&#x20;
* The _Subject_ and _Role_ fields will both update to display the name of the Rigid Body name.&#x20;

{% hint style="info" %}
The _LiveLinkController_ label can only be applied to Rigid Body assets.&#x20;
{% endhint %}

<figure><img src="../../../.gitbook/assets/Live Link Select Subject Representation.png" alt=""><figcaption><p>Properties for a new Live Link Controller component in Unreal Engine.</p></figcaption></figure>

## Camera Calibration

As noted above, Unreal Engine includes properties that allow you to calibrate a video camera streaming into Unreal Engine. This includes the ability to use a lens encoder with the camera.

#### Lens Encoder

When using a Lens Encoder or a calibrated Lens in Unreal Engine, use the Lens File Picker settings to select the appropriate Lens File.

<figure><img src="../../../.gitbook/assets/Live Link Camera Lens File Picker.png" alt=""><figcaption><p>Live Link Component Camera Role properties in Ureal Engine.</p></figcaption></figure>

{% hint style="info" %}
Please see [Camera Lens Calibration Overview in Unreal Engine](https://docs.unrealengine.com/4.27/en-US/WorkingWithMedia/IntegratingMedia/CameraCalibration/Overview/) for more information on calibrating cameras and working with lens files in Unreal Engine.&#x20;
{% endhint %}
