---
description: >-
  This page provides instructions to use Active Batch Programmer to configure
  active components.
---

# Active Batch Programmer

## Overview

Active Batch Programmer provides a convenient way of programming multiple OptiTrack components including Active Tags, CinePucks, Pucks, and BaseStations.&#x20;

In general, users should not need to use the batch programmer. Tags and Pucks are pre-configured for every set of devices that ships in the same order, and we ensure none of the Labels overlap.&#x20;

The cases when you would need to reconfigure the active components are:&#x20;

* When you have purchased new Tags/Pucks to add to a system from a previous order.
* When there is a need to change the RF communication channel to avoid interference.

When needed, multiple BaseStations can be connected to the same camera network, as long as they communicate through separate channels.

Please see the [Active Components Hardware](../active-components-hardware/) section for more details and specifications for Active Devices.&#x20;

### **Requirements**

* Windows 10 or 11&#x20;
* BaseStation: Mini USB Data Cable&#x20;
* Active Tag/Puck: Micro USB Data Cable&#x20;
* CinePuck: USB C Data Cable
* To use IMU components, all of the devices, including the BaseStation, must have firmware version 2.x or above installed. To determine the version installed, [attach each device](active-batch-programmer.md#program-active-components) in Read-Only Mode to display its current properties, including the firmware version.

<figure><img src="../../.gitbook/assets/ABP Log BaseStation Read Only.png" alt=""><figcaption><p>Log in read-only mode.</p></figcaption></figure>

{% hint style="info" %}
* If the installed firmware is an older version, please [contact us](https://optitrack.com/contact/) for assistance with upgrading the firmware.
* CinePucks on firmware version 3.x may require assistance from [Support](https://help.naturalpoint.com/) to configure.&#x20;
{% endhint %}

### Download and Install

* Download the Active Batch Programmer installer from the [Developer Tools](https://optitrack.com/support/downloads/developer-tools.html) section of the [OptiTrack Downloads](https://optitrack.com/support/downloads/) page.&#x20;
* Double-click to run the installer.&#x20;

<figure><img src="../../.gitbook/assets/ABP Installer.png" alt=""><figcaption><p>the Active Batch Programmer installer, with EULA.</p></figcaption></figure>

* Review the End User License Agreement, check the box to _agree to the license terms and conditions_, then click _Install_.&#x20;
* The installer will copy a shortcut for the Active Batch Programmer to the Windows desktop.

<figure><img src="../../.gitbook/assets/ABP Desktop Shortcut.png" alt=""><figcaption></figcaption></figure>

## Active Batch Programmer Settings

Open Active Batch Programmer without any components connected.&#x20;

#### Read-Only Mode

Active Batch Programmer opens in Read-Only Mode by default. Once Read-Only Mode is turned off, the current settings are applied when a new device is attached, then powered on.&#x20;

<figure><img src="../../.gitbook/assets/ABP Read-only mode.png" alt=""><figcaption><p>Read-Only Mode is in the bottom left corner.</p></figcaption></figure>

Stay in Read-Only Mode to view the active device's current configuration. Unchecking Read-Only Mode will apply the settings currently selected in the Active Batch Programmer when a device is connected.&#x20;

For this reason, we recommend you always configure the settings you wish to apply first, before connecting any devices or turning off Read-Only Mode.&#x20;

![Active Batch Programmer at launch.](<../../.gitbook/assets/ABP - default settings at open.png>)

### **Batch Information**

A _batch_ of active components contains one BaseStation and the active components that connect to it. These components can be devices such as Pucks and CinePucks or sets of Active Tags.&#x20;

Active Batch Programmer assigns a unique active label to each marker in the batch through _labeling groups._ A labeling group is a set of unique active marker labels that are programmed to the active IR LEDs on the device.

### Set Marker Labels

Applicable to Active Tags/Pucks only, _Set Marker Labels_ is selected by default.

<figure><img src="../../.gitbook/assets/Screenshot 2024-06-18 161633.png" alt=""><figcaption><p>Set Marker Labels options. </p></figcaption></figure>

Marker labels are the active IDs assigned to individual markers, applied to all the markers on a single device or set of active tags as a group. The label group will increment as each new device is attached.&#x20;

* If needed, individual markers can be turned off on a device using the _Disable Markers_ setting.&#x20;
* _Always on Mode_ sets all the markers on the programmed device to 0. This causes the markers to strobe in sync with the exposure of the cameras, without an active pattern, making them appear like passive markers.

{% hint style="warning" %}
**It's important there are no overlapping labels assigned within the same batch.**

When reconfiguring marker labels, program ALL of the Tags and Pucks in the same session, so that labels do not overlap with other components in the system.
{% endhint %}

### Set Radio

Select _Set Radio_ to update the Radio Frequency (RF) Channel. The available RF range is 11-26. All devices in a single batch (BaseStation, Pucks, and/or Active Tags) must use the same RF channel.

<figure><img src="../../.gitbook/assets/ABP Set Radio.png" alt=""><figcaption><p>Set Radio options.</p></figcaption></figure>

* Enter the _RF Channel_ you wish to use. If programming a new device to attach to an existing BaseStation, make sure to assign the same RF channel used by the BaseStation to the new device.
* The _Uplink ID_ property is applied to active devices only and is unique to each device. This number increments as each new device is programmed.&#x20;
* Use the _Signal Intensity_ slider to adjust the radio gain levels, as needed to address interference in the capture volume.&#x20;

{% hint style="info" %}
The Set Radio configuration applies to BaseStations as well as Pucks and Active Tags.
{% endhint %}

### **Set LED Options**

Select _Set LED Options_ to adjust the brightness of the Active IDs.&#x20;

<figure><img src="../../.gitbook/assets/APB Set LED Options.png" alt=""><figcaption><p>Set LED Options.</p></figcaption></figure>

* Use the _Custom Brightness_ setting to select a value between 0 and 100. The Default is 20.
* _Auto Brightness_ sets the value to 50.

## Program Active Components

Once the settings are configured, you are ready to begin the first batch.&#x20;

* Uncheck _Read-Only Mode (just report existing configuration)._

<figure><img src="../../.gitbook/assets/ABP Read-only mode.png" alt=""><figcaption><p>Read-Only Mode.</p></figcaption></figure>

* With the device powered off, attach the BaseStation, Puck or Active Tag to the PC running Active Batch Programmer, using the following cable type:
  * BaseStation: Mini USB data cable&#x20;
  * Active Tag/Puck: Micro USB data cable&#x20;
  * CinePuck: USB C data cable

{% hint style="info" %}
Skip updating the BaseStation if it's already set to the RF Channel you wish to use.
{% endhint %}

* Power on the device and wait for Active Batch Programmer to update the _Current Batch_ information (Active Tags, CinePucks, and Pucks only) and the _Log_.&#x20;
* Once the device is configured, disconnect it and attach the next device. Repeat until all devices in the batch are configured.

<figure><img src="../../.gitbook/assets/APB Batch in progress.png" alt=""><figcaption><p>Active Batch Programmer with a batch in progress.</p></figcaption></figure>

#### Current Batch

The _Current Batch_ field displays summary information about the label groups applied to the devices in the batch. This allows the user to easily track which devices are included in the batch and ensure that duplicate label groups are not assigned.&#x20;

Note that the _Next Label Group_ value has advanced automatically.&#x20;

{% hint style="info" %}
To prevent overlapping label groups, we recommend programming all the devices for each BaseStation in a single batch.
{% endhint %}

Click _Start New Batch_ to program additional BaseStations and devices.

#### Log&#x20;

Monitor the Log while connecting components to make sure configurations are applied successfully. The Log displays detailed information about the device in both read-only mode and when updates are made.&#x20;

* Firmware version
* Existing configuration
* Device serial number
* Details of all the changes applied

Read-only information is displayed in gray with a \[debug] tag, while changes are shown in black with the \[info] tag. If needed, click in the log pane to select and copy the log to paste it into a text file.&#x20;

<figure><img src="../../.gitbook/assets/ABP Log BaseStation RF Updated.png" alt=""><figcaption><p>Log for an update to a BaseStation RF Channel.</p></figcaption></figure>

## Firmware Compatibility

**Firmware Compatibility Chart**

The charts below outline the firmware versions available for BaseStations and Active Tags/Pucks. With  the exception of the CinePuck, the active devices and the BaseStation must be on the same firmware version. The CinePuck uses 3.x firmware and is compatible with BaseStations on 2.x.

For Active Tags specifically, if the device doesn't have an IMU then it's compatible with 1.x. firmware If it has the first version of an IMU, then it is compatible with 2.x. And, if it has an upgraded IMU (i.e., a CinePuck), then it is compatible with 3.x.

{% tabs %}
{% tab title="BaseStation Compatibility Flowchart" %}
![Click image to enlarge.](<../../.gitbook/assets/image (180).png>)
{% endtab %}

{% tab title="Active Tags and Pucks Compatibility Flowchart" %}
![Click image to enlarge.](<../../.gitbook/assets/image (1103).png>)
{% endtab %}
{% endtabs %}
