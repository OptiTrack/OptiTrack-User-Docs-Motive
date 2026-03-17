# Settings: Streaming

In Motive, the Application Settings can be accessed under the [View tab](../toolbar-command-bar.md#view) or by clicking the ![A screenshot of the Application Settings button from the Motive toolbar.  ](<../../.gitbook/assets/Settings button.png>) icon on the main toolbar. Default Application Settings can be recovered by Reset Application Settings under the Edit Tools tab from the main [Toolbar](../toolbar-command-bar.md).

In Motive, the Data Streaming pane can be accessed under the [View tab](../toolbar-command-bar.md#view) or by clicking the ![A screenshot of the Data Streaming button from the Motive control deck. ](<../../.gitbook/assets/Control Deck - Streaming Off SMALL.png>) icon on the [Motive Control Deck](../control-deck.md#streaming). For explanations on the streaming workflow, read through the [Data Streaming](../../motive/data-streaming.md) page.

## NatNet Basic Settings

This section allows you to stream tracking data via Motive's free streaming plugins or any custom-built NatNet interfaces. To begin streaming, select _Broadcast Frame Data_. Select which types of data (e.g. markers, Rigid Bodies, or Skeletons) will be streamed, noting that some third party applications will only accept one type of data. Before you begin streaming, ensure that the network type and interface are consistent with the network you will be streaming over and the settings in the client application.

![Data streaming settings in Motive](<../../.gitbook/assets/image (924).png>)

#### **Enable**

(Default: False) Enables/disables broadcasting, or live-streaming, of the frame data. _This must be set to true in order to start the streaming._

#### **Local Interface**

(Default: loopback) Sets the network address which the captured frame data is streamed to. When set to local loopback (127.0.0.1) address, the data is streamed locally within the computer. When set to a specific network IP address under the dropdown menu, the data is streamed over the network and other computers that are on the same network can receive the data.

#### **Transmission Type**

(Default: Multicast) Selects the mode of broadcast for NatNet. Valid options are: Multicast, Unicast.

#### **Labeled Markers**

(Default: True) Enables, or disables, streaming of _labeled_ Marker data. These markers are point cloud solved markers.

#### **Unlabeled Markers**

(Default: True) Enables/disables streaming of all of the _unlabeled_ Marker data in the frame.

#### **Asset Markers**

(Default: True) Enables/disables streaming of the Marker Set markers, which are named collections of all of the labeled markers and their positions (X, Y, Z). In other words, this includes markers that are associated with any of the assets (Marker Set, Rigid Body, Skeleton). The streamed list also contains a special marker set named _all_ which is a list of labeled markers in all of the assets in a\_Take\_. In this data, Skeleton and Rigid Body markers are point cloud solved and model-filled on occluded frames.

#### **Rigid Bodies**

(Default: True) Enables/disables streaming of Rigid Body data, which includes the name of Rigid Body assets as well as positions and orientations of their [pivot points](../../motive/rigid-body-tracking/).

#### **Skeletons**

(Default: Skeletons) Enables/disables streaming of Skeleton tracking data from active Skeleton assets. This includes the total number of bones and their positions and orientations in respect to global, or local, coordinate system.

#### **Devices**

When enabled, this streams active peripheral devices (ie. force plates, Delsys Trigno EMG devices, etc.)

#### **Skeleton Coordinates**

(Default: Global) When set to _Global_, the tracking data will be represented according to the global coordinate system. When this is set to _Local_, the streamed tracking data (position and rotation) of each skeletal bone will be relative to its parent bones.

#### **Bone Naming Convention**

(Default: Motive) Sets the bone naming convention of the streamed data. Available conventions include Motive, FBX, and BVH. The naming convention must match the format used in the streaming destination.

#### **Up Axis**

(Default: Y Axis) Selects the upward axis of the right-hand coordinate system in the streamed data. When streaming onto an external platform with a Z-up right-handed coordinate system (e.g. biomechanics applications) change this to Z Up.

#### **Remote Trigger**

(Default: False) Allows using the remote trigger for recording using XML commands. See more: [Remote Triggering](../../motive/data-streaming.md#remote-triggering)

## NatNet Advanced Settings

#### **Skeleton as Rigid Bodies**

(Default: False) When set to true, Skeleton assets are streamed as a series of Rigid Bodies that represent respective Skeleton segments.

#### **Subject Prefix**

(Default: True) When set to true, associated asset name is added as a subject prefix to each marker label in the streamed data.

#### **Visual3D Compatible**

Enables streaming to Visual3D. Normal streaming configurations may be not compatible with Visual3D, and this feature must be enabled for streaming tracking data to Visual3D.

#### **Scale**

Applies scaling to all of the streamed position data.

#### **Command Port**

(Default: 1510) Specifies the port to be used for negotiating the connection between the NatNet server and client.

#### **Data Port**

(Default: 1511) Specifies the port to be used for streaming data from the NatNet server to the client(s).

#### **Multicast interface**

Specifies the multicast broadcast address. (Default: 239.255.42.99). **Note:** When streaming to clients based on NatNet 2.0 or below, the default multicast address should be changed to 224.0.0.1 and the data port should be changed to 1001.

#### **Multicast as Broadcast**

{% hint style="danger" %}
**Warning: This mode is for testing purposes only and it can overflood the network with the streamed data.**
{% endhint %}

When enabled, Motive streams out the mocap data via _broadcasting_ instead of sending to Unicast or Multicast IP addresses. This should be used only when the use of Multicast or Unicast is not applicable. This will basically spam the network that Motive is streaming to with streamed mocap data which may interfere with other data on the network, so a dedicated NatNet streaming network may need to be set up between the server and the client(s).To use the broadcast set the streaming option to Multicast and have this setting enabled on the server. Once it starts streaming, set the NatNet client to connect as Multicast, and then set the multicast address to _255.255.255.255_. Once Motive starts broadcasting the data, the client will receive broadcast packets from the server.

#### **Socket Size**

{% hint style="danger" %}
**Warning: Do not modify unless instructed.**
{% endhint %}

(Default: 1000000)

This controls the socket size while streaming via Unicast. This property can be used to make extremely large data rates work properly.

## VRPN Streaming Engine

For information on streaming data via the VRPN Streaming Engine, please visit the [VRPN knowledge base](https://github.com/vrpn/vrpn). Note that only 6 DOF Rigid Body data can be streamed via VRPN.

![](<../../.gitbook/assets/image (1396).png>)

#### **Enabled**

(Default: False) When enabled, Motive streams Rigid Body data via the VRPN protocol.

#### **Broadcast Port**

_\[Advanced]_ (Default: 3883) Specifies the broadcast port for VRPN streaming. (Default: 3883).
