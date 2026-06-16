---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/animation/autodesk-motionbuilder/autodesk-motionbuilder-optitrack-optical-plugin
---

# Autodesk MotionBuilder: OptiTrack Optical Plugin

## **Overview**

This page provides instructions on how to use the OptiTrack MotionBuilder Optical plugin. The OptiTrack Optical Plugin device allows to you to map motion capture (optical) data onto an animated character within MotionBuilder.

![MotionBuilder Character driven by motion capture data.](<../../.gitbook/assets/image (694).png>)

## Motive Data Streaming Setup (Server)

First, you'll want to follow the instructions below to set up the data streaming settings in Motive. Once this is configured, Motive will be broadcasting tracking data onto a designated network interface where client applications can receive them.

### Streaming Settings

![](<../../.gitbook/assets/image (141) (1) (1) (1) (4).png>)

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

![Asset Browser tab > Devices view of the plugins.](<../../.gitbook/assets/image (1267).png>)

![Navigator tab.](<../../.gitbook/assets/image (1290).png>)

### Device Settings

![OptiTrack MotionBuilder Skeleton Plugin settings.](<../../.gitbook/assets/image (1284).png>)

* **Optical Model**
  * Specified the MotionBuilder "Opticals" model to map the markers to.
* **Generate a new Optical model/Update the current optical model**
  * Adds/updates the current Marker Set from OptiTrack to list of MotionBuilder "Opticals" model.
* **Damping Time**
  * Device damping time.
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
* **OptiTrack Marker Set**
  * The name of the OptiTrack Marker Set this optical is binding to.
* **Marker Set Scale**
  * The global scale factor to be applied to the marker data before mapping to the actor.

Once the above settings are input appropriately, you'll want to click the box next to **Online**. This indicate whether or not Motive is successfully streaming to MotionBuilder.

* **Online** color indicator
  * Green - Connected and streaming.
  * Yellow - Connected but not streaming.
  * Red - Not connected or streaming.
* **Live**
  * Indicates to MotionBuilder that data is coming from a live source (checked) or from a recorded take.
* **Recording**
  * Indicates to MotionBuilder that data from this device should be recorded when MotionBuilder is recording.
* **Model Bindings**
  * Unused.
* **Device Information**
  * Information about the status of the connection.

## Step-By-Step Example

Motive Skeleton Streaming Step-by-step

| Step                                                                        | Details                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| --------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><strong>[Motive]</strong></p><p>Configure Motive for Streaming Data</p>  | <p>From the Motive Streaming Pane:</p><ul><li>Select <strong>Enable</strong></li><li>Select <strong>Bone Naming Convention</strong> to FBX. (The plugin device will automatically reconfigure this if not already set to FBX.)</li><li>Choose <strong>Local Interface</strong> IP address from dropdown. If same computer is running both OptiTrack and MotionBuilder use the <em>Loopback</em> option.</li></ul><p>Be sure to configure any Firewall software first (either disable or permit MotionBuilder as an exception).</p>                                                                                   |
| <p><strong>[MoBu]</strong></p><p>Create an OptiTrack Optical device</p>     | <p>In the MotionBuilder Asset Browser Window > Devices window. You should see:</p><p><strong>OptiTrack Optical</strong></p><ul><li>Within MotionBuilder, drag the OptiTrack Optical device into the <strong>Navigator</strong>(or <strong>Viewer</strong>) pane. An instance will be created under the <strong>Devices</strong> node.</li></ul>                                                                                                                                                                                                                                                                      |
| <p><strong>[MoBu]</strong></p><p>Connect Optical Device to Motive</p>       | <ul><li>In the Navigator window, select OptiTrack Optical from the Devices node</li><li>On the OptiTrack Optical pane, set the IP address of the OptiTrack server (e.g. Motive).</li><li>Click on the <strong>Online</strong> box - it should change from red to yellow (or green if data from the OptiTrack Server is currently streaming).</li></ul>                                                                                                                                                                                                                                                               |
| <p><strong>[MoBu]</strong></p><p>Create a Marker Set > Opticals Mapping</p> | <ul><li>In the 'OptiTrack Marker Set's Dropdown, select the name of a currently defined Marker Set in Motive. You may need to resize the device pane in MotionBuilder to access the features.</li><li>Press the <strong>Generate new optical model</strong> button</li><li>In the Navigator window, under the <strong>Opticals</strong> node, you should see a new the marker list. This indicates the plugin has successfully retrieved the marker list from the OptiTrack server. You should also see the Opticals displayed in the <strong>Viewer</strong> window if the Server is currently streaming.</li></ul> |
| <p><strong>[MoBu]</strong></p><p>Begin streaming marker data</p>            | <ul><li>From Motive, start live capture or data playback</li><li>From MotionBuilder, ensure the <strong>Viewer</strong> window is active (MotionBuilder will not update otherwise).</li><li>The marker set should be animating in the MotionBuilder <strong>Viewer</strong> window.</li><li>The MotionBuilder <strong>Online</strong> check boxes should be green, indicating data is live and actively streaming.</li></ul>                                                                                                                                                                                         |

