# Properties Pane: NI-DAQ

When an NI-DAQ device is selected in Motive, its device information gets listed under the [Properties pane](./). Just basic information on the used device will be shown in the [Properties pane](./). For configuring properties of the device, use the [Devices pane](../devices-pane.md).

For more information, read through the NI-DAQ setup page: [NI-DAQ Setup](../../movement-sciences/movement-sciences-hardware/ni-daq-setup.md).

{% hint style="info" %}
**Advanced Settings**

The Properties: NI-DAQ contains _advanced settings_ that are hidden by default. Access these settings by going to the menu on the top-right corner of the pane and clicking _Show Advanced_ and all of the settings, including the advanced settings, will be listed under the pane.

The list of advanced settings can also be customized to show only the settings that are needed specifically for your capture application. To do so, go the pane menu and click _Edit Advanced_, and uncheck the settings that you wish to be listed in the pane by default. One all desired settings are unchecked, click _Done Editing_ to apply the customized configurations.
{% endhint %}

![](<../../.gitbook/assets/image (1007) (1) (1) (1) (1) (1) (1) (8).png>)

## Settings

![Properties for the NI-DAQ device selected in Devices pane gets displayed in the Properties pane.](<../../.gitbook/assets/image (960).png>)

#### **Enabled**

Only enabled NI-DAQ devics will be actively measuring analog signals.

#### **Trigger Sync**

This setting determines how the recording of the selected NI-DAQ device will be triggered. This must be set to _None_ for reference clock sync and to _Device_ for recording trigger sync.

* None: NI-DAQ recording is triggered when Motive starts capturing data. This is used when using the reference clock signal for synchronization.
* Device: NI-DAQ recording is triggered when a recording trigger signal to indicate the record start frame is received through the connected input terminal.

#### **Trigger Terminal**

_(available only when Trigger Sync is set to Device)_ Name of the NI-DAQ analog I/O terminal where the recording trigger signal is inputted to.

#### **Reference Clock Sync**

This setting sets whether an external clock signal is used as the sync reference. _For precise synchronization using the internal clock signal sync, set this to true._

* **True:** Setting this to true will configure the selected NI-DAQ device to synchronize with an inputted external sample clock signal. The NI-DAQ must be connected to an external clock output of the eSync on one of its digital input terminals. The acquisition rate will be disabled since the rate is configured to be controlled by the external clock signal.
* **False:** NI-DAQ board will collect samples in 'Free Run' mode at the assigned _Acquisition Rate_.

#### **Reference Clock Terminal**

_(available only when Reference Clock Sync is set to True)_ Name of the NI-DAQ digital I/O terminal that the external clock (TTL) signal is inputted to.

#### **eSync Output**

Set this to the output port of the eSync where it sends out the internal clock signal to the NI-DAQ.

#### **Rate**

Shows the acquisition rate of the selected NI-DAQ device(s).

## Device Channel Properties

![NI-DAQ device channel properties displayed in the Devices pane.](<../../.gitbook/assets/image (998).png>)

Properties of individual channels can be configured directly from the [Devices pane](../devices-pane.md). As shown in the image, you can click on the [![ContextMenu dotdotdot.png](https://v30.wiki.optitrack.com/images/c/c4/ContextMenu_dotdotdot.png)](https://v30.wiki.optitrack.com/index.php?title=File:ContextMenu_dotdotdot.png) icon to bring up the settings and make changes.

Depending on the model, NI-DAQ devices may have different sets of allowable input types and voltage ranges for their analog channels. Refer to your NI-DAQ device User's Guide for detailed information about supported signal types and voltage ranges.

#### **Min Voltage**

(Default: -10 volts) Configure the terminal's minimum voltage range.

#### **Max Voltage**

(Default: +10 volts) Configure the terminal's maximum voltage range.

#### **Terminal Type**

Configures the measurement mode of the selected terminal. In general, analog input channels with screw terminals use the single-ended measurement system (RSE), and analog input channels with BNC terminals use the differential (Diff) measurement system. For more information on these terminal types, refer to [NI documentation](http://www.ni.com/white-paper/3394/en/#toc3).

* **Terminal: RSE** Referenced single ended. Measurement with respect to ground (e.g. AI\_GND) (Default)
* **Terminal: NRSE** NonReferenced single ended. Measurement with respect to single analog input (e.g. AISENSE)
* **Terminal: Diff** Differential. Measurement between two inputs (e.g. AI0+, AI0-)
* **Terminal: PseudoDiff** Differential. Measurement between two inputs and impeded common ground.

## Details

#### **Name**

_\[Advanced]_ Name of the selected device.

#### **Model**

Device model ID, if available.

#### **Serial**

Device serial number of the selected NI-DAQ assigned by the manufacturer.

#### **GroupName**

Type of device.

#### **Channels**

Total number of available channels on the selected NI-DAQ device.

#### **Run Mode**

\_\[Advanced]\_What mode of Motive playback being used.

#### **State**

Whether the device is ready or not.

#### **SyncState**

Tristate status of either Need Sync, Ready for Sync, or Synced. Updates the "State" icon in the Devices pane.

#### **DeviceType**

_\[Advanced]_ Internal device number.

#### **DisplayName**

User editable name of the device.
