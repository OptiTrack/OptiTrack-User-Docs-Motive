# Properties Pane: OptiHub2

{% hint style="danger" %}
**Important Note**

Please note that the OptiHub2 is not designed for _precise_ synchronization with external devices. It is used to provide only a _rough_ synchronization to a trigger event on the input/output signal. Using an OptiHub2, there will be some amount of time delay between the trigger events and the desired actions, and for this reason, the OptiHub2 is not suitable for the precisely synchronizing to an external device. To accomplish such synchronization, it is recommended to use the [eSync 2](../../synchronization/synchronization-hardware/external-device-sync-guide-esync-2.md) instead along with an Ethernet camera system.
{% endhint %}

By modifying the device properties of the OptiHub, users can customize the sync configurations of the camera system for implementing external devices in various sync chain setups. This page directly lists out the properties of the OptiHub. For general instructions on customizing sync settings for integrating external devices, it is recommended to read through the [External Device Sync Guide: OptiHub 2](../../synchronization/synchronization-hardware/external-device-sync-guide-optihub2.md) guide.

![](<../../.gitbook/assets/image (1036) (1) (1) (1) (1) (1) (3).png>)

While the OptiHub is selected under the [Devices pane](../devices-pane.md), use the [Properties pane](./) to view and configure its properties. By doing so, users can set the parent sync source for the camera system, configure how the system reacts to input signals, and also which signals to output from the OptiHub for triggering other external acquisition devices.

![](<../../.gitbook/assets/image (14) (2).png>)

![OptiHub 2 properties.](<../../.gitbook/assets/image (1003).png>)

## Synchronization Control

#### **Internal Sync Freq (Hz)**

This option is only valid if the Sync Input: Source is set to Internal Sync. Controls the frequency in Hertz (Hz) of the OptiHub 2's internal sync generator. Valid frequency range is 8 to 120 Hz.

#### **Global Sync Offset (us)**

This option is only valid if the Sync Input: Source is set to _Sync In or_ USB Sync\_. Controls synchronization delay in microseconds (us) between the chosen sync source signal and when the cameras are actually told to expose. This is a global system delay that is independent of, and in addition to, an individual camera's exposure delay setting. Valid range is 0 to 65862 us, and should not exceed one frame period of the external signal.\_

## Sync Input Settings

To setup the sync input signals, first define a input **Source** and configure desired trigger settings for the source:

* **Internal/Wired** sets the OptiHub 2 as the sync source. This is the default sync configuration which uses the _OptiSync_ protocol for synchronizing the cameras. The _Parent OptiHub 2_ will generate an internal sync signal which will be propagated to other (child) OptiHub 2(s) via the _Hub Sync Out Jack_ and _Hub Sync In Jack_. For V100:R1(legacy) and the Slim 3U cameras, _Wired Sync_ protocol is used. In this mode, the internal sync signal will still be generated but it will be routed directly to the cameras via daisy-chained sync cables.
* **Sync In** sets an external device as the sync source.
* **USB Sync** sets an external USB device as the sync source. This mode is for customers who use the [Camera SDK](/broken/pages/OqlhAtWITURVrnotYIgE) development kits and would like to have their software trigger the cameras instead. Using the provided API, the OptiHub 2 will be send the trigger signal from the PC via the OptiHib 2's USB uplink connection to the PC.

### Source: _Internal/Wired_

![Sync settings when the input sync source is set to Internal/Wired.](<../../.gitbook/assets/image (941).png>)

The Internal/Wired input source uses the OptiHub 2's internal synchronization generator as the main sync source. You can modify the synchronization frequency for both [Wired and OptiSync](../../synchronization/synchronization-hardware/external-device-sync-guide-optihub2.md) protocol under the Synchronization Control section. When you adjust the system frame rate from this panel, the modified frame rate may not be reflected on the Devices pane. Check the streaming section of the status bar for the exact information.

#### **Internal Sync Freq (Hz)**

This option is only valid if the _Sync Input: Source_ is set to Internal Sync. Controls the frequency in Hertz (Hz) of the OptiHub 2's internal sync generator, and the this frequency will control the camera system frame rate. Valid frequency range is 8 to 120 Hz.

