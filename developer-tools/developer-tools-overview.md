# Developer Tools Overview

here are three OptiTrack developer tools for developing custom applications: the Camera SDK, the NatNet SDK, and the Motive API. All of the tools support a C/C++ interface to OptiTrack cameras and provides control over OptiTrack motion capture systems.

Visit our [website](http://www.optitrack.com/support/developers/) to compare OptiTrack developer tools and their functions.

{% hint style="danger" %}
**SDK/API Support Disclaimer**

We provide developer tools to enable OptiTrack customers across a broad set of applications to utilize their systems in the ways that best suit them. Our Motive API through the NatNet SDK and Camera SDK is designed to enable experienced software developers to integrate data transfer and/or system operation with their preferred systems and pipelines. Sample projects are provided alongside each tool, and we strongly recommend the users to reference or use the samples as reliable starting points. The following list specifies the range of support that will be provided for the SDK tools:

* Using the SDK tools requires background knowledge on software development; therefore, we do not provide support for basic project setup, compiling, and linking when using the SDK/API to create your own applications.
* Although we ensure the SDK tools and their libraries work as intended, we do not provide support for custom developed applications that have been programmed or modified by users using the SDK tools.
* Ticketed support will be provided for licensed Motive users using the Motive API and/or the NatNet SDK tools from the included libraries and sample source codes only.
* The Camera SDK is a free product, and therefore we do not provide free ticketed support for it.
* For other questions, please check out the [NaturalPoint forums](https://forums.naturalpoint.com/). Very often, similar development issues get reported and solved there.
{% endhint %}

## Camera SDK

![](<../.gitbook/assets/image (963).png>)

**Go to the Camera SDK page:** [**Camera SDK**](camera-sdk/)

The Camera SDK provides hardware (cameras and hubs) controls and access to the most fundamental frame data, such as grayscale images and 2D object information, from each camera. Using the Camera SDK, you can develop your own image processing applications that utilize the capabilities of the OptiTrack cameras. The Camera SDK is a free tool that can be downloaded from our website.

**Note:** 3D tracking features are not directly supported with Camera SDK, but they are featured via the Motive API. For more information on the Camera SDK, visit our [website](http://www.optitrack.com/products/camera-sdk/).

## Motive API

![](<../.gitbook/assets/image (848) (1) (1) (1).png>)

**Go to the Motive API page:** [**Motive API**](motive-api/)

The Motive API allows control of, and access to, the backend software platform of Motive. Not only does it allow access to 2D camera images and the object data, but it also gives control over the 3D data processing pipeline, including solvers for the assets. Using the Motive API, you can employ the features of Motive into your custom application.

**Note:** When you install Motive, all of the required components for utilizing the API will be installed within the Motive install directory.

## NatNet SDK

![](<../.gitbook/assets/image (1011).png>)

**Go to the NatNet SDK page:** [**NatNet SDK 4.0**](natnet-sdk/natnet-4.0.md)

The NatNet SDK is a client/server networking SDK designed for sending and receiving NaturalPoint data across networks. The NatNet SDK makes the motion capture data available to other applications in real-time. It utilizes UDP along with either Unicast or Multicast communication for integrating and streaming 3D reconstructed data, Rigid Body data, and Skeleton data from OptiTrack systems. Using the NatNet SDK, you can develop custom client/server applications that utilize motion capture data. The NatNet SDK is a free tool that can be downloaded from our website.

Visit our [website](http://optitrack.com/products/natnet-sdk/) or [Data Streaming](../motive/data-streaming.md) page for more information on NatNet SDK.
