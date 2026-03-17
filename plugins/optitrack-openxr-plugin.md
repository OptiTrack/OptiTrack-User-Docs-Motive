---
description: A Quick Start Guide for using OptiTrack's OpenXR Plugin.
---

# OptiTrack OpenXR Plugin

## Overview

The OptiTrack OpenXR plugin allows Motive to connect to a Head-Mounted Display (HMD) in order to provide movement tracking to the device. This guide details the required software that must be installed to stream to a game engine or other platforms.&#x20;

## HMD Software Platform <a href="#hmd-software-platform" id="hmd-software-platform"></a>

Download and install the software platform the supports your HMD from the manufacturer.

All HMDs require their own software to connect the headset to the computer. This typically includes a user interface with systems that allow the HMD to be recognized by programs such as [SteamVR](https://naturalpoint.atlassian.net/wiki/spaces/VI/pages/2624028691/OptiTrack+OpenXR+Plugin+-+Getting+Started#SteamVR), games and other VR/XR applications.&#x20;

Follow the HMD manufacturer's instructions to download and setup the applicable software for the HMD device.&#x20;

## Connect the HMD to the Motive Computer <a href="#connecting-your-hmd-to-the-desktop" id="connecting-your-hmd-to-the-desktop"></a>

Connect the HMD to the Motive computer via the HMD's software platform. In this example, we will use the Meta Quest 2 and the Meta Quest Link App.

{% hint style="success" %}
In our testing, we connected the HMD via a quest link cable (USB-C) designed specifically for the strongest signal connection between the HMD and PC. You can also use a wireless connection, which requires access to a Wi-Fi signal on both on the HMD and PC.
{% endhint %}

<figure><img src="../.gitbook/assets/image (1583).png" alt="A screenshot of the Meta Quest 2 HMD configuration settings. The red-circled X in the status indicates that audio is disabled, while the HMD is active."><figcaption><p>The Meta Quest 2 HMD. The red-circled X in the status indicates that audio is disabled, while the HMD is active.</p></figcaption></figure>

### Set the Framerate for Tracking <a href="#steamvr" id="steamvr"></a>

Every HMD has a refresh rate for its display. Some HMDs will run at a lower refresh rate to address issues such as battery life, resolution and overall performance, but they will also include the option to increase their refresh rate.

{% hint style="warning" %}
When using Motive and the OptiTrack OpenXR Plugin, Motive must either match or be a multiple of the refresh rate of the HMD.
{% endhint %}

In the example below, the Quest 2 is running at a refresh rate of 72Hz, which is the recommended rate for the device. In Motive, the camera frame rate is set at twice that rate, 144Hz, for better tracking and a smoother experience.

<figure><img src="../.gitbook/assets/image (1584).png" alt="Screenshots showing, from left to right, the Meta Quest 2 framerate options, with 72Hz as the recommended rate, 2. The Meta Quest application, 3. the Devices pane in Motive, showing the camera frame rate of 144 Hz."><figcaption></figcaption></figure>

## SteamVR <a href="#steamvr" id="steamvr"></a>

To use the plugin, create a Steam account and download SteamVR from the Steam Store [here](https://store.steampowered.com/app/250820/SteamVR/).&#x20;

The OptiTrack OpenXR Plugin injects code into the OpenXR runtime, to use tracking data from Motive for the HMD and controllers, overriding the position and rotation values for each.&#x20;

The SteamVR interface includes options to select the OpenXR API layers, which includes Motive Tracking.&#x20;

<figure><img src="../.gitbook/assets/image (1585).png" alt="A screenshot of the SteamVR OpenXR Settings, showing the OptiTrack OpenXR Tracking Solution highlighted. "><figcaption><p>Activating the OpitTrack OpenXR plugin from the SteamVR settings. </p></figcaption></figure>

## Install the OptiTrack OpenXR Plugin <a href="#installing-the-optitrack-openxr-plugin" id="installing-the-optitrack-openxr-plugin"></a>

* Download and install the OptiTrack OpenXR plugin from the software [plugins downloads page](https://optitrack.com/support/downloads/plugins.html).&#x20;
* Select the plugins install destination as C:\Program Files\OptiTrack\\.&#x20;
* The [OptiTrack OpenXR Config Application](https://naturalpoint.atlassian.net/wiki/spaces/VI/pages/2624028691/OptiTrack+OpenXR+Plugin+-+Getting+Started#Setting-Up-the-OpenXR-Plugin-Config-App) will appear on the desktop once the installation is done.

## Setting Up the OpenXR Plugin Config App

The OpenXR Config App is the interface to control settings for the OpenXR Plugin.&#x20;

<figure><img src="../.gitbook/assets/image (1579).png" alt="A screenshot of the OptiTrack OpenXR Configuration app. "><figcaption></figcaption></figure>

{% hint style="info" %}
**We strongly recommend using** [**IMU Sensor Fusion**](../motive/imu-sensor-fusion.md) **for this workflow.**&#x20;

Tracking the HMD using an IMU sensor fused device in Motive provides the smoothest results. Without IMU sensor fusion, performance in XR experiences may be unstable or uncomfortable.&#x20;

When the Rigid Body is Sensor Fused in Motive and connected to the config app, an indicator will appear green indicating complete tracking.

<p align="center"><img src="../.gitbook/assets/Sensor Fused HMD connected.png" alt="A screenshot from the OptiTrack OpenXR Plugin, showing the HMD successfully sensor-fused with the IMU." data-size="original"></p>
{% endhint %}

To configure:&#x20;

1. Launch the OptiTrack OpenXR Config App.
2. Set the connection type to the preferred connection type. We recommend Unicast when streaming with multiple devices in the same Motive server. For more information on streaming in Motive, please see the [Settings: Streaming](../motive-ui-panes/settings/settings-streaming.md) page.
3. **Rigid Body ID:** Verify that the [Streaming ID](../motive-ui-panes/properties-pane/properties-pane-rigid-body.md#streaming-id) matches the ID of the Rigid Body HMD you are tracking in Motive. This value is shown in the [Rigid Body Properties](../motive-ui-panes/properties-pane/properties-pane-rigid-body.md) or the [Assets pane](../motive-ui-panes/assets-pane.md).&#x20;
4. **IPD:** The HMD device has an Interpupillary Distance value, commonly known as IPD. Set this value in the Config app to match The IPD value shown on the HMD display when adjusting this distance in the lenses.
5. **Controller Left/Right:** Click the _Enable Override_ toggle to track controllers using the Rigid Bodies in Motive. Verify and input the corresponding Rigid body ID with the associated controller in Motive.
6. **Status:** When the two values match, the status indicator at the bottom will turn green and display the text _Connected to Motive._ If the rigid bodies are enabled but not detected, the status indicator will be yellow, with the message _Rigid Body IDs not found_.&#x20;
7. Click _Save_ to save the profile for use within the API Layer for OpenXR.&#x20;

<figure><img src="../.gitbook/assets/OpenXR Connected.png" alt="A screenshot of the bottom of the OpenXR Configuration panel, showing the device connected to Motive and the last saved date for the Configuration file. "><figcaption></figcaption></figure>

{% hint style="success" %}
Once the initial connection to Motive is established, the Config app can be closed. The OpenXR plugin will use the properties in the saved profile each time the HMD and controllers are connected.&#x20;

To change the settings, launch the Config app and make the required changes or use the _Load_ button to import a previous configuration. &#x20;
{% endhint %}

## Steam VR Setup <a href="#steam-vr-setup" id="steam-vr-setup"></a>

1. Launch Steam VR.
2. Go to Settings.&#x20;

<figure><img src="../.gitbook/assets/image (1580).png" alt="Screenshot of the SteamVR menu, with the Settings option selected."><figcaption><p>The SteamVR menu.</p></figcaption></figure>

3. Click _OpenXR_ on the left tab and select _Manage OpenXR API Layers_.&#x20;
4. Set the _Optitrack OpenXR Tracking Solution_ to _On._

<figure><img src="../.gitbook/assets/image (1581).png" alt=""><figcaption></figcaption></figure>

When using a Meta HMD, we recommend setting SteamVR as the OpenXR runtime source instead of Meta to avoid any graphical or tracking issues.

<figure><img src="../.gitbook/assets/image (1582).png" alt=""><figcaption></figcaption></figure>

## Connect to Game Engine <a href="#final-steps" id="final-steps"></a>

You can now launch your VR Apps and platforms such as Unity or Unreal Engine with HMD tracking coming from Motive. To troubleshoot if tracking is working, open the app and disable and re-enable the rigid body tracking in Motive.

{% hint style="info" %}
**Special Note for Quest HMD Users**&#x20;

In our testing, we found that the OpenXR Runtime needs to be set to Quest to use in Unity and SteamVR to use in Unreal Engine, when using a Quest HMD.
{% endhint %}

## Troubleshooting

### Sample App

The Configuration app includes a Sample app on the Tools menu to test and verify tracking results from Motive.&#x20;

<figure><img src="../.gitbook/assets/OpenXR Tools menu - sample app.png" alt="A screenshot of the OptiTrack OpenXR plugin with the Tools menu open, showing where the Sample App is located. "><figcaption></figcaption></figure>

The Sample app will launch a 3D scene of a 2x2m space in the HMD. The plugin version is displayed on the wall and the floor grid shows the axis conventions. Use both the text on the wall and the grid to orient yourself, compare origin positions, and validate tracking framerate consistency.

### Log

The Log window is a helpful debugging tool that shows what actions and functions are happening through the OptiTrack OpenXR Plugin. You can access it from the View menu.

<figure><img src="../.gitbook/assets/OpenXR View menu - Log.png" alt="A screenshot of the OptiTrack OpenXR plugin with the View menu open, showing where the Log file is located. "><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/OpenXR - log results.png" alt="A screenshot of the Log file in the OptiTrack OpenXR plugin. "><figcaption></figcaption></figure>
