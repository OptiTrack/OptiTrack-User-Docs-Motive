# Autodesk MotionBuilder Plugin

## **Overview**

{% embed url="https://www.youtube.com/watch?v=VicxmpC7v3E" %}
**Video Tutorial for all Motionbuilder plugins. For more information, please visit the individual pages for each of the plugins.**
{% endembed %}

The OptiTrack MotionBuilder Plugin is a collection of MotionBuilder devices, scripts, and samples used for working with OptiTtrack Motive data inside MotionBuilder. The device plugins allow users to stream Motive Live or .tak data into MotionBuilder. This page is designed to help you get started with the general download and setup process, and organize the three MotionBuilder plugin pages for quick reference.

![](<../../.gitbook/assets/image (683).png>)

For basic instructions on setting up a motion capture system, please refer to the [Getting Started](../../quick-start-guides/quick-start-guide-getting-started.md) guide.

**Included Plugins:**

* OptiTrack - Skeleton
* OptiTrack - Optical
* OptiTrack - Insight VCS

## Motive Data Streaming Setup (Server)

First, you'll want to follow the instructions below to set up the data streaming settings in Motive. Once this is configured, Motive will be broadcasting tracking data onto a designated network interface where client applications can receive them.

### Streaming Settings

![Broadcast Frame Data set to true for streaming.](<../../.gitbook/assets/image (141) (1) (1) (1) (1) (1) (1) (6).png>)

Open the [Data Streaming Pane](../../motive-ui-panes/settings/settings-streaming.md) in Motive's **Settings** window and set the following settings:

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
  * When streaming Skeletons, set to FBX.

{% hint style="info" %}
**Additional Tips**

* For best results, it is advised to run Motive and MotionBuilder separately on different computers, so that they are not competing for processing resources.
* When streaming the data over a Wi-Fi network, _Unicast_ transmission must be used.
* In order to stream data from the Edit mode, a capture-recording must be playing back in Motive.
* For additional information on data streaming in general, read through the [Data Streaming](../../motive/data-streaming.md) page.
{% endhint %}

## Plugins

#### **OptiTrack - Skeleton**

The OptiTrack Skeleton Device allows to you map Motive 6DOF Skeleton joint angle data directly onto a MotionBuilder character

#### **OptiTrack - Optical**

The OptiTrack Optical Plugin device allows to you to map motion capture (optical) data onto an animated character within MotionBuilder.

#### **OptiTrack - Insight VCS**

The Virtual Camera device is specifically designed for creating a Virtual Camera in MotionBuilder. You can use the Insight VCS device with standard OptiTrack applications such as Motive, or you can use the device in "Universal" mode, which works with generic MotionBuilder Optical or RigidBody objects, allowing you to use the Insight VCS device with alternative motion capture systems that support optical or rigid body devices in MotionBuilder.

![OptiTrack MotionBuilder Plugins view in MotionBuilder in the Asset Browser tab under Devices.](<../../.gitbook/assets/image (656).png>)

## Downloading the Plugins

After downloading the [MotionBuilder plugin](https://optitrack.com/support/downloads/plugins.html) from the OptiTrack website, follow the steps below for a successful install.

**Step 1. Installer Wizard**

![OptiTrack MotionBuilder Plugin .exe file.](<../../.gitbook/assets/image (113).png>)

1. Double click the OptiTrack MotionBuilder Plugin .exe file to open the install wizard.
2. Once the install wizard is open click **Next**.
3. Then read through the End User License Agreement and select _I accept the terms in the license agreement_ then click **Next**.
4. The next step is to select the version of the plugin that matches the version of MotionBuilder you have. Typically this should already auto-detect which version you have installed on your computer. However, if all have a red 'x', click the dropdown menu for the appropriate version and select _This feature will be installed on local hard drive._. Then click **Next**.
5. Click **Install \_and then** Yes'\_ for the installation to begin.

![2. OptiTrack MotionBuilder Plugin Installer.](<../../.gitbook/assets/image (723).png>) ![3. OptiTrack MotionBuilder Plugin Installer End User License Agreement.](<../../.gitbook/assets/image (719).png>)

![4. OptiTrack MotionBuilder Plugin Installer Select Version to install.](<../../.gitbook/assets/image (670).png>) ![5. OptiTrack MotionBuilder Plugin Installer Select Version to install.](<../../.gitbook/assets/image (685).png>)

## Wireless Multiplayer Setup

When setting up multiplayer games on wireless clients, it is more beneficial for each client to make direct connection to both the tracking-server (Motive) and the game-server, rather than rebroadcasting the streamed tracking data through the game-server. Then, any of the game related actions that interacts with the tracking data can be processed on the game-server, and this server can send out the corresponding updates to the wireless clients. This allows the wireless clients to only receive both the tracking data or updates without having to send back any information; in other words, minimizing the number of data transfers needed. If wireless clients are sending data there will be a minimum of two transfers on the wireless network, and each transfer of data through wireless network is at risk of latency or lost packets.

![](<../../.gitbook/assets/image (131) (1) (1) (1) (1) (1) (1) (3).png>)
