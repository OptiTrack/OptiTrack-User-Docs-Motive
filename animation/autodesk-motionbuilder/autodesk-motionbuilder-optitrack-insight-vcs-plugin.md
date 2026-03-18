# Autodesk MotionBuilder: OptiTrack Insight VCS Plugin

## **Overview**

This page provides instructions on how to use the OptiTrack MotionBuilder Virtual Camera Device (Insight VCS) plugin. The Virtual Camera device is specifically designed for creating a Virtual Camera in MotionBuilder. You can use the Insight VCS device with standard OptiTrack applications such as Motive, or you can use the device in "Universal" mode, which works with generic MotionBuilder Optical or RigidBody objects, allowing you to use the Insight VCS device with alternative motion capture systems that support optical or Rigid Body devices in MotionBuilder.

![Camera Tracking in MotionBuilder.](<../../.gitbook/assets/image (738).png>)

Before following the walkthrough below, please refer to [Autodesk MotionBuilder Plugin page](../../plugins/autodesk-motionbuilder/autodesk-motionbuilder-plugin.md) for initial steps for setting up motive and downloading the OptiTrack MotionBuilder plugin.

## Motive Data Streaming Setup (Server)

First, you'll want to follow the instructions below to set up the data streaming settings in Motive. Once this is configured, Motive will be broadcasting tracking data onto a designated network interface where client applications can receive them.

### Streaming Settings

![](<../../.gitbook/assets/image (141) (1) (1) (1) (1) (1) (1) (2).png>)

* **Enable** - Turn on the Enable setting at the top of the NatNet section.
* **Local Interface** - Choose the desired IP network address from this dropdown to stream data over.
  * **Loopback**
    * This is the local computer IP address (127.0.0.1 or Localhost).
    * Used for streaming data locally on the PC you are running Motive on that does not interact with the LAN.
    * Good option for testing network issues.
  * **192.168.0.1x** (typical, but may be different depending on which interface is used to establish a LAN connection)
    * This IP address is the interface of the LAN either by Wi-Fi or Ethernet.
    * This will be the same address the Client application will use to connect to Motive.
* **Transmission Type**
  * For streaming over a Wi-Fi network, setting the **Transmission Type** to _Unicast_ is strongly advised.
* Select desired data types to stream under streaming options:
  * **Rigid Bodies** - Enabled (required).
  * **Skeletons** - Optional for Skeleton tracking.
  * **Markers (Labeled, Unlabled, Asset)** - Disabled for HMDs (advised).
  * **Devices** - Disabled.
* **Skeleton Coordinates**
  * Set to _Local_.
* **Bone Naming Convention**
  * When streaming Skeletons, set to FBX.

{% hint style="info" %}
**Additional Tips**

* For best results, it is advised to run Motive and MotionBuilder separately on different computers, so that they are not competing for processing resources.
* When streaming the data over a Wi-Fi network, _Unicast_ transmission must be used.
* In order to stream data from the Edit mode, a capture-recording must be playing back in Motive.
* For additional information on data streaming in general, read through the [Data Streaming](../../motive/data-streaming.md) page.
{% endhint %}

## MotionBuilder Setup (Client)

To get started, drag the OptiTrack Optical plugin from the Motion Builder Asset Browser tab > Devices into the Viewer window. This will create a dropdown menu called **I/O Devices** in the **Navigator** tab. Click the **+** button next to **I/O Devices** and select _OptiTrack Optical_. This will populate the plugin's settings tab if it hasn't already auto-populated from the drag and drop step from earlier.

![Asset Browser tab > Devices view of the plugins.](<../../.gitbook/assets/image (644).png>)

![Navigator tab.](<../../.gitbook/assets/image (682).png>)

### Device Settings

![OptiTrack MotionBuilder Skeleton Plugin settings.](<../../.gitbook/assets/image (731).png>)

