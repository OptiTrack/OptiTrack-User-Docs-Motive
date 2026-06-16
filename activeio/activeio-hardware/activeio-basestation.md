---
description: >-
  This page provides specifications for ActiveIO BaseStations and information
  about their use.
---

# ActiveIO BaseStation

<figure><img src="../../.gitbook/assets/ActiveIO-Base Station-no-shadow.png" alt="An OptiTrack ActiveIO BaseStation, viewed from the front. The device is powered off. " width="563"><figcaption></figcaption></figure>

The BaseStation is the active hardware component that links other active components to Motive. Using a radio frequency channel (RF channel) between 11-26, the ActiveIO BaseStation synchronizes OptiTrack cameras with ActiveIO Tags, Pucks, Clips, Calibration Wands and Squares. Once the BaseStation receives the signal from the active component, it sends that data to the Motive computer along the camera network. This allows Motive to recognize Active Pucks and Tags even with significant occlusion of the LED markers, as compared to passive markers.

If you use ActiveIO Tags, Pucks, or Clips, at least one ActiveIO BaseStation is required per tracking system.&#x20;

For larger volumes, the approximate range from BaseStation to Tags/Pucks is 100’.

{% hint style="info" icon="comment-question" %}
#### Can I use ActiveIO and Active Classic hardware together?

You can use both ActiveIO and Active Classic devices in a single instance of Motive, with the ActiveIO devices connected to an ActiveIO BaseStation and the Active Classic devices connected to an Active Classic BaseStation.&#x20;
{% endhint %}

## BaseStation Specifications

<figure><img src="../../.gitbook/assets/ActiveIO BaseStation Technical Drawing.png" alt="Specifications for the ActiveIO BaseStation."><figcaption></figcaption></figure>

## BaseStation Load Capacity

An ActiveIO BaseStation can support 10-20 ActiveIO devices.&#x20;

## ActiveIO BaseStation Properties

As shipped, ActiveIO BaseStations will connect to the OptiTrack system without additional configuration by the user.&#x20;

* In the [Devices pane](../../motive-ui-panes/devices-pane.md), select the ActiveIO BaseStation.
* The [Properties pane](../../motive-ui-panes/properties-pane/) will display the device name, serial number, and frame rate.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO BaseStation Basic Props.png" alt=""><figcaption></figcaption></figure>

Click the <img src="../../.gitbook/assets/Motive Context Menu.png" alt="" data-size="line"> menu button in the top right corner of the Properties pane to view Advanced device information.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO BaseStation Adv Props CROPPED.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" icon="memo-pad" %}
#### Notes Property

The Advanced Properties include the user-editable Notes field. Use this freeform text field to identify devices in the manner that best suits your workflow.&#x20;
{% endhint %}

## **BaseStation Lightbar**

The Lightbar on the bottom front of the ActiveIO BaseStation indicates the device status.&#x20;

_Note: Behavior of the Lightbar on the ActiveIo BaseStation is controlled by firmware and is subject to change._

<details>

<summary>Off</summary>

Status: Powered & Awaiting Connection

When the ActiveIO BaseStation is first plugged in, the LED light bar is off until it receives commands from Motive and has successfully authenticated via the security key. If it is not successful in connecting to the network, but receiving power, it will remain off.

<figure><img src="../../.gitbook/assets/AIO BaseStation powered but not connected.jpg" alt="An OptiTrack ActiveIO BaseStation with the Lightbar off with a small red dot in the left corner, indicating the device is powered on but not connected to Motive."><figcaption></figcaption></figure>

</details>

<details>

<summary>Slow Flashing Cyan, No IR</summary>

Status: Idle

Powered and connected to the network, but Motive is not running.

<figure><img src="../../.gitbook/assets/AIO BaseStation - Idle Pulse.jpg" alt=""><figcaption><p>When powered on but not connected to Motive, the ActiveIO BaseStation <br>will flash between cyan lights (above) and no lights (below)</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/AIO BaseStation - pulsing cyan off.jpg" alt="An OptiTrack ActiveIO BaseStation with flashing cyan Lightbar, indicating the device is powered on but not connected to Motive."><figcaption></figcaption></figure>

</details>

<details>

<summary>Solid Green</summary>

Status: Receiving Data

The ActiveIO BaseStation is receiving / sending data.

<figure><img src="../../.gitbook/assets/AIO BaseStation - Green.jpg" alt="An OptiTrack ActiveIO BaseStation with Green Lightbar, indicating the device is sending or receiving data."><figcaption></figcaption></figure>

</details>

<details>

<summary>Cycle Cyan</summary>

Status: Firmware Update

Firmware is being written to flash.&#x20;

Cyan LEDs will turn off from left to right while the device uninstalls the existing firmware, then the cyan LEDs will return from left to right while writing the firmware. A single green LED will flash across the entire bar once the update is completed.&#x20;

<figure><img src="../../.gitbook/assets/AIO BaseStation Firmware Update 1.jpg" alt="An OptiTrack ActiveIO BaseStation with pulsing cyan Lightbar, indicating the device is updating its firmware. Image 1."><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/AIO BaseStation Firmware Update 2.jpg" alt="An OptiTrack ActiveIO BaseStation with pulsing cyan Lightbar, indicating the device is updating its firmware. Image 2."><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/AIO BaseStation Firmware Update 3.jpg" alt="An OptiTrack ActiveIO BaseStation with pulsing cyan Lightbar, indicating the device is updating its firmware. Image 3."><figcaption></figcaption></figure>

</details>
