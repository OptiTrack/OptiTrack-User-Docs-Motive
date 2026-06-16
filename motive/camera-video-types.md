---
description: An overview of the different video modes available on the OptiTrack cameras.
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/camera-video-types
---

# Camera Video Types

Captured frames are processed differently based on the video mode the camera is set to during recording. Only the configured video mode is recorded and saved in _Take_ files.

## Video Types

Video types, or image-processing modes, available in OptiTrack Cameras:

<div><figure><img src="../.gitbook/assets/image (1373).png" alt="An image taken from an OptiTrack camera in Object mode, with an inset close-up of a single marker. "><figcaption><p>Object mode</p></figcaption></figure> <figure><img src="../.gitbook/assets/image (1365).png" alt="An image taken from an OptiTrack camera in Precision mode, with an inset close-up of a single marker. "><figcaption><p>Precision mode</p></figcaption></figure></div>

<div><figure><img src="../.gitbook/assets/image (945).png" alt="An image taken from an OptiTrack camera in MJPEG mode, with an inset close-up of a single marker. "><figcaption><p>MJPEG mode</p></figcaption></figure> <figure><img src="../.gitbook/assets/image (1390).png" alt="An image taken from an OptiTrack camera in Object mode, with an inset close-up of a single marker. "><figcaption><p>Grayscale mode</p></figcaption></figure></div>

OptiTrack cameras have different image-processing modes, referred to as video types in Motive. Each mode processes captured frames differently at both the camera hardware and software levels.&#x20;

The precision of the capture and the required amount of CPU resources will vary depending on the configured video type.

The available modes vary some by camera model.&#x20;

