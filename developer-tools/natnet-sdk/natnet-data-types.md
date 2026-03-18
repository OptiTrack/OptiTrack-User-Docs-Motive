# NatNet: Data Types

This page provides an overview of the general data structure used in the NatNet software development kit (SDK) and how the library is used to parse received tracking information.

{% hint style="info" %}
For specific details on each of the data types, please refer to the [NatNetTypes.h](natnet-4.0.md#file-list) header file.
{% endhint %}

## General Structure

When receiving streamed data using the NatNet SDK library, its data descriptions should be received before receiving the tracking data. NatNet data is packaged mainly into two different formats: data descriptions and frame-specific tracking data. Utilizing this format, the client application can discover which data are streamed out from the server application in advance to accessing the actual tracking data.

For every asset (e.g. reconstructed markers, Rigid Bodies, Skeletons, force plates) included within streamed capture sessions, their descriptions and tracking data are stored separately. This format allows frame-independent parameters (e.g. name, size, and number) to be stored within instances of the description _structs_, and frame-dependent values (e.g. position and orientation) to be stored within instances of the frame data _structs_. When needed, two different packets of an asset can be correlated by referencing to its unique identifier values.

* **Dataset Descriptions** contains descriptions of the motion capture data sets for which a frame of motion capture data will be generated. (e.g. sSkeletonDescription, sRigidBodyDescription)
* **Frame of Mocap Data** contains a single frame of motion capture data for all the datasets described from the Dataset Descriptions. (e.g. sSkeletonData, sRigidBodyData)

{% hint style="info" %}
When streaming from Motive, received NatNet data will contain only the assets that are enabled in the [Assets pane](../../motive-ui-panes/assets-pane.md) and the asset types that are set to _true_ under Streaming Settings in the [Data Streaming](../../motive/data-streaming.md) tab in Motive **Settings**.
{% endhint %}

## Dataset Descriptions

To receive data descriptions from a connected server, use the [NatNetClient::GetDataDescriptionList](natnet-class-function-reference.md#natnetclient-getdatadescriptionlist) method. Calling this function saves a list of available descriptions in an instance of sDataSetDescriptions.

The **sDataSetDescriptions** structure stores an array of multiple descriptions for each of assets (Marker Sets, RigidBodies, Skeletons, and Force Plates) involved in a capture and necessary information can be parsed from it. The following table lists out the main data description _structs_ that are available through the SDK.

{% hint style="info" %}
Refer to the [NatNetTypes.h](natnet-4.0.md#file-list) header file for more information on each data type and members of each description struct.
{% endhint %}

Description Struct

| Data Type               | Saved struct Type: Native Library | Saved struct Type: Managed Assembly |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ----------------------- | --------------------------------- | ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Server Description      | _sServerDescription_              | _ServerDescription_                 | <p>Contains basic network information of the connected server application and the host computer that it is running on. Server descriptions are obtained by calling the GetServerDescription method from the NatNetClient class.</p><ul><li>Host connection status</li><li>Host information (computer name, IP, server app name)</li><li>NatNet version</li><li>Host's high resolution clock frequency. Used for calculating the latency</li><li>Connection status</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Data Descriptions       | _sDataDescriptions_               | _List\<DataDescriptor>_             | Contains an array of data descriptions for each active asset in a capture, and basic information about corresponding asset is stored in each description packet. Data descriptions are obtained by calling the GetDataDescriptions method from the NatNetClient class. Descriptions of each asset type is explained below.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Marker Sets Description | _sMarkerSetDescription_           | _MarkerSet_                         | <p>Marker Set description contains a total number of markers in a Marker Set and each of their labels. Note that Rigid Body and Skeleton assets are included in the Marker Set as well. Also, for every mocap session, there is a special MarkerSet named <em>all</em>, which contains a list of all of the labeled markers from the capture.</p><ul><li>Name of the Marker Set</li><li>Number of markers in the set</li><li>Marker names</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Rigid Body Description  | _sRigidBodyDescription_           | _RigidBody_                         | <p>Rigid Body description contains corresponding Rigid Body names. Skeleton bones are also considered as Rigid Bodies, and in this case, the description also contains hierarchical relationship for parent/child Rigid Bodies.</p><ul><li>Rigid Body name</li><li>Rigid Body streaming ID</li><li>Rigid Body parent ID (when streaming Skeleton as Rigid Bodies)</li><li>Offset displacement from the parent Rigid Body</li><li>Array of marker locations that represent the expected marker locations of the Rigid Body asset.</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Skeleton Description    | _sSkeletonDescription_            | _Skeleton_                          | <p>Skeleton description contains corresponding Skeleton asset name, Skeleton ID, and total number of Rigid Bodies (bones) involved in the asset. The Skeleton description also contains an array of Rigid Body descriptions which relates to individual bones of the corresponding Skeleton.</p><ul><li>Name of the Skeleton</li><li>Skeleton ID: Unique identifier</li><li>Number of Rigid Bodies (bones)</li><li>Array of bone descriptions'<br></li></ul><p><strong>Update Note:</strong> In NatNet 3.0, Skeleton bone data description packet has been changed from left-handed convention to right-handed convention to be consistent with the convention used in all other data packets. For older versions of NatNet clients, the server, Motive, will detect the client version and stream out Skeleton data in the matching convention. This change will only affect direct-depacketization clients as well as clients that have the NatNet library upgraded to 3.0 from previous versions; for those clients, corresponding changes must be made to work with Motive 2.0.</p> |
| Force Plate Description | _sForcePlateDescription_          | _ForcePlate_                        | <p>Force plate description contains names and IDs of the plate and its channels as well as other hardware parameter settings. Please refer to the <a href="natnet-4.0.md#file-list">NatNetTypes.h</a> header file for specific details.</p><ul><li>Force plate ID and serial number</li><li>Force plate dimensions</li><li>Electrical offset</li><li>Number of channels</li><li>Channel info</li><li>More. See <em>NatNetTypes.h</em> file for more information</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Camera Description      | sCameraDescription                | Camera                              | <p>An instance of the sCameraDescription contains information regarding the camera name, its position, and orientation.</p><ul><li>Camera Name (can be used with Get/Set property commands)</li><li>Camera Position (x, y, z float variables)</li><li>Camera Orientation (qx, qy, qz, qw float variables)</li><li>For more info, see the NatnetTypes.h file.</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Device Description      | _sDeviceDescription_              | _Device_                            | <p>An instance of the sDeviceDescription contains information of the data acquisition (NI-DAQ) devices. It includes information on both the DAQ device (ID, name , serial number) as well as its corresponding channels (channel count, channel data type, channel names). Please refer to the <a href="natnet-4.0.md#file-list">NatNetTypes.h</a> header file for specific details.</p><ul><li>Device ID. Used only for identification of devices in the stream.</li><li>Device Name</li><li>Device serial number</li><li>Device Type</li><li>Channel count</li><li>Channel Names</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

## Frame of Mocap Data

As mentioned in the beginning, frame-specific tracking data are stored separately from the DataDescription instances as this cannot be known ahead of time or out of band but only by per frame basis. These data gets saved into instances of **sFrameOfMocapData** for corresponding frames, and they will contain arrays of frame-specific data _structs_ (e.g.sRigidBodyData, sSkeletonData) for each types of assets included in the capture. Respective frame number, timecode, and streaming latency values are also saved in these packets.

The sFrameOfMocapData can be obtained by setting up a frame handler function using the [NatNetClient::SetFrameReceivedCallback](natnet-class-function-reference.md#natnetclient-setframereceivedcallback) method. In most cases, a frame handler function must be assigned in order to make sure every frames are promptly processed. Refer to the provided [_SampleClient_](natnet-sample-projects.md#running-the-.net-sample) project for an exemplary setup.

FrameOfMocapData

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

**Unique ID:** A unqiue ID is assigned to each Skeleton so that it could be referenced.

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

<summary>Latency</summary>

\_(Deprecated)\_Now, more accurate system latency values can be derived from the reported timestamp values. For more information, read through the [Latency Measurements](https://v30.wiki.optitrack.com/index.php?title=Latency_Measurements) page.

Variable name:

* _fSystemLatency_

\_(Deprecated)\_Now, more accurate software latency values can be derived from the reported timestamp values. For more information, read through the [Latency Measurements](https://v30.wiki.optitrack.com/index.php?title=Latency_Measurements) page.

Variable name:

* _fLatency_

</details>

<details>

<summary>Time Information</summary>

Timing information for the frame. If SMPTE timecode is detected in the system, this time information is also included. See: [OptiTrack Timecode](https://v30.wiki.optitrack.com/index.php?title=OptiTrack_Timecode)

* Frame ID
* Frame Timestamp
* SMPTE Timecode (If timecode is present)

Variable name:

* _Timecode_

The subframe value of the timecode. See: [OptiTrack Timecode](https://v30.wiki.optitrack.com/index.php?title=OptiTrack_Timecode).

Variable name:

* _TimecodeSubframe_

Software timestamp value. Reports the time since software start.

Variable name:

* _fTimestamp_

Given in host's high resolution ticks, this stores a timestamp value of when the cameras expose. The timestamp precisely indicates the center of the exposure window. For more information, refer to the [Latency Measurements](https://v30.wiki.optitrack.com/index.php?title=Latency_Measurements) article.

Variable name:

* _CameraMidExposureTimestamp_

Given in host's high resolution ticks, this stores a timestamp value of when Motive receives the camera data. For more information, refer to the [Latency Measurements](https://v30.wiki.optitrack.com/index.php?title=Latency_Measurements) article.

Variable name:

* _CameraDataReceivedTimestamp_

Given in host's high resolution ticks, this stores a timestamp value of when tracking data is fully processed and ready to be streamed out. For more information, refer to the [Latency Measurements](https://v30.wiki.optitrack.com/index.php?title=Latency_Measurements) article.

Variable name:

* _TransmitTimestamp_

</details>

### Additional Notes

* One reconstructed 3D marker can be stored in two different places (e.g. in LabeledMarkers and in RigidBody) within a frame of mocap data. In those cases, [unique identifier values](natnet-data-types.md#unique-id) of the marker can be used to correlate them in the client application if necessary.
* Declarations for these data types are listed in the [NatNetTypes.h](natnet-4.0.md#file-list) header files within the SDK. The SampleClient project included in the `\NatNet SDK\Sample` folder illustrates how to retrieve and interpret the data descriptions and frame data.

{% hint style="info" %}
Refer to the NatNetTypes.h header file or the NatNetML.dll assembly for the most up to date descriptions of the types.
{% endhint %}

## Unique ID

Most of the NatNet SDK data packets contain ID values. This value is assigned uniquely to individual markers as well as each of assets within a capture. These values can be used to figure out which asset a given data packet is associated with. One common use is for correlating data descriptions and frame data packets of an asset.

**Decoding Member IDs**

For each member object that is included within a parental model, its unique ID value points to both its parental model and the member itself. Thus, the ID value of a member object needs to be decoded in order to parse which objects and the parent models they are referencing to.

For example, a Skeleton asset is a hierarchical collection of bone Rigid Bodies, and each of its bone Rigid Bodies has unique ID that references to the involved Skeleton model and the Rigid Body itself. When analyzing Skeleton bones, its ID value needs to be decoded in order to extract the segment Rigid Body ID, and only then, it can be used to reference its descriptions.

* NatNet SDK provides a C++ helper function, [NatNet\_DecodeID](natnet-class-function-reference.md#natnet_decodeid), for decoding member ID and model ID of an member object. You can also decode by manually parsing the ID as demonstrated in [the WinFormSample or the SampleClientML](natnet-sample-projects.md) sample.
