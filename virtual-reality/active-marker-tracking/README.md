# Active Marker Tracking

This page provides instructions on how to set up and use the OptiTrack active marker solution. To configure assets that contain active tags and an Inertial Measurement Unit (IMU) such as Pucks and CinePucks, please refer to the article [IMU Sensor Fusion](/broken/pages/ysdyrsuQyF9qn6xMu4ix).&#x20;

{% hint style="info" %}
**Additional Note**

* This guide is for [OptiTrack active markers](http://optitrack.com/products/active-components/) only. Third-party IR LEDs will not work with instructions provided on this page.
* This solution is supported for Ethernet camera systems (Slim 13E or Prime series cameras) only. USB camera systems are not supported.
* Motive version 2.0 or above is required.
* This guide covers active component firmware versions 1.0 and above; this includes all active components that were shipped after _September 2017_.
* For active components that were shipped prior to _September 2017_, please see the [compatibility notes](../../active-components/configuration/active-component-firmware-compatibility.md) page for more information about the firmware compatibility.
{% endhint %}

## Overview

The OptiTrack Active Tracking solution allows _synchronized_ tracking of active LED markers using an OptiTrack camera system. Consisting of the **Base Station** and the users choice **Active Tags** that can be integrated in to any object and/or the "Active Puck" which can act as its own single rigid body.

Connected to the camera system the Base Station emits RF signals to the active markers, allowing precise synchronization between camera exposure and illumination of the LEDs. Each active marker is now uniquely labeled in Motive software, allowing more stable rigid body tracking since active markers will never be mislabeled and unique marker placements are no longer be required for distinguishing multiple rigid bodies.

## Hardware Setup

### Required Component

#### **BaseStation**

![](<../../.gitbook/assets/image (1312).png>)

Sends out radio frequency signals for synchronizing the active markers.

* Powered by PoE, connected via Ethernet cable.
* Must be connected to one of the switches in the camera network.

### Active Marker Options

#### **Active Tag**

![](<../../.gitbook/assets/image (716).png>)

* Connects to a USB power source and illuminates the active LEDs.
* Receives RF signals from the Base Station and correspondingly synchronizes illumination of the connected active LED markers.
* Emits 850 nm IR light.
* 4 active LEDs in each bundle and up to two bundles can be connected to each Tag.
* (8 Active LEDs (4(LEDs/set) x 2 set) per Tag)
* Size: 5 mm (T1 ¾) Plastic Package, half angle ±65°, typ. 12 mW/sr at 100mA

#### **Active Pucks**

![](<../../.gitbook/assets/image (1295).png>)

An active tag self-contained into a trackable object, providing information with 6 DoF for any arbitrary object that it's attached to. Carries a factory installed Active Tag with 8 LEDs and a rechargeable battery with up to 10-hours of run time on a single charge.

### Wiring the Components

#### **Camera System**

* Active tracking is supported only with the Ethernet camera system (Prime series or Slime 13E cameras). For instructions on how to set up a camera system see: [Hardware Setup](../../hardware/).

#### **BaseStation**

* Connects to one of the PoE switches within the camera network.
* For best performance, place the base station near the center of your tracking space, with unobstructed lines of sight to the areas where your Active Tags will be located during use. Although the wireless signal is capable of traveling through many types of obstructions, there still exists the possibility of reduced range as a result of interference, particularly from metal and other dense materials.
* Do not place external electromagnetic or radiofrequency devices near the Base Station.
* When Base Station is working properly, the LED closest to the antenna should blink green when Motive is running.

{% hint style="info" %}
**BaseStation LEDs**

_Note: Behavior of the LEDs on the base station is subject to be changed._

* **Communication Indicator LED:** When the BaseStation is successfully sending out the data and communicating with the active pucks, the LED closest to the antenna will blink green. If this LED lights is red, it indicates that the BaseStation has failed to establish a connection with Motive.
* **Interference Indicator LED:** The middle LED is an indicator for determining whether if there are other signal-traffics on the respective radio channel and PAN ID that might be interfering with the active components. This LED should stay dark in order for the active marker system to work properly. If it flashes red, consider switching both the channel and PAN ID on all of the active components.
* **Power Indicator LED:** The LED located at the corner, furthest from the antenna, indicates power for the **B**aseStation.
{% endhint %}

#### **Tag Setup**

* Connect two sets of active markers (4 LEDs in each set) into a Tag.
* Connect the battery and/or a micro USB cable to power the Tag. The Tag takes 3.3V \~ 5.0V of inputs from the micro USB cable. For powering through the battery, use only the batteries that are supplied by us. To recharge the battery, have the battery connected to the Tag and then connect the micro USB cable.
* To initialize the Tag, press on the power switch once. Be careful not to hold down on the power switch for more than a second, because it will trigger to start the device in the firmware update (DFU) mode. If it initializes in the DFU mode, which is indicated by two orange LEDs, just power off and restart the Tag. To power off the Tag, hold down on the power switch until the status LEDs go dark.
* Once powered, you should be able to see the illumination of IR LEDs from the 2D reference camera view.

![](<../../.gitbook/assets/image (588).png>)

![Assembled Tags.](<../../.gitbook/assets/image (1326).png>)

**Puck Setup**

* Press the power button for 1\~2 seconds and release. The top-left LED will illuminate in orange while it initializes. Once it initializes the bottom LED will light up green if it has made a successful connection with the base station. Then the top-left LED will start blinking in green indicating that the sync packets are being received.
* For more information, please read through the [Active Puck](../../active-components/active-components-hardware/active-puck.md) page.

![Puck initializing. Top-left: Orange.](<../../.gitbook/assets/image (820).png>) ![Connected to base station and receiving sync packets.](<../../.gitbook/assets/image (1348).png>)

## Motive Settings

**Active Patten Depth**

Settings → Live Pipeline → Solver Tab with Default value = 12

This adjusts the complexity of the illumination patterns produced by active markers. In most applications, the default value can be used for quality tracking results. If a high number of rigid bodies are tracked simultaneously, this value can be increased allowing for more combinations of the illumination patterns on each marker. If this value is set too low, duplicate active IDs can be produced, should this error appear increase the value of this setting.

**Minimum Active Count**

Settings → Live Pipeline → Solver Tab with Default value = 3

Setting the number of rays required to establish the active ID for each _on_ frame of an active marker cycle. If this value is increased, and active makers become occluded it may take longer for active markers to be reestablished in the Motive view. The majority of applications will not need to alter this setting

**Active Marker Color**

Settings → Views → 3D Tab with Default color = blue

The color assigned to this setting will be used to indicate and distinguish active and passive markers seen in the viewer pane of Motive.

## Camera Settings

For tracking of the active LED markers, the following camera settings may need to be adjusted for best tracking results:

### Camera Exposure

For tracking the active markers, set the camera exposures a bit higher compared to when tracking passive markers. This allows the cameras to better detect the active markers. The optimal value will vary depending on the camera system setups, but in general, you would want to set the camera exposure between 400 \~ 750, microseconds.

### IR LEDs

When tracking only active markers, the cameras do not need to emit IR lights. In this case, you can disable the IR settings in the [Devices pane](../../motive-ui-panes/devices-pane.md).

![](<../../.gitbook/assets/image (1343).png>)

## Active Markers in Motive

### Active Labels

With a BaseStation and Active Markers communicating on the same RF, active markers will be reconstructed and tracked in Motive automatically. From the unique illumination patterns, each active marker gets labeled individually, and a unique marker ID gets assigned to the corresponding reconstruction in Motive. These IDs can be monitored in the [Live-reconstruction mode or in the 2D Mode](../../motive/reconstruction-and-2d-mode.md). To check the marker IDs of respective reconstructions, enable the **Marker Labels** option under the visual aids ([![Viewport16.png](https://v30.wiki.optitrack.com/images/6/6d/Viewport16.png)](https://v30.wiki.optitrack.com/index.php?title=File:Viewport16.png)), and the IDs of selected markers will be displayed. The marker IDs assigned to active marker reconstructions are unique, and it can be used to point to a specific marker within many reconstructions in the scene.

![Unique marker IDs assigned to the active markers.](<../../.gitbook/assets/image (1316).png>)

{% hint style="info" %}
Rigid body definitions that are created from actively labeled reconstructions will search for specific marker IDs along with the marker placements to track the rigid body. Further explained in the following section.
{% endhint %}

{% hint style="danger" %}
**Duplicate active frame IDs**

For the active label to properly work, it is important that each marker has a unique active IDs. When there are more than one markers sharing the same ID, there may be problems when reconstructing those active markers. In this case, the following notification message will show up. If you see this notification, please contact support to change the active IDs on the active markers.
{% endhint %}

![](<../../.gitbook/assets/image (1305).png>)

### Labels in Recorded 3D Data

#### **Unlabeled Markers**

In recorded 3D data, the labels of the unlabeled active markers will still indicate that it is an active marker. As shown in the image below, there will be _Active_ prefix assigned in addition to the active ID to indicate that it is an active marker. This applies only to individual active markers that are not auto-labeled. Markers that are auto-labeled using a trackable model will be assigned with a respective label.

![](<../../.gitbook/assets/image (1132).png>)

#### **Auto-labeled Markers**

When a trackable asset (e.g. rigid body) is defined using active markers, it's active ID information gets stored in the asset along with marker positions. When auto-labeling the markers in the space, the trackable asset will additionally search for reconstructions with matching active ID, in addition to the marker arrangements, to auto-label a set of markers. This can add additional guard to the auto-labeler and prevents and mis-labeling errors.

![](<../../.gitbook/assets/image (1147).png>)

## Rigid Body Definition

Rigid body definitions created from actively labeled reconstructions will search for respective marker IDs in order to solve the rigid body. This gives a huge benefit because the active markers can be placed in perfectly symmetrical marker arrangements among multiple rigid bodies and not run into labeling swaps. With active markers, only the 3D reconstructions with active IDs stored under the corresponding rigid body definition will contribute to the solve.

### Rigid Body Properties

If a rigid body was created from actively labeled reconstructions, the corresponding Active ID gets saved under the corresponding rigid body properties. In order for the rigid body to be tracked, the reconstructions with matching marker IDs in addition to matching marker placements must be tracked in the volume. If the active ID is set to 0, it means no particular marker ID is given to the rigid body definition and any reconstructions can contribute to the solve.

![](<../../.gitbook/assets/image (1108).png>)

## Troubleshooting

<details>

<summary><strong>Q : Active markers are flickering from both the 3D viewport in Motive.</strong></summary>

A:

* Make sure Motive is set to tracking Active markers under the reconstruction settings. The Marker Labeling Mode must be set to either _Active Markers Only_ or _Active and Passive Markers_.
* If flickering occurs on markers of a specific Tag only, try power cycling it. If it tracks fine afterward, the Tag is using v0.8 firmware.

</details>
