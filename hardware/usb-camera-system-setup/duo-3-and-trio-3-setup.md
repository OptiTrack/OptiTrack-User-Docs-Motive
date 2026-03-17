# Duo 3 and Trio 3 Setup



<figure><img src="../../.gitbook/assets/duo-3_765 (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The V120:Duo and V120:Trio are now the Duo 3 and Trio 3.&#x20;
{% endhint %}

## Operating Range

* 0 to 50 degrees Celsius
* 20% to 80% relative humidity (non-condensing)

## Software Installation

1. Download the Motive 3.3 software installer from the [Motive Download Page](https://optitrack.com/support/downloads/) to each host PC.
2. Run the installer and follow its prompts.&#x20;

{% hint style="success" %}
Each Duo 3 and Trio 3 includes a free license to _Motive:Tracker_ for one device. No software license activation or security key is required.&#x20;
{% endhint %}

{% hint style="info" %}
To use multiple Duo 3 or Trio 3 devices, connect each one to a separate host PC with Motive installed.&#x20;
{% endhint %}

## Connect the Hardware

Please see the [Host PC Requirements](../../motive/installation-and-activation.md#host-pc-requirements) section of the [Installation and Activation](../../motive/installation-and-activation.md) page for computer specifications.&#x20;

<figure><img src="../../.gitbook/assets/IO-X Breakout Box - No connections CROPPED.jpg" alt=""><figcaption><p>I/O-X Breakout Box</p></figcaption></figure>

### Components Provided in the Box

* Duo 3 or Trio 3 device
* I/O-X (breakout box)&#x20;
* Power adapter and cord
* Camera bar cable (attached to I/O-X)
* USB Uplink cable

<figure><img src="../../.gitbook/assets/V120 Duo and Trio connect IO-X breakout box.png" alt=""><figcaption><p>Connecting the Camera and the I/O-X breakout box.</p></figcaption></figure>

### Steps

1. Mount the camera bar in the designated location.
2. Connect the Camera Bar Cable to the back of the camera and to the I/O-X device, as shown in the diagram above.&#x20;
3. Connect the I/O-X device to the PC using the USB uplink cable.&#x20;
4. Connect the power cable to the I/O-X device and plug it into a power source.

{% hint style="danger" %}
Make sure the power is disconnected from the I/O-X (breakout box) before plugging or unplugging the Camera Bar Cable. Hot-plugging this cable may damage the device.
{% endhint %}

### Sync Out&#x20;

The Duo 3 and Trio 3 cameras use a preset frequency for timing and can run at 25 Hz, 50 Hz or 100 Hz. To synchronize other devices with the Duo or Trio, use a BNC cable to connect an input port on the receiving device to the Sync Out port on the I/O-X device.&#x20;

#### Output Options

Output options are set in the Properties pane. Select T-Bar Sync in the Devices pane to change output options:

* Exposure Time:  Sends a high signal based on when the camera exposes.
* Passthrough:  Sync In signal is passed through to the output port.&#x20;
* Recording Gate:  Low electrical signal (0V) when not recording and a high (3.3V) signal when recording is in progress.
* Gated Exposure Time:  ends a high signal based on when the camera exposes, only while recording is in progress.

### Sync In

Timing signals from other devices can be attached to the Duo 3 or Trio 3 using the I/O-X device's Sync In port and a BNC cable. However, this port does not allow you to change the rate of the device reliably. The only functionality that may work is passing the data through to the output port.

{% hint style="warning" %}
The Sync In port cannot be used to change the camera's frequency reliably.&#x20;
{% endhint %}

### &#x20;Run Motive

* The Duo 3 and Trio 3 ship with a free license for Motive:Tracker installed.
* The camera is pre-calibrated and no wanding is required. The user can [set the ground plane](../../motive/calibration/#ground-plane-and-origin).&#x20;
* The Duo 3 and Trio 3 run in Selective Grayscale, Grayscale, and MJPEG modes. Object mode is not available.

<figure><img src="../../.gitbook/assets/Asset Pane - V120 Duo.png" alt=""><figcaption><p>Devices Pane: T-Bar Sync.</p></figcaption></figure>

## Status LEDs

<figure><img src="../../.gitbook/assets/V120 Duo with Power and Lights CROPPED.jpg" alt=""><figcaption><p>Status LEDs for a Duo 3 camera.</p></figcaption></figure>

LED lights on the back of a Duo 3 or Trio 3 indicate the device's status.

### Left LED Lights

| Color | Definition                      |
| ----- | ------------------------------- |
| None  | Device is off.                  |
| Red   | Device is on.                   |
| Amber | Device is recognized by Motive. |

### Right LED Lights

| Color          | Definition                                                                                   |
| -------------- | -------------------------------------------------------------------------------------------- |
| None           | Tracking/video is not enabled.                                                               |
| Solid Red      | Configured for External-Sync: _Sync Not Detected_                                            |
| Flashing Red   | <p>Configured for Default, Free Run Mode,</p><p>or External-Sync: <em>Sync Detected</em></p> |
| Solid Green    | Configured for Internal-Sync: _Sync Missing_                                                 |
| Flashing Green | Configured for Internal-Sync: _Sync Present_                                                 |

