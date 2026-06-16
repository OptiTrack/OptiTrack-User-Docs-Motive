---
description: Instructions to setup and use the OptiTrack active marker solution.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/active-components/active-marker-tracking
---

# Active Marker Tracking

## Overview

The OptiTrack Active Tracking solution allows synchronized tracking of active LED markers using an OptiTrack camera system. Consisting of a [BaseStation](../active-classic-hardware/basestation.md) and one or more active devices such as the  "users choice" [Active Tags](./#active-tag) that can be integrated in to any object, the [Active Puck](./#active-pucks) which can act as its own single Rigid Body, or the [CinePuck](../active-classic-hardware/cinepuck.md), designed to support Virtual Production and broadcast studios.&#x20;

The BaseStation emits RF signals to the active markers, allowing precise synchronization between camera exposure and illumination of the LEDs. Each active marker is uniquely labeled in Motive, allowing more stable Rigid Body tracking since active markers will never be mislabeled and unique marker placements are no longer required for distinguishing multiple Rigid Bodies.

To configure assets that contain active tags and an Inertial Measurement Unit (IMU) such as Pucks and CinePucks, please refer to the article [IMU Sensor Fusion](../../motive/imu-sensor-fusion.md).&#x20;

{% hint style="info" %}
**Notes:**

* This guide is for [OptiTrack active markers](http://optitrack.com/products/active-components/) only. Third-party IR LEDs will not work with the instructions provided on this page.
* This solution is supported only with **Ethernet camera systems** (Slim 13E or Prime series cameras). USB camera systems are not supported.
* Active Tracking works with **Motive versions 2.x or 3.1 and above**. It is not available in version 3.0.
* This guide covers active component **firmware versions 1.0 and above**, which includes all active components that were shipped after _September 2017_.  \
  \
  For active components  shipped prior to _September 2017_, please see the [compatibility notes](../configuration/active-component-firmware-compatibility.md) page for more information about firmware compatibility.
{% endhint %}

## Hardware Setup

### Required Components

#### **BaseStation**

* Emits radio frequency signals to synchronize the active markers.
* Powered by PoE, connected directly via Ethernet cable to one of the switches in the camera network.
* Please see the [BaseStation](../active-classic-hardware/basestation.md) page for product specifications and more information.&#x20;

<img src="../../.gitbook/assets/image (1312).png" alt="BaseStation." width="188">

### Active Marker Options

#### **Active Tags**

<img src="../../.gitbook/assets/image (716).png" alt="Active Tags." width="188">

* Connects to a USB power source to illuminate the active LEDs.
* Receives RF signals from the Base Station and synchronizes illumination of the connected active LED markers accordingly.
* LEDs come in bundles of 4. One or two bundles can be connected to each tag, for a maximum of 8 Active LEDs per Tag.
* Each LED emits 850 nm IR light.
* Size: 5 mm (T1 ¾) Plastic Package, half angle ±65°, typ. 12 mW/sr at 100mA

Please see the page[ Information for Assembling the Active Tags](../active-classic-hardware/information-for-assembling-the-active-tags.md) for more information. &#x20;

#### **Active Pucks**

<img src="../../.gitbook/assets/image (1295).png" alt="Active Puck." width="188">

An active tag self-contained into a trackable object, the Active Puck provides 6 DoF information for any object to which it's attached. Pucks include a factory installed Active Tag with 8 LEDs and a rechargeable battery with up to 10-hours of run time on a single charge.

For product specifications and other information about the Puck, please see the page [Active Puck](../active-classic-hardware/active-puck.md).&#x20;

To configure Pucks that contain an Inertial Measurement Unit (IMU), please refer to the page [IMU Sensor Fusion](../../motive/imu-sensor-fusion.md).&#x20;

#### CinePucks

<figure><img src="../../.gitbook/assets/image (35).png" alt="" width="227"><figcaption><p>CinePuck.</p></figcaption></figure>

Similar to the Active Puck, the CinePuck is designed to attach to a movie camera to support In-Camera Virtual Effects, often referred to as InCam VFX or ICVFX. Please see the page Unreal Engine: OptiTrack InCamera VFX for more information.&#x20;

For product specifications and other information about the CinePuck, please see the page [CinePuck](../active-classic-hardware/cinepuck.md).&#x20;

All CinePucks contain an Inertial Measurement Unit (IMU). Please refer to the page [IMU Sensor Fusion](../../motive/imu-sensor-fusion.md) for instructions to configure the CinePuck.&#x20;

### Wiring the Components

#### **Camera System**

Active tracking is supported only with an Ethernet camera system (Prime series or Slime 13E cameras). For instructions on how to set up a camera system, please refer to the [Ethernet Camera Network Setup](../../hardware/cabling-and-wiring/) chapter.&#x20;

#### **BaseStation**

* Connect the BaseStation to one of the PoE switches within the camera network.
* Metal and other dense materials can cause interference that may reduce the BaseStation's range.  For best performance, place the base station near the center of the tracking space, with unobstructed lines of sight to the areas where the Active Tags will be located during use.&#x20;
* Do not place external electromagnetic or radiofrequency devices near the Base Station.
* When Base Station is working properly, the LED closest to the antenna should blink green when Motive is running.
* The number of Active Devices that can attach to a a single BaseStation is determined by the system frame rate and the divisor applied to the BaseStation. The [BaseStation Load Capacity table](../active-classic-hardware/basestation.md#basestation-load-capacity) on the [BaseStation ](../active-classic-hardware/basestation.md)page shows the IMU maximum for common frame rates and divisors.

{% hint style="info" %}
**BaseStation LEDs**&#x20;

* **Communication Indicator LED:** When the BaseStation is successfully sending data and communicating with the Active Pucks, the LED closest to the antenna will blink green. **If this LED turns red**, it indicates that the BaseStation failed to establish a connection with Motive.
* **Interference Indicator LED:** The middle LED indicates if there are other signal-traffics on the respective radio channel and PAN ID that might be interfering with the active components. This LED should stay dark in order for the active marker system to work properly. **If it flashes in red,** consider switching both the channel and PAN ID on all of the active components.
* **Power Indicator LED:** The LED located at the corner indicates power for the BaseStation. This LED may be disabled on BaseStations with the latest firmware, but on older BaseStations this LED may light up in red to indicate the device has power.
{% endhint %}

#### **Tag Setup**

1. Connect two sets of active markers (4 LEDs in each set) into a Tag.
2. Connect the battery and/or a micro USB cable to power the Tag. The Tag takes 3.3V \~ 5.0V of inputs from the micro USB cable. If powering with a battery, use only the batteries supplied by OptiTrack. To recharge the battery, connect it to the Tag then connect the micro USB cable to a power source.
3. To initialize the Tag, press the power switch once. Be careful not to hold down on the power switch for more than a second, as this will initialize the device in the firmware update (DFU) mode. If it initializes in the DFU mode, which is indicated by two orange LEDs, just power off and restart the Tag. To power off the Tag, hold down on the power switch until the status LEDs go dark.
4. Once powered, you should be able to see the illumination of IR LEDs from the 2D reference camera view.

![BaseStation Setup](<../../.gitbook/assets/image (574).png>)

![Assembled Tags](<../../.gitbook/assets/image (219) (1).png>)

**Puck Setup**

* Press the power button for 1\~2 seconds and release to power the device on.&#x20;
* The top-left LED will turn amber while the Puck initializes. The bottom LED will turn green when the Puck has made a successful connection with the BaseStation, at which point the top-left LED will start blinking green to indicate the sync packets are being received.
* For more information, please read the [Active Puck](../active-classic-hardware/active-puck.md) page.

![Puck initializing. Top-left: Amber.](<../../.gitbook/assets/image (820).png>) ![Connected to BaseStation & receiving sync packets.](<../../.gitbook/assets/image (1348).png>)

### Configuration

As shipped, BaseStations and active devices will connect to the OptiTrack system without additional configuration by the user.  Some circumstances may require a configuration update, such as when adding new BaseStations to an existing system or to change the RF channel or BaseStation divisor rate.&#x20;

The BaseStation is configured outside of Motive, using one of the following programs:

* [Active Batch Programmer](../configuration/active-batch-programmer.md)
* [PuTTy](../configuration/active-hardware-configuration-putty.md)

&#x20;Please see the linked pages for more details on configuring the BaseStation.

## Motive Settings

Use the [Application Settings](../../motive-ui-panes/settings/) panel to customize Motive and set default values. Application Settings can be accessed from the [View menu](../../motive-ui-panes/toolbar-command-bar.md#view) or by clicking the <img src="../../.gitbook/assets/Settings button (10).png" alt="" data-size="line"> icon on the main toolbar.&#x20;

The following settings are relevant to Active Tracking.

### Live Pipeline Solver Tab - Trajectorizer Section&#x20;

[_Settings → Live Pipeline_](../../motive-ui-panes/settings/settings-live-pipeline.md) _→ Solver Tab  -> Trajectorizer_&#x20;

#### **Active Pattern Depth**

Default value:  12

This setting adjusts the complexity of the illumination patterns produced by active markers.&#x20;

In most applications, the default value is sufficient for high quality tracking results. If a large number of Rigid Bodies are tracked simultaneously, increase the value to allow more combinations of illumination patterns on each marker.&#x20;

If this value is set too low, duplicate active IDs can be produced, should this error appear increase the value of this setting.

#### **Minimum Active Count**

Default value:  3

This sets the number of rays required to establish the active ID for each _on_ frame of an active marker cycle.&#x20;

The default value works well for the majority of applications. If this value is increased and active markers become occluded, it may take longer to reestablish those markers in the [Motive 3D Viewport](../../motive-ui-panes/viewport.md#perspective-view).&#x20;

### Views 3D Tab - Markers Section

[_Settings → Views → 3D Tab -> Markers_ ](../../motive-ui-panes/settings/settings-views.md#markers)

The Markers section sets the default color assigned to different types of markers. Markers that are part of an asset will use the color selected in the visuals section of the [Asset Properties](../../motive-ui-panes/properties-pane/properties-pane-rigid-body.md).&#x20;

#### **Active**&#x20;

Default color: blue

The _Active_ setting distinguishes active markers from passive in the [Motive 3D Viewport](../../motive-ui-panes/viewport.md#perspective-view). &#x20;

#### **Intermediate**

Default color: white

Intermediate markers are active markers in a temporary state prior to being identified in Motive. These markers change to the active marker color (or the asset color, if different) once Motive identifies them.&#x20;

## Camera Settings

The following camera settings yield the best tracking results for active LED markers.&#x20;

### Camera Exposure

Set the camera exposure a bit higher than you would when tracking passive markers. This allows the cameras to better detect the active markers. The optimal value will vary depending on the camera system setup, but in general, set the camera exposure between 400 \~ 750, microseconds.

### IR LEDs

When tracking active markers only, the cameras do not need to emit IR lights. In this case, you can disable the LED lights in the [Devices pane](../../motive-ui-panes/devices-pane.md).

![](<../../.gitbook/assets/image (1343).png>)

## Active Devices in Motive

Information about BaseStations and Active Tags is available in the [Devices pane](../../motive-ui-panes/devices-pane.md). Select an item in the Devices pane to view its properties in the [Properties pane](../../motive-ui-panes/properties-pane/). All values are read-only.&#x20;

<figure><img src="../../.gitbook/assets/Devices Pane - Base Station and Active Tag (1).png" alt="" width="248"><figcaption><p>BaseStation and Active Tag in the Devices Pane.</p></figcaption></figure>

### BaseStations

&#x20;BaseStations are listed in the _Synchronization_ category of the Devices pane. Available display options are the _Device_ (device type) and the _Serial number_.

{% hint style="info" %}
The [Active Batch Programmer](../configuration/active-batch-programmer.md) is required to view additional settings or make configuration changes to a Base Station and its associated active devices.&#x20;
{% endhint %}

### Active Tags

Active devices that connect to the camera system via BaseStations are listed in the _Active Tag_ section.  The following properties are available:

* **Name:** the tag name consists of two numbers, the the RF channel used to communicate with the Base Station followed by the unique Uplink ID assigned to the device.&#x20;
* **Paired Asset:**  If the tag is paired to an asset, the asset's name will appear here. Otherwise, the field will display N/A.
* **Aligned:**  shows the status of the Active tag.
  * If the tag is unpaired, the circle x icon will appear. <img src="../../.gitbook/assets/image (1455).png" alt="" data-size="original">
  * If the tag is pairing, the circle with the wave icon will appear. ![](<../../.gitbook/assets/image (1456).png>)
  * If the tag is paired, the green circle with green check icon will appear. ![](<../../.gitbook/assets/image (1457).png>)
* **BaseStation:** displays the serial number of the connected BaseStation. This column is not displayed by default; right-click the header to add it.

## Active Markers in Motive

### Active Labels

Active Markers are reconstructed and tracked in Motive automatically. The unique illumination pattern ensures each active marker is individually labeled, with an Active ID assigned to the corresponding reconstruction. This applies whether or not the Active Marker is part of an asset.&#x20;

The Active IDs can be monitored in the [3D Viewport](../../motive-ui-panes/viewport.md#perspective-view) as part of the marker label, in both Live and Edit modes. To view:

1. Click the <img src="../../.gitbook/assets/image (65).png" alt="" data-size="line"> in the 3D Viewport to open the Visual Aids menu.&#x20;
2. Enable the _Marker Labels_ and the _Active ID_ options.

**Active IDs that are not part of an asset:**

<img src="../../.gitbook/assets/Marker IDs for Unpaired Puck.png" alt="Unique Active IDs assigned to unlabeled active markers." width="536">

**The same Active IDs after asset creation:**

<figure><img src="../../.gitbook/assets/RB - labeled with active IDs on (2).png" alt="" width="536"><figcaption><p>Unique Active IDs assigned to active markers in a Rigid Body.</p></figcaption></figure>

{% hint style="info" %}
Rigid body definitions created using Active Markers will search for specific Active IDs along with the marker placements to track the Rigid Body. See below for more details.&#x20;
{% endhint %}

<img src="../../.gitbook/assets/image (1305).png" alt="" width="375">

{% hint style="danger" %}
**Duplicate active frame IDs**

This Notification displays if more than one marker has the same ID. Duplicate IDs may cause errors during 3D reconstruction. &#x20;

If this occurs, please [contact support](https://help.naturalpoint.com/new-ticket) for assistance.
{% endhint %}

## Active Tags in Rigid Bodies

As noted above, rigid body definitions created from reconstructions with Active IDs will search for those IDs to solve the Rigid Body. This means active markers can be placed in perfectly symmetrical marker arrangements across multiple Rigid Bodies without the risk of labeling swaps.&#x20;

For more information, please see the following pages:

* To create or modify a Rigid Body asset, please see [Rigid Body Tracking](../../motive/rigid-body-tracking/).
* To configure Pucks and CinePucks with IMU sensors, please see [IMU Sensor Fusion](../../motive/imu-sensor-fusion.md).

## Troubleshooting

<details>

<summary><strong>Q : Active markers are flickering in both the 3D viewport and Cameras view in Motive.</strong></summary>

* Flicker can be caused by RF interference. Try changing the RF channel for the BaseStation using the[ Active Batch Programmer.](../configuration/active-batch-programmer.md)&#x20;
* Flickering can also occur if the volume does not have adequate camera coverage. Adjusting the exposure rate can also contribute to better marker detection.

</details>