* **Local address** - IP address of the MotionBuilder computer. In situations where multiple network adapter cards are present, select the adapter that is on the same network as the Motive application.
  * 127.0.0.1
    * This is the local computer IP address (127.0.0.1 or Localhost).
    * Use this loopback address if Motive is running on the same machine as MotionBuilder.
  * 192.168.0.1x (typical, but may be different depending on which interface is used to establish a LAN connection)
    * This IP address is the interface of the LAN either by Wi-Fi or Ethernet.
    * Use this if Motive is running on a different computer, but on the same network as the MotionBuilder computer.
  * 169.xxx.x.xx
    * This address is assigned when a DHCP server could not be reached.
    * This address can be ignored for our application.
* **Server Address** - IP address of computer that is running Motive
  * 127.0.0.1
    * Use this IP when both Motive and MotionBuilder are running on the same computer.
* **Server Type**
  * Multicast (default) or Unicast
  * Must match what is selected in the Motive Streaming settings.
  * Multicast is default and _recommended_.

Once the above settings are input appropriately, you'll want to click the box next to **Online**. This indicate whether or not Motive is successfully streaming to MotionBuilder.

* **Online** color indicator
  * Green - Connected and streaming.
  * Yellow - Connected but not streaming.
  * Red - Not connected or streaming.
* **Live**
  * Indicates to MotionBuilder that data is coming from a live source (checked) or from a recorded take.
* **Recording**
  * Indicates to MotionBuilder that data from this device should be recorded when MotionBuilder is recording.
* **Model Binding**
  * Indicates the MotionBuilder Camera to be controlled by the tracking controller.
* **Device Information**
  * Information about the status of the connection.
* **OptiTrack Connection**
  * Indicates the data source is an OptiTrack server application.
* **Universal Connection**
  * Indicates the data source is a generic MotionBuilder RigidBody.
* **Rigid Body ID**
  * \[OptiTrack Connection] Name of the OptiTrack server application’s Rigid Body to use for tracking.
* **Rigid Body**
  * \[Universal Connection] Name of the MotionBuilder RigidBody to use as a position/orientation source.

## Insight VCS Features

| Feature             | Description                                                                                                                                                         |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Pan/Dolly/Boom**  | Use VCS controls to Pan Left/Right and Up/Down. Pan in local, world, or a combination of coordinate systems. Adjust pan speeds on the fly with controls or scripts. |
| **Pitch/Tilt/Roll** | Absolute orientation at all times from the OptiTrack optical system.                                                                                                |
| **Free Move**       | Absolute position at all times from the OptiTrack optical system. Scale movement in real-time with controllers or from script.                                      |
| **Zoom**            | Fully control camera zoom/FOV and zoom rates using the controller's analog thumbsticks and speed adjusters.                                                         |
| **Smooth**          | Advanced Kalman filtering allows for customizing a "Steadicam" feeling.                                                                                             |
| **Play/Record**     | Control common actions like recording and playback using the controller.                                                                                            |
| **Custom Commands** | Customize the controller by mapping controller inputs to execute scripts for complete control and one-person camera operation.                                      |

{% hint style="info" %}
The Virtual Camera also integrates into existing MotionBuilder camera control workflows, including spline/path/constraint animation and custom scripted behaviors.
{% endhint %}

## Creating a Virtual Camera Device (OptiTrack Server)

First you'll need to create the "neutral" or "zero" orientation of a Rigid Body

The “neutral” or “zero” orientation of a Rigid Body is the orientation when it is created in Motive. This will be the camera’s neutral orientation. In addition, for correct interpretation into MotionBuilder’s coordinate system, it is important you align your Rigid Body with the correct axis and coordinate system convention as follows:

* Point your tracking controller (e.g. VCS Pro) along physical volume -Z axis.

![Controller orientation with CS-400 ground plane. Any ground plane can be used, but just make sure it oriented correctly along the physical -Z axis (longest side of ground plane).](<../../.gitbook/assets/image (156).png>)

