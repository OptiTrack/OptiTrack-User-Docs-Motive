# USB Camera Network Overview and Specs

A USB camera system provides high-quality motion capture for small to medium size volumes at an affordable price range. USB camera models include the **Flex series** (Flex 3 and Flex 13) and **Slim 3U** models. USB cameras are powered by the OptiHub, which is designed to maximize the capacity of Flex series cameras by providing sufficient power to each camera, allowing tracking at long ranges.&#x20;

For each USB system, **up to four OptiHubs** can be used. When incorporating multiple OptiHubs in the system, use RCA synchronization cables to interconnect each hub. A USB system is not suitable for a large volume setup because the USB 2.0 cables used to wire the cameras have a 5-meter length limitation.&#x20;

If needed, up to two active USB extensions can be used when connecting the OptiHub to the host PC. However, the extensions should not be used between the OptiHub and the cameras. We do not support using more than 2 USB extensions anywhere on a USB 2.0 system running Motive.

### Cabling the USB System

<figure><img src="../../.gitbook/assets/image (66).png" alt=""><figcaption><p>OptiHub 2 for USB camera systems.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption><p>Wiring diagram of a Flex series camera system.</p></figcaption></figure>

**Main Components**

* Host PC
* USB Cameras
* OptiHub(s) and a power supply for each hub.
* USB 2.0 cables:
  * USB 2.0 Type A/B per OptiHub.
  * USB 2.0 Type B/mini-b per camera.

**OptiHub**

The OptiHub is a custom-engineered USB hub that is designed to be incorporated in a USB camera system. It provides both power and external synchronization options. Standard USB ports do not provide enough power for the IR illumination within Flex 13 cameras and they need to be routed through an OptiHub in order to activate the LED array.

**USB Load Balancing**

When connecting hubs to the computer, load balancing becomes important. Most computers have several USB ports on the front and back, all of which go through two USB controllers. Especially for a large camera count systems (18+ cameras), it is recommended that you evenly split the cameras between the USB controllers to make the best use of the available bandwidth.

**OptiSync**

OptiSync is a custom synchronization protocol which sends the synchronization signals through the USB cable. It allows each camera to have one USB cable for both data transfer and synchronization instead of having separate USB and daisy-chained RCA synchronization cables as in the older models.

{% hint style="info" %}
**Difference Between OptiSync and Wired Sync**

**OptiSync**

* The OptiSync is a custom camera-to-camera synchronization protocol designed for Flex series cameras. The OptiSync protocol sends and receives sync signals over the USB cable, without the need for RCA sync cables. This sync method is only available when using Flex 3 or Flex 13 cameras connected to the OptiHub.

**Wired Sync**

* The Wired Sync is a camera-to-camera synchronization protocol using RCA cables in a daisy chain arrangement. With a master RCA sync cable connecting the master camera to the OptiHub, each camera in the system is connected in series via RCA sync cables and splitters. The **V100:R1 (Legacy)** and the **Slim 3U** cameras utilize Wired Sync only, and therefore any OptiTrack system containing these cameras need to be synchronized through the Wired Sync. Wired Sync is optionally available for Flex 3 cameras.
{% endhint %}

<div><figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption><p>OptiSync</p></figcaption></figure> <figure><img src="../../.gitbook/assets/Wired Sync.png" alt=""><figcaption><p>Wired Sync</p></figcaption></figure></div>

## Checkpoint

At this point, all of the connected cameras will be listed on the [Devices pane](../../motive-ui-panes/devices-pane.md) and the [3D viewport](../../motive-ui-panes/viewport.md) when you start up Motive. Check to make sure all of the connected cameras are properly listed in Motive.

Then, open up the Status Log panel and check there are no 2D frame drops. You may see a few frame drops when booting up the system or when switching between Live and Edit modes; however, this should only occur just momentarily. If the system continues to drop 2D frames, it indicates there is a problem with how the system is delivering the camera data. Please refer to the troubleshooting section for more details.
