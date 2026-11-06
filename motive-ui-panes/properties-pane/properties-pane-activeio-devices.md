---
description: An in-depth look at the properties available for the ActiveIO BaseStation.
---

# Properties Pane: ActiveIO BaseStation

## Overview

The Properties pane for the ActiveIO BaseStation displays facts such as device name and serial number, data-transfer rate, firmware details, and available bandwidth for tracking ActiveIO devices. See the [ActiveIO BaseStation page](../../activeio/activeio-hardware/activeio-basestation.md) for instructions on setting up and using an ActiveIO BaseStation. See [Properties Pane: ActiveIO Devices](properties-pane-activeio-devices-1.md) for information specific to the ActiveIO Puck, Wand, Square, and HMD Clips.

For general information on using and customizing the Properties pane, see the [Properties pane](./) page. For detailed descriptions of properties for other asset types or devices, see the following pages:

* [Properties: Take](properties-pane-take.md)
* [Properties: Trained Markerset](properties-pane-trained-markerset.md)
* [Properties: Skeleton](properties-pane-skeleton.md)
* [Properties: Camera](properties-pane-camera.md)
* [Properties: eSync 2](properties-pane-esync2.md)
* [Properties: Force Plates](properties-pane-force-plates.md)
* [Properties: NI-DAQ](properties-pane-ni-daq.md)
* [Properties: OptiHub 2](properties-pane-optihub2.md)
* [Properties: eSync 2](properties-pane-esync2.md)

## ActiveIO BaseStation Properties

As shipped, ActiveIO BaseStations connect to the OptiTrack system without additional configuration by the user.&#x20;

To view properties related to the ActiveIO BaseStation, select the device in the [Devices pane](../devices-pane.md).&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO BaseStation Device + Basic Props + RED BOX.png" alt="An ActiveIO BaseStation shown in Motive software&#x27;s Devices pane."><figcaption></figcaption></figure>

Click the <img src="../../.gitbook/assets/Motive Context Menu.png" alt="" data-size="line"> menu button in the top right corner of the Properties pane and choose Show Advanced device information.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO BaseStation Properties Show Advanced.png" alt=""><figcaption></figcaption></figure>

The Advanced properties appear in three categories: Details, General, and Advanced.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO BaseStation Properties Advanced Shown.png" alt=""><figcaption></figcaption></figure>

If you wish to display any or all of these properties by default rather than in the Advanced area, click Edit Advanced and check (or uncheck) the corresponding boxes. Click Done Editing to activate the changes.

<figure><img src="../../.gitbook/assets/ActiveIO BaseStation Properties Edit Advanced.png" alt=""><figcaption></figcaption></figure>

### Details

The Details section displays basic information about the ActiveIO BaseStation.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO BaseStation Advanced Properties 01 Details.png" alt="The Details section of the Properties pane in Motive software for the OptiTrack ActiveIO BaseStation."><figcaption></figcaption></figure>

<details>

<summary>Device Name</summary>

Identifies the type of device.&#x20;

</details>

<details>

<summary>Model</summary>

The internal model number.&#x20;

</details>

<details>

<summary>Sub-Model</summary>

The internal sub-model number.

</details>

<details>

<summary>Serial Number</summary>

The serial number of the ActiveIO BaseStation.&#x20;

</details>

<details>

<summary>Firmware Version</summary>

The Firmware version currently installed on the device.&#x20;

{% hint style="success" %}
Firmware updates happen automatically, if needed, after the device connects to Motive.&#x20;
{% endhint %}

</details>

<details>

<summary>Logic Version</summary>

The version of the internal hardware logic configuration programmed onto the device.&#x20;

{% hint style="success" %}
Logic configuration updates automatically, if needed, when the device connects to Motive.&#x20;
{% endhint %}

</details>

<details>

<summary>Notes</summary>

An open text field for storing custom device information. &#x20;

</details>

### General

The General section shows the device's refresh rate (the same as frame rate for a camera) and available bandwidth. &#x20;

<figure><img src="../../.gitbook/assets/ActiveIO BaseStation Advanced Properties 02 General.png" alt="The General section of the Properties pane in Motive software for the OptiTrack ActiveIO BaseStation."><figcaption></figcaption></figure>

The General IMU properties vary depending on the IMU type (ActiveIO or Active Classic) and the connection type (Ethernet or wireless).&#x20;

<details>

<summary>Rate</summary>

The rate that data is transferred from ActiveIO devices to the cameras through the BaseStation. This is the equivalent of frame rate for cameras.

</details>

<details>

<summary>Bandwidth Available</summary>

The remaining capacity for the ActiveIO BaseStation to track devices in its range. Each unit can accommodate as many as 70 ActiveIO devices.

</details>

### Advanced

The Advanced section of the ActiveIO BaseStation Properties pane lists the firmware versions currently running on the device’s dual internal radio modules.

<figure><img src="../../.gitbook/assets/ActiveIO BaseStation Advanced Properties 03 Advanced.png" alt="The Advanced section of the Properties pane in Motive software for the OptiTrack ActiveIO BaseStation."><figcaption></figcaption></figure>

<details>

<summary>Radio 1 Version / Radio 2 Version</summary>

The firmware version running the device's radio modules.

</details>

{% hint style="warning" %}
The properties shown are for ActiveIO devices. Not all are available for Active Classic devices.&#x20;
{% endhint %}
