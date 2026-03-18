# Devices Pane

The Devices pane can be accessed under the View tab in Motive or by clicking the ![](<../.gitbook/assets/image (131).png>) button on the main toolbar.

## Overview

In Motive, all of the connected devices get listed in the Devices pane, including tracking cameras, synchronization hubs, color reference cameras, and other supported peripheral devices such as force plates and data acquisition devices. Using this pane, core settings of each component can be adjusted, which includes sampling rates and camera exposures. Cameras can be grouped to control the system more quickly. You can also select individual devices to view and modify their properties in the [Properties pane](properties-pane/). Lastly, when specific devices are selected in this pane, their respective properties will get listed under [Properties pane](properties-pane/), where you can also make changes to the settings.

### Interface

At the very top of the devices pane, the master camera system frame rate is indicated. All synchronized devices will be capturing at a whole multiple or a whole divisor of this master rate.

![Devices Pane.](<../.gitbook/assets/image (630).png>)

## Camera Framerate

The master camera frame rate is indicated at top of the Devices pane. This rate sets the framerate which drives all of the _tracking_ cameras. If you wish to change this, you can simply click on the rate to open the drop-down menu and set the desired rate.

![](<../.gitbook/assets/image (593).png>)

{% hint style="info" %}
#### Frame Rates and Windowing

Each camera model has a native frame rate, which is the maximum frame rate that will provide the highest resolution and largest field of view (FOV). When a camera runs above its native frame rate, the resolution and FOV are reduced, resulting in a smaller image. This allows the camera to keep up with the higher frame rate.

See the specifications page for the selected camera model for more detail.
{% endhint %}

