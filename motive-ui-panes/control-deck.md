# Control Deck

## Overview

### In Live Mode

![](<../.gitbook/assets/image (944).png>)

### In Edit Mode

![](<../.gitbook/assets/image (993).png>)

**Timeline Frame Range Indicator**

* **Scrubber:** Current frame.
* Green: Working frame range.
* Yellow: Selected frame range.

![Timeline on the control deck in Edit mode.](<../.gitbook/assets/image (987).png>)

## Live and Edit mode

There are two different modes in Motive: **Live mode** and **Edit mode**. You can toggle between two modes from the Control Deck or by using the (Shift + \~) hotkey.

**Live Mode**

The **Live mode** is mainly used when recording new _Takes_ or when streaming a live capture. In this mode, all of the cameras are continuously capturing 2D images and reconstructing the detected reflections into 3D data in real-time.

![Motive in Live Mode.](<../.gitbook/assets/image (1021).png>)

**Edit Mode**

The **Edit Mode** is used for playback of captured Take files. In this mode, you can playback, or stream, recorded data. Also, captured _Takes_ can be post-processed by fixing mislabeling errors or interpolating the occluded trajectories if needed.

![Motive in Edit Mode.](<../.gitbook/assets/image (957).png>)

{% hint style="info" %}
**Tip:** Prime series cameras will illuminate in blue when in live mode, in green when recording, and turned-off in edit mode. See more at [Camera Status Indicators](../hardware/camera-status-indicators.md).
{% endhint %}

## Status Monitor

![Status parameter shown on the control deck.](<../.gitbook/assets/image (979).png>)

Located on the right corner of the control deck, the status monitor can be used to monitor specific operational parameters in Motive. Click on up/down arrows to switch the displayed status. You can also click on the status monitor to open a popup for displaying all available status.

The following status parameters will be available:

### Status definitions

![Status panel in Motive.](<../.gitbook/assets/image (1026).png>)

#### **Residual**

Average of [residual](../motive/reconstruction-and-2d-mode.md) values of all live-reconstructed 3D points. This is available only in the [Live mode](../motive/data-recording/#live-mode-and-edit-mode) or in the [2D Mode](../motive/reconstruction-and-2d-mode.md#2d-mode).

#### **Data**

Current incoming data transfer rate (KB/s) for all attached cameras.

#### **Point Cloud**

Measured latency of the point cloud reconstruction engine.

#### **Assets**

Measured latency of the rigid body solver and the skeleton solver combined.

#### **Software**

Measured software latency. It represents the amount of time it takes Motive to process each frame of captured data. This includes the time taken for reconstructing the 2D data into 3D data, labeling and modeling the trackable assets, displaying in the viewport, and other processes configured in Motive.

#### **System**

**Available only on Ethernet Camera systems (Prime series and Slim13E).** Measured total system latency. This is the time measured from the middle of the camera exposures to when Motive has fully solved all of the tracking data.

#### **Streaming**

The data rate at which the tracking data is streamed to connected client applications.

#### **Final Rate**

Final data acquisition rate of the system.

#### **Cameras**

**Available only on Ethernet Camera systems (Prime series or Slim 13E).** Average temperature, in Celsius, on the imager boards of the cameras in the system.

## Streaming Status

{% hint style="info" %}
Streaming status will be available only for Unicast streaming. This will be disabled for Multicast streaming.
{% endhint %}

The streaming status icon informs users of the streaming connection status. You can click on this icon to quickly access the [data streaming settings](../motive/data-streaming.md) also.

![](<../.gitbook/assets/image (1031).png>)

## Notifications

Important software notifications will be reported at the right corner of the control deck. Click on the [![ControlDeck Notification 20.png](https://v30.wiki.optitrack.com/images/7/73/ControlDeck_Notification_20.png)](https://v30.wiki.optitrack.com/index.php?title=File:ControlDeck_Notification_20.png) to view the message. Only the important configuration notification will be reported here. Software status messages are reported on the [Log pane](log-pane.md).

![Notifying the user to change to the high-performance mode.](<../.gitbook/assets/image (980).png>)
