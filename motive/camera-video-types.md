# Camera Video Types

This page covers different video modes that are available on the OptiTrack cameras. Depending on the video mode that a camera is configured to, captured frames are processed differently, and only the configured video mode will be recorded and saved in _Take_ files.

## Video Types

**Video types, or image-processing modes, available in OptiTrack Cameras**

![Object mode](<../.gitbook/assets/image (368).png>) ![Precision mode](<../.gitbook/assets/image (314).png>)

![MJPEG mode](<../.gitbook/assets/image (465).png>) ![Grayscale mode](<../.gitbook/assets/image (385).png>)

There are different video types, or image-processing modes, which could be used when capturing with OptiTrack cameras. Dending on the camera model, the available modes vary slightly. Each video mode processes captured frames differently at both camera hardware and software level. Furthermore, precision of the capture and required amount of CPU resources will vary depending on the configured video type.

The video types are categorized into either **tracking modes** (object mode and precision mode) and **reference modes** (MJPEG and raw grayscale). Only the cameras in the tracking modes will contribute to the reconstruction of 3D data.

To switch between video types, simply right-click on one of the cameras from the [2D camera preview](../motive-ui-panes/viewport.md#cameras-view) pane and select the desired image processing mode under the video types.

{% hint style="info" %}
Motive records frames of only the configured video types. Video types of the cameras cannot be switched for recorded _Takes_ in post-processing of captured data.
{% endhint %}

![Changing video types from the Camera Preview pane.](<../.gitbook/assets/image (373).png>)

### **Object Mode**

_(Tracking Mode)_ Object mode performs on-camera detection of centroid location, size, and roundness of the markers, and then, respective 2D object metrics are sent to the host PC. In general, this mode is best recommended for obtaining the 3D data. Compared to other processing modes, the Object mode provides smallest CPU footprint and, as a result, lowest processing latency can be achieved while maintaining the high accuracy. However, be aware that the 2D reflections are truncated into object metrics in this mode. The Object mode is beneficial for Prime Series and Flex 13 cameras when lowest latency is necessary or when the CPU performance is taxed by Precision Grayscale mode (e.g. high camera counts using a less powerful CPU).

**Supported Camera Models:** Prime/PrimeX series, Flex 13, and S250e camera models.

### **Precision Mode**

_(Tracking Mode)_ Precision Mode performs on-camera detection of marker reflections and their centroids. These centroid regions of interests are sent to the PC for additional processing and determination of the precise centroid location. This provides high-quality centroid locations but is very computationally expensive and is only recommended for low to moderate camera count systems for 3D tracking when the Object Mode is unavailable.

**Supported Camera Models:** Flex series, Tracking Bars, S250e, Slim13e, and Prime 13 series camera models.

### **MJPEG grayscale Mode**

_(Reference Mode)_ The MJPEG -compressed grayscale mode captures grayscale frames, compressed on-camera for scalable reference video capabilities. Grayscale images are used only for reference purpose, and processed frames will not contribute to the reconstruction of 3D data. The MJPEG mode can run at full frame rate and be synchronized with tracking cameras.

**Supported Camera Models:** All camera models

### **Raw grayscale**

_(Reference Mode)_ Processes full resolution, uncompressed, grayscale images. The grayscale mode is designed to be used only for reference purposes, and processed frames will not contribute to the reconstruction of 3D data. Because of the high bandwidth associated with sending raw grayscale frames, this mode is not fully synchronized with other tracking cameras and they will run at lower frame rate. Also, raw grayscale videos cannot be exported out from a recording. Use this video mode only for aiming and monitoring the camera views for diagnosing tracking problems.

**Supported Camera Models:** All camera models.

## Switching Video Types

You can check and/or switch video types of a selected camera from either the [camera properties](../motive-ui-panes/properties-pane/properties-pane-camera.md), [viewports](../motive-ui-panes/viewport.md). Also, you toggle the camera(s) between tracking mode and reference mode in the [Device pane](../motive-ui-panes/devices-pane.md) by clicking on the _Mode_ button ( <img src="../.gitbook/assets/Devices Pane - Object Mode.png" alt="" data-size="line"> ). If you want to use all of the cameras for tracking, make sure all of the cameras are in the **Tracking mode**.

### From Camera Properties

Open the [Devices pane](../motive-ui-panes/devices-pane.md) and [Properties pane](../motive-ui-panes/properties-pane/) and select one or more cameras listed. Once the selection is made, respective camera properties will be shown on the properties pane. Current video type will be shown in the _Video Mode_ section and you can change it using the drop-down menu.

![](<../.gitbook/assets/image (362).png>)

### From Viewports

**From Perspective View**

In the perspective view, right-click on a camera from the viewport and set the camera to the desired video mode.

![](<../.gitbook/assets/image (309).png>)

**From Cameras View**

In the cameras view, right-click on a camera view and change the video type for the selected camera.

![](<../.gitbook/assets/image (418).png>)

## Reference Videos

Cameras can also be set to record reference videos during capture. When using MJPEG mode, these videos are synchronized with other captured frames, and they are used to observe what goes on during recorded capture. To record the reference video, switch the camera into a MJPEG mode [![DevicesPane MJPEG.png](https://v30.wiki.optitrack.com/images/f/f2/DevicesPane_MJPEG.png)](https://v30.wiki.optitrack.com/index.php?title=File:DevicesPane_MJPEG.png) by toggling on the camera mode in the [Devices ](../motive-ui-panes/devices-pane.md)pane.

Compared to **object images** that are taken by non-reference cameras in the system, MJPEG videos are larger in data size, and recording reference video consumes more network bandwidth. High amount data traffic can increase the system latency or cause reductions in the system frame rate. For this reason, we recommend setting no more than one or two cameras to Reference mode. Reference views can be observed from either the Camera Preview pane or by selecting Video and selecting the camera that is in MJPEG mode from the Viewport dropdown.

{% hint style="danger" %}
If Greyscale mode is selected during a recording instead of MJPEG, no reference video will be recorded and the data from that camera will display a black screen. Full greyscale is strictly used for aiming and focusing cameras.
{% endhint %}

{% hint style="info" %}
**Note:**

* Processing latency can be monitored from the status bar located at the bottom.
* MJPEG video are used only for reference purposes, and processed frames will not contribute to reconstruction of 3D data.
{% endhint %}

<figure><img src="../.gitbook/assets/image (2) (2) (4).png" alt=""><figcaption><p>Located in the bottom right of Motive, you can view the amount of data being processed. This can help evaluate process latency.</p></figcaption></figure>

### View From Selection

The video captured by reference cameras can be monitored from the [viewport](../motive-ui-panes/viewport.md). To view the reference video, select the camera that you wish to monitor, and use the Num 3 hotkey to switch to the reference view. If the camera was [calibrated](calibration/) and capturing reference videos, 3D assets will be overlaid on top of the reference image.

![Monitoring reference view of a MJPEG camera from the viewport.](<../.gitbook/assets/image (387).png>) ![Switching a camera into the reference view. You can also select a camera and use number 3 hotkey to quickly set it to reference view.](<../.gitbook/assets/image (439).png>)
