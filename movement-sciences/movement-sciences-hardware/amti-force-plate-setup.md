# AMTI Force Plate Setup

Example force plate properties for triggered sync.This page provides instructions on integrating an AMTI Force plate system with an OptiTrack motion capture system.

## **Overview**

When a motion capture system is used in conjunction with force plates, they work together as an efficient tool for various research applications including biomechanical analysis, clinical gait analysis, physiology research, sports performance research, and many more. An OptiTrack motion capture system can synchronize with force plates to obtain both kinematic and kinetic measurements. Note that force plate integration is supported only with a Prime camera system using the eSync 2 synchronization hub. This page provides quick guidelines for setting up and configuring force plates — with digital outputs — along with the OptiTrack motion capture system.

For detailed information on specifications and configurations on the force plates, refer to the documentation provided by the force plate manufacturer.

{% hint style="info" %}
**Analog Platforms**

Analog force plate devices can only be implemented via DAQ devices. Incoming voltage signals can be detected through the data acquisition channels, but force plate related software features (vectors, position calibration, etc.) will not be supported in Motive for the analog platforms. Refer to the [NI-DAQ Setup](ni-daq-setup.md) page for detailed instructions on integrating analog devices.
{% endhint %}

{% hint style="info" %}
**Motive 3.0 Update**

* Starting from Motive 3.0, reference clock synchronization while in Live mode is supported.
{% endhint %}

### **Required Components**

* Supported Amplifier Models: AMTI Gen 5, AMTI Optima.
* Force platforms that are compatible with the above amplifier models.
* Prime series Ethernet camera system with the eSync synchronization hub.
* Motive 1.9 or above.

## Hardware Setup

### Component Wiring (AMTI)

**AMTI Force Plate System Setup**

Connect each force plate into the host PC. For force plate systems with external amplifiers, the platform must be connected to the amplifier which uplinks to the host computer. For detailed instructions on setting up the Force Plate system with a host PC, refer to the AMTI documentation.

**Camera System Setup**

Setup the OptiTrack camera system and place the force plate(s) at the desired location(s); ideally, near the center of the volume. See [Quick Start Guide](../../quick-start-guides/quick-start-guide-getting-started.md) or [Hardware Setup](../../hardware/) page for details.

**Wiring the eSync with the Gen 5 Amplifier**

