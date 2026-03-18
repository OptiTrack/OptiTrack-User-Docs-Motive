# Motive Basics

Before diving into specific details, let’s begin with a brief overview of Motive. If you are new to using Motive, we recommend you to read through this page and learn about the basic tools, configurations and navigation controls, as well as instructions on managing capture files.

## File Management

In Motive, the recorded mocap data is stored in a file format called _Take (TAK)_, and multiple _Take_ files can be grouped within a session folder. The [Data pane](../motive-ui-panes/data-pane.md) is the primary interface for managing capture files in Motive. This pane can be accessed from the <img src="../.gitbook/assets/Motive Data Pane Button.png" alt="" data-size="line"> icon on the main [Toolbar](../motive-ui-panes/toolbar-command-bar.md), and it contains a list of session folders and the corresponding _Take_ files that are recorded or loaded in Motive.

Motive will save and load Motive-specific file formats including the _Take_ files (TAK), camera calibration files (CAL), and Motive user profiles (MOTIVE) that can contain most of the software settings as well as asset definitions for Skeletons and Rigid Body objects. Asset definitions are related to trackable objects in Motive which will be explained further in the [Rigid Body Tracking](rigid-body-tracking/) and [Skeleton Tracking](skeleton-tracking.md) page.

![Motive Data pane](<../.gitbook/assets/image (117).png>)

![Windows File Explorer. Click image to enlarge.](<../.gitbook/assets/image (813).png>)

### Take File (.TAK)

<figure><img src="https://v30.wiki.optitrack.com/images/7/7b/MotiveBasics_TAK.png" alt=""><figcaption></figcaption></figure>

Motive file management is centered on the _Take_ (TAK) file. A TAK file is a single motion capture recording (aka 'take' or 'trial'), which contains all the information necessary to recreate the entire capture from the file, including camera calibration, camera 2D data, reconstructed and labeled 3D data, data edits, solved joint angle data, tracking models (Skeletons, Rigid Bodies), and any additional device data (audio, force plate, etc.). A Motive Take (TAK) file is a completely self-contained motion capture recording, and it can be opened by another copy of Motive on another system.

{% hint style="danger" %}
Take files are forward compatible, but not backwards compatible. Meaning, if you record in Motive 3.x and try and play it back in Motive 2.x, Motive will throw an error. You can, however, record a Motive 2.x take and play it back in Motive 3.x.
{% endhint %}

{% hint style="info" %}
If you have any old recordings from Motive 1.7 or below, with BAK file extension, please import these recordings into Motive 2.0 version first and re-save them into TAK file format in order to use it in Motive version 3.0 or above.
{% endhint %}

### Session Folders

A Session is a file folder that allows the user to organize multiple similar takes (e.g. Monday, Tuesday, Wednesday, or StaticTrials, WalkingTrials, RunningTrials, etc). Whether you are planning the day's shoot or incorporating a group of _Takes_ mid-project, creating session folders can help manage complex sets of data. In the [Data pane](../motive-ui-panes/data-pane.md), you can import session folders that contain multiple _Takes_ or create a new folder to start a new capture session. For a most efficient workflow, plan the mocap session before the capture and organize a list of captures (shots) that need to be completed. Type _Take_ names in a spreadsheet or a text file, and copy and paste the list, which will automatically create empty Takes (shot list) with corresponding names from the pasted list.

Click the <img src="../.gitbook/assets/Data Pane - Data Mgmt Pane (1).png" alt="" data-size="line"> button on the toolbar at the bottom of the [Data pane](../motive-ui-panes/data-pane.md) to hide or expand the list of open Session Folders.&#x20;

<figure><img src="../.gitbook/assets/image (219).png" alt=""><figcaption><p>Data Pane with the Session Folder list open (left) and the current session's contents displayed (right).</p></figcaption></figure>

The active Session Folder is noted with a <img src="../.gitbook/assets/Data Pane - Flag for current folder (1).png" alt="" data-size="line"> flag icon. To switch to a different folder, left-click on the folder name in the Session list.&#x20;

