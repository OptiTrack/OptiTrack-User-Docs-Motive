---
description: An overview of features available in the Devices Pane.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/devices-pane
---

# Devices Pane

## Overview

The Devices Pane lists all of the devices connected to the OptiTrack system and displays related properties that can be viewed and updated directly from the pane. Items are grouped by type:

* Tracking cameras
* Color reference cameras
* Synchronization hubs
* Base Stations&#x20;
* Active Tags
* Force plates&#x20;
* Data acquisition devices (DAQ)

When a single device is selected, the [Properties pane](properties-pane/) displays properties specific to the selection. When multiple devices are selected, only common properties are displayed; properties that are not shared are not included. Where the selected assets have different values, Motive displays the text _Mixed_ or places the toggle button in the middle position <img src="../.gitbook/assets/Properties - Mixed values for toggle switch (2).png" alt="" data-size="line">.&#x20;

### Interface

Open the Devices pane from the View menu or by clicking the ![](<../.gitbook/assets/image (71).png>) icon on the main toolbar.

![Devices Pane.](<../.gitbook/assets/Devices Pane - Anotated.png>)

{% hint style="info" %}
Right-click the header for any device type to select which properties to display. Drag the columns to re-order.&#x20;
{% endhint %}

## Camera Frame Rate

The master Camera Frame Rate is shown at the top of the pane. This is the frame rate for all the _tracking_ cameras. Other synchronized devices, such as reference cameras, can be set to run at a fraction or a multiple of this rate.&#x20;

To change the rate, click on the rate to open the drop-down menu and select the desired rate.

![](<../.gitbook/assets/image (380).png>)

{% hint style="info" %}
#### Frame Rates and Windowing

Each camera model has a native frame rate, which is the maximum frame rate that will provide the highest resolution and largest field of view (FOV). When a camera runs above its native frame rate, the resolution and FOV are reduced, resulting in a smaller image. This allows the camera to keep up with the higher frame rate.

See the specifications page for the selected camera model for more detail.
{% endhint %}

{% hint style="info" %}
With **Flex 3** and **Slim 3U** cameras, the variable frame rate is controlled through the software, rather than the camera hardware. When selecting lower frame rates, Motive will display new data every other frame (50/60hz) or every 4 frames (25/30hz).
{% endhint %}

#### Rate Multiplier

_Reference_ cameras in MJPEG or grayscale video mode and [Prime Color](../hardware/cameras/ethernet-cameras/prime-color.md) cameras can capture either at the master frame rate or at a fraction of that rate. Capturing reference video at a lower frame rate reduces the amount of data recorded, decreasing the size of the _TAKE_ files. &#x20;

