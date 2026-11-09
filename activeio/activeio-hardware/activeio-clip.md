---
description: >-
  A Quick Start Guide and specifications for three variations of the ActiveIO
  Clip.
---

# ActiveIO Clips

## Overview

ActiveIO Clips attach to Head Mounted Displays for tracking. Each of the Clips — the Focus 3, Focus Vision, and Varjo XR-4 — has a factory-installed [ActiveIO Tag8](activeio-tag8.md), which gives it 8 tracking LEDs. The Focus Clips are powered via the HMD, while the Varjo XR-4 has a cable that hooks to an independent power source.&#x20;

<figure><img src="../../.gitbook/assets/ActiveIO Clips Inclusive.jpg" alt="ActiveIO Clips for Focus 3, Focus Vision, and Varjo XR4 Head Mounted Displays"><figcaption><p>ActiveIO Clips for (clockwise from top left) Focus 3, Focus Vision, and Varjo XR-4 Head Mounted Displays</p></figcaption></figure>

## Quick Start Guide

#### Requirements

* Motive 3.5 or later.
* ActiveIO BaseStation. See the [ActiveIO BaseStation page](activeio-basestation.md) for instructions on setting up and using the device.&#x20;

The fronts of the individual Clips are shown in the tabs below.

{% tabs %}
{% tab title="Focus 3" %}
<figure><img src="../../.gitbook/assets/ActiveIO-Focus-3-HMD-no-shadow (1).png" alt="ActiveIO Clip for a Focus 3 Head Mounted Display"><figcaption><p>The Focus 3 ActiveIO Clip</p></figcaption></figure>
{% endtab %}

{% tab title="Focus Vision" %}
<figure><img src="../../.gitbook/assets/Focus Vision ActiveIO Clip Front.jpg" alt="ActiveIO Clip for a Focus Vision Head Mounted Display"><figcaption><p>Focus Vision ActiveIO Clip</p></figcaption></figure>
{% endtab %}

{% tab title="Varjo XR-4" %}
<figure><img src="../../.gitbook/assets/Varjo XR4 ActiveIO Clip Front Cord.jpg" alt="ActiveIO Clip for a Varjo XR4 Head Mounted Display"><figcaption><p>Varjo XR-4 Active IO Clip</p></figcaption></figure>
{% endtab %}
{% endtabs %}

### Connection, Power, and Setup

Each ActiveIO Clip needs no assembly by the user.

1. Connect the ActiveIO Clip to a Head Mounted Display (HMD). For the Focus 3 and Focus Vision Clips, a 4-Pin-Molex-to-USB-C adapter cable is included. This plugs directly into the headset. For the Varjo XR-4 Clip, a USB-A cable plugs into an independent power source.
2. Press the power button on the Tag8 inside the Clip to activate the Clip. The button is very small; you can activate is effectively by using a fingernail, pen, or pencil to push it. (See photos in the tabbed area below.)
3. Attach the ActiveIO Clip to the HMD.
4. Once powered, the Clip appears in Motive.

### Indicator LEDs and Power Button

Indicator LEDs and the power button are located on the Tag8 inside each ActiveIO Clip. The Tag8 in the Focus 3 Clip has no cover, while tags in the Focus Vision and Varjo XR-4 Clips are behind covers that have holes for the LEDs and power button. Functionality of indicator LEDs and power buttons are the same across all variations of ActiveIO Clips. Individual LEDs and power buttons are labeled in photos in the tabs below.&#x20;

{% tabs %}
{% tab title="Focus 3" %}
<figure><img src="../../.gitbook/assets/Focus 3 ActiveIO Clip Tag8 Labeled 4.jpg" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Focus Vision" %}
<figure><img src="../../.gitbook/assets/Focus Vision ActiveIO Clip Back Labeled.jpg" alt="Focus Vision ActiveIO HMD Clip Indicator LEDs labeled"><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Varjo XR-4" %}
<figure><img src="../../.gitbook/assets/Varjo XR-4 ActiveIO Clip Back Labeled.jpg" alt="Varjo XR-4 ActiveIO HMD Clip Indicator LEDs labeled"><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

