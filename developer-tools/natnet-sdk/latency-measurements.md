# Latency Measurements

This page provides detailed information on the definition of latency measurements in Motive and the NatNet SDK streaming protocol.

## Overview

The OptiTrack systems combine state of art technologies to provide swift processing of captured frame data in order to accomplish 3D tracking in real-time. However, minimal processing latencies are inevitably introduced throughout processing pipelines. For timing-sensitive applications, these latency metrics can be monitored from the [Status Panel](../../motive-ui-panes/status-panel.md) of Motive or in the [NatNet SDK 4.0](natnet-4.0.md) streaming protocol.

## Latency Simplified

The latency in an OptiTrack system can be broken down in the the components described in the image below.

![](<../../.gitbook/assets/image (984).png>)

With Motive 3.0+ PrimeX cameras now can go at up to 1000 Hz. In order to do this the image size processes reduces as the frequency goes over the native frame rate for a particular camera. Because less camera data is being process at higher rates, the latency also decreases. The image below shows how the latency changed from the previous image by going from 240 Hz to 500 Hz with PrimeX 13 cameras.

![](<../../.gitbook/assets/image (1153).png>)

Example frame rates vs the latency added by the camera for a PrimeX 41 camera....

| Rate           | Camera Latency |
| -------------- | -------------- |
| 20 Hz - 180 Hz | 5.56 ms        |
| 240 Hz         | 4.17 ms        |
| 360 Hz         | 2.78 ms        |
| 500 Hz         | 2.00 ms        |
| 1000 Hz        | 1.00 ms        |

## Latency Details

![](<../../.gitbook/assets/image (1044).png>)

| Point | Description                                                                   |
| ----- | ----------------------------------------------------------------------------- |
| A     | This point represents the center of the camera exposure window                |
| B     | This is when Motive receives the 2D data from the cameras                     |
| C     | This is when tracking data is fully solved in Motive.                         |
| D     | This is when the tracking data is all processed and ready to be streamed out. |
| E     | This is when the Client application receives the streamed tracking data.      |

### In Motive

![Status panel in Motive.](<../../.gitbook/assets/image (1038).png>)

#### **System Latency**

* This measurement is reported in the [Status Panel](../../motive-ui-panes/status-panel.md) in Motive.
* _(Available for Ethernet camera systems only)_ This value represents current system latency. This is reported under the Status Panel, and it represents the total time taken from when the cameras expose and when the data is fully solved.

#### **Software Latency (Motive)**

* This measurement is reported in the [Status Panel](../../motive-ui-panes/status-panel.md) in Motive.
* It represents the amount of time it takes Motive to process each frame of captured data. This includes the time taken for reconstructing the 2D data into 3D data, labeling and modeling the trackable assets, displaying in the viewport, and other processes configured in Motive.
* Please note that this does not include the time it takes for Motive to convert the solved data into the NatNet streaming protocol format. This conversion accounts for a slight additional latency (≈ 0.2 ms) which is only reflected in the software latency value reported via [NatNet SDK 4.0](natnet-4.0.md), therefore resulting in a small delta between the software latency values as reported by Motive and NatNet.

#### **Pipeline Specific Latencies**

* Latencies from the point cloud reconstruction engine, Rigid Body solver, and Skeleton solver are reported individually on the [Status Panel](../../motive-ui-panes/status-panel.md) in Motive.

### In NatNet

{% hint style="warning" %}
This is available only in NatNet version 3.0 or above.
{% endhint %}

{% hint style="info" %}
Exemplary latency calculations are demonstrated in the SampleClient project and the WinFormSample project. Please refer to these sources to find more about how these latency values are derived.
{% endhint %}

