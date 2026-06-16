---
description: This page provides an overview of the recording process in Motive.
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/data-recording
---

# Data Recording

## Overview

Camera data captured in Motive can be streamed live to other applications or recorded into the _Take_ file (.tak) file format.  Once recorded, data can be exported from the _Take._ The _Take_ can also be edited and streamed into other applications.&#x20;

A Take file includes:

* 2D Motion Capture data.&#x20;
* 3D Solved data.
* Reference video, if included during the capture.&#x20;

## Preparing to Record

Before you begin recording, make sure the following items are completed:

* [ ] The OptiTrack camera system is properly installed, with each camera focused and aimed for the best capture experience. Please see the [Installation and Activation page](../installation-and-activation.md) for more details.
* [ ] The camera system is fully calibrated. Please see the [Calibration page](../calibration/) for more details.&#x20;
* [ ] Markers have been applied to all Rigid Body and Trained Markerset assets required in the shoot. For more information about working with these assets, please see the [Rigid Body Tracking page](../rigid-body-tracking/), the [Trained Markersets page](../trained-markersets.md), and the [IMU Sensor Fusion page](/broken/pages/ysdyrsuQyF9qn6xMu4ix). &#x20;
* [ ] All actors are suited up with markers for the appropriate skeleton markerset. For more information about tracking human movement, please see the [Skeleton Tracking page](../skeleton-tracking.md), the [Builder Pane page](../../motive-ui-panes/builder-pane.md) for information about creating and modifying skeletons, and the [Skeleton Marker Sets](../../markersets/) collection of pages for diagrams and details for each of the available skeleton markersets.&#x20;

Once these items are completed, you are ready to capture _Takes_.&#x20;

{% hint style="info" %}
You can create Skeleton and Rigid Body assets in Live mode prior to recording. Trained Markerset assets require recorded data to capture the asset's full range of motion. These assets are best created in Edit mode, then copied into Live for use in additional captures. &#x20;
{% endhint %}

For real-time tracking applications, please see the [Data Streaming](../data-streaming.md) page.

### Live Mode and Edit Mode

Motive has two modes: **Live** and **Edit.** The Control Deck contains the operations for recording or playback, depending on which mode is active. Toggle between the two by selecting one from the <img src="../../.gitbook/assets/Live or Edit mode.png" alt="" data-size="line"> button on the Control Deck or by using the _Shift + \~_ hotkey.&#x20;

{% hint style="info" %}
**Tip:** Prime series cameras will illuminate in blue when in live mode, in green when recording, and are turned off in edit mode. See more at [Camera Status Indicators](../../hardware/camera-status-indicators.md).
{% endhint %}

#### **Live Mode**

Live mode is used when recording new _Takes_ or when streaming a live capture. In this mode, all enabled cameras continuously capture 2D images and reconstruct the detected reflections into 3D data in real-time.

![The Motive Viewport and Control Deck in Live Mode.](<../../.gitbook/assets/image (438).png>)

**Edit Mode**

Edit Mode is used for playback of captured _Take_ files. In this mode, you can playback or stream recorded data and complete post-processing tasks.

![The Motive Viewport and Control Deck in Edit Mode](<../../.gitbook/assets/image (929).png>)

### Control Deck

Recording (Live) and playback (Edit) functions are located on the [Control Deck](../../motive-ui-panes/control-deck.md) at the bottom of the Motive screen. Toggle between the two by selecting one from the <img src="../../.gitbook/assets/Live or Edit mode.png" alt="" data-size="line"> button on the Control Deck or by using the _Shift + \~_ hotkey.&#x20;

#### Live Mode

When in Live mode, the Control Deck provides controls to:

