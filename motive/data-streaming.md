---
description: >-
  Learn how to configure Motive to broadcast frame data over a selected server
  network.
---

# Data Streaming

## Overview

Common motion capture applications rely on real-time tracking. The OptiTrack system is designed to deliver data at an extremely low latency even when streaming to third-party pipelines.

Motive offers multiple options to stream tracking data to external applications in real-time. Streaming plugins are available on the [OptiTrack download site](https://optitrack.com/support/downloads/plugins.html) for the following applications:

* Autodesk Motion Builder
* Unreal Engine
* Unity
* Maya (VCS)

Motive can stream to the following applications or protocols as well:

* Visual3D
* VRPN

In addition to these plugins, the [NatNet SDK](../developer-tools/natnet-sdk/) enables users to build custom clients to receive capture data.&#x20;

## NatNet Streaming

NatNet is a client/server networking protocol for sending and receiving data across a network in real-time. It utilizes UDP along with either Unicast or Multicast communication to integrate and stream reconstructed 3D data, Rigid Body data, Trained Markerset data, and Skeleton data from OptiTrack systems to client applications.&#x20;

The API includes a class for communicating with OptiTrack server applications for building client protocols. Using the tools provided in the NatNet API, capture data can be used in various application platforms. Please refer to the [NatNet SDK section](../developer-tools/natnet-sdk/) of the user guide for more information on using NatNet and its API references.

![](<../.gitbook/assets/image (328).png>)

{% hint style="info" %}
**Rotation conventions**

NatNet streams rotational data in quaternions. If you wish to present the rotational data in the Euler convention (pitch-yaw-roll), the quaternions data must be converted into Euler angles.&#x20;

In the provided NatNet SDK samples, the SampleClient3D application converts quaternion rotations into Euler rotations to display in the application interface. The sample algorithms for the conversion are scripted in the **NATUtils.cpp** file.&#x20;

Refer to the NATUtils.cpp file and the SampleClient3D.cpp file to find out how to convert quaternions into Euler conventions.
{% endhint %}

## **Streaming Settings**

To quickly access streaming settings, click the streaming icon <img src="../.gitbook/assets/Control Deck - Streaming Off SMALL (3).png" alt="" data-size="line"> from the control deck. This will open the [Streaming tab](../motive-ui-panes/settings/settings-streaming.md) in the [Application Settings](../motive-ui-panes/settings/) panel. Alternately, you can open the Settings panel by clicking the <img src="../.gitbook/assets/Settings button (1).png" alt="" data-size="line"> button, then selecting the Streaming tab.&#x20;

{% hint style="info" %}
Settings in the NatNet category apply to streaming plugins as well as NatNet.&#x20;
{% endhint %}

![Broadcast Frame Data Enabled for streaming.](<../.gitbook/assets/Settings - Streaming Standard settings only (4).png>)

#### Enable Streaming

Check **Enable** to start streaming. This will change the color of the streaming icon in the Control Deck: &#x20;

<figure><img src="../.gitbook/assets/Control Deck Streaming Menu.png" alt=""><figcaption><p>Streaming Status in the Control Deck.</p></figcaption></figure>

Once enabled, Motive will display a warning if you attempt to exit without turning it back off first:

<figure><img src="../.gitbook/assets/Data Streaming - Warning at close.png" alt="" width="411"><figcaption><p>Warning at Exit if Streaming is enabled. </p></figcaption></figure>

#### Local Interface

Default: Loopback

This setting determines which network Motive will use to stream data.

Use the **Loopback** option when Motive and the client application are both running on the same computer. Otherwise, select the IP address for the network where the client application is installed.

Motive Host PCs often have multiple network adapters, one for the camera network and one or more for the local area network (LAN). When streaming over a LAN, select the IP address of the network adapter connected to the LAN where the client application resides.

{% hint style="danger" %}
Firewall or anti-virus software can block network traffic. It's important to either disable these applications or configure them to allow access to both server (Motive) and Client applications.
{% endhint %}

#### Transmission Type

Default: Multicast

NatNet uses the **UDP protocol** in conjunction with either **Point-To-Point Unicast** or **IP Multicasting** for sending and receiving data.&#x20;

Unicast NatNet clients can subscribe to just the data types they need, reducing the size of the data packets streamed. This feature helps to reduce the streaming latency. This is especially beneficial for wireless unicast clients, where streaming is more vulnerable to packet loss.

For more information on NatNet data subscription, please read the [NatNet: Unicast Data Subscription Commands](../developer-tools/natnet-sdk/natnet-unicast-data-subscription-commands.md) page.&#x20;

#### Labeled Markers

Default: Enabled

Enables streaming of _labeled_ Marker data. These markers are point cloud solved markers.

#### Unlabeled Markers

Default: Enabled

Enables streaming of all of the _unlabeled_ Marker data in the frame.

#### Asset Markers

Default: Enabled

Enables streaming of asset markers associated with all of the assets (Rigid Body, Trained Markerset, Skeleton) in the _Take_. The streamed list will contain a special marker set named _all,_ which is a list of labeled markers in all of the _Take's_ assets. In this data, Skeleton, Rigid Body, and Trained Markerset markers are point cloud solved and model-filled on occluded frames.

#### Rigid Bodies

Default: Enabled

Enables streaming of Rigid Body data, which includes the names of Rigid Body assets as well as positions and orientations of their [pivot points](rigid-body-tracking/).

#### Skeletons

Default: Enabled

Enables streaming of Skeleton tracking data from active Skeleton assets. This includes the total number of bones and their positions and orientations in respect to global, or local, coordinate system.

#### Trained Markerset Markers

Default: Enabled

Enables streaming of solved marker data for active Trained Markerset assets. This includes the total number of bones and their positions and orientations in respect to the global coordinate system.

#### Trained Markerset Bones

Default: Enabled

Enables streaming of bone data for active Trained Markerset assets. This includes the total number of bones, their positions and orientations in respect to the global coordinate system, and the structure of any bone chains the asset may have.

#### Devices

Default: Enabled

Enables the streaming active peripheral devices (ie. force plates, Delsys Trigno EMG devices, etc.).

#### Skeleton Coordinates

Default: Global

* **Global:**  Tracking data is represented according to the global coordinate system.&#x20;
* **Local:** The streamed tracking data (position and rotation) of each skeletal bone is relative to its parent bones.

#### Bone Naming Convention

Default:  Motive

The Bone Naming Convention determines the format to use for streaming Skeleton data so each segment can be properly recognized by the client application.&#x20;

* **Motive:** Uses the standard Motive bone naming convention.&#x20;
* **FBX:** Used for streaming to Autodesk pipelines, such as MotionBuilder or Maya.
* **BVH:**  Used for streaming biomechanical data using the BioVision Hierarchy (BVH) naming convention.
* **UnrealEngine:** Used for streaming to UnrealEngine.&#x20;

#### Up Axis

Default: Y Axis

Selects the upward axis of the right-hand coordinate system in the streamed data. Change this setting to Z Up when streaming to an external platform using a Z-up right-handed coordinate system (e.g., biomechanics applications).

For compatibility with left-handed coordinate systems, the simplest method is to rotate the capture volume 180 degrees on the Y axis when defining the ground plane during [Calibration](calibration/).

![Click image to enlarge.](<../.gitbook/assets/image (267).png>)

#### Remote Trigger

Default:  Disabled

Enables the use of a remote trigger for recording using XML commands. Read more in the [Remote Triggering](data-streaming.md#remote-triggering) section, below.

### Advanced Settings

The Settings panel contains advanced settings that are hidden by default. To access these settings, click the <img src="../.gitbook/assets/Motive Context Menu (25).png" alt="" data-size="line"> button in the top right corner and select _Show Advanced._&#x20;

<figure><img src="../.gitbook/assets/Settings - Streaming Advanced settings  HIGHLIGHTED.png" alt=""><figcaption><p>Application Settings Panel: Streaming tab, with Advanced NatNet Settings highlighted. </p></figcaption></figure>

#### Subject Prefix

Default: Enabled

Includes the associated asset name as a subject prefix to each marker label in the streamed data.

#### Visual3D Compatible

Default:  Disabled

Enables streaming to Visual3D. Normal streaming configurations may be not compatible with Visual3D. This feature ensures that the tracking data to be streamed to Visual3D is compatible.

We recommend leaving this setting disabled when streaming to other applications.&#x20;

#### Scale

Default: 1

Applies scaling to all of the streamed position data.

#### Command Port

Default: 1510

Specifies the port to use to negotiate the connection between the NatNet server and client.

#### Data Port

Default: 1511&#x20;

Specifies the port to use to stream data from the NatNet server to the client(s).

#### XML Broadcast Port

Default: 1512

Specifies the port to use to to stream XML data for remote trigger commands.&#x20;

{% hint style="info" %}
The XML Broadcast Port is linked to the Command Port and is not an editable field. The port will automatically update if the Command Port is changed from the default so that the XML Broadcast Port remains 2 ports away from the Command Port.&#x20;

For example, if the Command Port is changed to 1512, the XML Broadcast Port will update to 1514 automatically.
{% endhint %}

#### Multicast Interface

Default:  239.255.42.99

Defines the multicast broadcast address.&#x20;

{% hint style="info" %}
When streaming to clients based on **NatNet 2.0 or below,** change the _Multicast Interface_ to 224.0.0.1 and the _Data port_ to 1001.
{% endhint %}

#### Multicast as Broadcast

Default:  Disabled

When enabled, Motive streams data via _broadcasting_ instead of sending to Unicast or Multicast IP addresses. This should be used only when the use of Multicast or Unicast is not applicable.&#x20;

To use the broadcast, enable this setting and set the streaming option to Multicast. Set the NatNet client to connect as _Multicast_, and then set the multicast address to _255.255.255.255_. Once Motive starts broadcasting data, the client will receive broadcast packets from the server.

{% hint style="danger" %}
Broadcasting may interfere with other network traffic. A dedicated NatNet streaming network may be required between the server and the client(s).&#x20;
{% endhint %}

#### Socket Size

Default: 1000000

This controls the socket size while streaming via Unicast. This property can be used to make extremely large data rates work properly.

{% hint style="danger" %}
DO NOT modify this setting unless instructed to do so by OptiTrack Support.
{% endhint %}

### VRPN Settings

For information on streaming data via the VRPN Streaming Engine, please visit the [VRPN knowledge base](https://github.com/vrpn/vrpn/wiki). Note that only 6 DOF Rigid Body data can be streamed via VRPN.

![](<../.gitbook/assets/image (1396).png>)

#### **Enabled**

Default:  Disabled

When enabled, Motive streams Rigid Body data via the VRPN protocol.

#### **Broadcast Port**

Default: 3883

Specifies the broadcast port for VRPN streaming.&#x20;

## Remote Triggering

Recording in Motive can control or be controlled by other remote applications through sending or receiving either [NatNet commands](../developer-tools/natnet-sdk/natnet-remote-requests-commands.md) or XML broadcast messages to or from a client application using the UDP communication protocol. This enables client applications to trigger Motive and vice versa. We recommend using [NatNet](data-streaming.md#natnet-streaming) commands because they are more robust and offer additional control features.

Recording start and stop commands can also be transmitted via XML packets. To trigger via XML messages, the [_Remote Trigger_ setting](data-streaming.md#remote-trigger) under the Advanced Streaming Settings must be enabled. For Motive, or clients, to receive the packets, the XML messages must be sent via the [XML Broadcast port. ](data-streaming.md#xml-broadcast-port)&#x20;

**Tip:** Within the NatNet SDK sample package, there is are simple applications (BroadcastSample.cpp (C++) and NatCap (C#)) that demonstrates a sample use of XML remote trigger in Motive.

The XML messages must follow the appropriate syntax. The samples below show the correct XML syntax for the start / stop trigger packet:&#x20;

```
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

```
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

#### NatNet SDK

Runs locally or over a network. The NatNet SDK includes multiple sample applications for C/C++, OpenGL, WinForms/.NET/C#, MATLAB, and Unity. It also includes a C/C++ sample showing how to decode Motive UDP packets directly without the use of client libraries (for cross platform clients such as Linux). For more information regarding NatNet SDK visit our page [NatNet SDK 4.0](../developer-tools/natnet-sdk/natnet-4.0.md).

\
C/C++ or VB/C#/.NET or MATLAB

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y\
Trained Markersets: Y<br>

[Download](http://optitrack.com/products/natnet-sdk/)

#### Autodesk MotionBuilder Plugin

Runs locally or over a network.  Allows streaming of both recorded data and real-time capture data for markers, Rigid Bodies, and Skeletons.

Comes with Motion Builder Resources: OptiTrack Optical Device OptiTrack Skeleton Device OptiTrack Insight VCS

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y

[Download](http://optitrack.com/downloads/#mobu-plugin)

#### Autodesk Maya Plugin

Streams capture data into Autodesk Maya for using the Virtual Camera System.

Works with Maya 2011 (x86 and x64), 2014, 2015, 2016, 2017 and 2018

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y

[Download](http://optitrack.com/downloads/#mobu-plugin)

#### Visual3D

With a Visual3D license, you can download the Visual3D server application which is used to connect an OptiTrack server to a Visual3D application. Using the plugin, Visual 3D receives streamed marker data to solve precise Skeleton models for biomechanics applications.

Markers: Y\
Rigid Bodies: N\
Skeletons: N\
\
C-Motion wiki: [Visual3DServer Plugin](http://www.c-motion.com/v3dwiki/index.php/Visual3DServer_Overview)

#### Unreal Engine 5 Plugin

Runs locally or over a network.  Supports Unreal Engine version 5.3. This plugin allows streaming of Rigid Bodies, markers, Skeletons, trained markersets, and integration of HMD tracking within Unreal Engine projects. Please see the [OptiTrack Unreal Engine Plugin](../plugins/optitrack-unreal-engine-plugin/) section of our documentation for more information.

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y\
Trained Markersets: Y

[Download](http://optitrack.com/downloads/)

#### Unity Plugin

Runs locally or over a network. This plugin allows streaming of tracking data and integration of HMD tracking within Unity projects. Please see the [OptiTrack Unity Plugin](../plugins/optitrack-unity-plugin/) section of our documentation for more information.

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y

[Download](http://optitrack.com/downloads/)

#### Motive API

Runs Motive headlessly and provides the best Motive command/control. Also provides access to camera imagery and other data elements not available in the other streams.

C/C++

Markers: Y\
Rigid Bodies: Y\
Skeletons: N

Within Motive

#### VRPN Sample

Runs locally or over a network.&#x20;

The Virtual-Reality Peripheral Network (VRPN) is an open source project containing a library and a set of servers that are designed for implementing a network interface between application programs and tracking devices used in a virtual-reality system.

Motive 3.1 uses VRPN version 7.33.1.&#x20;

For more information: [VRPN Github](https://github.com/vrpn/vrpn/wiki)

{% hint style="info" %}
Join the community on the [OptiTrack Data Streaming](https://forums.naturalpoint.com/viewforum.php?f=59) Forum today!
{% endhint %}
