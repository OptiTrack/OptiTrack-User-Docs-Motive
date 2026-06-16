---
description: A list of components used in a Prime Color Camera setup.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/movement-sciences/prime-color-camera-setup/prime-color-setup
---

# Prime Color Setup: Required Components

{% hint style="info" %}
For the latest PC specifications, please see the [Quick Start Guide: Prime Color Camera Setup](../../quick-start-guides/quick-start-guide-prime-color-camera-setup.md) page.&#x20;
{% endhint %}

## Hardware

**Prime Color**

The Prime Color is a full-color video camera that is capable of recording synchronized high-speed videos. Powered by a standard PoE connection, the Prime Color can be used as a reference camera in any mocap system.

The camera enables recording of high frame rate videos (up to 500 FPS at 480p) with resolutions up to 1080p (at 250 FPS) by performing onboard compression (H.264) of captured frames.&#x20;

![](<../../.gitbook/assets/image (567).png>)

**eStrobe**

When capturing high-speed videos, the time-length of camera exposures are very short, and providing sufficient lighting becomes critical for obtaining clear images. The eStrobe is designed to optimally brighten the image taken by the Prime Color camera by synchronizing the illuminations of the eStrobe LEDs to the camera exposures. This allows the LEDs to illuminate with precisely the right timing, producing the most efficient and powerful lighting for high-speed video capture.&#x20;

The eStrobe emits only white light, and will not interfere with tracking within the IR spectrum.

{% hint style="info" %}
The eStrobe is for indoor use only. Sunlight should provide sufficient lighting for high-speed capture when filming outdoors.&#x20;
{% endhint %}

![](<../../.gitbook/assets/image (514).png>) ![](<../../.gitbook/assets/image (490).png>)

## Computer Requirements

{% hint style="info" %}
For the latest PC Specifications please see our [Quick Start Guide: Prime Color Camera Setup](../../quick-start-guides/quick-start-guide-prime-color-camera-setup.md) page.&#x20;
{% endhint %}

### **Storage Capacity**

Make sure there is sufficient capacity available on the disk drive where the Take files are saved.&#x20;

Each color camera can upload a large amount of data over the network, causing the recorded _Take_ (TAK) to get pretty large even with a short recording. For example, if a 10 second take was recorded with a total data throughput of 1 GBps, the resulting TAK file will be 10 GB, which can quickly fill up a storage device.&#x20;

If you are exporting the recorded data as video files, re-encoding the videos will reduce the file sizes magnitudes smaller. See: [Re-encoding](prime-color-setup-data-recording-export.md#re-encoding-exported-video).

### **Write Speed**

Ensure the write speed to the storage is fast enough.

Prime Color cameras can output a large amount of data to the RAM memory quickly. If the write speed to the secondary storage device isn't fast enough, the occupied memory in RAM storage may gradually increase to its maximum, resulting in system instability.&#x20;

For recording with just one or two Prime Color cameras, a standard SSD drive will suffice. When using multiple Prime Color cameras, we recommend using a fast storage drive (e.g. M.2 SSD).

### **Network Card**

Prime Color Camera systems with 1-2 cameras can be supported by a 1 Gbps NIC and 1 Gbps uplink port. When running two or more Prime Color cameras, the computer must have a 10 Gbps network adapter with a 10 Gbps uplink port in order to successfully receive all of the data output from the camera system. Please see the [Load Balancing](prime-color-setup-hardware-setup.md#load-balancing) page for more information.&#x20;

{% hint style="info" %}
It is important to update the NIC to the latest drivers, to prevent underutilization. &#x20;

For the [Intel X550-T2 10Gb NIC](https://optitrack.com/accessories/sync-networking/) recommended for Prime Color Camera systems, please install the latest [Intel® Ethernet Adapter Complete Driver Pack](https://www.intel.com/content/www/us/en/download/15084/intel-ethernet-adapter-complete-driver-pack.html).&#x20;

To see which driver is currently installed:

1. Open the _Network Connections_ folder in Windows.&#x20;
2. Right-click the network connection to the Motive switch and select _Properties_.
3. Click the _Configure..._ button.
4. The driver version and date are listed on the _Driver_ tab.
{% endhint %}

<figure><img src="../../.gitbook/assets/NIC Config - Driver tab DISABLE (1).png" alt=""><figcaption><p>NIC Properties:  Driver tab.</p></figcaption></figure>
