# Properties Pane: Force Plates

When a force plate is selected in Motive, its device information gets listed under the [Properties pane](./). For configuring force plate properties, use the [Devices pane](../devices-pane.md) and modify the corresponding device properties.

For more information, read through the force plate setup pages:

* [AMTI Force Plate Setup](../../movement-sciences/movement-sciences-hardware/amti-force-plate-setup.md)
* [Bertec Force Plate Setup](../../movement-sciences/movement-sciences-hardware/bertec-force-plate-setup.md)
* [Kistler Force Plate Setup](../../movement-sciences/movement-sciences-hardware/kistler-force-plate-setup.md)

{% hint style="info" %}
**Advanced Settings**

The Properties: Force Plates contains _advanced settings_ that are hidden by default. Access these settings by going to the menu on the top-right corner of the pane and clicking _Show Advanced_ and all of the settings, including the advanced settings, will be listed under the pane.

The list of advanced settings can also be customized to show only the settings that are needed specifically for your capture application. To do so, go the pane menu and click _Edit Advanced_, and uncheck the settings that you wish to be listed in the pane by default. One all desired settings are unchecked, click _Done Editing_ to apply the customized configurations.
{% endhint %}

![](<../../.gitbook/assets/image (1007) (1) (1) (1) (1) (1) (1) (6).png>)

## Settings

![](<../../.gitbook/assets/image (1020).png>)

{% hint style="info" %}
**Force Plate Group Properties:**

Group policy is enforced for the force plates that are from the same vendors. This means most of the force plate properties are shared within the force plate groups. Shared settings include the enabled status, sampling rates, and sync modes. These settings should be configured the same for all force plates in most cases. If you need to disable a specific force plate among the group, this will need to be done by powering off the amplifier or disabling the device from the Windows Device Manager.
{% endhint %}

#### **Enabled**

Enables or disables selected force plate. Only enabled force plates will be shown in Motive and be used for data collection.

#### **Triggered Sync**

Select whether the force plate is synchronized through a recording trigger. This must be set to _Device_ when force plates are synchronized through recording trigger signal from the eSync. This must be set to _None_ when synchronizing through a clock signal.

#### **Reference Clock Sync**

When set to true, the force plate system synchronizes by reference to an external clock signal. This must be enabled for the reference clock sync. When two systems syncs using the recording trigger, this must be turned off.

#### **eSync Output**

Indicates the output port on the eSync that is used for synchronizing the selected force plate. This must match the output port on the eSync that is connected to the force plate amplifier and sending out the synchronization signal.

#### **Multiple**

Multiplier applied to the camera system frame rate. This is available only for triggered sync and can also be configured from the [Devices pane](../devices-pane.md). The resulting rate decides the sampling rate of the force plates.

#### **Rate**

Resulting data acquisition rate of the force plates. For reference clock sync setups, it will match the frequency of the clock signal. For triggered sync setups, this will match the multiple of the camera system frame rate.

#### **Order**

Assigned number of the force plates.

#### **Device Asset**

Name of the Motive asset associated with the selected device. For Manus Glove integration, this must match the name of the Skeleton.

## Details

#### **Name**

Name of the selected force plate.

#### **Model**

Model number of the force plate

#### **Serial**

Force plate serial number.

#### **Channels**

Number of active channels available in the selected device. For force plates, this defaults to 6 with channels responsible for measuring 3-dimensional force and moment data.

#### **State**

Indicates the state that the force plate is in. If the force plate is streaming the data, it will be indicated _Receiving Data_. If the force plate is on standby for data collection, it will be indicated _Ready_.

#### **Scale**

Size scale of the resultant force vector shown in the 3D viewport.

#### **Length**

Length of the force plate.

#### **Width**

Width of the force plate.

#### **ElectricalOriginOffset**

Manufacturer defined electrical-to-mechanical offset values.

#### **Corners**

Lists out positions of the four force plate corners. Positions are measured with respect to the global coordinate system, and this is calibrated when you _Set Position_ using the CS-400 calibration square.
