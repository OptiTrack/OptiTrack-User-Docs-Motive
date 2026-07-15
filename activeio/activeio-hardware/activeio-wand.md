---
description: A Quick Start Guide and specifications for the ActiveIO Wand.
---

# ActiveIO Wand

## Overview

The high-powered ActiveIO Wand uses ActiveIO technology for more efficient and accurate calibrations. Unlike classic calibration wands, which contain passive markers that reflect light back to the camera, the ActiveIO Wand has LED markers that emit light rather than reflecting it, making it ideal for calibrating systems with SlimX cameras and large volumes.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO-Wand-shadow.png" alt="An ActiveIO Wand in the Open position, with the markers face down. " width="563"><figcaption></figcaption></figure>

Please consult our [ActiveIO Configuration](../activeio-configuration.md) page for more information on configuring and working with ActiveIO devices. &#x20;

## Quick Start Guide

### Requirements

* [ActiveIO BaseStation](activeio-basestation.md)
* Motive 3.5 or higher

Please see the [ActiveIO Wand Extension Pole](activeio-wand-extension-pole-adapter.md) page for instructions on connecting the optional extension pole accessory.

## Control Panel

The control panel for the ActiveIO Wand is located in the center of the wand, near the handle.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO Wand Controls - photo.jpg" alt="Photo of the ActiveIO Wand control panel. "><figcaption></figcaption></figure>

### Power

The ActiveIO Wand is powered by an internal battery that allows for 15W USB fast charging. The device ships with a USB-C cable and a wall charger. Charge the device before first use.&#x20;

<figure><img src="../../.gitbook/assets/Active Wand Controls - Power slot highlighted (1).png" alt="A technical drawing of the ActiveIO Wand control panel, with the USB-C slot highlighted. "><figcaption><p>The USB-C charging slot on the ActiveIO Wand. </p></figcaption></figure>

To power the device on or off, press the Power button. Once the device is powered on, it will be available in Motive.&#x20;

<figure><img src="../../.gitbook/assets/Active Wand Controls - Power Button highlighted.png" alt="A technical drawing of the ActiveIO Wand control panel, with the power button highlighted. "><figcaption><p>The Power button on the ActiveIO Wand.</p></figcaption></figure>

#### Mounting The Wall Charger&#x20;

The wall charger has a magnetic back to attach to any metal surface. 4 mounting holes accommodate 1/4-20 screws or M6 bolts for mounting to other surfaces.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO Wand Charger - technical drawing.png" alt="A technical drawing of the ActiveIO Wand charger. "><figcaption></figcaption></figure>

With the ActiveIO Wand in the closed position, insert the USB-C plug on the wall charger into the corresponding slot on the ActiveIO Wand, and slide the wand handle into the grip, like so:

<figure><img src="../../.gitbook/assets/ActiveIO Wand Charging.png" alt="An ActiveIO Wand in the closed position, mounted into the wall-mounted charger. "><figcaption></figcaption></figure>

The wall charger will display the ActiveIO Wand's indicator lights on the right side.&#x20;

### Sync Modes

The ActiveIO Wand has two operating modes, Sync and Always On. The switch on the control panel allows you to change the mode when the device is not connected to to an ActiveIO BaseStation.&#x20;

<figure><img src="../../.gitbook/assets/Active Wand Controls - sync switch highlighted.png" alt="A technical drawing of the ActiveIO Wand control panel, with the sync switch highlighted. "><figcaption><p>The Sync switch on the ActiveIO Wand.</p></figcaption></figure>

{% hint style="info" %}
When connected to an ActiveIO BaseStation, the control panel switch will remain in Sync mode, even when the marker state in Motive is set to Always On mode.&#x20;
{% endhint %}

#### Sync

In Sync mode, the ActiveIO Wand is synced with an ActiveIO BaseStation. In this state, the Infrared marker LEDs flash in sync with the camera exposures. This allows the IR markers to be as bright and as visible as possible, while reducing battery power consumption.&#x20;

The middle LED indicator light flashes blue when in this mode.

#### Continuous

In Continuous mode, the IR LEDs emit constant light with no blinking and are not synced with the camera exposure. This mode does not require an ActiveIO BaseStation. The markers may appear dimmer to the cameras and battery life will be reduced when compared to Sync mode.&#x20;

The middle LED indicator light is solid green in this mode.

### Indicator Lights

The ActiveIO Wand has three indicator lights on the control panel.&#x20;

#### Power

The left LED (the lightning bolt symbol) indicates battery strength and charging.

<figure><img src="../../.gitbook/assets/Active Wand Controls - Power light highlighted.png" alt="A technical drawing of the ActiveIO Wand control panel, with the Power Indicator light highlighted. "><figcaption><p>The Power indicator light on the ActiveIO Wand.</p></figcaption></figure>

* Solid blue: battery power is good.
* Solid orange: the battery is low and should be charged.&#x20;
* Blinking red: the battery is critically low and needs to be charged. The IR LEDs are disabled in this state.&#x20;
* Blinking green: the battery is charging.
* Solid green: the device is fully charged.

