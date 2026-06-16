---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/imu-sensor-fusion
---

# IMU Sensor Fusion

## Overview

An Inertial Measurement Unit (IMU) communicates coordinate data to Motive either through an Ethernet cable or through a connected BaseStation. When connected to an Active device containing an Inertial Measurement Unit (IMU), Motive is able to fuse the inertial and optical sources of data to produce more precise and accurate tracking.&#x20;

The process of merging the IMU data with the optical data is known as Sensor Fusion.&#x20;

<figure><img src="../.gitbook/assets/IMU Fused Asset Sample.png" alt=""><figcaption><p>Rigid body (Puck) with sensor fusion.</p></figcaption></figure>

## Quick Start Guide - Auto Configure

First and foremost, ensure that your tracking volume is setup with optimal conditions and your Calibration is Exceptional.&#x20;

1. Power on either a CinePuck or an Active IMU puck.&#x20;
2. Set the puck on a level surface and wait until the puck is finished calculating its bias. See [below ](imu-sensor-fusion.md#cinepuck-and-other-imu-active-puck-indicator-lights)for a description of the various indicator lights.
3. Select the markers from the active device and create a Rigid Body Asset. Please see the the [Create Rigid Body](../motive-ui-panes/builder-pane.md#creating-rigid-body) section of the [Builder pane](../motive-ui-panes/builder-pane.md) page for further instructions.&#x20;

{% hint style="warning" %}
We highly recommend ensuring all markers can be tracked with **minimal occlusions** for the best results when pairing and aligning the Rigid Body to the IMU.&#x20;
{% endhint %}

4. The Active Tag is displayed in the Devices pane. When selected, the tag's properties are visible in the Properties pane. These properties are read-only.&#x20;

<figure><img src="../.gitbook/assets/IMU Properties and Devices for Wired CinePuck 1 Not paired.png" alt=""><figcaption><p>Properties pane and Devices pane for an unpaired IMU (Wired CinePuck).  </p></figcaption></figure>

5. Right click the Rigid Body in the _Assets_ pane and select _Active Tags -> Auto-Configure Active Tag._&#x20;

<figure><img src="../.gitbook/assets/Assets Pane - Active Tag context menu.png" alt=""><figcaption><p>Context Menu from the Assets pane.</p></figcaption></figure>

6. Move the active device slowly around at least 3 axes. The status will update in the the Properties pane, and the Alignment status in the Devices pane will display a circled wave: <img src="../.gitbook/assets/IMU Alignment in progress.png" alt="" data-size="line">. The IMU label will also display the status in the Viewport. &#x20;

<figure><img src="../.gitbook/assets/IMU Properties and Devices for Wired CinePuck 2 DURING pairing.png" alt=""><figcaption><p>Active Tag status and Properties during alignment. </p></figcaption></figure>

7. Continue rotating the active device until the Alignment status in the Devices pane updates to a circled checkmark: ![](<../.gitbook/assets/IMU Sensor Fusion Successful Alignment (1).png>) . The IMU is now successfully paired and aligned with the Rigid Body.&#x20;

<figure><img src="../.gitbook/assets/IMU Properties and Devices for Wired CinePuck 3 Paired.png" alt=""><figcaption><p>Properties for an Active Tag that is successfully fused to the Rigid Body. </p></figcaption></figure>

8. Attach the CinePuck to the cinema camera or the Active Puck to the object to be tracked. The sensor-fused Puck is now available for seamless and robust tracking.&#x20;

#### If the IMU Does Not Pair&#x20;

This could mean that an IMU device is not present in the Rigid Body or it is not being recognized.&#x20;

* Check the _Devices_ pane to see if the IMU Device is populated in the table with its Uplink ID.&#x20;
* If the device is not listed, use [Active Batch Programmer](../active-classic/configuration/active-batch-programmer.md) to check the RF Channel and Uplink ID. If the device is set to the correct RF channel and an IMU does not appear, the active device may not have an IMU.

**If the IMU Doesn't Fuse**

* Try rotating the Puck on more axes. &#x20;
* Check the label above the rigid body asset to see if it is collecting alignment samples. If the number of samples does not increase as you rotate the tracker, the optical data may not be reliable enough to calculate an alignment.
* Unpair the IMU and complete the pairing and alignment process again.&#x20;

## Active Tag Context Menu Options

### Viewport Active Tag Menu

Active Tag options are also available by right clicking a Rigid Body in the [Viewport](../motive-ui-panes/viewport.md):

<figure><img src="../.gitbook/assets/Viewport Context Menu - Active Tag  (2).png" alt=""><figcaption><p>The Active Tag context menu from the Viewport.</p></figcaption></figure>

#### Auto-Configure Active Tag

This option pairs and aligns the Rigid Body to the IMU Tag all at once. This is the recommended method when getting started as it is also the quickest.&#x20;

#### Set Auto Pair&#x20;

Auto-Pair causes Motive to search for an IMU whose movements match the rigid body asset. Rotate the rigid body and Motive will find and pair it to the IMU automatically.

Once paired, this alignment status will be indicated in the _3D Viewport_ IMU visual. The asset name will display in the _Devices_ pane Active Tag Paired Asset column, and in the _Assets_ pane's Active Tag column.&#x20;

{% hint style="info" %}
**Auto-Configure vs. Auto-Pair**

Auto-Configure sets a property that allows tracking to continue if there are no markers visible to the cameras, whereas Auto-Pair does not.&#x20;

Both functions begin the alignment process immediately after pairing.&#x20;
{% endhint %}

#### Unpair Active Tag

This will remove a paired Tag from the Rigid Body.&#x20;

#### Align

Manually align the Tag to the Rigid Body after pairing. A minimum of 10 alignment samples are required; see the IMU label in the Viewport for the total number of samples currently collected.&#x20;

#### Remove Alignment&#x20;

Remove alignment from the Rigid Body while still paired to the IMU.&#x20;

#### Orient Pivot to IMU

Sets the pivot orientation to reflect the orientation of the IMU (internal). Motive will recognize the physical orientation of the IMU within the Puck and adjust the Rigid Body pivot bone appropriately.&#x20;

### Devices Pane Active Tag Menu

Other options are available by right-clicking the tag in the _Devices_ pane:

<figure><img src="../.gitbook/assets/Devices Pane - Active Tag context menu.png" alt=""><figcaption><p>The Active Tag context menu from the Devices pane. </p></figcaption></figure>

{% hint style="info" %}
**Groups**

Groups are a convenient way to manage multiple devices that require the same settings.&#x20;

Click the <img src="../.gitbook/assets/Devices Pane - show device groups button.png" alt="" data-size="line"> button at the top of the _Devices pane_ to select from the list of available [Device Groups](../motive-ui-panes/devices-pane.md#device-groups-panel).&#x20;
{% endhint %}

#### Add to Group

Add selected devices to a new or existing group with the _Add to Group_ option.&#x20;

#### Remove from Groups

Removes the selected devices from all groups.&#x20;

#### Manual Pair

If manually pairing from the _Devices_ pane:

* Choose the Rigid Body you would like to pair to the selected Tag in the _Devices_ pane.&#x20;

If manually pairing from the _Assets_ pane:

* Choose the Active Tag you would like to pair to the selected Rigid Body in the _Assets_ pane.&#x20;

## Assets Pane

#### Active Tag Column

Right click the header of the _Assets_ pane to add columns. For this IMU workflow, we recommend adding the Active Tag column. The Active Tag column will display the status along with the ID of the paired device.&#x20;

<figure><img src="../.gitbook/assets/Assets Pane - IMU Auto-pairing.png" alt=""><figcaption><p>The Active Tag column in the Assets pane.</p></figcaption></figure>

* **Auto-pairing:** This status appears while the auto-pair process is running on the device.&#x20;
* **Paired:** Indicates that the IMU is paired to the Rigid Body, but sensor fusion has not been performed yet.
* **Fused:** The IMU is paired to the Rigid Body and sensor fusion has been completed.&#x20;
* **None:** The Rigid Body does not have an IMU or is not yet Paired, this column will display "None."&#x20;

<figure><img src="../.gitbook/assets/Assets Pane - IMU Fused and Paired.png" alt=""><figcaption><p>Fused and Paired IMUs in the Assets pane.</p></figcaption></figure>

## 3D Viewport

If the [IMU label](imu-sensor-fusion.md#imu-label) is enabled in the [Rigid Body Properties](../motive-ui-panes/properties-pane/properties-pane-rigid-body.md), the Viewport will display the status of the IMU Sensor Fusion process.&#x20;

#### Rotate to Pair IMU

After Auto or Manually pairing, the status label above the Rigid Body will display _Rotate to Pair IMU_.&#x20;

<figure><img src="../.gitbook/assets/IMU Sensor Fusion START.png" alt=""><figcaption><p>Stage 1 of Sensor Fusion: IMU is paired but alignment has not started. </p></figcaption></figure>

#### Rotate to Align (##/100)&#x20;

Move and rotate the Rigid Body around to complete the alignment. The IMU label will display the status of the alignment as a fraction, i.e. 27/100.&#x20;

{% hint style="info" %}
**%:**

The Percentage of IMU packets that an IMU Tag is successfully delivering for every 100 frames. 100% indicates all packets are going through; 80% indicates 20% of IMU packets were dropped.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/IMU Sensor Fusion in progress.png" alt=""><figcaption><p>Alignment progress displayed in the IMU label.</p></figcaption></figure>

#### Fused&#x20;

The IMU is now successfully paired and aligned with the Rigid Body.&#x20;

<figure><img src="../.gitbook/assets/IMU Sensor Fusion completed.png" alt=""><figcaption><p>An Active Puck with a successful Sensor Fusion. </p></figcaption></figure>

#### Optical Status

The Optical status at the end of the label indicates how many of the Rigid Body's markers can be seen and tracked within the volume.

* **Optical Good:** most markers can be seen and tracked.
* **Optical:** the minimum number of markers can be seen and tracked.
* **No Optical:** either fewer than the minimum or no markers can be seen and tracked.&#x20;

## Devices Pane Active Tag Section

Tags recognized by Motive are listed in the _Devices_ pane under the Active Tag section. Please see the section above for [context menu options](imu-sensor-fusion.md#active-tag-context-menu-options) for this pane.&#x20;

{% hint style="info" %}
Only devices with firmware 2.2 and above are included in the Devices pane.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/Devices Pane - Active Tag section.png" alt=""><figcaption><p>Active Tag section of the Devices pane.</p></figcaption></figure>

#### Name

The Name identifies the type of tag, i.e., AnchorPuck, Wired CinePuck. For wireless devices, the Name is set to _Tag ##:##_, where the first set of numbers indicates the RF Channel and the second the Uplink ID. For example, Tag 22:02 is on RF Channel 22 and has an Uplink ID of 2.&#x20;

#### Paired Asset

When an Asset is paired to the Active Tag, this column displays the associated Rigid Body name, as shown in the _Assets_ pane.&#x20;

#### Aligned

The Aligned column will show the Aligned status of the Active Tag.&#x20;

* If the tag is unpaired, the circled x icon will appear. <img src="../.gitbook/assets/image (1455).png" alt="" data-size="original">
* If the tag is aligning with a rigid body, the circle with the wave icon will appear. ![](<../.gitbook/assets/image (1456).png>)
* If the tag is paired and aligned, the green circle with green check icon will appear. ![](<../.gitbook/assets/image (1457).png>)

#### Illumination

The amount of time the LEDs are on for each frame. This setting applies only to Wired CinePuck and the Anchor Puck at this time.&#x20;

This value should be aligned with the exposure of the cameras for maximum brightness.&#x20;

#### Group

The active pattern grouping currently applied to the device.&#x20;

## Properties Pane for Tag and Rigid Body

### Active Tag Properties

Click any tag in the Devices Pane to display its properties in the Properties pane. In Live mode, these properties can be edited for Wired tags. For wireless devices, these values are read-only.&#x20;

For wireless devices, the RF Channel and Uplink ID can be changed using [ Active Batch Programmer](../active-classic/configuration/active-batch-programmer.md).&#x20;

<figure><img src="../.gitbook/assets/Properties - IMU Paired to RB.png" alt=""><figcaption><p>Active Tag properties pane.</p></figcaption></figure>

### Rigid Body Properties

Rigid Body properties that pertain to IMU specific workflows can be found under the Sensor Fusion section.&#x20;

<figure><img src="../.gitbook/assets/RB Properties - Sensor Fusion Advanced.png" alt=""><figcaption><p>Sensor Fusion section of the Rigid Body properties. </p></figcaption></figure>

#### IMU Label

Display a label with the status of the Rigid Body's IMU in the 3D Perspective View. If the asset Label is enabled, the IMU state is appended to the asset name.&#x20;

* **None** - No visual is displayed.&#x20;
* **Text** - Descriptive text provides detailed information about the IMU state.
* **Icon** - An icon-only visual is used.&#x20;

<div><figure><img src="../.gitbook/assets/IMU Label - text.png" alt=""><figcaption><p>Text visual in 3D Viewport.</p></figcaption></figure> <figure><img src="../.gitbook/assets/IMU Label - Icon (2).png" alt=""><figcaption><p>Icon visual in 3D Viewport.</p></figcaption></figure></div>

The text label includes the following information:&#x20;

* **Tag Name.**
* The status of **Sensor Fusion:**
  * **Rotate to Align (##/100)**: this status indicates that more rotations are required to align the IMU with the Rigid Body.
  * **Fused:** Sensor Fusion completed successfully.&#x20;

#### Min Alignment Count _(Advanced)_

The minimum number of measurements required for the IMU to auto-align. Higher values may lead to fewer alignment errors, but each new sample will have less of an effect on the estimate than the previous sample.

#### Max Drift Correction _(Advanced)_

Determines the rate at which the drift in the IMU data is corrected to optical. Higher values will lead to more responsive turning behavior, but more noise while stationary.

#### Drift Correction Frames _(Advanced)_

The number of frames over which drift correction can apply.&#x20;

#### Impulse Correction Angle _(Advanced)_

Determines the angle (in degrees) between the calculated drift correction and the current drift correction that will trigger correction. Impulse correction differs from standard drift correction, causing an immediate correction to optical. This is used primarily to prevent physical impacts to the IMU from causing degraded tracking.

## Constraints Pane

After pairing a Rigid Body to an IMU Puck, an IMU Constraint with IMU information is created for the Rigid Body. The pairing process will also update the Constraint names based on the Puck type identified by Motive. &#x20;

<figure><img src="../.gitbook/assets/Constraints pane - CinePuck.png" alt=""><figcaption><p>Constraints tab.</p></figcaption></figure>

### IMU Constraint

The IMU Constraint stores the alignment information from when the Align action is performed, using either Auto-Group Active Tag or by Manually Aligning.&#x20;

Removing this Constraint will remove the pair and/or align information from the Rigid Body. Pair and align the tag again to re-adhere the sensor fusion data to the Rigid Body.&#x20;

## Active Debugging in Info Pane

The [Active Debugging](../motive-ui-panes/info-pane.md#active-debugging) tool on the [Info pane](../motive-ui-panes/info-pane.md) is a troubleshooting aid for active devices. IMU status  information is displayed in gray text when it falls within the user-established parameters set at the bottom of the pane. Magenta text indicates that values exceed the parameters.&#x20;

<div><figure><img src="../.gitbook/assets/Info Pane - Active Debugging No Errors.png" alt=""><figcaption><p>Active Debugging Info pane: within parameters. </p></figcaption></figure> <figure><img src="../.gitbook/assets/Info Pane - Active Debugging with Errors.png" alt=""><figcaption><p>Active Debugging Info pane: outside parameters. </p></figcaption></figure></div>

#### IMU % Drops

This column denotes the number of IMU packet drops that an IMU Tag encountered over 60 frames.

#### Max Gap Size

Max Gap Size is the number of frames between IMU data packets sent where the IMU packets were dropped. For example, in the image above on the left, the maximum gap is a 1 frame gap where IMU packets were either not sent or received. The image on the right has a gap of 3 frames where the IMU packets were either not sent or received.&#x20;

#### Alignment

The difference between the IMU rotation and the optical rotation after alignment. If this value exceeds 1 degree, it may indicate that the IMU and optical have become misaligned and should undergo the alignment process again.&#x20;

## BaseStation Load Capacity

Wireless pucks and CinePucks attach to the camera system using a BaseStation. The number of IMUs that can attach to a BaseStation is determined by the system frame rate and the divisor applied to the BaseStation. The table below shows the IMU maximum for common frame rates with a divisor rate of 1, 2, and in some cases 3.

| Frame Rate | Divisor Rate 1 | Divisor Rate 2 | Divisor Rate 3 |
| :--------: | :------------: | :------------: | :------------: |
|     60     |       26       |       54       |       83       |
|     70     |       22       |       47       |       71       |
|     80     |       19       |       39       |       62       |
|     90     |       16       |       36       |       54       |
|     100    |       14       |       32       |       49       |
|     110    |       13       |       29       |       44       |
|     120    |       11       |       26       |       40       |
|     130    |       10       |       24       |                |
|     140    |        9       |       22       |       34       |
|     150    |        9       |       20       |                |
|     160    |        8       |       19       |       30       |
|     170    |        7       |       17       |                |
|     180    |        7       |       16       |       26       |
|     190    |        6       |       15       |                |
|     200    |        6       |       14       |       23       |
|     210    |        5       |       14       |                |
|     220    |        5       |       13       |       21       |
|     230    |        5       |       12       |                |
|     240    |        4       |       11       |       18       |
|     250    |        4       |       11       |                |

As noted, the table does not include all possible frame rate and divisor combinations. If you are familiar with using Tera Term or [PuTTy](../active-classic/configuration/active-hardware-configuration-putty.md), you can determine the maximum number of IMUs for any specific frame rate and divisor combination not shown on the table.

1. Use PuTTy to change the divisor rate on the BaseStation.
2. Connect an IMU puck to PuTTy.
3. Attempt to set the ID of the puck to an unrealistically high value. This triggers a warning that includes the current number of slots available for the given frame rate.
4. Set the IMU puck ID to the highest available slot for the frame rate and confirm that it appears in Motive.

{% hint style="info" %}
BaseStations have 16 radio frequency (RF) channels available for use (11-26). When adding more than one BaseStation to a system, the IMU count is simply the maximum number of IMUs multiplied by the number of BaseStations (up to 16). For example, in a system with 4 BaseStations running at 90Hz and a divisor rate of 3, the number of allowable IMUs would be 216 (54\*4=216).&#x20;
{% endhint %}

## CinePuck and other IMU Active Puck Indicator Lights

<figure><img src="../.gitbook/assets/image (1464).png" alt=""><figcaption><p>Wireless CinePuck, powered down.</p></figcaption></figure>

<table><thead><tr><th width="174">Color</th><th>Description</th><th>Troubleshooting</th></tr></thead><tbody><tr><td><p>Bottom Right: </p><p><mark style="color:orange;">Orange</mark></p></td><td>Powered ON and Booting</td><td>N/A</td></tr><tr><td>Top: <br>Flashing <mark style="color:red;">Red</mark>/<mark style="color:green;">Green</mark></td><td>Calculating bias. Please set on level surface. </td><td>N/A</td></tr><tr><td>Top:<br>Fast flashing <mark style="color:green;">Green</mark><br>Bottom Right: <br>Slow flashing <mark style="color:green;">Green</mark></td><td>Bias has been successfully calculated and Puck is connected to BaseStation</td><td>N/A</td></tr><tr><td>Top: <br>Solid <mark style="color:red;">Red</mark> then no light<br>Bottom Right: Slow flashing <mark style="color:green;">Green</mark></td><td>After powering on, the top light turns a solid red then turns off. This means that it is not paired to a BaseStation. The slow flashing Green indicates that it is still ON. </td><td> Please check your RF Channel on both devices to ensure they match. </td></tr><tr><td>Top: <mark style="color:green;">Solid Green</mark> then no light<br>Bottom Right: Slow flashing <mark style="color:green;">Green</mark></td><td>The puck is disconnected from the BaseStation WHILE powered ON. </td><td>Please check your BaseStation and ensure it is powered ON and receiving a signal from the network cable/switch.</td></tr><tr><td>Top: Fast Flashing <mark style="color:green;">Green</mark><br>Bottom Right: <mark style="color:orange;">Orange</mark></td><td>Battery power is below half.</td><td>Please connect device to power or let charge before continuing. </td></tr><tr><td>Bottom Right: Flashing <mark style="color:red;">Red</mark></td><td>Battery is nearly depleted.</td><td>Please connect device to power or let charge before continuing. </td></tr><tr><td>Bottom Left:<br><mark style="color:red;">Red</mark></td><td>Plugged in and charging. </td><td>N/A</td></tr></tbody></table>

