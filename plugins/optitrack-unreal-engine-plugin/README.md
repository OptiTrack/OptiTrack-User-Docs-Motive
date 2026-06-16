---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/plugins/optitrack-unreal-engine-plugin
---

# OptiTrack Unreal Engine Plugin

{% hint style="info" %}
For our streaming applications, Unreal Engine 4 and 5 have essentially the same setup. The main difference is the UI and where to find the appropriate settings and buttons. All our guides on this Wiki have been updated to feature Unreal Engine 5. If you need assistance with Unreal Engine 4 please feel free to reach out to our [support](https://optitrack.com/support/) team.
{% endhint %}

## **Plugin Overview**

The [OptiTrack Unreal Engine Plugin](https://optitrack.com/support/downloads?cat=plugin) allows you to stream real-time tracking data from Motive into Unreal Engine. This includes tracking data of Rigid Bodies, Skeletons, and HMDs that are tracked within Motive. This article focuses on the organization of those plugins. For basic instructions on setting up a motion capture system, please refer to the [Getting Started](../../quick-start-guides/quick-start-guide-getting-started.md) guide instead.

![OptiTrack Unreal Engine plugin shown in the Plugins pane in UE5.](<../../.gitbook/assets/Unreal Engine Plugins.png>)

### **HMD Compatibility**

* A variety of head mounted displays (HMDs) can be integrated using the [OptiTrack OpenVR Driver](../optitrack-openvr-driver.md).&#x20;
* For plugin version 1.23 and above, support for Oculus HMDs has been deprecated.

## Motive Data Streaming Setup (Server)

First, you'll want to follow the below instructions to set up the data streaming settings in Motive. Once this is configured, Motive will be broadcasting tracking data onto a designated network interface where client applications can receive them.

### Streaming Settings

![Broadcast Frame Data set to true for streaming.](<../../.gitbook/assets/Settings - Streaming Standard settings only (2).png>)

Open the [Data Streaming Pane](../../motive/data-streaming.md) in Motive's **Settings** window and set the following settings:

* **Enable** - Turn on the Enable setting at the top of the NatNet section.
* **Local Interface** - Choose the desired IP network address from this dropdown to stream data over.
  * **Loopback**
    * This is the local computer IP address (127.0.0.1 or Localhost).
    * Used for streaming data locally on the PC you are running Motive on that does not interact with the LAN.
    * Good option for testing network issues.
  * **192.168.0.1x** (typical, but may be different depending on which interface is used to establish a LAN connection)
    * This IP address is the interface of the LAN either by Wi-Fi or Ethernet.
    * This will be the same address the Client application will use to connect to Motive.
* **Transmission Type**
  * For streaming over a Wi-Fi network, setting the **Transmission Type** to _Unicast_ is strongly advised.
* Select desired data types to stream under streaming options:
  * **Rigid Bodies** - Enabled (required).
  * **Skeletons** - Optional for Skeleton tracking.
  * **Markers (Labeled, Unlabled, Asset)** - Disabled for HMDs (advised).
  * **Devices** - Disabled.
* **Skeleton Coordinates**
  * Set to _Local_.
* **Bone Naming Convention**
  * Set the appropriate bone naming convention for the client application. For example, if the character uses the FBX naming convention, this will need to be set to FBX.

{% hint style="info" %}
**Additional Tips**

* For best results, it is advised to run Motive and Unreal Engine separately on different computers, so that they are not competing for processing resources.
* When streaming the data over a wifi network, _Unicast_ transmission must be used.
* In order to stream data from the Edit mode, a capture-recording must be playing back in Motive.
* For additional information on data streaming in general, read through the [Data Streaming](../../motive/data-streaming.md) page.
{% endhint %}

## Integrating HMDs

OptiTrack motion capture systems can be used to track head mounted displays (HMD) and integrate the tracking data into Unreal Engine for VR applications. For instructions on integrating HMD tracking data into Unreal Engine, please refer to the corresponding page:

* [Unreal Engine: HMD Setup](unreal-engine-hmd-setup.md)

{% hint style="info" %}
**Supported HMDs**

At the time of writing, the following HMDs are supported:

* HTC VIVE
* HTC VIVE Pro 1/2
* Valve Index
* HP Reverb G2
{% endhint %}

{% hint style="danger" %}
**Deprecated support for Oculus HMDs:**

* Support for Oculus Integration have been deprecated starting from UE plugin version 1.23; Plugin version 1.22 or below must be used for Oculus HMDs.
* Vive and Valve Index HMDs are supported through the OpenVR driver.
{% endhint %}

## Wireless Multiplayer Setup

When setting up multiplayer games on wireless clients, it is more beneficial for each client to make direct connection to both the tracking-server (Motive) and the game-server, rather than rebroadcasting the streamed tracking data through the game-server. Then, any of the game related actions that interacts with the tracking data can be processed on the game-server, and this server can send out the corresponding updates to the wireless clients. This allows the wireless clients to only receive both the tracking data or updates without having to send back any information; in other words, minimizing the number of data transfers needed. If wireless clients are sending data there will be a minimum of two transfers on the wireless network, and each transfer of data through wireless network is at risk of latency or lost packets.

![](<../../.gitbook/assets/image (131) (1) (1) (2).png>)
