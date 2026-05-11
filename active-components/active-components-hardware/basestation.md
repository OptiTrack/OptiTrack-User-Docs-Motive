---
description: >-
  This page provides specifications for BaseStations and information about their
  use.
---

# BaseStation

<img src="../../.gitbook/assets/image (595).png" alt="" width="188">

The BaseStation is the active hardware component that links other active components to Motive. Using a radio frequency channel (RF channel) between 11-26, the BaseStation synchronizes OptiTrack cameras with Active Tags and Pucks. Once the BaseStation receives the signal from the active component, it sends that data to the Motive computer along the camera network. This allows Motive to recognize Active Pucks and Tags even with significant occlusion of the LED markers, as compared to passive markers.

If you use Active Tags or Pucks, at least one BaseStation is required per tracking system.

For larger volumes, the approximate range from BaseStation to Tags/Pucks is 100’.

## BaseStation Specifications

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

## BaseStation Load Capacity

The number of IMUs that can attach to a BaseStation is determined by the system frame rate and the divisor applied to the BaseStation. The table below shows the IMU maximum for common frame rates with a divisor rate of 1, 2, and in some cases 3.

| FrameRate | Divisor Rate 1 | Divisor Rate 2 | Divisor Rate 3 |
| :-------: | :------------: | :------------: | :------------: |
|     60    |       26       |       54       |       83       |
|     70    |       22       |       47       |       71       |
|     80    |       19       |       39       |       62       |
|     90    |       16       |       36       |       54       |
|    100    |       14       |       32       |       49       |
|    110    |       13       |       29       |       44       |
|    120    |       11       |       26       |       40       |
|    130    |       10       |       24       |                |
|    140    |        9       |       22       |       34       |
|    150    |        9       |       20       |                |
|    160    |        8       |       19       |       30       |
|    170    |        7       |       17       |                |
|    180    |        7       |       16       |       26       |
|    190    |        6       |       15       |                |
|    200    |        6       |       14       |       23       |
|    210    |        5       |       14       |                |
|    220    |        5       |       13       |       21       |
|    230    |        5       |       12       |                |
|    240    |        4       |       11       |       18       |
|    250    |        4       |       11       |                |

As noted, the table does not include all possible frame rate and divisor combinations. If you are familiar with using Tera Term or [PuTTy](../configuration/active-hardware-configuration-putty.md), you can determine the maximum number of IMUs for any specific frame rate and divisor combination not shown on the table.

1. Use PuTTy to change the divisor rate on the BaseStation.
2. Connect an IMU puck to PuTTy.
3. Attempt to set the ID of the puck to an unrealistically high value. This triggers a warning that includes the current number of slots available for the given frame rate.
4. Set the IMU puck ID to the highest available slot for the frame rate and confirm that it appears in Motive.

{% hint style="info" %}
BaseStations have 16 radio frequency (RF) channels available for use (11-26). When adding more than one BaseStation to a system, the IMU count is simply the maximum number of IMUs multiplied by the number of BaseStations (up to 16). For example, in a system with 4 BaseStations running at 90Hz and a divisor rate of 3, the number of allowable IMUs would be 216 (54\*4=216).&#x20;
{% endhint %}

## Configure the BaseStation

As shipped, BaseStations will connect to the OptiTrack system without additional configuration by the user.  Some circumstances may require a configuration update, such as when adding new BaseStations to an existing system or when you wish to change the divisor rate.&#x20;

The BaseStation is configured outside of Motive, using one of the following programs:

* [Active Batch Programmer](../configuration/active-batch-programmer.md)
* [PuTTy](../configuration/active-hardware-configuration-putty.md)

&#x20;Please see the linked pages for more details on configuring the BaseStation.

## **BaseStation LEDs**

_Note: Behavior of the LEDs on the BaseStation is controlled by firmware and is subject to change._

<figure><img src="../../.gitbook/assets/Status Lights.jpg" alt="" width="188"><figcaption><p>LED Status Lights</p></figcaption></figure>

**From Right to Left:**

* **Communication Indicator LED:** When the BaseStation is successfully sending data and communicating with the Active Pucks, the LED closest to the antenna will blink green. **If this LED turns red**, it indicates that the BaseStation failed to establish a connection with Motive.
* **Interference Indicator LED:** The middle LED indicates if there are other signal-traffics on the respective radio channel and PAN ID that might be interfering with the active components. This LED should stay dark in order for the active marker system to work properly. **If it flashes in red,** consider switching both the channel and PAN ID on all of the active components.
* **Power Indicator LED:** The LED located at the corner indicates power for the BaseStation. This LED may be disabled on BaseStations with the latest firmware, but on older BaseStations this LED may light up in red to indicate the device has power.

## BaseStations in Motive

When connected to the OptiTrack system, the properties for any Base Station with firmware 2.x or greater and all associated active devices are shown in the Devices Pane. Please see the [Devices Pane](../../motive-ui-panes/devices-pane.md) page for more details.

{% hint style="warning" %}
This feature requires BaseStation firmware version 2.x or greater. BaseStations and tags with version 1.x firmware will not be visible in the Devices pane but will still work with the OptiTrack system.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Devices Pane - Base Station eSync and CinePuck (1).png" alt=""><figcaption><p>Devices Pane with a BaseStation and Active devices.</p></figcaption></figure>
