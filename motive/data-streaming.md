# Data Streaming

## Overview

The Data Streaming settings can be found by selecting the Settings cog or by selecting Edit > Settings in the Motive Toolbar/Command Bar.

<figure><img src="../.gitbook/assets/image (16) (3).png" alt=""><figcaption></figcaption></figure>

Motive offers multiple options to stream tracking data onto external applications in real-time. Streaming plugins are available for Autodesk Motion Builder, The MotionMonitor, Visual3D, Unreal Engine 4, 3ds Max, Maya (VCS), VRPN, and trackd, and they can be downloaded from the OptiTrack website. For other streaming options, the NatNet SDK enables users to build custom clients to receive capture data. All of the listed streaming options do not require separate licenses to use. Common motion capture applications rely on real-time tracking, and the OptiTrack system is designed to deliver data at an extremely low latency even when streaming to third-party pipelines. This page covers configuring Motive to broadcast frame data over a selected server network. Detailed instructions on specific [streaming protocols](data-streaming.md) are included in the PDF documentation that ships with the respective plugins or SDK's.

\
Read through the [Application Settings](../motive-ui-panes/settings/) page for explanations on each setting. NaturalPoint Data Streaming Forum: [OptiTrack Data Streaming](https://forums.naturalpoint.com/viewforum.php?f=59).

![Data Streaming pane in Motive.](<../.gitbook/assets/image (480).png>)

{% hint style="warning" %}
While streaming, the Labeled markers setting is required to be enabled for Unlabeled markers to stream. However, if you do not wish to see Unlabeled markers, these can be toggled off so only Labeled markers are streamed. Due to legacy properties, if Labeled is disabled, then both Labeled and Unlabeled markers are disabled even if Unlabeled is toggled on.&#x20;
{% endhint %}

## Streaming in Motive

### **Streaming Setup**

* To quickly access the streaming settings, click on the streaming icon ([![ControlDeck StreamingIcon 30.png](https://v30.wiki.optitrack.com/images/b/be/ControlDeck_StreamingIcon_30.png)](https://v30.wiki.optitrack.com/index.php?title=File:ControlDeck_StreamingIcon_30.png)) from the control deck. This will open the streaming tab in the application settings panel.
* Select the network interface address for streaming data.
* Select desired data types to stream under streaming options.
* When streaming Skeletons, set the appropriate bone naming convention for client application.
* Check **Enable** at the top under the NatNet settings.
* Configure streaming settings and designate the corresponding IP address from client applications
* Stream live or playback captures

![Broadcast Frame Data set to true for streaming.](<../.gitbook/assets/image (347).png>)

### Streaming IP Address

It is important to select the network adapter (interface, IP Address) for streaming data. Most Motive Host PCs will have multiple network adapters - one for the camera network and one (or more) for the local area network (LAN). Motive will only stream over the selected adapter (interface). Select the desired interface using the **Streaming** tab in Motive's Settings. The interface can be either over a local area network (LAN) or on the same machine (localhost, local loopback). If both server (Motive) and client application are running on the same machine, set the network interface to the local loopback address (127.0.0.1). When streaming over a LAN, select the IP address of the network adapter connected to the LAN. This will be the same address the Client application will use to connect to Motive.

{% hint style="danger" %}
Firewall or anti-virus software can block network traffic, so it is important to make sure these applications are disabled or configured to allow access to both server (Motive) and Client applications.
{% endhint %}

![Skeleton device pane in MotionBuilder.](<../.gitbook/assets/image (456).png>) ![Sample client application created using NatNet SDK.](<../.gitbook/assets/image (381).png>) ![Sample .NET sample created using NatNet SDK. Click image to enlarge.](<../.gitbook/assets/image (450).png>)

### Streaming Options

**Streamed Data Types**

Before starting to broadcast data onto the selected network interface, define which data types to stream. Under streaming options, there are settings where you can include or exclude specific data types and syntax. Set only the necessary criteria to true. For most applications, the default settings will be appropriate.

See: [Application Settings: Streaming](../motive-ui-panes/settings/settings-streaming.md)

**Unicast Subscription**

{% hint style="info" %}
New in Motive 3.0.
{% endhint %}

Starting from Motive version 3.0, unicast NatNet clients have the ability to subscribe only to desired data types that are being streamed out. This feature helps to minimize the size of the data packets and helps to reduce the streaming latency. This is especially beneficial for wireless unicast clients where streaming is more vulnerable to packet loss.

For more information on data subscription, please read the following page: [NatNet: Unicast Data Subscription Commands](../developer-tools/natnet-sdk/natnet-unicast-data-subscription-commands.md)

### Bone Naming Convention

When streaming Skeleton data, bone naming convention formats annotations for each segment when data is streamed out. Appropriate convention should be configured to allow client application to properly recognize segments. For example, when streaming to Autodesk pipelines, the naming convention should be set to FBX.

### Coordinate System Convention

Motive (1.7+) uses a right-handed Y-up coordinate system. However, coordinate systems used in client applications may not always agree with the convention used in Motive. In this case, the coordinate system in streamed data needs to be modified to a compatible convention. For client applications with a different ground plane definition, Up Axis can be changed under Advanced Network Settings. For compatibility with left-handed coordinate systems, the simplest method is to rotate the capture volume 180 degrees on the Y axis when defining the ground plane during [Calibration](calibration/).

![Click image to enlarge.](<../.gitbook/assets/image (390).png>) ![Click image to enlarge.](<../.gitbook/assets/image (306).png>)

## NatNet Streaming

NatNet is a client/server networking protocol which allows sending and receiving data across a network in real-time. It utilizes UDP along with either Unicast or Multicast communication for integrating and streaming reconstructed 3D data, Rigid Body data, and Skeleton data from OptiTrack systems to client applications. Within the API, a class for communicating with OptiTrack server applications is included for building client protocols. Using the tools provided in the NatNet API, capture data can be used in various application platforms. Please refer to the **NatNet User Guide** For more information on using NatNet and its API references.

![](<../.gitbook/assets/image (340).png>)

{% hint style="info" %}
**Rotation conventions**

NatNet streams rotational data in quaternions. If you wish to present the rotational data in the Euler convention (pitch-yaw-roll), the quaternions data need to be converted into Euler angles. In the provided NatNet SDK samples, the SampleClient3D application converts quaternion rotations into Euler rotations to display in the application interface. The sample algorithms for the conversion are scripted in the **NATUtils.cpp** file. Refer to the NATUtils.cpp file and the SampleClient3D.cpp file to find out how to convert quaternions into Euler conventions.
{% endhint %}

## Remote Triggering

If desired, recording in Motive can control or be controlled by other remote applications via sending or receiving either [NatNet commands](../developer-tools/natnet-sdk/natnet-remote-requests-commands.md) or XML broadcast messages to or from a client application through the UDP communication protocol. This enables client applications to trigger Motive or vise versa. Using [NatNet](data-streaming.md#natnet-streaming) commands is recommended because they are not only more robust but they also offer additional control features.

Recording start and stop commands can also be transmitted via XML packets. When triggering via XML messages, the _Remote Trigger_ setting under [Advanced Network Settings](../motive-ui-panes/settings/settings-streaming.md) must be set to true. In order for Motive, or clients, to receive the packets, the XML messages must be sent via the triggering UDP port. The triggering port is designated as two increments (2+) of the defined Command Port (default: 1510), under the advanced network settings, which defaults to 1512. Lastly, the XML messages must exactly follow the appropriate syntax:

**XML Triggering Port:** Command Port (Advanced Network Settings) + 2. This defaults to 1512 (1510 + 2).**Tip:** Within the NatNet SDK sample package, there is are simple applications (BroadcastSample.cpp (C++) and NatCap (C#)) that demonstrates a sample use of XML remote trigger in Motive.

XML syntax for the start / stop trigger packet

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

Capture Start Packet

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

Capture Stop Packet

|   Value   | Description                                                                                                                                   |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
|    Name   | Name of the recorded _Take_.                                                                                                                  |
|   Notes   | Informational notes for describing recorded a Take.                                                                                           |
|   Assets  | List of [assets](assets/) involved in the _Take_                                                                                              |
|  Timecode | Timecode values (SMPTE) for frame alignments. The [subframe](../synchronization/optitrack-timecode.md#timecode-representation) value is zero. |
|  HostName | (Reserved)                                                                                                                                    |
| ProcessID | (Reserved)                                                                                                                                    |

## Streaming Protocols/Plugins

### NatNet SDK

Runs local or over network. The NatNet SDK includes multiple sample applications for C/C++, OpenGL, WinForms/.NET/C#, MATLAB, and Unity. It also includes a C/C++ sample showing how to decode Motive UDP packets directly without the use of client libraries (for cross platform clients such as Linux). For more information regarding NatNet SDK visit our wiki page [NatNet SDK 4.0](../developer-tools/natnet-sdk/natnet-4.0.md).

\
C/C++ or VB/C#/.NET or MATLAB

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y

[Download](http://optitrack.com/products/natnet-sdk/)

### Autodesk MotionBuilder Plugin

Runs local or over network. Allows streaming both recorded data and real-time capture data for markers, Rigid Bodies, and Skeletons.

Comes with Motion Builder Resources: OptiTrack Optical Device OptiTrack Skeleton Device OptiTrack Insight VCS

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y

[Download](http://optitrack.com/downloads/#mobu-plugin)

### Autodesk Maya Plugin

Streams capture data into Autodesk Maya for using the Virtual Camera System.

Requirements:

* Requires Motive 1.0+
* Requires a license valid through March 2, 2018\
  ([check your status](https://optitrack.com/support/#checkLicense))
* Works with Maya 2011 (x86 and x64), 2014, 2015, 2016, 2017 and 2018

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y

[Download](http://optitrack.com/downloads/#mobu-plugin)

### Visual3D

With a Visual3D license, you can download Visual3D server application which is used to connect OptiTrack server to Visual3D application. Using the plugin, Visual 3D receives streamed marker data to solve precise Skeleton models for biomechanics applications.

Markers: Y\
Rigid Bodies: N\
Skeletons: N\
\
C-Motion wiki: [Visual3DServer Plugin](http://www.c-motion.com/v3dwiki/index.php/Visual3DServer_Overview)

### Unreal Engine 5 Plugin

Runs local or over network. Supports Unreal Engine versions up to 5. This plugin allows streaming of Rigid Bodies, markers, Skeletons, and integration of HMD tracking within Unreal Engine projects. For more details, read through the [OptiTrack Unreal Engine Plugin](../plugins/optitrack-unreal-engine-plugin/) documentation page.

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y

[Download](http://optitrack.com/downloads/)

### Unity Plugin

Runs local or over network. This plugin allows streaming of tracking data and integration of HMD tracking within Unity projects. For more details, read through the [OptiTrack Unity Plugin](../plugins/optitrack-unity-plugin/) documentation page.

Markers: Y\
Rigid Bodies: Y\
Skeletons: Y

[Download](http://optitrack.com/downloads/)

### Motive API

Runs Motive heedlessly. Best Motive command/control. Also provides access to camera imagery and other data elements not available in the other streams.

C/C++

Markers: Y\
Rigid Bodies: Y\
Skeletons: N

Within Motive

### VRPN Sample

Runs local or over network.

Includes source code (C++) of a sample implementation for VRPN streaming. The Virtual-Reality Peripheral Network (VRPN) is an open source project containing a library and a set of servers that are designed for implementing a network interface between application programs and tracking devices used in a virtual-reality system.

Motive 3.0 uses VRPN version 7.33.1.&#x20;

For more information: [VRPN Github](https://github.com/vrpn/vrpn/wiki)

Within Motive
