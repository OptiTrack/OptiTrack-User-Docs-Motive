---
description: Everything you need to know to move around the Motive interface.
---

# Motive Basics

This page provides an overview of Motive's tools, configurations, navigation controls, and instructions on managing capture files. Links to more detailed instructions are included.

## File Management

In Motive, motion capture recordings are stored in the _Take (.TAK)_ file format in folders known as session folders.&#x20;

The [Data pane](../motive-ui-panes/data-pane.md) is the primary interface for managing capture files. Open the Data pane by clicking the <img src="../.gitbook/assets/Motive Data Pane Button.png" alt="" data-size="line"> icon on the main [Toolbar](../motive-ui-panes/toolbar-command-bar.md) to see a list of session folders and the corresponding _Take_ files that are recorded or loaded in Motive.&#x20;

### Take Files (.TAK)

A .TAK file is a single motion capture recording (aka 'take' or 'trial'), which contains all the information necessary to recreate the entire capture, including camera calibration, camera 2D data, reconstructed and labeled 3D data, data edits, solved joint angle data, tracking models (Skeletons, Rigid Bodies, Trained Markersets), and any additional device data (audio, force plate, etc.). A Motive _take_ (.TAK) file is a completely self-contained motion capture recording, that can be opened by another copy of Motive on another system.

{% hint style="danger" %}
_Take_ files are forward compatible, but not backwards compatible, meaning you can play a take recorded in an older version of Motive in a newer version but not the other way around.&#x20;

For example, if you try to play a _take_ in Motive 2.x that was record in Motive 3.x, Motive will return an error. You can, however, record a Motive 2.x _take_ and play it back in Motive 3.x.
{% endhint %}

{% hint style="info" %}
If you have old recordings from Motive 1.7 or below, with .BAK file extensions, import them into Motive 2.0 and re-save them into the .TAK file format to open them in Motive versions 3.0 and above.
{% endhint %}

### Session Folders

The folder where _take_ files are stored is known as a session folder in Motive. Session folders allow you to plan shoots, organize multiple similar takes (e.g. Monday, Tuesday, Wednesday, or Static Trials, Walking Trials, Running Trials, etc.) and manage complex sets of data within Motive or Windows.

For a most efficient workflow, plan the mocap session before the capture and organize a list of captures (shots) to be completed. Type the _take_ names in a spreadsheet or a text file, then copy and paste the list into the data pane. This will create empty _takes_ (a shot list) with corresponding names from the pasted list.

Click the <img src="../.gitbook/assets/Data Pane - Data Mgmt Pane (1).png" alt="" data-size="line"> button on the toolbar at the bottom of the [Data pane](../motive-ui-panes/data-pane.md) to hide or expand the list of open Session Folders.&#x20;

<figure><img src="../.gitbook/assets/Data Pane - Session folders and Takes.png" alt=""><figcaption><p>Data Pane with the Session Folder list open (left) and <br>the current session's contents displayed (right).</p></figcaption></figure>

Alternately, with the session folder list closed, click the name of the current session folder in the top left corner for a quick selection.&#x20;

<figure><img src="../.gitbook/assets/Data Pane - change session folder.png" alt=""><figcaption><p>Quickly change session folder.</p></figcaption></figure>



The active Session Folder is noted with a <img src="../.gitbook/assets/Data Pane - Flag for current folder (1).png" alt="" data-size="line"> flag icon. To switch to a different folder, left-click the folder name in the Session list.&#x20;

