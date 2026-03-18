# Prime Color Camera Setup: Camera Settings

When you launch Motive, connected Prime Color cameras will be shown in Motive, and you will be able to configure the settings as you would do for other tracking cameras. Open up the [Devices pane](../../motive-ui-panes/devices-pane.md) and the [Properties pane](../../motive-ui-panes/properties-pane/), and select a Prime Color camera(s). On the Properties pane, key properties that are specific to the selected color cameras will be listed.&#x20;

Optimizing these settings are important in order to obtain best quality images without overflooding the network bandwidth. The key settings for the color cameras are _image resolution_, _gamma correction_, as well as _compression mode_ and _bit-rate_ settings, which will be covered in the following sections.

![](https://v30.wiki.optitrack.com/images/thumb/2/23/ColorCam_CameraProperties_21.png/750px-ColorCam_CameraProperties_21.png)

### Camera Resolution

Default: 1920, 1080

This property sets the resolution of the images that are captured by selected cameras. Since the amount of data increases with higher resolution, depending on which resolution is selected, the maximum allowable frame rate will vary. Below is the maximum allowed frame rates for each respective resolution setting.

| Resolution          | Max Frame rate |
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

### Bit-rate

Default: 50

**Available only while using Constant Bit-rate Mode**

Bit-rate setting determines the transmission rate outputted from the selected color camera. The value given under this setting is measured in percentage (100%) of the maximum data transmission speed, and each color camera can output up to \~100 MBps. In other words, the configured value will indirectly represent the transmission rate in Megabytes per second (MBps). At bit-rate setting of 100, the camera will capture the best quality image, however, it could overload the network if there is not enough bandwidth to handle the transmitted data.

Since the bit-rate controls the amount of data outputted from each color camera, this is one of the most important settings when properly configuring the system. If your system is experiencing 2D frame drops, it means one of the system requirements is not met; either network bandwidth, CPU processing, or RAM/disk memory. In such cases, you could decrease the bit-rate setting and reduce the amount of data output from the color cameras.

**Image Quality**

The image quality will increase at a higher bit-rate setting because it records a larger amount of data, but this will result in large file sizes and possible frame drops due to data bandwidth bottleneck. Often, the desired result is different depending on the capture application and what it is used for. The below graph illustrates how the image quality varies depending on the camera framerate and bit-rate settings.

![](https://v30.wiki.optitrack.com/images/3/3e/ColorCamera_NoStrobe.png)

{% hint style="info" %}
**Tip: Monitoring data output from each camera**

Data output from the entire camera system can be monitored through the Status Panel. Output from individual cameras can be monitored from the 2D Camera Preview pane when the _Camera Info_ is enabled under the visual aids ([![Viewport16.png](https://v30.wiki.optitrack.com/images/6/6d/Viewport16.png)](https://v30.wiki.optitrack.com/index.php?title=File:Viewport16.png)) option.
{% endhint %}

![](<../../.gitbook/assets/image (747).png>)

### Gamma

Default : 24

Gamma correction is a non-linear amplification of the output image. The gamma setting will adjust the brightness of dark pixels, midtone pixels, and bright pixels differently, affecting both brightness and contrast of the image. Depending on the capture environment, especially with a dark background, you may need to adjust the gamma setting to get best quality images.

![](<../../.gitbook/assets/image (778).png>) ![](<../../.gitbook/assets/image (832).png>)

### LED

Default: On

If you are using the [eStrobes](prime-color-setup-hardware-setup.md#estrobes) to light up the capture volume, the LED setting must be enabled on the Prime Color cameras which the eStrobes connect to. When this setting is enabled, the Prime Color camera will start outputting the signals from its RCA sync output port, allowing the eStrobes to receive this signal and illuminate the LEDs.
