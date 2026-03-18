# NatNet: RebroadcastMotiveData Sample

Rebroadcast Motive Data sample. This is a sample NatNet application that receives tracking data from a NatNet Server (Motive) and redistributes it in other formats.

Currently, there are two supported protocols in this sample; Unity and LightCraft. The Unity protocol repackages mocap data into XML packets and delivers it to the unity game engine. The LightCraft protocol takes definitions for a single Rigid Body and sends them over a _serial port_ in a format called the Spydercam protocol. The LightCraft protocol in addition to being a demonstration of serial port communication, it allows Motive and Previzion to be completely compatible, using Mocap data to track the Previzion camera.

**Unity Protocol**

Rebroadcasts data into a XML format compatible for unity.

**Previzion Protocol**

Rebroadcasts data via Spyder Cam protocol which

## Requirements

The following third-party library must be linked in order to build and run this sample application

* Asio library ([http://think-async.com/](http://think-async.com/)) : Required for communicating tracking data through serial port communication.

## Build

* Download the asio C++ library.
* In the RebroadcastMotiveData VS project, link the downloaded library.
* Build the sample project.

## Running the Sample

You can run the app from the command line with appropriate input arguments. For example: `RebroadcastMotiveData.exe 127.0.0.1 127.0.0.1 unity` There are total four arguments that can be inputed when running the sample application.

* argument 1: IP address of the server, Motive, machine
* argument 2: When streaming to unity, input the IP address of the local machine. When streaming to the lightcraft protocol, input local serial port name (e.g. COM1)
* argument 3: Protocol type \[unity/lightcraft]
* argument 4 (optional): Input test, to run in the test mode.

![Rebroadcasting tracking data onto unity. Click image to enlarge.](<../../.gitbook/assets/image (895).png>)
