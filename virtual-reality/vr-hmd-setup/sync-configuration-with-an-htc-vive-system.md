# Sync Configuration with an HTC Vive System

{% hint style="danger" %}
**OpenVR Driver**

This synchronization setup is not required for integrating HTC Vive with OptiTrack system. For integrating HTC Vive with OptiTrack system, please use the [OptiTrack OpenVR Driver](/broken/pages/xWnUfYD9jJDkWbDdsRsk). This driver will completely override the tracking of an HTC Vive HMD so that the HMD can be tracked just using the OptiTrack system without the lighthouse base stations, and when using the OpenVR driver, synchronization between two systems is not necessary. This article is for specific applications where both lighthouse base station and the OptiTrack system must be running simultaneously.
{% endhint %}

{% hint style="danger" %}
**Notes on the Sync Settings**

The sync settings listed on this page have not been tested with the latest version of the firmware. This means that the appropriate sync offset value indicated on this page might not be correct. For integrating into SteamVR, please consider using [OptiTrack OpenVR Driver](/broken/pages/xWnUfYD9jJDkWbDdsRsk) to completely override the tracking.
{% endhint %}

This article provides instructions on how to synchronize an OptiTrack Motion Capture system with an HTC Vive virtual reality system, specifically the lighthouse base stations, to avoid overlapping of the infrared tracking lights. The HTC Vive system also uses infrared LEDs and lasers for tracking its head-mounted display (HMD) and controllers. When using an OptiTrack mocap system in conjunction with the HTC Vive system, the infrared tracking from the two systems can interfere with each other. For this reason, the two systems must be synchronized in a way so that the two different tracking lights do not temporally overlap. Currently, sync configurations with only OptiTrack Prime-series camera systems have been tested.

Let’s go through the synchronization setup. The following setup instructions assume that the two tracking base stations of the HTC Vive system are set to channel b and c and are **optically synchronized**. The channel b base station will serve as the master device for synchronizing the two systems. Sync out signal from the channel b station will feed into one of the input ports on the eSync 2, and a sync offset (specified in microseconds, or μs) will be applied to so that IR lights from the two systems don’t interfere with each other. The following section describes the instructions in detail.

{% hint style="info" %}
**Note:**

* The eSync 2 is required in order to synchronize HTC Vive lighthouses with the camera system.
* Synchronization with Flex camera systems is not supported.
{% endhint %}

## Synchronization Configuration

#### **Step 1: Set up the HTC Vive system.**

The base stations will synchronize optically in this setup. Refer to the respective documentation for more details on setting up the HTC Vive system. Set the tracking stations to channels b and c, so that they are optically synchronized (in the absence of a sync cable connection between them).

#### **Step 2: Set up the OptiTrack mocap system.**

Refer to the [Hardware Setup](../../hardware/) wiki pages for more details.

#### **Step 3: Connect the sync output from the channel b base station into the input port 1 of the eSync 2 synchronization hub.**

The sync output of the base stations use 3.5 mm stereo (TRS) cables, whereas the Input ports of the eSync 2 are BNC ports. You will need to use a stereo female to RCA male adapter (e.g. [http://www.monoprice.com/product?p\_id=5612](http://www.monoprice.com/product?p_id=5612)) as well as an RCA-to-BNC adaptor (included with the eSync 2) to connect the channel b base station and the eSync 2 hub. After attaching the stereo to RCA adaptor, connect the red RCA cable into the eSync 2 using a BNC adapter, as shown in the following photo.

![Connecting an HTC Vive system into the eSync 2.](<../../.gitbook/assets/image (805).png>)

#### **Step 4: Motive: Synchronization pane. Configure the synchronization in Motive.**

Open the Synchronization pane in Motive, and set the synchronization type to Custom Synchronization.

#### **Step 5: Motive: Synchronization pane. Configure the Sync Input.**

Set the Sync Input to Input 1, which was the input port of the eSync 2 where the sync cable was connected to. If the sync cable is properly connected and the HTC Vive system is properly working, the bottom signal monitor will display a frequency of approximately 60 Hz detected through the Input 1 port of the eSync 2. Note that this configuration will synchronize the OptiTrack camera system to the sync signal coming through the Input port.

#### **Step 6: Motive: Synchronization pane. Introduce Sync Offset (μs).**

Now that the OptiTrack system’s shutter timing is synchronized with the base stations of the HTC Vive system, you will need to introduce a sync offset to avoid overlapping of the tracking lights. The following list of offset sync parameters are tested to avoid the interference. Input these parameters into the Synchronization pane. If you wish to increase the final frame rate of the mocap system, you will need to apply a multiplier.

* Final Frame Rate: 120 Hz
* Sync Multiplier: 2
* Sync Offset: 1780 μs
* Final Frame Rate: 240 Hz
* Sync Multiplier: 4
* Sync Offset: 3150 μs

![Custom synchronization configuration without applying multipliers to the final frame rate. 60 Hz input signal detected for the connected input under the Input Monitor.](<../../.gitbook/assets/image (748).png>)

![Custom synchronization configuration with multiplier (X2) applied to the input signal, resulting in final frame rate of approx. 120 Hz.](<../../.gitbook/assets/image (822).png>)

{% hint style="danger" %}
**Notes on the Sync Settings**

The sync settings listed on this page have not been tested with the latest version of the firmware. This means that the appropriate sync offset value indicated on this page might not be correct. For integrating into SteamVR, please consider using [OptiTrack OpenVR Driver](/broken/pages/xWnUfYD9jJDkWbDdsRsk) to completely override the tracking.
{% endhint %}

#### **Step 7: Motive: Synchronization pane. Apply sync configuration.**

Press _Apply_ to employ the sync configuration. The tracking IR lights from both systems will no longer interfere, and the HTC Vive components will be working properly and available in the SteamVR application.

#### **Step 8: Motive: Cameras pane. Lower the camera exposure on the OptiTrack system.**

Another important note is that high camera exposure settings may cause IR light from the base stations to be detected by the OptiTrack system. It's suggested to keep the camera exposure below 1000 us for all of the cameras.

Now that the two systems are synchronized to avoid the IR interference, both systems can be used together to provide immersive VR experiences. Note that the instructions listed on this page are tested to work with HTC Vive system, but alternative approaches may also be possible.
