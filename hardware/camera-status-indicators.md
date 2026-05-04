---
description: An overview of the status indicator lights on the OptiTrack Ethernet cameras.
---

# Camera Status Indicators

## Overview

PrimeX and SlimX series cameras have status lights on the front and back of the cameras.&#x20;

### PrimeX Status Ring Light Color

The PrimeX Series cameras have a front mounted status ring light to indicate the state of the Motive software and firmware updates on the cameras. The following table lists the default ring light color associated with the state of Motive.

<details>

<summary>Off</summary>

Status: Powered & Awaiting Connection

Can Modify Color: No

When a camera is first plugged in, the LED ring light on a PrimeX camera and the status light on a SlimX camera will be off until it receives commands from Motive and has successfully authenticated via the security key. If it is not successful in connecting to the network, but receiving power, it will remain off with a small flashing white dot light in the bottom left corner.

<div><figure><img src="../.gitbook/assets/image (11) (1) (3) (1).png" alt="A PrimeX camera with the ring light off."><figcaption><p>A PrimeX camera <br>powered and<br>awaiting connection</p></figcaption></figure> <figure><img src="../.gitbook/assets/SlimX Cyan Connected,Powered, Motive.jpg" alt="A SlimX Camera that is connected to Motive."><figcaption><p>A SlimX camera<br>powered and<br>awaiting connection</p></figcaption></figure></div>

</details>

<details>

<summary>Slow Flashing Cyan, no IR</summary>

Status: Idle

Can Modify Color: No

The camera is powered and connected to the network, but Motive is not running. Two dashes in the bottom left corner will display in lieu of ID number.

<div><figure><img src="../.gitbook/assets/image (168).png" alt="A PrimeX camera with the ringlight displaying a flashing cyan color, with no ringlight. "><figcaption><p>A PrimeX camera <br>with a flashing <br>cyan ring light,<br>and no camera number.</p></figcaption></figure> <figure><img src="../.gitbook/assets/SlimX Connected,Powered, NoMotive.jpg" alt="A SlimX camera with a flashing cyan light, and no camera number."><figcaption><p>A SlimX camera <br>with a flashing <br>cyan light, and <br>no camera number.</p></figcaption></figure></div>

</details>

<details>

<summary>Cyan</summary>

Status: Live

Can Change Color: Yes

The camera is actively sending data and receiving commands when loaded into Motive.

<div><figure><img src="../.gitbook/assets/image (142).png" alt="A PrimeX camera with the ringlight displaying a cyan color. "><figcaption><p>PrimeX Camera<br>with a Cyan<br>Ring light</p></figcaption></figure> <figure><img src="../.gitbook/assets/SlimX Cyan Live mode.jpg" alt="SlimX camera with a Cyan indicator light."><figcaption><p>SlimX Camera <br>with a Cyan <br>indicator light.</p></figcaption></figure></div>

</details>

<details>

<summary>White / Off</summary>

Status: Masking or Playback mode

Can Change Color: No

When a marker, or what a camera perceives as a marker, is visible to a camera when masking in the Calibration pane, the PrimeX ring light and the SlimX status light will turn white, and the SlimX light will blink. When masks are applied and no erroneous marker data is seen, the LEDs turn off and the volume is ready to wand.

On a SlimX Camera, a steady white light indicates the camera is in playback mode.&#x20;

<div><figure><img src="../.gitbook/assets/image (760).png" alt="A PrimeX camera with the ringlight displaying a white color. "><figcaption><p>PrimeX Camera<br>with a White<br>Ring Light. </p></figcaption></figure> <figure><img src="../.gitbook/assets/SlimX White.jpg" alt="SimX Camera with a White Status Light. "><figcaption><p>SimX Camera<br>with a White<br>Status Light. </p></figcaption></figure></div>

</details>

<details>

<summary>Solid Green</summary>

Status: Recording

Can Change Color: Yes

The Camera is sending data to be written to memory or disk.

<div><figure><img src="../.gitbook/assets/image (110).png" alt="A PrimeX camera with the ringlight displaying a solid green color. "><figcaption><p>PrimeX Camera<br>with a green<br>Ring Light</p></figcaption></figure> <figure><img src="../.gitbook/assets/SlimX Green Recording Calibrating.jpg" alt="A SlimX camera with the green status light on. "><figcaption><p>SlimX Camera<br>with a green<br>status light</p></figcaption></figure></div>

</details>

<details>

<summary>Variable Green / Blinking Green</summary>

Status: Sampling During Calibration

Can Change Color: No

A PrimeX camera starts out black, then the ring light will turn green depending on where you have wanded relative to that camera.

