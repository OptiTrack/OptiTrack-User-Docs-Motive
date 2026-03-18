# Active Marker Tracking: IMU Setup

{% hint style="danger" %}
Currently IMUs are unsupported in Motive 3.0.x, this page is purely for reference purposes.
{% endhint %}

## Overview

This page provides instructions on configuring the active components, Active Tags and/or Active Pucks, that are equipped with inertial measurement unit (IMU) sensors. By fusing the optical tracking data of the active markers with the IMU data, Motive can further stabilize the rotational tracking of the Rigid Bodies and accommodate for tiny jitters throughout the tracking. This is recommended for applications where the stability of rotation tracking data is important, including tracking cameras in virtual production applications, tracking drones in low camera-count setups, and more.

### **Requirements**

* Motive version 2.2 to 2.3.1
* IMU Active Batch Programmer
* Base Station: Firmware 2.2.2 or above
* IMU Active Tags/Pucks: Firmware 2.2.1 or above

### **Additional Information**

* When configured, each Active Base Station can communicate with up to 7 IMU Tags/Pucks.
* When needed, multiple Base Stations can be plugged into the same camera network; as long as they are communicating through a separate channel.
* To use the IMU components, all of the devices, including the Base Station, must have firmware version 2.x or above installed. Please follow the instruction below to check the firmware versions on each device.

## Active Component Setup

For the IMU data to be used for tracking in Motive, unique Uplink IDs must be assigned onto each IMU Tag or Puck using the active batch programmer program. Then, the Uplink IDs will need to be inputted under the properties of the corresponding Rigid Bodies in Motive. Please follow the steps below:

### 1) Download Active Batch Programmer

Use the following link to download the batch programmer used for 2.x firmware. Once downloaded, unzip the downloaded file and launch the EXE file.

* **Batch Programmer Download:**
* [OptiTrack Downloads: Active Batch Programmer](https://optitrack.com/support/downloads/developer-tools.html#active-batch-programmer)

### 2) Check the firmware version and existing configuration

Before setting up the components, we will want to check the existing configurations on the Base Station, Tags, and/or Pucks. To check this, enable the ‘’Read-Only Mode’’ check box at the bottom-left corner of the active batch programmer, and then connect the devices one at a time via USB. Each time a new active component is detected, existing configurations including the firmware version will get listed under the Log section. If any of the settings do not meet the below requirements, you can re-configure them in the next step.

{% hint style="danger" %}
**Important**

When checking the configuration, make sure the Read-Only Mode is enabled. If not, the active batch programmer will upload the settings onto the new Tags that are newly detected by the computer. This could reset the existing configuration that is already on the device.
{% endhint %}

![](<../../.gitbook/assets/image (104) (1).png>)

**Firmware Version**

In order to use IMU Tags/Pucks, all of the active components must have firmware version 2.2.x or above installed. Please check the firmware version on the active components. If the installed firmware is an older version, please [contact us](https://optitrack.com/contact/) for assistance with upgrading the firmware.

**RF Channel**

Please make sure that all of the active components are communicating through the same channel. Check this and take a note of the channel value as this will also need to be inputted into Motive for IMU data. The RF channel can be set anywhere between 11-26.

**Label**

The Labels are active IDs assigned to each marker, and it's important that there are no overlapping labels, or IDs, assigned to the same batch of active Tags/Pucks. This setting is applicable to Active Tags/Pucks only.

After checking the settings, you can unplug the device and connect the next one to check the settings.

### 3) Configure the settings in the Active Batch Programmer

Now that we understand the existing configurations and what needs to be changed, we can configure the active components. To do this, disable the Read-Only Mode in the batch programmer, and settings configured in the IMU batch programmer will get applied to each newly connected device. Please note that this could also reset the existing configuration, thus, make sure to configure only the settings that need to be changed.

**Configure Uplink ID**

For IMU Tags or Pucks, unique Uplink IDs need to be assigned for each of them. For doing this, simply check the box next to the Uplink ID whenever we are configuring IMU Tags or Pucks.

**RF Channel/Label**

Uncheck the boxes next to "Set marker labels" and "Set radio options" unless they also need to be reconfigured.

All of the Tags/Pucks are pre-configured for every set of devices that gets shipped out in the same order, and we also make sure none of the Labels overlap. Thus, users should not need to use this batch programmer in general. The cases when you would want to reconfigure the active components are: 1) When you have purchased new Tags/Pucks to add to the system from the previous order. 2) When there is a need to change the RF communication channel to avoid interferences.

In cases where marker labels or RF channels need to be reconfigured, enable the box next to the corresponding setting in the batch programmer. DO NOT check the box unless the settings need to be changed. When reconfiguring marker labels, ALL of the Tags and Pucks will need to be reconfigured at once, so that the labels do not overlap with other components in the system.

![](<../../.gitbook/assets/image (1042).png>) ![](<../../.gitbook/assets/image (1060).png>)

### 4) Connect an active component

