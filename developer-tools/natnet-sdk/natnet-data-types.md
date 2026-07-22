---
description: >-
  An overview of the general data structure used in the NatNet software
  development kit (SDK) and how the library is used to parse received tracking
  information.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/developer-tools/natnet-sdk/natnet-data-types
---

# NatNet: Data Types

{% hint style="info" %}
For specific details on each of the data types, please refer to the [NatNetTypes.h](natnet-4.5.md#file-list) header file.
{% endhint %}

## General Structure

When receiving streamed data using the NatNet SDK library, its data descriptions should be received before receiving the tracking data.&#x20;

NatNet data is packaged mainly into two different formats: data descriptions and frame-specific tracking data. Utilizing this format, the client application can discover which data are streamed out from the server application prior to accessing the actual tracking data.

For every asset (e.g., reconstructed markers, Rigid Bodies, Skeletons, force plates) included within streamed capture sessions, the description and tracking data are stored separately. This format allows frame-independent parameters (e.g., name, size, and number) to be stored within instances of the description _structs_, and frame-dependent values (e.g. position and orientation) to be stored within instances of the frame data _structs_. When needed, two different packets of an asset can be correlated by referencing its unique identifier values.

* **Dataset Descriptions** contains descriptions of the motion capture data sets for which a frame of motion capture data will be generated. (e.g. sSkeletonDescription, sRigidBodyDescription)
* **Frame of Mocap Data** contains a single frame of motion capture data for all the datasets described from the Dataset Descriptions. (e.g. sSkeletonData, sRigidBodyData)

{% hint style="info" %}
When streaming from Motive, received NatNet data will contain only the assets that are enabled in the [Assets pane](../../motive-ui-panes/assets-pane.md) and the asset types that are set to _true_ under Streaming Settings in the [Data Streaming](../../motive/data-streaming.md) tab in Motive **Settings**.
{% endhint %}

## Dataset Descriptions

To receive data descriptions from a connected server, use the [NatNetClient::GetDataDescriptionList](natnet-class-function-reference.md#natnetclient-getdatadescriptionlist) method. Calling this function saves a list of available descriptions in an instance of sDataSetDescriptions.

The **sDataSetDescriptions** structure stores an array of multiple descriptions for each asset (Marker Sets, RigidBodies, Skeletons, and Force Plates) involved in a capture and necessary information can be parsed from it.&#x20;

{% hint style="info" %}
Refer to the [NatNetTypes.h](natnet-4.5.md#file-list) header file for more information on each data type and members of each description struct.
{% endhint %}

### Description: Struct

The following data description _structs_ are available through the SDK:

<details>

<summary>Server Description</summary>

Saved struct Type: Native Library: _sServerDescription_

Saved struct Type: Managed Assembly: _ServerDescription_

Contains basic network information of the connected server application and the host computer that it is running on. Server descriptions are obtained by calling the GetServerDescription method from the NatNetClient class.

* Host connection status
* Host information (computer name, IP, server app name)
* NatNet version
* Host's high resolution clock frequency. Used for calculating the latency
* Connection status

</details>

<details>

<summary>Data Descriptions</summary>

Saved struct Type: Native Library: _sDataDescriptions_

Saved struct Type: Managed Assembly: _List\<DataDescriptor>_

Contains an array of data descriptions for each active asset in a capture, and basic information about corresponding asset is stored in each description packet. Data descriptions are obtained by calling the GetDataDescriptions method from the NatNetClient class. Descriptions of each asset type is explained below.

</details>

<details>

<summary>Marker Sets Description</summary>

Saved struct Type: Native Library: _sMarkerSetDescription_

Saved struct Type: Managed Assembly: _MarkerSet_

Marker Set description contains a total number of markers in a Marker Set and each of their labels. Note that Rigid Body and Skeleton assets are included in the Marker Set as well. Also, for every mocap session, there is a special MarkerSet named _all_, which contains a list of all of the labeled markers from the capture.

* Name of the Marker Set
* Number of markers in the set
* Marker names

</details>

<details>

<summary>Rigid Body Description</summary>

Saved struct Type: Native Library: _sRigidBodyDescription_

Saved struct Type: Managed Assembly: _RigidBody_

Rigid Body description contains corresponding Rigid Body names. Skeleton bones are also considered as Rigid Bodies, and in this case, the description also contains hierarchical relationship for parent/child Rigid Bodies.

* Rigid Body name
* Rigid Body streaming ID
* Rigid Body parent ID (when streaming Skeleton as Rigid Bodies)
* Offset displacement from the parent Rigid Body
* Array of marker locations that represent the expected marker locations of the Rigid Body asset.

</details>

<details>

<summary>Skeleton Description</summary>

Saved struct Type: Native Library: _sSkeletonDescription_

Saved struct Type: Managed Assembly: _Skeleton_

Skeleton description contains corresponding Skeleton asset name, Skeleton ID, and total number of Rigid Bodies (bones) involved in the asset. The Skeleton description also contains an array of Rigid Body descriptions which relates to individual bones of the corresponding Skeleton.

* Name of the Skeleton
* Skeleton ID: Unique identifier
* Number of Rigid Bodies (bones)
* Array of bone descriptions

**Note:** Beginning with NatNet 3.0, Skeleton bone data description packet changed from left-handed convention to right-handed convention to be consistent with the convention used in all other data packets. For older versions of NatNet clients, the server, Motive, will detect the client version and stream out Skeleton data in the matching convention. This change will only affect direct depacketization clients as well as clients that have the NatNet library upgraded to 3.0 from previous versions; for those clients, corresponding changes must be made to work with Motive 2.0.

</details>

<details>

<summary>Force Plate Description</summary>

Saved struct Type: Native Library: _sForcePlateDescription_

Saved struct Type: Managed Assembly: _ForcePlate_

Force plate description contains names and IDs of the plate and its channels as well as other hardware parameter settings. Please refer to the [NatNetTypes.h](natnet-4.5.md#file-list) header file for specific details.

* Force plate ID and serial number
* Force plate dimensions
* Electrical offset
* Number of channels
* Channel info
* More. See _NatNetTypes.h_ file for more information

</details>

<details>

<summary>Device Description</summary>

Saved struct Type: Native Library: _sDeviceDescription_

Saved struct Type: Managed Assembly: _Device_

An instance of the sDeviceDescription contains information of the data acquisition (NI-DAQ) devices. It includes information on both the DAQ device (ID, name , serial number) as well as its corresponding channels (channel count, channel data type, channel names). Please refer to the [NatNetTypes.h](natnet-4.5.md#file-list) header file for specific details.

* Device ID. Used only for identification of devices in the stream.
* Device Name
* Device serial number
* Device Type
* Channel count
* Channel Names

</details>

<details>

<summary>Camera Description</summary>

Saved struct Type: Native Library: sCameraDescription

Saved struct Type: Managed Assembly: Camera

An instance of the sCameraDescription contains information regarding the camera name, its position, and orientation.

* Camera Name (can be used with Get/Set property commands)
* Camera Position (x, y, z float variables)
* Camera Orientation (qx, qy, qz, qw float variables)
* For more info, see the NatnetTypes.h file.

</details>

<details>

<summary>Asset Description</summary>

Saved struct Type: Native Library: _sAssetDescription_

Saved struct Type: Managed Assembly: _Asset_

Asset description contains corresponding data for trained markerset assets:&#x20;

* Asset type - Trained Markerset&#x20;
* Asset name
* Asset ID: Unique identifier
* Number of markers&#x20;
* Number of Rigid Bodies (bones) in the asset

The following asset-specific arrays are also included:&#x20;

* Rigid Body (bone) descriptions
* Marker descriptions

</details>

<details>

<summary>IMU Description</summary>

Saved Struct Type: Native Library _sIMUDescription_

Saved Struct Type: Managed Library _IMU_

IMU description contains corresponding data for Inertial Measurement Units (IMUs):&#x20;

* IMU Name
* IMU ID (tag identifier)
* IMU Sensor Fused Boolean (on/off)
* IMU Rigid Body ID that correlates the IMU to its paired Rigid Body

</details>

<details>

<summary>GPIO Description</summary>

* Saved Struct Type: Native Library _sGPIODescription_
* Saved Struct Type: Managed Library _GPIO_

GPIO Description contains corresponding data for General Purpose input/Output (GPIO) devices:&#x20;

* GPIO Name
* GPIO streaming ID
* Number of GPIO Ports
* Array of relevant pin names

</details>

<details>

<summary>Anchor Description</summary>

* Saved Struct Type: Native Library _sAnchorDescription_
* Saved Struct Type: Managed Library _Anchor_

The Anchor Description contains a corresponding anchor name, anchor streaming ID, and the x,y,z anchor coordinates. It has the hierarchal relationship as following:

* Anchor Name
* Array of coordinates that describe where the Anchor Marker is in the scene.
* Anchor Active ID

</details>

## Frame of Mocap Data

Frame-specific tracking data are stored separately from the DataDescription instances as this cannot be known ahead of time or out of band but only on a per frame basis. These data get saved into instances of **sFrameOfMocapData** for corresponding frames, and they will contain arrays of frame-specific data _structs_ (e.g.sRigidBodyData, sSkeletonData) for each of the types of assets included in the capture. Respective frame number, timecode, and streaming latency values are also saved in these packets.

The sFrameOfMocapData can be obtained by setting up a frame handler function using the [NatNetClient::SetFrameReceivedCallback](natnet-class-function-reference.md#natnetclient-setframereceivedcallback) method. In most cases, a frame handler function must be assigned in order to make sure every frame is promptly processed. Refer to the provided [_SampleClient_](natnet-sample-projects.md#running-the-.net-sample) project for an exemplary setup.

When streamed, the following data are available in the FrameOfMocapData:&#x20;

<details>

<summary>Frame Count</summary>

Host (server) defined frame number.

Variable name:

* _iFrame_

</details>

<details>

<summary>Labeled Markers</summary>

A total number of labeled markers in the frame.

Variable name:

* _nLabeledMarkers - Native_
* _nMarkers - Managed_

A list of ordered, padded, point cloud solved, model filled (where occluded) labeled marker data. The data includes the unique ID, x/y/z positions, marker size, and its residual value from reconstruction.

The labeled marker data is solved by the point cloud engine only.

**Unique ID:** For Active markers, this value represents the Active ID. For passive markers labeled through an asset, this represents both Asset ID (High-bit) and Member ID (Low-bit). For unlabeled markers, this is just arbitrary value assigned by the Point Cloud reconstruction engine.

**Active or Passive**: Within the host defined 16-bit integer _param_ value, the sixth bit represents whether the marker is active or passive. This is demonstrated in SampleClient application. e.g.) `bActiveMarker = ((data->LabeledMarkers[i].params & 0x20) == 0);`

Variable name:

* _LabeledMarkers_

</details>

<details>

<summary>Unlabeled Markers</summary>

A total number of unlabeled markers in the frame.

Variable name:

* _nOtherMarkers_

\_\_ A list of point cloud solved 3D positions (X, Y, Z) for all _unlabeled_ markers in the frame.

The unlabeled marker data is solved by the point cloud engine only.

Variable name:

* _OtherMarkers_

</details>

<details>

<summary>Marker Set Data</summary>

A total number of markersets.

Variable name:

* _nMarkerSets_

A collection of Marker Sets (Marker Set, Rigid Body, or Skeletons) in the frame. The struct includes name, number of involved markers, and their corresponding X/Y/Z locations.

In this data, the corresponding 3D marker locations are point cloud solved and model-filled on occluded frames.

Variable name:

* _MocapData - Native_
* _MarkerSets - Managed_

</details>

<details>

<summary>Rigid Body Data</summary>

A total number of Rigid Body assets, both tracked and untracked, in the frame.

Variable name:

* _nRigidBodies_

A named segment with a unique ID, position, and orientation data. For Skeletons Rigid Bodies, this will represent one of the segments on a Skeleton asset.

**Unique ID**: For Rigid Body assets, Rigid Body ID is the streaming ID assigned under the Rigid Body properties in Motive. For Skeleton assets, this ID is both the Skeleton ID (High-bit) and the Bone index ID (Low-bit).

Variable name:

* _sRigidBodyData - Native_
* _RigidBodyData - Managed_

</details>

<details>

<summary>Skeleton Data</summary>

A total number of Skeleton assets, both tracked and untracked, in the frame.

Variable name:

* _nSkeletons_

A named, hierarchical collection of RigidBody data in sRigidBodyData struct.

**Unique ID:** A unique ID is assigned to each Skeleton so that it could be referenced.

Variable name:

* sSkeletonData - Native
* SkeletonData - Managed

</details>

<details>

<summary>Force Plate Data</summary>

A total number of force plates.

Variable name:

* _nForcePlates_

Force plate channel data (Fx, Fy, Fz, Mx, My, Mz). Each channel data is saved as an instance of the sAnalogchnnelData which contains values measured from corresponding channel as well as the total number of analog subframes contained per mocap frame. Force plate data will contain multiple samples per mocap frame, depending upon the force plate acquisition rate. The total number of subframes per mocap frame can be quiried from a AnalogChannelData instance of each channel.

Variable name:

* _ForcePlates_

</details>

<details>

<summary>Device Data</summary>

A total number of analog devices in the capture. (e.g. NI-DAQ)

Variable name:

* _nDevices_

An array containing data from each of analog device channels (e.g. NI-DAQ). Each channel data will be saved as an instance of the sAnalogchnnelData which contains values measured from corresponding channel as well as the total number of analog subframes contained per mocap frame.

Variable name:

* _Devices_

</details>

<details>

<summary>Asset Data</summary>

A total number of Trained Markerset assets, both tracked and untracked, in the frame.

Variable name:

* _nAssets_

A named, hierarchical collection of RigidBody data in sRigidBodyData struct.

**Unique ID:** A unique ID is assigned to each Trained Markerset asset so that it can be referenced.

Variable name:

* sAssetData - Native
* AssetData - Managed

</details>

<details>

<summary>IMU Data</summary>

Saved Struct Type: Native Library _sIMUData_

Saved Struct Type: Managed Library: _IMUData_

Position and orientation data for IMUs in the frame.&#x20;

* Float positional values for x, y, and z
* Float rotational values for gyroscope orientation (qx, qy, qz, qw)
* Parameters value (if IMU has relevant parameters to stream)

</details>

<details>

<summary>GPIO Data</summary>

Saved Struct Type: Native Library _sGPIOData_

Managed Library: _GPIOData_

Data related to GPIO devices in the frame.&#x20;

* GPIO ID to identify tag
* Number of GPIO ports
* GPIO pin values (an array of them)

</details>

<details>

<summary>Latency</summary>

\_(Deprecated)\_Now, more accurate system latency values can be derived from the reported timestamp values. For more information, read through the [Latency Measurements](latency-measurements.md) page.

Variable name:

* _fSystemLatency_

\_(Deprecated)\_Now, more accurate software latency values can be derived from the reported timestamp values. For more information, read through the [Latency Measurements](latency-measurements.md) page.

Variable name:

* _fLatency_

</details>

<details>

<summary>Time Information</summary>

Timing information for the frame. If SMPTE timecode is detected in the system, this time information is also included. See: [OptiTrack Timecode](../../synchronization/optitrack-timecode.md)

* Frame ID
* Frame Timestamp
* SMPTE Timecode (If timecode is present)

Variable name:

* _Timecode_

The subframe value of the timecode. See: [OptiTrack Timecode](../../synchronization/optitrack-timecode.md).

Variable name:

* _TimecodeSubframe_

Software timestamp value. Reports the time since software start.

Variable name:

* _fTimestamp_

Reports the Frame ID number in the 2D Cameras view in Live/Recording/Edit modes. In Edit mode, this variable references the frame ID from the take rather than Live.

Variable name:

* _CameraMidExposureTimestamp_

Given in host's high resolution ticks, this stores a timestamp value of when Motive receives the camera data. For more information, refer to the [Latency Measurements](latency-measurements.md) article.

Variable name:

* _CameraDataReceivedTimestamp_

Given in host's high resolution ticks, this stores a timestamp value of when tracking data is fully processed and ready to be streamed out. For more information, refer to the [Latency Measurements](latency-measurements.md) article.

Variable name:

* _TransmitTimestamp_

External Precision Timestamp value. Reports Precision Time Protocol (PTP) data, if present.&#x20;

Variable names:

* _PrecisionTimeStampSecs_
* _PrecisionTimeStampFractionalSecs_

&#x20;

</details>

### Additional Notes

* One reconstructed 3D marker can be stored in two different places (e.g. in LabeledMarkers and in RigidBody) within a frame of mocap data. In those cases, [unique identifier values](natnet-data-types.md#unique-id) of the marker can be used to correlate them in the client application if necessary.
* Declarations for these data types are listed in the [NatNetTypes.h](natnet-4.5.md#file-list) header files within the SDK. The SampleClient project included in the `\NatNet SDK\Sample` folder illustrates how to retrieve and interpret the data descriptions and frame data.

{% hint style="info" %}
Refer to the NatNetTypes.h header file or the NatNetML.dll assembly for the most up to date descriptions of the types.
{% endhint %}

## Unique ID

Most of the NatNet SDK data packets contain ID values. This value is assigned uniquely to individual markers as well as each of assets within a capture. These values can be used to figure out which asset a given data packet is associated with. One common use is for correlating data descriptions and frame data packets of an asset.

**Decoding Member IDs**

For each member object that is included within a parental model, its unique ID value points to both its parental model and the member itself. Thus, the ID value of a member object needs to be decoded in order to parse which objects and the parent models they are referencing to.

For example, a Skeleton asset is a hierarchical collection of bone Rigid Bodies, and each of its bone Rigid Bodies has unique ID that references to the involved Skeleton model and the Rigid Body itself. When analyzing Skeleton bones, its ID value needs to be decoded in order to extract the segment Rigid Body ID, and only then, it can be used to reference its descriptions.

* NatNet SDK provides a C++ helper function, [NatNet\_DecodeID](natnet-class-function-reference.md#natnet_decodeid), for decoding member ID and model ID of an member object. You can also decode by manually parsing the ID as demonstrated in [the WinFormSample or the SampleClientML](natnet-sample-projects.md) sample.
