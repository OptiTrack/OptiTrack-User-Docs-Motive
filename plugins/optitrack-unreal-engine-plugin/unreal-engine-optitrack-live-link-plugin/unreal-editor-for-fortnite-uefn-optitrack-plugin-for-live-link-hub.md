---
description: >-
  Use the Live Link Hub to stream OptiTrack camera data to the UEFN plugin for
  video game development in Fortnite.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/plugins/optitrack-unreal-engine-plugin/unreal-engine-optitrack-live-link-plugin/unreal-editor-for-fortnite-uefn-optitrack-plugin-for-live-link-hub
---

# Unreal Editor for Fortnite (UEFN): OptiTrack Plugin for Live Link Hub

## Overview <a href="#overview" id="overview"></a>

The OptiTrack Live Link Hub plugin allows game designers to use OptiTrack Motion Capture data to animate characters in Fortnite through Unreal Editor for Fortnite (UEFN).Comment

### Requirements <a href="#requirements" id="requirements"></a>

Download the latest Unreal Engine 5 Plugin from the [OptiTrack Downloads page](https://optitrack.com/support/downloads/plugins.html#unreal-plugin).

Open the Epic Games Launcher. The following Epic Games applications must be installed:

* Unreal Engine 5.5Comment
* Live Link Hub&#x20;
* UEFN&#x20;
* Fortnite&#x20;

## Getting Started <a href="#getting-started" id="getting-started"></a>

### Install the Plugin <a href="#install-the-plugin" id="install-the-plugin"></a>

* Launch Unreal Editor for Fortnite (UEFN).&#x20;
* Select _Live Link Hub_ from the Tools menu, if it's not already open.&#x20;
* Click the _Settings_ button in the upper right corner and select _Plugins..._

<figure><img src="../../../.gitbook/assets/Live Link Hub Settings Plugins.png" alt=""><figcaption><p>Live Link Hub with Settings button options displayed.</p></figcaption></figure>

* In the _User Plugin Directories_ section, click the _Add Element_ button. &#x20;

<figure><img src="../../../.gitbook/assets/LLHub - Add Element 2.png" alt=""><figcaption><p>Add a plugin to Live Link Hub.</p></figcaption></figure>

* Click the ellipses button to browse to and select the downloaded plugin. &#x20;

<figure><img src="../../../.gitbook/assets/LLHub - Add Element browse to plugin.png" alt=""><figcaption><p>Click to browse to the plugin.</p></figcaption></figure>

* Restart UEFN when prompted after the plugin is installed.&#x20;

### Motive Streaming Settings

To enable streaming in Motive, click the <img src="../../../.gitbook/assets/Settings button (17).png" alt="" data-size="line"> button to open the [_Applications Settings_](../../../motive-ui-panes/settings/) panel, then select the [_Streaming_ ](../../../motive-ui-panes/settings/settings-streaming.md)tab, or use the <img src="../../../.gitbook/assets/Control Deck - Streaming Off SMALL (4).png" alt="" data-size="line"> button in the right corner of the [Control Deck](../../../motive-ui-panes/control-deck.md) to open the _Streaming_ tab directly.&#x20;

* In the _NatNet_ section, select _**Enable**_ to begin streaming.&#x20;
* Select the **Local Interface**. Use Loopback if streaming to the same computer, otherwise select the IP address for the network where the client application resides.
* &#x20;Set the **Bone Naming Convention** to _UnrealEngine_.&#x20;
* Set the **Up Axis** to Y-Axis. The plugin will bring the data in with a Y-Forward orientation.&#x20;

Please see the [Data Streaming](../../../motive/data-streaming.md) page for more details on all settings available for streaming.&#x20;

<figure><img src="../../../.gitbook/assets/Settings - Streaming Standard settings only (1).png" alt="" width="489"><figcaption><p>Application Settings Panel: Streaming Tab, Streaming enabled. </p></figcaption></figure>

### Configure Live Link Hub

#### Add Source

* In Unreal Engine, open Live Link Hub from the _Tools_ menu _&#x6F;_&#x6E; the toolbar, if it's not open already. Under _Virtual Production,_ select _Live Link Hub._&#x20;
* Click the <img src="../../../.gitbook/assets/UE Add Source Button (1).png" alt="" data-size="line"> button in Live Link Hub to add a new Live Link source.
* Select _OptiTrack Source_, check _Connect Automatically,_ or enter the IP address for the Motive PC in the _Server Address_ field, the IP address for the Unreal PC in the _Client Address_ field. Enter 127.0.0.1 in both fields if running both on the same PC. Click create.

<figure><img src="../../../.gitbook/assets/LLHub - Add Source.png" alt=""><figcaption><p>Adding a source in Live Link Hub.</p></figcaption></figure>

Properties are shown in the Source Details tab when the OptiTrack source is selected. The properties that are applicable to Fortnite characters are listed below.

<figure><img src="../../../.gitbook/assets/LLHub - Source Details tab.png" alt="" width="317"><figcaption><p>Live Link Hub Sources and Source Details tab.</p></figcaption></figure>

#### Streaming Data Offset

Adjust the location, orientation, or scale of the streaming data. &#x20;

#### Timecode

Timecode is fully supported in the plugin. Click the button in the top right to use preset system time codes or add a new Timecode Provider in the _Source Details_ tab.&#x20;

<figure><img src="../../../.gitbook/assets/LLHub - Timecode in plugin MARKED UP.png" alt=""><figcaption><p>Live Link Hub Timecode settings.</p></figcaption></figure>

Timecode data may appear to stutter in Unreal Editor even when it is transmitting correctly. To confirm that the data is in sync, compare the timecode in Live Link Hub to the timecode in Motive.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Timecode stutter MARKED UP.png" alt=""><figcaption><p>Timecode displayed in Motive, Live Link Hub, and UEFN. </p></figcaption></figure>

{% hint style="info" %}
Unreal Editor for Fortnite does not support the display of markers.&#x20;
{% endhint %}

### Copy Assets to Project Folder

We recommend using Windows Explorer to copy assets into the project folder. Right-click the project folder in the Unreal Editor Content Browser and select _Show in Explorer_.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Content browser Show in Explorer.png" alt="" width="322"><figcaption></figcaption></figure>

In the Content Browser, copy the following files and folders from _All > Engine > Plugins > OptiTrack - Live Link Content > Animations_ to the project folder:&#x20;

* Female Avatar (folder)
* Male Avatar (folder)
* Textures (folder)
* IK\_MotiveAvatar\_Opti.uasset (file)
* SK\_MotiveAvatar\_Opti.uasset (file)

{% hint style="info" %}
The T-Pose asset and animation blueprints typically used in Unreal Engine are not supported in Unreal Editor. &#x20;
{% endhint %}

Once the required assets are copied to the project folder, click the <img src="../../../.gitbook/assets/Launch Session button.png" alt="" data-size="line"> button. Unreal Editor will prompt to _Save Selected_, with all unsaved content selected by default.

Unreal Editor will validate the project files before launching the live session.&#x20;

## Create Retargeter in Unreal Editor

All skeletons in Unreal Editor are based on the standard Fortnite mannequin. Animation is applied to the mannequin rather than using an animation blueprint. In this example, we will use the Fortnite Mannequin to build an IK Rig to receive data from the OptiTrack skeletons.&#x20;

### Create IK Rig

Before creating our IK Rig, drag the Motive Avatar of your choosing into the scene to prep the retarget phase.&#x20;

To create the IK Rig:&#x20;

* Right-click in the Content area. Select _Animation > Retargeting > IKRig._
* Name the IKRig. We recommend _IK\_FNMannequin_.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Content Menu - IK Rig.png" alt=""><figcaption><p>Add a new IK Rig to Unreal Editor.</p></figcaption></figure>

Double-click the newly created IKRig to edit it. This will open in a new window.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Add Preview Mesh COMPOSITE.png" alt=""><figcaption></figcaption></figure>

In the Details tab, change the Preview Mesh to the FN Mannequin. &#x20;

<figure><img src="../../../.gitbook/assets/UEFN Add Preview Mesh 2.png" alt=""><figcaption></figcaption></figure>

The mannequin is pre-configured to work with Fortnite. This allows you to use the _Auto Create_ features in the upper left corner to finish setting up the IK Rig.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Add Preview Mesh - Toolbar buttons.png" alt=""><figcaption></figcaption></figure>

1. Click the _Auto Create Retarget Chains_ button.
2. Click _Auto Create IK_.
3. Click _Reset_.
4. Click _Save_.

The IK Rig is now configured and the tab can be closed.&#x20;

### Create IK Retargeter

* Right-click in the Content area. Select _Animation > Retargeting > IK Retargeter._
* Name the IK Retargeter. We recommend _RTG\_Motive\_FN_.&#x20;

<figure><picture><source srcset="../../../.gitbook/assets/UEFN Content menu create IK Retargeter BLACK.png" media="(prefers-color-scheme: dark)"><img src="../../../.gitbook/assets/UEFN Content menu create IK Retargeter WHITE.png" alt=""></picture><figcaption></figcaption></figure>

* Open the newly created Retargeter.&#x20;
* On the Details tab, go to _Source > Source IKRig Asset._&#x20;
* Use the dropdown list to select the standard Motive avatar, _IK\_MotiveAvatar\_Opti._

<figure><picture><source srcset="../../../.gitbook/assets/UEFN Set Retargeter 1 BLACK.png" media="(prefers-color-scheme: dark)"><img src="../../../.gitbook/assets/UEFN Set Retargeter 1 WHITE.png" alt=""></picture><figcaption></figcaption></figure>

* In the Target section, set the _Target IKRig Asset_ to the [IKRig created earlier](https://app.gitbook.com/o/6K2GcxpSS9y4e9SRLTrx/s/uHClgoIWDmmoXSr2eD9q/plugins/optitrack-unreal-engine-plugin/unreal-engine-optitrack-live-link-plugin/unreal-editor-for-fortnite-uefn-optitrack-plugin-for-live-link-hub#create-ik-rig), _IK\_FNMannequin._&#x20;

<figure><picture><source srcset="../../../.gitbook/assets/UEFN Set Retargeter 2 BLACK.png" media="(prefers-color-scheme: dark)"><img src="../../../.gitbook/assets/UEFN Set Retargeter 2 WHITE.png" alt=""></picture><figcaption></figcaption></figure>

### Align Skeletons

The Viewport will show that the two skeletons are not properly aligned. This occurs because the skeletons are in different poses.&#x20;

* Click the Running Retargeter button in the upper left corner to stop the retargeter and switch to edit mode. The button will update to _Editing Retarget Pose._

<div><figure><img src="../../../.gitbook/assets/UE Running Retarget.png" alt=""><figcaption><p>The Retargeter in Run Mode. </p></figcaption></figure> <figure><img src="../../../.gitbook/assets/UE Editing Retarget Pose.png" alt=""><figcaption><p>The Retargeter in Edit Mode.</p></figcaption></figure></div>

* Click the Auto Align button <img src="../../../.gitbook/assets/UE Auto Align button CROPPED (1).png" alt="" data-size="original"> and select _Align all Bones &#x74;_&#x6F; complete the alignment.
* Set the Retargeter back to _Run_ mode for the remaining steps.&#x20;

#### Blend to Source

To complete the next step, it's easiest if only the mapped bone chains are visible.&#x20;

* In the Chain Mapping pane, click the Settings button and select _Hide Chains Without IK._&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Hide Chains without IK CROPPED.png" alt=""><figcaption></figcaption></figure>

* Select all of the mapped Chains.
* &#x20;In the Details tab, go to _IK > Blend to Source_.&#x20;
* Set the value to 1.0.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN IK Blend to Source.png" alt="" width="392"><figcaption></figcaption></figure>

* Click the _Root Settings_ button <img src="../../../.gitbook/assets/UEFN Root Settings Button.png" alt="" data-size="original"> in the top right corner.
* Go to _Blend to Source > Blend to Source_ and set the value to 1.0.

<figure><img src="../../../.gitbook/assets/UEFN Root Settings blend to source.png" alt="" width="392"><figcaption></figcaption></figure>

The retarget will now display correctly in the Viewport. This window can now be closed.

## Add Animation

* From the Content Browser, drag the skeletal mesh for the Fortnite mannequin into the scene. The mannequin is located in _All > Fortnite > Characters > PlayerBasics._&#x20;
* Both the Motive Avatar and the Fortnite Mannequin will be in the scene.
* Select the Motive Avatar.&#x20;
* Click the ![](<../../../.gitbook/assets/Live Link Add Component button.png>) Add button to add the Performer component.&#x20;
* In the Details tab, go to _Performer > Performance Capture > Subject Name._
* Select a performer from the list of actors in Motive. &#x20;
* The Motive Avatar will now animate with the selected actor.

<figure><img src="../../../.gitbook/assets/UEFN Select Performer for Motive Avatar CROPPED.png" alt="" width="481"><figcaption></figcaption></figure>

* Select the Fortnite Mannequin to display its properties in the Details pane.
* Click the Add button ![](<../../../.gitbook/assets/Live Link Add Component button (1).png>) and use the search bar to find and add the _Retarget Component_.

<figure><img src="../../../.gitbook/assets/UEFN Add Retarget to Mannequin 1 CROPPED.png" alt="" width="482"><figcaption></figcaption></figure>

Once the Retarget Component is attached to the Mannequin, update the following properties in the _Retarget_ section:&#x20;

* **Source Skeletal Mesh Component:** Select the Motive Avatar.
* **Controlled Skeletal Mesh Component:** This should already be set to the Fortnite Mannequin.
* **Retarget Asset:** Select the [IK Retargeter](unreal-editor-for-fortnite-uefn-optitrack-plugin-for-live-link-hub.md#create-ik-retargeter) created in an earlier step (_RTG\_Motive\_FN_ in our example).

<figure><img src="../../../.gitbook/assets/UEFN Add Retarget to Mannequin 3.png" alt="" width="481"><figcaption></figcaption></figure>

* Click the Push Changes button ![](<../../../.gitbook/assets/UEFN Push Changes Button.png>) to save the change into the Fortnite game.&#x20;

{% hint style="info" %}
The Avatar and Mannequin will animate in realtime only in the Editor, not in the game.&#x20;
{% endhint %}

#### Align the Avatar and Mannequin

* In the Outliner pane, drag the Mannequin to nest under the Motive Avatar.&#x20;
* In the Details pane for the Mannequin, go to _Transform > Location_ and reset the values to 0.&#x20;
* The Avatar and the Mannequin will be aligned.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Align Mannequin to Avatar reset Transform.png" alt="" width="481"><figcaption></figcaption></figure>

## Record Animation

Once all of the characters are configured, the next step is to record the animation using the Take Recorder and Sequencer in Unreal Editor.&#x20;

* To open either pane, go to the _Windows menu > Cinematics._&#x20;
* Type the project name in the Slate field.&#x20;
* With the Mannequin selected, click the add source ![](<../../../.gitbook/assets/UE Add Source Button.png>)  button.
* Select _From Actor > Add 'Device Mannequin'._

<figure><img src="../../../.gitbook/assets/UEFN Take Recorder Add Source 2.png" alt="" width="481"><figcaption></figcaption></figure>

With the Mannequin selected, update the following properties:

* Disable _Transform > Transform Track._&#x20;
* Disable _Animation Recorder > Remove Root Animation_ (shown below)_._

<figure><img src="../../../.gitbook/assets/UEFN Mannequin settings Remove Root Anim Recorder.png" alt="" width="480"><figcaption></figcaption></figure>

#### Countdown

Go to _User Settings > Countdown_ to include a countdown timer to start recording.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Record Animation Countdown setting.png" alt="" width="481"><figcaption></figcaption></figure>

#### Recording

To begin recording, click the large red Play button on the right edge of the Slate in the Take Recorder:&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Take Recorder Slate and record only.png" alt="" width="477"><figcaption></figcaption></figure>

Recorded tracks will show in the Sequencer tab. Click the Stop Recording button <img src="../../../.gitbook/assets/UEFN Stop Recording Button.png" alt="" data-size="original"> when done recording.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Record animation in progress ANNOTATED.png" alt=""><figcaption><p>Recording in Progress in UEFN.</p></figcaption></figure>

#### Review Recording

When the recording is completed, click the _Review_ button in the Take Recorder pane.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Review last recording CROPPED.png" alt=""><figcaption><p>Take Recorder pane - Review Last recording button. </p></figcaption></figure>

The character will now animate as expected.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Review last Recording 1.png" alt=""><figcaption></figcaption></figure>

You can find the Take and the associated animations in the Cinematics folder in the Content Browser.  Takes are organized with a folder for each subscene. The animations recorded in that subscene are stored in an Animation folder, one for the Device Mannequin and one for the Motive Avatar.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Saved Animation location.png" alt=""><figcaption><p>Animation for a subscene in the Content Browser.</p></figcaption></figure>

## Animate Fortnite Characters

Now that the animation has been created and aligned to the Device Mannequin, it's time to apply it to a Fortnite character. Since all characters in Fortnite use this same skeleton, no additional alignment is required. &#x20;

### Select a Character in UEFN

Fortnite has a large selection of characters available, all based on the Device Mannequin skeleton. To add a character to the scene from the Content Browser:

* Go to _Fortnite > Devices > AI_.
* Drag the **Character Device** to the scene.

<figure><img src="../../../.gitbook/assets/UEFN - How to select a FN Character 1A.png" alt=""><figcaption></figcaption></figure>

* Select the Character Device in the Viewport.
* Go to _Fortnite > Characters_ and select the desired character from the gallery.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN - How to select a FN Character 1.png" alt=""><figcaption></figcaption></figure>

In the Details pane for the newly added Character Device, drag the Fortnite character you wish to use to _User Options > Character_.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN - How to select a FN Character 2.png" alt=""><figcaption></figcaption></figure>

### Apply Animation <a href="#apply-animation" id="apply-animation"></a>

* Select the Fortnite character in the Viewport.
* Under _User Options_, check the box for _Custom Idle_.
* Drag the Device Mannequin animation from the Content Browser to the _Custom Idle_ field.

<figure><img src="../../../.gitbook/assets/UEFN Add animation to character 1.png" alt=""><figcaption></figcaption></figure>

* Click the Push Changes ![](<../../../.gitbook/assets/UEFN Push Changes Button (1).png>) button to save and update the game.&#x20;
* Fortnite will update the game in Edit Mode, with the status displayed in the upper right corner. The game will move through the following phases: Preparing; Loading Project; Downloading; and Connecting (displayed on the Edit Session screen). When the game loads, the status will be Up to Date.&#x20;

<figure><img src="../../../.gitbook/assets/UEFN Game launched with changes.png" alt=""><figcaption></figcaption></figure>

The animation will play on the Fortnite character when the game starts. It will not play in the editor. To see this, you can start the game from UEFN or inside Fortnite itself.  &#x20;
