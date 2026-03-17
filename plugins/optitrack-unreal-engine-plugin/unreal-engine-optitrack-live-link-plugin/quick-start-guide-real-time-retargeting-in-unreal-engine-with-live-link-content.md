---
description: Step-by-Step instructions for retargeting Live Link content in Unreal Engine.
---

# Quick Start Guide: Real-Time Retargeting in Unreal Engine with Live Link Content

## Requirements

* Motive 3.1 or higher
* Unreal Engine 5.5
* OptiTrack Live Link Plugin 5.5

## Setup

### Install Live Link Plugin

This step is completed once per computer.&#x20;

* Download and unzip the latest version of the OptiTrack Live Link Plugin from the OptiTrack [Download ](https://www.optitrack.com/support/downloads/plugins.html)site.&#x20;
* Place the plugin files into one of the following directories:
  * A global engine plugin can be placed in `C:\Program Files\Epic Games\ [Engine Version]\ Engine\ Plugins`
  * A project-specific plugin can be placed in `[Project Directory]\Plugins`

### Enable Plugin in Unreal Engine

This step is completed with each new project.&#x20;

Go to _Edit → Plugins_ and enable the two required plugins:

* **OptiTrack - Live Link** plugin, located under the _Installed_ group. This is the plugin downloaded in the previous step.
* Unreal Engine's built-in **Live Link** plugin.

{% hint style="info" %}
Search for _Live Link_ on the plugins window to find these and other Live Link related plugins.&#x20;
{% endhint %}

Allow Unreal Engine to restart, then close the plugin window when the project reloads.

{% hint style="info" %}
**Show Content**&#x20;

To show the OptiTrack plugins folder in the Content Browser, click the Settings button in the Browser's top right corner and check the boxes to _Show Engine Content_ and _Show Plugin Content_.&#x20;
{% endhint %}

### Motive Streaming Settings

To enable streaming in Motive, click the <img src="../../../.gitbook/assets/Settings button (17).png" alt="" data-size="line"> button to open the [_Applications Settings_](../../../motive-ui-panes/settings/) panel, then select the [_Streaming_ ](../../../motive-ui-panes/settings/settings-streaming.md)tab, or use the <img src="../../../.gitbook/assets/Control Deck - Streaming Off SMALL (4).png" alt="" data-size="line"> button in the right corner of the [Control Deck](../../../motive-ui-panes/control-deck.md) to open the _Streaming_ tab directly.&#x20;

* In the _NatNet_ section, select _**Enable**_ to begin streaming.&#x20;
* Select the **Local Interface**. Use Loopback if streaming to the same computer, otherwise select the IP address for the network where the client application resides.
* Set the **Bone Naming Convention** to _UnrealEngine_.&#x20;
* Set the **Up Axis** to Y-Axis. The plugin will bring the data in with a Y-Forward orientation.&#x20;

Please see the [Data Streaming](../../../motive/data-streaming.md) page for more details on all settings available for streaming.&#x20;

<figure><img src="../../../.gitbook/assets/Settings - Streaming Standard settings only (5).png" alt="" width="489"><figcaption><p>Application Settings Panel: Streaming Tab, Streaming enabled. </p></figcaption></figure>

## Connect Motive to Unreal Engine

* In Unreal Engine, open Live Link Hub from the _Tools_ menu _&#x6F;_&#x6E; the toolbar, if it's not open already. Under _Virtual Production,_ select _Live Link Hub._&#x20;
* Click the <img src="../../../.gitbook/assets/UE Add Source Button (1).png" alt="" data-size="line"> button in Live Link Hub to add a new Live Link source.
* Select _OptiTrack Source_, check _Connect Automatically,_ or enter the IP address for the Motive PC in the _Server Address_ field, the IP address for the Unreal PC in the _Client Address_ field. Enter 127.0.0.1 in both fields if running both on the same PC. Click create.

<figure><img src="../../../.gitbook/assets/LLHub - Add Source (1).png" alt=""><figcaption><p>Add a Live Link source in Unreal Engine.</p></figcaption></figure>

Live Link will display information about the connection, including a list of assets streaming from Motive:&#x20;

<figure><img src="../../../.gitbook/assets/image (1565).png" alt=""><figcaption><p>OptiTrack Live Link Connection in Unreal Engine. </p></figcaption></figure>

### OptiTrack Live Link Display

The OptiTrack Live Link Display provides validation that the data is streaming in correctly from Motive. In the Unreal Engine Outliner pane, all assets in the Motive volume should nest under the OptiTrack Live Link Display.&#x20;

#### Add OptiTrack Live Link Display

Click the <img src="../../../.gitbook/assets/Unreal Engine Quick Add button.png" alt="" data-size="line"> Quick Add button and start typing _OptiTrack_ over the menu to activate the search function.  Select the OptiTrack Live Link Display from the list of available options and drop it into the scene in the desired location.&#x20;

<figure><img src="../../../.gitbook/assets/Live Link Add OptiTrackNDisplay.png" alt=""><figcaption><p>Searching from the UE Quick Add button.</p></figcaption></figure>

Play the _Take_ file when working with recorded data to see the Live Link assets in the Viewport. Once the assets are available, you can pause playback and the assets will still be displayed.&#x20;

Once you have validated the Live Link connection, we recommend turning off Live Link asset visibility to improve performance as you work through the rest of the pipeline.

* Select _OptitrackLiveLinkDisplay_ in the Outliner panel.&#x20;
* The properties for the _OptitrackLiveLinkDisplay_ will populate in the Details pane.&#x20;
* In the _Assets_ section, uncheck _Display Assets_.&#x20;

<figure><img src="../../../.gitbook/assets/Display Assets Off in OLLD Details CROPPED.png" alt=""><figcaption><p>Assets section of the Details pane for the OptitrackLiveLinkDisplay: Display Assets highlighted. </p></figcaption></figure>

{% hint style="info" %}
Turn the _Display Assets_ setting on or off as needed throughout the workflow.&#x20;
{% endhint %}

## Retargeting to MetaHumans

Retargeting is the process of applying an existing animation model to a character, at the correct scale.&#x20;

In this section, we'll demonstrate the retargeting workflow using skeleton data streaming from Motive and retarget it to a MetaHuman in Unreal Engine in real-time. For each MetaHuman, we'll create the following in Unreal Engine:

* A Retargeter to map the Motive Animation data to the correct Skeletal Meshes in Unreal.
* An Animation Blueprint for the Motive Avatar.
* An Animation Blueprint for the MetaHuman.
* &#x20;A Blueprint for a MetaHuman character.&#x20;

For more information and tutorials about working with MetaHumans in Unreal Engine, please visit [Epic Games' MetaHuman community](https://dev.epicgames.com/community/metahuman).&#x20;

{% hint style="info" %}
This workflow is fine-tuned specifically for MetaHumans, but it can be used for characters with unique custom skeletons as well.&#x20;
{% endhint %}

#### Y-Forward vs. X-Forward Axis

MetaHuman joints use a Y-Forward axis, and the plugin brings the data in using this orientation.&#x20;

Prior versions of the plugin used an X-Forward axis for the skeletal mesh, with adjustments made to the linked asset in Unreal Engine. To work with legacy assets configured for an X-Forward axis:

* From the LiveLink tab, select OptiTrack to display the LiveLink properties.
* In the _Coordinates_ section, uncheck _Animate Y-Forward_.&#x20;

<figure><img src="../../../.gitbook/assets/Animate Y-Forward ANNOTATED.png" alt="" width="563"><figcaption><p>Live Link settings: Animate Y-Forward property. </p></figcaption></figure>

### Add MetaHuman

We'll start the workflow by adding the MetaHuman to the project. This will create a folder structure in the project to consolidate the content related to each individual MetaHuman. We'll use these folders to save the Retargeter and the two Animation Blueprints we need to complete the retarget.&#x20;

#### Add the MetaHuman to the Project

To add a new MetaHuman to your project:

* Click the Quick Add button <img src="../../../.gitbook/assets/Unreal Engine Quick Add button (1).png" alt="" data-size="line"> and select _Quixel Bridge._&#x20;
* Select either a new MetaHuman from a preset to download or browse the local collection for any previously downloaded MetaHumans.&#x20;
* Once the MetaHuman is downloaded, a green arrow will appear in the upper left corner of the profile picture. Click the blue arrow in the upper right corner to add the MetaHuman to your project.&#x20;

<figure><img src="../../../.gitbook/assets/MetaHuman - Add to Project.png" alt=""><figcaption><p>A downloaded MetaHuman in UE.</p></figcaption></figure>

* The Content Browser will have a new _MetaHumans_ folder within the _Content_ folder. Each MetaHuman has their own folder, which contains their Blueprint and all the content needed to render them.&#x20;

<figure><img src="../../../.gitbook/assets/MetaHuman in Content Browser.png" alt="" width="563"><figcaption><p>MetaHuman content in the Content Browser in UE.</p></figcaption></figure>

#### Copy the MetaHuman Blueprint

We recommend using a copy of the MetaHuman when setting up the retarget. This allows you to take the data that comes from the MetaHuman in the retarget during production and add it to the original MetaHuman later in post-production.

To create a copy, right-click the Blueprint and select _Duplicate_, or use the keyboard shortcut _Ctrl + D_.&#x20;

We suggest using a simple convention such as _BP\_<_&#x4D;etaHumanNa&#x6D;_&#x65;>\_Retarget_ for all copies.&#x20;

<figure><img src="../../../.gitbook/assets/image (1568).png" alt=""><figcaption><p>MetaHuman Blueprints: Original and Copy.</p></figcaption></figure>

Now that the file structure for the MetaHumans is setup, we can create the Retargeter and the two Animation Blueprints. We'll update the MetaHuman Blueprint once these are done. &#x20;

### Create Retargeter

* In the Content Browser, browse to and open the folder for the MetaHuman. &#x20;
* Right-click the Content Browser and select _Animation -> Retargeting -> IK retargeter_.&#x20;
* Name the retargeter. We recommend a name such as _IKR\_Motive\_to\_Meta_.&#x20;

#### Set Retargeter Source and Target&#x20;

Open the newly created retargeter. In the Details pane, update the Source and Target values as follows:

* **Source IKRig Asset:** IK\_MotiveAvatar\_Opti
* **Source PreviewMesh:**
  * Female avatars:  SKM\_F\_MotiveAvatar\_Opti
  * Male avatars:  SKM\_M\_MotiveAvatar\_Opti
* **Target IKRig Asset:**  IK\_metahuman
* **Target Preview Mesh:**&#x20;
  * Female avatars:  f\_med\_nrw\_body
  * Male avatars:  m\_med\_nrw\_body

{% hint style="success" %}
The _Preview Mesh_ fields will auto-complete once the _IKRig Asset_ is selected.&#x20;
{% endhint %}

#### Align Skeletons

The Viewport will show that the two skeletons are not properly aligned. This occurs because the skeletons are in different poses.&#x20;

<figure><img src="../../../.gitbook/assets/Metahuman Skeleton pre-alignment (1).png" alt="" width="563"><figcaption><p>Prior to alignment.</p></figcaption></figure>

Click the Running Retargeter button in the upper left corner to stop the retargeter and switch to edit mode. The button will update to _Editing Retarget Pose._

<div><figure><img src="../../../.gitbook/assets/UE Running Retarget (1).png" alt=""><figcaption><p>The Retargeter in Run Mode. </p></figcaption></figure> <figure><img src="../../../.gitbook/assets/UE Editing Retarget Pose (1).png" alt=""><figcaption><p>The Retargeter in Edit Mode.</p></figcaption></figure></div>

Click the Auto Align button <img src="../../../.gitbook/assets/UE Auto Align button CROPPED (1).png" alt="" data-size="original"> and select _Align all Bones &#x74;_&#x6F; complete the alignment.

The retarget will now display correctly in the Viewport.

<figure><img src="../../../.gitbook/assets/Metahuman Skeleton post-alignment (1).png" alt=""><figcaption><p>After alignment.</p></figcaption></figure>

### Motive Avatar Animation Blueprint

* Right-click the Content Browser and select _Animation -> Animation Blueprint_.

<figure><img src="../../../.gitbook/assets/image (1569).png" alt=""><figcaption><p>Add Animation Blueprint in Unreal Engine.</p></figcaption></figure>

In the _Create Animation Blueprint_ Search bar, type _Opti_, then select the _SK\_MotiveAvatar\_Opti_ skeleton. Give the newly created Animation Blueprint a name, such as _ABP\_MotiveAvatar_.&#x20;

<figure><img src="../../../.gitbook/assets/image (1570).png" alt="" width="479"><figcaption><p>Create Animation Blueprint: Select template.</p></figcaption></figure>

* Double-click the new Animation Blueprint to open the AnimGraph window.&#x20;
* Right-click in the graph area and type _Live Link Pose_ in the Search field, then select the node that appears.&#x20;
* In the Live Link Pose node, use the dropdown list under _Live Link Subject Name_ to select the actor whose skeleton will be used for the Motive avatar.&#x20;
* To connect the two nodes, click the _Result_ icon in the Output Pose and drag it to the corresponding icon on the Live Link Pose.&#x20;

<div><figure><img src="../../../.gitbook/assets/Link Output Pose to Live Link Pose 1.png" alt=""><figcaption><p>Click the Result icon to connect the Output Pose...</p></figcaption></figure> <figure><img src="../../../.gitbook/assets/Link Output Pose to Live Link Pose 2.png" alt=""><figcaption><p>...to the Live Link input pose. </p></figcaption></figure></div>

* Click the Compile button, then Save. The Compile button will update as all changes are incorporated:

<div><figure><img src="../../../.gitbook/assets/Compile - Dirty (1).png" alt=""><figcaption><p>Pre-Compilation.</p></figcaption></figure> <figure><img src="../../../.gitbook/assets/Compile - Clean.png" alt=""><figcaption><p>Post-Compilation.</p></figcaption></figure></div>

### &#x20;MetaHuman Animation Blueprint

* Right-click the Content Browser and select _Animation -> Animation Blueprint_.
* On the Create Animation Blueprint window, select the _metahuman\_base\_skel_ skeleton.&#x20;
* We suggest a naming convention such as _ABP\__\<MetaHumanName>_\_Meta._ Name, then open the newly created animation blueprint.&#x20;
* Right click the AnimGraph. From the list of _All Actions_, search for and select _Retarget Pose From Mesh_.

<figure><img src="../../../.gitbook/assets/image (1561).png" alt=""><figcaption><p>Unconfigured Retarget Pose from Mesh in UE.</p></figcaption></figure>

* Select _Retarget Pose from Mesh_ in the AnimGraph to display its properties in the Details pane.
* Find _IKRetargeter Asset_ in the Settings section.&#x20;
* Click the <img src="../../../.gitbook/assets/UE Selector Button.png" alt="" data-size="line"> button and select the IK retargeter created in the [prior step](quick-start-guide-real-time-retargeting-in-unreal-engine-with-live-link-content.md#create-retargeter-asset).

<div><figure><img src="../../../.gitbook/assets/IKRetaregeter Asset Property - nothing selected.png" alt=""><figcaption><p>IKRetargeter Asset - None selected. </p></figcaption></figure> <figure><img src="../../../.gitbook/assets/IKRetaregeter Asset Property - Asset selected.png" alt=""><figcaption><p>IKRetargeter Asset - with Retargeter Asset selected. </p></figcaption></figure></div>

* Drag the _Output Pose_ Result icon to the corresponding icon on the _Retarget Pose From Mesh_ node to link the two. &#x20;

<figure><img src="../../../.gitbook/assets/Link Output Pose to Retarget Pose.png" alt=""><figcaption></figcaption></figure>

* Click the Compile button, then save.

### Update MetaHuman Blueprint

#### Add Skeletal Mesh and Skeletal Animation

* Open the [MetaHuman Blueprint](quick-start-guide-real-time-retargeting-in-unreal-engine-with-live-link-content.md#copy-the-metahuman-blueprint) created in a prior step.&#x20;
* Click the _Viewport_ tab to see the MetaHuman character.
* In the Components panel, Click the <img src="../../../.gitbook/assets/Live Link Add Component button (6).png" alt="" data-size="line"> Add button and select _Skeletal Mesh_.&#x20;
* Name the new mesh something distinct, such as _OptiTrackSkeletalMesh_.&#x20;
* Drag the body component of the MetaHuman under the new skeletal mesh.
* The Components should now look like this:

<figure><img src="../../../.gitbook/assets/Metahuman - Components with Opti SM.png" alt=""><figcaption><p>Skeletal Mesh added to a MetaHuman in UE.</p></figcaption></figure>

* Next, add the _Live Link Skeletal Animation_ component. This will allow playback to start once the animation blueprint is attached. &#x20;
* To improve performance while streaming to MetaHumans, click the _LODSync_ component. In the Details pane, go to _LOD -> Forced LOD_ and change the setting to 1.
* Click Compile to update the Blueprint, then save.&#x20;

#### Apply Animation Blueprints to Skeletal Meshes

* In the _Components pane_, select the OptiTrack [skeletal mesh](quick-start-guide-real-time-retargeting-in-unreal-engine-with-live-link-content.md#link-metahuman) created previously.&#x20;
* In the Details pane, go to _Animation -> Anim Class_.&#x20;
* Use the drop-down to search for and select the [Motive Avatar Animation Blueprint](quick-start-guide-real-time-retargeting-in-unreal-engine-with-live-link-content.md#motive-avatar-animation-blueprint) created earlier.&#x20;

<figure><img src="../../../.gitbook/assets/image (1559).png" alt=""><figcaption><p>Animation Details for the OptiTrack Skeletal Mesh Component in UE.</p></figcaption></figure>

* With the OptiTrack skeletal mesh still selected, go to _Mesh -> Skeletal Mesh Asset_.
* Type _Opti_ in the dropdown's search bar to quickly find the applicable Motive Avatar. This should match the the Source Preview Mesh used in the [IK Retargeter](quick-start-guide-real-time-retargeting-in-unreal-engine-with-live-link-content.md#set-retargeter-source-and-target) created earlier:
  * Female avatar:  SKM\_F\_MotiveAvatar\_Opti
  * Male avatar:  SKM\_M\_MotiveAvatar\_Opti

<figure><img src="../../../.gitbook/assets/Skeletal Mesh for OptiTrack SM.png" alt=""><figcaption><p>Skeletal Mesh Asset for the OptiTrack Skeletal Mesh component in UE.</p></figcaption></figure>

* In the _Components pane,_ select the skeletal mesh for the MetaHuman. This is the _Body_ previously moved to nest directly below the OptiTrack Skeletal mesh.&#x20;
* In the Details pane, go to _Animation -> Anim Class_.&#x20;
* Use the drop-down to search for and select the [MetaHuman Animation Blueprint ](quick-start-guide-real-time-retargeting-in-unreal-engine-with-live-link-content.md#metahuman-animation-blueprint)created earlier. &#x20;

<figure><img src="../../../.gitbook/assets/image (1560).png" alt=""><figcaption><p>Animation Details for the MetaHuman Skeletal Mesh.</p></figcaption></figure>

* With the MetaHuman (body) skeletal mesh still selected, go to _Mesh -> Skeletal Mesh Asset_.
* Select the same mesh used in the Target Preview Mesh in the IK Retargeter created earlier:&#x20;
  * Female avatar:  f\_med\_nrw\_body
  * Male avatar:  m\_med\_nrw\_body

Animation should now be playing in the viewport of the MetaHuman blueprint.&#x20;

{% hint style="warning" %}
Disregard any visual issues with the animation in this view. They will not appear in the environment when you add the MetaHuman to your scene.
{% endhint %}

### Add MetaHuman to Scene

* Now that the MetaHuman blueprint is configured correctly, drag it from the Content Browser into the scene.&#x20;
* In the Outliner pane, drag the newly added blueprint to the _OptiTrackLiveLinkDisplay_ component created earlier.  The mouse tip will display the drop location with a green checkmark as you drag the component, to show exactly where it will nest when the mouse is released.&#x20;

<figure><img src="../../../.gitbook/assets/UE_Move_MetaHuman_1.gif" alt="" width="563"><figcaption><p>Move the MetaHuman under the <em>OptiTrackLiveLinkDisplay</em> in the Outliner. </p></figcaption></figure>

* Once the MetaHuman is nested under the _OptiTrackLiveLinkDisplay_, its location coordinates will update to reflect the OptiTrack global origin.&#x20;
* To align the MetaHuman with the subject configured in the Motive Avatar Animation Blueprint, go to _Details -> Transform_ and zero out the coordinates by clicking the <img src="../../../.gitbook/assets/UE Reset values button (1).png" alt="" data-size="line"> button to the right of the values.

<figure><img src="../../../.gitbook/assets/Transform coordinates.png" alt=""><figcaption><p>Transform values for the MetaHuman prior to reset. </p></figcaption></figure>

{% hint style="info" %}
If you previously disabled the display of assets after setting up the [OptiTrack Live Link Display](quick-start-guide-real-time-retargeting-in-unreal-engine-with-live-link-content.md#add-optitrack-live-link-display), re-enable the display now to validate that the retarget is running correctly.&#x20;
{% endhint %}

### MetaHuman Animation Tips

The MetaHuman may not be animating exactly as intended. At this point, the rest of retargeting is much more of a trial-by-error artistic process.

We achieved the best standard results using the following settings for all the Hand and Foot Goals, however, we recommend testing other values and changing other fields to get the best results for your project:

* FK
  * Rotation Mode: One to One
  * Translation Mode: Absolute
* IK
  * Blend to Source: 1

<figure><img src="../../../.gitbook/assets/image (1567).png" alt="" width="563"><figcaption><p>Properly aligned MetaHuman in Unreal Engine. </p></figcaption></figure>
