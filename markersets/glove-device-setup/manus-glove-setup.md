---
description: >-
  Basic setup and troubleshooting guide for integrating Manus Glove devices with
  Motive.
---

# Manus Glove Setup

## **Overview**

The Manus Glove device integration brings finger tracking data from the external glove tracking system into Motive, providing a more comprehensive tracking solution.

Visit the Manus website to download and install the necessary software.

{% hint style="info" %}
For detailed instructions on using Manus gloves, including the OptiTrack integration, please see the [OptiTrack Motive plugin documentation](https://docs.manus-meta.com/2.3.0/Plugins/Motive/) on the [Manus Knowledge Center](https://docs.manus-meta.com/2.3.0/).&#x20;
{% endhint %}

**Required Components**

* Manus Gloves and the USB Dongle.&#x20;
* Manus Core and Dashboard software.
* Motive 3.0 or above.
* (optional) MoCap suit and markers for full body capture.

{% hint style="info" %}
**Important Notes**

* **Supported Glove Models:** Manus Prime gloves and Quantum Metagloves.
* **Sampling Rate:** Manus gloves run at a fixed sampling rate of 90Hz. If the camera system is set to run at a higher frame rate higher, Motive will pad the missing samples in the glove data with previous samples.
* **Sync:** Manus gloves do not support hardware synchronization. Motive uses a software synchronization scheme to attempt to keep the Manus glove as close as possible to mocap data.
* **Manus Dongle:** Plug the Manus dongle on a separate USB bus from the one used to connect the USB Security Key. If both dongles are connected to the same bus, it may cause conflicts with Motive activation.
{% endhint %}

***

## Manus Glove Setup

{% hint style="info" %}
The steps required to setup the glove may change depending on Manus Software versions. For the latest information, please refer to the [Manus user documentation](https://www.manus-vr.com/setup).
{% endhint %}

Before using Manus gloves in Motive, please ensure all gloves have been paired, calibrated and are able to report data from the Manus Dashboard software. This is a crucial first step for the successful use of Manus Gloves with Motive software.

1. Start the Manus Dashboard software.
2. Insert the Manus Glove Dongle(s) onto the computer. _Do not connect the dongle into the same USB bus used by the USB Security Key as it can cause conflicts with device detection._
3. Power on the Manus Gloves.
4. (optional) You may need to pair the glove with the dongle. The gloves should come already paired.
5. Calibrate each glove according to the [Manus user documentation](https://www.manus-vr.com/setup). This step is critical to provide the most robust finger solve data.
6. Start Motive and the gloves should appear in the [Devices pane](../../motive-ui-panes/devices-pane.md).

{% hint style="info" %}
Note: We recommend closing the Manus Dashboard while running Motive to prevent performance issues.
{% endhint %}

***

## Motive Setup

Please refer to our [Glove Device Setup](./) page.&#x20;

### Wrist Alignment

{% hint style="info" %}
For best tracking results, we recommend attaching markers with Velcro directly to the gloves at the hand and wrist rather than using an attached rigid body.
{% endhint %}

The easiest method to properly align the constraints with the device is to place a camera in MJPEG mode (reference mode) and use the [Gizmo tool ](../../motive/assets/gizmo-tool-translate-rotate-and-scale.md)to make adjustments. &#x20;

<div><figure><img src="../../.gitbook/assets/Manus Glove Align with Reference Cam 1.png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Manus Glove Align with Reference Cam 2.png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/Manus Glove Align with Reference Cam 3.png" alt=""><figcaption></figcaption></figure></div>

{% hint style="info" %}
Adjust the gain and exposure on the reference camera until the actor's hand in the Manus glove is clearly visible.
{% endhint %}

***

## Export and streaming

Once Motive is tracking the glove, the finger tracking data can be output for various applications. Real-time finger data can be streamed into any NatNet client, and recorded finger data can be exported into other file formats. For instructions, please refer to the following pages:

* [Data Streaming](../../motive/data-streaming.md)
* [Data Export](../../motive/data-export/)<br>

***

## Troubleshooting

### Licensing&#x20;

Manus Core requires the appropriate license for streaming to Motive. If that license is not found, Motive will report an error when the program is launched. &#x20;

Until the proper license is installed, the gloves will appear in Motive, but when paired with a hand skeleton there is no hand animation as expected.&#x20;

Contact Manus support to resolve Manus licensing issues.&#x20;

<figure><img src="../../.gitbook/assets/Manus License Error.png" alt=""><figcaption></figcaption></figure>

### Log Pane Messages

The Log pane will record several informational entries when Manus gloves are connected:

<figure><img src="../../.gitbook/assets/Manus Successful Connection Log pane.png" alt="" width="501"><figcaption><p>Log pane showing successful connection of a pair of Manus gloves. </p></figcaption></figure>

&#x20;The following Log pane entries indicate that additional steps are required to connect the gloves:

[Failed to Load Plugin](manus-glove-setup.md#failed-to-load-plugin) | [Unable to Load dll ... The specified module could not be found](manus-glove-setup.md#unable-to-load-dll-...-the-specified-module-could-not-be-found) **|** [ManusCore not found on %s", szServerAddress](manus-glove-setup.md#manuscore-not-found-on-s-szserveraddress) | [ManusCore not found on localhost](manus-glove-setup.md#manuscore-not-found-on-localhost) | [Failed to initialize the ManusSDK](manus-glove-setup.md#failed-to-initialize-the-manussdk) | [Error: %s", p\_SystemMessage->infoString](manus-glove-setup.md#error-s-p_systemmessage-greater-than-infostring) | [Incompatible SDK version. Use 2.0 or above](manus-glove-setup.md#incompatible-sdk-version.-use-2.0-or-above) | [Skeleton-Related Error Messages](manus-glove-setup.md#skeleton-related-error-messages)

***

#### Failed to Load Plugin

The OptiTrack Manus plugin did not load when Motive was initialized.&#x20;

_**Troubleshooting Steps:**_&#x20;

* make the correct version of Plugin.dll is in the devices folder.&#x20;
* make sure ManusSDK.dll is in the same folder as  Motive.exe.

***

#### Unable to Load dll ... **The specified module could not be found**

The plugin DLL was found but not loaded due to missing dependencies. This indicates the plugin setup is incomplete.

_**Troubleshooting Steps:**_&#x20;

* Reinstall the plugin.&#x20;
* Contact [Manus support](https://www.manus-meta.com/request-support).&#x20;

***

#### ManusCore not found on %s", szServerAddress

The ManusCore application was not found at the designated server address.

_**Troubleshooting Steps:**_&#x20;

* Ensure the correct server address is indicated for the ManusCore PC.
* Check that the ManusCore PC is running and that the software is installed.

***

#### ManusCore not found on localhost

The ManusCore application was not found on the Motive PC.

_**Troubleshooting Steps:**_&#x20;

Ensure that the Motive PC has the ManusCore application installed.

***

#### Failed to initialize the ManusSDK

The ManusSDK did not initialize.

_**Troubleshooting Steps:**_&#x20;

* Restart the ManusCore and Motive PCs.&#x20;
* See [Manus support](https://www.manus-meta.com/request-support) for additional troubleshooting.

***

#### Error: %s", p\_SystemMessage->infoString

Error callback from Manus SDK.

_**Troubleshooting Steps:**_&#x20;

Contact [Manus support](https://www.manus-meta.com/request-support) for the specific message received.&#x20;

***

#### Incompatible SDK version. Use 2.0 or above

Error reported from ManusSDK

_**Troubleshooting Steps:**_&#x20;

Contact [Manus support](https://www.manus-meta.com/request-support).&#x20;

***

#### Skeleton-Related Error Messages

The following error messages indicate issues with the skeleton in Manus.&#x20;

| Error Message                                                           | Description                                       |
| ----------------------------------------------------------------------- | ------------------------------------------------- |
| \[Manus] Failed to load the skeleton                                    | Failed initialization of Manus skeleton           |
| \[Manus] Failed to give skeleton an ID                                  | Failed initialization of Manus skeleton           |
| \[Manus] Failed to create skeleton setup                                | Skeleton chaining error                           |
| \[Manus] Failed to create skeleton chains.                              | Skeleton chaining error                           |
| \[Manus] Error with setting up right hand skeleton node.                | Failed initialization of Hand skeleton            |
| \[Manus] Error with setting up left hand skeleton node.                 | Failed initialization of Hand skeleton            |
| \[Manus] Failed to Add Chain To Skeleton Setup. Error Code: %d", result | Skeleton chaining error. Error code from ManusSDK |

_**Troubleshooting Steps:**_&#x20;

* Check the configuration in Manus Dashboard and make sure the hand skeleton is correctly defined and working there.&#x20;
* Contact [Manus support](https://www.manus-meta.com/request-support).&#x20;
