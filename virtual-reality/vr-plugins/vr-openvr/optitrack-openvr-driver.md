# OptiTrack OpenVR Driver

## **Overview**

The OptiTrack VR driver lets you stream tracking data of the head-mounted display (HMD) and the controllers from Motive into SteamVR. The plugin ships in an installer package (MSI), and it will set up the driver along with a tool for configuring streaming settings. Using this, the tracking data from Motive can be used to override the tracking of the VR system in any applications that are compatible with SteamVR.

{% hint style="info" %}
**Supported HMDs**:

* Vive
* Vive Pro
* Vive Pro 2
* Valve Index
* HP Reverb
{% endhint %}

{% hint style="warning" %}
HP Reverb Notice

* Stuttering will occur when exceeding the frame period (i.e. rendering too much data will cause tracking noise).&#x20;

Beginning with Windows Mixed Reality for SteamVR v1.3.58.0:

* When starting the WMR for SteamVR, the HP Reverb must be facing forward down the Z+ axis.&#x20;

These changes are due to updates to WMR for SteamVR and are out of OptiTrack's control.
{% endhint %}

### **Requirements**

* Motive version 2.2 or higher
* SteamVR installed on the host computer.

## HMD Setup

### Place Markers on the HMD

For the camera system to track the HMD, a set of markers must be attached to the HMD. You can either use the active markers (Active HMD clip or Active Tags) or the passive markers. Passive markers are retroreflective markers that reflect infrared light emitted from the IR LEDs on the camera. On the other hand, the active markers are LED markers that emit the IR light and has the intelligence to be uniquely identified.

