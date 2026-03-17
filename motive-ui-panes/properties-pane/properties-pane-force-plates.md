# Properties Pane: Force Plates

## Overview

This page covers the properties specific to Force Plates. For general information on using and customizing the Properties pane, see the [Properties Pane](./) page. For detailed descriptions of properties for various asset types or other devices, please see the following pages:

* [Properties: Take](properties-pane-take.md)
* [Properties: Trained Markerset](properties-pane-trained-markerset.md)
* [Properties: Skeleton](properties-pane-skeleton.md)
* [Properties: Rigid Body](properties-pane-rigid-body.md)
* [Properties: eSync](properties-pane-esync2.md)
* [Properties: Camera](properties-pane-camera.md)
* [Properties: NI-DAQ](properties-pane-ni-daq.md)

## Force Plate Setup

Follow the manufacturer's instructions to setup the force plate and install the software required to operate it on the Motive PC. This software must be installed before the force plate can be used in Motive.&#x20;

For detailed information, please see the following force plate setup pages:

* [General Motive Force Plate Setup](../../movement-sciences/movement-sciences-hardware/general-motive-force-plate-setup.md)
* [AMTI Force Plate Setup](../../movement-sciences/movement-sciences-hardware/amti-force-plate-setup.md)
* [Bertec Force Plate Setup](../../movement-sciences/movement-sciences-hardware/bertec-force-plate-setup.md)
* [Kistler Force Plate Setup](../../movement-sciences/movement-sciences-hardware/kistler-force-plate-setup.md)

{% hint style="info" %}
#### Connecting Multiple Force Plates

When connecting more than one force plate, use devices from the same manufacturer for the plates to work together properly. Collectively, the connected force plates are known as the Force Plate Group.&#x20;
{% endhint %}

## Force Plate Properties

