---
description: An overview of the NatNet SDK.
---

# NatNet 4.4

## **NatNet SDK**

The NatNet SDK is a networking software development kit (SDK) for receiving OptiTrack data across networks. It allows streaming of live or recorded motion capture data from a tracking server (e.g. Motive) into various client applications. Using the SDK, you can develop custom client applications that receive data packets containing real-time tracking information and send remote commands to the connected server. NatNet uses the **UDP protocol** in conjunction with either **Point-To-Point Unicast** or **IP Multicasting** for sending and receiving data. The following diagram outlines the major components of a typical NatNet network setup and how they establish communication between NatNet server and client application.

* For previous versions of NatNet, please refer to the provided PDF user guide that ships with the SDK.

{% hint style="info" %}
Click the Download button to access the [changelog](https://optitrack.com/support/downloads/developer-tools.html) for key changes in this version.&#x20;
{% endhint %}

{% hint style="info" %}
NatNet is backwards compatible with any version of Motive, however, older versions may be missing features that are present in newer versions.
{% endhint %}

## Overview

![](<../../.gitbook/assets/image (1150).png>)

### **SDK Contents**

The NatNet SDK consists of the following:

* **NatNet Library:** Native C++ networking library contents, including the static library file (.lib), the dynamic library file (.dll), and the corresponding header files.
* **NatNet Assembly:** Managed .NET assembly (NatNetML.dll) for use in .NET compatible clients.
* **NatNet Samples:** Sample projects and compiled executables designed to be quickly integrated into your code.

### **Additional Info**

* A NatNet server (e.g. Motive) has 2 threads and 2 sockets: one for sending tracking data to a client and one for sending/receiving commands.
* NatNet servers and clients can exist either on a same machine or on separate machines.
* Multiple NatNet clients can connect to a single NatNet server.
* When a NatNet server is configured to use IP Multicast, the data is broadcasted only once, to the Multicast group.
* Default multicast IP address: 239.255.42.99 and Port: 1511.
* IP address for unicast is defined by a server application.

## File List

The NatNet SDK is shipped in a compressed ZIP file format. Within the unzipped NatNet SDK directory, the following contents are included:

**Sample Projects: `NatNet SDK\Samples`**

The Sample folder, contains Visual Studio 2013 projects that use the NatNetSDK libraries for various applications. These samples are the quickest path towards getting NatNet data into your application. **We strongly recommend taking a close look into these samples and adapt applicable codes into your application.** More information on these samples are covered in the [NatNet Samples](natnet-sample-projects.md) page.

**Library Header Files: `NatNet SDK\include`**

The include folder contains headers files for using the NatNet SDK library.

| File                      | Description                                                                                                                                                                                                                                                                       |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| \include\NatNetTypes.h    | NatNetTypes.h header file contains the type declaration for all of the data formats that are communicated via the NatNet protocol.                                                                                                                                                |
| \include\NatNetClient.h   | NetNetClient.h header file contains declaration of the [NatNetClient](natnet-class-function-reference.md#natnetclient-class) class, which is the key object used in the SDK. This object must be initialized in order to run a client application for receiving the data packets. |
| \include\NatNetRequests.h | NatNetRequest.h header file contains a list of [NatNet commands](natnet-remote-requests-commands.md) that can be sent over to a server application using the _SendMessageAndWait_ function.                                                                                       |
| \include\NatNetRepeater.h | NatNetRepeater.h header file controls how big the packet sizes can be.                                                                                                                                                                                                            |
| \include\NatNetCAPI.h     | NatNetCAPI.h header file contains declaration for the NatNet API helper functions. These functions are featured for use with native client applications only.                                                                                                                     |

**Library DLL Files: `NatNet SDK\lib`**

NatNet library files are contained in the lib folder. When running applications that are developed against the NatNet SDK library, corresponding DLL files must be placed alongside the executables.

| File                   | Description                                                                                                                                                                                                                                                                                                                    |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| \lib\x64               | This folder contains NatNet SDK library files for 64-bit architecture.                                                                                                                                                                                                                                                         |
| \lib\x64\NatNetLib.dll | Native NatNet library for 64-bit platform architecture. These libraries are used for working with NatNet native clients.                                                                                                                                                                                                       |
| \lib\x64\NatNetML.dll  | <p>Managed NatNet assembly files for 64-bit platform architecture. These libraries are used for working with NatNet managed clients, including applications that use .NET assemblies.</p><p>Note that this assembly is derived from the native library, and to use the NatNetML.dll, NatNetLib.dll must be linked as well.</p> |
| \lib\x64\NatNetML.xml  | Includes XML documentations for use with the NatNetML.dll assembly. Place this alongside the DLL file to view the assembly reference.                                                                                                                                                                                          |
| \lib\x86               | No longer supported in 4.0                                                                                                                                                                                                                                                                                                     |
| \lib\x86\NatNetLib.dll | No longer supported in 4.0.                                                                                                                                                                                                                                                                                                    |
| \lib\x86\NatNetML.dll  | No longer supported in 4.0.                                                                                                                                                                                                                                                                                                    |
| \lib\x86\NatNetML.xml  | No longer supported in 4.0.                                                                                                                                                                                                                                                                                                    |

## API Reference

#### [NatNet: NatNetClient class reference](natnet-class-function-reference.md)

* NatNet class and function references for the _NatNetClient_ object.

#### [NatNet: Data Types](natnet-data-types.md)

* List of tracking data types available in the NatNet SDK streaming protocol.

#### [NatNet: Remote Requests/Commands](natnet-remote-requests-commands.md)

* NatNet commands for remote triggering the server application

#### [NatNet: Unicast Data Subscription Commands](natnet-unicast-data-subscription-commands.md)

* NatNet commands for subscribing to specific data types only.

## User Documentation Pages

{% hint style="info" %}
**Tip:** Code samples are the quickest path towards getting familiar with the NatNet SDK. Please check out the NatNet samples page.
{% endhint %}

#### [NatNet: Sample Projects](natnet-sample-projects.md)

* List of NatNet sample projects and the instructions.

#### [NatNet: Timecode](../../synchronization/optitrack-timecode.md)

* Timecode representation in OptiTrack systems and NatNet SDK tools.

#### [Creating a NatNet Native C++ Client](natnet-creating-a-native-c++-client-application.md)

* A general guideline to using the NatNet SDK for developing a **native** client application.

#### [Creating a NatNet Managed C# Client](natnet-creating-a-managed-c-sharp-client-application.md)

* A general guideline to using the NatNet SDK for developing a **managed** client application.

## Orientation Data in NatNet

In streamed NatNet data packets, orientation data is represented in the **quaternion format** (qx, qy, qz, qw). In contrast to Euler angles, Quaternion orientation convention is _order independent_, however, it indicates the _handedness_. When converting quaternion orientation into Euler angles, it is important to consider and decide which coordinate convention that you want to convert into. Some of the provided NatNet samples demonstrate quaternion to Euler conversion routines. Please refer to the included [WinFormSample, SampleClient3D, or Matlab samples](natnet-sample-projects.md) for specific implementation details and usage examples.

To convert from provided quaternion orientation representation, the following aspects of desired Euler angle convention must be accounted:

* Rotation Order
* Handedness: Left handed or Right handed
* Axes: Static (Global) or relative (local) axes.

\
For example, Motive uses the following convention to display the Euler orientation of an object:

* **Rotation Order:** X (Pitch), Y (Yaw), Z (Roll)
* **Handedness:** Right-handed (RHS)
* **Axes:** Relative Axes (aka 'local')

## Analog Data

When streaming analog data, all of the data will be sent, but the following issues need to be addressed in the client:&#x20;

* A mocap frame of data can contain 0, 1, or multiple analog packets, depending on how the data is transmitted from the device. For example, NI-DAQ devices send data in batches that are not necessarily aligned to the mocap frame. Rather than waiting for the NI-DAQ batch to arrive, which would introduce significant latency, the late batch is sent with the next mocap frame along with the current analog batch, if available.&#x20;
* Each analog packet is going to contain a variable number of samples per mocap frame.&#x20;

&#x20;The **SampleClient.cpp** file includes sample code for streaming analog data.&#x20;

## Direct Depacketization

In situations where the use of the NatNet library is not applicable (e.g. developing on unsupported platforms such as Unix), you can also depacketize the streamed data directly from the raw bit-stream without using the NatNet library. In order to provide the most current bitstream syntax, the NatNet SDK includes a testable working depacketization sample (PacketClient, PythonClient) that decodes NatNet Packets directly without using the NatNet client class.

DirectDepacketizers should specify the version of the bitsream they expect. Do this in the NatNet connection, using the Connection Parameters:

{% code overflow="wrap" %}
```
// sConnectionOptions
// Describes optional connection arguments.
// Only used publicly by clients who are depacketizing NatNet packets directly
// NatNetClients use sNatNetClientConnectParams
typedef struct sConnectionOptions
{
    bool subscribedDataOnly;
    uint8_t BitstreamVersion[4];
#if defined(__cplusplus)
    sConnectionOptions() : subscribedDataOnly(false)
    {
        memset(BitstreamVersion, 0, sizeof(BitstreamVersion));
    }
#endif
} sConnectionOptions;
```
{% endcode %}

Specifying the bitstream guarantees future versions of Motive will still send the requested version.

{% hint style="danger" %}
**Important Note:** The ability to specify the bitstream version applies to **Unicast** streaming only. **Multicast** streaming, by nature, sends only one packet, which will always use the bitstream format for the version of Motive installed.&#x20;
{% endhint %}

### Bit-stream Syntax

For the most up-to-date syntax, please refer to either the PacketClient sample or the PythonClient sample to use them as a template for depacketizing NatNet data packets.

1. Adapt the PacketClient sample (PacketClient.cpp) or the PythonClient sample (PythonSample.py) to your application's code.
2. Regularly update your code with each revision to the NatNet bitstream syntax.

{% hint style="info" %}
When working in Edit mode, pause playback in Motive to view the streamed data. Press the **h key** to display the NatNet help screen for additional commands.&#x20;
{% endhint %}

### Bit-stream Version

The 4.0 update included bit-stream syntax changes to allow up to 32 force plates to be streamed at once. This requires corresponding updates for each program that uses the direct depacketization approach for parsing streamed data. A system under 32 force plates should still avoid using direct depacketization. See the **Important Note** above in the Direct Depacketization section for more information.

Starting with Motive 3.0, you can send NatNet remote commands to Motive and select the version of bitstream syntax to be outputted from Motive. This is accomplished by sending a command through the command port. For details on doing this, please refer to the SetNatNetVersion function demonstrated in the PacketClient.

**Bit-Stream NatNet Versions**

* NatNet 4.3 (Motive 3.3)
* NatNet 4.2 (Motive 3.2)
* NatNet 4.1 (Motive 3.1)
* NatNet 4.0 (Motive 3.0)
* NatNet 3.1 (Motive 2.1)
* NatNet 3.0 (Motive 2.0)
* NatNet 2.10 (Motive 1.10)
* NatNet 2.9 (Motive 1.9)

