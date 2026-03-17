---
description: An in-depth look at the features and functions available on the Control Deck.
---

# Control Deck

## Overview

Motive has two modes: **Live** and **Edit.** The Control Deck contains the operations for recording or playback, depending on which mode is active. Toggle between the two by selecting one from the <img src="../.gitbook/assets/Live or Edit mode.png" alt="" data-size="line"> button on the Control Deck or by using the _Shift + \~_ hotkey.&#x20;

{% hint style="info" %}
**Tip:** Prime series cameras will illuminate in blue when in live mode, in green when recording, and are turned off in edit mode. See more at [Camera Status Indicators](../hardware/camera-status-indicators.md).
{% endhint %}

## **Live Mode**

**Live mode** is used when recording new _Takes_ or when streaming a live capture. In this mode, all enabled cameras continuously capture 2D images and reconstruct the detected reflections into 3D data in real-time.

![Motive's Control Deck in LIVE mode.](<../.gitbook/assets/Control Deck - LIVE Mode Annotated.png>)

#### Live/Edit Mode

Use the Live/Edit button to switch between Live and Edit modes. When in Live mode, the [Perspective View](viewport.md#perspective-view) of the [3D Viewport](viewport.md) will display the capture volume. &#x20;

#### Take Name

Recorded captures are known as _Takes_ in Motive, and are saved with the file extension .tak. The _Take Name_ is an editable field that populates by default as _Take \<date & time>_ when Motive is first launched or if the field is left blank.&#x20;

{% hint style="info" %}
**Session Folders in Live**

The _Take_ file is saved in the [Session Folder](data-pane.md#list-of-session-folders) currently open. If there is no Session Folder open or the [Persistent Data Folders](settings/settings-general.md#persistent-data-folders) setting has been disabled, the _Take_ will be saved in the Default file location:  _C:\Users\\\<user\_name>\Documents\OptiTrack\Default._&#x20;

Read more about Session Folders and _Take_ management on the [Data Pane](data-pane.md) page.
{% endhint %}

When switching from Edit to Live mode, the default _Take Name_ depends on the name of the Take currently open in Edit mode.&#x20;

* If the current file has a _default_ name then the new file will also use the default. &#x20;
* If the current file has a unique name, the new file will use the same name, adding a [Take Suffix](settings/settings-general.md#take-suffix). The default suffix adds an underscore as a separator followed by three digits, including leading zeroes, e.g., _My Take\_001,_ incrementing up from the highest number of the Takes with the same name.&#x20;

{% hint style="info" %}
To Change the default Take Suffix, click the <img src="../.gitbook/assets/Settings button (5).png" alt="" data-size="line"> button to open the [_Application Settings_](settings/) panel. Go to the _General tab -> General Section -> Take Suffix._&#x20;
{% endhint %}

#### **Timecode**

Timecode displays the recording time and subframe in the format H:MM:SS:### where # is the recorded subframe number. The number of subframes per second is equal to the camera frame rate.

{% hint style="info" %}
**External Timecode Display Options**

When using an external timecode signal through an eSync device, you can display the timecode signal here in the Control Deck or at the bottom of the 3D Viewport (the default setting).&#x20;

To update, click the <img src="../.gitbook/assets/Settings button (5).png" alt="" data-size="line"> button to open the [_Application Settings_](settings/) panel. Go to the _Views tab ->  3D -> Heads Up Display -> Timecode_. Options are:&#x20;

* Show in 3D View
* Show in Control Deck
* Do not Show
{% endhint %}

#### Frame Counter

Displays the current frame number during recording.&#x20;

#### Record / Stop

When you are ready to begin recording, click the Record button. While recording, a red outline visual displays around the Viewport panes and the Record button becomes a Stop Recording button: <img src="../.gitbook/assets/Stop Recording Button.png" alt="" data-size="line">

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption><p>Motive while recording a <em>Take</em>. </p></figcaption></figure>

#### Recording Delay

The Recording Delay feature adds a countdown before the start of the capture, allowing time to set the scene and ensure all actors are in place.&#x20;

<figure><img src="../.gitbook/assets/Recording Delay Countdown.png" alt=""><figcaption><p>Motive counting down a delayed start. </p></figcaption></figure>

#### Recording Duration

Click to select one of the pre-set recording duration times (up to 60 seconds) or set to Manual to control the length of the take.&#x20;

## **Edit Mode**

**Edit Mode** is used for playback of captured _Take_ files. In this mode, you can playback and stream recorded data and complete post-processing tasks.

The Cameras View displays the recorded 2D data while the 3D Viewport represents either recorded or real-time processed data as described below.

![The Control Deck in Edit mode.](<../.gitbook/assets/Control Deck - Edit Mode Annotated (5).png>)

There are two modes for editing:

* **Edit:** Playback in standard Edit mode displays and streams the processed 3D data saved in the recorded _Take_. Changes made to settings and assets are not reflected in the Viewport until the _Take_ is [reprocessed](../motive/reconstruction-and-2d-mode.md#applying-changes-to-3d-data).&#x20;
* **Edit 2D:** Playback in Edit 2D mode performs a live reconstruction of the 3D data, immediately reflecting changes made to settings or assets. These changes are displayed in real-time but are not saved into the recording until the _Take_ is [reprocessed](../motive/reconstruction-and-2d-mode.md#applying-changes-to-3d-data) and saved. To playback in 2D mode, click the Edit button and select _Edit 2D_. &#x20;

<figure><img src="../.gitbook/assets/Live or Edit mode - switch to 2D (1).png" alt="" width="200"><figcaption><p>Click Edit to select the Edit mode.</p></figcaption></figure>

{% hint style="info" %}
Regardless of the selected Edit mode, you must reprocess the _Take_ to create new 3D data based on the modifications made.&#x20;
{% endhint %}

Please see the [Data Editing ](../motive/data-editing.md)page for more information about editing _Takes_.&#x20;

#### Take Name

Displays the name of the current _Take._

#### Playback Controls

Use the playback controls to play the _Take_ at regular speed or to move one frame at a time, forward or back.

#### Timecode

Timecode displays the recording time and subframe in the format H:MM:SS:### where # is the recorded subframe number. The number of subframes per second is equal to the camera frame rate.

#### Frame Counter

Displays the current frame number during playback.&#x20;

#### Playback Mode

There are three modes for playback:

* **Loop:** replays the selected range from the start until stopped manually. This is the default mode.
* **Bounce:** playback reverses direction when it reaches either the end or start of the selected rang&#x65;_,_ continuing to alternate directions until stopped manually.
* **End Point:** playback stops when the selected range reaches the end.

#### Reverse Playback

Click _REVERSE_ to playback the selected range in reverse. Unlike the _Bounce_ playback mode, this setting maintains the reverse direction until turned off and is used with the _Loop_ and _End Point_ playback modes.&#x20;

#### Playback Speed

Increase the playback speed or use a preset reduced rate (ranging from 5% to 50%) to slow it down.&#x20;

#### View Range

The View Range fields show the Starting Frame and the Ending Frame numbers for the range selected for playback. The View Range is also known as the Working Range as it can be used to facilitate post-processing by restricting playback to the specific section being edited. &#x20;

When the entire _Take_ is selected (as in the [Edit Mode](control-deck.md#edit-mode) image, above) the Start Frame will show 0, and the End Frame will show the final frame of the _Take_. If a specific range is selected, the View Range will display the Starting Frame and the Ending Frame numbers of that Working Range.&#x20;

<figure><img src="../.gitbook/assets/Selected Timeline in View Range.png" alt=""><figcaption><p>View Range with a Working Range displayed.</p></figcaption></figure>

{% hint style="info" %}
You can also use the View Range fields to manually enter the desired Working Range.&#x20;
{% endhint %}

### Timeline Controls

In Edit mode, the Timeline is displayed across the top of the Control Deck.&#x20;

<figure><img src="../.gitbook/assets/Timeline - Annotated.png" alt=""><figcaption><p>The Timeline in Motive.</p></figcaption></figure>

* **The Scrubber** is a vertical white bar that shows the location of the current frame. Drag the scrubber left or right to move to a different frame.&#x20;
* The **Working Range** is a horizontal green line with vertical handles for the Starting and Ending frames. Click and drag the handles to adjust the range.&#x20;
* The **selected frame range on a graph** is shaded in yellow, with 2 yellow vertical lines to define the Starting and Ending frames. Read the [Graph View Pane](graph-view-pane.md) page for more information about working with graph data. &#x20;

## Status Monitor

![Status parameter shown on the control deck.](<../.gitbook/assets/image (113).png>)

Located on the right corner of the control deck, the status monitor displays specific operational parameters in Motive.&#x20;

Click the monitor to see all monitored data. The blue check mark in the leftmost column indicates the status that displays on the control deck when the monitor window is closed. To select a different status to display, click the column to the left of the status name to move the check mark.&#x20;

![Status panel in Motive.](<../.gitbook/assets/image (169).png>)

#### **Residual**&#x20;

This is the average of [residual](../motive/reconstruction-and-2d-mode.md) values of all live-reconstructed 3D points. This is available only in Live mode or in 2D Edit mode.

#### **Data**

The current incoming data transfer rate (KB/s) for all attached cameras.

#### **Point Cloud**

The measured latency of the point cloud reconstruction engine.

#### **Assets**

The measured latency of the rigid body solver and the skeleton solver combined.

#### **Software**&#x20;

The measured software latency. This represents the amount of time it takes Motive to process each frame of captured data. This includes reconstructing the 2D data into 3D data, labeling and modeling the trackable assets, displaying in the viewport, and other processes configured in Motive.

#### **System**

**Available only on Ethernet Camera systems (Prime series and Slim13E).** The measured total system latency. This is the time measured from the middle of the camera exposures until Motive has fully solved all of the tracking data.

#### **Streaming**

The data rate at which the tracking data is streamed to connected client applications.

#### **Final Rate**&#x20;

The final data acquisition rate of the system.

#### **Cameras**

**Available only on Ethernet Camera systems (Prime series or Slim 13E).** The average temperature, in Celsius, on the imager boards of the cameras in the system. &#x20;

## Streaming Status

{% hint style="info" %}
Streaming status is available only for Unicast streaming. This status is disabled for Multicast streaming.
{% endhint %}

* Hover over the icon to see streaming connection status messages.
* Click the icon to quickly access the [Data Streaming settings](../motive/data-streaming.md).

![Streaming Status](<../.gitbook/assets/image (119).png>)

## Notifications

Important software notifications are reported at the right corner of the control deck. Click on the <img src="../.gitbook/assets/Control Deck Notification Icon.png" alt="" data-size="line"> button to view the messages.&#x20;

Only important configuration notifications are reported here. Software status messages are reported on the [Log pane](log-pane.md).

![Sample Notification.](<../.gitbook/assets/image (94).png>)
