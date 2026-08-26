---
description: An in-depth look at the properties available for ActiveIO devices.
---

# Properties Pane: ActiveIO Devices

## Overview

ActiveIO properties determine how the corresponding ActiveIO device is tracked and provides status information about the device, such as signal strength, battery level, etc. This page covers the properties specific to the following ActiveIO devices:&#x20;

* ActiveIO Puck
* ActiveIO Wand
* ActiveIO Square
* ActiveIO Clips

Select an ActiveIO device in the Devices pane to display the corresponding properties in the [Properties pane](./). These properties can be modified both in Live and Edit mode.&#x20;

Many ActiveIO devices can also be Rigid Body assets in Motive. This page covers the properties specific to ActiveIO. For information about asset properties, please see the [Properties: Rigid Body](properties-pane-rigid-body.md) page.&#x20;

To learn more about pairing an Inertial Measurement Unit (IMU) to a Rigid Body, please see the [IMU Sensor Fusion](../../motive/imu-sensor-fusion.md) page.&#x20;

For general information on using and customizing the Properties pane, see the [Properties pane](./) page. For detailed descriptions of properties for other asset types or devices, please see the following pages:

* [Properties: Take](properties-pane-take.md)
* [Properties: Trained Markerset](properties-pane-trained-markerset.md)
* [Properties: Skeleton](properties-pane-skeleton.md)
* [Properties: Camera](properties-pane-camera.md)
* [Properties: eSync2](properties-pane-esync2.md)
* [Properties: Force Plates](properties-pane-force-plates.md)
* [Properties: NI-DAQ](properties-pane-ni-daq.md)
* [Properties: OptiHub2](properties-pane-optihub2.md)
* [Properties: eSync2](properties-pane-esync2.md)

{% hint style="info" %}
**Advanced Settings**

The Properties pane contains advanced settings that are hidden by default. To access these settings, click the <img src="../../.gitbook/assets/Motive Context Menu (24).png" alt="the Motive 3-dot settings menu button. " data-size="line"> button in the top right corner.&#x20;

Use the _Edit Advanced_ option to customize which settings are in the _Advanced Settings_ category and which appear in the standard view, to show only the settings that are needed specifically for your capture application.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Properties Pane - Show Advanced (3).png" alt="The menu to Show Advanced or Edit Advanced settings in Motive. "><figcaption><p>Show or Edit Advanced Settings.</p></figcaption></figure>

## Active Tag Properties

To view properties related to the ActiveIO device, select it from the Active Tag section of the [Devices pane](../devices-pane.md).&#x20;

{% hint style="warning" %}
The properties shown are for ActiveIO devices. Not all are available for Active Classic devices.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/ActiveIO Standard Properties and Devices Pane.png" alt="The Properties Pane and Devices Pane for an ActiveIO Puck, paired to a Rigid Body."><figcaption><p>Properties Pane for an Active Tag (IMU) paired to a Rigid Body. Standard Properties only. </p></figcaption></figure>

### Details

The Details section displays basic information about the device and IMU.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO Adv Properties - Details.png" alt="The Details section of the ActiveIO device properties, standard and advanced properties shown."><figcaption><p>Standard and Advanced properties in the Details section of the Active Tag properties.</p></figcaption></figure>

<details>

<summary>Device Name</summary>

Identifies the type of device in which the IMU is installed.&#x20;

</details>

<details>

<summary>Tag Type</summary>

Identifies the type of tag in terms of Connection type, number of LEDs, and IMU type, if available.&#x20;

</details>

<details>

<summary>Serial Number</summary>

The serial number of the IMU.&#x20;

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Model (Advanced)</summary>

The internal model number for the IMU.

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Firmware Version <em>(Advanced)</em></summary>

The Firmware version currently installed on the IMU.&#x20;

{% hint style="success" %}
The Firmware will update automatically if necessary when the device connects to Motive.&#x20;
{% endhint %}

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Notes <em>(Advanced)</em></summary>

An open text field for storing custom device information, such as asset tag, location, etc. &#x20;

</details>

### General

The General IMU properties vary depending on the IMU type (ActiveIO or Active Classic) and the connection type (Ethernet or wireless).&#x20;

<figure><img src="../../.gitbook/assets/Properties - RB IMU General Adv (1).png" alt="The General section of the ActiveIO device properties, standard and advanced properties shown."><figcaption><p>Standard and Advanced properties in the General section of the Active Tag properties.</p></figcaption></figure>

