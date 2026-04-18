# Unreal Engine: HMD Setup

This page provides instructions on setting up the [OptiTrack OpenVR driver](../optitrack-openvr-driver.md) for integrating OptiTrack system with Vive HMDs within SteamVR applications; including Unreal Engine and Unity.



## **Overview**

For integrating Vive HMDs, the **OptiTrack OpenVR Driver** must be used. This driver lets you track the head-mounted display (HMD) and the VR controllers using OptiTrack motion capture system and stream the tracking data from Motive directly into SteamVR. In other words, this will basically override the tracking from the lighthouse stations. The plugin ships as an installer package (MSI) which will set up the driver along with a utility tool for configuring client streaming settings. Once integrated, the streamed tracking data can be used in any application platform that utilizes SteamVR. For tracking of objects other than the HMDs, please read through the [OptiTrack Unreal Engine Plugin](./) page for details.

**Supported Systems**

* Vive
* Vive Pro 1/2
* Valve Index
* HP Reverb G2

## Unreal Engine Plugin

### **Unreal Engine 4**

When developing for SteamVR applications using the OpenVR Driver to track the HMD in Unreal Engine 4, the **OptiTrack - Streaming Client version 2.27** must be used and the **OptiTrack - VR Latency Optimization version 2.27** plugin is suggested. The **OptiTrack - VR Latency Optimization** provides HMD render compensation that helps to minimize the latency in VR application.

![OptiTrack plugins listed in UE4.](<../../.gitbook/assets/image (350).png>)

### **Unreal Engine 5**

The latest plugins that support Unreal Engine 5 are **OptiTrack - Live Link version 3.0** and **OptiTrack - Streaming Client version 3.0**.

![OptiTrack plugins listed in UE5.](<../../.gitbook/assets/image (1209).png>)

## HMD Setup

First of all, setup and optimize the motion capture volume as explained in the [Getting Started guide](../../quick-start-guides/quick-start-guide-getting-started.md) or the [Hardware Setup](../../hardware/) documentation. If you plan to install any obstacles (e.g. walls) within the capture volume, make sure they are non-reflective, and place and orient the cameras so that every corner is thoroughly captured by multiple cameras.

**General Setup Steps**

1. Attach the markers on the HMD
2. Create a Rigid Body asset
3. Calibrate the Pivot Point of the Rigid Body
4. Configure the Rigid Body settings in Motive

### Place Markers on the HMD

For the camera system to track the HMD, a set of markers must be attached to the HMD. You can either use the active markers (Active HMD clip or Active Tags) or the passive markers. Passive markers are retroreflective markers that reflect infrared light emitted from the IR LEDs on the camera. On the other hand, the active markers are LED markers that emit the IR light and has the intelligence to be uniquely identified.

