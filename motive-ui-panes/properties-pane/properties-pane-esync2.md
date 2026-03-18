# Properties Pane: eSync2

By modifying the device properties of the eSync, users can customize the sync configurations of the camera system for implementing various sync chain setups.

While the eSync is selected under the [Devices pane](../devices-pane.md), use the [Properties pane](./) to monitor the eSync properties. Here, users can configure the parent sync source of the camera system and also the output sync signals from the eSync for integrating child devices (e.g. [NI-DAQ](../../movement-sciences/movement-sciences-hardware/ni-daq-setup.md)). For a specific explanation on steps for synchronizing external devices, read through the following page: [External Device Sync Guide: eSync 2](../../synchronization/synchronization-hardware/external-device-sync-guide-esync-2.md).

<figure><img src="../../.gitbook/assets/image (3) (4) (1).png" alt=""><figcaption></figcaption></figure>

![eSync2 Properties](<../../.gitbook/assets/image (1014).png>)

## Sync Input

Configure the input signal by first defining which input source to use. Available input sources include Internal Free Run, Internal Clock, SMPTE Timecode In, Video Gen Lock, Inputs (input ports), Isolated, VESA Stereo In, and Reserved. Respective input configurations appear on the pane when a source is selected. For each selected input source, the signal characteristics can be modified.

![](<../../.gitbook/assets/image (1006).png>)

Synchronization Input Source Options

| Input Source      | Description                                                                                                                                                                                                                                                                                          |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Internal Free Run | This is the default synchronization protocol for Ethernet camera systems without an eSync2. In this mode, Prime series cameras are synchronized by communicating the time information with each other through the camera network itself using a high-precision algorithm for timing synchronization. |
| Internal Clock    | Sets the eSync 2 to use its internal clock to deliver the sync signal to the Ethernet cameras, and the sync signal can be modified as well.                                                                                                                                                          |
| SMPTE Timecode In | Sets a timecode sync signal from an external device as the input source signal.                                                                                                                                                                                                                      |
| Video Gen Lock    | Locks the camera sync to an external video sync signal.                                                                                                                                                                                                                                              |
| Isolated          | Used for generic sync devices connected to the Isolated Sync In port from the eSync 2. Considered safer than other general input ports (Hi-Z and Lo-Z). The max signal voltage cannot exceed 12 Volts.                                                                                               |
| Inputs            | Uses signals through the input ports of the eSync 2. Used for high impedance output devices. The max signal voltage cannot exceed 5 Volts.                                                                                                                                                           |
| VESA Stereo In    | Sets cameras to sync to signal from the VESA Stereo input port.                                                                                                                                                                                                                                      |
| Reserved          | _Internal use only._                                                                                                                                                                                                                                                                                 |

### Sync Input Settings

#### **Clock Freq (Hz)**

Controls the frequency of the eSync 2's internal sync generator when using the internal clock.

#### **Sync Offset (us)**

Introduces an offset delay, in microsecond, to selected trigger signal.

#### **Input Trigger**

Sets the trigger mode. Available modes are _Either Edge_, _Rising Edge_, and _Falling Edge_, and each of them uses the corresponding characteristic of the input signal as a trigger.

#### **Input Divider**

Allows a triggering rate, compatible with the camera frame rate, to be derived from higher frequency input signals.

#### **Input Multiplier**

Allows a triggering rate, compatible with the camera frame rate, to be derived from lower frequency input signals. Available multiplier range: 1 to 15.

#### **Final Frame Rate**

Displays the final rate of the camera system.

{% hint style="info" %}
**eSync2 ports vs eSync ports**

In the eSync2, three general input ports are implemented in place of Lo-Z and Hi-Z input ports from the eSync. These general input ports are designed for high impedance devices, but low impedance devices can also be connected with appropriate adjustments. When the eSync 2 is connected to the system, options for Lo-Z and Hi-Z will be displayed.

* **Lo-Z input:** Sets an external low impedance device as the trigger. The max signal voltage cannot exceed 5 Volts.
* **Hi-Z input:** Sets an external high impedance device as the trigger. The max signal voltage cannot exceed 5 Volts.
{% endhint %}

## Outputs

Allows you to configure signal type and polarity of synchronization signal through the output ports, including the VESA stereo output port, on the eSync 2.

**Type:** Defines the output signal type of the eSync 2. Use this to sync external devices to the eSync 2.

**Polarity:** Change the polarity of the signal to normal or inverted. Normal signals constantly output a low signal and pulses high when triggering. Inverted signals constantly output a high signal and pulse low when triggering.

Output Signal Types