#### Power Status LED (Lower Right)

* **Solid blue:** The device is on and connected to a battery; battery power is good.
* **Slow-blink red:** The battery is critically low (less than 10%).
* **Slow-blink green:** The battery is charging.
* **Solid green:** The battery is fully charged, or no battery is installed and the device is connected to an external power source.

{% hint style="info" %}
IR marker LEDs become disabled until the connected battery is recharged to more than 10%.
{% endhint %}

#### Sync Status LED (Upper Left)

* **One-second blink blue:** The device is synced. (Intermittent orange blinks appear when timing packets aren’t received; a lot of orange blinks indicates poor RF conditions.)
* **Slow-blink green:** The device is advertising (claimed).
* **Slow-blink violet:** The device is advertising (unclaimed).
* **Solid orange:** The device is on standby (wake-on-motion status).
* **Solid green:** The device is in Continuous mode.

#### IMU Status LED (Upper Right)

* **Fast-blink orange:** The Inertial Measurement Unit (IMU) needs calibration.
* **Solid orange:** The IMU is calibrated.
* **Fast-blink violet:** Fusing
* **Solid blue:** Fused

#### All LEDs at Once

* **Solid yellow:** The device has been selected in the Devices pane of Motive (this lets users identify the device when more than one device is active in the volume).
* **Cycle through all colors:** The device is updating firmware.

### Marker LEDs

Each ActiveIO Clip has 8 Marker LEDs fed by connections to the installed Tag8. The positions of those LEDs are shown in photos in the tabs below.&#x20;

{% tabs %}
{% tab title="Focus 3" %}
<figure><img src="../../.gitbook/assets/Focus 3 ActiveIO Clip Marker LED Locations.jpg" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Focus Vision" %}
<figure><img src="../../.gitbook/assets/Focus Vision ActiveIO Clip LEDs Labeled.jpg" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Varjo XR-4" %}
<figure><img src="../../.gitbook/assets/Varjo XR4 Active10 Clip Front LEDs Labeled 2.jpg" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### Modes

Each ActiveIO Clip has two synced modes (Patterned and Always On) and one non-synced mode (Continuous). To switch between Patterned and Always On modes, a property is available in Motive. To switch between a synced mode and the Continuous non-synced mode, double-click the power button, wait 1 second, then double-click it again.&#x20;

{% hint style="success" icon="power-off" %}
To switch between Synced and Continuous modes, double-click the power button on the device, wait 1 second, then double-click again.&#x20;
{% endhint %}

#### Patterned and Always On (Synced)

Patterned and Always On modes are synchronized with the camera system through an ActiveIO BaseStation. Synchronization allows the IR markers to be as bright and visible as possible when needed while reducing power consumption overall. The top left indicator LED on the Tag8 blinks blue when the ActiveIO Clip is synced.&#x20;

{% hint style="info" %}
The two synced modes, Patterened and Always On, do not work with the previous generation Active BaseStation.
{% endhint %}

The two synced modes differ as follows:

* **Patterned:** IR LEDs flash a unique identifying pattern.
*  **Always On:** All LEDs emit IR light synchronized to camera exposure.

#### Continuous (not Synced)

Continuous mode is not synchronized and does not require an ActiveIO BaseStation. In Continuous mode, the IR LEDs emit constant light with no blinking and are not synced with the camera exposure. The markers can appear dimmer to the cameras than they do in the synced modes, and power consumption is increased. In Continuous mode, the upper left indicator LED is solid green.

## Operation

The ActiveIO Clip does not need to be programmed with a unique label. Once connected to Motive, all labeling is automatic.

## Technical Drawings

Technical drawings for the three variations of the ActiveIO Clip are in the tabs below.

