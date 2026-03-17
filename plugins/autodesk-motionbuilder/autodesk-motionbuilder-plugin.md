# Autodesk MotionBuilder Plugin

## **Overview**

{% embed url="https://youtu.be/Sk8s7i4aUwM?si=OpjnuMrlFPwL5ibc" %}
**Video Tutorial for all Motionbuilder plugins. For more information, please visit the individual pages for each of the plugins.**
{% endembed %}

The OptiTrack MotionBuilder Plugin is a collection of MotionBuilder devices, scripts, and samples used for working with OptiTrack Motive data inside MotionBuilder. The device plugins allow users to stream Motive Live or from recorded ._tak_ data into MotionBuilder.&#x20;

This page is designed to help you get started with the general download and setup process, and organize the three MotionBuilder plugin pages for quick reference.

![](<../../.gitbook/assets/image (1263).png>)

For basic instructions on setting up a motion capture system, please refer to the [Getting Started](../../quick-start-guides/quick-start-guide-getting-started.md) guide.

**Included Plugins:**

* OptiTrack - Skeleton
* OptiTrack - Optical
* OptiTrack - Insight VCS

## Motive Data Streaming Setup (Server)

Follow the steps below to configure data streaming in Motive. When the NatNet streaming service is enabled, Motive broadcasts tracking data to a designated network interface where client applications can receive them.

### Streaming Settings

To enable streaming in Motive, click the <img src="../../.gitbook/assets/Settings button (17).png" alt="" data-size="line"> button to open the [_Applications Settings_](../../motive-ui-panes/settings/) panel, then select the [_Streaming_ ](../../motive-ui-panes/settings/settings-streaming.md)tab, or use the <img src="../../.gitbook/assets/Control Deck - Streaming Off SMALL (4).png" alt="" data-size="line"> button in the right corner of the [Control Deck](../../motive-ui-panes/control-deck.md) to open the _Streaming_ tab directly.&#x20;

* In the _NatNet_ section, select _**Enable**_ to begin streaming.&#x20;
* Select the **Local Interface**. Use Loopback if streaming to the same computer, otherwise select the IP address for the network where the client application resides.
* &#x20;Set the **Bone Naming Convention** to _FBX_ if streaming skeletons.&#x20;

Please see the [Data Streaming](../../motive/data-streaming.md) page for more details on all settings available for streaming.&#x20;

![Broadcast Frame Data set to true for streaming.](<../../.gitbook/assets/Settings - Streaming FBX Bones (1).png>)

#### **Additional Tips**

* For best results, run Motive and MotionBuilder on separate computers so they are not competing for processing resources.
* When streaming the data over a Wi-Fi network, use _Unicast_ transmission.

#### Streaming Recorded Data

* To stream recorded data, load the _Take_ in Motiv&#x65;_._&#x20;
* Set the [Playback mode](../../motive-ui-panes/control-deck.md#playback-mode) to _Endpoint_.&#x20;
* Begin recording in MotionBuilder.
* At the desired frame, start playback in Motive. This will stream the captured _Take_ into MotionBuilder.&#x20;
* Stop and save the recording in MotionBuilder when the _Take_ ends in Motive.&#x20;

{% hint style="danger" %}
If playback mode is set to Loop in Motive, MotionBuilder will stop recording once the final frame is reached even though playback continues in Motive.
{% endhint %}

&#x20;For additional information on data streaming in general, read through the [Data Streaming](../../motive/data-streaming.md) page.

## Plugins

#### **OptiTrack - Skeleton**

The OptiTrack Skeleton Device allows to you map Motive 6DOF Skeleton joint angle data directly onto a MotionBuilder character

#### **OptiTrack - Optical**

The OptiTrack Optical Plugin device allows to you to map motion capture (optical) data onto an animated character within MotionBuilder.

#### **OptiTrack - Insight VCS**

The Virtual Camera device is specifically designed for creating a Virtual Camera in MotionBuilder. You can use the Insight VCS device with standard OptiTrack applications such as Motive, or you can use the device in "Universal" mode, which works with generic MotionBuilder Optical or RigidBody objects, allowing you to use the Insight VCS device with alternative motion capture systems that support optical or rigid body devices in MotionBuilder.

![OptiTrack MotionBuilder Plugins view in MotionBuilder in the Asset Browser tab under Devices.](<../../.gitbook/assets/image (1306).png>)

## Downloading the Plugins

After downloading the [MotionBuilder plugin](https://optitrack.com/support/downloads/plugins.html) from the OptiTrack website, follow the steps below for a successful install.

1. Double click the OptiTrack MotionBuilder Plugin .exe file to open the installer.
2. Read the End User License Agreement, then check the box "_I agree to the license terms and conditions."_&#x20;
3. Click the **Install** button to begin the installation.

![OptiTrack MotionBuilder Plugin Installer.](<../../.gitbook/assets/MoBu Installer (2).png>)

## Wireless Multiplayer Setup

When setting up multiplayer games on wireless clients, it's best for each client to directly connect to both the tracking server (Motive) and the game server, rather than rebroadcasting the streamed tracking data through the game-server. This ensures that game-related actions that interact with the tracking data can be processed on the game server, which then sends out the corresponding updates to the wireless clients. This allows the wireless clients to receive both the tracking data or updates without having to send back any information, minimizing the number of data transfers needed. If wireless clients are sending data, it will require at least two transfers on the wireless network, with each wireless transfer increasing the risk of latency or lost packets.

![](<../../.gitbook/assets/image (678) (2).png>)
