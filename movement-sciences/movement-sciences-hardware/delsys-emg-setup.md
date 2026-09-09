---
description: A Quick Start Guide for the Delsys Trigno EMG integration with Motive.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/movement-sciences/movement-sciences-hardware/delsys-emg-setup
---

# Delsys Trigno EMG Setup

## Overview

Motive versions 3.4 and later support the digital integration of Delsys Trigno devices. Through this integration, Motive records electromyography (EMG) measurements from the Trigno EMG sensors along with the tracking data.&#x20;

This page provides instructions to set up the Delsys Trigno platform with the OptiTrack motion capture system.

### Required Components

The following hardware is required to use the Delsys Trigno EMG plugin with an OptiTrack Ethernet camera system:

* OptiTrack eSync 2 with BNC cable
* Delsys Trigno Centro
* Delsys Trigno Avanti, Mini, Duo or Quattro Sensors
* USB cable to connect the Delsys Trigno Base Station to Motive computer

The following software must be installed:

* Motive 3.4 or above, with a _Motive:Body_ or _Body Unlimited_ license
* Delsys Trigno Discover, with a license for 2.1 or above
* OptiTrack Delsys Plugin from the OptiTrack [downloads](https://www.optitrack.com/support/downloads) page.&#x20;

## Hardware Setup

The diagram below shows how the Delsys Trigno hardware connects to the Motive computer and the OptiTrack camera network.&#x20;

{% hint style="success" %}
Instructions on using the Delsys equipment are available in the [Delsys Trigno User Guide](https://delsys.com/downloads/USERSGUIDE/MAN-047-1-2-Trigno-Discover.pdf) or through [Delsys support](https://delsys.com/support/).&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/DelsysEMGDiagram_NoNI-DAQ (1).png" alt="A Diagram showing how the Delsys Trigno EMG Sensor connects to the Delsys Trigno BaseStation, and how the Delsys Trigno BaseStation connects to the Motive PC and the Camera network. "><figcaption></figcaption></figure>

1. Connect the eSync 2 to the camera network. Please see the [External Device Sync Guide: eSync 2](../../synchronization/synchronization-hardware/external-device-sync-guide-esync-2.md) page for instructions on this step.
2. Connect the Trigno BaseStation to the Motive PC with the USB cable.&#x20;
3. Connect the Trigno BaseStation to the eSync 2 with the BNC cable.
4. Open the _Trigno Discover_ application.
5. Activate the Trigo Base Station and EMG sensor and connect them to Trigno Discover.&#x20;

## Software Setup

Install the required software and plugin on the Motive PC.&#x20;

### Delsys Software Setup

Follow the instructions for installing and using the Delsys _Trigno Discover_ software found in the [Delsys Trigno User Guide](https://delsys.com/downloads/USERSGUIDE/MAN-047-1-2-Trigno-Discover.pdf) or through [Delsys support](https://delsys.com/support/).&#x20;

Open the _Centro Triggers_ tab and enable the _Start Input_ and _Stop Input_ options. Select the channel the BNC cable is connected to on the Trigno Base Station (see below).

<figure><img src="../../.gitbook/assets/Trigno Discover - Centro Trigger setup CROPPED.png" alt="The Centro Triggers panel, showing Channel 1 enabled for Start Input and Stop Input. " width="413"><figcaption></figcaption></figure>

Click the green Start button at the bottom of the Centro Triggers panel.

<figure><img src="../../.gitbook/assets/Trigno Discover - Start input CROPPED (1).png" alt="The Start button from the Trigo Discover application&#x27;s Centro Triggers panel. "><figcaption></figcaption></figure>

The EMG sensor will begin streaming real-time sensor data, as shown below.

<figure><img src="../../.gitbook/assets/Trigo Discover Data from EMG.png" alt="The data output from a successfully connected Delsys trigno, as shown in Trigno Discover."><figcaption></figcaption></figure>

Once streaming is confirmed, close the Trigno Discovery application.

### Motive Setup

Download and install Motive from the [OptiTrack downloads](https://www.optitrack.com/support/downloads?cat=motive) site. Please see the [Installation and License Activation](../../motive/installation-and-activation.md) page for more information about system specifications, licensing requirements, and installation instructions.&#x20;

{% hint style="success" %}
This plugin requires Motive version 3.4 or higher. Please [contact Sales](https://www.optitrack.com/contact) if you need assistance upgrading your Motive license.&#x20;
{% endhint %}

### Install Plugin

Download and install the Delsys Trigno plugin from the [OptiTrack downloads page](https://www.optitrack.com/support/downloads?cat=external-peripherals).&#x20;

### Device Setup in Motive

{% hint style="danger" %}
Before attempting to connect the device in Motive, make sure the device is configured and sending data in Trigno Discovery. Once confirmed, close the Trigno Discovery application.&#x20;

Do NOT launch Motive while Trigno Discovery is still running.&#x20;
{% endhint %}

The Delsys EMG will appear in the [Devices pane](../../motive-ui-panes/devices-pane.md) in the General Devices section.&#x20;

<figure><img src="../../.gitbook/assets/Delsys Trigno in Devices Pane CROPPED.png" alt="The Motive Devices pane, with the General Devices section highlighted in red to show where the Delsys Trigno device is located. "><figcaption></figcaption></figure>

Select the eSync 2 in the Device pane to display its properties in the Properties pane.&#x20;

In the eSync 2 Properties pane, set the following values for the output port that is connected to the Trigno base station. In this example, the Trigno Base Station is connected to Output Port 1 on the eSync 2.&#x20;

* Set the **Output port** to _Enabled_.
* Set the **Type** to _Record Start/Stop Pulse_.
* Set the **Polarity** to _Normal_.

<figure><img src="../../.gitbook/assets/Delsys Trigno Esync Properties CROPPED.png" alt="The Motive Devices pane and Properties pane, with the eSync 2 properties displayed. The settings for the output port 1 are shown. " width="341"><figcaption></figcaption></figure>

Once the eSync 2 properties are set, select the Delsys EMG in the Devices pane, then click the <img src="../../.gitbook/assets/Motive Context Menu (35).png" alt="Motive&#x27;s 3-dot context menu button. " data-size="line"> button that appears in the device's Info column.&#x20;

<figure><img src="../../.gitbook/assets/Delsys Trigno Configure Device step1 CROPPED.png" alt="The button to click to see more info on the Delsys Trigno device in Motive. "><figcaption></figcaption></figure>

This will open the DelsysEMG configuration window.&#x20;

The numbers at the top correspond to the individual data channels provided by the specific sensors in use. Sensors may have IMUs or multiple EMG sensors. Each sensor typically provides data in the following order: EMG, accelerometer, and gyro data.&#x20;

* Click the number for the data channel you wish to record.
* Toggle the Enabled setting to _on_.&#x20;

<figure><img src="../../.gitbook/assets/Delsys Trigno Select Channel CROPPED.png" alt="The DelsysEMG Control panel in Motive. "><figcaption></figcaption></figure>

#### Graph View

The Graph View allows you to see the data streaming from the Trigno EMG device:&#x20;

1. Click the <img src="../../.gitbook/assets/Graph Pane 1 Button (1).png" alt="Button from the Motive toolbar to open the Graph View pane." data-size="line"> button to open the [Graph View pane](../../motive-ui-panes/graph-view-pane.md).&#x20;
2. Select the DelsysEMG device from the Devices pane.&#x20;
3. Click the <img src="../../.gitbook/assets/Graph Pane - Edit Graph (3).png" alt="Button from the Graph View pane to open the Graph Editor." data-size="line"> button to open the [Graph Editor](../../motive-ui-panes/graph-view-pane.md#graph-editor).
4. On the [Data tab](../../motive-ui-panes/graph-view-pane.md#data-tab), enable the EMG in the Device section.
5. sensor data that you wish to view in each graph pane.&#x20;
6. After selecting the data, right-click in the Graph pane and select _Lock Selection_. This will ensure that the data remains visible in the graph even if other devices or assets are selected in Motive.&#x20;

<figure><img src="../../.gitbook/assets/Delsys Trigno Graph pane in Motive CROPPED.png" alt="The Graph View pane with the Graph Editor panel open, the EMG Sensor selected as a Device, and the X coordinates selected for the first panel."><figcaption><p>Selecting the EMG Sensor in the Graph Editor Data panel. </p></figcaption></figure>

Once you have set all the channels you wish to track in the Graph pane, you're ready to record.
