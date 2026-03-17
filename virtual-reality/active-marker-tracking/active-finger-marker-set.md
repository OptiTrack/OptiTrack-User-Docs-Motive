---
description: This page reviews the active finger marker set and how to set it up.
---

# Active Finger Marker Set

## Overview

The active finger Marker Set utilizes the tracking capability of active markers and the active labeling features to accomplish tracking of both the hands and the fingers. These Marker Sets require the [active marker](../../active-components/active-marker-tracking/) tracking solution and a set of Tag(s). Wired from an active Tag, each active marker must attach to the expected locations. For each hand, 8 active markers are needed, with 2 passive markers attached at the wrist.

{% hint style="info" %}
**Manus VR Gloves**

Alternatively, you can also use Manus VR Gloves for tracking the fingers. For more information, refer to the [Manus Glove Setup](../../active-components/active-components-hardware/manus-glove-setup.md) page.
{% endhint %}

#### **Requirements**

* The Active BaseStation
* Active Tag(s) with active markers.
* A way to attach active markers onto the hands (e.g., gloves).

#### **Below** Marker Sets **uses active finger tracking**

* Baseline + Active Fingers (57)
* Core + Active Fingers (62)
* Right Hand + Active Fingers (10)
* Left Hand + Active Fingers (10)

Please note that the numbers listed in the Marker Set names are the total number of markers needed, including both active and passive markers.&#x20;

## Marker Placement

* Total of 10 markers will be attached on each hand (8 Active markers and 2 passive).
* **Tags:** Attach Tags to each hand for the active LEDs.
* **Passive Markers (2):** Attach the 2 passive markers to both sides of the wrist, directly on the joints of either side along the wrist flexion point.
* **Active Markers (8):** Each Tag connects up to 8 active markers. Position the wired active markers at the tip of all five fingers (5), one each on the knuckle of the index finger and the pinky finger (2), and place the remaining active marker on the inside of the bottom thumb joint.

![Marker placements shown in the Builder pane.](<../../.gitbook/assets/image (1337).png>)

![Active finger markers tracked in the 3D viewport, and the&#x20;
corresponding markers shown in the Prime Color reference view.](<../../.gitbook/assets/image (1275).png>)

## Creating the hand

Steps for creating an active finger Marker Set is the same as the other Skeleton Marker Sets:

1. Open the [Builder pane](../../motive-ui-panes/builder-pane.md) and select the desired hand Marker Set under the drop-down menu.
2. Make sure all of the markers are placed in the correct positions. For the Core + Active Fingers (62) Marker Set, please make sure the passive full body tracking markers are also placed on the person's body.
3. Once the markers have been placed, ask the subject to strike the [calibration pose](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#calibration-pose).
4. Select the finger markers in the 3D viewport.
5. The Marker Detected must match Marker Required in the [Builder pane](../../motive-ui-panes/builder-pane.md).
6. Click _Create_.

![10 markers selected for creating the Left Hand + Active Fingers.](<../../.gitbook/assets/image (1319).png>) ![Left Hand created.](<../../.gitbook/assets/image (1296).png>)
