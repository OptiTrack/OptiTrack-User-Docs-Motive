---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/plugins/autodesk-motionbuilder/autodesk-motionbuilder-timecode-data
---

# Autodesk MotionBuilder: Timecode Data

## Overview

Timecode for each captured frame can also be streamed into MotionBuilder using the plugin. When the timecode data is available in Motive, you can view the streamed data under the properties of the connected OptiTrack devices.

To monitor the timecode, select the connected OptiTrack I/O devices under the **Navigator** tab and open the **Properties** tab of the **Resources** panel as the tracking data is being streamed to MotionBuilder. Among the properties, timecode values will be reported. This will be available for any type of devices (**Optical** device, **Skeleton** device, **Insight VCS** device) that is connected to Motive. Please note that timecode gets streamed out only if it is available in the capture. Timecode signal can be integrated to the capture data only when SMPTE timecode signal is fed into the camera system via the eSync synchronization hub.

* Timecode data is presented to MotionBuilder on each device with the following properties, which can be keyed during recording.
* Use the **Timecode Key Interpolation** property to set the interpolation method:
  * 0 : Constant (aka Stepping)
  * 1 : Linear
  * 2 : Cubic (MoBu default)

![Timecode settings.](<../../.gitbook/assets/image (1339).png>)

![Timecode display in Motive.](<../../.gitbook/assets/image (182).png>)

### Timecode on Assets

In addition to timecode on each device, the Skeleton device also writes timecode onto each Skeleton asset root as an animatable user property. This allows you to export that asset only, while keeping the original timecode.

![Click on image to enlarge.](<../../.gitbook/assets/image (1254).png>)

### The Skeleton Device Keying to Timecode

{% hint style="info" %}
This is for the Skeleton device plugin ONLY.
{% endhint %}

The Skeleton Device has the option of writing keys using the timecode contained in the Motive data stream. This requires:

* A timecode generator
* OptiTrack Ethernet Series only
* OptiTrack eSync connected to timecode generator and configured in Motive for timecode.

See the [Timecode setup Wiki page](../../synchronization/optitrack-timecode.md) for how to do this.

To enable keying to timecode, set the following Device properties:

* **Use Motive Timecode**
  * Check this property to enable timestamping keys using the timecode contained in the Motive data packet.
* **Timecode Format**
  * Use this property to specify the timecode format.
  * This must be correctly specified, and requires you to specify the format of the timecode generator that is connected to Motive via the OptiTrack eSync device.

MotionBuilder defines the following formats, and the numeric value to use for the property:

NTSC\_DROP : 29.97\
NTSC\_FULL: -29.97f\
PAL\_25: -25.0f\
FILM\_24 : -24.0f\
FILM\_23976: -23.976f\
FRAMES\_30: -30.0f\
FRAMES\_5994: -59.94f