### Step-By-Step

After correctly orienting your Rigid Body follow the steps below to continue with the setup:

1. \[Motive] Create a Rigid Body from your tracking controller’s markers.
2. \[OptiTrack Server App] Enable network streaming (make sure Rigid Body data is streaming).
3. \[MotionBuilder] Drag the OptiTrack Insight VCS device from the Motion Builder Asset Browser Panel into the Viewer or Navigator window.
4. \[Insight VCS Panel] Connect to an OptiTrack Server (e.g. Motive, Arena, TrackingTools) by clicking the “Online” checkbox. If the connection was successful and data is streaming from you OptiTrack server application, this box will change from Red to Green.
5. \[Insight VCS Panel] Create a new MotionBuilder camera using the Model Binding dropdown.
6. \[Insight VCS Panel] \[Optional] If tracking more than one Rigid Body object in your OptiTrack server application, select the Rigid Body you wish to use as your tracking source using the Rigid Body ID dropdown on the CameraTracker device panel (Note: the camera tracker will automatically default to the first detected Rigid Body).

You should now see a standard MotionBuilder Camera moving within your 3D scene:

![Camera in 3D scene.](<../../.gitbook/assets/image (721).png>)

## Creating a Virtual Camera Device (Universal Mode)

In Universal mode, a MotionBuilder Rigid Body is used to drive a camera position. This position/orientation information is merged with the VCS camera controls and applied to the camera's final state (position, lens settings, etc.). It is assumed the Rigid Body orientation matches the MotionBuilder default camera orientation (camera lens aimed down +X axis). For example, if streaming from Motive, create a Rigid Body in MotionBuilder from the optical data, with the camera lens aimed down +X in MotionBuilder.

### Step-By-Step

1. \[MotionBuilder] Create a Rigid Body or a Marker. For a Marker:
   * Create a bone (or some rigid element) from the geometry your 6DOF system streams into MotionBuilder
   * Create a MotionBuilder "Marker" element, and make this new marker a child of the bone
   * This new “Marker” marker should now have the same 6DOF value as the bone
   * . Use this “Marker” in the VCS universal dropdown to drive the 6DOF data of the VCS.
2. \[Insight VCS Panel] Check the "Universal Connection" Radio.
3. \[Insight VCS Panel] Check "Online".
4. \[Insight VCS Panel] Create a new MotionBuilder camera binding using the Model Binding dropdown.
5. \[Insight VCS Panel] Select the Rigid Body you created in step 1 using the Rigid Body dropdown in the Universal Connection group box.

{% hint style="info" %}
**Limitations**

* The following VCS features/properties are unavailable when operating in Universal Mode:
* Scale Rotation
* Offset Rotation
{% endhint %}

## Controllers

The Insight VCS plugin supports any DirectInput compatible joystick or USB device. Controllers can then be configured to perform actions or control the camera using **Controller Profiles**.

### Controller Profiles

Virtual Camera controls are managed by a Control-to-Event mapping system called the Controller Profile. The controller profile is configured in the Controller Tab. The Insight VCS plugin allows you to create and swap between multiple controller profiles, allowing you to create any number of custom button/axis configurations depending upon the scene, particular move types, different physical VCS controllers or HID devices, etc. Profiles can be saved and then later swapped out using the Profile Dropdown. Profiles are saved into \<VCS Mobu install folder>\Profiles folder.

The VCS plugin ships with 2 default profiles:

* The 2 controller VCS Pro (\<VCS Mobu install folder>\Profiles\VCSProDefault.xml).
* The XBox based VCS Mini (\<VCS Mobu install folder>\Profiles\VCSMiniDefault.xml).

When the Insight VCS plugin is first launched, it will attempt to detect any compatible controllers. It will then attempt to match the detected controllers with an existing **Controller Profile**, beginning with the last used ("preferred") profile.

### Profile Setup

The VCS plugin supports 2 types of controller inputs and 2 types of actions:

**Axis Inputs / Actions**

* Axis inputs are analog inputs and represent the range of values. This range has been scaled to \[0, 1000]. Axis inputs can be assigned to Axis actions. PTZ operations (Pan, Tilt, Zoom) are good examples of typical Axis Actions.

**Button Inputs / Actions**

* Button inputs are the button inputs on the controller. These are “one shot” events that occur when the button is pressed. Transport commands such as Play, Record, and Rewind are typical examples of “one shot” events.

{% hint style="info" %}
Some Insight VCS controllers have a dial that is represented in the Axis list as a "Wheel". This is a special form of an axis, and can be used to modify existing actions, such as zoom speed, pan speed, and motion scale amount.
{% endhint %}

### Typical Insight VCS Controller Map

![Insight VCS Controller Map tab.](<../../.gitbook/assets/image (671).png>)

Insight VCS Inputs/Action Settings

| **Axes**   | Name of the controller’s analog input.                                                                     |
| ---------- | ---------------------------------------------------------------------------------------------------------- |
| **Action** | Action to take or value to change.                                                                         |
| **Param**  | Input parameter used by some actions to modify the action in some way (e.g. speed up or slowdown zooming). |
| **Value**  | Current value of the control input.                                                                        |

### Action Parameters

Some actions have parameters that modify the way they operate. The following tables list the axis and button actions, and how the parameter value for that action is interpreted.

VCS Controller - Axis Actions

| Action                  | Parameter(s)                                                                                                                                                                              | Example                                                                                                                                                                                                                                                                                              |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| _**Pan Right/Left**_    | \[Pan Speed] \[Curve Type]                                                                                                                                                                | <ul><li><strong>1.0</strong> [ pan at normal rate, linear curve]</li><li><strong>1.0 1</strong> [ pan at normal rate, ease-in curve]</li><li><strong>0.5 1</strong> [ pan at half speed, ease-in curve]</li><li><strong>2.0</strong> [ pan at 2x speed ]</li></ul>                                   |
| _**Dolly In/Out**_      | \[Pan Speed] \[Curve Type]                                                                                                                                                                | 1.0                                                                                                                                                                                                                                                                                                  |
| _**Pan Up/Down**_       | \[Pan Speed] \[Curve Type]                                                                                                                                                                | 1.0                                                                                                                                                                                                                                                                                                  |
| _**Focal Length +/-**_  | \[Focal length change rate] \[Curve Type]                                                                                                                                                 | 1.0                                                                                                                                                                                                                                                                                                  |
| _**Orbit Offset**_      | \[Orbit offset change rate] \[Curve Type]                                                                                                                                                 | 1.0                                                                                                                                                                                                                                                                                                  |
| _**Focal Distance**_    | \[Focal distance change rate] \[Curve Type]                                                                                                                                               | 1.0                                                                                                                                                                                                                                                                                                  |
| _**Wheel Modifier**_    | <p>[VCS Dial controls only] Modify an axis' parameter value (e.g. zoom speed, pan speed, translation scale) by a specified increment.Format:</p><ul><li>[axis name] [increment]</li></ul> | <p>Examples:</p><ul><li>X Axis .1 (+/- the X Axis parameter by 0.1)</li><li>Y Axis .2 (+/- the Y Axis parameter by 0.2)</li><li>Z Axis .1 (+/- the Z Axis parameter by 0.1)</li><li>Scale All .5 (+/- all translational scale by .5)</li><li>Translate All 1.0 (+/- all pan speeds by 1.0)</li></ul> |
| _**Rotate Right/Left**_ | \[Rotate Speed] \[Curve Type]                                                                                                                                                             | <ul><li>1.0 [ rotate at normal rate, linear curve]</li><li>1.0 1 [rotate at normal rate, ease-in curve]</li><li>0.5 1 [rotate at half speed, ease-in curve]</li><li>2.0 [rotate at 2x speed ]</li></ul>                                                                                              |
| _**Rotate Up/Down**_    | \[Rotate Speed] \[Curve Type]                                                                                                                                                             | **SAME AS ABOVE**                                                                                                                                                                                                                                                                                    |
| _**Tilt Right/Left**_   | \[Rotate Speed] \[Curve Type]                                                                                                                                                             | **SAME AS ABOVE**                                                                                                                                                                                                                                                                                    |