Select a force plate in the [Devices pane](../devices-pane.md) or in the [3D viewport](../viewport.md#perspective-view), and the corresponding properties will be listed under the [Properties pane](./). These properties can be modified only in Live mode.&#x20;

{% hint style="info" %}
**Advanced Settings**

The Properties pane contains advanced settings that are hidden by default. To access these settings, click the <img src="../../.gitbook/assets/Motive Context Menu (24).png" alt="" data-size="line"> button in the top right corner.&#x20;

Use the _Edit Advanced_ option to customize which settings are in the _Advanced Settings_ category and which appear in the standard view, to show only the settings that are needed specifically for your capture application.&#x20;
{% endhint %}

![Show or Edit Advanced Settings.](<../../.gitbook/assets/Properties Pane - Show Advanced (5).png>)

### **Force Plate Group Policy**

Group policy requires certain properties to be identical on all devices in the force plate group. Shared settings include:

* Enabled status
* Sampling rates &#x20;
* Sync modes&#x20;

These settings must have the same values for all force plates in the group.&#x20;

{% hint style="info" %}
If you need to disable a specific force plate in the group, power off its amplifier or disable the device through Windows Device Manager.
{% endhint %}

### Settings

The following items are available in the Settings section. All of these are standard properties.&#x20;

![Properties Pane: Force Plate Settings.](<../../.gitbook/assets/Force Plates - Adv Prop Settings only CROPPED.png>)

#### **Enabled**

Enables the selected force plate. Only enabled force plates are shown in Motive and used for data collection.

#### **Triggered Sync**

Select whether the force plate is synchronized through a recording trigger. This must be set to _Device_ when force plates are synchronized through recording trigger signal from the eSync2. This must be set to _None_ when synchronizing through a clock signal.

#### **Reference Clock Sync**

Enables the force plate system to synchronize to an external clock signal, the eSync2. When this setting is enabled, the _eSync Output_ setting becomes available.&#x20;

#### **eSync Output**

Select the output port that the force plate amplifier is connected to on the eSync2. This setting is only visible when Reference Clock Sync is enabled. &#x20;

<figure><img src="../../.gitbook/assets/Force Plate Settings esync Output CROPPED.png" alt=""><figcaption><p>Select the eSync2 Output source.</p></figcaption></figure>

#### **Multiple**

This sets the multiplier applied to the camera system frame rate. This setting is only available when using triggered sync and can also be configured from the [Devices pane](../devices-pane.md). The resulting rate determines the sampling rate of the force plates.

#### **Rate**

The resulting data acquisition rate of the force plates, based on the camera frame rate set in the Devices pane and the multiplier property set above, when using triggered sync. For reference clock sync configurations, this will match the frequency of the clock signal. For triggered sync setups, this will be the product of the Multiple value (above) and the camera system frame rate.

#### **Order**

The assigned number of the force plate.

#### User Data

A text field available to input user-specified information.&#x20;

### Details

The following items are available in the Details section. Properties are Standard unless noted otherwise.&#x20;

_**\*Values for properties noted with an asterisk (\*) are derived from the force plate manufacturer's software.**_

<figure><img src="../../.gitbook/assets/Force Plates - Adv Prop Details only CROPPED (1).png" alt=""><figcaption><p>Properties Pane: Force Plate Details section.</p></figcaption></figure>

#### **Name (Advanced)\***

The name of the selected force plate.&#x20;

#### **Model\***

The model number of the force plate.

#### **Serial\***

The force plate serial number.

#### Group Name\*

The force plate group name, typically the name of  the manufacturer.

#### **Channels (Advanced)**

The number of active channels available in the selected device. For force plates, this defaults to 6, with channels responsible for measuring 3-dimensional force and moment data.

#### Run Mode  / Sync Mode (Advanced)

The Mode property varies depending on whether Motive is in Live or Edit mode. When Live, the property will display _Run Mode Live_. When in edit mode, the property _Sync Mode_ displays either a 1 if the device was set to use a trigger sync, and a 0 if it was not synced or it was set to a reference clock.&#x20;

#### **State**

Indicates the state that the force plate is in. If the force plate is streaming data, the state is _Receiving Data_. If the force plate is on standby for data collection, the state is _Ready_.

#### **SyncStatus**

Current status of the force plate synchronization: need sync, ready for sync, or sync.&#x20;

#### DeviceType (Advanced)

A numeric value (2) assigned by Motive to identify the device as a force plate.&#x20;

#### **DisplayName**&#x20;

A free-form text field that will be used to label the force plate in the graph view.

#### **Scale (Advanced)**

Size scale of the resultant force vector shown in the 3D viewport.

#### **AmpModel (Advanced)**

The amplifier model used by the force plate.&#x20;

#### AmpSerial (Advanced)

The serial number of the amplifier used by the force plate.&#x20;

#### Model Type\*

Model type of the force plate.&#x20;

#### **Length**

Length of the force plate.

#### **Width**

Width of the force plate.

#### X/Y/Z Offset

Distance offset from the geometrical center, as defined by the calibration square placement, to the electrical center of the force plate. The offset values are in meters relative to the force plate's coordinate system.

### Calibration

The following items are available in the Settings section.&#x20;

<figure><img src="../../.gitbook/assets/Properties - FP calibration SCRUBBED.png" alt=""><figcaption><p>Force Plate Calibration properties.</p></figcaption></figure>

#### X/Y/Z Coordinates

Adjust the pivot point along the x/y/z axis.

#### Calibration Square Rotation (Advanced)

Determines the location of the force plate relative to the calibration square. Use _None_ (the default) if placing the calibration square on top of the force plate in the lower right corner. Select _-90 degrees_ if the square is placed next to the force plate, against the lower right corner.&#x20;

### Advanced

The items available in the Advanced section are for use by OptiTrack Support. This section is available only when the Advanced Settings are displayed.

#### **Corners**

Displays the positions of the four force plate corners. Positions are measured with respect to the global coordinate system, which is calibrated when you _Set Position_ using the CS-400 calibration square.

<figure><img src="../../.gitbook/assets/Properties - FP Corners.png" alt=""><figcaption><p>Force Plate Properties: Corners.</p></figcaption></figure>