<details>

<summary>Enabled</summary>

When enabled, the device is available for tracking in Motive.&#x20;

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Connected LEDs <em>(Advanced)</em></summary>

The number of LED active markers on the device.

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Marker State</summary>

* **Off** turns off the LED pulse so the markers are lit continuously.&#x20;
* **ActiveIO** sets the LEDs to pulse on and off according to a preset pattern.&#x20;
* **Synchronized** sets the LEDs to illuminate every frame.&#x20;

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Pattern Group</summary>

A preset collection of LED patterns that ensures a unique ID for each active marker in the device. Pattern groups also make it easier to assign a different set of patterns to each device in the volume.&#x20;

* Pattern groups each specify 8 marker patterns. Devices with more than 8 markers will occupy the selected pattern group and part of the next group.
* Motive will attempt to prevent overlapping patterns with ActiveIO active tags, but cannot directly read or change the pattern group values of Active Classic devices.
* If running an ActiveIO tag and an Active Classic tag concurrently, you can confirm that the markers are in different pattern groups by selecting them in the 3D view and reading the label that appears.&#x20;
* Motive will also notify users when it detects duplicate active patterns in the scene.

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Illumination</summary>

Indicates the amount of time, in microseconds, that the active LEDs will illuminate per frame when the [Marker State](properties-pane-activeio-devices.md#marker-state) is set to _Synchronized_ or _ActiveIO_.&#x20;

By Default, this property is set to match the camera frame rate.&#x20;

</details>

<details>

<summary>Battery Level</summary>

Indicates the amount of battery power available, in percent.

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Signal Strength</summary>

The strength of the RF signal, in decibel-milliwatts (dBm).&#x20;

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Packet Error Rate</summary>

Displays the percentage of:&#x20;

The number of frames where device data is received / number of frames (over the past 3 seconds)

The rate is updated about every 3 seconds.&#x20;

</details>

<details>

<summary>BaseStation <em>(Advanced)</em></summary>

The serial number of the BaseStation where the active device is connected.&#x20;

{% hint style="info" %}
This property is available only for wireless devices that connect to a BaseStation.&#x20;
{% endhint %}

</details>

<details>

<summary>RF Channel <em>(Advanced)</em></summary>

The radio frequency communication channel used to communicate with the BaseStation for wireless devices.&#x20;

This property is available only for wireless devices that connect to a BaseStation.&#x20;

</details>

<details>

<summary>Quality of Service</summary>

The Quality of Service property allows the device to send the IMU packet multiple times on redundant RF channels to reduce dropped packets in difficult RF environments.

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

<details>

<summary>Device State</summary>

Indicates whether or not the device is connected to the instances of Motive:&#x20;

* Advertising: The device is available but not connected to Motive.&#x20;
* Claimed: The device is connected to Motive.&#x20;

For more information on connecting an ActiveIO device, see the [ActiveIO Configuration](../../activeio/activeio-configuration.md) page.&#x20;

{% hint style="info" %}
This property is available for ActiveIO devices only.&#x20;
{% endhint %}

</details>

### IMU

The IMU section of the Active device properties contains status information about the IMU.&#x20;

Please see the [IMU Sensor Fusion](../../motive/imu-sensor-fusion.md) page for more information on pairing an IMU to a Rigid Body.&#x20;

<figure><img src="../../.gitbook/assets/Properties - RB IMU IMU Adv.png" alt="The IMU section of the ActiveIO device properties, standard and advanced properties shown."><figcaption><p>Standard properties in the IMU section of the Active Tag properties.</p></figcaption></figure>

<details>

<summary>IMU Type</summary>

Identifies the type of IMU in the device.

</details>

<details>

<summary>Paired</summary>

Identifies the rigid body currently paired to the IMU. Lists _None_ if the IMU is currently unpaired.&#x20;

</details>

<details>

<summary>Aligned</summary>

Displays the current state of the IMU pairing.&#x20;

* Unpaired&#x20;
* Paired
* Aligned

</details>

<details>

<summary>Uplink ID <em>(Active Classic devices only)</em></summary>

For Active Classic devices, the Uplink ID is a number programmed to a tag that allows its paired BaseStation to identify it uniquely from other tags. This number should be unique for each device associated with a BaseStation. For wireless devices, the Uplink ID is the second component of the Active Tag name in the Devices pane.&#x20;

</details>