| Type                                                                                                                                                        | Description                                                                                    |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Exposure Time                                                                                                                                               | Outputs a pulse signal when the cameras expose.                                                |
| Recording Gate                                                                                                                                              | Outputs a constant high level signal while recording. Other times the signal is low.           |
| Record Start/Stop Pulse                                                                                                                                     | Outputs a pulse signal both when the system starts and stops recording.                        |
| Gated Exposure Time                                                                                                                                         | Outputs a pulse signal when the cameras expose, when the system is recording.                  |
| Gated Internal Clock                                                                                                                                        | Outputs the internal clock, while the system is recording.                                     |
| Selected Sync                                                                                                                                               | Outputs the Sync Input signal without factoring in signal modifications (e.g. input dividers). |
| Adjusted Sync                                                                                                                                               | Outputs the Sync Input signal accounting for adjustments made to the signal.                   |
| <ul><li>Internal Clock</li><li>SMPTE Timecode In</li><li>Video Genlock In</li><li>Isolated</li><li>Inputs</li><li>VESA Stereo In</li><li>Reserved</li></ul> | Uses a selected input signal to generate the synchronization output signal.                    |

## Record Triggering

**Trigger Source:** Determines which trigger source is used to initiate the recording in Motive. Available options are Software, Isolated, and Inputs. When the trigger source set to software, recording is initiated in Motive.

### Triggering with External Signals

With the eSync 2, external triggering devices (e.g. remote start/stop button) can integrate into the camera system and set to trigger the recording start and stop events in Motive. Such devices will connect to input ports of the eSync 2 and configured under the Record Triggering section of the eSync 2 properties.

By default, the remote trigger source is set to _Software_, which is the record start/stop button click events in Motive. Set the trigger source to the corresponding input port and select an appropriate trigger edge when an external trigger source (Trigger Source → isolated or input) is used. Available trigger options include _Rising Edge_, _Falling Edge_, _High Gated_, or _Low Gated_. The appropriate trigger option will depend on the signal morphology of the external trigger. After the trigger setting have been defined, **press the recording button in advance**. It sets Motive into a standby mode until the trigger signal is detected through the eSync. When the trigger signal is detected, Motive will start the actual recording. The recording will be stopped and return to the 'armed' state when the second trigger signal, or the falling edge of the gated signal, is detected.

