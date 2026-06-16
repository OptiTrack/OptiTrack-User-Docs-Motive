---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/movement-sciences/prime-color-camera-setup/prime-color-setup-hardware-setup
---

# Prime Color Setup: Hardware Setup

### Camera Lens

Different types of lenses can be equipped on a Prime Color camera as long as the lens mount is compatible, however, for Prime Color cameras, we suggest using C-mount lenses to fully utilize the imager. Prime Color cameras with C-mount can be equipped with either the 12mm F#1.8 lenses or the 6.8mm F#1.6 lenses. The 12mm lens is zoomed in more and is more suitable for capturing at long ranges. On the other hand, the 6.8mm lens has a larger field of view and is more suitable for capturing a wide area. Both lenses have adjustable f-stop and focus settings, which can be optimized for different capture environments and applications.

* **F-Stop:** Set the f-stop to a low value to make the aperture size bigger. This will allow in more light onto the imager, improving the image quality. However, this may also decrease the camera's depth of field, requiring the lens to be focused specifically on the target capture area.
* **Focus:** For best image quality, make sure the lenses are focused on the target tracking area.

{% hint style="info" %}
**6.5mm F#1.6 lens**: When capturing 1080p images with 6.5mm F#1.6 lens, you may see vignetting in each corner of the captured frames due to imager size limitations. For larger FOV, please use the 6.8mm F#1.6 lens to avoid this vignetting issue.
{% endhint %}

### Load Balancing

#### **Data Bandwidth**