<figure><img src="../.gitbook/assets/image (122).png" alt="A PrimeX camera with the ringlight displaying a partial green color. "><figcaption></figcaption></figure>

When the camera starts to take samples, there will be a white light that follows the wand movement rotating around the LED.

<figure><img src="../.gitbook/assets/image (132).png" alt="A PrimeX camera with the ringlight displaying the white color rotating around the LED. "><figcaption></figcaption></figure>

This will fill in dark green and then light green when enough samples are taken.

<figure><img src="../.gitbook/assets/image (740).png" alt="A PrimeX camera with the ringlight displaying the light green color. "><figcaption></figcaption></figure>

On a SlimX camera, the status light will blink green during calibration.

<figure><img src="../.gitbook/assets/SlimX Green Recording Calibrating (1).jpg" alt="A SlimX Camera with a green status indicator. This light will blink green during calibration."><figcaption></figcaption></figure>

</details>

<details>

<summary>Flashing White</summary>

Status: Calibration

Can Change Color: No

During calibration, when cameras have collected sufficient data the ring light on a PrimeX and the status light on a SlimX will turn green. Once enough cameras have collected enough samples the remaining cameras will flash white to indicate they still need to collect more samples for a successful calibration.

<div><figure><img src="../.gitbook/assets/image (188).png" alt="A PrimeX camera with the ringlight displaying the flashing white color. "><figcaption><p>A PrimeX camera<br>with a white<br>ring light</p></figcaption></figure> <figure><img src="../.gitbook/assets/SlimX White.jpg" alt="A SlimX camera with a white indicator light."><figcaption><p>A SlimX camera <br>with a white <br>status light</p></figcaption></figure></div>

</details>

<details>

<summary>None</summary>

Status: Playback

Can Change Color: Yes

Camera is operating but Motive is in Edit Mode.

<div><figure><img src="../.gitbook/assets/image (179).png" alt="A PrimeX camera with the ringlight displaying no color. "><figcaption><p>A PrimeX camera <br>with the ring light <br>displaying no color.</p></figcaption></figure> <figure><img src="../.gitbook/assets/SlimX MotiveinEdit.jpg" alt="A SlimX camera with the status light displaying no color. "><figcaption><p>A SlimX camera <br>with the status light <br>displaying no color.</p></figcaption></figure></div>

</details>

<details>

<summary>Yellow</summary>

Status: Selected

Can Change Color: Yes

The camera is selected in Motive.&#x20;

<div><figure><img src="../.gitbook/assets/image (193).png" alt="A PrimeX camera with the ringlight displaying the Yellow color. "><figcaption><p>A PrimeX camera <br>with a yellow<br>Ring Light</p></figcaption></figure> <figure><img src="../.gitbook/assets/SlimX Yellow Camera Selected.jpg" alt="A SlimX camera with the status light displaying the Yellow color. "><figcaption><p>A SlimX camera <br>with a yellow<br>status light</p></figcaption></figure></div>

</details>

<details>

<summary>Red</summary>

Status: Reference

Can Change Color: Yes

The camera is in reference mode. Instead of capturing the marker data, the camera is recording reference video, Grayscale and MJPEG.

<div><figure><img src="../.gitbook/assets/image (194).png" alt="A PrimeX camera with the ringlight displaying the Red color. "><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/SlimX Red Reference.jpg" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>Cycle Cyan / Blinking Cyan</summary>

Status: Firmware Update

Can Change Color: No

PrimeX cameras will cycle in cyan and SlimX cameras will flash in cyan when firmware is being written to flash.&#x20;

The bottom left display will show the percentage of the firmware update that has occurred. Once the update reaches 100%, the color turns off and the camera reboots.

<div><figure><img src="../.gitbook/assets/image (765).png" alt="A PrimeX camera with the ringlight displaying the Cycle Cyan color. "><figcaption><p>A PrimeX camera <br>with the ring light <br>cycling in cyan</p></figcaption></figure> <figure><img src="../.gitbook/assets/SlimX Cyan Blinking Firmware Update.jpg" alt="A SlimX camera with the indicator light blinking the Cycle Cyan color. "><figcaption><p>A SlimX camera<br>with the status light<br>blinking in cyan</p></figcaption></figure></div>

</details>

{% hint style="success" icon="aperture" %}
#### Prime Series Cameras&#x20;

The ring light on the legacy Prime Series of cameras will cycle yellow to indicate a firmware update.&#x20;

<img src="../.gitbook/assets/image (163).png" alt="A Prime series camera with a flashing yellow ring light, to indicate a firmware update." data-size="original">
{% endhint %}