In general, for most VR applications, using active markers is recommended for better tracking stability and ease of use. Active markers also have advantages over passive markers when tracking a large number of objects. For applications that are sensitive to the accuracy of the tracking data, using passive marker may have more benefits. To get more help with finding the best solution for your tracking application, please [contact us](https://optitrack.com/contact/).

When using the active markers, you can conveniently put a set of 8 markers onto the HMD by using the HMD Clip, or you can attach the markers from the Tag manually onto the HMD using adhesives and marker posts.

{% tabs %}
{% tab title="HMD Clip" %}
**Active HMD Clip**

Active HMD Clip is an HMD enclosure with a total of 8 active markers embedded for tracking. At the time of writing, there are active HMD clips for Vive Pro / Valve Index HMDs available on the webstore. The clips can be mounted easily by pushing it onto the HMD until the latches click, and you can detach it by gently lifting the three latches located at the top, left, and right side of the clip.

Once the clip has been mounted, next step is to import the provided [Rigid Body asset](../../motive/rigid-body-tracking/) into Motive and refine the definition to get the calibrated pivot point position and orientation, which will be explained on the next section.

![Active marker clip for HTC Vive Pro.](<../../.gitbook/assets/image (167) (1) (1) (2).png>) ![Active marker clip for HP Reverb G2.](<../../.gitbook/assets/image (814).png>)
{% endtab %}

{% tab title="Markers" %}
**Marker Types**

You can either use the passive retro-reflective type markers or the active LED markers to track the HMD. Passive markers are retroreflective markers that reflect infrared light emitted from the IR LEDs on the camera. On the other hand, the active markers are LED markers that emit the IR light which gets uniquely identified in Motive. Either type of marker can be used to track HMDs. Using [active marker](../../active-components/active-marker-tracking/) is recommended especially for applications that involve tracking of multiple HMDs in the scene.

**Marker Placement**

* Make sure the markers are attached securely and do not move. If the markers happen to move even slightly after a Rigid Body is defined, it will negatively affect the tracking and the Rigid Body definition may need to be updated.
* Avoid placing multiple markers in close vicinity as they may overlap in the camera view in certain orientations.
* Using marker _posts_ to extend out the markers is recommended to improve marker visibility from more angles.
* If you are using the active markers, there is an extra USB port on the HMD that you could draw the power from.
* Please read through the [Rigid Body Tracking](../../motive/rigid-body-tracking/) page for additional information on the marker placement on a Rigid Body.
{% endtab %}
{% endtabs %}

### Create HMD Rigid Body in Motive

![Creating an HMD Rigid Body in the Builder pane.](<../../.gitbook/assets/image (1313).png>)

{% hint style="warning" %}
This feature can be used only with HMDs that have an OptiTrack Active HMD clips mounted.
{% endhint %}

For using OptiTrack system for VR applications, it is important that the pivot point of HMD Rigid Body gets placed at the appropriate location, which is at the root of the nose in between the eyes. When using the HMD clips, you can utilize the HMD creation tools in the Builder pane to have Motive estimate this spot and place the pivot point accordingly. It utilizes known marker configurations on the clip to precisely positions the pivot point and sets the desired orientation.

{% hint style="info" %}
HMDs with passive markers can utilize the [External Pivot Alignment](../../motive/rigid-body-tracking/#adjusting-rigid-body-pivot-point) tool to calibrate the pivot point.
{% endhint %}

**Steps**

1. First, make sure Motive is configured for tracking [active markers](../../active-components/active-marker-tracking/).
2. Open the [Builder pane](../../motive-ui-panes/builder-pane.md) under [View tab](../../motive-ui-panes/toolbar-command-bar.md#view) and click _Rigid Bodies_.
3. Under the _Type_ drop-down menu, select HMD. This will bring up the options for defining an HMD Rigid Body.
4. If the selected marker matches one of the Active clips, it will indicate which type of Active Clip is being used.
5. Under the _Orientation_ drop-down menu, select the desired orientation of the HMD. The orientation used for streaming to Unity is +Z forward and Unreal Engine is +X forward, or you can also specify the expected orientation axis on the client plugin side.
6. Hold the HMD at the center of the tracking volume where all of the active markers are tracked well.
7. Select the 8 active markers in the [3D viewport](../../motive-ui-panes/viewport.md#perspective-view).
8. Click _Create_. An HMD Rigid Body will be created from the selected markers and it will initiate the calibration process.
9. During calibration, slowly rotate the HMD to collect data samples in different orientations.
10. Once all necessary samples are collected, the calibrated HMD Rigid Body will be created.

## Setting up the OpenVR driver

{% hint style="info" %}
**SteamVR Required**: The VR driver streams tracking data through SteamVR. Please make sure SteamVR is installed on the computer before setting up the driver.
{% endhint %}

### Setup Steps

#### **Download and run the installer**

Download the OpenVR driver from the [downloads](https://optitrack.com/support/downloads?cat=plugin) page. Once downloaded, launch the installer and follow the prompts to set up the driver. On the last window, make sure to select **Launch Configuration Utility** before clicking **Finish**. This will open the Configuration options to setup your HMD with Motive.

{% hint style="info" %}
You may receive a warning window prior to the installation wizard. To circumvent this, select **More info** and then **Run Anyway**.
{% endhint %}

![Windows installation warning.](<../../.gitbook/assets/image (1291).png>) ![OptiTrack OpenVR Driver Setup Wizard Window.](<../../.gitbook/assets/image (1307).png>)

#### **Open the configuration program**

Once the driver has been successfully installed, launch the configuration utility software (C:\Program Files\OptiTrack\OpenVR Driver\ConfigUtil). Using this tool, you can load and check existing configurations and make changes to the settings as needed. To import current settings, click _Load_ and to save out the changes, click _Save_.

Please make sure you are running this tool with admin privileges; if not, it might not be able to modify the settings properly. If the configuration software detects a running instance of SteamVR through OpenVR, it will be indicated as _Initialized_ at the very top as shown in the image. Please note that when the settings get modified while SteamVR is running, the SteamVR must be restarted to apply the changes.

![](<../../.gitbook/assets/image (180) (1) (1) (1) (9).png>)

#### **Configure connection settings**

First, configure the connection settings so that the driver listens to the Motive server where the tracking data is streamed from. The server address must match the address where Motive is streaming the data to, and the local address must match the IP address of the computer on the network where the driver is installed.

![](<../../.gitbook/assets/image (772).png>)

![](<../../.gitbook/assets/image (180) (1) (1) (1) (15).png>)

#### **Set up the HMD**

In the HMD section, enable the HMD and input the Rigid Body ID of the HMD. The Rigid Body ID must match the [Streaming ID](../../motive-ui-panes/properties-pane/properties-pane-rigid-body.md#streaming-id) property of the HMD Rigid Body definition in Motive.

![](<../../.gitbook/assets/image (182) (1) (1) (2).png>)

![](<../../.gitbook/assets/image (34) (1) (1) (1) (4).png>)

#### **Save out the configuration**

Save the configurations by clicking on _Save_. This will modify the set of configurations in the _steamvr.settings_ file in the steam installation directory and they will override the HMD tracking with the tracking data from Motive. If you already had an instance of OpenVR or SteamVR running, restart the application to apply the changes.

{% hint style="info" %}
**Configuration File**

The configuration tool basically imports and modifies the contents in the **steamvr.settings** file (C:\Program Files (x86)\Steam\config\steamvr.settings). When needed, the driver related settings can be changed directly from this file also, but it will be easier to configure the settings using the provided configuration tool.
{% endhint %}

**Confirm the setup**

Launch SteamVR. If the driver is successfully set up, you should see a tracker icon added to the right of the HMD icon and the HMD will now be using the motion capture system instead of the base stations. Here, please make sure all of the lighthouse base stations are powered off.

![](<../../.gitbook/assets/image (1271).png>)

### VIVE Controllers

{% hint style="danger" %}
**VIVE controllers** are a Beta feature and may not work for every device. Support for this particular feature is limited.
{% endhint %}

#### **Setting up the controller (optional)**

When needed, the Vive controllers can be configured as well. To do so, open the configuration utility tool while SteamVR is running. At the top of the configuration tool, it should indicate OpenVR status as _Initialized_ and the controllers must be showing up in SteamVR. Then, in the controller sections, enable the controllers, specify the override device using the drop-down menu, and input the corresponding streaming ID of the controller Rigid Bodies in Motive. Once everything has been configured, save the changes and restart SteamVR. When the override is configured properly, SteamVR will have an additional tracker icon per each enabled controller.

![](<../../.gitbook/assets/image (103) (1) (1) (1) (1) (3).png>)

## Data Streaming

Now that the driver is set up, the HMD tracking will be overridden by tracking data from the mocap camera system, and you can integrate HMDs into the game engine through their own VR integration.

### Streaming settings in Motive

![HMD Rigid Body streaming settings in Motive.](<../../.gitbook/assets/image (129) (1) (1) (1) (3).png>)

First, make sure the streaming settings are configured in Motive for streaming out the data. For more information regarding streaming in Motive please visit our [Streaming ](../../motive/data-streaming.md)wiki page:

* **Enable** must be set to toggled on.
* **Local interface** must be set to the desired IP address to stream the tracking data from.
* Streaming of **Rigid Bodies** must be set to True
* For wireless streaming, use **Unicast** streaming type.

### Confirm the Connection

Once Motive is configured for streaming, launch SteamVR home to check the connection. If everything is setup correctly, you should be able to move around, or translate, within the scene freely. You may also need to check the ground plane to make sure it's well aligned.

If you experience any unexpected rotations in the view as you move your head, it could indicate that the HMD pivot point has not been calibrated properly. Please revisit the HMD Setup section and make sure the HMD Rigid Body pivot point is positioned and oriented at the expected pivot; which is at the root of nose with z-forward.

### Developing in Unreal Engine

Make sure Unreal Engine is configured for SteamVR development. Please refer to the Unreal Engine's documentation for more information on developing for SteamVR.

[**Developing for SteamVR**](https://docs.unrealengine.com/5.0/en-US/develping-for-steamvr-in-unreal-engine/)

## Streaming Rigid Body/Skeleton data

This driver is designed for streaming of HMD and controller tracking data only. For streaming tracking data of other Rigid Body objects, use the corresponding plugins, UnrealEngine or Unity, available on our [Downloads](https://optitrack.com/support/downloads?cat=plugin) page. The HMD tracking data will be streamed through the SteamVR using the driver you've installed, and all other tracking data will be streamed through the plugin.

### Aligning world coordinates with the UE plugin

**Client Origin**

When using the OpenVR driver for the HMD and the game engine plugins (UE/Unity) for other types of tracking data, including Rigid Body data, the client origin object must be located at the global origin without any rotations. In other words, the position must be set to (0,0,0) and the rotation must be set to (0,0,0) on the client origin. This is important because this will align the coordinate system from the (UE/Unity) plugin with the coordinate system in OpenVR pipeline

**Notes for Unreal Engine Users**

When using the Unreal Engine plugin, you will need to additionally create a custom pawn for properly aligning the coordinate systems between SteamVR and OptiTrack UE plugin:

1. Create an "OptTrack Client Origin" to the scene and set the relevant connection info. Refer to the [OptiTrack Unreal Engine Plugin](./) page for more information on setting up the client origin.
2. Create a new pawn. Right-click in Content Browser, and from the context menu, select _Blueprint → Blueprint Class → Pawn_.
3. Load created Blueprint in the editor and add a camera component.
4. _(optional)_ Double-check that the “Lock to HMD” property is set to true under the camera component properties in the details pane.
5. Select the pawn and set the “Base Eye Height” property to 0 in the details pane.
6. Compile the pawn then add it to the scene.
7. Select the pawn and set the “Auto Possess Player” to “Player 0”.
8. The HMD should now be working for Levels built for VR.

![Configured properties of the custom pawn.](<../../.gitbook/assets/image (736).png>)

![Configured properties of the added camera component.](<../../.gitbook/assets/image (1335).png>)
