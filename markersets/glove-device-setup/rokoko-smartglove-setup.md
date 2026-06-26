---
description: >-
  Integrate the Rokoko Smartglove plugin to bring finger tracking data into
  Motive.
---

# Rokoko Smartglove Setup

## **Overview** <a href="#overview" id="overview"></a>

The Rokoko Smartgloves plugin allows for easy integration of the external glove tracking system directly in Motive, for use in tandem with the OptiTrack system, providing a more comprehensive tracking solution.

### **Required Components** <a href="#required-components" id="required-components"></a>

#### **Rokoko**

* **Rokoko Smartgloves:** Hardware powered through USB or a battery pack.
* **WiFi Router:** A dedicated Wi-Fi router or supported Wi-Fi network for Rokoko devices.
* **Rokoko Studio:** Rokoko Studio software must be installed on the computer that will receive the glove data. Download and setup information is available from [Rokoko Support](https://support.rokoko.com/hc/en-us).
* **Rokoko Plugin DLL:** The software package that allows the Rokoko gloves to work in Motive. [Download the DLL](https://support.rokoko.com/hc/en-us/article_attachments/47902603867537) from the Rokoko site.&#x20;

**OptiTrack**

* **Motive Software**: Version 3.1 or above is installed on the computer that will receive the glove data. Note that the plugin was tested in Motive 3.4.
* **OptiTrack System:** OptiTrack cameras and network equipment.
* **Markers and Suits:** Markers for the hands or full body capture, plus any suits needed.

## Quick Setup Instructions <a href="#quick-setup-instructions" id="quick-setup-instructions"></a>

This guide provides detailed instructions for connecting the Rokoko Smartgloves to Motive, with the following steps:&#x20;

1. Get the Rokoko Smartgloves working in Rokoko Studio using their [online documentation](https://support.rokoko.com/hc/en-us/categories/46732254599313-Smartgloves-II).
2. Obtain the Rokoko DLL and place it in _C:\Program Files\OptiTrack\Motive\devices._
3. Start Motive and get markers tracking using [OptiTrack's online documentation](../../quick-start-guides/quick-start-guide-getting-started.md).
4. [Enable Streaming in Motive](../../motive/data-streaming.md) to send glove data to Motive. You may need to restart Motive to get the glove devices to appear in Motive.
5. [Create a skeleton](../../motive/skeleton-tracking.md#creating-skeletons) (hand or full body), then pair the glove to the skeleton by right-clicking the Smartglove in the Devices pane.
6. You are now hand tracking using Rokoko Smartgloves in Motive.

<figure><img src="../../.gitbook/assets/Rokoko Glove Photo.png" alt="A left hand Rokoko Smartglove II"><figcaption><p>The Left-handed Rokoko Smartglove II.</p></figcaption></figure>

## Rokoko Setup <a href="#rokoko-setup" id="rokoko-setup"></a>

#### Hardware and Network Configuration <a href="#configure-the-hardware-and-network" id="configure-the-hardware-and-network"></a>

1. Connect any required battery or power source to the Rokoko Smartgloves.
2. Connect the computer running Rokoko Studio to the same Wi-Fi network that will be used by the Smartgloves.
3. If the computer also needs Ethernet for the OptiTrack camera network, configure the network adapter priority so Wi-Fi can remain available while Ethernet is connected. See Rokoko’s [Wi-Fi and Ethernet connection at the same time](https://support.rokoko.com/hc/en-us/articles/17477120249617-How-to-have-WiFi-and-Ethernet-connection-at-the-same-time) guide.
4. It's best to use a dedicated Wi-Fi network. Avoid shared office, guest, or university networks when possible. If the gloves do not appear in Rokoko Studio, test with a dedicated router or phone hotspot to check whether the network is the issue.

#### Connect and Calibrate in Rokoko Studio <a href="#connect-and-calibrate-in-rokoko-studio" id="connect-and-calibrate-in-rokoko-studio"></a>

We recommend using Rokoko’s documentation for setting up the Smargloves:

* [Getting Started with your Smartgloves](https://support.rokoko.com/hc/en-us/articles/4410471103249-Getting-Started-with-your-Smartgloves)
* [Setting up your Smartgloves in Rokoko Studio](https://support.rokoko.com/hc/en-us/articles/16556553247121-Setting-up-your-Smartgloves-in-Rokoko-Studio)

The basic steps are outlined below:

1. Launch Rokoko Studio.
2. Open the device manager or live input area in Rokoko Studio and connect the Smartgloves using Rokoko’s normal setup flow.

{% hint style="info" %}
You may need to plug the gloves directly into the computer to perform a firmware update before they will connect.&#x20;
{% endhint %}

3. Apply or verify the Wi-Fi settings for the gloves. Make sure the receiver IP is the IP address of the computer running Rokoko Studio.
4. Confirm that each glove appears as a live input in Rokoko Studio.
5. Run the Rokoko glove calibration procedure for the performer. Follow Rokoko Studio’s prompts and confirm that finger motion is displayed correctly on the avatar.
6. **Enable Motive Streaming:** In the [Streaming Settings](../../motive-ui-panes/settings/settings-streaming.md), activate streaming for Motive.

<figure><img src="../../.gitbook/assets/Rokoko with Motive plugin activated.png" alt="The Rokoko Studio screen, with the Motive plugin enabled. "><figcaption></figcaption></figure>

### Motive Setup <a href="#motive-setup" id="motive-setup"></a>

1. Download the Rokoko DLL and place it in _C:\Program Files\OptiTrack\Motive\devices._
2. With Rokoko Studio running and the gloves connected, launch Motive.&#x20;
3. If the Rokoko setup was successful and the DLL copied to the devices folder, the Smartgloves will appear in the Devices pane in Motive.&#x20;
4. Create a hand or full body skeleton.
5. Right click each glove in the Devices pane to pair the left and right glove devices to the correct skeleton.
6. Move the performer’s fingers to confirm that the corresponding hand/finger motion updates in Motive.

<figure><img src="../../.gitbook/assets/Rokoko Glove Motive Config settings.png" alt="The Motive Devices Pane and the Assets Pane, with a set of Rokoko Smartgloves installed. "><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Rokoko Glove tracking in Motive.png" alt="The Motive 3D Viewport showing a pair of hands being tracked with Rokoko Smartgloves. "><figcaption><p>Successful hand tracking with Rokoko in Motive. </p></figcaption></figure>

### Connecting to a Remote Host <a href="#connecting-to-a-remote-host" id="connecting-to-a-remote-host"></a>

For the most reliable setup, run Rokoko Studio and Motive on the same computer. It may be possible to run the Rokoko and OptiTrack applications on different computers, but this is not recommended or directly supported.&#x20;

### Troubleshooting <a href="#troubleshooting" id="troubleshooting"></a>

#### Gloves do not appear in Rokoko Studio <a href="#gloves-do-not-appear-in-rokoko-studio" id="gloves-do-not-appear-in-rokoko-studio"></a>

* Confirm the gloves are powered and charged.
* Confirm the computer is connected to the same router or access point selected for the Rokoko devices.
* Verify that the receiver IP is the current IP address of the computer running Rokoko Studio. If the IP changes frequently, configure a static IP or DHCP reservation for the adapter.
* Temporarily disable firewall or antivirus software to test whether it is blocking communication, then add exceptions if needed.
* Test with a dedicated router or phone hotspot if using a managed network.
* See Rokoko’s troubleshooting article, [device is not appearing in Rokoko Studio](https://support.rokoko.com/hc/en-us/articles/4410470876689-Smartsuit-Pro-%CE%99%CE%99-is-not-appearing-in-Rokoko-Studio), which also applies to Smartgloves.

#### Gloves appear in Rokoko Studio but not in Motive <a href="#gloves-appear-in-rokoko-studio-but-not-in-motive" id="gloves-appear-in-rokoko-studio-but-not-in-motive"></a>

* Restart Motive after confirming the gloves are connected in Rokoko Studio.
* Confirm that [the required Rokoko glove DLL](https://support.rokoko.com/hc/en-us/article_attachments/47902603867537) is in _C:\Program Files\OptiTrack\Motive\devices_.
* Open the Devices pane and verify that a Rokoko device is created, registered, and assigned to the correct hand.
* Check the [Motive Log pane](../../motive-ui-panes/log-pane.md) for device connection, registration, or sync messages.
* Check Rokoko to make sure that the firmware for the gloves is at a reasonable version. Connect it to the Rokoko computer to update the firmware, if necessary.