## Recording Optical Data

The OptiTrack Optical device can record streamed optical data to the current MotionBuilder take. Note that the looping feature in Motive must be disabled in order to record streamed data in MotionBuilder. The following step-by-step procedure can be used to record data:

Recording Optical Data Step-by-step

| Step                                | Details                                                                                                                                                                               |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Enable Optical Device for recording | \[Mobu] > Optical > Check **Recording**                                                                                                                                               |
| Start Recording                     | <ul><li>[Mobu] > Transport Control > Record (Create new take)</li><li>[Mobu] > Transport Control > Play ( start recording frames)</li><li>[Mobu] > Transport Control > Stop</li></ul> |

## Playing Back Recorded Data

The OptiTrack Optical device can be used to show live data or blend live data with a recorded take. To playback recorded optical data, you need to tell MotionBuilder to disable live streaming.

Playing Back Recorded Data Step-by-step

| Step                   | Details                                                                                         |
| ---------------------- | ----------------------------------------------------------------------------------------------- |
| Disable Live streaming | <ul><li>[Mobu] > Optical > Uncheck Recording</li><li>[Mobu] > Optical > Uncheck Live</li></ul>  |
| Playback recorded take | <ul><li>[Mobu] > Transport Control > Rewind</li><li>[Mobu] > Transport Control > Play</li></ul> |

## Optical Data Namespace

When the opticals are generated, their naming conventions will be determined depending on whether the **Organize Assets** option was enabled under the Optical Device properties.

**Organize Assests Enabled (default)**

The device will generate optical data with colon ( : ) separator (e.g. AssetName:MarkerName), and all of the optical data will be organized under their corresponding root nodes.

**Organize Assets Disabled**

The device will generate optical data with an underscore ( \_ ) (e.g. AssetName\_MarkerName) and all of the optical data will be listed under a same optical node.

{% hint style="info" %}
For auto-mapping imported FBX actors to optical data, the **Organize Assets** setting must be disabled and underscore separators must be used.
{% endhint %}

![Organize Assets enabled.](<../../.gitbook/assets/image (1330).png>)

![Organize Assets disabled.](<../../.gitbook/assets/image (1283).png>)

## MotionBuilder Actor/Character Setup

