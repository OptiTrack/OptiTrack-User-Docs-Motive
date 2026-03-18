# Prime Color Setup: Required Components

This page is a list of hardware used in a Prime Color Camera setup.&#x20;

{% hint style="info" %}
For the latest PC Specifications please see our [Quick Start Guide: Prime Color Camera Setup](../../quick-start-guides/quick-start-guide-prime-color-camera-setup.md) page.&#x20;
{% endhint %}

## Overview

**Prime Color**

The Prime Color is a full-color video camera that is capable of recording synchronized high-speed and videos. It can also be hooked up to a mocap system and used as a reference camera. The camera enables recording of high frame rate videos (up to 500 FPS at 480p) with resolutions up to 1080p (at 250 FPS) by performing onboard compression (H.264) of captured frames. It connects to the camera network and receives power by a standard PoE connection.

![](<../../.gitbook/assets/image (782).png>)

**eStrobe**

When capturing high-speed videos, the time-length of camera exposures are very short, and thus, providing sufficient lighting becomes critical for obtaining clear images. The eStrobe is designed to optimally brighten the image taken by Prime Color camera by precisely synchronizing the illuminations of the eStrobe LEDs to each camera exposure. This allows the LEDs to illuminate at a right timing, producing the most efficient and powerful lighting for the high-speed video capture. Also, the eStrobe emits white light only, and it will not interfere with the tracking within the IR spectrum.

{% hint style="info" %}
The eStrobe is intended for indoor use only. For capturing outdoors, the sunlight will provide sufficient lighting for the high-speed capture.
{% endhint %}

![](<../../.gitbook/assets/image (750).png>) ![](<../../.gitbook/assets/image (824).png>)

## Computer Requirements

### **General Requirements**

{% hint style="info" %}
For the latest PC Specifications please see our [Quick Start Guide: Prime Color Camera Setup](../../quick-start-guides/quick-start-guide-prime-color-camera-setup.md) page.&#x20;
{% endhint %}

## **Storage Capacity**

Since each color camera can upload a large amount of data over the network, the size of the recorded _Take_ (TAK) can get pretty large even with a short recording. For example, if a 10-second take was recorded with a total data throughput of 1-GBps, the resulting TAK file will be 10-GB, and it can quickly fill up the storage device. Please make sure there is enough capacity available on the disk drive. If you are exporting out the recorded data onto video files after they are captured, re-encoding the videos will help with reducing the files magnitudes smaller. See: [Re-encoding](prime-color-setup-data-recording-export.md#re-encoding-exported-video)

## **Write Speed**

Since Prime Color cameras can output a large amount of data to the RAM memory quickly, it is also important that the write-out speed to the storage is also fast enough. If the write-out speed to secondary drive isn't fast enough, the occupied memory in RAM storage may gradually increase to its maximum. For recording with just a one or two Prime Color cameras, standard SSD drive will do its job. However, when using multiple Prime Color cameras, it is recommended to use a fast storage drive (e.g. M.2 SSD) that can quickly write out the recorded capture that from the RAM.

## **Network Card**

Prime Color Camera setups with 1-2 cameras can be supported by a 1Gbps NIC and 1Gbps uplink port. When running two or more Prime Color cameras, the computer must have a 10Gbps network adapter with a 10Gbps uplink port in order to successfully receive all of the data outputted from the camera system. Please see [Load Balancing](prime-color-setup-hardware-setup.md#load-balancing) section for more information.&#x20;

{% hint style="warning" %}
It is important to update your NIC to the latest drivers, failing to do so can result in underutilization of the NIC.  For the [Intel X540-T1 10Gb NIC](https://optitrack.com/accessories/sync-networking/) that we recommend for Prime Color Camera setups, please install the latest [Intel® Ethernet Adapter Complete Driver Pack](https://www.intel.com/content/www/us/en/download/15084/intel-ethernet-adapter-complete-driver-pack.html). You can verify which driver is installed via the Devices Manger on Windows.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>