Please refer to the [Session Folders](../motive-ui-panes/data-pane.md#list-of-session-folders) section of the Data pane page for more information on working with these folders.&#x20;

### Motive User Profile (.MOTIVE)

Software configurations are saved onto the motive profile (\*.motive) files. In the motive profile, all of the application-related configurations, lists of assets, and the loaded session folders are saved and preserved. You can export and import the profiles to easily maintain the same software configurations each time Motive is launched.

All of the currently configured software settings will get saved onto the `C:\ProgramData\OptiTrack\MotiveProfile.motive` file periodically throughout capture and when closing out of Motive. This file is the default application profile, and it gets loaded back when Motive is launched again. This allows all of the configurations to be persisted in between different sessions of Motive. If you wish to revert all of the settings to its factory default, use the _Reset Application Settings_ button under the _Edit_ tab of the main command bar.

Motive profiles can also be exported and imported from the _File_ menu of the main command bar. Using the profiles, you can easily transfer and persist Motive configurations among different instances and different computers.

**The followings are saved on application profile:**

* Application Settings
* Live Pipeline Settings
* Streaming Settings
* Synchronization Settings
* Export Settings
* Rigid Body & Skeleton assets
* Rigid Body & Skeleton settings
* Labeling settings
* Hotkey configurations

### Calibration files (CAL)

A calibration file is a standalone file that contains all of the required information to completely restore a calibrated camera volume, including positions and orientations of each camera, lens distortion parameters, and the camera settings. After a camera system is calibrated, CAL file can be exported and imported back again onto Motive when needed. Thus, it is recommended to save out the camera calibration file after each round of calibration.

Please note that reconstruction settings also get stored in the calibration file; just like how it gets stored in the MOTIVE profile. If the calibration file is imported after the profile file was loaded, it may overwrite the previous reconstruction settings as it gets imported.

Note that this file is reliable only if the camera setup has remained unchanged since the calibration. Read more from [Calibration](calibration/) page.

**The followings are saved on application profile:**

* Reconstruction settings
* Camera settings
* Position and orientation of the cameras
* Location of the global origin
* Lens distortion of each camera

{% hint style="info" %}
**Default System Calibration**

The default system calibration gets saved onto the `C:\ProgramData\OptiTrack\Motive\System Calibration.cal` file, and it gets loaded automatically at application startup to provide instant access to the 3D volume. This file also gets updated each time calibration is modified or when closing out of Motive.
{% endhint %}

## Viewports

In Motive, the main [viewport](../motive-ui-panes/viewport.md) is fixed at the center of the UI and is used for monitoring the 2D or 3D capture data in both live capture and playback of recorded data. The viewport can be set to either perspective view or camera view. The [Perspective View](../motive-ui-panes/viewport.md) mode shows the reconstructed 3D data within the calibrated 3D space, and the [Camera View](../motive-ui-panes/viewport.md) mode shows 2D images from each camera in the setup. These modes can be selected from the drop-down menu at the top-right corner, and both of these views are essential for assessing and monitoring the tracking data.

![Selecting viewport mode from the drop-down menu.](<../.gitbook/assets/image (169).png>)

### Perspective View - 3D

* Use the dropdown menu at the top-left corner to switch into the Perspective View mode. You can also use the number 1 hotkey while on a viewport.
* Used to look through the reconstructed 3D representation of the capture, analyze marker positions, rays used in reconstruction, etc.
* The context menu in the Perspective View allows you to access more options related to the markers and assets in 3D tracking data.

![](<../.gitbook/assets/image (108).png>)

### Camera Preview - 2D

* Use the dropdown menu at the top-left corner to switch into the Camera View mode. You can also use the number 2 hotkey while on a viewport.
* Each camera’s view can be accessed from the [Camera Preview pane](../motive-ui-panes/viewport.md). It displays the images that are being transmitted from each camera. The image processing modes are displayed, including grayscale and object.
* Detected IR lights and/or reflections are also shown in this pane. Only the IR lights that satisfy the object filters get considered as markers.
* From the Camera Preview pane, you can [mask](calibration/) certain pixel regions to exclude them from the process.

![](<../.gitbook/assets/image (184).png>)

### Additional Viewports

* When needed, the viewport can be split into 4 different smaller views. This can be selected from the menu at the top-right corner of the viewport. You can use the hotkeys (Shift + 4) to do this also.
* When needed, an additional Viewer pane can be opened under the [View tab](../motive-ui-panes/toolbar-command-bar.md) or by clicking the <img src="../.gitbook/assets/Motive ViewPort Button.png" alt="" data-size="line"> icon on the main toolbar.

![Main viewport split into 4 different views](<../.gitbook/assets/image (165).png>) ![Options for splitting the view](<../.gitbook/assets/image (780).png>)

## Basic Navigation Controls

{% hint style="info" %}
Most of the navigation controls in Motive are customizable, including both mouse and [Hotkey](motive-hotkeys.md) controls. The Hotkey Editor Pane and the Mouse Control Pane under the Edit tab allow you to customize mouse navigation and keyboard shortcuts to common operations.
{% endhint %}

### View Port Mouse Control

Mouse controls in Motive can be customized from the [application settings panel](../motive-ui-panes/settings/settings-mouse-and-keyboard.md) to match your preference. Motive also includes a variety of common mouse control presets so that any new users can easily start controlling Motive. Available preset control _profiles_ include Motive, Blade, Maya, and Visual3D. The following table shows a few basics actions that are commonly used for navigating the viewports in Motive.

![Mouse actions can be customized from the application settings panel.](<../.gitbook/assets/image (190).png>)

| Function                 | Default Control             |
| ------------------------ | --------------------------- |
| Rotate view              | Right + Drag                |
| Pan view                 | Middle (wheel) click + drag |
| Zoom in/out              | Mouse Wheel                 |
| Select in View           | Left mouse click            |
| Toggle Selection in View | CTRL + left mouse click     |

### Hotkeys

Using the Hotkeys can speed up workflows. Most of the default hotkeys are listed on the [Motive Hotkeys](motive-hotkeys.md) page. When needed, the hotkeys can also be customized from the application settings panel which can be accessed under the Edit tab. Various actions can be assigned with a custom hotkey using the Hotkey Editor.

![](<../.gitbook/assets/image (816).png>)

## Control Deck

The [Control Deck](../motive-ui-panes/control-deck.md) is always docked at the bottom of Motive, and it provides both recording and navigation controls over Motive's two primary operating modes: Live mode and Edit mode.

![Live Mode](<../.gitbook/assets/image (172).png>)

![Edit Mode](<../.gitbook/assets/image (123).png>)

### Live Mode and Edit Mode

<img src="../.gitbook/assets/image (182).png" alt="" data-size="line">Switching to Live Mode in Motive using the control deck.

In the **Live Mode**, all cameras are active and the system is processing camera data. If the mocap system is already calibrated, Motive is live-reconstructing 2D camera data into labeled and unlabeled 3D trajectories (markers) in [real-time](data-recording/data-types.md). The live tracking data can be streamed to other applications using the [data streaming](data-streaming.md) tools or the NatNet SDK. Also, in Live mode, the system is ready for recording and corresponding capture controls will be available in the [Control Deck](../motive-ui-panes/control-deck.md).

In the **Edit Mode**, the cameras are not active, and Motive is processing loaded _Take_ file (pre-recorded data). The playback controls will be available in the control deck, and the small timeline will appear at the top of the control deck for scrubbing through the recorded frames. In this mode, you can review the recorded 3D data from the TAK and make post-processing [edits](data-editing.md) and/or manually assign marker [labels](labeling.md) to the recorded trajectories before [exporting](data-export/) out the tracking data. Also, when needed, you can switch to the [2D mode](reconstruction-and-2d-mode.md), and view the real-time reconstructed 3D data to understand how the 3D data was obtained and perform post-processing reconstruction pipeline to re-obtain a new set of 3D data.

{% hint style="info" %}
**Hotkeys:** "Shift + \~" is the default hotkey for toggling between Live and Edit modes in Motive.
{% endhint %}

## Graph View pane

The [Graph View pane](../motive-ui-panes/graph-view-pane.md) is used for plotting live or recorded channel data in Motive. For example, 3D coordinates of the reconstructed markers, 3D positions and orientations of Rigid Body assets, force plate data, analog data from data acquisition devices, and more can be plotted on this pane. You can switch between existing layouts or create a custom layout for plotting specific channel data.

Basic navigation controls are highlighted below. For more information, read through the [Graph View pane](../motive-ui-panes/graph-view-pane.md) page.

![](<../.gitbook/assets/image (139).png>)

### Basic Navigation Controls

#### On the Graph

**Navigate Frames (Alt + Left-click + Drag)**

Alt + left-click on the graph and drag the mouse left and right to navigate through the recorded frames. You can do the same with the mouse scroll as well.

**Panning (Scroll-click + Drag)**

Scroll-click and drag to pan the view vertically and horizontally throughout plotted graphs. Dragging the cursor left and right will pan the view along the horizontal axis for all of the graphs. When navigating vertically, scroll-click on a graph and drag up and down to pan vertically for the specific graph.

**Zooming (Right-click + Drag)**

Right-click and drag on a graph to free-form zoom in and out on both vertical and horizontal axis. If the _Autoscale Graph_ [![Graph Autoscale 20.png](https://v30.wiki.optitrack.com/images/7/79/Graph_Autoscale_20.png)](https://v30.wiki.optitrack.com/index.php?title=File:Graph_Autoscale_20.png) is enabled, the vertical axis range will be fixed according to the max and min value of the plotted data.

{% hint style="info" %}
**Other Ways to Zoom:**

* Press "Shift + F" to zoom out to the entire frame range.
* Zoom into a frame range by Alt + right-clicking on the graph and selecting the specific frame range to zoom into.
* When a frame range is selected, press "F" to quickly zoom onto the selected range in the timeline.
{% endhint %}

**Selecting Frame Range (Left-click + Drag)**

The frame range selection is used when making post-processing edits on specific ranges of the recorded frames. Select a specific range by left-clicking and dragging the mouse left and right, and the selected frame ranges will be highlighted in yellow. You can also select more than one frame ranges by shift-selecting multiple ranges.

### On the Navigation Bar

**Navigate Frames (Left-click)**

Left-click and drag on the nav bar to scrub through the recorded frames. You can do the same with the mouse scroll as well.

**Pan View Range**

Scroll-click and drag to pan the view range range.

**Frame Range Zoom**

Zoom into a frame range by re-sizing the scope range using the navigation bar handles. You can also easily do this by **Alt + right-clicking** on the graph and selecting a specific range to zoom into.

### Navigation Bar

![Navigation bar at the bottom of the Graph View pane.](<../.gitbook/assets/image (150).png>)

**Working Range / Playback range**

The working range (also called the playback range) is both the view range and the playback range of a corresponding _Take_ in Edit mode. Only within the working frame range, recorded tracking data will be played back and shown on the graphs. This range can also be used to output a specific frame ranges when exporting tracking data from Motive.

The working range can be set from different places:

* In the navigation bar of the Graph View pane, you can drag the handles on the scrubber to set the working range.
* You can also use the navigation controls on the Graph View pane to zoom in or zoom out on the frame ranges to set the working range.
* Start and end frames of a working range can also be set from the [Control Deck](../motive-ui-panes/control-deck.md) when in the Edit mode.

**Selection Range**

The selection range is used to apply post-processing edits only onto a specific frame range of a Take. Selected frame range will be highlighted in yellow on both Graph View pane as well as Timeline pane.

**Gap indication**

When playing back a recorded capture, the red colors on the navigation bar indicate the amount of occlusions from labeled markers. Brighter red means that there are more markers with labeling gaps.

## Application Settings

The [Application Settings](../motive-ui-panes/settings/) can be accessed under the _Edit tab_ or by clicking the [![Toolbar AppSettings 20.png](https://v30.wiki.optitrack.com/images/8/8e/Toolbar_AppSettings_20.png)](https://v30.wiki.optitrack.com/index.php?title=File:Toolbar_AppSettings_20.png) icon on the main toolbar.

This pane is used for configuring application-wide settings, which include startup configurations, display options for both 2D and 3D viewports, settings for asset creation, and most importantly, live-pipeline parameters for the **Solver** and the **2D Filter** settings for the cameras. The _Cameras_ tab includes the 2D filter settings that basically determine which reflections gets considered as marker reflections on the camera views, and the _Solver_ setting determines which 3D markers get reconstructed in the scene from a group of marker reflections from all of the cameras. References for the available settings are documented in the [Application Settings](../motive-ui-panes/settings/) page.

{% hint style="info" %}
If you wish to reset the default application setting, go to Reset Application Settings under the Edit tab.
{% endhint %}

**Solver Settings**

Under the [Solver tab](../motive-ui-panes/settings/settings-live-pipeline.md), you can configure a real-time solver engine. These settings, including the trajectorizer settings, are one of the most important settings in Motive. These settings determine how 3D coordinates are acquired from the captured 2D camera images and how they are used for tracking Rigid Bodies and Skeletons. Thus, understanding these settings is very important for optimizing the system for the best tracking results.

**Camera Settings**

Under the [Camera tab](../motive-ui-panes/settings/settings-live-pipeline.md), you can configure the 2D Camera filter settings (circularity filter and size filter) as well as other display options for the cameras. The 2D Camera filter setting is one of the key settings for optimizing the capture. For most applications, the default settings work well, but it is still beneficial to understand some of the core settings in order for more efficient control over the camera system.

For more information, read through the [Application Settings: Live Pipeline](../motive-ui-panes/settings/settings-live-pipeline.md) page and the [Reconstruction and 2D Mode](reconstruction-and-2d-mode.md)

## Layouts

The UI layout in Motive is customizable. All panes can be docked and undocked from the UI. Each pane can be positioned and organized by drag-and-drop using the on-screen docking indicators. Panes may float, dock, or stack. When stacked together, they form a tabbed window for quickly cycling through. Layouts in Motive can be saved and loaded, allowing a user to switch quickly between default and custom configurations suitable for different needs. Motive has preset layouts for Calibration, Creating a Skeleton, Capturing (Record), and Editing workflows. Custom layouts can be created, saved, and set as default from the Main Menu -> 'Layout' menu item. Quickly restore a particular layout from the Layout menu, the Layout Dropdown at the top right of the Main Menu, or via HotKeys.

{% hint style="info" %}
**Note:** Layout configurations from Motive versions older than 2.0 cannot be loaded in latest versions of Motive. Please re-create and update the layouts for use.
{% endhint %}

![Docking indicator](<../.gitbook/assets/image (755).png>) ![Motive layout options](<../.gitbook/assets/image (763).png>)
