# Synchronization Setup

## **Overview**

The OptiTrack motion capture system can synchronize with other external devices for various applications. The synchronization device, the OptiHub2 and the eSync2, connects external devices through BNC cables, and sync signal patterns can be configured in Motive. Commonly integrated devices include video genlock, timecode generators, force plates, and actuators.

Motive offers flexible synchronization configurations to match various external signals with unique characteristics. The mocap system can be set as either a parent or a child in the sync chain to receive input signals, send output signals, or both. With such adaptability, the sync configurations may vary depending on which devices and signals are integrated. A basic understanding of signal processing is necessary in order to properly set up the sync chain.

## Synchronization Settings

![eSync2 properties listed under the Properties pane.](<../.gitbook/assets/image (1089).png>)

Synchronization settings can be configured by setting the properties of the synchronization hubs. For Ethernet camera systems, the connected eSync2 synchronization hub will get listed. For USB camera systems, the parent OptiHub2 will get listed for Flex cameras, and the sync I/O device will get listed for Duo/Trio tracking bars.

To configure the external synchronization, select the sync device in the [Devices pane](../motive-ui-panes/devices-pane.md) and open the [Properties pane](../motive-ui-panes/properties-pane/). All of the synchronization settings will be listed as properties of the selected sync device. By modifying these settings, you can control the sync input/output behavior as well as the triggering patterns. This allows you to customize the synchronization of the camera system and other peripheral devices. Commonly integrated peripheral devices include timecode generator, video genlock signal, force plates, data acquisition devices, recording trigger, and more.

### Configuring External Sync Settings

Depending on which type of system and what type of synchronization hub is used, the available customization options are slightly different. Please refer to the following pages for more details:

**External Device Synchronization Guide**

* [External Device Sync Guide: eSync 2](synchronization-hardware/external-device-sync-guide-esync-2.md)
* [External Device Sync Guide: OptiHub 2](synchronization-hardware/external-device-sync-guide-optihub2.md)

**Sync Device Properties**

* Prime series or Slim13E camera system: [Properties: eSync 2](../motive-ui-panes/properties-pane/properties-pane-esync2.md)
* Flex series camera system: [Properties: OptiHub 2](../motive-ui-panes/properties-pane/properties-pane-optihub2.md)
* Tracking bars (Duo 3 and Trio 3) have sync settings that are same as the OptiHub2. Please refer to the above OptiHub2 properties page for references its sync settings.
