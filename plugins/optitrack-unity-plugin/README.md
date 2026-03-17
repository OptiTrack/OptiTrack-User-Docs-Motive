# OptiTrack Unity Plugin

## **Overview**



The [OptiTrack Unity3D Plugin](http://optitrack.com/downloads/plugins.html) allows you to stream real-time Rigid Body, Skeleton, and HMD tracking data from Motive into Unity. Using the streamed data, objects and characters in the scene can be animated. The plugin contents are distributed in _unitypackage_ format, and you can simply load this file into Unity projects to import its contents. Once imported, included C# scripts can be used for instantiating a client origin and receiving the tracking data. This article focuses on how to set up and use the plugin.

### **Versions Requirements**

* Unity 2022 LTS through Unity 6 LTS
* Visual Studio 2019 or latest Visual C++ Redistributable

![Streaming tracking data into Unity.](<../../.gitbook/assets/image (1224).png>)

{% hint style="info" %}
**Notes on HMD Integration**

* The HTC VIVE, VIVE Pro, VIVE Pro 2, Valve Index, and HP Reverb HMDs can be integrated through the [OptiTrack OpenVR Driver](../optitrack-openvr-driver.md).
* To download the driver, visit the [Plug-ins section](https://optitrack.com/support/downloads/plugins.html) of the OptiTrack [Downloads](https://optitrack.com/support/downloads/) page.&#x20;
{% endhint %}

## Motive Setup (Server)

### Streaming Setup

![Data Streaming settings in Motive.](<../../.gitbook/assets/Settings - Streaming for Unity Plugin.png>)

From Motive, tracking data can be streamed in real-time, either from a live capture (Live Mode) or recorded data (Edit Mode). Settings are configured in [Application Settings](../../motive-ui-panes/settings/), on the [Streaming Settings](../../motive-ui-panes/settings/settings-streaming.md) tab.&#x20;

**Streaming in Motive**

Click the <img src="../../.gitbook/assets/Control Deck - Streaming Off SMALL (1).png" alt="" data-size="line"> button in the lower right corner of the Control Deck to open the [Streaming Settings](../../motive-ui-panes/settings/settings-streaming.md).  Configure the settings below:

* **Enable** - Turn on the Enable setting at the top of the NatNet section.
* **Local Interface** - Choose the desired IP network address from this dropdown to stream data over.
* **Transmission Type**&#x20;
  * **Unicast** subscribes only to the data selected and normally uses less network bandwidth. Use this method when only streaming Rigid Bodies and/or Skeleton&#x73;_._ This is especially advised if streaming data over WiFi.
  * Multicast transmission is required when streaming Trained Markersets. This method requires more bandwidth, therefore we recommend enabling only the desired data types. For example, When tracking HMDs, we recommend disabling _Marker_ streaming.

{% hint style="info" %}
**Additional Streaming Tips**

* To stream data from Edit mode, a capture recording must be playing back in Motive.
* We recommend running Motive and Unity on different computers, so the applications are not competing for processing resources.
* When streaming the data over a WiFi network, _Unicast_ transmission must be used.
{% endhint %}

## Unity Setup (Client)

![Unity plugin files.](<../../.gitbook/assets/image (1180).png>)

### Import Plugin Package

While in the Unity project, double-click on the plugin _unitypackage_ file and import the plugin assets into the project. When the package has been successfully imported, the following contents will be available within the project:

Plugin Contents

| Folder                   | Content Description                                                                                                                                                  |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Assets/OptiTrack         | All of the Unity plugin contents are included in this folder.                                                                                                        |
| Assets/OptiTrack/Scripts | This is the folder that you will mainly use. It contains plugin C# script components that can be imported into Unity objects for receiving streamed data.            |
| Assets/OptiTrack/Plugins | This folder contains the plugin libraries and header files.                                                                                                          |
| Assets/OptiTrack/Prefabs | This is the easiest place to get started. This folder contains premade objects for setting up a streaming client, tracking a Rigid Body, and retargeting a Skeleton. |
| Assets/OptiTrack/Scenes  | This folder contains sample Unity scene that includes pre-configured client, Rigid Body, and Skeleton objects.                                                       |

### Setting Up the Client Object

In order to receive tracking data from a server application (e.g. Motive), a client object must be set up. The _OptitrackStreamingClient.cs_ script can be attached to any object to stream data relative to that object. Typically, this script is attached to an empty object or loaded in using the "Client - OptiTrack" prefab object in the `Assets/Optitrack/Prefabs` folder.

* **\[Motive]** In the [Streaming Settings](../../motive-ui-panes/settings/settings-streaming.md), configure the desired connection settings.
* **\[Unity]** Under the Prefabs folder, import the "Client - OptiTrack" prefab object into the scene, or attach _OptitrackStreamingClient.cs_ script onto an empty object.
* **\[Unity]** In the streaming Client object, configure the connection settings to match the streaming settings in Motive.
* **Server Address** - IP address of the PC that the server application (Motive) is running on.
* **Local Address** - Local IP Address of the PC that the client application (Unity) is running on. (Typically, this looks similar to the Server Address except maybe the last digits.)
* **Connection Type** - Must match Motive. Unicast is recommended.
* **\[Unity]** If you wish to receive tracking data from more than one server instances, you may create multiple objects with the client script attached.

![Client object in Unity and the corresponding Motive data streaming network settings. Click image to enlarge.](<../../.gitbook/assets/image (1320).png>)

{% hint style="info" %}
**Position Data in Unity**

Although it is not strictly necessary, you may find it helpful to organize your tracked objects as children of the streaming Client object. This will allow you to adjust the position of the Client object to adjust the position of all streamed objects relative to the Client object.
{% endhint %}

![Position data in unity. Click image to enlarge.](<../../.gitbook/assets/image (182).png>)

### Animating a Rigid Body

1. **\[Unity]** On an object that you wish to animate, attach the _OpitrackRigidBody.cs_ script.
2. **\[Unity]** In the **Streaming Client** entry, link the Client object in which the _OptitrackStreamingClient.cs_ script is attached. By default, it searches for an existing client instance, but this must be specified when there are more than one streaming client objects.
3. **\[Unity]** For the **Rigid Body ID** entry, input the streaming ID of corresponding Rigid Body asset in Motive. The streaming ID can be found, and changed, under the [Rigid Body properties](/broken/pages/sQK8scBDhFagaBZY6IVS).
4. **\[Motive]** Make sure Motive is tracking and streaming the data.
5. **\[Unity]** Play the scene. The linked object will be animated according to the associated Rigid Body movement in Motive.

![OptiTrack Rigid Body configuration along with the Rigid Body properties in Motive. Configured Streaming ID must match the Rigid Body ID designated from the client side. Click image to enlarge.](<../../.gitbook/assets/image (1302).png>)

### Animating a Skeleton

By integrating with Unity's animation system, [Mecanim](https://docs.unity3d.com/Manual/AnimationOverview.html), the Unity3D plugin allows Motive to stream full body Skeleton data. The Skeleton tracking data from Motive is streamed out as hierarchical bone segment orientations, and this data is fed into the Unity's Mecanim system which allows animating characters with different proportions.

{% hint style="danger" %}
**Note:** At the time of writing, Mecanim does not support explicit goals for inverse kinematics end-effectors when using real-time retargeting. In addition, you may observe a difference in the overall scale of the position data between the retargeted skeletal animations and streamed Rigid Bodies. These two limitations may lead to inconsistencies with actors interacting with Rigid Body props, and will hopefully be addressed in a future version of the integration.
{% endhint %}

#### **Steps**

1. **\[Unity]** On Unity characters, attach _OptitrackSkeletonAnimator.cs_ script as one of its components.
2. **\[Unity]** For the **Streaming Client** entry, link the Client object in which the _OptitrackStreamingClient.cs_ script is attached. By default, it searches for an existing client instance, but this must be specified when there are more than one streaming client objects.
3. **\[Unity]** Enter **Skeleton Asset Name** which is assigned in Motive
4. **\[Unity]** For the **Destination Avatar** entry, link to the character's avatar component.
5. **\[Motive]** Make sure Motive is tracking and streaming the data.
6. **\[Unity]** Play the scene. When everything is set up properly, the linked avatar in Unity will be animated according to the streamed Skeleton in Motive. The position of the actor will be in its _reference position_ as explained above.

![OptiTrack Skeleton Animator script configuration from a character in Unity.](<../../.gitbook/assets/image (1308).png>)

### Animating a Trained Markerset

1. **\[Motive]** Export the asset using the FBX Binary format, with the following settings:

* **Export Skeletons** is Enabled
* **Bone Naming Convention** is set to FBX
* **Markerset Nulls** is Enabled
* **Skeletal Mesh** is Enabled
* **Remove Bone Naming Prefix** is Enabled

{% hint style="info" %}
Make note of the asset name in Motive to ensure the same name is used for the asset after it's imported into Unity.
{% endhint %}

<figure><img src="../../.gitbook/assets/Data Export for Unity Plugin.png" alt="" width="563"><figcaption><p>Settings to export a Trained Markerset asset for use in Unity.</p></figcaption></figure>

2. **\[Motive]** On the Streaming tab of the Settings panel, set the following properties:

* **Transmission type** is set to Multicast
* **Skeleton Coordinates** is set to Local

{% hint style="info" %}
Trained Markersets have their own bone naming convention and are not affected by the _Bone Naming Convention_ setting on the Streaming tab.&#x20;
{% endhint %}

3. **\[Unity]** Select Assets in the Project tab then right-click in the Assets pane and select _Import New Asset..._ from the context menu. Import the Asset exported in step 1.&#x20;

<figure><img src="../../.gitbook/assets/Unity - Import Asset CROPPED.png" alt=""><figcaption><p>Import an Asset into Unity.</p></figcaption></figure>

4. **\[Unity]** Drag the newly imported asset into the scene. In the _Hierarchy_ tab, drag the asset to nest under the _Origin_ for the Scene.&#x20;

<figure><img src="../../.gitbook/assets/Unity - TM in scene under origin CROPPED.png" alt=""><figcaption><p>Imported Trained Markerset nested under the Origin.</p></figcaption></figure>

5. **\[Unity]** Select the imported asset from the Hierarchy tab. In the _Transform_ section of the _Inspector_ tab, zero out the position and rotation values to place the asset at the local origin. &#x20;

<figure><img src="../../.gitbook/assets/Unity - TM Zero Transform to origin CROPPED.png" alt=""><figcaption><p>Inspector Tab. </p></figcaption></figure>

6. **\[Unity]** Select the origin from the _Hierarchy_ tab. The OptiTrack Streaming Client (Script) section will appear in the _Inspector_ tab. Ensure the following properties are set:

<figure><img src="../../.gitbook/assets/Unity - TM Streaming Client Script settings CROPPED.png" alt=""><figcaption><p>OptiTrack Streaming Client (script) settings for Trained Markersets </p></figcaption></figure>

* **Server Address** is set to the IP address for the Motive PC. Use 127.0.0.1 for loopback transmission.
* **Local Address** is set to the IP address for the Unity PC. Use 127.0.0.1 for loopback transmission.
* **Connection type** is Multicast.&#x20;
* **Skeleton** **and T Markerset Coordinates** are both set to Local.
* **Bone Naming Convention** is set to FBX by default. This setting does not apply to trained markerset assets.&#x20;
* **Draw T Markerset Markers** is checked (enabled). &#x20;

{% hint style="warning" %}
Trained Markerset will not stream into Unity in unicast or using global coordinates. &#x20;
{% endhint %}

7. **\[Motive]** Ensure that NatNet streaming is enabled.&#x20;
8. **\[Unity]** With the asset selected in the _Hierarchy_ tab, click the _Add Component_ button in the _Inspector_ tab. Search for OptiTrack, then select _OptiTrack Trained Markerset_ from the list of available options.&#x20;

<figure><img src="../../.gitbook/assets/Unity - TM Add Component part 2 CROPPED.png" alt="" width="316"><figcaption><p>Add Component in Unity.</p></figcaption></figure>

9. **\[Unity]** In the _T Markerset Asset Name_ field, rename the imported asset to match the name in Motive.&#x20;

<figure><img src="../../.gitbook/assets/Unity - TM Rename Asset to match Motive FINAL.png" alt=""><figcaption><p>Trained Markerset Asset Name in Unity.</p></figcaption></figure>

{% hint style="info" %}
Unity does not include a simple method for retargeting trained markersets. Many Unity users perform retargeting functions using third-party applications.  &#x20;
{% endhint %}

### Animating Markers, Etc.

1. **\[Unity]** On the OptiTrack Streaming instance, enable the _Draw Markers_, "Draw Cameras", or "Draw Force Plates" setting(s).
2. **\[Motive]** Make sure that marker streaming is enabled in Motive if you wish to visualize markers.
3. **\[Unity]** Make sure the streaming setting is set up correctly, and play the scene.
4. **\[Unity]** Each marker, camera, or force plate will be drawn in the scene, as shown in the screenshot below. (Note: Only markers will animate.)\\

![Skeleton labeled markers drawn in Unity scene.](<../../.gitbook/assets/image (1270).png>)

## Integrating HMDs

***

OptiTrack motion capture systems can be used to track head mounted displays (HMD) and integrate the tracking data into Unity for unique VR applications. For instructions on integrating HMD tracking data into Unreal Engine, please refer to the corresponding page [Unity: HMD Setup](unity-hmd-setup.md).

{% hint style="info" %}
**Supported HMDs**

At the time of writing, the following HMDs are supported:

* HTC VIVE
* HTC VIVE Pro
* HTC VIVE Pro 2
* Valve Index
* HP Reverb
{% endhint %}

## Wireless Multiplayer Setup

When setting up multiplayer games with wireless clients, it is more beneficial for each client to make direct connection to both the tracking-server (Motive) and the game-server, rather than rebroadcasting the streamed tracking data through the game-server. Then, any of the game related actions that interacts with the tracking data can be processed on the game-server, and this server can send out the corresponding updates to the wireless clients. This allows the wireless clients to only receive both the tracking data or updates without having to send back any information; in other words, minimizing the number of data transfers needed. If wireless clients are sending data there will be a minimum of two transfers on the wireless network, and each transfer of data through wireless network is at risk of latency or lost packets.

![](<../../.gitbook/assets/image (131) (1) (1) (1) (3).png>)