{% hint style="info" %}
The light flashes red if a charging error occurs. Disconnect and reconnect the device if this happens. If the problem persists, [contact Support](https://optitrack.com/support#create-new-support-ticket).&#x20;
{% endhint %}

#### Sync State



The middle LED (the light emitting dome symbol) indicates which sync mode the device is in.&#x20;

<figure><img src="../../.gitbook/assets/Active Wand Controls - Sync light highlighted.png" alt="A technical drawing of the ActiveIO Wand control panel, with the Sync State Indicator light highlighted. "><figcaption><p>The Sync state indicator light on the ActiveIO Wand.</p></figcaption></figure>

* Blinking blue: the ActiveIO Wand is in sync mode.
* Blinking green: the device is scanning.
* Solid green: the device is in Continuous mode

#### IMU&#x20;

The right LED (the gyro symbol) is disabled on the ActiveIO Wand.

<figure><img src="../../.gitbook/assets/Active Wand Controls - Power IMU light highlighted.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
#### Firmware Updates

Every time the ActiveIO Wand connects to a new instance of Motive, the system does a firmware check and updates the device to the applicable firmware for the version of Motive. All three indicator lights will cycle through the rainbow during a firmware update. &#x20;
{% endhint %}

## Motive Setup

The first time Motive detects the ActiveIO Wand, it appears in the [Devices pane](../../motive-ui-panes/devices-pane.md) in an Advertising state. Right-click to claim it and make it available for use in that instance of Motive. Select it to view the Device properties.&#x20;

{% hint style="info" %}
#### Using the Wand with Multiple Instances of Motive

Once claimed, the ActiveIO Wand will remain available in that version of Motive. You must release the device first to claim it in another instance of Motive.&#x20;

* Within Motive, Right-click the device in the Devices pane and select _Release_.&#x20;
* On the device, triple-click the power button to release it from the system.

See the page [ActiveIO Configuration](../activeio-configuration.md) for more detail on connecting and configuring ActiveIO devices. &#x20;
{% endhint %}

When powered on in Sync mode, the ActiveIO Wand connects to Motive through an ActiveIO BaseStation.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO Wand in AIO Sync mode Props and Device Panes.png" alt=""><figcaption><p>The ActiveIO Wand Basic Properties when the wand is in Sync (ActiveIO) mode. </p></figcaption></figure>

When powered on in Always On mode, the ActiveIO Wand will appear in the Devices pane, with fewer editable properties.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO Wand Devices and Adv Properties.png" alt="A screenshot of the Motive Properties and Devices pane, with the ActiveIO Wand selected, and Advanced properties displayed. "><figcaption><p>The ActiveIO Wand Advanced Properties when the wand is in Continuous mode. </p></figcaption></figure>

#### Notes (Advanced)

The Notes field is an optional freeform text field for user-defined content. Click the  button and select Show Advanced if the field is not visible.&#x20;

#### Marker State

The Marker State dropdown allows you to change between Patterned mode (ActiveIO), Always On mode (Synchronized), and Continuous Illumination mode (Off) when the device is synced.&#x20;

{% hint style="success" %}
For best results, we recommend using the ActiveIO Wand in Synchronized mode.&#x20;
{% endhint %}

If the device is set to run in Always On mode, the Marker State is a read-only property, set to _Off_.&#x20;

{% hint style="info" %}
The switch on the ActiveIO Wand control panel will remain set to Sync whenever the device is connected to Motive through an ActiveIO BaseStation, even when the of the Marker State is set to _Off_ in Motive.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/ActiveIO Wand Change Marker State CROPPED.png" alt="The Marker State Device Property in Motive, with options: Off; Synchronized; ActiveIO "><figcaption><p>Marker State options for the ActiveIO Wand.</p></figcaption></figure>

#### Pattern Group

A collection of unique patterns that can be assigned to a specific device. The Pattern Group determines how the IR LEDs blink. You can manually change the Pattern Group through the Device properties as needed. This control is editable only when the ActiveIO Wand is connected through an ActiveIO BaseStation, and the Marker State is set to ActiveIO.&#x20;

When connecting multiple devices to the camera system, we recommend using the [auto-pattern](../activeio-configuration.md#auto-pattern) option to ensure the patterns are unique across all devices in the take.&#x20;

#### Quality of Service

The Quality of Service property is a standard ActiveIO setting that allows you to send a device's IMU packet multiple times on redundant RF channels to reduce dropped packets in difficult RF environments. The result is more stable tracking performance under difficult conditions.

{% hint style="warning" %}
This setting does not apply to the ActiveIO Wand as the device IMU is not used during calibration. &#x20;
{% endhint %}

## Specifications

[Additional specifications](https://optitrack3.payloadcms.app/api/media/file/activeio-wand-spec-sheet.pdf) are available on the [OptiTrack website](https://optitrack.com/).&#x20;

<details>

<summary>Wand Dimensions</summary>

**Dimensions when Open**

* Width: 538 mm (21.2")
* Height: 600 mm (23.6")
* Depth: 94 mm (3.7")  <br>

**Dimensions when Closed**

* Width: 27 mm (1.1")
* Height: 855 mm (33.7")
* Depth: 94 mm (3.7")

</details>

<details>

<summary>Weight</summary>

0.7 kg (1 lb. 9.6 oz.)

</details>

<details>

<summary>Battery</summary>

**3500mAh Li-ion Battery**\
Expected battery life of 12hrs at nominal operating conditions \
Expected battery life of 4hrs in continuous mode

Charging

* USB-C PD Charging (5V@3A, 9v@1.5A, 15V@1A)
* \~4hrs zero to full charge

</details>

<details>

<summary>LEDs</summary>

* 850nm IR Spectrum
* 3 LEDs with diffusers
  * Globe Diffusers: (15.875mm, 5/8" diameter)
  * Flat Diffusers: (8mm, 5/16" diameter)
* Illuminations synchronized with camera exposures

Illumination Angles

* Diffuser: +/- 135 Degree
* Bare LED: +/- 56 Degree

</details>
