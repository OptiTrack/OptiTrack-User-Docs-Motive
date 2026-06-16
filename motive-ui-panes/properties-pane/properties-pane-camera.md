---
description: An in-depth look at the properties available for Cameras.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/properties-pane/properties-pane-camera
---

# Properties Pane: Camera

Camera properties determine how and what a camera captures when recording. These settings can be configured to optimize your capture application.&#x20;

This page covers the properties specific to cameras. For general information on using and customizing the Properties pane, see the [Properties Pane](./) page. For detailed descriptions of properties for various asset types or other devices, please see the following pages:

* [Properties: Take](properties-pane-take.md)
* [Properties: Trained Markerset](properties-pane-trained-markerset.md)
* [Properties: Skeleton](properties-pane-skeleton.md)
* [Properties: Rigid Body](properties-pane-rigid-body.md)
* [Properties: eSync](properties-pane-esync2.md)
* [Properties: Force Plates](properties-pane-force-plates.md)
* [Properties: NI-DAQ](properties-pane-ni-daq.md)

{% hint style="info" %}
**Advanced Settings**

The Properties pane contains advanced settings that are hidden by default. To access these settings, click the <img src="../../.gitbook/assets/Motive Context Menu (24).png" alt="Screenshot of Motive&#x27;s button to open a menu within a pane. " data-size="line"> button in the top right corner.&#x20;

Use the _Edit Advanced_ option to customize which settings are in the _Advanced Settings_ category and which appear in the standard view, to show only the settings that are needed specifically for your capture application.&#x20;
{% endhint %}

<div data-full-width="false"><img src="../../.gitbook/assets/Properties Pane - Show Advanced (5).png" alt="Show or Edit Advanced Settings."></div>

## Show Properties

