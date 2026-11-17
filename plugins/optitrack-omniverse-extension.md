---
description: A guide to installing and using the OptiTrack Omniverse
---

# OptiTrack Omniverse Extension

## Overview

The OptiTrack Omniverse Extension is designed to stream OptiTrack Motive data onto customized OptiTrack assets in Omniverse, providing a way to animate in Omniverse using our precision, real-world data. Only rigid body and skeleton data from Motive can be animated at this time.

### Purpose

The OptiTrack Omniverse Extension allows a running tracking server such as Motive to stream live, high-accuracy motion‑capture data directly into an Omniverse USD stage.

Using the extension, you can bind USD assets in the stage to assets being tracked in Motive so that it animates in real time as the physical object moves in the capture volume.

### Use Cases

The OptiTrack Omniverse Extension feeds precision, live, real-world motion data into Omniverse as ground truth, expanding and enhancing the data against which digital twins and trained robot behaviors can be validated.

#### Robotics and Sim-First Development

Motion capture data can help inform a robot of where it and its surroundings are in the physical world. It can serve to enhance the realism of digital environment representations, and it can let individual members of multi-robot fleets know each other’s real-time locations.

#### Product Design, Architecture, Engineering

Design review and iteration benefit from being able to physically move a prototype or mockup and see that exact motion reflected on its USD counterpart in real time. Because Motive captures precise motion, hands-on interaction with a physical part, mechanism, or fixture translates directly into the virtual model in which a team collaborates.

### Limitations

Only rigid bodies and skeletons can be animated using the extension.

## Getting Started

### Requirements

* Motive version 3.5 or later
* Omniverse Kit App Template version 110.1 or later
* Git version 2.30 or later

{% hint style="warning" %}
The OptiTrack Omniverse Extension was developed with the **Kit Base Editor** as its baseline environment. Because Omniverse applications are modular and can include different functionality, the application hosting the extension should provide, at minimum, the same capabilities as the Kit Base Editor. If you are using an existing Omniverse application, verify that it includes the functionality required by the Kit Base Editor before proceeding.
{% endhint %}

### Omniverse Kit App Template Setup