Before going into details of setting up a system with Prime Color cameras, it is important to go over the data bandwidth availability within the camera network. At its maximum [bit-rate](prime-color-camera-setup-camera-settings.md#bit-rate) setting for capturing the best quality image, one Prime Color camera can transmit data at a rate of up to \~100 Megabytes-per-second (MBps), or \~800 Megabits-per-second (Mbps). For a comparison, a tracking camera in [Object Mode](../../motive/camera-video-types.md) outputs data at a rate less than 1MBps, which is several magnitudes smaller than the output from a Prime Color camera. A standard network switch (1 Gb switch) and network card only support network traffic of up to 1000 Mbps (or 1 Gbps). When Prime Color camera(s) are used, they can take up a large portion, or all, of the available bandwidth, and for this reason, extra attention to bandwidth use will be needed when first setting up the system.

When there is not enough available bandwidth, captured 2D frames may drop out due to the data bottleneck. Thus, it is important to take the bandwidth consumption into account and make sure an appropriate set of network switches (PoE and Uplink), Ethernet cables, and a network card is used. If a 1-Gb network/uplink switch is used, then only 1-2 Prime Color camera can be used at its maximum bit-rate setting. If three or more Prime Color cameras need to be used, then either a 10-Gb network setup will be required OR the [bit-rate](prime-color-camera-setup-camera-settings.md#bit-rate) setting will need to be turned down. A lower bit-rate will further compress the image with a tradeoff on the image quality, which may or may not be acceptable depending on the capture application.&#x20;

{% hint style="success" %}
Upgraded PC specifications and settings can aid with stability in increased bit rates, please see our [Quick Start Guide: Prime Color Camera Setup](../../quick-start-guides/quick-start-guide-prime-color-camera-setup.md) page for more information.&#x20;
{% endhint %}

{% hint style="info" %}
**Detecting Dropped 2D Frames**

Every 2D frame drops are logged under the[ Log Pane](../../motive-ui-panes/log-pane.md), and it can also be identified in the Devices pane. It will be indicated with a warning sign next to the corresponding camera. You may see a few frame drops when booting up the system or when switching between Live and Edit modes; however, this should only occur just momentarily.&#x20;

If the system continues to drop 2D frames, that indicates there is a problem with receiving the camera data. If this is happening with Prime Color cameras, try lowering down the bit-rate, and if the system stops dropping frames, that means there wasn’t enough bandwidth availability. To use the cameras in a higher bit-rate setting, you will need to properly balance out the load within the available network bandwidth or [upgrade your PC specifications and settings](../../quick-start-guides/quick-start-guide-prime-color-camera-setup.md).

_Note: Due to the current architecture of our bug reporting in Motive, a single color camera will not display dropped frame messages. If you need these messages you will need to either connect another camera or an eSync 2 into the system._
{% endhint %}

### Cabling

#### **Power**

Each Prime Color camera must be uplinked and powered through a standard PoE connection that can provide at least 15.4 watts to each port simultaneously.

{% hint style="warning" %}
Please note that if your aggregation switch is PoE, you can plug your Prime Color Cameras **directly** into the aggregation switch. PoE injectors are **optional** and will only be required if your aggregation switch is not PoE.
{% endhint %}

{% tabs %}
{% tab title="One or Two Color Cameras" %}
Prime Color cameras connect to the camera system just like other Prime series camera models. Simply plug the camera onto a PoE switch that has enough available bandwidth and it will be powered and synchronized along with other tracking cameras. When you have two color cameras, they will need to be distributed evenly onto different PoE switches so that the data load is balanced out.

<figure><img src="../../.gitbook/assets/image (845).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
For 1-2 Prime Color Cameras it is recommended to use 1Gbps network switch with 1Gbps uplink port and a 1Gpbs NIC or higher. For 3+ Prime Color Cameras it is required to use network switches with a 10Gbps uplink port in conjunction with a 10Gbps designated NIC and their appropriate drivers.&#x20;

NIC drivers may need to be installed via disc or downloaded from the manufacture's support website. If you're unsure of where to find these drivers or how to install them, please reach out to our [Support ](https://optitrack.com/support/)team.
{% endhint %}
{% endtab %}

{% tab title="Multiple Color Cameras" %}
When using multiple Prime Color cameras, we recommend connecting the color cameras directly into the 10-gigabit aggregation (uplink) switch, because such setup is best for preventing bandwidth bottleneck. A PoE injector will be required if the uplink switch does not provide PoE. This allows the data to travel directly onto the uplink switch and to the host computer through the 10-gigabit network interface. This will also separate the color cameras from the tracking cameras.

<figure><img src="../../.gitbook/assets/image (795).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### Ethernet Cable Requirements

**Cable Type**

There are multiple categories for Ethernet cables, and each has different specifications for maximum data transmission rate and cable length. For an Ethernet based system, Cat6 or above Gigabit Ethernet cables should be used. 10 Gigabit Ethernet cables – Cat6a or above — are recommended in conjunction with a 10 Gigabit uplink switch for the connection between the uplink switch and the host PC in order to accommodate for high data traffic.

{% hint style="info" %}
**Note**

10Gb uplink switches, NICs, and cables are recommended for large camera counts or high data cameras like the Prime Color cameras. Typically 1Gb switches, NICs, and cables should be enough to accommodate smaller and moderately sized systems. If you're unsure of whether or not you need more than 1Gb, please contact one of our Sales Engineers [here](https://optitrack.com/contact/) or see our [Cabling and Load Balancing](../../hardware/cabling-and-wiring/cabling-and-load-balancing.md) page for more information.
{% endhint %}

**Electromagnetic Shielding**

We recommend using only cables that have electromagnetic interference shielding. If unshielded cables are used, cables in close proximity to each other have the potential to create data transfer interference and cause cameras to stall in Motive.

{% hint style="danger" %}
Unshielded cables do not protect the cameras from Electrostatic Discharge (ESD), which can damage the camera. Do not use unshielded cables in environments where ESD exposure is a risk.&#x20;
{% endhint %}

### eStrobes

#### **eStrobe Setup**

The eStrobe synchronizes with Prime Color cameras through RCA cable connection. It receives exposure signals from the cameras and synchronizes its illuminations correspondingly. Depending on the frame rate of the camera system, the eStrobe will vary its illumination frequency, and it will also vary the percent duty cycle depending on the exposure length. Multiple eStrobes can be daisy-chained in series by relaying the sync signal from the output port to the input port of another as shown in the diagram.

{% tabs %}
{% tab title="eStrobe with Single Prime Color Camera" %}
![Click image to enlarge.](<../../.gitbook/assets/image (209).png>)

{% hint style="info" %}
**Illumination:**

The eStrobe emits only white light and does not interfere with tracking within the IR spectrum. In other words, its powerful illumination will not introduce noise to the IR tracking data.
{% endhint %}

{% hint style="info" %}
**Power Requirement:**

The amount of power drawn by each eStrobe will vary depending on the system frame rate as well as the length of camera [exposures](../../motive-ui-panes/devices-pane.md), because the eStrobe is designed to vary its illumination rate and percent duty cycle depending on those settings.At maximum, one eStrobe can draw up to 240 Watts of power. A typical 110V wall outlet outputs 110V @ 15A; which totals up to 1650W of power. Also, there may be other factors such as restrictions from the surge protector or extension cords that are used. Therefore, in general, we recommend connecting no more than five eStrobes onto a single power source.
{% endhint %}

{% hint style="danger" %}
**Warning:**

* Please be aware of the hot surface. The eStrobe will get very hot as it runs.
* Avoid looking directly at the eStrobe, it could damage your eyes.
* Make sure the power strips or extension cords are able to handle the power. Using light-duty components could damage the cords or even the device if they cannot sufficiently handle the amount of the power drawn by the eStrobes.
* The eStrobe is not typically needed for outdoor use. Sunlight should provide enough lighting for the capture.
{% endhint %}
{% endtab %}

{% tab title="eStrobe with Multiple Prime Color Cameras" %}
<figure><img src="../../.gitbook/assets/image (802).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### Capturing without eStrobes

When capturing without eStrobes, the camera entirely relies on the ambient lighting to capture the image, and the brightness of the captured frames may vary depending on which type of light source is used. In general, when capturing without an eStrobe, we recommend setting the camera at a lower framerate (30\~120 FPS) and increasing the camera exposure to allow for longer exposure time so that the imager can take in more light.

**Indoor**

When capturing indoors without the eStrobe, you will be relying on the room lighting for brightening up the volume. Here, it is important to note that every type of artificial light source illuminates, or flickers, at a certain frequency (e.g. fluorescent light bulbs typically flicker at 120Hz). This is usually fast enough so that the flickering is not noticeable to human eyes, however, with high-speed cameras, the flickering may become apparent.

When Prime Color captures at a frame rate higher than the ambient illumination frequency, you will start noticing brightness changes between consecutive frames. This happens because, with mismatching frequencies, the cameras are exposing at different points of the illumination phase. For example, if you capture at 240FPS with 120Hz light bulbs lighting up the volume, brightness of captured images may be different in even and odd numbered frames throughout the capture. Please take this into consideration and provide appropriate lighting as needed.

![Incandescent light flickering. The video was captured at (121 FPS).](<../../.gitbook/assets/image (1058).png>)

{% hint style="info" %}
**Info: Frequencies of typical light bulbs**

* **Fluorescent:** Fluorescent light bulbs typically illuminate at 120 Hz with 60 Hz AC input.
* **Incandescent:** Incandescent light bulbs typically illuminate at 120 Hz with 60 Hz AC input.
* **LED light bulbs:** Variable depending on the manufacturer.
* **eStrobe:** LEDs on the eStrobe will be synchronized to the exposure signal from the cameras and illuminate at the same frequency.
{% endhint %}

**Outdoor**

When capturing outdoors using Prime Color cameras, sunlight will typically provide enough ambient lighting. Unlike light bulbs, sunlight is emitted continuously, so there is no need to worry about the illumination frequency. Furthermore, the sun is bright enough and you should be able to capture high-quality images by adjusting only the f-stop (aperture size) and the exposure values.

### Setup Check-Point

Now that you have set up a camera system with Prime Color, all of the connected cameras should be listed under the [Devices pane](../../motive-ui-panes/devices-pane.md). At this point, you would want to launch Motive and check the following items to make sure your system is operating properly.

* **2D Frame Delivery:** There should be no dropped 2D frames. You can monitor this under the [Log pane](../../motive-ui-panes/log-pane.md) or from the [Devices pane](../../motive-ui-panes/devices-pane.md). If frame drops are reported continuously, you can lower down the [bit-rate](prime-color-camera-setup-camera-settings.md#bit-rate) setting or revisit the network configuration and make sure the data loads are balanced out. For more information, [Data Bandwidth](prime-color-setup-hardware-setup.md#data-bandwidth) section of this page.
* **CPU Usage:** Open the windows task manager and check the CPU processing load. If only one of the CPU core is fully occupied, the CPU is not fast enough to process data from the color camera. In this case, you will want to use a faster CPU or lower down the [bit-rate](prime-color-camera-setup-camera-settings.md#bit-rate) setting.
* **RAM Usage:** Open the windows task manager and check the memory usage. If the RAM usage slowly creeps up to the maximum memory while recording a take, it means the disk driver is not fast enough to write out the color video from RAM. You will have to reduce the bit-rate setting or use a faster disk drive (e.g. M.2 SSD).
* **Hard Drive Space:** Make sure there is enough memory capacity available on the computer. Take files (TAK) with color camera data can be quite large, and it could quickly fill up the memory, especially, when recording lightly-compress video from multiple color cameras.