### Bottom Left Display Values

On every PrimeX and SlimX camera there is an additional display in the bottom left corner of the camera.

{% hint style="info" %}
#### How to Troubleshoot E Codes

Codes with the E prefix are error codes that are typically caused by network issues, such as a bad Ethernet cable or a bad port on the switch. These issues can often be resolved by unplugging the camera from the switch and plugging it back in or restarting the switch to reset the entire network. Replace the Ethernet cable or plug the camera into a different port or into a different switch, if the reset doesn't work.&#x20;

If the error code persists after changing the cable and the port, contact [OptiTrack Support](https://optitrack.com/support#create-new-support-ticket).&#x20;
{% endhint %}

<details>

<summary>Cycling Numbers</summary>

Camera is in the process of updating the firmware. The numbers will start at 0 and increase to 100 indicating that the firmware has completed 100% of the update.

</details>

<details>

<summary>Constant Number</summary>

This is the camera number as assigned by Motive. Every time Motive is closed and reopened or a camera is removed from the system, the number will update accordingly.

</details>

<details>

<summary>E1</summary>

The Camera has failed to auto negotiate a link speed with the switch it is plugged into.

</details>

<details>

<summary>E2</summary>

The firmware received from motive is corrupt or invalid.

</details>

<details>

<summary>E3</summary>

The bitstream received from motive is corrupt or invalid.

</details>

<details>

<summary>E4</summary>

The bitstream received from Motive was unable to be loaded.

</details>

<details>

<summary>E5</summary>

The camera was unable to write the firmware provided by Motive to internal flash.

contact [OptiTrack Support](https://optitrack.com/support#create-new-support-ticket) if this error displays.&#x20;

</details>

### Changing Status Ring Light

Some of the colors of the Status Ring can be customized. To do so, go to [Settings > General](../motive-ui-panes/settings/settings-general.md). Click the color box next to the status you would like to change. This will open a color picker window where you can choose a solid color or choose multi-color to oscillate between colors. You also have the ability to save a color to your color library to apply it to other statuses.

#### Turning off Aim Assist Button LED

The Aim Assist button on the back of the camera is illuminated with a built-in LED. Once the system is setup and all the cameras are focused and aimed correctly, you may prefer to turn this off.&#x20;

* Go to [Settings > General](../motive-ui-panes/settings/settings-general.md).&#x20;
* In the Aim Assist section, toggle the [Aiming Button LED](../motive-ui-panes/settings/settings-general.md#aiming-button-led) setting to off.&#x20;

![](<../.gitbook/assets/image (109).png>)

### Back Ring Light Colors

The PrimeX and SlimX Series cameras also have a status light on the back panel to indicate the state of the camera.&#x20;

{% hint style="success" icon="aperture" %}
#### A Note about Firmware

Different versions of Motive require different versions of firmware. During startup, Motive will automatically update the firmware to the required version if necessary, whenever a newer (or older) version of Motive is installed.
{% endhint %}

<details>

<summary>Green - Initialize Phase 1</summary>

Camera is powered and boot loader is running. Preparing to run main firmware.

</details>

<details>

<summary>Yellow - Initialize Phase 2</summary>

Firmware is running and switch communication in progress.

</details>

<details>

<summary>Blinking Green (Slow) - Initialize Phase 3</summary>

Switch communication established and awaiting an IP address.

</details>

<details>

<summary>Cyan - Firmware Loading</summary>

Host has initiated firmware upload process.

</details>

<details>

<summary>Blinking Yellow - Initialize Phase 4</summary>

Camera has fully initialized. In process of synchronizing with camera group or eSync.

</details>

<details>

<summary>Blinking Green (Fast) - Running</summary>

Camera is fully operational and synchronized to the camera group. Ready for data capture.

</details>

<details>

<summary>Blue - Hibernating</summary>

Camera is in a low power state and not sending data. Occurs after closing Motive but leaving the cameras connected to the switch.

</details>

<details>

<summary>Alternating Red - Firmware Reset</summary>

On board flash memory is being reset.

</details>

<details>

<summary>Alternating Yellow - Firmware Update</summary>

Firmware is being written to flash. Numeric display in front will show progress. On completion, the light turns green and camera reboots.

</details>

### Firmware Updates

The camera should not be unplugged during a firmware reset or firmware update. Give the camera time to finish this process before closing Motive.

If a camera doesn't update its firmware with the rest of the cameras, it will not get loaded into Motive. This could be caused by miscommunication between the camera and the switch when loading in numerous cameras. If this occurs, wait for all cameras that are updating to finish, then restart Motive. The cameras that failed to update will now update.&#x20;
