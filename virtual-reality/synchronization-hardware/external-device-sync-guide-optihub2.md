# External Device Sync Guide: OptiHub2

## **Overview**

This page provides general instructions on how to use the OptiHub2 for integrating external devices with Flex series mocap systems. The OptiHub2 not only provides power for the USB cameras, but it also includes external sync in/out ports for integration of external devices. With proper configurations, you can have another device (parent) control the mocap system or have the mocap system control another external device (child), or both. Setup instructions for both child and parent devices will be covered. Note that the sync setup may vary depending on the type of integrated devices as well as the morphology of the communicated sync signals. Use this guide for understanding the general idea of how external devices are implemented, and apply it to your own needs.

### **External Device Synchronization**

On the OptiHub2, there are one _External SYNC In_ and one _External SYNC Out_ ports for connecting external devices. In general, parent devices connect to the input port for controlling the mocap system, and child devices connect to the output port to be triggered by the mocap system. Once the devices are connected, the input and output source needs to be configured under the [OptiHub2 properties](../../motive-ui-panes/properties-pane/properties-pane-optihub2.md) in Motive.

{% hint style="danger" %}
**Important Note**

Please note that the OptiHub2 is not designed for _precise_ synchronization with external devices. It is used to provide only a _rough_ synchronization to a trigger event on the input/output signal. Using an OptiHub2, there will be some amount of time delay between the trigger events and the desired actions, and for this reason, the OptiHub2 is not suitable for the precisely synchronizing to an external device. To accomplish such synchronization, it is recommended to use the [eSync 2](../../synchronization/synchronization-hardware/external-device-sync-guide-esync-2.md) instead along with an Ethernet camera system.
{% endhint %}

{% hint style="info" %}
**Difference Between OptiSync and Wired Sync**

**OptiSync**

* The OptiSync is a custom camera-to-camera synchronization protocol designed for Flex series cameras. The OptiSync protocol sends and receives sync signals over the USB cable, without the need for RCA sync cables. This sync method is only available when using Flex 3 or Flex 13 cameras connected to the OptiHub2.

**Wired Sync**

* The Wired Sync is a camera-to-camera synchronization protocol using RCA cables in a daisy chain arrangement. With a master RCA sync cable connecting the master camera to the OptiHub2, each camera in the system is connected in series via RCA sync cables and splitters. The V100:R1 (Legacy) and the Slim 3U cameras utilize Wired Sync only, and therefore any OptiTrack system containing these cameras need to be synchronized through the Wired Sync. Wired Sync is optionally available for Flex 3 cameras.
{% endhint %}

![OptiSync](<../../.gitbook/assets/image (1081).png>) ![Wired Sync](<../../.gitbook/assets/image (1336).png>)

**Additional Notes:**

* Unlike the eSync2, the OptiHub2 cannot generate an output signal at a higher frequency than the camera capture rate.
* When using multiple OptiHub2s, input and output ports of only the parent OptiHub2 can be used. The parent OptiHub2 is the first OptiHub2 within the daisy-chained RCA sync chain.

![The OptiHub2.](<../../.gitbook/assets/image (1097).png>)

![OptiHub setup.](<../../.gitbook/assets/image (601).png>)

{% hint style="info" %}
**Duo/Trio Tracking Bars:**

* Use the Sync In/Out ports on the I/O-X USB hub to use the external signal to drive the tracking bar.
{% endhint %}

## Synchronization Setup

### Setting Up a Parent Device

**Step 1. \[Hardware]** Connect a parent device into the _External SYNC In_ port of the _parent_ OptiHub2.

**Step 2. \[Motive]** Launch Motive.

**Step 3. \[Motive]** Open the [Devices pane](../../motive-ui-panes/devices-pane.md) and the [Properties pane](../../motive-ui-panes/properties-pane/) under the view tab.

**Step 4. \[Motive]** Select the parent OptiHub2 in the [Devices pane](../../motive-ui-panes/devices-pane.md), then its properties will get listed under the [Properties pane](../../motive-ui-panes/properties-pane/).