{% hint style="success" %}
[Duplex mode](camera-video-types.md#duplex-mode) records both MJPEG and Object mode and is available in the following cameras:

* PrimeX 13, 22, 41, and 120
* SlimX 22, 41, and 120
* VersaX 22, 41, and 120&#x20;
{% endhint %}

The video types are categorized as either **tracking modes** (object mode and precision mode) or **reference modes** (MJPEG and raw grayscale). Only cameras in tracking modes will contribute to the reconstruction of 3D data.

To switch between image processing modes, simply right-click on the camera from the [2D camera preview](../motive-ui-panes/viewport.md#cameras-view) pane and select the desired video type.

{% hint style="info" %}
Motive records frames of only the configured video types. Video types of the cameras cannot be switched for recorded _Takes_ in post-processing of captured data.
{% endhint %}

<figure><img src="../.gitbook/assets/ViewPort Cameras View - change video type 3.3.png" alt="The context menu available from the Cameras viewport in Motive, with the Video Mode option selected and the available video modes displayed: Object; Grayscale; MJPEG; and Duplex. "><figcaption><p>Changing video types from the Camera Preview pane.</p></figcaption></figure>

### **Object Mode**

_(Tracking Mode)_ Object mode performs on-camera detection of centroid location, size, and roundness of the markers, sending respective 2D object metrics to the host PC. This mode is best for obtaining the 3D data. Compared to other processing modes, Object mode provides the smallest CPU footprint, resulting in the lowest processing latency while maintaining the high accuracy.&#x20;

**Supported Camera Models:** Prime/PrimeX series, Slim/SlimX series, VersaX Series, Flex 13, and S250e camera models.

### **Precision Mode**

_(Tracking Mode)_ Precision Mode performs on-camera calculations to determine which pixels are over the threshold value, including a two pixel halo around the above-threshold pixels. These pixels are sent to the PC for additional processing and determination of the precise centroid location.&#x20;

Precision mode provides quality centroid locations but is computationally expensive and network bandwidth intensive. We recommend this mode for low to moderate camera count systems for 3D tracking when Object Mode is unavailable or when using the 0.3 MegaPixel USB cameras.&#x20;

**Supported Camera Models:** Flex series, Tracking Bars, S250e, Slim13e, and Prime 13 series camera models.

{% hint style="info" %}
Precision mode is not more accurate than object mode. Object mode is the preferred mode for tracking and should be used when available.&#x20;
{% endhint %}

### **MJPEG grayscale Mode**

_(Reference Mode)_ The MJPEG-compressed grayscale mode captures grayscale frames, compressed on-camera for scalable reference video capabilities. Grayscale images are used only for reference purpose, and processed frames will not contribute to the reconstruction of 3D data. The MJPEG mode can run at full frame rate and be synchronized with tracking cameras and can be exported.&#x20;

**Supported Camera Models:** All camera models.

### **Raw grayscale**

_(Reference Mode)_ This mode processes full resolution, uncompressed, grayscale images. The grayscale mode is designed to be used only for reference purposes, and processed frames will not contribute to the reconstruction of 3D data. Because of the high bandwidth associated with sending raw grayscale frames, this mode is not fully synchronized with other tracking cameras and will run at lower frame rate. Raw grayscale videos cannot be exported from a recording.&#x20;

This video mode is recommended only for aiming and monitoring the camera views for diagnosing tracking problems.

**Supported Camera Models:** All camera models.

### Duplex Mode

_(Tracking and Reference Mode)_ Duplex mode captures in both Object and MJPEG mode, providing reference video and tracking data from the same camera. Duplex mode unlocks more reference viewpoints when needed and supports post production markerless workflows.&#x20;

**Supported Camera Models:** PrimeX 13, 22, 41, and 120, SlimX 22, 41, and 120, and VersaX 22, 41, and 120.

{% hint style="info" %}
Duplex mode is available with the **Motive:Body** and **Motive:Body-Unlimited** licenses only.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/Viewport Cameras View - Duplex Mode PICKLEBALL MARKUP (2).png" alt="An image taken from an OptiTrack camera in Duplex mode, with an arrow-shaped text box pointing to the orange-colored markers visible in the shot. "><figcaption><p>Duplex mode combines Reference video in MJPEG mode and tracking data in Object mode. </p></figcaption></figure>

#### Marker Color

Change the display color for the markers in the [Properties pane](../motive-ui-panes/properties-pane/properties-pane-camera.md) for the selected camera under the 2D Display Options.&#x20;

<figure><img src="../.gitbook/assets/Properties - Camera Duplex mode color (1).png" alt="A screenshot from Motive of the 2D Display Options with the Duplex Object Color property shown for a camera that supports duplex mode. "><figcaption><p>Duplex color options in Camera Properties.</p></figcaption></figure>

#### Camera Masks

Masked cameras that appear in the duplex capture will display a red halo around the camera light. If the ring light is disabled, the camera will appear like any other masked object in the volume.&#x20;

<figure><img src="../.gitbook/assets/Duplex mode Cameras masked ANNOTATED.png" alt="An image taken from an OptiTrack camera in Duplex mode, with notes highlighting the difference between the 2 masked cameras in the shot, where the camera on the left has the ring light enabled and the camera on the right has the ring light disabled. "><figcaption><p>Masked cameras in Duplex mode.</p></figcaption></figure>

#### Threshold Values

Threshold is an important setting while using Duplex mode, because MJPEG usually works best with brighter images while object mode does best using dark images with hotspots.

Adjust the [Threshold ](../motive-ui-panes/properties-pane/properties-pane-camera.md#threshold)values in the [Properties pane](../motive-ui-panes/properties-pane/properties-pane-camera.md). We recommend setting the value around 220 – 255.&#x20;

## Switching Video Types

You can check and/or change the video type of the selected camera from either the [Devices pane](../motive-ui-panes/devices-pane.md), the  [camera properties](../motive-ui-panes/properties-pane/properties-pane-camera.md), or the [Cameras view](../motive-ui-panes/viewport.md#cameras-view) in the [Viewport](../motive-ui-panes/viewport.md). Hotkeys can also be used to change the video type.

### Video Mode Hotkeys

You can select a camera or cameras and use the associated hotkey to change the video mode.

* **Object:** O
* **Grayscale:** U
* **MJPEG:** I
* **Duplex:** Y

### From the Devices Pane

From the [Device pane](../motive-ui-panes/devices-pane.md), click the Mode icon for the selected camera to toggle between frequently used modes for each camera.&#x20;

<figure><img src="../.gitbook/assets/Devices Pane with Duplex Mode camera ANNOTATED.png" alt="The Devices pane in Motive, showing a list of 13 tracking cameras with the Mode column highlighted with a red box. " width="320"><figcaption><p>The Devices pane with the Mode column highlighted.</p></figcaption></figure>

Available video modes may vary for different camera types, and not all modes may be available by clicking the _Mode_ icon in the Devices pane.&#x20;

|                                           Icon                                           | Mode           |
| :--------------------------------------------------------------------------------------: | -------------- |
|  <img src="../.gitbook/assets/Devices Pane - Object Mode.png" alt="" data-size="line">   | Object mode    |
| <img src="../.gitbook/assets/Devices Pane - Precision Mode.png" alt="" data-size="line"> | Precision mode |
| <img src="../.gitbook/assets/Devices Pane - Grayscale Mode.png" alt="" data-size="line"> | Grayscale      |
|   <img src="../.gitbook/assets/Devices Pane - MJPEG Mode.png" alt="" data-size="line">   | MJPEG          |
|      <img src="../.gitbook/assets/Duplex mode icon (2).png" alt="" data-size="line">     | Duplex         |

### From Camera Properties

Select one or more cameras in either the Viewport or the [Devices pane](../motive-ui-panes/devices-pane.md) to view and change settings in the [Properties pane](../motive-ui-panes/properties-pane/), including the video type in the _Video Mode_ section. Use the dropdown list to update the mode on all the selected cameras.&#x20;

* If the selected cameras are not all in the same mode, the Video Mode field will display _mixed_.&#x20;
* The drop-down menu will only display modes common to all of the selected cameras. Some video types, such as Precision or Duplex mode, are not available on all models.&#x20;

<figure><img src="../.gitbook/assets/Properties - Camera Video Mode Selections.png" alt="A screenshot of the Camera Properties pane in Motive, showing the four Video Modes available: Object; Grayscale, MJPEG, and Duplex."><figcaption><p>Camera properties - Change Video Mode.</p></figcaption></figure>

### From Viewports

#### **From Perspective View**

In the Viewport's [Perspective view](../motive-ui-panes/viewport.md#perspective-view), right-click on the selected camera to open the Viewport's context menu. Click _Video Type_ to choose from the available modes.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-04-21 102201.png" alt="The context menu from the Motive Perspective View when a camera is selected. The Camera Video Types menu is open with the available types displayed: Object; Grayscale; MJPEG; and Duplex. "><figcaption><p>The Context menu for a selected camera in the Viewport.</p></figcaption></figure>

#### **From Cameras View**

In the Viewport's Cameras view, right-click on the camera you wish to change, then click _Video Type_ to select the new mode.&#x20;

![Changing the Video mode from the Cameras view in the Viewport.](<../.gitbook/assets/ViewPort Cameras View - change video type 3.3.png>)

####

## Reference Videos

Cameras can be set to record reference videos during capture, which is used to observe what goes on during recording. Reference video is recorded in either MJPEG or Duplex mode, and is synchronized with other captured frames.&#x20;

<figure><img src="../.gitbook/assets/Camera context menu (1).png" alt="The Camera context menu from the Viewport in Motive, with the &#x22;Make Reference&#x22; option highlighted."><figcaption></figcaption></figure>

Compared to **object images** that are taken by non-reference cameras in the system, MJPEG videos produce more data and consume more network bandwidth. A high volume of data traffic can increase the system latency. For this reason, we recommend setting no more than one or two cameras to full MJPEG mode.&#x20;

The Video option on the Viewport pane menu allows you to quickly switch that pane to the desired reference camera. Only cameras in MJPEG or Duplex mode will appear in the list.&#x20;

<figure><img src="../.gitbook/assets/Viewport - switch to Video (1).png" alt="the Perspective pane menu with the Video option selected and the available reference cameras shown. "><figcaption><p>The main Viewport pane menu. </p></figcaption></figure>

{% hint style="danger" %}
If Grayscale mode is selected during a recording instead of MJPEG, no reference video will be recorded and the data from that camera will display a black screen. Full grayscale is strictly used for aiming and focusing cameras.
{% endhint %}

{% hint style="info" %}
**Note:**

* Processing latency can be monitored from the status bar located at the bottom.
* MJPEG video are used only for reference purposes, and processed frames will not contribute to reconstruction of 3D data.
* Select Duplex mode to collect both reference video and tracking data from the same camera. Duplex mode is only available on select PrimeX, SlimX, and VersaX cameras.&#x20;
{% endhint %}

The Data Transmission rate in the bottom right corner of Motive helps evaluate process latency.

<figure><img src="../.gitbook/assets/image (670).png" alt="A screenshot of the data transmission rate from the bottom right corner of the Motive screen."><figcaption><p>Data transmission rate.</p></figcaption></figure>

### View From Selection

When a reference camera is selected in the Cameras view, the _View from Selection_ menu option changes to the selected camera.&#x20;

<div><figure><img src="../.gitbook/assets/Viewport - switch to Video (2).png" alt="A screenshot from Motive of the menu from the Perspective viewport that has the reference video options expanded. The &#x22;View from Selected&#x22; option is grayed out. "><figcaption><p>The Perspective menu, with no camera selected.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Viewport - switch to Video WITH A CAMERA SELECTED.png" alt="A screenshot from Motive of the menu from the Perspective viewport that has the reference video options expanded. The &#x22;View from Selected&#x22; option has changed to display the selected camera (Camera 1).. "><figcaption><p>The Perspective menu, with camera one selected.</p></figcaption></figure></div>

Use the hotkey **3** in the Perspectives pane to switch to the selected camera's video in the main viewport. If the camera was [calibrated](calibration/) and capturing reference videos, 3D assets will be overlaid on top of the reference image.

<figure><img src="../.gitbook/assets/image (1430).png" alt="A screenshot from Motive of a reference video with asset overlay information for a skeleton (actor) walking on 2 force plates. "><figcaption><p>Monitoring reference view of a MJPEG camera from the viewport.</p></figcaption></figure>