Once we have configured the settings in the batch programmer, connect Active Tags or Pucks one at a time and the programmer will apply the configured settings to the newly connected device, and it will also make sure that the IDs do not overlap in the same batch. Once the settings get applied the details will get listed under the Log.

It’s recommended to note the assigned Uplink IDs for each Tag/Puck so that we can track down the settings easily when needed.

![](<../../.gitbook/assets/image (1044).png>)

### 5) Disconnect and connect remaining devices

Once a device is configured, disconnect and connect the next device to apply the same settings and unique IDs. Repeat this for all of the active components that need to be configured.

## Tag Attachment to Tracked Objects

When using an IMU Active Tag to create a custom Rigid Body, please make sure both the PCB board of the tag and the LEDs are securely attached and rigidly constrained to the object. The IMU sensor fusion will not work correctly if either the markers or the tag are not secured to the rigid object.

## Motive Setup

Now that each of the IMU Tags/Pucks has been assigned with an Uplink ID, the next step is to input this ID into the properties of the corresponding Rigid Bodies in Motive. Also, the RF channel configured for each active component will need to be inputted as well. Follow the below steps to assign Active Tag ID and Active RF Channel property for each Rigid Body:

**1) Launch Motive**

Make sure the configured Active Base Station is connected to the camera system and launch Motive.

**2) Power the IMU Tag/Puck**

Click the power button on the Tag/Puck to start the device. When the Tag/Puck first initializes, the status LEDs will start blink in red and orange rapidly. This indicates that the IMU sensor is attempting to initialize. At this stage, keep the IMU Tag/Puck stationary until the status LED blinks in green indicating that it has completed the initialization.

{% hint style="info" %}
**Note:** Do not hold down on the power button when powering up the Tag/Puck as it will put the device into a boot mode. When in boot mode, it will not track in Motive and two of the LEDs will light up in orange. If this happens, hold down on the power button again to turn off the Tag/Puck and restart it with just a single click on the button.
{% endhint %}

**3) Create a Rigid Body**

Select the active markers associated with a Tag/Puck and create a Rigid Body.

**4) Access advanced rigid properties**

Open the [Properties pane](../../motive-ui-panes/properties-pane/) and select the Rigid Body. Reveal the advanced properties by clicking on "..." menu at the top-right and selecting _Show Advanced_.

![](<../../.gitbook/assets/image (229).png>)

**5) Input IMU Properties: Active Tag ID and RF Channel**

Scroll down to find the IMU section and input the "Uplink ID" value for the corresponding Tag/Puck into. Additionally, input the "RF Channel" used the the corresponding Base Station. Once this is completed the Rigid Body should have the correct properties set to use the IMU in the tag. You can also adjust the Sensor Fusion property to balance the contribution between optical tracking data and IMU data for the Rigid Body solve.

![](<../../.gitbook/assets/image (248).png>)

**6) Check the status**

At this point, the IMU Tags and Pucks are ready to be used. The color of the Rigid Body indicates the status of the IMU data stream.

| Connected                                                                                                                                  | Calibrating                                                                                                                          | No Incoming Data                                                                                                                                                                                                                            | Status      |
| ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| <img src="../../.gitbook/assets/IMU_Status1.png" alt="" data-size="original">                                                              | <img src="../../.gitbook/assets/IMU_Status2.png" alt="" data-size="original">                                                        | <img src="../../.gitbook/assets/IMU_Status3.png" alt="" data-size="original">                                                                                                                                                               | iewport     |
| When the color of Rigid Body is the same as the assigned Rigid Body color, it indicates Motive is connected to the IMU and receiving data. | If the color is orange, it indicate the IMU is attempting to calibrate. Slowly rotate the object until the IMU finishes calibrating. | If the color is red, it indicates the Rigid Body is configured for receiving IMU data, but no data is coming through the designated RF channel. Make sure Active Tag ID and RF channel values mat the configuration on the active Tag/Puck. | Description |

{% hint style="info" %}
**Confirm IMU Tracking**

It may be helpful to double-check to confirm that IMU is working properly. To do this, access the properties of the IMU Rigid Body, set the Min Marker Count Rigid Body property to 2, and set the Tracking Algorithm to Marker Based. Then, cover up all of the active markers on the Tag/Puck except for two, and make sure that Motive is still able to track the Rigid Body rotation.
{% endhint %}

### IMU's per BaseStation

BaseStations are only capable of hosting a finite number of IMUs based on the speed of the framerate in Motive.

{% hint style="info" %}
You can, however, have an unlimited number of active tags associated with a BaseStation if you are not using the IMU data.
{% endhint %}

Below is a table depicting how many IMUs are able to connect per a single BaseStation at varying framerates. BaseStations have 16 radio frequency (RF) channels for use (11-26). Therefore, when adding more than one BaseStation to a system, the IMU count is simply the number of IMUs below multiplied by the number of BaseStations up to 16. For example, if you have 4 BaseStations and you're running at 90Hz, the number of allowable IMUs would be 60 (15\*4=60).

<figure><img src="../../.gitbook/assets/image (13) (1) (2).png" alt=""><figcaption></figcaption></figure>