### Curve Types

When mapping a controller thumbstick axis to an animatable camera parameter (pan, zoom), you have the option of specifying how the Insight VCS plugin should interpret controller axis movement as a standard animation curve. Instead of modifying the value over time, however, the motion curve modifies the value over the controller span, from neutral/center position (0) to maximum position (Max). The following diagram describes this relationship:

![VCS Plugin built-in curve options.](<../../.gitbook/assets/image (717).png>)

### Button Actions

VCS Controller - Button Actions

| Action                      | Parameter                                                                                                                                                                                                                                                                                                                                                                                                     | Example                                         |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| _**Record**_                | Copy data from previous take.                                                                                                                                                                                                                                                                                                                                                                                 | true                                            |
| _**Play**_                  | None.                                                                                                                                                                                                                                                                                                                                                                                                         |                                                 |
| _**Fullscreen**_            | Toggles between Fullscreen and the MotionBuilder GUI. On return to the MotionBuilder GUI, this parameter indicates the number of viewports to show.                                                                                                                                                                                                                                                           | 2                                               |
| _**RunScript**_             | Runs a MotionBuilder python script. This script must be located in your MotionBuilder scripts root folder.                                                                                                                                                                                                                                                                                                    | ResetOffset.py                                  |
| _**ToggleAxisAction**_      | <ul><li>Toggles a specified axis between 2 actions.</li><li>[Axis name],[Action1 Index], [Action1 Params],[Action2 Index],[Action2 Params]</li><li>The example at right toggles the Y Axis behavior between Dolly In/Out at speed 1.0 with a Cubic Curve and Focal Length at 0.1 speed with a Quartic curve.</li><li>This action can be used to extend axis functionalitywithout swapping profiles.</li></ul> | Y Axis, 3, 1.0 1, 4, 0.1 2                      |
| _**Pause**_                 | None.                                                                                                                                                                                                                                                                                                                                                                                                         |                                                 |
| _**Stop**_                  | None.                                                                                                                                                                                                                                                                                                                                                                                                         |                                                 |
| _**Rewind**_                | None.                                                                                                                                                                                                                                                                                                                                                                                                         |                                                 |
| _**Suspend Tracking**_      | None.                                                                                                                                                                                                                                                                                                                                                                                                         |                                                 |
| _**Scale Translation +/-**_ | Increment amount.                                                                                                                                                                                                                                                                                                                                                                                             | .5                                              |
| _**Scale Rotation +/-**_    | Increment amount.                                                                                                                                                                                                                                                                                                                                                                                             | .5                                              |
| _**Zoom +/-**_              | Increment amount.                                                                                                                                                                                                                                                                                                                                                                                             | .5                                              |
| _**FOV +/-**_               | Increment amount.                                                                                                                                                                                                                                                                                                                                                                                             | .5                                              |
| _**Playback Speed +/-**_    | Enumerated value that matches MoBu transport.                                                                                                                                                                                                                                                                                                                                                                 | 2                                               |
| _**Reset Zoom**_            | Focal Length to reset to.                                                                                                                                                                                                                                                                                                                                                                                     | 50.0                                            |
| _**Reset Offset**_          | \[x y z] Optional - specifies the position to reset camera to, otherwise camera is reset to (0.0,0.0,0.0).                                                                                                                                                                                                                                                                                                    | 10.0 10.0 0.0 \[reset camera offset to 10,10,0] |
| _**Reset Rotation Offset**_ | \[x y z] Optional - specifies the rotation vector to reset to (in degrees), otherwise camera is reset to (0.0,0.0,0.0).                                                                                                                                                                                                                                                                                       | 0.0 90.0 0.0 ( reset camera to 90 degrees yaw)  |
| _**Reset Orbit Offset**_    | None.                                                                                                                                                                                                                                                                                                                                                                                                         |                                                 |
| _**Change Camera**_         | None.                                                                                                                                                                                                                                                                                                                                                                                                         |                                                 |
| _**Play Last Take**_        | None.                                                                                                                                                                                                                                                                                                                                                                                                         |                                                 |
| _**Reset to Live**_         | None.                                                                                                                                                                                                                                                                                                                                                                                                         |                                                 |