_Reference_ cameras using MJPEG grayscale video mode, or [Prime Color](../hardware/cameras/ethernet-cameras/prime-color.md) cameras, can capture either at a same frame rate as the other tracking cameras or at a whole fraction of the master frame rate. In many applications, capturing at a lower frame rate is better for reference cameras because it reduces the amount of data recorded/outputted decreasing the size of the capture files overall. This can be adjusted by configuring the [Multiplier](devices-pane.md#multiplier) setting.

![](<../.gitbook/assets/image (555).png>)

{% hint style="info" %}
**eSync2 users:** If you are using the eSync2 synchronization hub to synchronize the camera system to another signal (e.g. Internal Clock), you can apply multiplier/divisor to the input signal to adjust the camera system frame rate.
{% endhint %}

## Device Group

By clicking on the down-arrow button under the camera frame rate, you can expand list of grouped devices. At first, you may not have any grouped devices. To create new groups, you can select multiple devices that are listed under this panel, right-click to bring up the context menu, and create a new group. Grouping the cameras allows easier control over multiple devices in the system.

![](<../.gitbook/assets/image (561).png>)

## Tracking Cameras

Under the tracking cameras section, it lists out all of the motion capture cameras connected to the system. Here, you can configure and control the cameras. You can right-click on the camera setting headers to show/hide specific camera settings and drag them around to change the order. When you have multiple cameras selected, making changes to the settings will modify them for all of the selected cameras. You can also group the cameras to easily select and change the settings quickly. The configurable options include:

* Framerate multiplier
* [Camera video mode](../motive/camera-video-types.md)
* Exposure length (microseconds)
* IR LED ring on/off
* Real-time reconstruction contribution
* Imager Gain
* IR Filter on/off

![](<../.gitbook/assets/image (608).png>)

### Settings

#### **Multiplier**

The multiplier setting applies selected multiplier to the master sampling rate. Multipliers cannot be applied to the tracking cameras, but you can apply them to the reference cameras that are capturing in [MJPEG video](../motive/camera-video-types.md) processing mode. This allows the reference cameras to capture at a slower framerate. This reduces the number of frames captured by the reference camera which reduces the overall data size.

#### **Mode**

The mode setting indicate which [video mode](../motive/camera-video-types.md) that the cameras are set to. You can click on the icons to toggle between the tracking mode and the reference grayscale mode. Available video modes may be slightly different for different camera types, but available types include:

* [![DevicesPane Object.png](https://v30.wiki.optitrack.com/images/5/52/DevicesPane_Object.png)](https://v30.wiki.optitrack.com/index.php?title=File:DevicesPane_Object.png) Object mode _(tracking)_
* [![DevicesPane Precision.png](https://v30.wiki.optitrack.com/images/0/0c/DevicesPane_Precision.png)](https://v30.wiki.optitrack.com/index.php?title=File:DevicesPane_Precision.png) Precision mode _(tracking)_
* [![DevicesPane MJPEG.png](https://v30.wiki.optitrack.com/images/f/f2/DevicesPane_MJPEG.png)](https://v30.wiki.optitrack.com/index.php?title=File:DevicesPane_MJPEG.png) MJPEG compressed grayscale mode _(reference)_
* [![DevicesPane Rawgray.png](https://v30.wiki.optitrack.com/images/f/f5/DevicesPane_Rawgray.png)](https://v30.wiki.optitrack.com/index.php?title=File:DevicesPane_Rawgray.png) Ray grayscale mode _(reference)_

#### **Exposure**

Sets the amount of time that the camera exposes per frame. The minimum and maximum values will depend on both the type of camera and the frame rate. Higher exposure will allow more light in, creating a brighter image that can increase visibility for small and dim markers. However, setting exposure too high can introduce false reflections, larger marker blooms, and marker blurring--all of which can negatively impact marker data quality.

{% hint style="info" %}
Exposure value is measured in scanlines for V100 and V120 series cameras, and in microseconds for Flex13, S250e and PrimeX Series cameras.
{% endhint %}

#### **LED**

This setting enables or disables illumination of the LEDs on the camera IR LED ring. In certain applications, you may want to disable this setting to stop the IR LEDs from strobing. For example, when tracking active IR LED markers, there is no need for the cameras to emit IR lights, so you may want to disable this to stop the IR illuminations which may introduce additional noise in the data.

**The IR intensity setting is now a on/off setting. Please adjust the exposure setting to adjust the brightness of the image in the IR spectrum.**

#### **Reconstruction**

This enables/disables contribution of respective cameras to the [real-time reconstruction](../motive/reconstruction-and-2d-mode.md) of the 3D data. When cameras are disabled from contributing to the reconstruction, the cameras will still be collecting capture data but they will not be processed through the real-time reconstruction. Please note that 2D frames will still get recorded into the capture file, and you can run post-processing reconstruction pipeline to obtain fully contributed 3D data in the Edit mode.

In most applications, you can have all of the cameras contributing to the 3D reconstruction engine without any problem. But for a very high-camera count systems, having all camera to contribute to the reconstruction engine can slow down the real-time processing of point cloud solve and result in dropped frames. In this case, you can have a few cameras disabled from real-time reconstruction to prevent frame drops and use the collected 2D data later in post-processing.

#### **Gain**

Increasing a camera’s gain will brighten the image, which can improve tracking range at very long distances. Higher gain levels can introduce noise into the 2D camera image, so gain should only be used to increase range in large setup areas, when increasing exposure and decreasing lens f-stop does not sufficiently brighten up the captured image.

#### **IR Filter**

Sets the camera to view either visible or infrared light on cameras equipped with a Filter Switcher. Infrared Spectrum should be selected when the camera is being used for marker tracking applications. Visible Spectrum can optionally be selected for full frame video applications, where external, visible spectrum lighting will be used to illuminate the environment instead of the camera’s IR LEDs. Common applications include reference video and external calibration methods that use images projected in the visible spectrum.

## Color Cameras

[Prime color](../hardware/cameras/ethernet-cameras/prime-color.md) reference cameras will also get listed under the devices pane. Just like other cameras in the Tracking group, you can configure the camera settings, including the sampling rate multiplier to decrease the sampling rate of the camera. Additionally, captured [image resolution](../movement-sciences/prime-color-camera-setup/prime-color-setup.md#camera-resolution) and the data transfer [bit-rate](../movement-sciences/prime-color-camera-setup/prime-color-setup.md#bit-rate) can be configured.

#### **Image Resolution**

This property sets the resolution of the images that are captured by selected cameras. Since the amount of data increases with higher resolution, depending on which resolution is selected, the maximum frame rate allowed by the network bandwidth will vary.

#### **Bit-rate**

Bit-rate setting determines the transmission rate outputted from the selected color camera. This is how you can control the data output from color cameras to avoid overloading the camera network bandwidth. At a higher bit-rate setting, more amount of data is outputted and the image quality is better since there is less amount of image compression being done. However, if there is too much data output, it may overload the network bandwidth and result in frame drops. Thus, it is best to minimize this while keeping the image quality at a acceptable level.

## Sync Hub

Detected synchronization hubs will also get listed under the devices pane. You can select the synchronization hubs in the Devices pane, and configure its input and output signals through the [Properties pane](properties-pane/). For more information on this, please read through the [Synchronization](../synchronization/synchronization-setup.md) page.

![](<../.gitbook/assets/image (633).png>)

## Force Plates / Data Acquisition

Detected force plates and NI-DAQ devices will get listed under the Devices pane as well. You can apply multipliers to the sampling rate if the they are synchronized through trigger. If they are synchronized via a reference clock signal (e.g. Internal Clock), their sampling rate will be fixed to the rate of that signal.

For more information, please read through the force plate setup pages ([AMTI Force Plate Setup](../movement-sciences/movement-sciences-hardware/amti-force-plate-setup.md), [Bertec Force Plate Setup](../movement-sciences/movement-sciences-hardware/bertec-force-plate-setup.md), [Kistler Force Plate Setup](../movement-sciences/movement-sciences-hardware/kistler-force-plate-setup.md)) or the [NI-DAQ Setup](../movement-sciences/movement-sciences-hardware/ni-daq-setup.md) setup page.\\