### Source: _Sync In_

![Input sync settings when the source is set to Sync In.](<../../.gitbook/assets/image (983).png>)

The Sync In input source setting uses signals coming into the input ports of the OptiHub 2 to trigger the synchronization. Please refer to External [Device Sync Guide: OptiHub 2](../../synchronization/synchronization-hardware/external-device-sync-guide-optihub2.md) page for more instructions on this.

#### **Source Frequency**

Detects and displays the frequency of the sync signal that's coming through the input port of the _parent_ OptiHub 2, which is at the very top of the RCA sync chain. When sync source is set to _Sync In_, the camera system framerate will be synchronized to this input signal. Please note that OptiHub 2 is not designed for precise sync, so there may be slight sync discrepancies when synchronizing through OptiHub 2.

#### **Sync Offset**

Manually adds global sync time offset to how camera system reacts to the received input signal. The input unit is measured in microseconds.

#### **Input Trigger**

Can select from Either Edge, Rising Edge, Falling Edge, Low Gated, or High Gated signal from the connected input source.

#### **Input Divider**

Allows a triggering rate compatible with the camera frame rate to be derived from higher frequency input signals (e.g. 300Hz decimated down to 100Hz for use with a V100:R2 camera). Valid range is 1 (no decimation) to 15 (every 15th trigger signal generates a frame).

### Source: _USB Sync_

![Sync settings when the input sync source is set to USB sync.](<../../.gitbook/assets/image (947).png>)

(The camera system will be the child) sets an external USB device as the sync source. This mode is for customers who use the [Camera SDK](/broken/pages/OqlhAtWITURVrnotYIgE) development kits and would like to have their software trigger the cameras instead. Using the provided API, the OptiHub 2 will be send the trigger signal from the PC via the OptiHib 2's USB uplink connection to the PC.

#### **Source Frequency**

Detects and displays the frequency of the parent source.

#### **USB Sync-In Control**

Allows the user to allow or block trigger events generated by the internal sync control. This option has been deprecated for use in the GUI. Valid options are _Gate-Open_ and _Gate-Closed_.

#### **Input Divider**

Allows a triggering rate compatible with the camera frame rate to be derived from higher frequency input signals (e.g. 360Hz decimated down to 120Hz for use with a Flex 13 camera). Valid range is 1 (no decimation) to 15 (every 15th trigger signal generates a frame).\}}

### Input Trigger Options

| Trigger        | Description                                                                                                             |
| -------------- | ----------------------------------------------------------------------------------------------------------------------- |
| _Either Edge_  | Uses either the rising or falling edge of the pulse signal.                                                             |
| _Rising Edge_  | Uses the rising edge of the pulse signal.                                                                               |
| _Falling Edge_ | Uses the falling edge of the pulse signal.                                                                              |
| _High Gated_   | High Gated mode triggers when the input signal is at a high voltage level, but stops triggering at a low voltage level. |
| _Low Gated_    | Low Gated mode triggers when the input signal is at a low voltage level, but stops triggering at a high voltage level.  |

## External Sync Output

Sync signals can also be sent out through the output ports of the OptiHub 2 to child devices in the synchronization chain. Read more: [External Device Sync Guide: OptiHub 2](../../synchronization/synchronization-hardware/external-device-sync-guide-optihub2.md).

### Pulse Type

Selects condition and timing for a pulse to be sent out over the External Sync Out jack. Available Types are: Exposure Time, Pass-Through, Recording Level, and Recording Pulse.

#### External Sync Output Options

| Output                | Description                                                                                                                             |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| _Exposure Time_       | Outputs a pulse signal when the cameras expose.                                                                                         |
| _Pass-Through_        | Passes the input signal to the output.                                                                                                  |
| _Recording Gate_      | Outputs a constant high level signal while recording. Other times the signal is low. (Referred as _Recording Level_ in older versions). |
| _Gated Exposure Time_ | Outputs a pulse signal when the cameras expose during a recording only. (Referred as _Recording Pulse_ in older versions).              |

**Polarity**

Selects output polarity of External Sync Out signal. Valid options are: Normal and Inverted. Normal signals are low and pulse high and inverted signals are high and pulse low.
