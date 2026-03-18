# Properties Pane: Camera

When a camera, or a camera group, is selected from the [Devices pane](../devices-pane.md), related camera settings will be displayed in the [Properties pane](./). From the Properties pane, you can configure the camera settings so that it is optimized for your capture application. You can enable/disable IR LEDs, change exposure length of the cameras, set the video mode, apply gain to the capture frames, and more. This page lists out properties of the cameras and what they are used for.

{% hint style="info" %}
**Advanced Settings**

The Properties: Camera contains _advanced settings_ that are hidden by default. Access these settings by going to the menu on the top-right corner of the pane and clicking _Show Advanced_ and all of the settings, including the advanced settings, will be listed under the pane.

The list of advanced settings can also be customized to show only the settings that are needed specifically for your capture application. To do so, go the pane menu and click _Edit Advanced_, and uncheck the settings that you wish to be listed in the pane by default. One all desired settings are unchecked, click _Done Editing_ to apply the customized configurations.
{% endhint %}

![](<../../.gitbook/assets/image (1007) (1) (1) (1) (1) (1) (1) (7).png>)

## General Settings

<figure><img src="../../.gitbook/assets/image (5) (2).png" alt=""><figcaption></figcaption></figure>

#### **Enabled**

Enables/disables selected cameras. When cameras are disabled, they don't record any data nor contribute to the reconstruction of 3d data.

#### **Rate**

Shows the frame rate of the camera. The camera frame rate can only be changed within the devices pane.

{% hint style="info" %}
#### Frame Rates and Windowing

Each camera model has a native frame rate, which is the maximum frame rate that will provide the highest resolution and largest field of view (FOV). When a camera runs above its native frame rate, the resolution and FOV are reduced, resulting in a smaller image. This allows the camera to keep up with the higher frame rate.

See the specifications page for the selected camera model for more detail.
{% endhint %}

#### **Reconstruction**

This setting determines whether or not selected cameras contribute to the real-time reconstruction.

#### **Rate Multiplier**

Shows the rate multiplier or divider applied to the master frame rate. The master frame rate depends on the sync configuration.

#### **Exposure**

Sets the amount of time that the camera exposes per frame. The minimum and maximum values will depend on both the type of camera and the frame rate. Higher exposure will allow more light in, creating a brighter image that can increase visibility for small and dim markers. However, setting exposure too high can introduce false markers, larger marker blooms, and marker blurring--all of which can negatively impact marker data quality. Exposure value is measured in scanlines for tracking bars and Flex3 series cameras, and in microseconds for Flex13, S250e, Slim13E, and Prime Series cameras.

#### **Threshold**

Defines the minimum brightness for a pixel to be seen by a camera, with all pixels below the threshold being ignored. Increasing the threshold can help filter interference by non-markers (e.g. reflections and external light sources), while lowering the threshold can allow dimmer markers to be seen by the system (e.g. smaller markers at longer distances from the camera).

#### Partition ID

_\[Advanced]_ When calibrating multi-room spaces, you can partition select cameras to allow for [Continuous Calibration](../../motive/calibration/continuous-calibration.md) to collect samples from each room and calibrate even when there is no camera overlap between spaces. This creates the ability to have several capture volumes tied to a single system while maintaining continuously calibrated cameras for each space.&#x20;

#### **LED**

This setting enables or disables the IR LED ring on selected cameras. For tracking passive retro-reflective markers, this setting must be set to true to illuminate the IR LED rings for tracking. If the IR illumination is too bright for the capture, you can decrease the camera exposure setting to decrease the amount of light received by the imager; dimming the overall captured frames.

#### **Video Mode**

Sets the [video type](../../motive/camera-video-types.md) of the selected camera.

#### **IR Filter**

Sets the camera to view either visible or IR spectrum on cameras equipped with a Filter Switcher. When enabled, the camera captures in IR spectrum, and when disabled, the camera captures in visible spectrum.Infrared Spectrum should be selected when the camera is being used for marker tracking applications. Visible Spectrum can optionally be selected for full frame video applications, where external, visible spectrum lighting will be used to illuminate the environment instead of the camera’s IR LEDs. Common applications include reference video and external calibration methods that use images projected in the visible spectrum.

#### **Gain**

Sets the imager gain level for the selected cameras. Gain settings can be adjusted to amplify or diminish the brightness of the image. This setting can be beneficial when tracking at long ranges. However, note that increasing the gain level will also increase the noise in the image data and may introduce false reconstructions. Thus, before deciding to change the gain level, adjust the camera settings first to optimize the image clarity.

#### **Calibrated**

_\[Advanced]_ This property indicates whether the selected camera has been calibrated or not. This is just an indication of whether the camera has been processed through the calibration wanding, but it does not validate the quality of the camera calibration.

## Details