* Change the _Take_ name from the default.
* Start or stop recording.
* [Delay recording](./#recording-delay).&#x20;
* Record for a preset duration of time, or until manually stopped.

![The Control Deck in LIVE mode.&#x20;
Click image to enlarge.](<../../.gitbook/assets/Control Deck - LIVE Mode Annotated (1).png>)

#### Edit Mode

<figure><img src="../../.gitbook/assets/Control Deck - Edit Mode Annotated (6).png" alt=""><figcaption><p>The Control Deck in Edit mode.<br>Click image to enlarge.</p></figcaption></figure>

**Edit Mode** is used for playback of captured _Take_ files. In this mode, you can playback and stream recorded data and complete post-processing tasks. The Cameras View displays the recorded 2D data while the 3D Viewport represents either recorded or real-time processed data as described below.

There are two modes for editing:

* **Edit:** Playback in standard Edit mode displays and streams the processed 3D data saved in the recorded _Take_. Changes made to settings and assets are not reflected in the Viewport until the _Take_ is [reprocessed](../reconstruction-and-2d-mode.md#applying-changes-to-3d-data).&#x20;
* **Edit 2D:** Playback in Edit 2D mode performs a live reconstruction of the 3D data, immediately reflecting changes made to settings or assets. These changes are not applied to the recording until the _Take_ is [reprocessed](../reconstruction-and-2d-mode.md#applying-changes-to-3d-data). To playback in 2D mode, click the Edit button and select _Edit 2D_. &#x20;

<figure><img src="../../.gitbook/assets/Live or Edit mode - switch to 2D (1).png" alt="" width="200"><figcaption><p>Click Edit to select the Edit mode.</p></figcaption></figure>

{% hint style="info" %}
Regardless of the selected Edit mode, you must reprocess the _Take_ to create new 3D data based on the modifications made.&#x20;
{% endhint %}

Please see the [Data Editing ](../data-editing.md)page for more information about editing _Takes_.&#x20;

## Recording

In Live mode, click the Record Button <img src="../../.gitbook/assets/Record Button.png" alt="" data-size="line"> on the [Control Deck](../../motive-ui-panes/control-deck.md) to begin recording. Motive will display a red border around the Viewport and the Cameras View while recording is in progress.

<figure><img src="../../.gitbook/assets/Motive While Recording.png" alt=""><figcaption><p>The red outline indicates that Motive is recording. </p></figcaption></figure>

&#x20;When using a preset duration timer, Motive will stop recording once the timer runs out. When the duration is set to Manual, click the Stop button <img src="../../.gitbook/assets/Stop Recording Button (1).png" alt="" data-size="line"> to end the recording. &#x20;

#### Recording Delay&#x20;

The Recording Delay feature adds a countdown before the start of the capture, allowing time to set the scene and ensure all actors are in place.&#x20;

<figure><img src="../../.gitbook/assets/Recording Delay Countdown (1).png" alt=""><figcaption><p>Motive counts down to begin recording after a pre-selected delay. </p></figcaption></figure>

### Recorded Data Management

In Motive, _Take_ file are stored in folders known as session folders.&#x20;

The [Data pane](../../motive-ui-panes/data-pane.md) is the primary interface for managing capture files. It displays a list of session folders and the corresponding _Take_ files that are recorded or loaded in Motive.&#x20;

Open the Data pane by clicking the <img src="../../.gitbook/assets/Motive Data Pane Button.png" alt="" data-size="line"> icon on the main [Toolbar](../../motive-ui-panes/toolbar-command-bar.md).&#x20;

![The Data Pane Advanced Layout. Click image to enlarge.](<../../.gitbook/assets/Data Pane - Advanced layout explained (1).png>)

### **Tips for Managing Takes**

* Always start by creating session folders for organizing related _Takes_ (e.g., name of the tracked subject). Click the <img src="../../.gitbook/assets/Data Pane - Add session folder (1).png" alt="" data-size="line"> button at the bottom of the pane to create a new folder.&#x20;
* Plan ahead for the capture day by creating a list of captures in a text file or a spreadsheet. Copy and paste (_Ctrl + V_) the list into the Data Management pane to create empty _Takes_ as placeholders for the shoot. (e.g. walk, jog, run, jump).
* Start the capture day with a training _Take_ for each Trained Markerset. Once the Markerset assets are created, they can be imported into Live and included in the remaining captures.&#x20;
* Select one of the empty _Takes_ and start recording. Motive will save the capture using the same  name as the selected _Take_.
* If the capture was unsuccessful, simply record it again. Motive will record additional _Takes_ with an incremented suffix added to the given _Take_ name (e.g. walk\_001, walk\_002, walk\_003). The suffix format is defined on the [General tab of the Application Settings](../../motive-ui-panes/settings/settings-general.md) panel.
* When the capture is successful, select another empty _Take_ in the list to begin the next capture.
* To close an individual session folder, right-click on the folder and select _Remove_.&#x20;
* To close all the open session folders at once, right-click in the empty space in the session folder list and select _Remove all Folders._&#x20;

<div><img src="../../.gitbook/assets/TXT copy to import empty takes.png" alt="Copying a list of Take names from a Text File."> <figure><img src="../../.gitbook/assets/Data Pane with Imported list of Takes.png" alt=""><figcaption><p>Use Ctrl + V to paste the copied list <br>into a Session folder in  the Data Pane. </p></figcaption></figure></div>

### Recorded Data Types

When a capture is recorded, both 2D data and real-time reconstructed 3D data are saved in the _Take_. For more details on each data type, refer to the [Data Types](data-types.md) page.

* **2D data:**  Consists of the 2D object images captured by each camera.&#x20;
* **3D data:**  Reconstructed 3D marker data, solved from the 2D data.&#x20;

{% hint style="info" %}
Reference Video from Prime Color cameras or from mocap cameras running in MJPEG mode is also included in the _Take_.&#x20;
{% endhint %}

## Marker Types in Motive

In the [3D perspective view](../../motive-ui-panes/viewport.md#perspective-view), marker data displays the 3D positions of the actual markers, as calculated from the camera data. This is distinct from the position of marker constraints in the solver calculation for any assets that include the selected markers.&#x20;

Markers can be Passive or Active, Labeled or Unlabeled.&#x20;

To customize the color associated with a specific marker type, click <img src="../../.gitbook/assets/Settings button (15).png" alt="" data-size="line"> to open the [Applications Setting](../../motive-ui-panes/settings/) panel. Marker settings are located on the [Views tab](../../motive-ui-panes/settings/settings-views.md). Asset markers will display in the color set in the asset properties.&#x20;

Markers associated with Rigid Bodies, Skeletons, or Trained Markersets will use the color properties of the asset rather than the application defaults.&#x20;

For more detail on markers, please see the [Markers ](../markers.md)page.&#x20;

### Passive and Active Markers

**Passive Markers** have a retroreflective covering that reflects incoming light back to its source. IR light emitted from the camera is reflected by passive markers, detected by the camera’s sensor, and captured as 2D marker data.&#x20;

Passive markers that are not part of an asset are white by default.&#x20;

**Active Markers** emit a unique LED pulse in sync with a BaseStation for optimal tracking. Active markers are reconstructed and tracked in Motive automatically. The unique illumination pattern ensures each active marker is individually labeled, with an Active ID assigned to the corresponding reconstruction. This applies whether or not the Active Marker is part of an asset.&#x20;

Active markers that are not part of an asset are cyan by default.

### Labeled and Unlabeled Markers

Marker labels are software tags assigned to identify **trajectories** of reconstructed 3D markers so they can be referenced for tracking individual markers, Rigid Bodies, Skeletons, or Trained Markersets. When an asset is created, the markers used to define it are automatically labeled as part of the asset definition.&#x20;

To display Marker Labels in the 3D Viewport, click the <img src="../../.gitbook/assets/Viewport Visual Options button (10).png" alt="" data-size="line"> _Visual Aids_ button and select _Labels_ from the _Marker_ section of the menu. Alternately, use the **hotkey L** to toggle labels on or off.&#x20;

Select _Simplify Labels_ (or use **hotkey Ctrl + L**) to display the marker label without the asset name prefix. &#x20;

<figure><img src="../../.gitbook/assets/Rigid Body in Viewport with Labels (4).png" alt="" width="377"><figcaption><p>Labels displayed for a Rigid Body asset.</p></figcaption></figure>

#### Unlabeled Markers

Markers that are not part of an asset remain unlabeled and are displayed in the 3D Viewport using the selected color values in Applications Settings.&#x20;

Unlabeled Markers can also result from tracking errors that occur during the capture, such as marker occlusions. You can do another Take, or address [labeling errors](../data-editing.md#labeling-errors) in post-processing. Please see the [Data Editing](../data-editing.md) and [Labeling ](../labeling.md)pages for more detail on this process. &#x20;

![Left: an unlabeled passive marker. Right: unlabeled active markers on a Puck. ](<../../.gitbook/assets/Unlabeled markers - active and passive.png>)

{% hint style="info" %}
Marker color can also be changed through the [Constraints XML file](../../motive-ui-panes/constraints-pane/constraints-xml-files.md) if needed.
{% endhint %}

## Marker Constraints

The reconstructed 3D markers that comprise an asset are known as **Constraints** in Motive. They appear as transparent spheres that reflect the expected position of a 3D marker in the solved data, based on the asset definition. &#x20;

To view Marker Constraints, select _Marker Constraints_ from the Visual Aids <img src="../../.gitbook/assets/Viewport Visual Options button (11).png" alt="" data-size="line"> menu in the viewport and select _Show All_.&#x20;

For more information about working with Constraints, please see the [Constraints Pane](../../motive-ui-panes/constraints-pane/) page.&#x20;

![A Marker Constraint for a single marker.](<../../.gitbook/assets/Constraint - single.png>)
