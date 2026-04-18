---
description: An overview of the samples available in the OptiTrack MATLAB plugin.
---

# OptiTrack MATLAB Plugin

## Overview

OptiTrack provides a wrapper class (natnet.m) for using real-time streamed NatNet data in MATLAB applications. Using this class, you can easily connect/disconnect to the server, receive the tracking data, and parse each component.

The Matlab-NatNet wrapper class is a wrapper for the NatNet assembly and provides a simplified interface for managing the native members in MATLAB. The class definition and supporting code should be placed within the MATLAB PATH. The implementation automatically disposes running connections when ending a streaming session, along with basic object management. In order to use the Matlab wrapper class, the NatNetML assembly must be loaded into the MATLAB session. This is handled automatically and the first time the class is used the user is prompted to find the NatNetML.dll file in the Windows file browser. A reference to this location is used in future MATLAB sessions.

The MATLAB Plugin provides Samples of Code for MATLAB users to connect to Motive via NatNet streaming. It provides support for streaming in all assets by iteration. It additionally provides examples of listeners, graphing, and data via streaming ID.

## Setup <a href="#matlab-wrapper-setup" id="matlab-wrapper-setup"></a>

Download the MATLAB plugin from our [Downloads](https://optitrack.com/support/downloads?cat=plugin) page.&#x20;

The first time you run any of the samples the system will prompt for a DLL. This is the NatNetML.dll that comes packaged with the product.&#x20;

Load the NatNetML.dll file into MATLAB when prompted, then press play.&#x20;

## MATLAB Samples&#x20;

MATLAB samples included in the OptiTrack MATLAB plugin have the prefix _OptiSample\__ in their file names.&#x20;

<figure><img src="../.gitbook/assets/All MATLAB samples.png" alt=""><figcaption><p>Extracted files for the OptiTrack MATLAB plugin.  </p></figcaption></figure>

### OptiSample\_RigidBodyGraph

The OptiTrack Sample for Rigid Body Graphing supports streaming rigid body asset data from Motive into MATLAB and graphing the results.&#x20;

This sample demonstrates how to use real time graphing from MATLAB with Motive software.

<figure><img src="../.gitbook/assets/Rigid Body Graph.png" alt=""><figcaption><p>Graphs created using the <em>OptiSample_RigidBodyGraph</em> file. </p></figcaption></figure>

#### How it Works

The NatNet wrapper class interface uses the _getFrame_ method to poll mocap data and return the data structure of the streamed data packet. Polling is supported but not recommended due to access errors.&#x20;

The function, _poll.m_, provides a simple example of how to poll the frames of mocap data. Connect the NatNet object to the host server then run the polling script to acquire the data packets in the main workspace.

### Optisample\_AllTypesPolling

The OptiTrack Sample for All Asset Types Polling supports streaming from Motive for each asset or device, including rigid bodies, NIDAQ, trained markersets, skeleton data, marker data, force plate data, and camera data. This provides sample code for polling each of the various types of data out of Motive.&#x20;

<figure><img src="../.gitbook/assets/All_types polling.png" alt=""><figcaption></figcaption></figure>

### OptiSample\_RigidBodyMarkerData

The OptiTrack Sample for Rigid Body Marker Data uses the streaming ID of a Rigid Body in Motive to obtain all the marker data for that Rigid Body. This sample demonstrates how to poll individual marker data from an asset into MATLAB.

### OptiSample\_RigidBodyPoseData

The OptiTrack Sample for Rigid Body Pose Data uses the streaming ID of a Rigid Body in Motive to poll for associated Rigid Body data including its position and orientation within Motive. This is the twin streaming ID example for MATLAB.

## Build Your Own

To create an instance of the NatNet wrapper class, call the class with no input arguments and store it in a variable.

![](<../.gitbook/assets/image (1154).png>)

**Class Properties:** To see the available properties to the class, use the following command: &#x20;

```
properties('natnet')
```

![](<../.gitbook/assets/image (988).png>)

**Class Methods Available:**&#x20;

<figure><img src="../.gitbook/assets/Methods (1).png" alt=""><figcaption></figcaption></figure>

### Event Callback Functions

Three types of callback functions are included with the NatNet class. If they are added to the NatNet listener list and enabled, they will execute each time the host sends a frame of data. The _setup.m_ file contains an example of how to operate the class.&#x20;

#### Add Listener

The NatNet method, _addlistener_, requires two input arguments. The first input indicates which listener slot to use, and the second is the name of the m-function file to be attached to the listener. Once the function is attached using the _addlistener_ method, it will be called each time a frame is received. When the callback function is first created, the listener is turned off by default to ensure the user has control of the execution of the event callback function.

Multiple functions can be attached to the listener.&#x20;

#### **Enable Listener**&#x20;

Call the _enable_ method to begin receiving streamed data.&#x20;

The input of the enable method indicates the index value of the listener to enable. To enable a specific listener enter its index value. Enter 0 to enable all listeners.

<figure><img src="../.gitbook/assets/image (1577).png" alt=""><figcaption></figcaption></figure>

#### **Disable Listener**

To stop streaming, use the disable method. To disable all listeners, enter a value of 0. To disable a specific listener enter its index value.

<figure><img src="../.gitbook/assets/image (1576).png" alt=""><figcaption></figcaption></figure>