In general, for most VR applications, using active markers is recommended for better tracking stability and ease of use. Active markers also have advantages over passive markers when tracking a large number of objects. For applications that are sensitive to the accuracy of the tracking data, using passive marker may have more benefits. To get more help with finding the best solution for your tracking application, please [contact us](https://optitrack.com/contact/).

When using the active markers, you can conveniently put a set of 8 markers onto the HMD by using the HMD Clip, or you can attach the markers from the Tag manually onto the HMD using adhesives and marker posts.

{% tabs %}
{% tab title="HMD Clip" %}
**Active HMD Clip**

Active HMD Clip is an HMD enclosure with a total of 8 active markers embedded for tracking. At the time of writing, there are active HMD clips for Vive Pro / Valve Index HMDs available on the webstore. The clips can be mounted easily by pushing it onto the HMD until the latches click, and you can detach it by gently lifting the three latches located at the top, left, and right side of the clip.

Once the clip has been mounted, next step is to import the provided [Rigid Body asset](../../../motive/rigid-body-tracking/) into Motive and refine the definition to get the calibrated pivot point position and orientation, which will be explained on the next section.
{% endtab %}

{% tab title="Markers" %}
**Marker Types**

You can either use the passive retro-reflective type markers or the active LED markers to track the HMD. Passive markers are retroreflective markers that reflect infrared light emitted from the IR LEDs on the camera. On the other hand, the active markers are LED markers that emit the IR light which gets uniquely identified in Motive. Either type of marker can be used to track HMDs. Using [active marker](../../../active-components/active-marker-tracking/) is recommended especially for applications that involve tracking of multiple HMDs in the scene.

**Marker Placement**

* Make sure the markers are attached securely and do not move. If the markers happen to move even slightly after a Rigid Body is defined, it will negatively affect the tracking and the Rigid Body definition may need to be updated.
* Avoid placing multiple markers in close vicinity as they may overlap in the camera view in certain orientations.
* Using marker _posts_ to extend out the markers is recommended to improve marker visibility from more angles.
* If you are using the active markers, there is an extra USB port on the HMD that you could draw the power from.
* Please read through the [Rigid Body Tracking](../../../motive/rigid-body-tracking/) page for additional information on the marker placement on a Rigid Body.
{% endtab %}
{% endtabs %}

### Create HMD Rigid Body in Motive

![Creating an HMD Rigid Body in the Builder pane.](<../../../.gitbook/assets/image (419) (1) (1) (1) (6).png>)

**This feature can be used only with HMDs that have the** [**OptiTrack Active HMD**](http://optitrack.com/products/active-components/) **clips mounted.**

For using OptiTrack system for VR applications, it is important that the pivot point of HMD Rigid Body gets placed at the appropriate location, which is at the root of the nose in between the eyes. When using the HMD clips, you can utilize the HMD creation tools in the Builder pane to have Motive estimate this spot and place the pivot point accordingly. It utilizes known marker configurations on the clip to precisely positions the pivot point and sets the desired orientation.

{% hint style="info" %}
HMDs with passive markers can utilize the [External Pivot Alignment](../../../motive/rigid-body-tracking/#adjusting-rigid-body-pivot-point) tool to calibrate the pivot point.
{% endhint %}

#### **Steps**

1. First of all, make sure Motive is configured for tracking [active markers](../../../active-components/active-marker-tracking/).
2. Open the [Builder pane](../../../motive-ui-panes/builder-pane.md) under [View tab](../../../motive-ui-panes/toolbar-command-bar.md#view) and click _Rigid Bodies_.
3. Under the _Type_ drop-down menu, select HMD. This will bring up the options for defining an HMD Rigid Body.
4. If the selected marker matches one of the Active clips, it will indicate which type of Active Clip is being used.
5. Under the _Orientation_ drop-down menu, select the desired orientation of the HMD. The orientation used for streaming to Unity is +Z forward and Unreal Engine is +X forward, or you can also specify the expected orientation axis on the client plugin side.
6. Hold the HMD at the center of the tracking volume where all of the active markers are tracked well.
7. Select the 8 active markers in the [3D viewport](../../../motive-ui-panes/viewport.md#perspective-view).
8. Click _Create_. An HMD Rigid Body will be created from the selected markers and it will initiate the calibration process.
9. During calibration, slowly rotate the HMD to collect data samples in different orientations.
10. Once all necessary samples are collected, the calibrated HMD Rigid Body will be created.

{% hint style="info" %}
**This is supported only for Motive versions 2.1.2 or above.** If you are using any other versions of Motive 2.1, please update the version to 2.1.2, or use a template to create the Rigid Body definition; instructions for which is provided in the following page: [Using a Template File to Create Vive Pro Active Clip Rigid Body](https://github.com/OptiTrack/GitBook-Wiki/blob/main/virtual-reality/vr-plugins/vr-openvr/broken-reference/README.md).
{% endhint %}

## Setting up the OpenVR Driver

{% hint style="info" %}
**SteamVR Required**: The VR driver streams tracking data through SteamVR. Please make sure SteamVR is installed on the computer before setting up the driver.
{% endhint %}

### **Download and run the installer**

Download the OpenVR driver from the [downloads](https://optitrack.com/downloads/plugins.html) page. Once downloaded, launch the installer and follow the prompts to set up the driver. On the last window, make sure to select **Launch Configuration Utility** before clicking **Finish**. This will open the Configuration options to setup your HMD with Motive.

{% hint style="info" %}
You may receive a warning window prior to the installation wizard. To circumvent this, select **More info** and then **Run Anyway**.
{% endhint %}

![Windows installation warning.](<../../../.gitbook/assets/image (1238).png>) ![OptiTrack OpenVR Driver Setup Wizard Window.](<../../../.gitbook/assets/image (1183).png>)

### **Open the configuration program**

Once the driver has been successfully installed, launch the configuration utility software (C:\Program Files\OptiTrack\OpenVR Driver\ConfigUtil). Using this tool, you can load and check existing configurations and make changes to the settings as needed. To import current settings, click _Load_ and to save out the changes, click _Save_.

Please make sure you are running this tool with admin privileges; if not, it might not be able to modify the settings properly. If the configuration software detects a running instance of SteamVR through OpenVR, it will be indicated as _Initialized_ at the very top as shown in the image. Please note that when the settings get modified while SteamVR is running, the SteamVR must be restarted to apply the changes.

<figure><img src="../../../.gitbook/assets/image (842).png" alt=""><figcaption></figcaption></figure>

### **Configure connection settings**

First, configure the connection settings so that the driver listens to the Motive server where the tracking data is streamed from.&#x20;

![](<../../../.gitbook/assets/image (1353).png>)

<figure><img src="../../../.gitbook/assets/image (761).png" alt=""><figcaption></figcaption></figure>

**Connection Type**

Choose between either Unicast or Multicast. This should match the settings within Motive.&#x20;

#### Server Address

The server address must match the address where Motive is streaming the data to.&#x20;

#### Local Address

The local address must match the IP address of the computer on the network where the driver is installed.

#### Tracking Type

Choose your tracking type that is applicable to your setup.&#x20;

* Standard Tracking
  * Standard tracking involves sensor fusion tracking for the HMD along with OptiTrack outside-in tracking for controllers.&#x20;
* &#x20;OptiTrack Only&#x20;
  * OptiTrack only is OptiTrack outside-in tracking that applies to both the HMD and the controllers.&#x20;
* HMD Tracking Only
  * This tracking uses only the native tracking of the HMD and controllers without OptiTrack input.&#x20;

{% hint style="info" %}
Controllers are only able to be tracked solely by OptiTrack outside-in tracking or it's own native tracking. Controllers are explicitly designed to not have sensor fusion tracking.
{% endhint %}

### **Set up the HMD**

In the HMD section, enable the HMD and input the Rigid Body ID of the HMD. The Rigid Body ID must match the [Streaming ID](../../../motive/rigid-body-tracking/) property of the HMD Rigid Body definition in Motive.

<figure><img src="../../../.gitbook/assets/image (782).png" alt=""><figcaption></figcaption></figure>

![](<../../../.gitbook/assets/image (1317).png>)

#### **Save out the configuration**

Save the configurations by clicking on _Save_. This will modify the set of configurations in the _steamvr.settings_ file in the steam installation directory and they will override the HMD tracking with the tracking data from Motive. If you already had an instance of OpenVR or SteamVR running, restart the application to apply the changes.

{% hint style="info" %}
**Configuration File**

The configuration tool basically imports and modifies the contents in the **steamvr.settings** file (C:\Program Files (x86)\Steam\config\steamvr.settings). When needed, the driver related settings can be changed directly from this file also, but it will be easier to configure the settings using the provided configuration tool.
{% endhint %}

#### **Confirm the setup**

Launch SteamVR. If the driver is successfully set up, you should see a tracker icon added to the right of the HMD icon and the HMD will now be using the motion capture system instead of the base stations. Here, please make sure all of the lighthouse base stations are powered off.

![](<../../../.gitbook/assets/image (694) (1) (1) (2).png>)

### VIVE Controllers

{% hint style="danger" %}
**VIVE controllers** are a Beta feature and may not work for every device. Support for this particular feature is limited.
{% endhint %}

#### **Setting up the controller (optional)**

When needed, the Vive controllers can be configured as well. To do so:

* Open the configuration utility tool while SteamVR is running.&#x20;
* At the top of the configuration tool, it should indicate OpenVR status as _Initialized_ and the controllers must be showing up in SteamVR.&#x20;
* Then, in the controller sections, enable the controllers, specify the override device using the drop-down menu, and input the corresponding streaming ID of the controller Rigid Bodies in Motive.&#x20;
* Once everything has been configured, save the changes and restart SteamVR.&#x20;
* When the override is configured properly, SteamVR will have an additional tracker icon per each enabled controller.

<figure><img src="../../../.gitbook/assets/image (319).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (309).png" alt=""><figcaption></figcaption></figure>

## Data Streaming

Now that the driver is set up, the HMD tracking will be overridden by tracking data from the mocap camera system, and you can integrate HMDs into the game engine through their own VR integration.

### Streaming settings in Motive

![](<../../../.gitbook/assets/image (82) (1).png>)

First of all, make sure the streaming settings are configured in Motive for streaming out the data. For more information regarding streaming in Motive, please visit our [Streaming ](../../../motive-ui-panes/settings/settings-streaming.md)page:

* **Broadcast Frame Data** must be set to _true_.
* **Local interface** must be set to the desired IP address to stream the tracking data from.
* Streaming of **Rigid Bodies** must be set to True
* For wireless streaming, use **Unicast** streaming type.

### Notes for Unity users

Please make sure the Unity project is configured for OpenVR development. In Unity, open player settings from _Edit → Project Settings → Player_ and select the OpenVR under the Virtual Reality SDK lists. Once this is set up properly, it will play the scene on the HMD.

**Unity-OpenVR documenation:** [**https://docs.unity3d.com/Manual/VRDevices-OpenVR.html**](https://docs.unity3d.com/Manual/VRDevices-OpenVR.html)

### Unreal Engine

Make sure Unreal Engine is configured for SteamVR development. Please refer to the Unreal Engine's documentation for more information on developing for SteamVR.

**Unreal Engine-SteamVR:** [**https://docs.unrealengine.com/en-us/Platforms/SteamVR**](https://docs.unrealengine.com/en-us/Platforms/SteamVR)

### Data Port Note

As of the OpenVR Driver 2.1.0 the auto-detection port default is 1513. In the case where a firewall must configure individual ports to allow or disallow data, this port can be used to allow the OpenVR Driver to connect automatically to Motive.

## Streaming Rigid Body/Skeleton data

This driver is designed for streaming of HMD and controller tracking data only. For streaming tracking data of other Rigid Body objects, you will need to use the corresponding plugins ([UnrealEngine](https://github.com/OptiTrack/GitBook-Wiki/blob/main/virtual-reality/vr-plugins/vr-openvr/broken-reference/README.md) or [Unity](https://github.com/OptiTrack/GitBook-Wiki/blob/main/virtual-reality/vr-plugins/vr-openvr/broken-reference/README.md)). In other words, the HMD tracking data will be streamed through the SteamVR using the driver you've installed, and all other tracking data will be streamed through the plugin's client origin.

### Aligning world coordinates

**Client Origin**

When using both the VR driver and the plugins (UE/Unity), it is important that the client origin object is located at the origin without any rotations. In other words, it must have the position set to (0,0,0) and the rotation set to (0,0,0).

**Notes for Unreal Engine Users**

When using the Unreal Engine plugin, you will need to additionally create a custom pawn for properly aligning the coordinate systems between SteamVR and OptiTrack UE plugin:

1. Create an "Optitrack Client Origin" to the scene and set the relevant connection info. Refer to the [OptiTrack Unreal Engine Plugin](../../../plugins/optitrack-unreal-engine-plugin/) page for more information on setting up the client origin.
2. Create a new pawn. Right-click in Content Browser, and from the context menu, select _Blueprint → Blueprint Class → Pawn_.
3. Load created Blueprint in the editor and add a camera component.
4. _(optional)_ Double-check that the “Lock to HMD” property is set to true under the camera component properties in the details pane.
5. Select the pawn and set the “Base Eye Height” property to 0 in the details pane.
6. Compile the pawn then add it to the scene.
7. Select the pawn and set the “Auto Possess Player” to “Player 0”.
8. The HMD should now be working for Levels built for VR.

![Configured properties of the custom pawn.](<../../../.gitbook/assets/image (1236).png>)

![Configured properties of the added camera component.](<../../../.gitbook/assets/image (1250).png>)
