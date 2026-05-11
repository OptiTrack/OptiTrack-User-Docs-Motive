# Log Pane

## Overview

The status Log pane displays important events or statuses of the camera system operation. Events that are actively occurring are shown under the _Current_ section, with all of the logged events saved in the _History_ section for the record.&#x20;

Open the status Log pane from the [View menu](toolbar-command-bar.md#view) or by clicking the <img src="../.gitbook/assets/image (1513).png" alt="" data-size="line"> icon on the main toolbar.

<img src="../.gitbook/assets/Log Pane - with Current Events.png" alt="Status messages indicating a disconnected camera." width="313">

In general, when there are no errors in the system operation, the _Current_ section of the log will remain free of warning, <img src="../.gitbook/assets/Log Pane - Warning icon 2 (1).png" alt="" data-size="line"> error, <img src="../.gitbook/assets/Log Pane - Error icon CROPPED.png" alt="" data-size="line"> or critical <img src="../.gitbook/assets/Log Pane - Critical icon CROPPED.png" alt="" data-size="line"> messages. Occasionally during system operations, the error/warning messages (e.g., Dropped Frame, Discontinuous Frame ID) may pop-up momentarily and disappear afterward. This could occur when Motive is changing its configuration, for example, when switching between Live and Edit modes or when re-configuring the synchronization settings. This is a common behavior and does not necessarily indicate system errors as long as the messages do not persist in the _Current_ section. If the error message persists under the _Current_ section or there is an excessive number of events, there may be an issue with the system operation.

## Export Log

To export the log history to a text file, click the <img src="../.gitbook/assets/Log Pane - Export log details.png" alt="Export Log Button" data-size="line"> button at the top left of the log pane. Open the file in Notepad or the text editor of your choice. The file can also be opened in Excel.&#x20;

<figure><img src="../.gitbook/assets/Log File Exported to Text file.png" alt="Sample of a log file exported to a text file."><figcaption><p>Sample log file export. </p></figcaption></figure>

## Clear Log

To reset the log history, click the <img src="../.gitbook/assets/Log Pane - Clear Events.png" alt="Clear Log Button" data-size="line"> button in the upper left corner of the log pane.&#x20;

## Status Messages

Status messages are categorized into five categories: Informational, Warning, Error, Critical, and Debugging. Logged status messages in the history list display in chronological order by default. The log history can be sorted by any field by clicking the column header. The sorted column is indicated with a cyan header.&#x20;

**Symbol Convention**

* <img src="../.gitbook/assets/image (1558).png" alt="" data-size="line"> : Informational
* <img src="../.gitbook/assets/Log Pane - Warning icon 2 (2).png" alt="" data-size="line"> : Warning
* <img src="../.gitbook/assets/Log Pane - Error icon CROPPED (1).png" alt="" data-size="line"> : Error
* <img src="../.gitbook/assets/Log Pane - Critical icon CROPPED (2).png" alt="" data-size="line">  : Critical
* <img src="../.gitbook/assets/Log Pane - Debug message.png" alt="" data-size="line"> : Debugging

![The status log panel, sorted by message type.](<../.gitbook/assets/Log Pane - History full view.png>)

### Informational Messages

Informational messages are noted with the <img src="../.gitbook/assets/Log Pane - Info icon CROPPED (11).png" alt="" data-size="line"> icon.&#x20;

***

#### Device already added

Peripheral Devices: Attempting to add a device with an already existing serial number.

_**Troubleshooting steps:**_ Check hardware configuration and make sure all is setup correctly.

***

#### Device factory count mismatch

Peripheral Devices: Device reported a different number of attached devices than were created.

_**Troubleshooting steps:**_&#x20;

* Check hardware configuration and make sure all is setup correctly.
* Contact support for the affected peripheral device (e.g., AMTI force plate).

***

#### Error resolving entry point

Peripheral Devices: Plugin does not contain the required creation functions.

_**Troubleshooting steps:**_ Try reinstalling peripheral DLLs and plugins.

***

#### Error: no active channels

Peripheral Devices: Unable to start plugin device because there are no active channels enabled on the device.

_**Troubleshooting steps:**_ Contact support for the affected peripheral device (e.g., AMTI force plate).

***

#### Error: no devices enabled

Peripheral Devices: Unable to start collecting from plugin devices. Devices are present but not enabled.

_**Troubleshooting steps:**_ Check hardware configuration and make sure all is setup correctly.

***

#### Error: no devices.

Peripheral Devices: Motive attempted to start device collecting but the previously available device(s) are no longer present.

_**Troubleshooting steps:**_ Check hardware configuration and make sure all is setup correctly.

***

#### Hotplug Remove Device Serial : { Serial# }

Peripheral Devices: A plugin device with the specified serial number was removed or is no longer responding.

_**Troubleshooting steps:**_ Check hardware configuration and make sure all is setup correctly.

***

#### Loaded Plugin : { File Name }

Peripheral Devices: Plugin DLL {File Name} has been loaded.

_**Troubleshooting steps:**_ Informational only. No troubleshooting required.&#x20;

***

#### No plugins loaded

Peripheral Devices: No plugin devices were loaded.

_**Troubleshooting steps:**_ Check hardware configuration and make sure all is setup correctly.

***

#### Plugin Device Created : { Device Name }

The plugin device object for an external device (e.g., force plate or NIDAQ) has been successfully created.

_**Troubleshooting steps:**_ Informational only. No troubleshooting required.&#x20;

***

#### Plugin Device Registered : { Device Name }

The plugin device has been registered in Motive.

_**Troubleshooting steps:**_ Informational only. No troubleshooting required.&#x20;

***

#### Remove Device { Device Name }

Peripheral Devices: The specific device was removed.

_**Troubleshooting steps:**_ Informational only. No troubleshooting required.&#x20;

***

#### The selected device has no enabled channels. Please enable at least one channel first.

Peripheral Devices: The peripheral device requires manual channel enabling before recording.

_**Troubleshooting steps:**_&#x20;

* Check Ni-DAQ channels and make sure they are enabled.&#x20;
* Make sure connections to the NI-DAQ are correct.

***

#### Unable to add device

Peripheral Devices: A Plugin device was detected, but Motive was unable to add it.

_**Troubleshooting steps:**_ Check hardware configuration and make sure all is setup correctly.

***

### Error Messages

Error messages are noted with the <img src="../.gitbook/assets/Log Pane - Error icon CROPPED (2).png" alt="" data-size="line"> icon.&#x20;

***

#### \[Load Plugins] Unable to find exported function

Peripheral Devices: The peripheral device manager was unable to find a required function in the device plugin dll.

_**Troubleshooting steps:**_

* Check that the plugin was installed correctly. &#x20;
* Test on another machine.

***

#### \[Load Plugins] Unable to load dll&#x20;

Peripheral Devices: The peripheral device manager was unable to find a required function in the device plugin dll.

_**Troubleshooting steps:**_ Make sure the device plugin peripheral DLL was installed during Motive installation.

***

#### \[Unload Plugin] Error occurred unloading plugin

Peripheral Devices: The peripheral device manager encountered an error when unloading a the device plugin dll.

_**Troubleshooting steps:**_ Contact Support for further troubleshooting.&#x20;

***

#### \[Unload Plugin] Error resolving unload entry point

Peripheral Devices: The peripheral device manager was unable to find the unload function from the plugin device dll.

_**Troubleshooting steps:**_ Contact Support for further troubleshooting.&#x20;

***

#### \[Unload Plugin] Unable to unload plugin

Peripheral Devices: The peripheral device manager was unable to unload the plugin device dll.

_**Troubleshooting steps:**_ Contact Support for further troubleshooting.&#x20;

***

#### { Device } Disconnected

Camera System: A mocap camera or other OptiTrack device (e.g., an eSync) was disconnected from the system.

_**Troubleshooting steps:**_

* Try replacing the cable or device if possible;
* Connect to another port on switch or PC;
* Try connecting the device (e.g., an eSync) directly to the aggregator switch and auxiliary power;&#x20;
* Make sure the correct power adapter is being used.

***

#### Dropped Frame

Camera System: A mocap camera dropped a frame of data, either because of incomplete packet delivery, buffer overflow, or it was not able to provide the frame in the time required to be part of the current frame group.

_**Troubleshooting steps:**_

* General networking troubleshooting;&#x20;
* Check if PC specs are sufficient for system;&#x20;
* Check if Windows background processes are causing any interruption;
* Monitor system performance using the Windows Task Manager; &#x20;
* Validate if the dropped frame was in 2D or 3D. Data can be reconstructed in Edit mode unless 2D data is missing.

***

#### ERROR: failed to stop { Device }

Peripheral Devices: The peripheral device manager encountered an error while attempting to stop a peripheral device.

_**Troubleshooting steps:**_ Check hardware configuration and make sure all is setup correctly.

***

#### Partial Frame Group Delivered

Camera System: the delivered frame group is missing a frame from one or more cameras.

_**Troubleshooting steps:**_

* General network troubleshooting;
* Identify if there is a faulty camera;
* Disable any managed features on the switch.

***

#### There was an attempt to synchronize a peripheral device to an eSync device that is not currently present

Peripheral Devices: Devices was set to hardware sync, but no eSync was present.

_**Troubleshooting steps:**_ Check hardware configuration and make sure all is setup correctly.

***

#### Unable to restart device after configuration update \[ Error : { Device Name } ]

Peripheral Devices : Device did not restart after configuration.

_**Troubleshooting steps:**_ Check hardware configuration and make sure all is setup correctly.

***

#### Unable to start { Device }

Peripheral Devices : Unable to start peripheral device collecting.

_**Troubleshooting steps:**_ Check hardware configuration and make sure all is setup correctly.

***

### Critical Messages

Critical messages are noted with either the <img src="../.gitbook/assets/Log Pane - Critical icon CROPPED (3).png" alt="" data-size="line"> or the <img src="../.gitbook/assets/Log Pane - Debug message (1).png" alt="" data-size="line"> icon.&#x20;

***

#### Out Of Band FrameID

Camera System: A specified camera's current frame ID is more than the default buffer size's (100 by default) frames difference from the group.

_**Troubleshooting steps:**_ General networking troubleshooting.

***

#### Synchronizer Queue Overflow

Camera System: The camera frame group synchronizer's queue is full and is unable to add a new frame group to the queue, so it is delivering a partial frame group instead.

_**Troubleshooting steps:**_ General networking troubleshooting.

***

#### Missing synchronization telemetry

Camera System: The eSync dropped a frame of telemetry data.

_**Troubleshooting steps:**_&#x20;

* Check that eSync settings are correct for the setup;
* Confirm that the eSync is plugged in correctly;
* Verify sync source signal is strong and the volume is up.

***

#### Out Of Order Frame Group

Camera System: The current camera frame group is older than the previous camera  frame group (out of order).

_**Troubleshooting steps:**_ Contact Support for further troubleshooting.&#x20;

***
