---
description: >-
  This page lists the NatNet sample applications provided with the SDK and
  provides instructions for some of the samples.
---

# NatNet: Sample Projects

Our code samples are the quickest path to get NatNet data into your application. We recommend the following steps:

1. Identify your application’s development/interface requirements (managed, native, etc.).
2. Adapt the NatNet sample code from the corresponding NatNet sample application in the samples folder into your application.
3. Use the API reference in the next page for additional information.

The Visual Studio solution file `\Samples\NatNetSamples.sln` will open and build all of the NatNet sample projects. If you are creating an application from scratch, please refer to the following sections for application specific requirements.

## NatNet Sample Projects

The following projects are located in the `NatNet SDK\Samples` folder.

### **NatNet SDK Samples**

The following sample projects utilizes NatNet SDK library for obtaining tracking data from a connected server application.

| Sample Name                                                                               | NatNet Library Type | Description                                                                                                                                                                                                                                                                                                                    |
| ----------------------------------------------------------------------------------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Matlab](natnet-sample-projects.md#running-the-matlab-sample)                             | Managed: Matlab     | Sample MATLAB code file (.m) for using MATLAB with the NatNet managed assembly (NatNetML.dll) using the provided [natnet.p wrapper](https://v30.wiki.optitrack.com/index.php?title=NatNet:_Matlab_Wrapper) class. Works in Matlab version 2014 or above.                                                                       |
| MinimalClient                                                                             | Native: C++         | <p>Sample NatNet console app that connects to a NatNet server to receive a data stream. </p><p></p><p>Contains the bare minimum code to make the NatNet connection. Good for testing connectivity. </p>                                                                                                                        |
| [SampleClient](natnet-sample-projects.md#running-the-console-output-sample-sample-client) | Native: C++         | <p>Sample NatNet console app that connects to a NatNet server, receives a data stream, and writes that data stream to an ASCII file.   </p><p></p><p>More robust than the <em>MinimalClient</em>, <em>SampleClient</em> provides a feature-rich template that includes everything necessary to build your own application.</p> |
| [SampleClient3D](natnet-sample-projects.md#running-the-rigid-body-sample-sampleclient3d)  | Native: C++         | Sample NatNet application that connects to a NatNet server, receives a data stream, and displays that data in an OpenGL 3D window.                                                                                                                                                                                             |
| SampleClientML                                                                            | Managed: .NET (C#)  | Sample NatNet C# console application that connects to a NatNet server on the local IP address, receives data stream, and outputs the received data. **Note:** [**Skeleton As Rigid Bodies**](../../motive-ui-panes/settings/settings-streaming.md#skeleton-as-rigid-bodies) **must be set to false.**                          |
| [WinFormsSample](natnet-sample-projects.md#running-the-.net-sample)                       | Managed: C# .NET    | Simple C# .NET sample showing how to use the NatNet managed assembly (NatNetML.dll). This sample also demonstrates how to send and receive the NatNet commands.                                                                                                                                                                |

### **Direct Depacketization Samples**

The following sample projects do not use the NatNet SDK library. Client/Server connection is established at a low-level by creating sockets and threads within the program, and the streamed data are depacketized directly from the bit-stream syntax. The following sample approaches should be used only when the use of NatNet SDK library is not applicable (e.g., streaming into UNIX clients).

| Sample Name  | Type   | Description                                                                                                                                                            |
| ------------ | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PacketClient | C++    | Simple example showing how to connect to a NatNet multicast stream and decode NatNet packets directly without using the NatNet SDK.                                    |
| PythonSample | Python | <p>Sample Python code file (.py) for using Python with NatNet streaming. This sample depacketizes data directly from the bit-stream without using the library.<br></p> |

{% hint style="info" %}
When working in Edit mode, pause playback in Motive to view the streamed data. Press the **h key** to display the NatNet help screen for additional commands.&#x20;
{% endhint %}

### **XML trigger broadcast**

The following samples demonstrate how to use remote triggering in Motive using the [XML formatted UDP broadcast packets](../../motive/data-streaming.md).

| Sample Name     | Type | Description                                                                                                                          |
| --------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------ |
| BroadcastSample | C++  | XML broadcast. Sample application illustrating how to use remote record trigger in Motive using XML formatted UDP broadcast packets. |

## Running NatNet Samples

### Console Output Sample (SampleClient)

1. Start the OptiTrack Server (e.g. Motive) and begin streaming data via the Streaming Panel.&#x20;
2. Start the _SampleClient_ application from the command prompt or directly from the `NatNet SDK/Samples/bin` folder.
3. At startup, the _SampleClient_ application searches the local network and lists the IP addresses of available tracking servers that are streaming tracking data.&#x20;

![Motive is streaming to the local loopback address, detected by the SampleClient application.](<../../.gitbook/assets/NatNet SampleClient select server (1).png>)

Select a server address by pressing the corresponding number key. The _SampleClient_ application will begin receiving tracking data. &#x20;

Press Q at any time to quit the _SampleClient_ application.

![Running the SampleClient project from the windows command prompt.](<../../.gitbook/assets/NatNet SampleClient Data received.png>)

### Minimal Sample (MinimalClient)

* Start the OptiTrack Server (e.g. Motive) and begin streaming data via the Streaming Panel.&#x20;
* Start the _MinimalClient_ application from the command prompt or directly from the `NatNet SDK/Samples/bin` folder.
* Data will begin streaming once the connection is established, beginning with a list all the data descriptions in the _Take,_ followed by individual frames of MoCap data.
* If the _Take_ is paused in Motive, the _MinimalClient_ will remain in a listening state, waiting for Motive to stream additional data. Start the _MinimalClient_ with playback paused if you wish to verify the data descriptions being streamed.&#x20;
* If the _MinimalClient_ cannot make a connection, the application will terminate.

<figure><img src="../../.gitbook/assets/MinimalClient Streaming paused at start.png" alt=""><figcaption><p>Connecting to the MinimalClient before starting playback in Motive.</p></figcaption></figure>

### Rigid Body Sample (SampleClient3D)

The Rigid Body sample (SampleClient3D) illustrates how to decode NatNet 6DOF Rigid Body and Skeleton Segment data from OptiTrack quaternion format to euler angles and display them in a simple OpenGL 3D viewer. This sample also illustrates how to associate RigidBody/Skeleton Segment names and IDs from the data descriptions with the IDs streamed in the FrameOfMocapData packet.

#### With Client/Server on same machine:

1. In Motive, load a dataset with Rigid Body or Skeleton definitions.
2. Enable network streaming (Data Streaming Pane -> Check Broadcast Frame Data).
3. Enable streaming Rigid Body data (check Stream Options -> Stream Rigid Bodies = True)
4. Open the Sample3D project, go to File -> Connect.

#### With Client/Server on separate machines:

1. In Motive, Load a dataset with Rigid Body or Skeleton definitions.&#x20;
2. Set the IP address to stream from (Network Interface Selection -> Local Interface).&#x20;
3. Enable network streaming ( Data Streaming Pane -> Check Broadcast Frame Data ).
4. Enable streaming Rigid Body data (check Stream Options -> Stream Rigid Bodies = True).
5. Open the Sample3D project. Set the Client and Server IP addresses.&#x20;
6. File -> Connect.

Edit the sample with the following properties:

* IP Address: Use the IP address of the client NIC card you wish to use.
* Server IP Address: IP Address of the server entered in step 2 above.

![SampleClient3D - Decoding and draqing labeled Rigid Body position and orientation (6DoF) data.](<../../.gitbook/assets/image (346).png>)

### WinForms .NET Sample

1. Start a NatNet server application, such as Motive (as used in our example).&#x20;
2. Enable NatNet streaming from the Server application.
3. Start the WinForms sample application from the NatNet Samples folder.
4. Update the _Local_ and _Server_ IP Addresses as necessary.
5. Press the _Connect_ button to connect to the server.
6. Select _Get Data Descriptions_ to request and display a detailed description of the Server’s currently streamed objects.
7. Select a Row in the DataGrid to display that value in the graph.

![Receiving tracking data via NatNet in a .NET environment.](<../../.gitbook/assets/image (1046).png>)

![Issuing remote control commands to Motive.](<../../.gitbook/assets/image (981).png>)

### Matlab Sample

1. Start a NatNet server application (e.g. Motive).
2. Enable NatNet streaming from the Server application.
3. Start Matlab.
4. Open the _NatNetPollingSample.m_ file.
5. From the editor window, press _Run_.

![Real-time streaming mocap data from Motive into Matlab. Click image to enlarge.](<../../.gitbook/assets/image (991).png>)