### Run Script Usage

When using the Run Script action to map button presses to MotionBuilder scripts, be sure to note the following:

1. Scripts must be placed in the MotionBuilder scripts folder in order to be correctly located. For a typical MotionBuilder installation this folder is:
   * C:\Program Files\Autodesk\MotionBuilder 2014\bin\config\Scripts:
2. The RunScript Param is the filename of the script, including the .py extension:

![](<../../.gitbook/assets/image (736).png>)

![](<../../.gitbook/assets/image (137).png>)

## Virtual Camera Device Settings

The Insight VCS plugin has several properties that can be used to customize its behavior. These properties can be accessed in the same manner as any other MotionBuilder object property, such as from the Asset Browser or from MotionBuilder's Python scripting environment.

![Insight VCS Properties.](<../../.gitbook/assets/image (653).png>)

| Action                          | Parameter                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| _**Scale Translation**_         | Scale the physical movement (when tracking controller is moved).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| _**Scale Rotation**_            | Scale the physical movement (when tracking controller is moved).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| _**Offset Translation**_        | <p>Can be used for 2 purposes :</p><ol><li>To adjust the center of the physical volume to the virtual scene.</li><li>To effectively pan/truck/dolly the camera. This value is updated by the thumbstick controls for the Pan/dolly/truck operations</li></ol>                                                                                                                                                                                                                                                                                             |
| _**OffsetTranslationMode**_     | <p>Affects how Offset Translation is applied to the camera:</p><ul><li>0 : <strong>Global</strong> Translates the camera according to the MotionBuilder global coordinate system (global)</li><li>1 : <strong>Local</strong> Translates the camera according to the camera’s coordinate system (local).</li><li>2 : <strong>LocalOnStart</strong> Translates the camera according to the camera’s coordinate system when the camera first moves (stick first moves), then keeps that axis (Does not continuously update the coordinate system).</li></ul> |
| _**Boom Global Always**_        | Always pan camera up/down in the global Y axis, regardless of the **OffsetTranslationMode**                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| _**Scale Updates Offset**_      | Instructs whether changes to Scale Translation update the Offset Translation value in order to keep the camera in the same position (true) or does not affect Offset Translation, resulting in camera position moving to new scaled amount.                                                                                                                                                                                                                                                                                                               |
| _**Smooth Translation Amount**_ | Applies smoothing to the camera position values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| _**Smooth Rotation Amount**_    | Applies smoothing to the camera rotation values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| _**Dead Zone**_                 | Controller thumbsticks do not typically restore to an exact center value. Dead Zone can be used to specify a value range around thumbstick center that should be ignored. This can be used, for example, to prevent drift in pan/dolly/zoom when thumbsticks are mapped to these actions.                                                                                                                                                                                                                                                                 |

## MotionBuilder Camera Settings

A MotionBuilder Camera controls how you see the 3D scene. MotionBuilder’s Camera object allow users the ability to model realworld cameras, including settings such as Focal length, aspect ratio, film format, etc.

Refer to the [MotionBuilder documentation](https://knowledge.autodesk.com/support/motionbuilder/learn-explore/caas/simplecontent/content/autodesk-motionbuilder-documentation.html) for more information on Camera Settings.
