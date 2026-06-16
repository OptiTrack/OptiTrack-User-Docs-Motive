---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/quick-start-guides/quick-start-guide-outdoor-tracking-setup
---

# Quick Start Guide: Outdoor Tracking Setup

PrimeX 41, PrimeX 22, Prime 41\*, and Prime 17W\* camera models have powerful tracking capability that allows tracking outdoors. With strong infrared (IR) LED illuminations and some adjustments to its settings, a Prime system can overcome sunlight interference and perform 3D capture. This page provides general hardware and software system setup recommendations for outdoor captures.

Please note that when capturing outdoors, the cameras will have shorter tracking ranges compared to when tracking indoors. Also, the system calibration will be more susceptible to change in outdoor applications because there are environmental variables (e.g. sunlight, wind, etc.) that could alter the system setup. To ensure tracking accuracy, routinely re-calibrate the cameras throughout the capture session.

## Weather and Backgrounds

Even though it is possible to capture under the influence of the sun, it is best to pick cloudy days for captures in order to obtain the best tracking results. The reasons include the following:

* Bright illumination from the daylight will introduce extraneous reconstructions, requiring additional effort in the post-processing on cleaning up the captured data.
* Throughout the day, the position of the sun will continuously change as will the reflections and shadows of the nearby objects. For this reason, the camera system needs to be routinely re-masked or re-calibrated.

The surroundings can also work to your advantage or disadvantage depending on the situation. Different outdoor objects reflect 850 nm Infrared (IR) light in different ways that can be unpredictable without testing. Lining your background with objects that are black in Infrared (IR) will help distinguish your markers from the background better which will help with tracking. Some examples of outdoor objects and their relative brightness is as follows:

* Grass typically appears as bright white in IR.
* Asphalt typically appears dark black in IR.
* Concrete depends, but it's usually a gray in IR.

## Hardware Setup Recommendations

**1. \[Camera Setup]** [Camera mount setup](../hardware/camera-mount-structures.md)

In general, setting up a truss system for mounting the cameras is recommended for stability, but for outdoor captures, it could be too much effort to do so. For this reason, most outdoor capture applications use tripods for mounting the cameras.

\
**2. \[Camera Setup]** [Camera aim](../hardware/aiming-and-focusing.md)

Do not aim the cameras directly towards the sun. If possible, place and aim the cameras so that they are capturing the target volume at a downward angle from above.

\
**3. \[Camera Setup]** [Lens f-stop](../hardware/aiming-and-focusing.md)

Increase the f-stop setting in the Prime cameras to decrease the aperture size of the lenses. The f-stop setting determines the amount of light that is let through the lenses, and increasing the f-stop value will decrease the overall brightness of the captured image allowing the system to better accommodate for sunlight interference. Furthermore, changing this allows camera exposures to be set to a higher value, which will be discussed in the later section. Note that f-stop can be adjusted only in PrimeX 41, PrimeX 22, Prime 41\*, and Prime 17W\* camera models.

![For outdoor capture applications, increase the f-stop setting to decrease the lens aperture size](<../.gitbook/assets/image (625).png>)

**4. \[Camera Setup]** Utilize shadows

Even though it is possible to capture under sunlight, the best tracking result is achieved when the capture environment is best optimized for tracking. Whenever applicable, utilize shaded areas in order to minimize the interference by sunlight.

![Capturing outdoors under shadows](<../.gitbook/assets/image (627).png>)

## Motive Settings

**1. \[Camera Settings]** [Max IR LED Strength](../motive-ui-panes/devices-pane.md)

Increase the LED setting on the camera system to its maximum so that IR LED illuminates at its maximum strength. Strong IR illumination will allow the cameras to better differentiate the emitted IR reflections from ambient sunlight.

**2. \[Camera Settings]** [Camera Exposure](../motive-ui-panes/devices-pane.md)

In general, increasing camera exposure makes the overall image brighter, but it also allows the IR LEDs to light up and remain at its maximum brightness for a longer period of time on each frame. This way, the IR illumination is stronger on the cameras, and the imager can more easily detect the marker reflections in the IR spectrum.

![](<../.gitbook/assets/image (632).png>)

When used in combination with the increased f-stop on the lens, this adjustment will give a better distinction of IR reflections. Note that this setup applies only for outdoor applications, for indoor applications, the exposure setting is generally used to control overall brightness of the image.

\*Legacy camera models

\\
