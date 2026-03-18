# Active Finger Marker Set

This page briefly goes over the active finger marker set and how it needs to be set up.

## Overview

The active finger Marker Set utilizes the tracking capability of active markers and its active labeling features to accomplish tracking of both the hands and the fingers. These Marker Sets require the [active marker](../../active-components/active-marker-tracking/) tracking solution and the Tag(s). Wired from an active Tag, each active marker must attach to the expected locations. For each hand, 10 active markers are needed for each hand.

{% hint style="info" %}
**Manus VR Gloves**

Alternatively, you can also use Manus VR Gloves for tracking the fingers. For more information, refer to the [Manus Glove Setup](../../active-components/active-components-hardware/manus-glove-setup.md) page.
{% endhint %}

#### **Requirements**

* The Active Base Station
* Active Tag(s) with active markers.
* A way to attach active markers onto the hands (e.g. gloves).

#### **Below** Marker Sets **uses active finger tracking**

* Baseline + Active Fingers (57)
* Core + Active Fingers (62)
* Right Hand + Active Fingers (10)
* Left Hand + Active Fingers (10)

## Marker Placement

* Total 10 markers will be attached on each hand (8 Active markers and 2 passive)
* The 8 Active markers will be placed on the hand and the 2 passive markers will be on either side of the wrist.
* **Tags:** Attach Tags to each hand for the active LEDs.
* **Active Markers (10):** Each Tag connects up to 8 active markers. Position the wired active markers at the tip of all five fingers (5), one each on the knuckle of the index finger and the pinky finger (2), and lastly, place the remaining active marker on the inside of the bottom thumb joint.

![Marker placements shown in the Builder pane.](<../../.gitbook/assets/image (696).png>)

![Active finger markers tracked in the 3D viewport, and the corresponding markers shown in the Prime Color reference view.](<../../.gitbook/assets/image (720).png>)

## Creating the hand

Steps for creating an active finger Marker Set is the same as the other skeleton Marker Set:

1. Open the [Builder pane](../../motive-ui-panes/builder-pane.md) and select the desired hand Marker Set under the drop-down menu.
2. Make sure all of the markers are placed in the correct positions. For the Core + Active Fingers (62) Marker Set, please make sure the passive full body tracking markers are also placed on the person's body.
3. Once the markers have been placed, ask the subject to strike the [calibration pose](../../motive/skeleton-tracking.md#calibration-pose).
4. Select the finger markers in the 3D viewport.
5. The Marker Detected must match Marker Required in the [Builder pane](../../motive-ui-panes/builder-pane.md).
6. Click _Create_.

![10 markers selected for creating the Left Hand + Active Fingers.](<../../.gitbook/assets/image (679).png>) ![Left Hand created.](<../../.gitbook/assets/image (697).png>)