**Step 5. \[Motive]** Under the _Sync Input Settings_ section, configure the source and the corresponding settings. If you are using an external device connected to the _External SYNC In_ port as the sync source, set the input source to _Sync In_. See more under the [Input Source](external-device-sync-guide-optihub2.md#input-source) section of this page.

**Step 6. \[Motive]** Once above is configured, the camera system will capture according to the input signal, and you should be able to see the change in the [Devices pane](../../motive-ui-panes/devices-pane.md) camera frame rate section.

### Setting Up a Child Device

**Step 1. \[Hardware]** Connect a child device into the _External SYNC Out_ port of the _parent_ OptiHub2.

**Step 2. \[Motive]** Launch Motive.

**Step 3. \[Motive]** Open the [Devices pane](../../motive-ui-panes/devices-pane.md) and the [Properties pane](../../motive-ui-panes/properties-pane/) from the view tab.

**Step 4. \[Motive]** Select the parent OptiHub2 in the [Devices pane](../../motive-ui-panes/devices-pane.md), then its properties will get listed under the [Properties pane](../../motive-ui-panes/properties-pane/). By modifying the properties, you can configure the for outputting sync signals to the child devices.

**Step 5. \[Motive]** Under the output section, set the output signal type. This will determine the signal characteristic that the child device will receive. See the [Output Source](external-device-sync-guide-optihub2.md#output-source) section of this page for details.

**Step 6. \[Motive]** Once this is set, the OptiHub2 will output configured signal through its output ports.

## Input Source

The Sync Input configuration determines how the camera system is synchronized. Depending on which input source is configured under the custom sync settings, the cameras will shutter at the corresponding frequency. To configure the sync input signals, first define an input **Source** and then configure the respective trigger settings. The following input sources can be configured with the OptiHub2:

### Internal Sync

**(The camera system will be the parent)**

When the sync source is set to _Internal/Wired_ the camera system uses the OptiHub2 as the sync source. This is the default configuration, and it uses OptiHub2's sync protocol for synchronizing the cameras. The _Parent OptiHub2_ will generate an internal sync signal which will be propagated to other (child) OptiHub2(s) via the _Hub Sync Out Jack_ and _Hub Sync In Jack_, and all of the cameras connected to the OptiHub2s will be synchronized. For V100:R1(legacy) and the Slim 3U cameras, _Wired Sync_ protocol is used. In this mode, the internal sync signal will still be generated but it will be routed directly to the cameras via daisy-chained sync cables.

When the _Internal Sync_ is selected as the sync source, _Internal Sync Freq (Hz)_ can be set under the _Synchronization Control_ section. This setting determines how the OptiHub2 triggers the camera exposures or the camera framerate.

### Sync In

**(The camera system will be the child)**

When synchronizing the camera system to an external device, set the source to _Sync In_, and the camera system references the external signal through the _SYNC In_ port as the parent sync. In this mode, the _Input Trigger_ event must be defined so that the camera systems respond to the incoming signal as desired; available triggers are Either Edge, Rising Edge, Falling Edge, High Gated, and Low Gated. Note that the suitable event will vary depending on characteristics of the received signal and how you want the system to synchronize with it.

For syncing to input signals with a frequency higher than the supported camera frame rates, the _Input Divider_ can be applied so that the sync source is down-sampled to the supported rate range.

{% hint style="info" %}
**Duo/Trio Tracking Bars:**

* In Duo/Trio Tracking bars, when there is external signal detected through its I/O-X box, the tracking bar will no longer be able to operate in free-run mode. In this case, the source must be set to _Sync In_ to utilize the external signal OR the external input must be disconnected from the I/O-X box for free-run.
{% endhint %}

### USB Sync

**(The camera system will be the child)**

This mode is for customers who use the [software development kits](../../developer-tools/developer-tools-overview.md) and would like to have their software trigger the cameras instead. Using the provided API, the OptiHub2 will can receive the trigger signal from the PC via the OptiHub2's USB uplink connection.

### Trigger and Camera Exposure

Note that the precise moment of the camera exposure does not exactly coincide with the sync input trigger event. There is a fixed latency between these two events due to specific implementation of the sensors used in the cameras. This delay from the onset of the trigger-event to the start of exposure on the cameras can be calculated as the following:

#### **Flex 3 and Duo/Trio tracking bars**

* Camera exposure (measured in microseconds).
* Imager Scan-Rate: Frame Rate Setting defined under the [Devices pane](../../motive-ui-panes/devices-pane.md).

![](<../../.gitbook/assets/OptiHub2 Trigger to Exposure Delay.png>)

#### **Flex 13**

Flex 13 cameras have a different trigger-to-exposure latency. From the moment the sync trigger event is received, it takes _480 microseconds_ for the cameras to synchronize and start exposing. After this delay, the Flex 13 cameras expose for the duration defined under the exposure settings in the [Devices pane](../../motive-ui-panes/devices-pane.md). The camera exposures are measured in microseconds for Flex 13 cameras.

![Trigger to exposure delay in Flex 13 cameras.](<../../.gitbook/assets/image (1116).png>)

## Output Source

The _External SYNC Out_ port of the OptiHub2 can be used if you want to set up the camera system to be a parent of other systems. The output port sends out the sync signals which can be configured under the _External Sync Output_ section of the [OptiHub2 properties](../../motive-ui-panes/properties-pane/properties-pane-optihub2.md). First, understand the characteristic of sync signal that the connected child device is expecting and configure the output source accordingly.

* All output signals can be inverted by setting the _Output::Polarity_ to Inverted.
* For connecting more than one child devices, output signals may be split using a BNC splitter.
* The sync hubs are capable of sending out the following signals:

![Using the BNC splitter for connecting additional child devices.](<../../.gitbook/assets/image (1141).png>)

### Exposure Time & Gated Exposure Time

Exposure output signals to inform when the cameras are exposing. When the output type is set to _Exposure Time_, the sync hub asserts the output signals when the cameras are exposing, or shuttering, in the live mode. When the output is configured to Recording Pulse, the exposure signal is asserted only when Motive is recording.

![Exposure Time output signal.](<../../.gitbook/assets/image (1095).png>)

### Recording Gate

The Recording Gate signal can be used to tell the child device when Motive is recording or not. When configured to Recording Gate, the sync hub will output a constant high voltage signal when Motive is recording. Please note that OptiHub2 is not specifically designed for precise synchronization, and there will be a slight delay when it starts outputting the trigger signal. This delay varies on each camera system setup.

![Recording Gate output signal.](<../../.gitbook/assets/image (1064).png>)

{% hint style="info" %}
**Gated Output Signal (OptiHub2) Note:**

The gated (while-recording) output signal from the OptiHub2 is not frame-synchronous with the recorded frame data. When the recording trigger is received in the middle of a frame, mocap frames starting from the next one get recorded in the _Take_. The gate output signal, however, does not respect this and begins outputting the signal as soon as the recording trigger is received. For this reason, there could be a slight offset between the outputted gated signal and the recorded mocap data.
{% endhint %}

### Pass-Through

The _Pass-through_ type outputs the signal that is received through the SYNC In port.