For accurate synchronizations, the [eSync 2 synchronization hub](http://optitrack.com/products/esync-2/) must be used. The eSync 2 has signal output ports that are used to send out synchronization signals to child devices. Connect the BNC _output_ ports of the eSync to sync input ports _(Genlock/Trigger Input)_ of force plate amplifiers.If force plate systems have RCA sync ports, use RCA cables along with the _50 Ohm BNC Male to 75 Ohm RCA Jack Adapters_ included with the eSync 2 to connect the amplifiers. The above wiring diagram shows how force plate systems need to be connected to an Ethernet camera system through the eSync 2.

**Multiple Devices Sync**

There are total four output ports on the eSync 2, and multiple force plates and external devices can be integrated if needed. Consult our [Engineers](http://optitrack.com/support/) for multiple force plate synchronizations.

**Hot Plugging**

{% hint style="danger" %}
Hot plugging is not supported with the integration. When a new device is connected to the system, you must re-start Motive to instantiate it.
{% endhint %}

![Diagram for Prime Camera System with integrated force plates. (\*) Some force plates don't have external amplifiers, but instead, have their amplifiers integrated within the platform. In this case, connect sync cables and the USB cables directly to the host PC. Click image to enlarge.](<../../.gitbook/assets/image (584).png>)

![The eSync 2 output and input ports.](<../../.gitbook/assets/image (1110) (1) (1) (1) (3).png>)

## Software Setup

### AMTI Software Setup

Before setting up the force plates in Motive, make sure software components required by the force plate system is installed on the computer. AMTI's software (e.g. AMTINetForce) must be able to detect and initialize the connected devices in order for the force plates to be properly initialized and used in Motive. Once this has been confirmed working, start setting up Motive. Please refer to manufacturer documentation for more information.

![Optima amplifier detected in the NetForce software.](<../../.gitbook/assets/image (1142).png>)

### Peripheral Device Module

In order to integrate force plate systems with Motive, you will need to setup the required drivers and plugins. Motive installer is packaged with the Peripheral Device module which can be added. During the Motive installation, a list of program features will be shown in the Custom Setup section. Here, change the setting for the _Peripheral Device_ module, as shown in the below image, so that the module is installed along with Motive Files.

{% hint style="info" %}
**Note** : Even if you are not using NI-DAQ, it is still necessary to install NI-DAQmx drivers that come up next in the installer.
{% endhint %}

![](<../../.gitbook/assets/image (525).png>) ![](../../.gitbook/assets/DAQmxInstall.gif)

### Force Plate Setup in Motive

**1. Start Motive**

If the hardware and software for the force plates are configured and successfully recognized, Motive will list out the detected force plates with number labels (1, 2, etc..). Motive will notify you of incorrect or nonexistent force plate calibration files. When the devices are successfully instantiated in Motive, the [Log pane](../../motive-ui-panes/log-pane.md) will indicate that the device has been created and loaded.

![Motive force plate representation in Perspective view.](<../../.gitbook/assets/image (1086).png>)

**2. Calibrate Cameras**

Calibrate the capture volume as normal to get the orientation of the cameras (see the [Quick Start Guide](../../quick-start-guides/quick-start-guide-getting-started.md) or [Calibration](../../motive/calibration/) page for more information). The position of the force plate is about the center of the volume, and when you recalibrate or reset the ground plane, you will need to also realign the position of your force plates for best results.

![Motive with force plates and camera calibration.](<../../.gitbook/assets/image (1136).png>)

**3. Setup CS-400**

On the [CS-400 calibration square](../../motive/calibration/calibration-squares.md), pull the force plate alignment tabs out and put the force plate leveling jigs at the bottom. The leveling jigs align the calibration square to the surface of your force plate. The alignment tabs allow you to put the CS-400 flush against the sides of your force plate giving the most accurate alignment.

![CS-400 calibration square with force plate force plate parts.](<../../.gitbook/assets/image (1072).png>)

**4. Place CS-400 on force plate**

Place the calibration wand on the force plate so that vertex of the wand is located at the right-hand corner of the side where the cable input is located (as shown in the image below). A correct placement of the calibration square is important because it determines the orientation of the force plate and its local coordinate axis within the global system. The coordinate systems for force plates are independent of the system used Motive.

{% hint style="info" %}
**AMTI Force Plates**

AMTI force plates use the right-hand system. The long arm of CS-400 will define the Y axis, and the short arm will define the X axis of the force plate. Accordingly, Z axis is directed downwards for measuring the vertical force.
{% endhint %}

![Force plate with CS-400 aligned properly.](<../../.gitbook/assets/image (1145).png>) ![Calibrated force plate position and orientation. X and Y axis is shown.](<../../.gitbook/assets/image (1131).png>)

**5. Set force plate position in Motive.**

After placing the calibration square on the force plate, select the CS-400 markers in Motive. Right click on the force plate you want to locate, and click **Set Position**. When there are multiple force plates in a volume, you may need to step on the force plate to find which platform the calibration square is on. In Motive, uncalibrated force plates will light up in green and a force vector will appear when you step on the plate. Repeat step 4 and 5 for other force plates as necessary.

Referencing to the markers on the calibration square, Motive defines the location of the force plate coordinate system within the global coordinate system.

Motive uses manufacturer defined X, Y, and Z mechanical-to-electrical center offset when calculating the force vector and the center of pressure. For digital based plates, this information is available from the SDK and also stored in the plate's on-board calibration data.

![Setting the position of a force plate in Motive. The number label on the force plate is inverted because the force plate position and orientation has not been calibrated yet.](<../../.gitbook/assets/image (1341).png>)

**6. Zero force plates.**

After you have calibrated each of your force plates, remove the CS-400 from the volume. Right click one of your force plates in Motive and click **Zero (all)**. This will tare the scale and set the current force on the plate data to 0. This will account for a small constant amount of measurement offset from the force plate. Remember that it zeros _all_ of the force plates at once. So make sure there are no objects on any of the force plates.

![Set the force plate data to zero for more accurate data.](<../../.gitbook/assets/image (1076).png>)

**7. Set sampling rate**

Sampling rate of force plates is configured through the synchronization setup which will be covered in the following section. You can sync the force plates either through the _reference clock sync_ or through the _triggered sync_. Please note that only specific sampling rates may be supported depending on the amplifier models.

{% hint style="info" %}
**Supported force plate sampling rates:**

For AMTI force plates support the following sampling rates depending on the amplifier used. For the most up-to-date information, consult their documentation. The supported sampling rates (Hz) are the following:

* **AMTI Gen 5 Amplifier:** 2000, 1800, 1500, 1200, 1000, 900, 800, 600, 500, 450, 400, 360, 300, etc...
* **AMTI Optima Amplifier:** 1000, 600, 500, 300, 250, 200, 150, 125, 120, 100, 60, 50, 30, 25, 15, 10.
{% endhint %}

![Configuring force plate sampling rate from Devices pane.](<../../.gitbook/assets/image (1084).png>)

## Synchronization Configuration

There are two synchronization approaches you could take: Synchronization through **clock signal** or through **recording trigger signal**.

Synchronization via clock signal utilizes the internal clock signal of the eSync to synchronize the sampling of the force plates on per-frame basis. However, when there is another device (e.g. NI-DAQ) being synchronized to the clock signal frequency, the sampling rate cannot be set for each individual device. In that case, triggered sync must be used for synchronizing the initial recording trigger. Synchronization via trigger signal utilizes the recording trigger in Motive to align the initial samples from both systems. After the initial sync, both systems run freely at their own sampling rate. If the force plates are running at whole multiples of the camera system, the collected samples will be aligned. However, since the sampling clocks are not perfectly accurate, alignment of the samples may slowly drift over time. Thus, when synchronizing via recording trigger, it is better to keep the record times short.

When synchronizing through the eSync, use the following steps to configure the sync settings in Motive. This will allow both systems to be triggered simultaneously with reference to the parent synchronization device, the eSync.

### Sync Configuration Steps: eSync 2

{% tabs %}
{% tab title="Reference Clock Sync" %}
**Reference Clock Sync Setup Steps**

1. Open the [Devices pane](../../motive-ui-panes/devices-pane.md) and the [Properties pane](../../motive-ui-panes/properties-pane/).
2. In the [Devices pane](../../motive-ui-panes/devices-pane.md), select the eSync among the listed devices. This will list out the synchronization settings in the properties pane for the selected eSync.
3. In the [Properties pane](../../motive-ui-panes/properties-pane/), under **Sync Input Settings** section, set the **Source** to **Internal Clock**.
4. Next, to the **Clock Frequency** section, input the sampling rate that you wish the run the force plates in. This clock signal will be eventually outputted to the force plate system to control the sampling rate. For this guide, let's set this to 1200 Hz.
5. Once the clock frequency is set, apply the **Input Divider/Multiplier** to the clock frequency to set the framerate of the camera system. For example, if you set the **Input Divider** to 10 and the _Input Multiplier_ to 2 with internal clock frequency running at 1200 Hz, the camera system will be running at 240 FPS. The resulting frame rate of the camera system will be displayed in the **Camera Rate** section.
6. Next step is to configure the output signal so that the clock signal can be sent to the force plate system. Under the _Outputs_ section, enable the corresponding output port of the eSync which the force plate system is connected to.
7. Set the _Output 1-4 → Type_ to [Internal Clock](../../synchronization/synchronization-hardware/external-device-sync-guide-esync-2.md#sync-input-select-the-sync-source).
8. Now that the eSync has been configured, you need to configure the force plate properties in Motive. While the force plate(s) is selected in Motive, access the Properties pane to view the [force plate properties](../../motive-ui-panes/properties-pane/properties-pane-force-plates.md). Here, set the following properties:
9. Record Trigger → _False_
10. Reference Clock Sync → _True_
11. eSync Output Channel → output port used on the eSync.

Once this is set, the force plate system will start sampling at the frequency of the clock signal configured on the eSync, and this rate will be displayed on the [Devices pane](../../motive-ui-panes/devices-pane.md) as well.

![Example eSync 2 properties for clock sync. Make sure the eSync 2 is selected in the Properties pane.](<../../.gitbook/assets/image (1087).png>) ![Example force plate properties for clock sync. Make sure the Force Plate is selected in the Properties pane.](<../../.gitbook/assets/image (1069).png>)

{% hint style="info" %}
**eSync 2 Settings Tip:**

In Motive 3.0 and above, you can quickly configure eSync into biomech sync settings by right-clicking on the eSync from the [Devices pane](../../motive-ui-panes/devices-pane.md) and select one of the presets from the context menu. This will enable and set all of the eSync outputs to the Internal Clock and set the clock frequency.
{% endhint %}

![Applying Biomech preset settings.](<../../.gitbook/assets/image (490).png>)

{% hint style="info" %}
**Live Data**

Starting from Motive 3.0, clock synchronization in Live mode is supported, and the force vector visualization will be available both in Live and Edit modes.
{% endhint %}
{% endtab %}

{% tab title="Triggered Sync" %}
**Triggered Sync Setup Steps**

1. Open the [Devices pane](../../motive-ui-panes/devices-pane.md) and the [Properties pane](../../motive-ui-panes/properties-pane/).
2. The final frame rate of the camera system will be displayed at the very top of the [Devices pane](../../motive-ui-panes/devices-pane.md).
3. In the [Devices pane](../../motive-ui-panes/devices-pane.md), select the eSync among the listed devices. This will list out the synchronization settings in the Properties pane for the selected eSync.
4. Set up the output signal so that the recording trigger signal can be sent to the force plate system. In the _Outputs_ section, enable and configure the corresponding output port of the eSync which the force plate system is connected to.
5. Set the _Output 1-4 → Type_ to [Recording Gate](../../synchronization/synchronization-hardware/external-device-sync-guide-esync-2.md#recording-gate-and-recording-start-stop-pulse).
6. Now that the eSync has been configured, you need to configure the properties of the force plates. While the force plate(s) is selected in Motive, access the Properties pane to view the [force plate properties](../../motive-ui-panes/properties-pane/properties-pane-force-plates.md). Here, set the following properties:
7. Record Trigger → _Device_
8. Reference Clock Sync → _False_
9. eSync Output Channel → output port used on the eSync.

Once this is done, the force plate system will synchronize to the recording trigger signal when Motive starts collecting data, and the force plates will free-run after the initial sync trigger. You can configure the sampling rate of the force plates by modifying the _Multiplier_ values in [Devices pane](../../motive-ui-panes/devices-pane.md) to sample at a whole multiple of the camera system frame rate.

![Example eSync 2 properties for triggered sync.](<../../.gitbook/assets/image (491).png>) ![Example force plate properties for triggered sync.](<../../.gitbook/assets/image (1114).png>)

{% hint style="info" %}
For free run sync setups, sampling rates of force plates can be set from the [Devices pane](../../motive-ui-panes/devices-pane.md), but the sampling rate of force plates must be configured to a whole multiple of the camera system's framerate. By adjusting the _Rate Multiplier_ values in the [Devices pane](../../motive-ui-panes/devices-pane.md), sampling rates of the force plates can be modified. First, pick a frame rate of the camera system and then adjust the rate multiplier values to set force plates to the desired sampling rate.
{% endhint %}

{% hint style="info" %}
**ReSynch**

When two systems are synchronized by recording trigger signals (Recording Gate or Recording Pulse), both systems are in _Free Run Mode_. This means that the recording of both the mocap system and the force plate system are triggered simultaneously at the same time and each system runs at its own rate.

Two systems, however, are synchronized at the recording trigger but not by per frame basis. For this reason, alignment of the mocap data and the force plate data may gradually drift from each other for longer captures. But this is not a problem since the sync chain will always be re-synchronized each time recording in Motive is triggered. Furthermore, _Takes_ in general do not last too long for this drift to take effect on the data.

However, this could be an issue when live-streaming the data since recording is never initiated and two systems will be synchronized only when Motive first launches. To zero out the drift, the **ReSynch** feature can be used. Right-click on force plates from either the [Devices pane](../../motive-ui-panes/devices-pane.md) or the [perspective view](../../motive-ui-panes/viewport.md#perspective-view), and select Resynch from the context menu to realign the sampling timing of both systems.
{% endhint %}

![Re-aligning initial sampling timing of the force plate.](<../../.gitbook/assets/image (1094).png>)
{% endtab %}
{% endtabs %}

### How to Validate your Synchronization

Before you start recording, you may want to validate that the camera and force plate data are in sync. There are some tests you can do to examine this.

The first method is to record dropping a retroreflective ball/marker onto the platform few times. The bouncing ball produces a sharp transition when it hits the surface of the platform, and it makes the data more obvious for validating the synchronization. Alternately, you can attach a marker on a tip of the foot and step on and off the force plate. _Make sure that your toe — closest to the marker — strikes the platform first, otherwise the data will seem off even when it is not._ You can then monitor the precise timing of the ball or the foot impacting the force plate and compare them between the mocap data and the force plate data.

The following is an example of validating good synchronization outcomes:

![Good synchronization](<../../.gitbook/assets/image (1061).png>)

## Device Settings Profile

All of the configured device settings, including the calibration, get saved on _Device Profile_ XML files. When you exit out of Motive, updated device profiles will be saved under the program data directory (`C:\ProgramData\OptiTrack\Motive\DeviceProfiles`), and this file gets loaded again when you restart Motive. You can have this file backed up to persist configured eSync and device settings. Also, if you wish to reset the device settings, you can remove XML files other than the default one from the folder, and Motive will load from the default settings.

## Force Plate Data in Motive

Force plate data can be monitored from the [Graph View pane](../../motive-ui-panes/graph-view-pane.md). You will need to either use a provided _Force Plate Forces_ layout or configure a custom graph layouts to show force plate data. To view the force plate data, make sure the corresponding force plates are selected, or selection-locked, in Motive.

If you are configuring your own force plate graph layout, make sure the desired force plate data channels (Fx, Fy, Fz, Mx, My, or Mz) are selected to be plotted. Then, when you select a force plate in Motive, and the data from the corresponding channels will be plotted on the graphs. When both reconstructed markers and force plate channels are selected, the force plot will be sub-sampled in order to be plotted along with trajectory data. For more information about how to configure graph layouts, read through the [Graph View pane](../../motive-ui-panes/graph-view-pane.md) page.

#### **Live Force Plate Data**

{% hint style="info" %}
**Notes**

* The force and moment data reflects the coordinate system defined by the force plate manufacturer, which is typically the Z-down right-handed coordinate system. Note: This convention is independent of the global coordinate system used in Motive. Thus, the Fz components represent the vertical force. For more in-depth information, refer to the force plate specifications.
{% endhint %}

![Default force plate layout selected from the dropdown menu located at top-right corner of the Graph pane.](<../../.gitbook/assets/image (1079).png>)

![Graph of live force plate data.](<../../.gitbook/assets/image (1328).png>) ![Graph view pane layout configuration.](<../../.gitbook/assets/image (1112).png>)

## Data Export

We recommend the following programs for analyzing exported data in biomechanics applications:

* [Visual3D](http://www.c-motion.com/products/visual3d/)
* [The MotionMonitor](http://www.innsport.com/)
* [MATLAB](http://www.mathworks.com/products/matlab/)

### C3D Export

Motive exports tracking data and force plate data into C3D files. Exported C3D files can then be imported into a biomechanics analysis and visualization software for further processing. See the [Data Export](amti-force-plate-setup.md#data-export) or [Data Export: C3D](../../motive/data-export/data-export-c3d.md) page for more information about C3D export in Motive. Note that the coordinate system used in Motive (y-up right-handed) may be different from the convention used in the biomechanics analysis software.

**C3D Axes**

**Common Conventions**

Since Motive uses a different coordinate system than the system used in common biomechanics applications, it is necessary to modify the coordinate axis to a compatible convention in the C3D exporter settings. For biomechanics applications using z-up right-handed convention (e.g. Visual3D), the following changes must be made under the custom axis.

* X axis in Motive should be configured to positive X
* Y axis in Motive should be configured to negative Z
* Z axis in Motive should be configured to positive Y.

This will convert the coordinate axis of the exported data so that the x-axis represents the anteroposterior axis (left/right), the y-axis represents the mediolateral axis (front/back), and the z-axis represents the longitudinal axis (up/down).

![The MotionMonitor biomechanics analysis software.](<../../.gitbook/assets/image (1067).png>) ![Visual3D biomechanics analysis software provided by C-Motion](<../../.gitbook/assets/image (537).png>)

![C3D export setting for applications using z-up right-handed coordinate systems.](<../../.gitbook/assets/image (1055) (1) (1) (1) (4).png>)

### CSV Export

Force plate data and the tracking data can be exported into CSV files as well. When a _Take_ file is exported into a CSV file. Separate CSV files will be saved for each force plate and it will contain the force, moment, and center of pressure data. Exported CSV file can be imported for analysis.

### Data Streaming

To stream tracking data along with the force plate data, open the Data Streaming Pane and check the _Broadcast Frame Data_, and make sure that you are not streaming over the camera network. Read more about streaming from the [Data Streaming](../../motive/data-streaming.md) workflow page.

Motive can stream the tracking data and the force plate data into various applications — including Matlab — using [NatNet Streaming](../../motive/data-streaming.md#natnet-streaming) protocol. Find more about [NatNet streaming](http://www.optitrack.com/products/natnet-sdk/) from the User's Guide included in the download.

{% hint style="danger" %}
**Number of Force Plates**

At the time of writing, there is a hard limit on the maximum number of force plate data that can be streamed out from Motive. Please note that only up to 8 force plate data can be streamed out from Motive and received by a [NatNet SDK 4.0](../../developer-tools/natnet-sdk/natnet-4.0.md) application.
{% endhint %}