In NatNet 3.0, new data types have been introduced to allow users to monitor measured timestamps from specific points in the pipeline. From [sFrameOfMocapData](natnet-data-types.md#frame-of-mocap-data) received in the NatNet client applications, the following timestamps can be obtained:

* **Timestamp of Point A:** sFrameOfMocapData::CameraMidExposureTimestamp. _Available for Ethernet cameras only (Prime / Slim13E)._
* **Timestamp of Point B:** sFrameOfMocapData::CameraDataReceivedTimestamp.
* **Timestamp of Point D:** sFrameOfMocapData::TransmitTimestamp.
* Refer to the [NatNet:\_Data\_Types](natnet-data-types.md) page or the NatNetTypes.h file for more information

These timestamps are reported in “ticks” that are provided by the host computer clock. When computing latencies, you need to divide the timestamp values by the clock frequency in order to obtain the time values in seconds. The clock frequency is included in the server description packet: sServerDescriptionPacket::HighResClockFrequency. To calculate the time that has elapsed since a specific timestamp, you can simply call the [NatNetClient::SecondsSinceHostTimestamp](natnet-class-function-reference.md#natnetclient-secondssincehosttimestamp) method, passing the desired timestamp as its input. Using clock synchronization between the client and server, this will return the time in seconds since the corresponding timestamp.

**System Latency (NatNet)**

* **(Available for Ethernet camera systems only)**
* This is the latency introduced by both hardware and software component of the system. This represents the time difference between when the cameras expose and when the capture data is all processed and prepared to be streamed out.
* This value needs to be derived from the [NatNet SDK 4.0](natnet-4.0.md) streaming protocol by subtracting two timestamp values that are reported in NatNet:

```
const bool bSystemLatencyAvailable = data->CameraMidExposureTimestamp != 0;

// From SampleClient.cpp (522 ~ 531)
if ( bSystemLatencyAvailable )
{
 
        const uint64_t systemLatencyHostTicks = data->TransmitTimestamp - data->CameraMidExposureTimestamp;
        const double systemLatencyMillisec = (systemLatencyHostTicks * 1000) / static_cast<double>(g_serverDescription.HighResClockFrequency);
}
```

{% hint style="info" %}
System Latency may not always be available for all system configurations. Thus, it is suggested to enclose this calculation within a conditional statement.
{% endhint %}

**Software Latency (NatNet)**

* This value needs be derived from the NatNet streaming protocol.
* This latency value represents the time it takes Motive to process the captured data and have it fully ready to be streamed out. This measurement also covers the data packaging time.
* This can be derived by subtracting two timestamp values that are reported in NatNet:

```
// From SampleClient.cpp (502~503)
const uint64_t softwareLatencyHostTicks = data->TransmitTimestamp - data->CameraDataReceivedTimestamp;
const double softwareLatencyMillisec = (softwareLatencyHostTicks * 1000) / static_cast<double>(g_serverDescription.HighResClockFrequency);
```

{% hint style="info" %}
In the older versions of NatNet, the software latency was roughly estimated and reported as fLatency data, which is now deprecated. The derived software latency described in this can be used to replace the fLatency values.
{% endhint %}

**Transmission Latency**

* This value must be derived from the [NatNet SDK 4.0](natnet-4.0.md) streaming protocol.
* The transmission latency represents the time difference between when Motive streams out the packaged tracking data and when the data reaches the client application(s) through a selected network.
* This value can be obtained by calling the [SecondsSinceHostTimestampmethod](natnet-class-function-reference.md#natnetclient-secondssincehosttimestamp) using sFrameOfMocapData::TransmitTimestamp as the input.

```
// From SampleClient.cpp (507)
const double transitLatencyMillisec = pClient->SecondsSinceHostTimestamp( data->TransmitTimestamp ) * 1000.0;
```

**Client Latency**

* This value must be derived from the [NatNet SDK 4.0](natnet-4.0.md) streaming protocol.
* The client latency is the time difference between when the cameras expose and when the NatNet client applications receive the processed data. This is basically the total time it takes for a client application(s) to receive the tracking data from a mocap system.
* This value can be obtained by calling the [SecondsSinceHostTimestamp](https://v30.wiki.optitrack.com/index.php?title=NatNet:_Class/Function_Reference#NatNetClient::SecondsSinceHostTimestamp) method using **sFrameOfMocapData::CameraMidExposureTimestamp** as the input.

```
// Sample code
const bool bSystemLatencyAvailable = data->CameraMidExposureTimestamp != 0;

if ( bSystemLatencyAvailable )
{
    const double clientLatencyMillisec = pClient->SecondsSinceHostTimestamp(data->CameraMidExposureTimestamp) * 1000.0;
}
```

## Latency in Older Versions

In previous versions of Motive (prior to 2.0), the only reported latency metric was the software latency. This was an estimation of the software latency derived from the sum of the processing times taken from each of the individual solvers in Motive. The latency calculation in Motive 2.0 is a more accurate representation and will be slightly larger by comparison than the latency reported in the older versions.

## Troubleshooting

<details>

<summary><strong>Q: Latency increases when playing media applications on the host PC.</strong></summary>

A: When playing media files using applications such as Chrome or VLC, you may experience increased system latency in Motive. This is due to Window's Multimedia Class Scheduler Service (MMCSS). The MMCSS will prioritize CPU resources to these time-sensitive media applications over other applications including Motive. This may cause increased system latency and dropped frames in Motive. We recommend closing media applications if there are any issues with system latency and dropped frames.

</details>
