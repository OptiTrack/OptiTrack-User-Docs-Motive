# Unreal Engine: OptiTrack Live Link Plugin

## **Overview**

This page provides instructions on how to use the OptiTrack Unreal Engine Live Link plugin. The plugin communicates with Unreal's built-in Live Link system by providing a Live Link source for receiving tracking data streamed from Motive. This plugin can be used for controlling cameras and objects in virtual production applications. When needed, the [OptiTrack Unreal Engine Plugin](../../../../plugins/optitrack-unreal-engine-plugin/) can also be alongside this plugin. For a specific guide to InCamera VFX (i.e. LED Wall Virtual Production) please see this wiki page [Unreal Engine: OptiTrack InCamera VFX](../../../../virtual-production/unreal-engine-optitrack-incamera-vfx.md).

## Setup

**1. \[Motive] Setup rigid body streaming in Motive.**

Get Motive streaming with at least one rigid body or Skeleton asset. Make sure the [Streaming](../../../../motive/data-streaming.md) settings are configured correctly, and the asset is active under the [Assets pane](../../../../motive-ui-panes/assets-pane.md).

**2. \[UE] Install the OptiTrack plugins in Unreal Engine (UE).**

You can install the OptiTrack Unreal Engine plugin by putting the plugin files into one of the following directories:

* A global engine plugin can be placed in `C:\Program Files\Epic Games\[Engine Version]\Engine\Plugins`
* A project-specific plugin can be placed in `[Project Directory]\Plugins`

**3. \[UE] Enable the plugins in UE project.**

Go to _Edit → Plugins_ and enable two of the required plugins. First one is the **OptiTrack - Live Link** plugin under _Installed_ group, and the second one is the built-in **Live Link** plugin under Built-In group.

![OptiTrack - Live Link plugin. Make sure the plugins are placed in the plugins folder either in the project or engine directory.](<../../../../.gitbook/assets/image (1208).png>)

![Built-In Live Link plugin.](<../../../../.gitbook/assets/image (1226).png>)

**4. \[UE] Open the LiveLink pane**

Open the LiveLink pane from _Window → Virtual Production → Live Link_ in the toolbar.

![Live Link pane in UE5.](<../../../../.gitbook/assets/image (1195).png>)

![Live Link pane in UE5.](<../../../../.gitbook/assets/image (1220).png>)

**5. \[UE] Configure and create a new OptiTrack source**

In the LiveLink pane under _Source_ options, go to the OptiTrack Source menu and configure the proper connection settings and click _Create_. Please make sure to use matching network settings configured from the Streaming pane in Motive.

![Creating OptiTrack source with client streaming settings.](<../../../../.gitbook/assets/image (1192).png>)

**6. \[UE] Check the Connection.**

If the streaming settings are correct and the connection to Motive server is successful, then the plugin will list out all of the detected assets. They should have green dots next to them indicating that the corresponding asset has been created and is receiving data. If the dots are yellow, then it means that the client has stopped receiving data. In this case, check if Motive is still tracking or if there is a connection error.

![Connected to the rigid body data stream.](<../../../../.gitbook/assets/image (1178).png>)

## Using the Plugin

### Static Meshes or Camera Actors

**1. Add the camera object or static mesh object that you wish to move**

Add a camera actor from the Place Actors pane or a static mesh from the project into your scene. For the static meshes, make sure their Mobility setting is set to _Movable_ under the Transform properties.

![Camera actor listed under the Place Actors pane.](<../../../../.gitbook/assets/image (1237).png>) ![Actor mobility set to movable.](<../../../../.gitbook/assets/image (1200).png>)

**2. Add a LiveLinkController Component**

Select an actor you want to animate. In the **Details** tab select your "actor" (Instance). In the search bar, type in Live Link. Then click on the _Live Link Controller_ from the populated list.

![Live Link Controller component needs be added.](<../../../../.gitbook/assets/image (1229).png>)

**3. Select the target rigid body**

Under the Live Link properties in the Details tab click in the **Subject Representation** box and select the target rigid body.

![The target rigid body selected under Live Link Controller component properties.](<../../../../.gitbook/assets/image (1185).png>)

**4. Check**

