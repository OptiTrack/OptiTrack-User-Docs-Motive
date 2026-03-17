# Troubleshooting Q\&A

### Hardware: Cabling and Wiring

<details>

<summary>Q: Can USB and Ethernet Cameras be used in a same system?</summary>

A:No.

</details>

### Ethernet System

<details>

<summary>Q: Cameras are not detected in Motive</summary>

A: There are a number of reasons why this could be happening.

* Firewall blocking the camera system.
* Camera system not connected to its designated network card.

</details>

### External Device Sync

<details>

<summary>Q: Peripheral Device - Motive crashes at its launch</summary>

A: Motive may freeze at launch if an incompatible version of the NI-DAQmx driver is installed. If Motive is crashing at launch and you have the NI-DAQmx driver already installed, try uninstalling the driver, restart the computer, and reinstall the driver by reinitiating the Motive installation process. When you select the peripheral device to be installed, it will lead to the compatible version of NI-DAQmx driver setup.

</details>

## Software: Data Streaming

<details>

<summary>Q: Data is not streamed</summary>

* Check the data streaming settings in Motive
  * Is **Streaming Enabled in the Settings?**
  * Is the Network Interface address set properly?
  * Are the desired data types enabled for streaming?
* Check the data streaming settings in the client software.
  * Is the client application connected to the server at a network interface designated by the server?
* Check if the desired data type is enabled for streaming.

</details>

### NI-DAQ

<details>

<summary><strong>Q: Connected NI-DAQ device is not detected in Motive</strong></summary>

A\*\*:\*\*

1\) Confirm the NI-DAQ device is detected by the MS Windows system (Devices Manager) and by the NI Device Monitor (task tray) that installs with your NI-DAQ software.

2\) If the device is still not detected in Motive even after confirming the connection from the above step, completely uninstall the National Instruments Software drivers and re-install Motive. Make sure to choose 'Yes' to install packaged OptiTrack Peripheral Module and the NI-DAQmx runtime. After installing the drivers, it is essential to restart your computer.

3\) After launching Motive, check the **Status Log** panel (View tab → Status Log) and confirm the following:

a. The Peripheral Device module, or the OptiTrack Peripherals Module (OPM), is loaded by checking the Motive Status Log panel during startup.b. The NI-DAQ device is detected and created.

* The _Loaded Plugin_ message indicates the plugin was successfully loaded.
* The _Plugin Device Registered_ message indicates the devices is registered in Motive.
* The _Plugin Device Created_ message indicates the device is detected and initialized.

4\) If the Status Log shows that it failed to load the plugin, make sure the BiomechDevicePlugin.dll is located within the devices folder in Motive's install directory.

<img src="../.gitbook/assets/image (968).png" alt="Status log message when the NI-DAQ device is successfully loaded." data-size="original">

</details>

<details>

<summary><strong>Q: I have the NI-DAQmx driver installed for my DAQ device, but they are not the recommended version.</strong></summary>

A: This is fine as long as the NI-DAQmx driver version is 15.1.1 or later. If you are experiencing connection difficulties, try uninstalling your current driver and re-installing the driver that ships with Motive.

</details>

<details>

<summary><strong>Q: When installing the device NI-DAQmx driver, I get to a screen that indicates  no changes will be made</strong> and I can't proceed.</summary>

A: This indicates the driver for your device is already installed. Hit cancel to exit the installer, and ensure the driver version is at least 15.1.1 or later. If not, update your driver. You can also re-install the driver that ships with Motive, but make sure the previous install is completely removed before the re-installation.

</details>

<details>

<summary><strong>Q: I can't change the multiplier for my DAQ from the Devices pane in Motive.</strong></summary>

A: If the device is configured to use external clock signals, the option to change the acquisition rate for NI-DAQ devices within Motive will be disabled. Set UseExternalClock to False to use the Free Run mode.

</details>

<details>

<summary><strong>Q: Motive warns that the sampling rate is too high for my device.</strong></summary>

A: This warning indicates that the sampling may be out of the allowable range for the DAQ device. Some devices share the allowable sample rate across all channels, and each channel takes up a portion of the total allowable sample rate of the device. Other devices have dedicated sample rates for each channel, and the allowable sample rate can be set for each channel in this case. For detailed specification on how your device samples incoming signals, refer to the respective NI-DAQ User's Guide.

</details>

<details>

<summary><strong>Q: The analog input value does not appear to be correct.</strong></summary>

A: Ensure that the appropriate channel type is selected. If your signal increases or decreases, with a steady baseline, your ground is not set correctly. See the section on [channel types](../movement-sciences/movement-sciences-hardware/ni-daq-setup.md#device-channel-properties) for more information.

</details>

<details>

<summary><strong>Q: In the Device pane, I can't enable my device when checking the box next to it.</strong></summary>

A: A device can't be enabled until one of it's channels is made active. Activate at least one channel under the device to enable the device itself. Only the channels that are active, and have the associated device enabled, will be recorded.

</details>

<details>

<summary><strong>Q: No really, my analog input is incorrect.</strong></summary>

&#x41;**:** Input channels can be verified using NI's Device Monitor and opening up a configuration session. Within the device monitor, the channel input can be observed. If the observed output is different from what appears in Motive, there may be an issue. This may also be due to aliasing of the sampled signal. Ensure that the signal is captured at the appropriate sampling frequency. A low sampling frequency may inaccurately capture high-frequency signals.

</details>

<details>

<summary><strong>Q: Voltages from one channel seem to affect another channel.</strong></summary>

A: Crosstalk or ghosting is a normal occurrence in a digital acquisition device, and can be caused by a variety of sources. For detailed information on crosstalk, and steps you can take to minimize it, please refer to your NI-DAQ documentation. National Instrument also provides some steps on reducing unwanted voltages here: [http://digital.ni.com/public.nsf/allkb/B9BCDFD960C06B9186256A37007490CD?OpenDocument](http://digital.ni.com/public.nsf/allkb/B9BCDFD960C06B9186256A37007490CD?OpenDocument)

</details>
