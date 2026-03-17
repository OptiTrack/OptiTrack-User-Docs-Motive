# NatNet: Matlab Wrapper

## NatNet-Matlab Wrapper

To ease your use of NatNet data in MATLAB applications, we provide a wrapper class (natnet.p) for using real-time streamed NatNet data. Using this class, you can easily connect/disconnect to the server, receive the tracking data, and parse each component.

## Matlab Wrapper: Setup

The Matlab-NatNet wrapper class is a wrapper for the NatNet assembly and provides a simplified interface for managing the native members in MATLAB. The class definition and supporting code should be placed within the MATLAB PATH. The implementation automatically disposes running connections when ending a streaming session, along with basic object management. In order to use the Matlab wrapper class, the NatNetML assembly must be loaded into the MATLAB session. This is handled automatically and the first time the class is used the user is prompted to find the NatNetML.dll file in the Windows file browser. A reference to this location is used in future MATLAB sessions.

### Overview

To create an instance of the natnet wrapper class, simply call the class with no input arguments and store it in a variable.

![](<../../.gitbook/assets/image (1154).png>)

**Class Properties:** The available properties to the class can be seen with the following command, properties('natnet').

![](<../../.gitbook/assets/image (988).png>)

**Class Methods:** And Available methods

![](<../../.gitbook/assets/image (967).png>)

Creating an instance of the class does not automatically connect the object to a host application. After enabling the broadcast frame data under the [Data Streaming pane](../../motive/data-streaming.md) in Motive or in any other server, configure the connection type and IP addresses for the client and host to reflect your network setup.

![](<../../.gitbook/assets/image (1000).png>)

Then enter the following line to call the connect method for connecting to the natnet object to the host.

![](<../../.gitbook/assets/image (983).png>)

When creating a natnet class instance, the default host and client IP address is set to '127.0.0.1', which is the local loopback address of the computer. The natnet object will fail to connect if the network address of the host or client is incorrect.

## Matlab Wrapper: Polling

\
The natnet wrapper class interface has a method to poll mocap data called getFrame. getFrame method returns the data structure of the streamed data packet. Polling is supported but not recommended due to accessing errors. The function, poll.m, provides a simple example showing out to poll the frames of mocap data. After connecting the natnet object to the host server, run the polling script to acquire the data packets in the main workspace.

![](<../../.gitbook/assets/image (980).png>)

## Matlab Wrapper: Event Callbacks

\
The natnet class implements a simple interface to use event callbacks. The natnet method, addlistener, requires two input arguments. The first input is which listener slot to use, and the second is the name of the m-function file to be attached to the listener. Once the function is attached using addlistener method, it will be called each time a frame is received. When the callback function is first created, the listener is turned off by default. This is to ensure the user had control of the execution of the even callback function.

### Callback Function

**Enabling Listener:** Start receiving streamed data by enabling the callback function by calling the _enable_ method. The input of the enable method indicates the index value of the listener to enable. Multiple functions can be attached to the listener, and you can enable a specific listener by inputting its index value. Entering 0 will enable all listeners.

![](<../../.gitbook/assets/image (1014).png>)

**Disabling Listener:** There are three types of callback functions that ships with the natnet class. IF they are added to the natnet listener list and enabled, they will execute each time the host sends a frame of data. The setup.m file, contains an example of how to operate the class. To stop streaming, use the disable method and be sure to enter a value of 0 to disable all listeners.

![](<../../.gitbook/assets/image (998).png>)

## Matlab Wrapper: Motive Control

\
The natnet class also has functionality to control the Motive application. To enable recording use the _startRcord_ and _stopRecord_ methods, and for playback, use the _startPlayback_ and _stopPlayback_ methods. There are a number of additional commands as shown below.

![](<../../.gitbook/assets/image (1006).png>)

To display the actions of the class, set the _IsReporting_ property to true. This displays operations of the class to the Command Window.
