---
description: >-
  Learn how to configure Motive to broadcast frame data over a selected server
  network.
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/data-streaming
---

# Data Streaming

## Overview

Common motion capture applications rely on real-time tracking. The OptiTrack system is designed to deliver data at an extremely low latency even when streaming to third-party pipelines.

Motive offers multiple options to stream tracking data to external applications in real-time. Streaming plugins are available on the [OptiTrack download site](https://optitrack.com/support/downloads/plugins.html) for the following applications or protocols:

* Autodesk Motion Builder
* Unreal Engine
* Unity
* Blender
* Godot
* MatLab
* MoCap4ROS2
* OpenXR or OpenVR
* Visual3D
* VRPN

In addition to these plugins, the [NatNet SDK](../developer-tools/natnet-sdk/) enables users to build custom clients to receive capture data.&#x20;

## NatNet Streaming

NatNet is a client/server networking protocol for sending and receiving data across a network in real-time. It utilizes UDP along with either Unicast or Multicast communication to integrate and stream reconstructed 3D data, Rigid Body data, Trained Markerset data, and Skeleton data from OptiTrack systems to client applications.&#x20;

The API includes a class for communicating with OptiTrack server applications for building client protocols. Using the tools provided in the NatNet API, capture data can be used in various application platforms. Please refer to the [NatNet SDK section](../developer-tools/natnet-sdk/) of the user guide for more information on using NatNet and its API references.

<figure><img src="../.gitbook/assets/image (329).png" alt="A diagram of the NatNet clients. "><figcaption></figcaption></figure>

{% hint style="info" %}
**Rotation conventions**

NatNet streams rotational data in quaternions. If you wish to present the rotational data in the Euler convention (pitch-yaw-roll), the quaternions data must be converted into Euler angles.&#x20;

In the provided NatNet SDK samples, the SampleClient3D application converts quaternion rotations into Euler rotations to display in the application interface. The sample algorithms for the conversion are scripted in the **NATUtils.cpp** file.&#x20;

Refer to the NATUtils.cpp file and the SampleClient3D.cpp file to find out how to convert quaternions into Euler conventions.
{% endhint %}

## **Streaming Settings**

To quickly access streaming settings, click the streaming icon <img src="../.gitbook/assets/Control Deck - Streaming Off SMALL (3).png" alt="The Streaming icon from the Motive control deck." data-size="line"> from the control deck. This will open the [Streaming tab](../motive-ui-panes/settings/settings-streaming.md) in the [Application Settings](../motive-ui-panes/settings/) panel. Alternately, you can open the Settings panel by clicking the <img src="../.gitbook/assets/Settings button (1).png" alt="The Motive Settings button. " data-size="line"> button, then selecting the Streaming tab.&#x20;

{% hint style="info" %}
Settings in the NatNet category apply to streaming plugins as well as NatNet.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/Settings - Streaming Basic.png" alt="The Application Settings panel in Motive, with the Streaming tab, standard settings displayed. " width="563"><figcaption><p>Motive's standard Streaming settings.  </p></figcaption></figure>

#### Enable Streaming

Check **Enable** to start streaming. This will change the color of the streaming icon in the Control Deck: &#x20;

<figure><img src="../.gitbook/assets/Control Deck Streaming Menu.png" alt=""><figcaption><p>Streaming Status in the Control Deck.</p></figcaption></figure>

Once enabled, Motive will display a warning if you attempt to exit without turning it back off first:

<figure><img src="../.gitbook/assets/Data Streaming - Warning at close.png" alt="" width="411"><figcaption><p>Warning at Exit if Streaming is enabled. </p></figcaption></figure>

### NatNet Settings

The NatNet settings allow streaming of tracking data via Motive's free streaming plugins or any custom-built NatNet interfaces.&#x20;

{% hint style="info" %}
Some third-party applications accept only certain types of streamed data. Please refer to the pages in the [Plugins section](../plugins/) of our documentation for more information on OptiTrack-supported integrations.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/Settings Streaming - NatNet Adv TOP .png" alt="The Motive Settings panel, with the Streaming tab selected and advanced properties displayed."><figcaption><p>Streaming Advanced settings (partial list) in Motive.</p></figcaption></figure>

With Advanced settings displayed, scroll to see additional options:

<figure><img src="../.gitbook/assets/Settings Streaming - NatNet Adv BOTTOM CROPPED .png" alt=""><figcaption><p>Additional Advanced Streaming settings in Motive. </p></figcaption></figure>

<details>

<summary><strong>Enable</strong></summary>

Enables or disables broadcasting, or live-streaming, of the frame data.&#x20;

</details>

<details>

<summary><strong>Local Interface</strong></summary>

Sets the network address where the captured frame data will be streamed. &#x20;

* Loopback (127.0.0.1) streams the data locally within the same same computer. Select this if the application you are streaming to is on the same computer as Motive.
* When streaming to another computer, select the IP address for the network where the other computer is located.&#x20;

Motive Host PCs often have multiple network adapters, one for the camera network and one or more for the local area network (LAN). When streaming over a LAN, select the IP address of the network adapter connected to the LAN where the client application resides.

{% hint style="danger" %}
Firewall or anti-virus software can block network traffic. It's important to either disable these applications or configure them to allow access to both server (Motive) and Client applications.
{% endhint %}

</details>

<details>

<summary><strong>Transmission Type</strong></summary>

Selects the mode of broadcast for NatNet.&#x20;

NatNet uses the **UDP protocol** in conjunction with either **Point-To-Point Unicast** or **IP Multicasting** for sending and receiving data.&#x20;

Unicast NatNet clients can subscribe to just the data types they need, reducing the size of the data packets streamed. This feature helps to reduce the streaming latency. This is especially beneficial for wireless unicast clients, where streaming is more vulnerable to packet loss.

For more information on NatNet data subscription, please read the [NatNet: Unicast Data Subscription Commands](../developer-tools/natnet-sdk/natnet-unicast-data-subscription-commands.md) page.&#x20;

</details>

<details>

<summary><strong>Labeled Markers</strong></summary>

Enables or disables streaming of _labeled_ Marker data. Labeled markers are point cloud solved markers.

</details>

<details>

<summary><strong>Unlabeled Markers</strong></summary>

Enables or disables streaming of the _unlabeled_ Marker data in the frame.

</details>

<details>

<summary><strong>Asset Markers</strong></summary>

Enables or disables streaming of the asset markers, which are named collections of all of the labeled markers and their positions (X, Y, Z). This includes all markers associated with any of the assets (Trained Markerset, Rigid Body, Skeleton).&#x20;

The streamed data also contains a special marker set named _all,_ which is a list of labeled markers in all of the assets in a _Take_. In this data, Skeleton and Rigid Body markers are point cloud solved and model-filled on occluded frames.

</details>

<details>

<summary><strong>Rigid Bodies</strong></summary>

Enables or disables streaming of Rigid Body data, which includes the name of the Rigid Body assets as well as positions and orientations of their [pivot points](rigid-body-tracking/).

</details>

<details>

<summary><strong>Skeletons</strong></summary>

Enables or disables streaming of Skeleton tracking data from active Skeleton assets. This includes the total number of bones and their positions and orientations in respect to global, or local, coordinate system, as selected in the Skeleton Coordinates setting.&#x20;

</details>

<details>

<summary><strong>Cameras</strong></summary>

Enables or disables the inclusion of Camera information in the Data Description packet.&#x20;

</details>

<details>

<summary><strong>Trained Markerset Markers</strong> </summary>

Enables or disables streaming of asset marker tracking data from active Trained Markerset assets.

</details>

<details>

<summary><strong>Trained Markerset Bones</strong></summary>

Enables or disables streaming of bone information from Trained Markerset assets. This includes the total number of bones and their positions and orientations in respect to global, or local, coordinate system.&#x20;

</details>

<details>

<summary><strong>Devices</strong></summary>

Enables or disables streaming of active peripheral devices (ie. force plates, Delsys Trigno EMG devices, etc.)

</details>

<details>

<summary><strong>IMU</strong></summary>

Enables or disables streaming of IMU (Inertial Measurement Unit) data for client-side sensor fusion workflows.&#x20;

</details>

<details>

<summary><strong>GPIO</strong></summary>

Enables or disables streaming of GPIO (General Purpose Input/Output) data. This setting enables workflows where button inputs are activated on ActiveIO devices, then sent to game engines or other client applications where actions in the game can occur.

</details>

<details>

<summary><strong>Anchors</strong></summary>

Enables or disables streaming of anchor marker data. This allows for improved monitoring of system health using a NatNet Client.

</details>

<details>

<summary><strong>Skeleton Coordinates</strong></summary>

Sets the coordinate system to use for skeleton tracking.

* **Global:** The tracking data will be represented according to the global coordinate system.&#x20;
* **Local:** the streamed tracking data (position and rotation) of each skeletal bone will be relative to its parent bones.

</details>

<details>

<summary><strong>Skeleton as Rigid Bodies (Advanced)</strong></summary>

When enabled, Skeleton assets are streamed as a series of Rigid Bodies that represent respective Skeleton segments.

</details>

<details>

<summary><strong>Bone Naming Convention</strong></summary>

The Bone Naming Convention determines the format to use for streaming Skeleton data so each segment can be properly recognized by the client application. The naming convention must match the format used in the streaming destination.

* **Motive:** Uses the standard Motive bone naming convention.&#x20;
* **FBX:** Used for streaming to Autodesk pipelines, such as MotionBuilder or Maya.
* **BVH:**  Used for streaming biomechanical data using the BioVision Hierarchy (BVH) naming convention.
* **UnrealEngine:** Used for streaming to UnrealEngine.&#x20;

</details>

<details>

<summary><strong>Up Axis</strong></summary>

Sets the upward axis of the right-hand coordinate system in the streamed data. When streaming onto an external platform with a Z-up right-handed coordinate system (e.g. biomechanics applications) change this to Z Up.

{% hint style="info" %}
For compatibility with left-handed coordinate systems, the simplest method is to rotate the capture volume 180 degrees on the Y axis when defining the ground plane during [Calibration](calibration/).



<p align="center"><img src="../.gitbook/assets/image (268).png" alt="An OptiTrack ground plane, with the X and Z axis noted. " data-size="original"></p>
{% endhint %}

</details>

<details>

<summary><strong>Remote Trigger</strong></summary>

Allows using the remote trigger for recording using XML commands. See the [Remote Triggering](data-streaming.md#remote-triggering) section of the Data Streaming page for more detail on this feature.

</details>

<details>

<summary><strong>Subject Prefix (Advanced)</strong></summary>

When enabled, the associated asset name is added as a subject prefix to each marker label in the streamed data.

</details>

<details>

<summary><strong>Visual 3D Compatible (Advanced)</strong></summary>

Enables streaming to Visual3D. Normal streaming configurations may be not compatible with Visual3D, and this feature must be enabled for streaming tracking data to Visual3D.

</details>

<details>

<summary><strong>Scale (Advanced)</strong></summary>

Applies scaling to all of the streamed position data.

</details>

<details>

<summary><strong>Command Port (Advanced)</strong></summary>

Specifies the port to use for negotiating the connection between the NatNet server and client. The default value is 1510.&#x20;

</details>

<details>

<summary><strong>Data Port (Advanced)</strong></summary>

Specifies the port to use for streaming data from the NatNet server to the client(s). The default value is 1511.&#x20;

</details>

<details>

<summary><strong>XML Broadcast Port (Advanced)</strong></summary>

Specifies the port to use to to stream XML data for remote trigger commands. The default value is 1512.

{% hint style="info" %}
The XML Broadcast Port is linked to the Command Port and is not an editable field. The port will automatically update if the Command Port is changed from the default so that the XML Broadcast Port remains 2 ports away from the Command Port.&#x20;

For example, if the Command Port is changed to 1512, the XML Broadcast Port will update to 1514 automatically.
{% endhint %}

</details>

<details>

<summary><strong>Multicast interface (Advanced)</strong></summary>

Specifies the multicast broadcast address. The default address is 239.255.42.99.&#x20;

{% hint style="info" %}
When streaming to clients based on **NatNet 2.0 or below,** change the _Multicast Interface_ to 224.0.0.1 and the _Data port_ to 1001.
{% endhint %}

</details>

<details>

<summary><strong>Multicast as Broadcast (Advanced)</strong></summary>

{% hint style="danger" %}
**Warning: This mode is for testing purposes only and it can overflood the network with the streamed data.**
{% endhint %}

When enabled, Motive streams the mocap data via _broadcasting_ instead of sending to Unicast or Multicast IP addresses. This should be used only when the use of Multicast or Unicast is not applicable.&#x20;

This streaming method will flood the network that Motive is streaming to with streamed mocap data, which may interfere with the transmission of other data on the network, so a dedicated NatNet streaming network may need to be set up between the server and the client(s).

**To use the broadcast:**&#x20;

1. set the streaming option to Multicast and have this setting enabled on the server.&#x20;
2. Once it starts streaming, set the NatNet client to connect as Multicast, and then set the multicast address to _255.255.255.255_.&#x20;
3. Once Motive starts broadcasting the data, the client will receive broadcast packets from the server.

</details>

<details>

<summary><strong>Socket Size</strong> (Advanced)</summary>

{% hint style="danger" %}
**Warning: Do not modify unless instructed.**
{% endhint %}

This controls the socket size while streaming via Unicast. This property can be used to make extremely large data rates work properly. The default value is 1000000.

</details>

<details>

<summary><strong>Filter Data Description Types (Advanced)</strong></summary>

When enabled, Motive sends data descriptions only for the asset types selected for streaming and filters out the rest. When the setting is not enabled (the default), Motive sends data descriptions for all assets in the scene, regardless of their streaming status.&#x20;

{% hint style="danger" %}
Enable this setting only if you are experiencing description packet errors. &#x20;
{% endhint %}

</details>

### VRPN Settings

For information on streaming data via the VRPN Streaming Engine, please visit the [VRPN knowledge base](https://github.com/vrpn/vrpn). Note that only 6 DOF Rigid Body data can be streamed via VRPN.

<figure><img src="../.gitbook/assets/Settings - Streaming VRPN Adv.png" alt="Motive VRPN standard and advanced Settings, from the Application Settings > Streaming tab."><figcaption><p>VRPN Standard and Advanced Settings in Motive.</p></figcaption></figure>

<details>

<summary><strong>Enable</strong></summary>

Enables or disables streaming of Rigid Body data via the VRPN protocol.

</details>

<details>

<summary><strong>Zero When Untracked</strong></summary>

When enabled, this setting zeros out the data for untracked assets.&#x20;

</details>

## Remote Triggering

You can send and receive either [NatNet commands](../developer-tools/natnet-sdk/natnet-remote-requests-commands.md) or XML broadcast messages using the UDP communication protocol between Motive and a client application. This includes the ability for either Motive or the client application to remotely trigger the other application.&#x20;

{% hint style="info" %}
We recommend using [NatNet](data-streaming.md#natnet-streaming) commands because they are more robust and offer additional control features.
{% endhint %}

Recording start and stop commands can also be transmitted via XML packets. To trigger via XML messages, the [_Remote Trigger_ setting](data-streaming.md#remote-trigger) under the Advanced Streaming Settings must be enabled. For Motive or clients to receive the packets, the XML messages must be sent via the [XML Broadcast port. ](data-streaming.md#xml-broadcast-port)&#x20;

**Tip:** Within the NatNet SDK sample package, there is are simple applications (BroadcastSample.cpp (C++) and NatCap (C#)) that demonstrates a sample use of XML remote trigger in Motive.

The XML messages must follow the appropriate syntax. The samples below show the correct XML syntax for the start / stop trigger packet:&#x20;

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<CaptureStart>
    <Name VALUE="RemoteTriggerTest_take01"/>
    <SessionName VALUE="SessionName" />
    <Notes VALUE="Take notes goes here if any"/>
    <Assets VALUE="skel1, skel2, sword" />
    <Description VALUE="" />
    <DatabasePath VALUE="S:/shared/testfolder/"/>
    <TimeCode VALUE="00:00:00:00"/>
    <PacketID VALUE="0"/>
    <HostName VALUE="optional host name" />
    <ProcessID VALUE="optional process id" />
</CaptureStart>
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<CaptureStop>
    <Name VALUE="TakeName" />
    <Notes VALUE="Take notes go here if any." />
    <Assets VALUE="skel1, skel2, sword" />
    <TimeCode VALUE="00:00:00:00" />
    <HostName VALUE="optional host name" />
    <ProcessID VALUE="optional process id" />
</CaptureStop>
```

#### Capture Start Packet

|      Value     | Description                                                                                                                                                                                                                                                                                                                                                |
| :------------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|      Name      | Name of the _Take_ that will be recorded.                                                                                                                                                                                                                                                                                                                  |
|   SessionName  | Name of the session folder.                                                                                                                                                                                                                                                                                                                                |
|      Notes     | Informational note for describing the recorded _Take_.                                                                                                                                                                                                                                                                                                     |
|   Description  | (Reserved)                                                                                                                                                                                                                                                                                                                                                 |
|     Assets     | List of [assets](assets/) involved in the _Take_.                                                                                                                                                                                                                                                                                                          |
|  DatabasePath  | The file directory where the recorded captures will be saved.                                                                                                                                                                                                                                                                                              |
| Start Timecode | Timecode values (SMTPE) for frame alignments, or reserving future record trigger events for timecode supported systems. Camera systems usually have higher framerates compared to the SMPTE Timecode. In the triggering packets, the [subframe values](../synchronization/optitrack-timecode.md#timecode-representation) always equal to 0 at the trigger. |
|    PacketID    | (Reserved)                                                                                                                                                                                                                                                                                                                                                 |
|    HostName    | (Reserved)                                                                                                                                                                                                                                                                                                                                                 |
|    ProcessID   | (Reserved)                                                                                                                                                                                                                                                                                                                                                 |

#### Capture Stop Packet

|   Value   | Description                                                                                                                                   |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
|    Name   | Name of the recorded _Take_.                                                                                                                  |
|   Notes   | Informational notes for describing recorded a Take.                                                                                           |
|   Assets  | List of [assets](assets/) involved in the _Take_                                                                                              |
|  Timecode | Timecode values (SMPTE) for frame alignments. The [subframe](../synchronization/optitrack-timecode.md#timecode-representation) value is zero. |
|  HostName | (Reserved)                                                                                                                                    |
| ProcessID | (Reserved)                                                                                                                                    |

## Streaming Protocols/Plugins

Unless otherwise noted, the following plugins are available on the OptiTrack [downloads](https://www.optitrack.com/support/downloads?cat=plugin) site.&#x20;

<details>

<summary>NatNet SDK</summary>

Runs locally or over a network. The NatNet SDK includes multiple sample applications for C/C++, OpenGL, WinForms/.NET/C#, MATLAB, and Unity. It also includes a C/C++ sample showing how to decode Motive UDP packets directly without the use of client libraries (for cross platform clients such as Linux). For more information regarding NatNet SDK visit our page [NatNet SDK 4.0](../developer-tools/natnet-sdk/natnet-4.5.md).

\
C/C++ or VB/C#/.NET or MATLAB

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y\
Trained Markersets: Y

</details>

<details>

<summary>Autodesk MotionBuilder Plugin</summary>

Runs locally or over a network.  Allows streaming of both recorded data and real-time capture data for markers, Rigid Bodies, and Skeletons.

Comes with Motion Builder Resources: OptiTrack Optical Device OptiTrack Skeleton Device OptiTrack Insight VCS

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y

</details>

<details>

<summary>Blender Plugin</summary>

Runs locally or over a network.  Supports Blender versions 4.4 and 5. This plugin allows streaming of Rigid Bodies, markers, and Skeletons within Blender projects. Please see the [OptiTrack Blender Plugin](../plugins/optitrack-blender-plugin/) section of our documentation for more information.

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y

</details>

<details>

<summary>Visual3D</summary>

With a Visual3D license, you can download the Visual3D server application which is used to connect an OptiTrack server to a Visual3D application. Using the plugin, Visual 3D receives streamed marker data to solve precise Skeleton models for biomechanics applications.

Markers: Y\
Rigid Bodies: N\
Skeletons: N\
\
C-Motion wiki: [Visual3DServer Plugin](http://www.c-motion.com/v3dwiki/index.php/Visual3DServer_Overview)

</details>

<details>

<summary>Unreal Engine 5 Plugin</summary>

Runs locally or over a network.  Supports Unreal Engine version 5.3. This plugin allows streaming of Rigid Bodies, markers, Skeletons, trained markersets, and integration of HMD tracking within Unreal Engine projects. Please see the [OptiTrack Unreal Engine Plugin](../plugins/optitrack-unreal-engine-plugin/) section of our documentation for more information.

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y\
Trained Markersets: Y

</details>

<details>

<summary>Unity Plugin</summary>

Runs locally or over a network. This plugin allows streaming of tracking data and integration of HMD tracking within Unity projects. Please see the [OptiTrack Unity Plugin](../plugins/optitrack-unity-plugin/) section of our documentation for more information.

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y

</details>

<details>

<summary>Motive API</summary>

Runs Motive headlessly and provides the best Motive command/control. Also provides access to camera imagery and other data elements not available in the other streams.

C/C++

Markers: Y\
Rigid Bodies: Y\
Skeletons: N

Within Motive

</details>

<details>

<summary>VRPN Sample</summary>

Runs locally or over a network.&#x20;

Motive versions 3.1 and above use VRPN version 7.33.1.&#x20;

The Virtual-Reality Peripheral Network (VRPN) is an open source project containing a library and a set of servers that are designed for implementing a network interface between application programs and tracking devices used in a virtual-reality system.

* Supports VRPN Tracker (RigidBodies), Axis (e.g. Analog joysticks), and Button (button) types.
* Does not support VRPN messaging.
* Timestamps are designed for synchronization within the tracked device (6DOF + Axis + button data).  Timestamps use the stl chronos system clock time since epoch. Motive third party peripheral devices may use a different synchronization system.
* Timeout warnings are incorrect – include the use of VRPN “shutup” if the console messages are an issue.
* For peripheral devices, channels with units of “axis” are streamed as VRPN Analog channels.  Channels with units of “button” are streamed as VRPN Button.
* Make sure trackable and RigidBody name are the same.

Use the OptiTrack [VRPN Sample](../developer-tools/vrpn-sample.md) to test your VRPN configuration.&#x20;

For more information: [VRPN Github](https://github.com/vrpn/vrpn/wiki)

</details>

{% hint style="info" %}
Join the community on the [OptiTrack Discord](https://discord.com/channels/1404531193180848260/1446623038153031893) today!
{% endhint %}