Please refer to the [Session Folders](../motive-ui-panes/data-pane.md#list-of-session-folders) section of the Data pane page for more information on working with these folders.&#x20;

### Motive User Profile (.MOTIVE)

Software configuration settings are saved in the motive profile (\*.motive) file, located by default at:

`C:\ProgramData\OptiTrack\MotiveProfile.motive`

The profile includes application-related settings, asset definitions, and the open session folders. The file is updated as needed during a Motive session and at exit, and loads again the next time Motive is launched.&#x20;

**The profile includes:**

* Application Settings
* Live Pipeline Settings
* Streaming Settings
* Synchronization Settings
* Export Settings
* Rigid Body & Skeleton assets
* Rigid Body & Skeleton settings
* Labeling settings
* Hotkey configuration

{% hint style="info" %}
Profile files can be exported and imported, to maintain the same software configuration and asset definitions. This is helpful when the profile is specific to a project and the configuration and assets need to be used on different computers or saved for future use.&#x20;

Please see the [Export Assets Definition](data-export/#export-assets-definition) section of the [Data Export](data-export/) page for more details.&#x20;
{% endhint %}

#### Reset Settings

To revert all settings to Motive factory defaults, select _Reset Application Settings_ from the _Edit_ menu.

<figure><img src="../.gitbook/assets/Edit Menu with Reset settings Selected (1).png" alt=""><figcaption><p>Edit Menu - Reset Settings.</p></figcaption></figure>

### Calibration files (.CAL)

A calibration file is a standalone file that contains all the required information to restore a calibrated camera volume, including the position and orientation of each camera, lens distortion parameters, and  camera settings. After a camera system is calibrated, the .CAL file can be exported and imported back into Motive again when needed. For this reason, we recommend saving the camera calibration file after each round of calibration.

{% hint style="warning" %}
Reconstruction settings are also stored in the calibration file, in addition to the .MOTIVE profile. If the calibration file is imported after the profile file is loaded, the calibration may overwrite the previous reconstruction settings during import.
{% endhint %}

Note that an imported .CAL file is reliable only if the camera setup has remained unchanged since the calibration. Read more from the [Calibration](calibration/) page.

**The calibration file includes:**&#x20;

* Reconstruction settings
* Camera settings
* Position and orientation of the cameras
* Location of the global origin
* Lens distortion of each camera

{% hint style="info" %}
**Default System Calibration**

The default system calibration is saved at: `C:\ProgramData\OptiTrack\Motive\System Calibration.cal`&#x20;

This file is loaded at startup to provide instant access to the 3D volume. The .CAL file is updated each time the calibration is modified or when closing out of Motive.
{% endhint %}

## Viewports

In Motive, the main [viewport](../motive-ui-panes/viewport.md) is fixed at the center of the UI and is used to monitor the 2D or 3D capture data in both live capture and playback of recorded data. The viewports can be set to either [Perspective View](../motive-ui-panes/viewport.md#perspective-view), which shows the reconstructed 3D data within the calibrated 3D space, or [Cameras View](../motive-ui-panes/viewport.md#cameras-view), which shows 2D images from each camera in the system. These views can be selected from the drop-down menu at the top-right corner. By default, the Perspective View opens in the top pane and the Cameras view opens in the bottom pane. Both views are essential for assessing and monitoring the tracking data.

![Selecting viewport mode from the drop-down menu.](<../.gitbook/assets/image (542).png>)

### Perspective View - 3D

* Click on any viewport window and use the hotkey **1** to quickly switch to the [Perspective view](../motive-ui-panes/viewport.md#perspective-view).
* Displays the reconstructed 3D representation of the capture.
* Used to analyze marker positions, view rays used in reconstruction, create assets, etc.&#x20;
* The Visual Aids menu <img src="../.gitbook/assets/Viewport Visual Options button (9).png" alt="" data-size="line"> allows you to select which data to display.

![](<../.gitbook/assets/image (707).png>)

### Cameras View - 2D

* Click on any viewport window and use the hotkey **2** to quickly switch to the [Cameras View](../motive-ui-panes/viewport.md#cameras-view).&#x20;
* This view displays the images transmitted from each camera, with a header that shows the camera's Video Mode (Object, Precision, Grayscale, or MJPEG) and resolution.&#x20;
* Detected IR lights and reflections also show in this pane. Only IR lights that satisfy the object filters are identified as markers. See [Cameras Basic Settings](../motive-ui-panes/settings/settings-live-pipeline.md#cameras-basic-settings) in the [Settings: Live Pipeline](../motive-ui-panes/settings/settings-live-pipeline.md) page for more detail on object filters.
* Includes tools to report camera information, inspect pixels, troubleshoot markers, and mask pixel regions to exclude them from processing. See [Cameras View](../motive-ui-panes/viewport.md#cameras-view) in the [Viewport](../motive-ui-panes/viewport.md) page for more details.

![](<../.gitbook/assets/image (781).png>)

### Additional Viewports

* When needed, the Viewport can be split into 3 or 4 smaller views. Click the <img src="../.gitbook/assets/Motive Context Menu (27).png" alt="" data-size="line"> in the top-right corner of the viewport to open the Viewport context menu to select additional panes or different layouts. You can also use the hotkey **Shift + 4** to open the four pane layout.
* When needed, additional Viewer panes can be opened from the [View menu ](../motive-ui-panes/toolbar-command-bar.md)or by clicking the ![](<../.gitbook/assets/Motive ViewPort Button (1).png>) icon on the main toolbar.

![Main viewport split into 4 different views](<../.gitbook/assets/image (764).png>) ![Options for splitting the view](<../.gitbook/assets/image (511).png>)

## Viewport Navigation Controls

{% hint style="info" %}
Most of the navigation controls in Motive are customizable, including mouse and [Hotkey](motive-hotkeys.md) controls. The Hotkey Editor Pane and the Mouse Control Pane under the Edit tab allow you to customize mouse navigation and keyboard shortcuts to common operations.
{% endhint %}

### Viewport Mouse Control

Mouse controls in Motive can be customized from the Mouse tab in [application settings panel](../motive-ui-panes/settings/settings-mouse-and-keyboard.md) to match your preference. Motive also includes common mouse control presets for Motive (the default), Blade, Maya, MotionBuilder and Visual3D applications. Click the <img src="../.gitbook/assets/Settings button (11).png" alt="" data-size="line"> button to open the Settings panel.&#x20;

![Mouse settings can be customized from the application settings panel.](<../.gitbook/assets/Settings - Mouse.png>)

The table below lists basic actions that are commonly used for navigating the viewports in Motive:

| Function                 | Default Control             |
| ------------------------ | --------------------------- |
| Rotate view              | Right + Drag                |
| Pan view                 | Middle (wheel) click + drag |
| Zoom in/out              | Mouse Wheel                 |
| Select in View           | Left mouse click            |
| Toggle Selection in View | CTRL + left mouse click     |

### Hotkeys

Hotkeys speed up workflows. See all the defaults on the [Motive Hotkeys](motive-hotkeys.md) page. To create custom hotkeys, save or import a keyboard preset, click the <img src="../.gitbook/assets/Settings button (11).png" alt="" data-size="line"> button to open the Settings panel.&#x20;

![Keyboard settings.](<../.gitbook/assets/Settings - Keyboard.png>)

## Control Deck

The [Control Deck](../motive-ui-panes/control-deck.md) is always docked at the bottom of Motive, providing both recording and navigation controls over Motive's two operating modes: Live and Edit.

&#x20;The <img src="../.gitbook/assets/Live or Edit mode (1).png" alt="" data-size="line"> button at the far left of the Control Deck switches between Live and Edit mode, with the active mode shown in cyan. Hotkey _**Shift + \~**_ toggles between Live and Edit modes.&#x20;

{% hint style="info" %}
When using a timecode generator, you can control where the timecode data is displayed, either in the 3D view (default), in the Control Deck, or not shown at all.&#x20;

From the Applications Settings panel, select [_Views -> 3D -> Heads Up Display -> Timecode_](../motive-ui-panes/settings/settings-views.md#heads-up-display).
{% endhint %}

### Live Mode

* All cameras are active and the system is processing camera data.
* If the system is calibrated, Motive live-reconstructs 2D camera data into labeled and unlabeled 3D trajectories (markers) in [real-time](data-recording/data-types.md).&#x20;
* Live tracking data can stream to other applications using the [data streaming](data-streaming.md) tools or the NatNet SDK.
* The system is ready for recording. Capture controls are available in the [Control Deck](../motive-ui-panes/control-deck.md).

![Live Mode](<../.gitbook/assets/image (827).png>)

### Edit Mode

* Used for processing a loaded _Take_ file (pre-recorded data). Cameras are not active.&#x20;
* Playback controls are available in the Control Deck, including a timeline (in green) at the top of the control deck for scrubbing through the recorded frames.&#x20;
* Review recorded 3D data from the _Take_ file, make post-processing [edits](data-editing.md) and manually assign marker [labels](labeling.md) to the recorded trajectories before [exporting](data-export/) the tracking data.&#x20;
*

    ![Edit Mode](<../.gitbook/assets/image (798).png>)
* When needed, you can switch from editing in 3D to [2D mode](reconstruction-and-2d-mode.md), to view the real-time unreconstructed 3D data. Use this to perform a post-processing reconstruction pipeline to re-obtain a new set of 3D data.

<figure><img src="../.gitbook/assets/Live or Edit mode - switch to 2D (3).png" alt="" width="200"><figcaption><p>Click the Edit button to <br>switch to Edit 2D mode.</p></figcaption></figure>

## Graph View pane

The [Graph View pane](../motive-ui-panes/graph-view-pane.md) is used to plot live or recorded channel data. There are many uses cases for plotting data in Motive; examples include tracking 3D coordinates of the reconstructed markers, 3D positions and orientations of Rigid Body assets, force plate data, analog data from data acquisition devices, and many more.&#x20;

![The Graph View Pane, with Channel View selected.](<../.gitbook/assets/image (697).png>)

You can switch between existing layouts or create a custom layout for plotting specific channel data.

Basic navigation controls are highlighted below. For more information on graphing data in Motive, please read the [Graph View pane](../motive-ui-panes/graph-view-pane.md) page.

### Graph View Navigation Controls

#### **Navigate Frames (Alt + Left-click + Drag )**

Hold the Alt key while left-clicking and dragging the mouse left or right over the graph to navigate through the recorded frames. You can use the mouse scroll also.

#### **Pan (Scroll-click + Drag)**

Scroll-click and drag to pan the view vertically and horizontally throughout plotted graphs. Dragging the cursor left and right pans the view along the horizontal axis for all of the graphs. When navigating vertically, scroll-click on a graph and drag up and down to also pan vertically.

#### **Zoom (Right-click + Drag)**

Right-click and drag on a graph to zoom in and out on both vertical and horizontal axis. If _Autoscale Graph_ <img src="../.gitbook/assets/Graph Pane - Auto Extent graphs.png" alt="" data-size="line"> is enabled, the vertical axis range will be fixed according to the max and min values of the plotted data.

{% hint style="info" %}
**Other Ways to Zoom:**

* Press **Shift + F** to zoom out to the entire frame range.
* Zoom to a frame range by **Alt + right-clicking** the graph and selecting the specific frame range to zoom to.
* When a frame range is selected in the timeline, press **F** to quickly zoom to it.
{% endhint %}

#### **Select Frame Range (Left-click + Drag)**

Frame range selection is used when making post-processing edits on specific ranges of the recorded frames. Select a specific range by left-clicking and dragging the mouse left and right, and the selected frame ranges will be highlighted in yellow. You can also select more than one frame ranges by holding the shift key while selecting multiple ranges.

### Graph View Navigation Bar

The Navigation Bar at the bottom of the Graph View pane can also be used to&#x20;

![The Graph View pane Navigation Bar.](<../.gitbook/assets/image (839).png>)

#### **Navigate Frames (Left-click)**

Left-click and drag on the navigation bar to scrub through the recorded frames. You can use the mouse scroll also.

#### **Pan View Range**

Scroll-click and drag to pan the view range.

#### **Frame Range Zoom**

Zoom to a frame range by re-sizing the scope range using the navigation bar handles. As noted above, you can also do this by pressing **Alt + right-clicking** on the graph to select the range to zoom to.

#### **Working Range / Playback range**

The working range (also called the playback range) is both the view range and the playback range of a corresponding _Take_ in Edit mode. In playback, only the working range will play, and in the Graph View pane, only the data for the working range will display.&#x20;

{% hint style="info" %}
**Tip:** Use the working range to limit exported tracking data to a specific range.&#x20;
{% endhint %}

The working range can be set from different places:

* In the navigation bar of the Graph View pane, drag the handles on the scrubber.
* Use the navigation controls on the Graph View pane to zoom in or zoom out on the desired range.
* Enter the start and end frames of the working range in the <img src="../.gitbook/assets/Control Deck - Working Range manual entry.png" alt="" data-size="line"> fields in the [Control Deck](../motive-ui-panes/control-deck.md).

#### **Selection Range**

The selection range is used to apply post-processing edits only to a specific frame range of a _Take_. The selected frame range is highlighted in yellow on both Graph View pane and the Control Deck Timeline.

#### **Gap Indication**

When playing back a recorded capture, red marks on the navigation bar indicate areas with occlusions of labeled markers. Brighter colors indicate a greater number of markers with labeling gaps.

## Application Settings

Motive's [Application Settings](../motive-ui-panes/settings/) panel holds application-wide settings, including:

* Startup configuration and display options for both 2D and 3D viewports.&#x20;
* Settings for asset creation.
* &#x20;Live-pipeline parameters for the **Solver** and the **2D Filter** settings for the cameras.&#x20;
  * The _Cameras_ tab includes the 2D filter settings that determine which reflections are classified as marker reflections on the camera views. &#x20;
  * The _Solver_ settings determine which 3D markers are reconstructed in the scene from the group of marker reflections from all the cameras.&#x20;

Access Application Settings from the _Edit_ menu or by clicking the <img src="../.gitbook/assets/Settings button (12).png" alt="" data-size="line"> icon on the main toolbar. Read more about all of the available settings on the [Application Settings](../motive-ui-panes/settings/) pages.&#x20;

{% hint style="info" %}
To reset all application settings to Motive defaults, select _Reset Application Settings_ from the _Edit_ menu.
{% endhint %}

### **Live Pipeline > Solver Settings**

The [Solver tab](../motive-ui-panes/settings/settings-live-pipeline.md) on the Live Pipeline settings panel configures the real-time solver engine. These are some of the most important settings in Motive as they determine how 3D coordinates are acquired from the captured 2D camera images and how they are used for tracking Rigid Bodies and Skeletons. Understanding these settings is very important for optimizing the system for the best tracking results.

### **Live Pipeline > Camera Settings**

Under the [Camera tab](../motive-ui-panes/settings/settings-live-pipeline.md), you can configure the 2D Camera filter settings (circularity filter and size filter) as well as other display options for the cameras. The _2D Camera filter_ setting is a key setting for optimizing the capture.&#x20;

For most applications, the default settings work well, but it is still helpful to understand these core settings for more efficient control over the camera system.

{% hint style="info" %}
For more information, read through the [Application Settings: Live Pipeline](../motive-ui-panes/settings/settings-live-pipeline.md) page and the [Reconstruction and 2D Mode](reconstruction-and-2d-mode.md).
{% endhint %}

## Layouts

#### Predefined Layouts

Motive includes several predefined layouts suited to various workflow activities. Access them from the Layout menu, or use the buttons in the top right corner of the screen.&#x20;

<div><figure><img src="../.gitbook/assets/Layout menu.png" alt=""><figcaption><p>Layout menu.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Layout shortcut buttons (2).png" alt=""><figcaption><p>Layout buttons - with a custom layout.</p></figcaption></figure></div>

#### Customized Layouts

The User Interface (UI) layout in Motive is highly customizable.&#x20;

* Select the desired panes from the View menu or from the standard toolbar.
* All panes can be undocked to float, dock elsewhere, or stack with other panes with a simple drag-and-drop.&#x20;
* Reposition panes using on-screen docking guides: &#x20;

<figure><img src="../.gitbook/assets/Dock pane options.png" alt=""><figcaption><p>Docking guides to reposition a pane.</p></figcaption></figure>

* Drag-and-drop the pane over the icon for the desired position. To have the pane float, drop it away from the docking guides.
* Stacked panes form a tabbed window. The option to stack is only available when dragging a pane over another stackable pane.
* &#x20;Custom layouts can be saved and loaded again, allowing a user to easily switch between default and custom configurations suitable for different needs.&#x20;
  * Select _Create Layout..._ from the _Layout_ menu to save your custom layout.
  * The custom layout will appear in the selection list to the left of the Layout buttons. &#x20;
* Custom layouts can also be accessed using [HotKeys](motive-basics.md#hotkeys), with **Ctrl+6** through **Ctrl+9** set for user layouts by default.&#x20;

{% hint style="info" %}
**Note:** Layout configurations from Motive versions older than 2.0 cannot be loaded in latest versions of Motive. Please re-create and update the layouts for use.
{% endhint %}