Once the target rigid body is selected, each object with the Live Link Controller component attached and configured will be animated in the scene.

### Timecode Setup

When the camera system is synchronized to another master sync device and a timecode signal is feeding into [eSync 2](../../../../synchronization/synchronization-hardware/external-device-sync-guide-esync-2.md), then the received timecode can be used in UE project through the plugin.

**1. Set Timecode Provider under project settings**

From _Edit → Project Settings_, search timecode and under Engine - General settings, you should find settings for the timecode. Here, set the the Timecode Provider to LiveLinkTimeCodeProvider.

![Select the timecode provider under project settings.](<../../../../.gitbook/assets/image (1223).png>)

**2. Set OptiTrack source in the Live Link pane as the Timecode Provider**

Open the Live Link pane, and select the OptiTrack subject that we created when first setting up the plugin connection. Then, under its properties, check the Timecode Provider box.

![Enable timecode provider setting in the plugin.](<../../../../.gitbook/assets/image (1205).png>)

**3. Check**

The timecode from Motive should now be seen in the Take Recorder pane. Take Recorder pane can be found under Window → Cinematics → Take Recorder in the toolbar.

![Timecode shown in the Take Recorder pane.](<../../../../.gitbook/assets/image (1191).png>)

### Skeletons

**1. Create a new Animation Blueprint**

Right click the mesh you would like to use and select "Create > Anim Blueprint"

![New animation blueprint.](<../../../../.gitbook/assets/image (1204).png>)

**2. Name and Open the Animation Blueprint**

Name the animation blueprint something appropriate, then double click it to open the blueprint.

![Rename blueprint.](<../../../../.gitbook/assets/image (1246).png>)

**3. Hook up your Blueprint**

Create a "Live Link Pose" component and connect it to the "Output Pose". Assign the "Live Link Subject Name" to the Skeleton that you would like to use.

![Connect to pose, then choose name.](<../../../../.gitbook/assets/image (1053).png>)

Change the "Retarget Asset" property in the Details pane of the blueprint editor to "OptiTrackLiveLinkRetarget"

![Retargeting option.](<../../../../.gitbook/assets/image (1240).png>)

**4. Getting the Skeleton to Animate**

To animate the Skeleton in real time click the Animation Blueprint from earlier. In the Details pane under the skelteonLive Link Skeleton Animation". After you add that component the mesh should start animating.

To animate the Skeleton in a game, just press the play button. Adding the "Live Link Skeleton Animation" object is not necessary to animate in play mode.

![Component to animate Skeleton.](<../../../../.gitbook/assets/image (1243).png>)

**5. OptiTrack Live Link Display**

In order to see the debug skeleton overlay from Motive, you can enable the OptiTrack Live Link Display. From the Quick Add dropdown from the toolbar, you can select OptiTrack Live Link Display. This will appear in the Outliner tab and you can change any settings in its Details tab as needed.&#x20;

<figure><img src="../../../../.gitbook/assets/image (790).png" alt=""><figcaption><p>Select OptiTrack Live Link Display from Quick Add</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (797).png" alt=""><figcaption><p>Default green debug skeleton from OptiTrack Live Link Display</p></figcaption></figure>

**Debugging Note**

If the retargeting doesn't match the mesh correctly, then you can create a new OptiTrackLiveLinkRetarget blueprint from scratch and modify the bone mapping names.

![Options for retargeting to different names. Click image to enlarge.](<../../../../.gitbook/assets/image (1171).png>)

### MetaHumans

