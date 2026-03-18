# NatNet: Sample Projects

This page lists out the NatNet sample applications provided with the SDK and provides instructions for some of the samples. The code samples are the quickest path towards getting NatNet data into your application. We typically recommend you:

**1. Identify your application’s development/interface requirements (managed, native, etc).2. Adapt the NatNet sample code from the corresponding NatNet sample application in the samples folder into your application.3. Use the API reference in the next page for additional information.**

The Visual Studio solution file `\Samples\NatNetSamples.sln` will open and build all of the NatNet sample projects. If you are creating an application from scratch, please refer to the following sections for application specific requirements.

## NatNet Sample Projects

The following projects are located in the `NatNet SDK\Samples` folder.

### **NatNet SDK Samples**

The following sample projects utilizes NatNet SDK library for obtaining tracking data from a connected server application.

| Sample Name                                                                               | NatNet Library Type | Description                                                                                                                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Matlab](natnet-sample-projects.md#running-the-matlab-sample)                             | Managed: Matlab     | Sample MATLAB code file (.m) for using MATLAB with the NatNet managed assembly (NatNetML.dll) using the provided [natnet.p wrapper](https://v30.wiki.optitrack.com/index.php?title=NatNet:_Matlab_Wrapper) class. Works in Matlab version 2014 or above.                                                |
| [SampleClient](natnet-sample-projects.md#running-the-console-output-sample-sample-client) | Native: C++         | Sample NatNet console app that connects to a NatNet server, receives a data stream, and writes that data stream to an ASCII file. This sample                                                                                                                                                           |
| [SampleClient3D](natnet-sample-projects.md#running-the-rigid-body-sample-sampleclient3d)  | Native: C++         | Sample NatNet application that connects to a NatNet server, receives a data stream, and displays that data in an OpenGL 3D window.                                                                                                                                                                      |
| SampleClientML                                                                            | Managed: .NET (C#)  | Sample NatNet C# console appication that connects to a NatNet server on the local IP address, receives data stream, and outputs the received data. **Note:** [**Skeleton As Rigid Bodies**](https://v30.wiki.optitrack.com/index.php?title=Data_Streaming#Streaming_SEttings) **must be set to false.** |
| [WinFormsSample](natnet-sample-projects.md#running-the-.net-sample)                       | Managed: C# .NET    | Simple C# .NET sample showing how to use the NatNet managed assembly (NatNetML.dll). This sample also demonstrates how to send and receive the NatNet commands.                                                                                                                                         |

### **Direct Depacketization Samples**

The following sample projects do not use the NatNet SDK library. Client/Server connection is established at a low-level by creating sockets and threads within the program, and the streamed data are depacketized directly from the bit-stream syntax. The following sample approaches should be used only when the use of NatNet SDK library is not applicable (e.g. streaming into UNIX clients).

| Sample Name  | Type   | Description                                                                                                                                                 |
| ------------ | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PacketClient | C++    | Simple example showing how to connect to a NatNet multicast stream and decode NatNet packets directly without using the NatNet SDK.                         |
| PythonClient | Python | Sample Python code file (.py) for using Python with NatNet streaming. This sample depacketizes data directly from the bit-stream without using the library. |

### **XML trigger broadcast**

The following samples demonstrate how to use remote triggering in Motive using the [XML formatted UDP broadcast packets](../../motive/data-streaming.md).

| Sample Name     | Type | Description                                                                                                                          |
| --------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------ |
| BroadcastSample | C++  | XML broadcast. Sample application illustrating how to use remote record trigger in Motive using XML formatted UDP broadcast packets. |

## Running the Console Output Sample (Sample Client)

#### On Windows

**1. \[Motive]** Start the Optitrack Server (e.g. Motive) and begin streaming data via the Streaming Panel.

\
**2. \[SampleClient]** Start the client application from the command prompt or directly from the `NatNet SDK/Samples/bin` folder.

\
**3. \[SampleClient]** Once the sample application starts up, it will search the local network and list out IP addresses of available tracking servers where tracking data is streamed from. Select a server address by pressing the corresponding number key.

![Motive is streaming to the local loopback address, and it is detected by the SampleClient application.](<../../.gitbook/assets/image (923).png>)

**4. \[SampleClient]** The client application is connected to the local loopback address (127.0.0.1) and receiving tracking data.

![Running the SampleClient project from the windows command prompt.](<../../.gitbook/assets/image (910).png>)

## Running the Rigid Body Sample (SampleClient3D)

The Rigid Body sample (SampleClient3D) illustrates how to decode NatNet 6DOF Rigid Body and Skeleton Segment data from OptiTrack quaternion format to euler angles and display them in a simple OpenGL 3D viewer. This sample also illustrates how to associate RigidBody/Skeleton Segment names and IDs from the data descriptions with the IDs streamed in the FrameOfMocapData packet.

#### With Client/Server on same machine:

**1. \[Motive]** Load a dataset with Rigid Body or Skeleton definitions

**2. \[Motive]** Enable network streaming ( Data Streaming Pane -> Check Broadcast Frame Data )

**3. \[Motive]** Enable streaming Rigid Body data (check Stream Options -> Stream Rigid Bodies = True)

**4. \[Sample3D]** File -> Connect

#### With Client/Server on separate machines:

**1. \[Motive]** Load a dataset with Rigid Body or Skeleton definitions

**2. \[Motive]** Set IP address to stream from (Network Interface Selection -> Local Interface)

**3. \[Motive]** Enable network streaming ( Data Streaming Pane -> Check Broadcast Frame Data )

**4. \[Motive]** Enable streaming Rigid Body data (check Stream Options -> Stream Rigid Bodies = True)

**5. \[Sample3D]** Set Client and Server IP addresses

**6. \[Sample3D]** File -> Connect

* IP Address IP Address of client NIC card you wish to use.
* Server IP Address IP Address of server entered in step 2 above.

![SampleClient3D - Decoding and draqing labeled Rigid Body position and orientation (6DoF) data.](<../../.gitbook/assets/image (850).png>)

## Running the .NET Sample

**1. \[Motive]** Start a NatNet server application (e.g. Motive).

**2. \[Motive]** Enable NatNet streaming from the Server application.

**3. \[WinFormTestApp]** Start the WinForms sample application from the NatNet Samples folder.

**4. \[WinFormTestApp]** Update the “Local” and “Server” IP Addresses as necessary.

**5. \[WinFormTestApp]** Press the “Connect” button to connect to the server.

**6. \[WinFormTestApp]** Press the “Get Data Descriptions” button to request and display a detailed description of the Server’s currently streamed objects.

**7. \[WinFormTestApp]** Select a Row in the DataGrid to display that value in the graph.

![Receiving tracking data via NatNet in a .NET environment.](<../../.gitbook/assets/image (867).png>)

![Issuing remote control commands to Motive.](<../../.gitbook/assets/image (929).png>)

## Running the Matlab Sample

**1. \[Motive]** Start a NatNet server application (e.g. Motive).

**2. \[Motive]** Enable NatNet streaming from the Server application.

**3. \[Matlab]** Start Matlab

**4. \[Matlab]** Open the NatNetPollingSample.m file.

**5. \[Matlab]** From the editor window, press Run

![Real-time streaming mocap data from Motive into Matlab. Click image to enlarge.](<../../.gitbook/assets/image (925).png>)