The following guide is provided as a simplified process for working specifically with Motive, but this is not the only way. For the latest information on setting up and configuring MotionBuilder Actors and Characters, please refer to the [MotionBuilder documentation](https://knowledge.autodesk.com/support/motionbuilder/learn-explore/caas/simplecontent/content/autodesk-motionbuilder-documentation.html).

To animate characters in MotionBuilder, you need to create the following data flow (or “mapping”):

_**Mocap Marker Data > MotionBuilder “Actor” > Skeleton Data > MotionBuilder “Character”**_

The _**Mocap Marker Data > MotionBuilder Actor**_ step maps Motion Capture data (Markers) to the MotionBuilder Actor object. The MotionBuilder Actor object is a Skeleton solver that creates joint angles from Marker data.

The _**MotionBuilder “Actor” > Skeleton Data > MotionBuilder “Character”**_ step is specific to MotionBuilder, and this pipeline maps the MotionBuilder Actor Skeleton onto your final character Skeleton. This step requires a “rigged” character. Refer to the MotionBuilder help for detailed information on this process.

### Actor Setup (_**Mocap Marker Data > MotionBuilder "Actor"**_)

There are 3 ways to create a Motive Marker Set > MobBu Actor mapping.

1. Create a new marker map from scratch.
2. Import a Motive exported FBX Ascii file.
3. Auto-create an actor from the Motive stream.

{% hint style="danger" %}
Autodesk has discontinued support for FBX Ascii import in MoBu 2018 and above.
{% endhint %}

#### 1. Create a new marker map from scratch

1. Create OptiTrack Optical device
2. Connect to Motive
3. Generate Opticals
4. Stream a frame of T-Pose data from Motive
   * You should see the Opticals in the MotionBuilder 3D viewer
5. Create MB Actor
6. Fit MB Actor to Opticals
7. Create an Optical > Marker Set > Actor mapping:
   * Import existing mapping
     * Actor > Marker Set > Import > OptiTrack HIK file
     * Drag all opticals (incl root) onto Actor’s “Reference Cell”
   * Create a new mapping:
     * Actor > Marker Set > Create
     * Drag individual opticals to Actor segments
8. Activate Actor (Actor > Activate)
   * Actor snaps to marker cloud pose
   * Actor should now be animating in Viewer

#### 2. Import Existing Marker Map (from File)

**Option 1: Restore Marker Set from HIK file**

1. \[MoBu] Import Marker Set definition (.hik file)
2. \[MoBu] Connect to Motive
3. \[MoBu] Generate Opticals
4. \[Motive] Stream a T-Pose frame of data into MotionBuilder
5. \[MoBu] Actor Panel : Drag Opticals to Actor Markers (Actor Prop Sheet > Reference)
6. \[MoBu] Activate Actor (Actor > Activate)
   * Actor snaps to marker cloud pose
   * Actor should now be animating in Viewer

**Option 2. Export FBX from Motive (Mobu 2017 and earlier only)**

1. \[Motive] Right-click on the Skeletons in the Assets pane and export Skeleton as FBX. Make sure the namespace separator is set to (\_).
2. \[MoBu] Merge FBX from Step 1 (File > Merge)
3. \[MoBu] Connect to Motive
4. \[MoBu] Select the OptiTrack Optical device in the navigator and access its properties under the resources panel.
5. \[MoBu] Disable Organize Assets property to generate Opticals with underscore separators in its names.
6. \[MoBu] Generate Opticals.
7. \[Motive] Stream a T-Pose frame of data into MotionBuilder
8. \[MoBu] Actor Panel : Select all of the streamed Opticals and Drag them onto the Actor Markers (Actor Prop Sheet > Reference). The names under the marker name sheet **MUST** match the Skeleton labels for auto-mapping.
9. \[MoBu] Activate Actor (Actor > Activate)
   * Actor snaps to marker cloud pose
   * Actor should now be animating in Viewer

#### 3. Auto-Create from Stream

The Optitrack MotionBuilder plugin can generate a MoBU Actor for you automatically.

1. Set the “Create Actors” property to true before bringing the Optical device online.
2. The Optitrack Mobu plugin will generate an Actor for each Marker Set in the Motive data stream, and correctly map the Motive Marker Set markers to the corresponding Mobu Actor.

## Offline Workflow with Actor Binding

In order to workaround Autodesk's removal of support for FBX actor import, we recommend the following:

1. \[Motive] Load a TAK file with desired assets
2. \[Mobu] Use Optical Device to Create Actors over stream from TAK file.
3. \[Motive] Export TAK data from Motive (FBX or C3D)
4. \[Mobu] Import C3D/FBX into Mobu
5. \[Mobu] Update Actor binding to imported C3D / FBX

## Character Setup (MotionBuilder Actor > Character)

1. Do Actor Setup (Above)
2. Import a rigged Skeleton (File -> Merge -> Skeleton)
3. If Skeleton is not “characterized, characterize it:
4. Create MB Character (Drag onto Skeleton “hips” )
5. Map Character to Actor
   * Select Character -> Character Settings -> Input Type -> Actor Input
   * Check “Active”
6. Activate Actor (Actor -> Activate)
   * Skeleton and Actor should now be animating in Viewer

{% hint style="info" %}
For more information on setting up and configuring MotionBuilder Actors and Characters, please refer to Autodesk's [MotionBuilder documentation](https://knowledge.autodesk.com/support/motionbuilder/learn-explore/caas/simplecontent/content/autodesk-motionbuilder-documentation.html).
{% endhint %}

## Unlabled Markers

Unlabeled markers are not commonly needed in the MotionBuilder workflow, but if needed, they can get streamed through the Optical Device plugin.

1. \[Motive] Make sure streaming of unlabeled markers is enabled in Motive’s data streaming panel.
2. \[MoBu] Under the properties of the Optical Device loaded in the scene, make sure Using Unlabeled Markers option is enabled and the Unlabeled Marker Limit is set to the maximum number of unlabeled makers allowed in the scene.
3. \[MoBu] In Optical Devices, generate or update the optical model.
4. \[MoBu] Unlabeled markers will show up as orange opticals in the scene.

![Properties tab in MotionBuilder Using Unlabeled Markers.](<../../.gitbook/assets/image (1261).png>)

{% hint style="info" %}
The Optical Device has a special property for Arena Expression ( viewable from the MotionBuilder Properties tab) that must be checked when using with Arena Expression software:
{% endhint %}

![Arena Expression checked in Properties tab.](<../../.gitbook/assets/image (1350).png>)
