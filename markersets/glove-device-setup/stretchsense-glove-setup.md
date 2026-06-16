---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/markersets/glove-device-setup/stretchsense-glove-setup
---

# StretchSense Glove Setup

This page provides instructions on integrating StretchSense gloves with an OptiTrack motion capture system.

## **Overview**

Starting from Motive 3.0 and above, StretchSense gloves can be integrated into Motive. This allows for easy integration of the external glove tracking system directly in Motive so that it can be used in tandem with the OptiTrack system to provide a more comprehensive tracking solution.

**Required Components**

* StretchSense SuperSlay or Fidelity Gloves with corresponding dongles.
* [Hand Engine 2.2.2+](https://get.stretchsense.com/knowledge/hand-engine-release-notes-doc-5050) software
* [StretchSense DLL](https://optitrack.com/support/downloads/plugins.html)
* Motive 3.0 or above
* (optional) MoCap suit and markers for full body capture.
* (optional) 2 PCs, one to run Motive another to run Hand Engine

If you're having issues with latency, it is recommended that you run Hand Engine on a separate PC than Motive. For more instruction on how to do so, please see our [Connecting to Remote Host](stretchsense-glove-setup.md#connecting-to-a-remote-host) section Below.&#x20;

## StretchSense Setup

Before getting setup in Motive, you'll need to pair and calibrate your gloves within Hand Engine . Hand Engine is StretchSense's software that allows you to pair your gloves to their respective USB dongles and calibrate prior to integrating into Motive.&#x20;

{% hint style="info" %}
For a full guide on setting up your gloves with Hand Engine, please visit the [StretchSense Knowledge Base](https://stretchsense.my.site.com/defaulthelpcenter26Sep/s/article/OptiTrack-Motive-Streaming-from-Hand-Engine?language=en_US).&#x20;
{% endhint %}

## Motive Setup

1. In order for StretchSense gloves to appear in the Devices pane in Motive, you'll first need to download the [StretchSense DLL](https://optitrack.com/support/downloads/plugins.html) from our website.&#x20;
2. Once downloaded, you can place the DLL file into the directory below:

C:\Program Files\OptiTrack\Motive\devices

<figure><img src="../../.gitbook/assets/image (843).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Make sure Motive is not open during this process. Once the DLL has been stored in the devices folder, you can then open Motive.&#x20;
{% endhint %}

3. Open Motive and power on the StretchSense gloves. You'll see the gloves appear in the Devices pane.&#x20;
4. Create 2 hand Skeletons from the glove markers (left, and right hands).

<figure><img src="../../.gitbook/assets/image (836).png" alt=""><figcaption></figcaption></figure>

5. From the Devices pane select the Right glove and pair it to the right Skeleton.&#x20;

<figure><img src="../../.gitbook/assets/image (805).png" alt=""><figcaption></figcaption></figure>

6. Repeat Step 5 with the left hand.
7. Your gloves should now be fully integrated into Motive and ready for tracking!

<figure><img src="../../.gitbook/assets/image (1168).png" alt=""><figcaption></figcaption></figure>

## Connecting to a Remote Host

To improve any latency issues, you can follow the steps below for running Motive and Hand Engine on separate PCs.&#x20;

1. On the host computer, make sure Hand Engine is running with 'Enable SDK' option turned on.
2. On the separate Motive PC, open Motive.
3. In Motive Settings -> General -> Glove Server Address, specify the IP address and port number of the remote Hand Engine instance. Glove Server Address is an advanced property, so 'Show Advanced' must be toggled. The IP address must follow with a colon ":" and then a port number that matches the number defined in Hand Engine. (e.g. 192.168.1.5:50051)
4. Check the [Log pane](stretchsense-glove-setup.md#log-pane) in Motive to confirm the connection. If the plugin stopped detecting, restart Motive.

## Devices Pane

Below is a description of the columns associated with the gloves in the [Devices pane](../../motive-ui-panes/devices-pane.md).&#x20;

#### Device

This is the name of the device. By default the naming convention is 'StretchSense\_Actor #Serial number'. This is useful to identify each glove based on its serial number incase it was incorrectly paired in Hand Engine .&#x20;

#### Asset

This column will populate with the Skeleton Asset that the glove was paired to within Motive.&#x20;

#### Hand

This column denotes the left and right hands as they were setup in Hand Engine. If the gloves were incorrectly paired in Hand Engine, they will be incorrectly displayed here as well.&#x20;

#### Battery

This column displays the current battery level of the gloves.&#x20;

#### Signal

This column denotes the signal strength. It is important to make sure the signal strength is as full as possible for the best tracking experience.&#x20;

## Log Pane

Important information regarding the status of the gloves as they integrate into Motive can be found in the Log pane.&#x20;

<figure><img src="../../.gitbook/assets/image (1052).png" alt=""><figcaption><p>Click image to enlarge.</p></figcaption></figure>

#### \[StretchSense] Connected to the Hand Engine SDK

This denotes that Motive is now connected to Hand Engine.

#### Plugin Device Created

Prepares the glove to be created in Motive.&#x20;

#### Plugin Device Registered

Creates the glove instance in Motive and populates the glove in the Devices pane.&#x20;

#### \[StretchSense\_Actor] Device Synced. MocapFrame:0 DeviceFrame:0

This message should only appear initially and may occur if there are camera frame drops in other parts of your system. For the most part however, this isn't necessary general user information.&#x20;