{% tabs %}
{% tab title="Focus 3" %}
<figure><img src="../../.gitbook/assets/ActiveIO Focus 3 Clip Tech Drawing.png" alt="A technical drawing of the ActiveIO Focus 3 Clip showing various angles and measurements of height, width and depth."><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Focus Vision" %}
<figure><img src="../../.gitbook/assets/Focus Vision ActiveIO Clip Tech Drawing.png" alt="ActiveIO HMD Clip for the Focus Vision"><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Varjo XR-4" %}
<figure><img src="../../.gitbook/assets/Varjo XR-4 ActiveIO Clip Tech Drawing.png" alt="ActiveIO HMD Clip for the Varjo XR-4"><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

## Specifications

{% tabs %}
{% tab title="Focus 3" %}
<table data-header-hidden><thead><tr><th width="170"></th><th></th></tr></thead><tbody><tr><td><strong>Dimensions</strong></td><td><p><strong>Width:</strong> 213 mm (8.37”)</p><p><strong>Height:</strong> 114 mm (4.5”)</p><p><strong>Depth:</strong> 96 mm (3.77”)</p></td></tr><tr><td><strong>Weight</strong></td><td>~100g (0.1Kg)</td></tr><tr><td><strong>Mounting</strong></td><td>Mechanical snap (clip) onto specific HMD (Head Mounted Display).</td></tr><tr><td><strong>Power</strong></td><td>Plugs directly into (and powered by) the HMD.</td></tr><tr><td><strong>LEDs</strong></td><td><p>8 LED markers (external)</p><p>3 LED indicators (internal)</p></td></tr><tr><td><strong>RF</strong></td><td><p>Frequency: 2.4 GHz</p><p>FCC: CISPR 32 CLASS A/2.4GHz Intentional Radiator</p><p>FCC ID: XPYNORAB2 PART 15 of FCC Rules</p></td></tr></tbody></table>
{% endtab %}

{% tab title="Focus Vision" %}
<table data-header-hidden><thead><tr><th width="170"></th><th></th></tr></thead><tbody><tr><td><strong>Dimensions</strong></td><td><p><strong>Width:</strong> 214 mm (8.41”)</p><p><strong>Height:</strong> 129 mm (5.07”)</p><p><strong>Depth:</strong> 97 mm (3.81”)</p></td></tr><tr><td><strong>Weight</strong></td><td>~100g (0.1Kg)</td></tr><tr><td><strong>Mounting</strong></td><td>Mechanical snap (clip) onto specific HMD (Head Mounted Display).</td></tr><tr><td><strong>Power</strong></td><td>Plugs directly into (and powered by) the HMD.</td></tr><tr><td><strong>LEDs</strong></td><td><p>8 LED markers (external)</p><p>3 LED indicators (internal)</p></td></tr><tr><td><strong>RF</strong></td><td><p>Frequency: 2.4 GHz</p><p>FCC: CISPR 32 CLASS A/2.4GHz Intentional Radiator</p><p>FCC ID: XPYNORAB2 PART 15 of FCC Rules</p></td></tr></tbody></table>
{% endtab %}

{% tab title="Varjo XR-4" %}


<table data-header-hidden><thead><tr><th width="170"></th><th></th></tr></thead><tbody><tr><td><strong>Dimensions</strong></td><td><p><strong>Width:</strong> 228 mm (8.99”)</p><p><strong>Height:</strong> 131 mm (5.15”)</p><p><strong>Depth:</strong> 82 mm (3.21”)<br><strong>USB-A Power Cable Length:</strong> 1,778 mm (70")</p></td></tr><tr><td><strong>Weight</strong></td><td>~100g (0.1Kg)</td></tr><tr><td><strong>Mounting</strong></td><td>Mechanical snap (clip) onto specific HMD (Head Mounted Display).</td></tr><tr><td><strong>Power</strong></td><td> USB-A cable plugs into the same independent source that powers the HMD.</td></tr><tr><td><strong>LEDs</strong></td><td><p>8 LED markers (external)</p><p>3 LED indicators (internal)</p></td></tr><tr><td><strong>RF</strong></td><td><p>Frequency: 2.4 GHz</p><p>FCC: CISPR 32 CLASS A/2.4GHz Intentional Radiator</p><p>FCC ID: XPYNORAB2 PART 15 of FCC Rules</p></td></tr></tbody></table>
{% endtab %}
{% endtabs %}