To set a new rate, click in the [Multiplier](devices-pane.md#multiplier) field and select a fractional rate from the drop-down list. Note that this field does not open for cameras in object mode. &#x20;

<img src="../.gitbook/assets/Devices Pane - Rate multiplier.png" alt="Set the Rate Multiplier on a Reference Camera." width="249">

{% hint style="info" %}
**eSync2 users:**  When using an eSync2 synchronization hub to synchronize the camera system to another signal (e.g., Internal Clock), use the Multiplier on the input signal to adjust the camera system frame rate.
{% endhint %}

## Device Group

Device Groups are shortcuts that make it easier to select and manage multiple devices in the system. Groups are different from [Camera partitions](properties-pane/properties-pane-camera.md#partition-id) as they can comprise any device type and individual devices can be members of more than one group.&#x20;

There are a couple of ways to create, view, and update Device groups.&#x20;

#### Device Context Menu options

1. Select one or more devices of the same type from the list.
2. Right-click and select _Add to Group -> New Group_ or select an existing group from the list.

**Presets** are sets of properties you can apply to a camera rather than a collection of devices. When you assign a preset, the camera's properties are updated to the preset's defined values.&#x20;

* Tracking camera options are _Aiming, Tracking,_ or _Reference._&#x20;
* [Color camera options](devices-pane.md#color-camera-presets) are _Small Size - Lower Rate, Small Size - Full Rate, Great Image,_ or _Calibration Mode._&#x20;

<div><figure><img src="../.gitbook/assets/Devices Pane - Add to Group (1).png" alt="" width="251"><figcaption><p><em>Add to Group</em> options.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Devices Pane - Group presets (1).png" alt="" width="244"><figcaption><p>Preset options for tracking cameras.</p></figcaption></figure></div>

{% hint style="info" %}
_Presets_ and the option to _Add to an existing group_ are only available from the context menu.
{% endhint %}

#### Device Groups Panel

The Device Groups panel is the only place to access existing Device Groups. You can also use this panel to create new groups or to delete existing groups.

1. Select one or more devices of the same type from the list.
2. Click the down button <img src="../.gitbook/assets/Devices Pane - show device groups button (1).png" alt="" data-size="line"> under the camera frame rate to expand the list of Device groups.&#x20;
3. To create a new group, click _New Group from Selection..._&#x20;
4. To select all the devices in a group, select the group in the panel.
5. To delete a group, click the <img src="../.gitbook/assets/Devices Pane - device group delete button.png" alt="" data-size="line">that appears to the right of the group name when the mouse hovers over it.&#x20;

<img src="../.gitbook/assets/Devices Pane - Device Groups.png" alt="Device Group panel expanded." width="245">

## Tracking Cameras

The Tracking cameras category includes all the motion capture cameras connected to the system, even those running in reference video mode (MJPEG).&#x20;

{% hint style="info" %}
Reference cameras do not contribute to the 3D reconstruction. The video captured by the reference camera is included in the _Take_ file.&#x20;
{% endhint %}

![](<../.gitbook/assets/image (449).png>)

### Tracking Camera Settings

Select one or more cameras to change settings for all the selected devices either directly from the Devices pane or through the Properties pane.

Right-click the header to show or hide specific camera settings and drag the columns to change the order. Some items are displayed for reference only and cannot be changed from the Devices pane. Others, such as the camera serial number, cannot be changed at all.

All of these settings (and more) are also available on the [Cameras Properties pane](properties-pane/properties-pane-camera.md).&#x20;

#### Number (view only)

Displays the camera number assigned by Motive.&#x20;

{% hint style="info" %}
Camera numbering is determined by the [Camera ID setting](settings/settings-general.md#camera-id) on the General tab of Motive's settings panel. When the ID value is set to _Custom Number,_ the Number field in the Camera Properties pane opens for editing.&#x20;
{% endhint %}

#### Enable

A camera must be enabled to record data and contribute to the reconstruction of 3D data, if recording in object mode. Disable a camera if you do not want it included in the data capture.

#### Multiplier

This property is also known as the Frame Rate Multiplier. As noted [above](devices-pane.md#rate-multiplier), a reference camera can be set to run at a reduced rate (half, quarter, etc.) to reduce the data output and size of the _Take_ file. Tracking camera are reference cameras if they are running in MJPEG mode.&#x20;

#### Mode

The icon indicates the [video mode](../motive/camera-video-types.md) for each camera. Click the icons to toggle between frequently used modes for each camera.&#x20;

* **Tracking:**  Tracking modes capture the 2D marker data used in the reconstruction of 3D data.&#x20;
  * **Object mode:** <img src="../.gitbook/assets/Devices Pane - Object Mode.png" alt="" data-size="line"> Performs on-camera detection of centroid location, size, and roundness of the markers, and sends respective 2D object metrics to Motive to calculate the 3D data. Recommended as the default mode for recording.&#x20;
  * **Precision mode:** <img src="../.gitbook/assets/Devices Pane - Precision Mode.png" alt="" data-size="line"> Performs on-camera detection of marker reflections and their centroids and sends the respective data to Motive to determine the precise centroid location. Precision mode is more processing intensive than Object mode.&#x20;
* **Reference Modes:**  Reference modes capture grayscale video as a visual aid during the take. Cameras in these modes do not contribute to the reconstruction of 3D data.
  * **Grayscale:** <img src="../.gitbook/assets/Devices Pane - Grayscale Mode.png" alt="" data-size="line"> Raw grayscale is intended for aiming and monitoring the camera views and diagnosing tracking problems and includes aiming crosshairs by default. Grayscale video cannot be exported.&#x20;
  * **MJPEG:** <img src="../.gitbook/assets/Devices Pane - MJPEG Mode.png" alt="" data-size="line"> A reference mode that captures grayscale frames, compressed on-camera for scalable reference videos. MJPEG videos can be [exported ](../motive/data-export/#reference-video-export)along with overlay information such as markers, rigid bodies, and skeleton data.&#x20;

**Duplex Mode:** Duplex mode captures in both Object and MJPEG mode, providing reference video and tracking data from the same camera. Duplex mode unlocks more reference viewpoints when needed and supports post production markerless workflows.

Available video modes may vary for different camera types, and not all modes may be available by clicking the _Mode_ icon in the Devices pane. Find all available modes for the camera model by right-clicking the camera in the [Cameras View](viewport.md#cameras-view) window and selecting _Video Type._

{% hint style="success" %}
Duplex mode is available in the following cameras:

* PrimeX 13, 22, 41, and 120
* SlimX 22, 41, and 120
* VersaX 22, 41, and 120&#x20;

Duplex mode is available with the **Motive:Body** and **Motive:Body-Unlimited** licenses only.
{% endhint %}

#### Exposure&#x20;

Sets the amount of time that the camera exposes per frame in microseconds. The minimum and maximum values allowed depend on both the type of camera and the frame rate.&#x20;

Higher exposure allows more light in, creating a brighter image that can increase visibility for small and dim markers. However, setting the exposure too high can introduce false markers, larger marker blooms, and marker blurring, all of which can negatively impact marker data quality.&#x20;

{% hint style="info" %}
Prior to Motive 3.2, exposure value was measured in scanlines for tracking bars and Flex3 series cameras.&#x20;
{% endhint %}

#### LED&#x20;

This setting enables the IR LED ring on the selected camera. This setting must be enabled to illuminate the IR LED rings to track passive retro-reflective markers.&#x20;

If the IR illumination is too bright for the capture, decrease the camera exposure setting to decrease the amount of light received by the imager, dimming the captured frames.

#### Reconstruction&#x20;

This setting determines whether the selected camera contributes to the [real-time reconstruction](../motive/reconstruction-and-2d-mode.md) of the 3D data.

When this setting is disabled, Motive continues to record the camera's 2D frames into the capture file, they are just not processed in the real-time reconstruction. A [post-processing reconstruction pipeline](../motive/reconstruction-and-2d-mode.md#post-processing-reconstruction) allows you to obtain fully contributed 3D data in Edit mode.

{% hint style="info" %}
For most applications, it's fine to have all cameras contribute to the 3D reconstruction engine. In a system with a high camera-count, this can slow down the real-time processing of the point cloud solve and result in dropped frames. Resolve this by disabling some cameras from real-time reconstruction and using the collected 2D data later in post-processing.
{% endhint %}

#### **Device** (view only)

Displays the name of the selected camera type, e.g., Prime 13, Slim 3U, etc.

#### Serial (view only)

Displays the camera's serial number.&#x20;

#### Gain

Sets the imager gain level for the selected camera. Gain settings can be adjusted to amplify or diminish the brightness of the image.&#x20;

This setting can be beneficial when tracking at long ranges. However, note that increasing the gain level will also increase the noise in the image data and may introduce false reconstructions.&#x20;

{% hint style="warning" %}
Before changing the gain level, we recommend adjusting other camera settings first to optimize image clarity, such as increasing exposure and decreasing the lens f-stop.
{% endhint %}

#### Focal length (view only)

Displays the focal length of the camera's lens.

#### IR Filter&#x20;

Sets the camera to view either visible or IR spectrum light on cameras equipped with a Filter Switcher. When enabled, the camera captures in IR spectrum, and when disabled, the camera captures in the visible spectrum.&#x20;

Infrared Spectrum should be selected when the camera is being used for marker tracking applications. Visible Spectrum can optionally be selected for full frame video applications, where external, visible spectrum lighting will be used to illuminate the environment instead of the camera’s IR LEDs. Common applications include reference video and external calibration methods that use images projected in the visible spectrum.

#### Rate (view only)

Shows the frame rate of the camera, calculated by applying the the rate multiplier (if applicable) to the master frame rate.

#### Partition ID (view only)

Camera partitions create the ability to have several capture volumes (multi-room) tied to a single system. [Continuous Calibration](../motive/calibration/continuous-calibration.md) collects samples from each partition and calibrates the entire system even when there is no camera overlap between spaces.&#x20;

The Partition ID can only be changed from the Camera Properties pane.

## Color Cameras

[Prime color](../hardware/cameras/ethernet-cameras/prime-color.md) reference cameras are a separate category under the devices pane. Just like cameras in the Tracking group, you can customize the column view and configure camera settings directly from this pane.&#x20;

### Color Camera Video Modes

* Color Video: This is the standard mode for capturing color video data.&#x20;
* Object: Use this mode during calibration.&#x20;

### Color Camera Settings

On the Devices pane, color cameras have all of the settings available for tracking cameras, with three additional settings, summarized below.&#x20;

#### **Resolution**

This property sets the resolution of the images captured by the selected camera.

You may need to reduce the maximum frame rate to accommodate the additional data produced by recording at higher resolutions. The table below shows the maximum allowed frame rates for each respective resolution setting.

| Resolution                    | Max Frame Rate |
| ----------------------------- | -------------- |
| 960 x 540 (540p)              | 500 FPS        |
| 1280 x 720 (720p)             | 360 FPS        |
| 1920 x 1080 (1080p) _Default_ | 250 FPS        |

#### **Bit Rate**

This setting determines the selected color camera's output transmission rate, and is only applicable when the [Compression mode](properties-pane/properties-pane-camera.md#compression-mode) for the camera is set to [Constant Bit Rate](properties-pane/properties-pane-camera.md#bit-rate) (the default value) in the Camera properties.&#x20;

The maximum data transmission speed that a Prime color camera can output is 100 megabytes per second (MB/s). At this setting, the camera will capture the best quality image, however, it could overload the network if there isn't enough bandwidth to handle the transmitted data.

{% hint style="info" %}
Since the bit-rate controls the rate of data each color camera outputs, this is one of the most important settings to adjust when configuring the system.&#x20;

When a system is experiencing 2D frame drops, one of the following system requirements is not being met:&#x20;

* Network bandwidth
* CPU processing speed
* RAM/disk memory

Decreasing the bit-rate in such cases may slow the data transmission speed of the color camera enough to resolve the problem.
{% endhint %}

Read more about compression mode and bit rate settings on the page [Properties Pane: Camera](properties-pane/properties-pane-camera.md).&#x20;

#### Gamma

Gamma correction is a non-linear amplification of the output image. The gamma setting adjusts the brightness of dark pixels, mid-tone pixels, and bright pixels differently, affecting both brightness and contrast of the image. Depending on the capture environment, especially with a dark background, you may need to adjust the gamma setting to get best quality images.

### Color Camera Presets

Presets for Color Cameras use standard settings to optimize for different outcomes based on file size and image quality.  Calibration mode sets the appropriate video mode for the camera type in addition to other setting changes.&#x20;

<figure><img src="../.gitbook/assets/Devices Pane - Color Camera Presets (1).png" alt=""><figcaption><p>Color Camera preset options.</p></figcaption></figure>

{% hint style="info" %}
The optimal [Bit Rate](devices-pane.md#bit-rate) for each preset is calculated based on the master camera frame rate when the preset is selected. Lower bit rates result in smaller file sizes. Higher bit rates produce higher quality captures and result in larger file sizes.
{% endhint %}

* **Small Size - Lower Rate**
  * Video Mode:  Color Video
  * Rate Multiplier:  1/4 (or closest possible)
  * Exposure:  20000 (or max)
  * Bit Rate:  \[calculated]
* **Small Size - Full Rate**
  * Video Mode:  Color Video
  * Rate Multiplier:  x1
  * Exposure:  20000 (or max)
  * Bit Rate:  \[calculated]
* **Great Image**
  * Video Mode:  Color Video
  * Rate Multiplier:  x1
  * Exposure:  20000 (or max)
  * Bit Rate:  \[calculated]
* **Calibration Mode**
  * Video Mode:  Object Mode
  * Rate Multiplier:  x1
  * Exposure:  250
  * Bit Rate:  N/A

## Synchronization Devices

The Synchronization category includes synchronization devices such as the eSync and OptiHub2 as well as Base Stations used to connect Active devices to the system.

<figure><img src="../.gitbook/assets/Devices Pane - eSync and BaseStation.png" alt=""><figcaption><p>Synchronization and Active Tag devices in the Devices pane.</p></figcaption></figure>

### Base Stations&#x20;

[Base Station](../active-classic/active-classic-hardware/basestation.md) values are read-only, in both the Devices pane and the Properties pane. Available display options are the _Device_ (device type) and the _Serial number_.

{% hint style="info" %}
The [Active Batch Programmer](../active-classic/configuration/active-batch-programmer.md) is required to view additional settings or make configuration changes to a Base Station and its associated active devices.&#x20;
{% endhint %}

### Sync Hub

Values displayed for [eSync](properties-pane/properties-pane-esync2.md) and [OptiHub2](properties-pane/properties-pane-optihub2.md) devices are read-only, but there are configurable settings available for these devices on the Properties pane. Available display options for the Devices pane are the _Device_ (device type) and the _Serial number_.

For more information on configuring a sync hub, please read the [Synchronization](../synchronization/synchronization-setup.md) page.

![Devices pane and Properties pane for eSync 2. ](<../.gitbook/assets/image (1089).png>)

## Active Tags

Active devices that connect to the camera system via Base Stations are listed in the Active Tag section.&#x20;

* **Name:** the tag name consists of two numbers, the the RF channel used to communicate with the Base Station followed by the unique Uplink ID assigned to the device.&#x20;
* **Paired Asset:**  If the tag is paired to an asset, the asset's name will appear here. Otherwise, the field will display N/A.
* **Aligned:**  shows the status of the Active tag.
  * If the tag is unpaired, the circle x icon will appear. <img src="../.gitbook/assets/image (1455).png" alt="" data-size="original">
  * If the tag is pairing, the circle with the wave icon will appear. ![](<../.gitbook/assets/image (1456).png>)
  * If the tag is paired, the green circle with green check icon will appear. ![](<../.gitbook/assets/image (1457).png>)
* **BaseStation:** displays the serial number of the connected Base Station. This column is not displayed by default; right-click the header to add it.

<figure><img src="../.gitbook/assets/image (1556).png" alt="" width="563"><figcaption></figcaption></figure>

## Force Plates / Data Acquisition

Detected force plates and NI-DAQ devices are also listed under the Devices pane. You can apply multipliers to the sampling rate if the they are synchronized through trigger. If they are synchronized via a reference clock signal (e.g. Internal Clock), their sampling rate will be fixed to the rate of that signal.

For more information, please read the force plate setup pages:  [AMTI Force Plate Setup](../movement-sciences/movement-sciences-hardware/amti-force-plate-setup.md), [Bertec Force Plate Setup](../movement-sciences/movement-sciences-hardware/bertec-force-plate-setup.md), [Kistler Force Plate Setup](../movement-sciences/movement-sciences-hardware/kistler-force-plate-setup.md), or the [NI-DAQ Setup](../movement-sciences/movement-sciences-hardware/ni-daq-setup.md) setup page.
