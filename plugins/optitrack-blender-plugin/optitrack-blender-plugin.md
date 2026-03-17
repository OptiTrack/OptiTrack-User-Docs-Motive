---
description: Learn to setup and use the OptiTrack Blender plugin.
---

# OptiTrack Blender Plugin

## Overview <a href="#overview" id="overview"></a>

The [OptiTrack Blender Plugin](https://optitrack.com/support/downloads/plugins.html) enables streaming of real-time Rigid Body data from Motive to Blender.&#x20;

### Version Requirements <a href="#version-requirements" id="version-requirements"></a>

* Blender Version: 4.1 or above (recommended)
* Motive Version: 3.1.0 or higher

## Blender Setup (Client) <a href="#blender-setup-client" id="blender-setup-client"></a>

To install the plugin:

* Download the Blender Plugin from the [OptiTrack downloads](https://optitrack.com/support/downloads/plugins.html) site.&#x20;
* DO NOT unzip the downloaded file.&#x20;

### Import Plugin Package into Blender <a href="#import-plugin-package-in-blender" id="import-plugin-package-in-blender"></a>

* In Blender, select _Preferences_ from the Edit menu.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>The Edit menu in Blender.</p></figcaption></figure>

* Select _Add-ons_ from the menu on the left.
* Use the dropdown arrow in the upper right corner to select _Install from Disk..._
* Browse to the downloaded zip file and _Install from Disk_.

<figure><img src="../../.gitbook/assets/image (5).png" alt="" width="495"><figcaption><p>Blender Preferences: Add-ons.</p></figcaption></figure>

### Enable the Plugin <a href="#enabling-the-plugin" id="enabling-the-plugin"></a>

* Click in the Search bar at the top of the Preferences pane and search for _Motive_.
* Search will return the Motive Blender Plugin. Check the checkbox to enable it.&#x20;

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Enabling the Motive Blender Plugin from the Blender Preferences pane.</p></figcaption></figure>

* Once the plugin is successfully enabled, it appears as a tab in the Sidebar.

{% hint style="info" %}
If the Sidebar is not visible, click the small arrow (highlighted, below) in the upper right corner of the 3D Viewport, or use the hotkey "N" to toggle it open or closed.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Blender 3D Viewport with the Sidebar collapsed. </p></figcaption></figure>

## Motive Data Streaming Setup (Server) <a href="#motive-data-streaming-setup-server" id="motive-data-streaming-setup-server"></a>

Start by configuring the data streaming settings in Motive. Once configured and enabled, Motive broadcasts tracking data to the designated network interface where client applications can receive it.

The OptiTrack Blender Plugin is designed to configure the necessary streaming settings automatically. This section covers the Motive settings needed for the Plugin to work effectively.

<figure><img src="../../.gitbook/assets/image (9).png" alt="" width="491"><figcaption><p>Motive Application Settings: Streaming Pane. <br>Recommended settings for streaming to Blender.</p></figcaption></figure>

Click the <img src="../../.gitbook/assets/Control Deck - Streaming Off SMALL (2).png" alt="" data-size="line"> button in the right corner of the Control Deck to open the [Data Streaming Pane](https://docs.optitrack.com/motive/data-streaming) in Motive’s [Application Settings](../../motive-ui-panes/settings/) window. Configure the following settings:

* **Enable** - Toggle this setting on to enable streaming in Motive.
* **Local Interface** - This is the Local Host IP address. Motive is the Server and Blender is the client.&#x20;
  * When running Motive and Blender on the same machine, select loopback. This sets the IP address for both Server and Client to 127.0.0.1.
  * When streaming to a different PC, select the IP address that connects the Motive (server) computer to the network where the Blender (client) computer is located.&#x20;
* **Transmission type** - Set to _Multicast_. The Blender Plugin is currently unable to use Unicast.
* **Rigid Bodies**- Enable _Rigid Bodies_.
* **Skeleton coordinates** - Set to Global.
* **Bone Naming Convention** - Set to _FBX_.
* **Up Axis** - Set to _Y-Axis_. The plugin automatically converts the Up-Axis to the Z-axis.
* **Remote Trigger** - Keep this setting disabled.

Once these settings are configured correctly, prepare your live Motive session or a _Take_ to get ready to stream data into Blender.

{% hint style="warning" %}
Blender 1.0.0 only supports Rigid Body data.
{% endhint %}

## Blender Plugin Connection Setup

The Blender Plugin panel includes a Properties section for assigning assets.&#x20;

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption><p>The Motive Plugin Panel in Blender.</p></figcaption></figure>

### Apply Motive Streaming Data to Objects

#### Assign the Server IP and Client IP

* Server IP: enter the IP address for the Motive PC.
* Client IP: enter the IP address for the Blender PC.
* Enter 127.0.0.1 in both fields when Motive and Blender are running on the same computer.

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>IP settings.</p></figcaption></figure>

#### Set Transmission Type

The Motive Blender plugin works in Multicast only. Make sure that Multicast is set in both Blender and Motive, as [noted above](optitrack-blender-plugin.md#motive-data-streaming-setup-server). &#x20;

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Transmission settings.</p></figcaption></figure>

#### Update Blender Configuration (optional)

As needed, Blender settings can be changed in the plugin panel for the following settings:

* Unit System
* Unit Scale
* Frame Rate

Once changes are made, click the _Apply Configuration_ checkbox to override Blender's settings with those selected. Deselect the checkbox to revert settings back to Blender's default.&#x20;

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>Configuration settings.</p></figcaption></figure>

#### Start Connection

Select _Start Connection_ to obtain the data stream from Motive.&#x20;

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p>Connection options - not connected.</p></figcaption></figure>

When connected, the Connection settings will display the assets streaming from Motive. Assets will be labeled by _Streaming ID: Asset Name._

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption><p>Connection options - while connected.</p></figcaption></figure>

* Use the _Refresh Assets_ button to update the asset data after switching _Takes_ in Motive.&#x20;
* Click _Stop Connection_ to stop streaming data entirely.

### Assign Assets - Rigid Bodies <a href="#assigning-assets-rigid-bodies" id="assigning-assets-rigid-bodies"></a>

* Open the _Object Properties_ for the 3D Mesh you wish to link to the Rigid Body.
* In the _Motive: Assign Assets_ section, select the Rigid Body that you want to track with the mesh from the Cube dropdown list.

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption><p>3D Mesh properties: Motive: Assign Assets.</p></figcaption></figure>

* In the Motive plugin panel, select _Start Receiver._ The 3D Mesh will start ingesting the Rigid Body data directly from Motive.
* Use the Pause button to stop the data from streaming into the object, and the data will stop being written to the 3D mesh.

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption><p>Motive Rigid Body data streaming into Blender.<br>Click image to enlarge.</p></figcaption></figure>

## Using the Recorder

The Recorder function of the plugin allows you to plot keyframes on the tracked object in Blender's timeline. Keyframes will plot on the Location and Rotation Transform values of the object's properties.&#x20;

{% hint style="info" %}
Rotation values are plotted in Quaternion angles. Data can still be modified in post-processing in Blender using the rotation gizmo, which uses Euler angles.
{% endhint %}

### Recording <a href="#recording" id="recording"></a>

* Click the _Start Record_ button <img src="../../.gitbook/assets/image (19).png" alt="" data-size="original"> to begin recording.
* Keyframes will begin moving forward and plotting on the timeline.

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption><p>Blender timeline with plotted keyframes.</p></figcaption></figure>

* Click the _Stop_ button <img src="../../.gitbook/assets/image (21).png" alt="" data-size="original"> to stop plotting the key frames.

### Record a Frame Range <a href="#recording-a-frame-range" id="recording-a-frame-range"></a>

Use the _Record a Frame Range_ function when data needs to be recorded within a set time limit.&#x20;

* Check the box to toggle on the _Record Frame Range_ function. <img src="../../.gitbook/assets/image (22).png" alt="" data-size="original">
* Click _Select Frame Range,_ input the desired start and end frames to record within, and click OK.

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption><p>Select Frame Range to record in Blender.</p></figcaption></figure>

* Whenever this option is toggled on, Blender will record the data only within the selected Frame Range when recording is in progress.&#x20;
* Uncheck the box to toggle the _Record Frame Range_ function off.&#x20;

### Record Multiple Actions <a href="#recording-multiple-actions" id="recording-multiple-actions"></a>

The _Create New Action_ function allows you to record multiple actions in one Blender session. This function swaps the current action and keyframes in the timeline with a new action containing no keyframes. To start recording in the new timeline, click _Start Record_.

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption><p>The Create New Action button.</p></figcaption></figure>

### Managing Actions with Dope Sheet

The Dope Sheet Action Editor shows all of the Actions in the file.&#x20;

* Select the dropdown clock icon in the upper left of the Timeline window.&#x20;
* Select _Dope Sheet_ from the popup menu.

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption><p>Access the Dope Sheet in Blender.</p></figcaption></figure>

* In the _Mode_ dropdown, select _Action Editor_.

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption><p>Dope Sheet Mode selection.</p></figcaption></figure>

* Use the dropdown list in the upper middle of the Action Editor window to create and edit multiple actions within the same Blender session. If you would like to create new actions this way, click the ![](<../../.gitbook/assets/image (28).png>) button.&#x20;

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption><p>Available Actions in a Blender session.</p></figcaption></figure>

{% hint style="danger" %}
* The preferred method for making new actions is to use the “Create New Action” button in the plugin’s panel rather than creating them through the Action Editor.&#x20;
{% endhint %}

When moving to the next action, Click the _Delete Action_ button to remove all the key frames from the previous recorded action.&#x20;

<figure><img src="../../.gitbook/assets/Delete Action buttons.png" alt=""><figcaption><p>Delete Actions in Blender.</p></figcaption></figure>

## Access Help <a href="#note-for-maryanne-knight" id="note-for-maryanne-knight"></a>

The _Info_ section of the plugin includes linked buttons to access the OptiTrack website and the Blender documentation in our online user guide (coming in release 1.1). &#x20;

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption><p>The Info Panel in the <br>Motive Blender plugin.</p></figcaption></figure>