Select one or more cameras in either the [Devices pane](../devices-pane.md), the [Cameras View](../viewport.md#cameras-view), or the [3D Viewport](../viewport.md#perspective-view) to view Camera properties. When a single camera is selected, the Properties pane displays properties specific to the selection. When multiple cameras are selected, only shared values are displayed. Where the selected cameras have different values, Motive displays the text _Mixed_ or places the toggle button in the middle position <img src="../../.gitbook/assets/Properties - Mixed values for toggle switch (2).png" alt="A screenshot of Motive&#x27;s &#x22;mixed setting&#x22; toggle button." data-size="line">.&#x20;

Changes made to camera settings through the Properties Pane apply to all selected cameras.&#x20;

## Camera Details

This section provides basic information about the selected camera(s). Properties are Standard unless noted otherwise. Most are read-only.

<figure><img src="../../.gitbook/assets/Properties Pane - Camera Details.png" alt=""><figcaption><p>Camera Advanced Properties - <br>Details section.</p></figcaption></figure>

#### **Device Name**

Displays the name of the selected camera type, e.g., Prime 13, Slim 3U, etc.

#### **Model** (Advanced)

Displays the model number of the selected camera, where applicable.

#### **Sub-Model (Advanced)**

Displays the sub-model number of the selected camera, where applicable.&#x20;

#### **Serial Number**

Displays the camera serial number.

#### **Firmware Version** (Advanced)

Displays the camera's firmware version.&#x20;

#### **Logic Version** (Advanced)

Displays the camera's logic version. For internal Support use.&#x20;

#### **Number**

Displays the camera number assigned by Motive.&#x20;

{% hint style="info" %}
Camera numbering is determined by the [Camera ID setting](../settings/settings-general.md#camera-id) on the General tab of Motive's settings panel. To open up the number field for editing, set the Camera ID to _Custom_.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Properties - Camera Custom Number (1).png" alt="" width="309"><figcaption><p>Camera Properties with Custom Camera Number.</p></figcaption></figure>

#### **Focal Length**

Displays the focal length of the camera's lens.

#### Position (Advanced)

Displays the x/y/z coordinates of the camera in relation to the global origin.

#### Orientation (Advanced)

Displays the orientation (pitch/yaw/roll) of the camera in relation to the global origin.

#### Pixel Dimensions (Advanced)

Displays the resolution of the camera's image sensor, in pixels.

## General Settings

The following items are available in the General Properties section. Properties are Standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/Camera Properties - General.png" alt="" width="251"><figcaption><p>Camera Advanced Properties - <br>General Settings</p></figcaption></figure>

#### **Enabled**

A camera must be enabled to record data and contribute to the reconstruction of 3D data, if recording in object mode. Disable a camera if you do not want it included in the data capture.

#### Reconstruction

This setting determines whether the selected camera contributes to the [real-time reconstruction](../../motive/reconstruction-and-2d-mode.md) of the 3D data.

When this setting is disabled, Motive continues to record the camera's 2D frames into the capture file, they are just not processed in the real-time reconstruction. A [post-processing reconstruction pipeline](../../motive/reconstruction-and-2d-mode.md#post-processing-reconstruction) allows you to obtain fully contributed 3D data in Edit mode.

{% hint style="info" %}
For most applications, it's fine to have all cameras contribute to the 3D reconstruction engine. In a system with a high camera-count, this can slow down the real-time processing of the point cloud solve and result in dropped frames. Resolve this by disabling some cameras from real-time reconstruction and using the collected 2D data later in post-processing.
{% endhint %}

#### **Rate**

Shows the frame rate of the camera. The camera frame rate can be changed from the [Devices pane](../devices-pane.md#camera-framerate).

{% hint style="info" %}
#### Frame Rates and Windowing

Each camera model has a native frame rate, which is the maximum frame rate that will provide the highest resolution and largest field of view (FOV). When a camera runs above its native frame rate, the resolution and FOV are reduced, resulting in a smaller image. This allows the camera to keep up with the higher frame rate.

See the specifications page for the selected camera model for more detail.
{% endhint %}

#### **Rate Multiplier**

Shows the rate multiplier or divider applied to the master frame rate. The master frame rate depends on the sync configuration.

#### **Exposure**

Sets the amount of time that the camera exposes per frame in microseconds. The minimum and maximum values allowed depend on both the type of camera and the frame rate.&#x20;

Higher exposure allows more light in, creating a brighter image that can increase visibility for small and dim markers. However, setting the exposure too high can introduce false markers, larger marker blooms, and marker blurring, all of which can negatively impact marker data quality.&#x20;

{% hint style="info" %}
Prior to Motive 3.2, exposure value was measured in scanlines for tracking bars and Flex3 series cameras.&#x20;
{% endhint %}

#### **Threshold**

Defines the minimum brightness for a pixel to be recognized by a camera, with all pixels below the threshold ignored.&#x20;

Increasing the threshold can help filter interference by non-markers (e.g. reflections and external light sources), while lowering the threshold can allow dimmer markers to be seen by the system (e.g. smaller markers at longer distances from the camera).

Threshold is an important setting while using Duplex mode, because MJPEG usually works best with brighter images while object mode does best using dark images with hotspots. For cameras in Duplex mode, we recommend setting the threshold around 220-255.

#### Partition ID (Advanced)

Camera partitions create the ability to have several capture volumes (multi-room) tied to a single system. [Continuous Calibration](../../motive/calibration/continuous-calibration.md) collects samples from each partition and calibrates the entire system even when there is no camera overlap between spaces.&#x20;

#### **LED**

This setting enables the IR LED ring on the selected camera. To track passive retro-reflective markers, this setting must be set to true (enabled) to illuminate the IR LED rings for tracking.&#x20;

If the IR illumination is too bright for the capture, decrease the camera exposure setting to decrease the amount of light received by the imager, dimming the captured frames.

#### **Video Mode**

Select from [the following video types](../../motive/camera-video-types.md):

* **Tracking:**  Tracking modes capture the 2D marker data used in the reconstruction of 3D data.&#x20;
  * **Object mode:** Performs on-camera detection of centroid location, size, and roundness of the markers, and sends respective 2D object metrics to Motive to calculate the 3D data. Recommended as the default mode for recording.&#x20;
  * **Precision mode:** Performs on-camera detection of marker reflections and their centroids and sends the respective data to Motive to determine the precise centroid location. Precision mode is more processing intensive than Object mode.&#x20;
* **Reference Modes:**  Reference modes capture grayscale video as a visual aid during the take. Cameras in these modes do not contribute to the reconstruction of 3D data.
  * **Grayscale:**  Raw grayscale is intended for aiming and monitoring the camera views and diagnosing tracking problems and includes aiming crosshairs by default. Grayscale video cannot be exported.&#x20;
  * **MJPEG:**  A reference mode that captures grayscale frames, compressed on-camera for scalable reference videos. MJPEG videos can be [exported ](../../motive/data-export/#reference-video-export)along with overlay information such as markers, rigid bodies, and skeleton data.&#x20;
* **Duplex Mode:** [Duplex mode](properties-pane-camera.md#duplex-mode) captures in both Object and MJPEG mode, providing reference video and tracking data from the same camera. Duplex mode unlocks more reference viewpoints when needed and supports post production markerless workflows.&#x20;

{% hint style="success" %}
Duplex mode is available in the following cameras:

* PrimeX 22, 41, and 120
* SlimX 22, 41, and 120
* VersaX 22, 41, and 120&#x20;

Duplex mode is available with the **Motive:Body** and **Motive:Body-Unlimited** licenses only.
{% endhint %}

#### **MJPEG Quality**

For cameras in MJPEG or Duplex mode, this indicates the quality of the video recording. This property is only visible when an applicable video mode is selected. &#x20;

#### **IR Filter**

Sets the camera to view either visible or IR spectrum light on cameras equipped with a Filter Switcher. When enabled, the camera captures in IR spectrum, and when disabled, the camera captures in the visible spectrum.&#x20;

Infrared Spectrum should be selected when the camera is being used for marker tracking applications. Visible Spectrum can optionally be selected for full frame video applications, where external, visible spectrum lighting will be used to illuminate the environment instead of the camera’s IR LEDs. Common applications include reference video and external calibration methods that use images projected in the visible spectrum.

#### **Gain**

Sets the imager gain level for the selected camera. Gain settings can be adjusted to amplify or diminish the brightness of the image.&#x20;

This setting can be beneficial when tracking at long ranges. However, note that increasing the gain level will also increase the noise in the image data and may introduce false reconstructions.&#x20;

{% hint style="warning" %}
Before changing the gain level, we recommend adjusting other camera settings first to optimize image clarity, such as increasing exposure and decreasing the lens f-stop.
{% endhint %}

#### **Calibrated (Advanced)**

Shows whether the selected camera has been calibrated. This property does not indicate the quality of the calibration.

## Display

#### **Show Field of View**

When enabled, the estimated field of view (FOV) of the selected camera is shown in the perspective viewport. When the camera is selected, the lines display in yellow. When the camera is not selected, the lines display in cyan.

<img src="../../.gitbook/assets/Camera Properties - display FOV.png" alt="Selected camera with Show Field of View setting enabled. " width="344">

#### **Show Frame Delivery Info**

Frame delivery information is used to determine how fast a camera is delivering its frame packets. When enabled, the frame delivery information is shown in the [Camera views](../viewport.md#cameras-view).

This setting can also be enabled by right-clicking a camera in the Cameras view or in the 3D Viewport and selecting _Frame Delivery Visual_.

{% hint style="info" %}
Aiming Crosshairs are controlled globally through Motive's general settings. To see and change those settings:

1. Click <img src="../../.gitbook/assets/Settings button (13).png" alt="" data-size="line"> to open the Settings panel.&#x20;
2. In the [_Aim Assist_](../settings/settings-general.md#aim-assist) section of the General tab, select a value for _Aiming Crosshairs:_&#x20;
   * None
   * Grayscale Only (default)
   * All Modes
{% endhint %}

### 2D Display Options

Properties specific to cameras that support Duplex mode.&#x20;

<figure><img src="../../.gitbook/assets/Properties - Camera Duplex mode color.png" alt=""><figcaption><p>2D Display Options for Duplex mode cameras.</p></figcaption></figure>

#### Duplex Object Color

Set the color to use to display detected objects when in Duplex mode.&#x20;

## Prime Color Camera Properties

Prime color cameras also have the following additional properties that can be configured:

![General Properties of a Prime Color camera.](<../../.gitbook/assets/Prime Color Variable Bit Rate.png>)

### Resolution

Default: 1920 x 1080

This property sets the resolution of the images captured by the selected camera.

You may need to reduce the maximum frame rate to accommodate the additional data produced by recording at higher resolutions. The table below shows the maximum allowed frame rates for each respective resolution setting.

<table><thead><tr><th width="361">Resolution</th><th>Max Frame Rate</th></tr></thead><tbody><tr><td>960 x 540 (540p)</td><td>500 FPS</td></tr><tr><td>1280 x 720 (720p)</td><td>360 FPS</td></tr><tr><td>1920 x 1080 (1080p)</td><td>250 FPS</td></tr></tbody></table>

### Compression Mode

Default: Constant Bit Rate.

This property determines how much the captured images will be compressed.&#x20;

**Constant Bit-Rate**

In the Constant Bit-Rate mode, Prime Color cameras vary the degree of image compression to match the data transmission rate given under the Bit Rate settings. At a higher bit-rate setting, the captured image will be compressed less. At a lower bit-rate setting, the captured image will be compressed more to meet the given data transfer rate. Compression artifacts may be introduced if it is set too low.

The Constant Bit-Rate mode is used by default and recommended because it is easier to control the data transfer rate and efficiently utilizes the available network bandwidth.

**Variable Bit-Rate**

The Variable Bit-Rate setting keeps the amount of the compression constant and allows the data transfer rate to vary. This mode is beneficial when capturing images with objects that have detailed textures because it keeps the amount of compression consistent on all frames. However, this mode may also cause dropped frames if the camera needs to compress highly detailed images, spiking the data transfer rate, which may overflow the network bandwidth as a result. For this reason, we recommend using the Constant Bit-Rate setting in most applications.

### Compression

The compression property sets the percentage (100%) of the maximum data transmission speed to allocate for the camera.&#x20;

### Bit Rate

Default: 100 MB/s

**Available only while using Constant Bit-rate Mode**

<figure><img src="../../.gitbook/assets/Prime Color Constant Bit Rate MARKED UP and CROPPED.png" alt=""><figcaption></figcaption></figure>

The bit-rate setting determines the selected color camera's output transmission rate.&#x20;

The maximum data transmission speed that a Prime color camera can output is 100 megabytes per second (MB/s). At this setting, the camera will capture the best quality image, however, it could overload the network if there isn't enough bandwidth to handle the transmitted data.

{% hint style="info" %}
Since the bit-rate controls the rate of data each color camera outputs, this is one of the most important settings to adjust when configuring the system.&#x20;

When a system is experiencing 2D frame drops, one of the following system requirements is not being met:&#x20;

* Network bandwidth
* CPU processing speed
* RAM/disk memory

Decreasing the bit-rate in such cases may slow the data transmission speed of the color camera enough to resolve the problem.
{% endhint %}

#### **Bit Rate and Image Quality**

While the image quality increases at a higher bit-rate setting, this also results in larger file sizes and possible frame drops due to data bandwidth bottlenecks. The desired result may differ depending on the capture application and its intended use. The below graph illustrates how the image quality varies depending on the camera frame rate and bit-rate settings.

![](<../../.gitbook/assets/image (125).png>)

{% hint style="info" %}
**Tip: Monitoring data output from each camera**

Data output from the entire camera system can be monitored through the [Status Panel](../status-panel.md). Output from individual cameras can be monitored from the 2D Camera Preview pane when the _Camera Info_ display is enabled under the visual aids ( <img src="../../.gitbook/assets/Motive Visual Options button (4).png" alt="" data-size="line"> ) option.
{% endhint %}

![Camera Info displayed in the Cameras View.](<../../.gitbook/assets/image (121).png>)

### Gamma

Default : 24

Gamma correction is a non-linear amplification of the output image. The gamma setting will adjust the brightness of dark pixels, mid-tone pixels, and bright pixels differently, affecting both brightness and contrast of the image. Depending on the capture environment, especially with a dark background, you may need to adjust the gamma setting to get best quality images.

![](<../../.gitbook/assets/image (554).png>) ![](<../../.gitbook/assets/image (501).png>)
