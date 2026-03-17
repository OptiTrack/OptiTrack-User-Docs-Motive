---
description: A guide to installing and using the OptiTrack Godot plugin.
---

# OptiTrack Godot Plugin

## Overview

The OptiTrack Godot Plugin enables real-time streaming of Rigid Body data from Motive into Godot for visualization and recording.

{% embed url="https://youtu.be/KoKBG98iSOg" %}

### Requirements

* Godot version 4.6 or higher. Download the Godot software from the [godotengine.org download page](https://godotengine.org/download/windows/). &#x20;
* Motive version 3.4 or higher.

## Godot Setup

### Download the Plugin

The OptiTrack Godot plugin is available on GitHub in OptiTrack's optitrack-godot repository:&#x20;

{% embed url="https://github.com/OptiTrack/optitrack-godot" %}

* Click the green ![A screenshot of the <> Code button in Github. ](<../.gitbook/assets/Github Code download button.png>) code button at the top of the file list.&#x20;
* Select **Download ZIP** to download the plugin locally.&#x20;

<figure><img src="../.gitbook/assets/Godot Plugin - how to download.png" alt="A screenshot of the OptiTrack\optitrack-godot repository in GitHub, with the code button activated to show the menu options. Download ZIP is at the bottom of the list. "><figcaption></figcaption></figure>

* Once downloaded, unzip the plugin to a local directory.&#x20;
* In Windows Explorer, open the extracted folder, _optitrack-godot-main_, then open the _**example-project**_ folder. Leave this folder open for a future step.&#x20;

### Import into the Godot Project

* Open Godot, version 4.6 or higher.&#x20;
* The Project Manager window will open.&#x20;

<figure><img src="../.gitbook/assets/Godot Create Project Step 1 .png" alt="A screenshot of the Godot Project Manager screen, with no projects in the list. "><figcaption></figcaption></figure>

* Click the ![A screenshot of the Create button on the Godot Project Manager screen. ](<../.gitbook/assets/Godot Create button.png>) Create button in the upper left.&#x20;
* Assign a Project Name and Browse to select the location to save the project.&#x20;

<figure><img src="../.gitbook/assets/Godot Create Project Step 2 (1).png" alt="A screenshot of the Godot Create Project screen. "><figcaption></figcaption></figure>

* Click the ![A screenshot of the Create button that saves the Godot project. ](<../.gitbook/assets/Godot Create Project Step 2 - Create button.png>) Create button at the bottom of the screen to open the project.
* Return to the Windows Explorer window where the extracted folder _optitrack-godot-main_ is ope&#x6E;_._ Open the _example-project_ folder and drag the _**addons**_ folder into the _FileSystem_ tab in Godot.&#x20;

{% hint style="info" %}
If your project already has a folder called _**addons**_, open the plugin's _addons_ folder and copy the folder named _**optitrack\_plugin**_ into the project's existing _addons_ folder.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/Godot - Activate OptiTrack plugin Step 1 - Drag Addons to project.gif" alt="A screenshot of the Godot application just after dragging the OptiTrack Godot plugin addins folder into the Godot fileshare tab. "><figcaption></figcaption></figure>

{% hint style="info" %}
You may see several error messages after the application finishes registering global classes, even though the plugin has installed successfully. Look for the _optitrack\_plugin_ in the _addons_ folder in the Godot File System to verify that the installation completed.&#x20;
{% endhint %}

### Activate the Plugin in Godot

Now that the plugin is available in the project, it needs to be activated.&#x20;

* From the _Project_ menu, go to _Project Settings..._

<figure><img src="../.gitbook/assets/Godot - Activate OptiTrack plugin step 3 - open Program settings.png" alt="A screenshot of a project in Godot, with the Project menu open. "><figcaption></figcaption></figure>

* Open the Plugins tab.&#x20;
* Find the Optitrack plugin in the list and check the box to Enable it.&#x20;
* Click Close to return to the project.&#x20;

<figure><img src="../.gitbook/assets/Godot - Activate Step 4png.png" alt="A screenshot of the Godot Project Settings, Plugins tab, with the Optitrack plugin enabled. "><figcaption></figcaption></figure>

The OptiTrack tab will now be available in the left-most pane, along with the File System and History tabs. You may need to expand the width of the pane to see all three.&#x20;

Once the plugin is enabled, restart Godot.&#x20;

<figure><img src="../.gitbook/assets/Godot -Optitrack pane.png" alt="A screenshot of the Optitrack pane in Godot. "><figcaption></figcaption></figure>

## Motive Setup

#### Enable Streaming

In Motive, click the ![A screenshot of the Streaming Settings button from the Motive Control Deck. ](<../.gitbook/assets/Control Deck - Streaming Off SMALL (8).png>) Streaming Settings button in the bottom right corner of the Control Deck. &#x20;

To stream to Godot, make sure Streaming is enabled in the NatNet settings and the Transmission Type is set to Multicast.&#x20;

For more information about streaming from Motive, please see the [Data Streaming](../motive/data-streaming.md) page.&#x20;

<figure><img src="../.gitbook/assets/Motive - Streaming Settings for Godot.png" alt="A screenshot of the Motive Streaming Settings, with the &#x22;Enable&#x22; setting turned on and the &#x22;Transmission Type&#x22; setting set to Multicast. Both settings are highlighted. "><figcaption></figcaption></figure>

#### Create Rigid Bodies

In Motive, create the Rigid Bodies that you wish to stream into Godot. Refer to the [Rigid Body Tracking](../motive/rigid-body-tracking/) page for detailed instructions on how to create a Rigid Body in Motive.&#x20;

Once you have Rigid Bodies to track in Motive, you're ready to stream them into Godot.&#x20;

## Godot Plugin Connection Setup

Now that Motive is streaming, you're ready to configure the object connection in Godot.&#x20;

### Create an OptiTrack Rigid Body Node

In the Scene pane, in the Create Root Node options, click _3D Scene_.&#x20;

<figure><img src="../.gitbook/assets/Godot -Scene Pane.png" alt="A screenshot of the Scene pane in Godot, with the options to Create Root Node: shown. "><figcaption></figcaption></figure>

The Scene pane will change to show Node3D. The Inspector tab will display on the right.&#x20;

* Right click Node3D to access the context menu, then select _Add Child Node..._&#x20;

<figure><img src="../.gitbook/assets/Godot - Add child node step 1.png" alt="A screenshot of the Godot project screen, with the context menu for the Node3D options displayed. "><figcaption></figcaption></figure>

The Create New Node window will open.&#x20;

* Type Optitrack in the search bar and press enter.&#x20;
* The search results will return _OptiTrackRigidBody_.&#x20;
* Select _OptiTrackRigidBody_ then click the Create button at the bottom.&#x20;

<figure><img src="../.gitbook/assets/Godot - Add Child Node - search for Optitrack.png" alt="A screenshot of the &#x22;Add Child Node&#x22; screen, with OptiTrack in the search criteria and OptiTrackRigidBody as the sole search results. " width="563"><figcaption></figcaption></figure>

The child node will appear in the Scene pane. To see the list of rigid body assets from Motive in the OptiTrack pane, click the _Start Connection_ button. &#x20;

<div><figure><img src="../.gitbook/assets/Godot - Scene and Optitrack panes - Motive Streaming OFF.png" alt="A screenshot of the Godot Scene and OptiTrack panes, with the OptiTrackRigidBody child node added and the Streaming Connection stopped. "><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/Godot - Scene and Optitrack panes Streaming ON.jpg" alt="A screenshot of the Godot Scene and OptiTrack panes, with the OptiTrackRigidBody child node added and the Streaming Connection enabled."><figcaption></figcaption></figure></div>

### Add a Mesh

Apply a mesh to visualize the rigid body in the scene.&#x20;

* In the Scene tab, right click _OptiTrackRigidBody_ and select _Create Child Node_.&#x20;
* Search for _MeshInstance3D_. When found, select it and click _Create_.&#x20;

<figure><img src="../.gitbook/assets/Godot - Add MeshInstance3D.png" alt="A screenshot of the Godot &#x22;Add Child Node&#x22; search results,with MeshInstance3d selected. " width="563"><figcaption></figcaption></figure>

* The MeshInstance3D properties will display in the Inspector Window.&#x20;
* Click the dropdown menu in the Mesh field to select a mesh. For testing, we recommend selecting a primitive mesh, such as a box or a sphere.&#x20;
* Once the mesh is applied, a graphical representation will display in the Inspector tab as well as in the 3D scene.&#x20;

<div><figure><img src="../.gitbook/assets/Godot - MeshInstance Inspector tab step 1.png" alt="A screenshot of the Godot Inspector tab, showing the properties for the MeshInstance3D child node. No mesh has been applied yet. "><figcaption><p>Before a Mesh is added.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Godot - MeshInstance Inspector tab step 2.png" alt="A screenshot of the Godot Inspector tab, showing the properties for the MeshInstance3D child node. The dropdown menu to apply a mesh is open. "><figcaption><p>Adding the Mesh.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Godot - MeshInstance Inspector tab step 3.png" alt="A screenshot of the Godot Inspector tab, showing the properties for the MeshInstance3D child node. A Box Mesh is now applied. "><figcaption><p>Mesh is now applied. </p></figcaption></figure></div>

<figure><img src="../.gitbook/assets/Godot - Mesh applied in 3D view.png" alt="A screenshot of the Godot 3D perspective window, with a box mesh applied to the rigid body asset.. "><figcaption><p>Mesh shown in the 3D scene. </p></figcaption></figure>

### Add Animation&#x20;

* &#x20;With the _MeshInstance3D_ installed, select the _OptiTrackRigidBody_ node in the Scene hierarchy.&#x20;
* In the Inspector panel, check the box to _Animate in Editor._&#x20;

<figure><img src="../.gitbook/assets/Godot - MeshInstance Inspector tab step 4 - Animate in Editor.png" alt="A screenshot of the top portion of the Godot Inspector tab, for the OptiTrack plugin."><figcaption></figcaption></figure>

* Use the buttons at the bottom of the OptiTrack pane to play or pause the selected take in Motive.&#x20;

<figure><img src="../.gitbook/assets/Godot - Motive Play and Pause buttons.jpg" alt="A screenshot of the Motive Timeline Play and Motive Timeline Pause buttons from the OptiTrack plugin in Godot. "><figcaption></figcaption></figure>

## Troubleshooting

If the object does not animate:&#x20;

* Restart Godot.
* Reopen the project.
* Click _Start Connection_ again.

In most cases, the data stream will reconnect successfully after restarting.