Basic information about the selected camera gets listed in the _Details_ section

#### **Number**

Displays the camera number assigned by Motive.

#### **Camera Type**

Displays the model of a selected camera.

#### **Serial Number**

Displays the serial nubmer of a selected camera.

#### **Focal Length**

Displays focal length of the lens on the selected camera.

## Display

#### **Show Field of View**

When this is enabled, the estimated field of view (FOV) of the selected camera will be shown in the perspective viewport.

![](<../../.gitbook/assets/image (985).png>)

#### **Show Frame Delivery Info**

Show of hide frame delivery information from the selected camera. The frame delivery information is used for diagnosing how fast each camera is delivering its frame packets. When enabled, the frame delivery information will be shown in the [camera views](../viewport.md#cameras-view).

#### **Show Aim Assist Reticle**

Show or hide the guide reticle when using the [Aim Assist](../../hardware/aiming-and-focusing.md) button for aiming the cameras.

## Prime Color Camera

Prime color cameras also have the following properties that can be configured:

![Properties of a Prime Color camera.](<../../.gitbook/assets/image (995).png>)

### Resolution

Default: 1920, 1080

This property sets the resolution of the images that are captured by selected cameras. Since the amount of data increases with higher resolution, depending on which resolution is selected, the maximum allowable frame rate will vary. Below is the maximum allowed frame rates for each respective resolution setting.

| Resolution          | Max Frame Rate |
| ------------------- | -------------- |
| 960 x 540 (540p)    | 500 FPS        |
| 1280 x 720 (720p)   | 360 FPS        |
| 1920 x 1080 (1080p) | 250 FPS        |

### Compression Mode

Default: Constant Bit Rate.

This property determines how much the captured images will be compressed. The Constant Bit-Rate mode is used by default and recommended because it is easier to control the data transfer rate and efficiently utilize the available network bandwidth.

**Constant Bit-Rate**

In the Constant Bit-Rate mode, Prime Color cameras vary the degree of image compression to match the data transmission rate given under the Bit Rate settings. At a higher bit-rate setting, the captured image will be compressed less. At a lower bit-rate setting, the captured image will be compressed more to meet the given data transfer rate, but compression artifacts may be introduced if it is set too low.

**Variable Bit-Rate**

Variable Bit-Rate setting is also available for keeping the amount of the compression constant and allowing the data transfer rate to vary. This mode can be beneficial when capturing images with objects that have detailed textures because it keeps the amount of compression same on all frames. However, this may introduce dropped frames whenever the camera tries to compress highly detailed images because it will increase the data transfer rate; which may overflow the network bandwidth as a result. For this reason, we recommend using the Constant Bit-Rate setting in most applications.

### Bit Rate

Default: 50

**Available only while using Constant Bit-rate Mode**

Bit-rate setting determines the transmission rate outputted from the selected color camera. The value given under this setting is measured in percentage (100%) of the maximum data transmission speed, and each color camera can output up to \~100 MBps. In other words, the configured value will indirectly represent the transmission rate in Megabytes per second (MBps). At bit-rate setting of 100, the camera will capture the best quality image, however, it could overload the network if there is not enough bandwidth to handle the transmitted data.

Since the bit-rate controls the amount of data outputted from each color camera, this is one of the most important settings when properly configuring the system. If your system is experiencing 2D frame drops, it means one of the system requirements is not met; either network bandwidth, CPU processing, or RAM/disk memory. In such cases, you could decrease the bit-rate setting and reduce the amount of data output from the color cameras.

**Image Quality**

The image quality will increase at a higher bit-rate setting because it records a larger amount of data, but this will result in large file sizes and possible frame drops due to data bandwidth bottleneck. Often, the desired result is different depending on the capture application and what it is used for. The below graph illustrates how the image quality varies depending on the camera framerate and bit-rate settings.

![](<../../.gitbook/assets/image (989).png>)

{% hint style="info" %}
**Tip: Monitoring data output from each camera**

Data output from the entire camera system can be monitored through the Status Panel. Output from individual cameras can be monitored from the 2D Camera Preview pane when the _Camera Info_ is enabled under the visual aids ([![Viewport16.png](https://v30.wiki.optitrack.com/images/6/6d/Viewport16.png)](https://v30.wiki.optitrack.com/index.php?title=File:Viewport16.png)) option.
{% endhint %}

![](<../../.gitbook/assets/image (952).png>)

### Gamma

Default : 24

Gamma correction is a non-linear amplification of the output image. The gamma setting will adjust the brightness of dark pixels, mid-tone pixels, and bright pixels differently, affecting both brightness and contrast of the image. Depending on the capture environment, especially with a dark background, you may need to adjust the gamma setting to get best quality images.

![](<../../.gitbook/assets/image (958).png>) ![](<../../.gitbook/assets/image (986).png>)