Animating a MetaHuman follows basically the same steps as another Skeleton, but requires hooking into the Skeleton at a very specific location. For more information about MetaHuman setup outside of our scope, please visit [Epic Games's website](https://docs.metahuman.unrealengine.com/en-US/).

**1. Find the Skeletal Mesh**

Navigate to the Skeletal Mesh for your MetaHuman. This is typically located in a folder such as MetaHumans > \[Name] > \[Female/Male] > \[Height] > \[Weight] > Body. Double click the Skeletal Mesh to open the blueprint.

![Component to animate Skeleton.](<../../../../.gitbook/assets/image (1212).png>)

**2. Open the AnimGraph Tab**

Click the "Blueprint" option on the top bar of new window. In the bottom left corner navigate to My Blueprint > Animation Graphs > AnimGraph and double click.

![MetaHuman Skeletal Mesh default window view.](<../../../../.gitbook/assets/image (1179).png>)

![Blueprint tab view.](<../../../../.gitbook/assets/image (1217).png>)

**3. Hook up your Blueprint**

You'll see a very complex AnimGraph already setup. Make a new Live Link Pose object like in the Skeleton creation steps. Connect the Input Pose or Control Rig to the input of the Live Link Pose. Connect the output of the Live Link Pose to the Output Pose AnimGraph object.

![Animgraph before.](<../../../../.gitbook/assets/image (1186).png>)

![Animgraph after.](<../../../../.gitbook/assets/image (1164).png>)

**4. Retarget in the Details Tab**

The last step in this window is to set the **Retarget Asset** to **OptiTrackLiveLinkRetarget** for the **Live Link Pose** node. To do this, simply click on the dropdown in the **Details tab** and click the dropdown under **Retarget Asset** and select **OptiTrackLiveLinkRetarget**. After it has been set, click **Compile** in the top left of this window. You may now close this window and move on to the next steps.

![Retarget Asset from Details Tab](<../../../../.gitbook/assets/image (1231).png>)

**5. Level of Detail (LOD)**

MetaHumans will change their Level of Detail (LOD), i.e. how complex the asset is, based on how far the camera is from the actor among other factors. In order for things to animate correctly the Forced LOD must be a minimum of 1 (default of -1). To change this setting, click on the **(Instance)** you wish to change in the **Details** tab on the main workspace window. Below the selected **(Instance)** select the **LOD** tab. From here you can change the value in the **Forced LOD Model** field.

![Component to animate Skeleton.](<../../../../.gitbook/assets/image (1207).png>)

**6. Animate your MetaHuman**

At this point if you drag the base MetaHuman object into the scene then it will animate like other Skeletons.

![Component to animate Skeleton.](<../../../../.gitbook/assets/image (1173).png>)

## Standalone Game Mode

For testing the project in standalone game mode, or when developing an nDislay application, the Live Link plugin settings must be saved out and selected as the default preset to be loaded onto the project. If this is not done, the configured settings may not get applied. After configuring the LiveLink plugin settings, save out the preset from the Live Link pane first. Then, open the Project Settings and find Live Link section in the sidebar. Here, you can select the default Live Link preset to load onto the project, as shown in the screenshot below. Once the preset is properly saved and loaded, the corresponding plugin settings will be applied to the standalone game mode.

If all the configuration is correct, the actors will get animated in the newly opened game window when playing the project in the standalone game mode.

![Creating a preset from Live Link panel. Select Save As Preset.](<../../../../.gitbook/assets/image (1198).png>)

![Assigning the preset in the Project Settings.](<../../../../.gitbook/assets/image (1242).png>)

![Playing a scene in standalone game mode.](<../../../../.gitbook/assets/image (1193).png>)

## MotionBuilder Retargeting

Another path to get data into Unreal Engine is to stream data from Motive -> MotionBuilder (using the OptiTrack MotionBuilder Plugin) -> Unreal Engine (using the Live Link plugin for MotionBuilder). This has the benefit of using the Human IK (HIK) retargeting system in MotionBuilder, which will scale characters of very different sizes/dimensions better than the base Live Link plugin. More information can be found by consulting [Unreal Engine's Live Link to MotionBuilder documentation](https://docs.unrealengine.com/4.27/en-US/AnimatingObjects/SkeletalMeshAnimation/LiveLinkPlugin/ConnectingLiveLinktoMobu/).

## Troubleshooting

<details>

<summary><strong>Q - Trying to add more than 64 frames in the same frame. Oldest frames will be discarded.</strong></summary>

A - This notification message may appear at the bottom of the Live Link pane if the frame rate in the data stream doesn't match the rendering frame rate inside UE. This is within notification within the Engine only, so it should not interfere with the project. If this notification must be removed, you can go to the Project Settings → Engine → General Settings → Framerate section, check _Use Fixed Frame Rate_ option, and set the Fixed Frame Rate to be the same rate as the Motive frame rate.

</details>