This section of the guide was adopted from information in the [Kit App Template Quick Start Guide](https://github.com/NVIDIA-Omniverse/kit-app-template#quick-start). You are encouraged to review it for more information on topics covered in this section.

#### Prerequisite: Clone the Kit App Template Repository with Git

Begin by cloning the `kit-app-template` to your local workspace:

* Clone

```
git clone https://github.com/NVIDIA-Omniverse/kit-app-template.git
```

* Navigate to Cloned Directory

```
cd kit-app-template
```

#### Building an Omniverse App

If you do not have an Omniverse application that meets the requirements above, create one using the **Kit Base Editor** template.

* Run the following command to initiate the configuration wizard:
* Linux:

```
./repo.sh template new
```

* Windows:

```
.\repo.bat template new
```

* Select `Application` → `[kit_base_editor]: Kit Base Editor` to create an application using the Kit Base Editor template.

<figure><img src="../.gitbook/assets/image (1588).png" alt=""><figcaption><p>Making a Kit Base Editor application with the Kit App Template</p></figcaption></figure>

* After making the selection above, follow the prompt instructions as seen in the image below:
  * Enter name of application .kit file \[name-spaced, lowercase, alphanumeric]: \[set application name]
  * Enter application\_display\_name: \[set application display name]
  * Enter version: \[set application version]
  * Do you want to add application layers? No
    * Application layers are a separate Omniverse Kit feature that is not used by the OptiTrack Omniverse Extension. Selecting No will not affect this extension.
* When you have responded to all of the prompts, the console output should look like this:

<figure><img src="../.gitbook/assets/image (1589).png" alt=""><figcaption><p>Console output after successfully creating an Omniverse Application with the Omniverse Kit App Template tool</p></figcaption></figure>

### OptiTrack Omniverse Setup

#### Installing the Extension

* Download the OptiTrack Omniverse Extension’s .zip file from [the Downloads page](https://www.optitrack.com/support/downloads) on OptiTrack’s website.
* Unzip the extension’s .zip file into `kit-app-template\source\extensions`.
  * If the `\extensions` folder doesn't exist in the `\source` folder, create it.
* Rename the unzipped folder to `optitrack.natnet_py_ext`.

<figure><img src="../.gitbook/assets/image (1590).png" alt=""><figcaption><p>Correct naming convention for the extension placed in kit-app-template\source\extensions</p></figcaption></figure>

* Navigate back to the kit-app-template directory and rebuild Omniverse using the build command.
* Linux:

```
./repo.sh build
```

* Windows:

```
.\repo.bat build
```

* A successful build produces the message `BUILD (RELEASE) SUCCEEDED (Took XX.XX seconds)`

#### Enabling the Extension in Omniverse

Once the extension is available in the Omniverse application, enable it.

* Launch your Omniverse app by running the launch command from the `kit-app-template` directory.
* Linux:

```
./repo.sh launch
```

* Windows:

```
.\repo.bat launch
```

* Select with arrow keys which app you want to launch: \[Select the created editor application]
* Once the Omniverse application window launches, open the Omniverse Extension menu by selecting Developer → Extensions from the ribbon menu.

<figure><img src="../.gitbook/assets/image (1591).png" alt=""><figcaption><p>Developer → Extensions menu item from the ribbon menu at the top of the Omniverse application</p></figcaption></figure>

* Clear the search bar, search for OptiTrack, and enable the switch next to OPTITRACK NATNET PYTHON EXTENSION.
  * On success, an OptiTrack menu item appears in the app’s ribbon menu.

<figure><img src="../.gitbook/assets/image (1592).png" alt=""><figcaption><p>The OptiTrack extension, enabled via the Omniverse extension menu</p></figcaption></figure>

### Motive Setup

#### Enable Streaming

In Motive, click the ![](<../.gitbook/assets/image (1594).png>) Streaming Settings button in the lower right corner of the Control Deck.

To stream to Omniverse, make sure Streaming is enabled in the NatNet settings.

Users can change the **Local Interface** and **Transmission Type** values as needed. Remember these values, as they are required in the next section.

Ensure the **Skeleton Coordinates** value is set to Local and the **Up-Axis** value is set to Y-Axis.

<figure><img src="../.gitbook/assets/image (1595).png" alt=""><figcaption><p><strong>Red:</strong> Streaming settings in Motive that the OptiTrack Omniverse Extension must be configured to match<br><strong>Yellow:</strong> Streaming settings in Motive that must be set to specific values</p></figcaption></figure>

For more information about streaming from Motive, please see the [Data Streaming](https://docs.optitrack.com/motive/data-streaming) page.

### Starting a NatNet Connection

Once Motive streaming is enabled, make a connection between the Omniverse app and Motive.

#### Editing NatNet Settings

In the Omniverse app, open the OptiTrack settings window by selecting OptiTrack → Settings from the ribbon menu.

<figure><img src="../.gitbook/assets/image (1596).png" alt=""><figcaption><p>OptiTrack → Settings from the ribbon menu at the top of the Omniverse app</p></figcaption></figure>

Populate the NatNet Connection section of the settings window using the **Local Interface** and **Transmission Type** values from Motive's NatNet settings. For help finding these, review the [Enable Streaming](optitrack-omniverse-extension.md#enable-streaming) section.

For the Client Address and Server Address fields:

* If Local Interface is set to `loopback` in Motive, set both Client Address and Server Address to `127.0.0.1`.
* Otherwise, use the IP address shown in Motive's Local Interface field as the Server Address, and the IP address of the machine running the Omniverse application as the Client Address.

The settings window automatically validates the IP addresses you enter as you type.

* Invalid IPs cause a small red notification to appear under the text box with the invalid value.
* When you finish entering a valid IP address, the notification disappears.

While unsaved changes are present in the NatNet Connection window, a pink warning message appears.

<figure><img src="../.gitbook/assets/image (1597).png" alt=""><figcaption><p>Example of settings windows with valid values (left) and invalid (right). An unsaved changes warning message is present.</p></figcaption></figure>

When all settings look correct, click Save.

* On success, the unsaved changes warning message disappears.
* If invalid values remain in the address fields when you click Save, nothing happens. Only valid settings can be saved. Revise the invalid fields and try again.

{% hint style="info" %}
You can toggle the Connect on Startup setting from the NatNet settings window. This makes the NatNet connection attempt to run every time the extension is initialized (that is, on Omniverse app startup).
{% endhint %}

After a successful save, the settings entered are remembered in future sessions.

#### Starting the NatNet Connection

There are several ways to start a NatNet connection once the NatNet connection settings are configured:

* From the settings window, click Save & Connect to connect using your updated settings.
* From the app ribbon menu, select OptiTrack → Start or OptiTrack → Refresh to start the connection with the most recent set of saved settings.
* If the Connect on Startup setting is enabled in the settings window, the connection attempts to initialize on Omniverse application startup.

Once the NatNet connection is started, a notification popup appears on the bottom right side of the USD viewport indicating success or failure.

* On success, a blue ![](<../.gitbook/assets/image (1599).png>) Info notification appears that contains the server address and name of the connected app.
  * Info notifications also appear to report user errors, such as attempting to start a NatNet connection using OptiTrack → Start when an existing connection is already running.
* On failure, a yellow ![](<../.gitbook/assets/image (1598).png>) Warning notification appears that describes the cause of failure.

<figure><img src="../.gitbook/assets/image (1600).png" alt=""><figcaption><p>Example of success notification</p></figcaption></figure>

#### Stop and Refresh the NatNet Connection

* To stop a running NatNet connection, select OptiTrack → Stop from the ribbon menu.
* To refresh the NatNet connection, select OptiTrack → Refresh from the ribbon menu.
* Both of these methods notify you on success.

<figure><img src="../.gitbook/assets/image (1601).png" alt=""><figcaption><p>The OptiTrack dropdown menu’s different connection methods</p></figcaption></figure>

### Animating Motive Assets

Now you’re ready to begin animating Motive assets in Omniverse.

{% hint style="info" %}
To maintain framerate, ensure OptiTrack assets and their children aren’t selected while assets are in motion, and the USD stage viewport is not unnecessarily large.
{% endhint %}

#### Animating Rigid Bodies

This section covers how to animate Motive rigid body assets in Omniverse.

**Create an OptiTrack Rigid Body Asset**

From the application’s ribbon menu, select Create → OptiTrack → Rigid Body.

<figure><img src="../.gitbook/assets/image (1602).png" alt=""><figcaption><p>The Create → OptiTrack → Rigid Body menu item</p></figcaption></figure>

An OptiTrackRigidBody object spawns in the Stage window on the right side of the screen.

* Nothing is visible in the USD viewport yet. This is expected.
* Click on the new OptiTrackRigidBody to select it and reveal its properties in the Property window on the bottom right of the screen.

<figure><img src="../.gitbook/assets/image (1603).png" alt=""><figcaption><p>An OptiTrackRigidBody object selected in the Stage window</p></figcaption></figure>

**Add a Mesh**

Apply a mesh to visualize the rigid body in the stage.

* In the Stage window, right-click OptiTrackRigidBody while it is selected to access the context menu, then hover over Create → Mesh, and select an option from the Mesh submenu.
  * For testing, we recommend selecting a primitive mesh, such as a box or a cone.

<figure><img src="../.gitbook/assets/image (1604).png" alt=""><figcaption><p>Assigning a mesh as a child of an OptiTrackRigidBody with the context menu</p></figcaption></figure>

Once spawned, the mesh is visible in the USD viewport.

<figure><img src="../.gitbook/assets/image (1605).png" alt=""><figcaption><p>OptiTrackRigidBody’s child mesh visible in the USD viewport</p></figcaption></figure>

For steps to align the child mesh with the position of the rigid body in Motive, see the [Labeled Markers](optitrack-omniverse-extension.md#labeled-markers) section.

**Add Animation**

* Reselect OptiTrackRigidBody from the Stage window to reveal its properties in the Property window.
* Scroll all the way down the list in the Property window until you reach Raw USD Properties. Click on the section header to expand it.
  * When expanded, 2 subsections titled OptiTrack and Extra Properties become visible inside Raw USD Properties.

<figure><img src="../.gitbook/assets/image (1606).png" alt=""><figcaption><p>The Raw USD Properties section in the Property window, expanded to reveal the OptiTrack and Extra Properties subsections</p></figcaption></figure>

* In the OptiTrack section, click on the dropdown in the Rigid Body ID field.
  * A list of the Rigid Bodies present in Motive appears. Select the value corresponding to the Rigid Body you want to animate.
* Ensure Motive is playing/rendering a take. The OptiTrackRigidBody in Omniverse should be running through the same animations as the Rigid Body in the stage.

#### Animating Skeletons

This section covers how to animate Motive skeleton assets in Omniverse.

**Create an OptiTrack Skeleton Asset**

The process for spawning OptiTrack skeleton assets in Omniverse is similar to spawning rigid body assets.

* From the application’s ribbon menu, select Create → OptiTrack → Skeleton.

<figure><img src="../.gitbook/assets/image (1607).png" alt=""><figcaption><p>The Create → OptiTrack → Skeleton menu item</p></figcaption></figure>

* An OptiTrackSkeleton object spawns in the Stage window on the right side of the screen.
  * As with rigid bodies, nothing is visible in the USD viewport yet. This is expected.
* Click on the new OptiTrackSkeleton to select it and reveal its properties in the Property window on the bottom right of the screen.

<figure><img src="../.gitbook/assets/image (1608).png" alt=""><figcaption><p>An OptiTrackSkeleton object selected in the Stage window</p></figcaption></figure>

* Selecting the Skeleton ID dropdown in the OptiTrack section of the OptiTrackSkeleton’s Raw USD Properties reveals the list of skeletons being streamed by Motive.

<figure><img src="../.gitbook/assets/image (1609).png" alt=""><figcaption><p>The list of skeletons streamed by Motive, seen in the Skeleton ID dropdown of the OptiTrackSkeleton’s properties</p></figcaption></figure>

* Setting the Skeleton ID value automatically generates a wireframe skeleton in the neutral T pose at the Omniverse’s stage origin. This skeleton begins to animate on the arrival of the next NatNet frame.

<figure><img src="../.gitbook/assets/image (1610).png" alt=""><figcaption><p>A skeleton in Motive represented with an OptiTrackSkeleton asset</p></figcaption></figure>

## Marker Visibility

The extension provides a way to toggle the visibility of markers in the Omniverse stage. Labeled as well as unlabeled markers can be made visible. This feature is intended to let users align meshes in Omniverse to the same positions they appear in Motive by using the position of the markers in the volume as reference.

{% hint style="info" %}
After enabling marker visibility, if Motive is in edit mode with a paused take, you might need to resume and pause the take to ensure the most recent marker data is available in Omniverse.
{% endhint %}

### Labeled Markers

To reveal the labeled markers of any OptiTrack asset in Omniverse, complete the following steps:

* Access the Raw USD Properties of a given OptiTrack asset.
* In the OptiTrack section of the Raw USD Properties, enable the Show Markers setting.
  * The labeled markers for this asset should now be visible in the Omniverse stage. If they aren’t, refer to the note in the [Marker Visibility](optitrack-omniverse-extension.md#marker-visibility) section.
* You can adjust the color of the individual asset’s markers by changing the Marker Color setting.

<figure><img src="../.gitbook/assets/image (1611).png" alt=""><figcaption><p>An OptiTrack rigid body asset in Omniverse with its markers enabled</p></figcaption></figure>

* You can now use the labeled markers to align meshes in the Omniverse stage to their positions in Motive.
  * When aligning assets, apply transforms onto the visible children of the OptiTrack assets in the Omniverse stage organizer, not to the OptiTrack assets themselves.

<figure><img src="../.gitbook/assets/image (1612).png" alt=""><figcaption><p>Labeled markers belonging to a series of rigid bodies representing a Unitree Go2 dog used to align meshes in Omniverse</p></figcaption></figure>

* You can configure the Show Markers setting to be enabled by default for newly spawned assets by toggling the Show Marker Constellation by Default setting in the Markers section of the OptiTrack Settings window.

<figure><img src="../.gitbook/assets/image (1613).png" alt=""><figcaption><p>The Show Marker Constellation by Default setting in the Markers section of the OptiTrack Settings window</p></figcaption></figure>

### Unlabeled Markers

Unlabeled marker visibility can be toggled by enabling the Show Unlabeled Markers setting in the Markers section of the OptiTrack Settings window.

* The default color of unlabeled markers is red; you can adjust this with the Unlabeled Markers Color setting in the same section.

<figure><img src="../.gitbook/assets/image (1614).png" alt=""><figcaption><p>Unlabeled markers (red) and labeled markers (blue) visble in Omniverse</p></figcaption></figure>

## Example Configuration

A folder containing an example Motive take file, Omniverse USD scene, and a setup guide is packaged with the plugin at optitrack.natnet\_py\_ext\Example.

This example uses the OptiTrack Omniverse Extension to animate a digital twin of the Unitree Go2 robot dog in Omniverse with a prerecorded Motive take.

The provided example can be used to check that the extension is installed and streaming correctly, or as a reference for how to set up a scene.

## Troubleshooting

This section describes troubleshooting options for users encountering issues when using the extension.

### Troubleshooting Guides

#### Troubleshooting the NatNet Connection

Here are troubleshooting steps to take when NatNet fails to connect.

* Review settings window and check for blank or invalid values.
* Ensure the Save button was pressed in the NatNet Connection section of the OptiTrack settings screen in Omniverse to write address field inputs into settings.
* Review NatNet settings in Motive and ensure the following:
  * Streaming is enabled.
  * The Local Interface and Transmission Type values match those in the Omniverse NatNet settings window (see the [Enable Streaming](optitrack-omniverse-extension.md#enable-streaming) section).
* Switch the Local Interface value in Motive NatNet settings to another value, then back to your desired value, and attempt to connect again.

#### Troubleshooting OptiTrack Asset Animation

Here are troubleshooting steps to take when OptiTrack assets fail to animate in Omniverse.

* Review the Rigid Body / Skeleton ID property of the OptiTrack asset.
  * Make sure it is not set to Unassigned.
  * Confirm it corresponds to the asset in Motive you want to animate via the asset’s name and streaming ID.
* If the value corresponding to the asset you want to animate is not present in the Rigid Body / Skeleton ID property dropdown:
  * Ensure Motive Streaming is on (see the [Enable Streaming](optitrack-omniverse-extension.md#enable-streaming) section).
  * Refresh the NatNet connection (see the [Stop and Refresh the NatNet Connection](optitrack-omniverse-extension.md#stop-and-refresh-the-natnet-connection) section) and check the dropdown menu again.
  * Confirm that the Asset Name and Streaming ID properties of the asset in Motive match the values that you seek in the dropdown.

<figure><img src="../.gitbook/assets/image (1615).png" alt=""><figcaption><p>The Asset Name and Streaming ID values of a rigid body in Motive, and how they are reflected in the Rigid Body ID property dropdown of OptiTrackRigidBody in Omniverse</p></figcaption></figure>

#### Troubleshooting Low Framerate

Here are troubleshooting steps if there is a low framerate during animation.

* Ensure the OptiTrackRigidBody asset or its children aren’t selected while assets are in motion.
* Ensure the USD stage viewport is not unnecessarily large.
* Ensure the following settings are an appropriate value for your computer’s hardware specifications:
  * NatNet FPS Cap in the Data Stream section of the OptiTrack Settings window
  * The Default Animation Rate Omniverse setting, found in Edit → Preferences → Stage

<figure><img src="../.gitbook/assets/image (1616).png" alt=""><figcaption><p>The locations of the NatNet FPS Cap and Default Animation Rate settings</p></figcaption></figure>