_Note: For capturing multiple recordings via recording trigger, only the first_ TAK _will contain the 3D data. For the subsequent_ TAKs\_, the 3D data must be reconstructed through the\_ [_post-processing reconstruction_](../../motive/reconstruction-and-2d-mode.md#post-processing-reconstruction) _pipeline._

#### **Steps**

1. Open the [Devices pane](../devices-pane.md) and the [Properties pane](./) to access the eSync 2 properties.
2. Under the **Record Triggering** section, set the source to the respective input port where the trigger signal is inputted.
3. Choose an appropriate trigger option, depending on the morphology of the trigger signal.
4. Press the record button in Motive, which prepares Motive for recording. At this stage, Motive awaits for an incoming trigger signal.
5. When the first trigger is detected, Motive starts recording.
6. When the second trigger is detected, Motive stops recording and awaits for next trigger for repeated recordings. For High Gated and Low Gated trigger options, Motive will record during respective gated windows.
7. Once all the recording is finished, press the stop button to disarm Motive.

![](<../../.gitbook/assets/image (977).png>)

## Input Monitor

Input Monitor displays the corresponding signal input frequency. This feature is used to monitor the synchronization status of the signals into the eSync 2.

#### **Internal Clock**

Displays the frequency of the Internal Clock in the eSync 2.

#### **SMTPE Time Code In**

Displays the frequency of the timecode input.

#### **Video Genlock In**

Displays the frequency of the video genlock input.

#### **Inputs**

Displays the frequency of the input signals into the eSync 2.

#### **Lo-Z**

Displays the frequency of the external low impedance sync device.

#### **Hi-Z**

Displays the frequency of the external high impedance sync device.

#### **Isolated**

Display the frequency of the external generic sync device.

#### **Reserved**

For internal use only.

_Synchronization Input Source Options_

| Input Source      |                                                                                                                                                                                                                                                                                                           |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Internal Free Run | This is the default synchronization protocol for Ethernet camera systems without an eSync **2**. In this mode, Prime series cameras are synchronized by communicating the time information with each other through the camera network itself using a high-precision algorithm for timing synchronization. |
| Internal Clock    | Sets the eSync 2 to use its internal clock to deliver the sync signal to the Ethernet cameras, and the sync signal can be modified as well.                                                                                                                                                               |
| SMPTE Timecode In | Sets a timecode sync signal from an external device as the input source signal.                                                                                                                                                                                                                           |
| Video Gen Lock    | Locks the camera sync to an external video sync signal.                                                                                                                                                                                                                                                   |
| Isolated          | Used for generic sync devices connected to the Isolated Sync In port from the eSync 2. Considered safer than other general input ports (Hi-Z and Lo-Z). The max signal voltage cannot exceed 12 Volts.                                                                                                    |
| Inputs            | Uses signals through the input ports of the eSync2. Used for high impedance output devices. The max signal voltage cannot exceed 5 Volts.                                                                                                                                                                 |
| VESA Stereo In    | Sets cameras to sync to signal from the VESA Stereo input port.                                                                                                                                                                                                                                           |
| Reserved          | _Internal use only._                                                                                                                                                                                                                                                                                      |

### Sync Input Settings

#### **Clock Freq (Hz)**

Controls the frequency of the eSync 2's internal sync generator when using the internal clock.

#### **Sync Offset (us)**

Introduces an offset delay, in microsecond, to selected trigger signal.

#### **Input Trigger**

Sets the trigger mode. Available modes are _Either Edge_, _Rising Edge_, and _Falling Edge_, and each of them uses the corresponding characteristic of the input signal as a trigger.

#### **Input Divider**

Allows a triggering rate, compatible with the camera frame rate, to be derived from higher frequency input signals.

#### **Input Multiplier**

Allows a triggering rate, compatible with the camera frame rate, to be derived from lower frequency input signals. Available multiplier range: 1 to 15.

#### **Final Frame Rate**

Displays the final rate of the camera system.

{% hint style="info" %}
**eSync ports vs eSync2**

In the eSync 2, three general input ports are implemented in place of Lo-Z and Hi-Z input ports from the eSync. These general input ports are designed for high impedance devices, but low impedance devices can also be connected with appropriate adjustments. When the eSync is connected to the system, options for Lo-Z and Hi-Z will be displayed.

* **Lo-Z input:** Sets an external low impedance device as the trigger. The max signal voltage cannot exceed 5 Volts.
* **Hi-Z input:** Sets an external high impedance device as the trigger. The max signal voltage cannot exceed 5 Volts.
{% endhint %}

## Outputs

Allows you to configure signal type and polarity of synchronization signal through the output ports, including the VESA stereo output port, on the eSync2.

#### **Type**

Defines the output signal type of the eSync2. Use this to sync external devices to the eSync2.

**Polarity**

Change the polarity of the signal to normal or inverted. Normal signals constantly output a low signal and pulses high when triggering. Inverted signals constantly output a high signal and pulse low when triggering.

_Output Signal Types_

| Type                                                                                                                                                        | Description                                                                                    |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Exposure Time                                                                                                                                               | Outputs a pulse signal when the cameras expose.                                                |
| Recording Gate                                                                                                                                              | Outputs a constant high level signal while recording. Other times the signal is low.           |
| Record Start/Stop Pulse                                                                                                                                     | Outputs a pulse signal both when the system starts and stops recording.                        |
| Gated Exposure Time                                                                                                                                         | Outputs a pulse signal when the cameras expose, when the system is recording.                  |
| Gated Internal Clock                                                                                                                                        | Outputs the internal clock, while the system is recording.                                     |
| Selected Sync                                                                                                                                               | Outputs the Sync Input signal without factoring in signal modifications (e.g. input dividers). |
| Adjusted Sync                                                                                                                                               | Outputs the Sync Input signal accounting for adjustments made to the signal.                   |
| <ul><li>Internal Clock</li><li>SMPTE Timecode In</li><li>Video Genlock In</li><li>Isolated</li><li>Inputs</li><li>VESA Stereo In</li><li>Reserved</li></ul> | Uses a selected input signal to generate the synchronization output signal.                    |

## Record Triggering

**Trigger Source:** Determines which trigger source is used to initiate the recording in Motive. Available options are Software, Isolated, and Inputs. When the trigger source set to software, recording is initiated in Motive.

### Triggering with External Signals

[External Device Sync Guide: eSync 2](../../synchronization/synchronization-hardware/external-device-sync-guide-esync-2.md)

## Input Monitor

Input Monitor displays the corresponding signal input frequency. This feature is used to monitor the synchronization status of the signals into the eSync 2.

**Internal Clock:** Displays the frequency of the Internal Clock in the eSync 2.

**SMTPE Time Code In:** Displays the frequency of the timecode input.

**Video Genlock In:** Displays the frequency of the video genlock input.

**Inputs:** Displays the frequency of the input signals into the eSync 2.

**Lo-Z:** Displays the frequency of the external low impedance sync device.

**Hi-Z:** Displays the frequency of the external high impedance sync device.

**Isolated:** Display the frequency of the external generic sync device.

**Reserved:** For internal use only.
