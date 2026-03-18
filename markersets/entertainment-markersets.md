# Entertainment Marker Sets

## Overview

There are two different Skeleton marker templates that can be used for entertainment applications: Baseline and Core. Both of these Marker Sets provide high-quality tracking, but the Core marker set templates may provide more stable tracking for high-camera count systems.

Among these marker sets, some of the placements are shared. For example, the Baseline (41) Marker Sets serves as a starting point, and the other baseline Marker Sets add more markers to it. When attaching the markers, you should reference the Skeleton avatar from the [Builder pane](https://v30.wiki.optitrack.com/index.php?title=Builder_pane#Skeleton:_Create) for relative locations. The following charts and pages provide additional descriptions to where each marker should be placed, find related markers or click on one of the baseline Marker Sets pages for specific placement descriptions.

{% hint style="info" %}
**Asymmetry**

Asymmetry is the key to avoiding the congruency for tracking multiple Marker Sets. When there are more than one similar marker arrangements in the volume, marker labels may be confused. Thus, it is beneficial to place segment makers — joint markers must always be placed on anatomical landmarks — in asymmetrical positions for similar rigid bodies and skeletal segments. This provides a clear distinction between two similar arrangements. Furthermore, avoid placing markers in a symmetrical shape within the segment as well. For example, a perfect square marker arrangement will have ambiguous orientation and frequent mislabels may occur throughout the capture. Instead, follow the rule of thumb of placing the less critical markers in asymmetrical arrangements.
{% endhint %}

## Skeleton Templates

**List of Baseline marker set templates**

* [Baseline (41)](full-body/baseline-41.md)
* [Baseline + Passive Fingers (49)](full-body-+-fingers/baseline-+-passive-fingers-49.md)
* [Baseline + ActiveFingers (57)](../active-components/active-marker-tracking/active-finger-markerset.md)
* [Baseline Upper (25)](upper/baseline-upper-25.md)
* [Baseline Lower (20)](lower/baseline-lower-20.md)

**List of Core marker set templates**

* [Core (50)](full-body/core-50.md)
* [Core + Passive Fingers (54)](full-body-+-fingers/core-+-passive-fingers-54.md)
* [Core + ActiveFingers (62)](../active-components/active-marker-tracking/active-finger-markerset.md)

### Baseline Markers

![Front view of the Baseline (37) Marker Set.](<../.gitbook/assets/image (226).png>) ![Back view of the Baseline (37) Marker Set.](<../.gitbook/assets/image (218).png>)

| **Head Markers** |                 |                                                                                                                                                                                              |
| ---------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Label            | Related Segment | Description                                                                                                                                                                                  |
| HeadTop          | Head            | Place the marker on the head tip.                                                                                                                                                            |
| HeadFront        | Head            | Place the marker at the center of the forehead.                                                                                                                                              |
| HeadSide         | Head            | Place the marker on the either side of the head, slightly above the ear. When capturing multiple actors with similar proportions, place the marker on opposite side for clearer distinction. |

| **Torso Markers**            |                 |                                                                                                                                                                                                                                                                                                                                                  |
| ---------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Label                        | Related Segment | Description                                                                                                                                                                                                                                                                                                                                      |
| BackTop                      | Torso           | Place the marker on the spine right below the neck. For best results, LUArmHigh-LShoulderBack-BackTop-RshoulderBack-RUArmHigh markers should align roughly in a straight line when the actor is in T-pose. Also, note that this marker must be placed at an elevation higher than the chest marker for the torso segment to be tracked properly. |
| Chest                        | Torso           | Place the marker at the center of the sternum, about 5 cm below where the neck starts.                                                                                                                                                                                                                                                           |
| <p>BackLeft<br>BackRight</p> | Torso           | These two markers are located symmetrically on each side of the back, slightly below the lowest end of the shoulder blade (scapular bone).                                                                                                                                                                                                       |

| **Waist Markers**               |                 |                                                                                                                                                                                           |
| ------------------------------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Label                           | Related Segment | Description                                                                                                                                                                               |
| WaistLFront                     | Pelvis          | Placed the marker on the protruding bone located on the front of the pelvis (left/right anterior iliac spine bone). The prominence can be palpated from left and right side of the waist. |
| WaistRFront                     | Pelvis          |                                                                                                                                                                                           |
| <p>WaistLBack<br>WaistRBack</p> | Pelvis          | Place the WaistLBack and WaistRBack markers above left/right hip; about 10 cm above the hip joint.                                                                                        |

{% hint style="info" %}
Note that the waist markers are the key markers in modeling the pelvis bone, which is the major segment governing the other subsequent Skeleton segments. For best results, avoid placing the waist markers in a rectangle shape. When tracking multiple actors with similar proportions, introduce an offset to one of the WaistBack marker, or the WaistCMarker (included only with the 13 additional Marker Set), to create an asymmetrical arrangements.
{% endhint %}

| **Shoulder Markers**                  |                 |                                                                                                                                                                                                                                                                                |
| ------------------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Label                                 | Related Segment | Description                                                                                                                                                                                                                                                                    |
| <p>LShoulderBack<br>RShoulderBack</p> | Shoulder        | Place the marker on the shoulder joint (glenohumeral joint) on the back.                                                                                                                                                                                                       |
| <p>LShoulderTop<br>RShoulderTop</p>   | Shoulder        | Place the marker at the top of each shoulder where you can palpate the protruding bone, which is usually located just before where the upper arm start when in T-pose. More specifically, the prominence is on the distal end of the clavicle bone (acrominoclavicular joint). |

{% hint style="info" %}
When placing the shoulder markers, ask the actor to stand in the [T-pose](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#calibration-pose) in order to place the markers on accurate locations. It could also be helpful to ask the actor to do few rounds of arm abduction and adduction to palpate for the shoulder axis. These markers determine the width of the shoulder and respective relationship with the upper arm segment.
{% endhint %}

| **Arm Markers**               |                 |                                                                                                                                                                                                                                                                                                                                                    |
| ----------------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Label                         | Related Segment | Description                                                                                                                                                                                                                                                                                                                                        |
| <p>LElbowOut<br>RElbowOut</p> | Upper Arm       | Place the marker on the lateral side of the elbow joint, slightly towards the upper arm. More specifically, on the lateral epicondyle of the distal end of the humerous. Ask the actor to flex and extend the arm few times to confirm that markers are placed along the elbow axis and maintain stationary throughout the range of motion cycles. |
| <p>LUArmHigh<br>RUArmHigh</p> | Upper Arm       | Place the marker on the back of the upper arm near the groove between the triceps. For best results, LUArmHigh, LShoulderBack, BackTop, RshoulderNack, and RUArmHigh should align roughly in a straight line when in T-pose.                                                                                                                       |

| Hand Markers                  |                 |                                                                                                                                                                                                            |
| ----------------------------- | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Label                         | Related Segment | Description                                                                                                                                                                                                |
| <p>LWristOut<br>RWristOut</p> | Fore Arm / Hand | Place the marker on the outside (lateral side) of the wrist axis. (distal end of the radius bone). Note that the wrist axis is not always located on the protruding bone but 1-2 cm more towards the hand. |
| <p>LWristIn<br>RWristIn</p>   | Fore Arm / Hand | Place the marker on the inner prominence (medial side) of the wrist axis (distal end of the ulnar bone).                                                                                                   |
| <p>LHandOut<br>RHandOut</p>   | Hand            | Place the marker slightly below the pinky knuckle. More specifically, between distal end of the fifth and fourth mertacarpal bones.                                                                        |

{% hint style="info" %}
For best results, place the hand markers so that the shape of the marker arrangement is asymmetrical itself and also unique to the shape on the other hand. Since the wrist marker placement is fixed along the wrist axis, offset the HandOut or the HandIn markers to create the unique arrangements. For more robust and simple tracking, hand rigid-bodies can be attached on the hand to replace the markers and guarantee the asymmetrical and non-deforming marker placement.
{% endhint %}

| **Leg Markers**                   |                 |                                                                                                                                                                                                                                                                                                                                                                            |
| --------------------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Label                             | Related Segment | Description                                                                                                                                                                                                                                                                                                                                                                |
| <p>LThighFront<br>RThighFront</p> | Upper Leg       | Place the marker on the front side of the thigh, along the midline. For best results, slightly offset the height of the left and right markers to introduce the asymmetry.                                                                                                                                                                                                 |
| <p>LKneeOut<br>RKneeOut</p>       | Upper Leg       | Place the marker on the outter prominence of the knee joint; on the lateral epicondyle of the femur. Palpate the knee for the protruding bone from the upper leg, and place it right on the axis. Ask the actor to flex and extend the knee few times to confirm that the markers are placed along the axis and maintain stationary throughout the range of motion cycles. |
| <p>LShin<br>RShin</p>             | Lower Leg       | Place the marker on the shin bone; on the midline of the lower leg. For best results, slightly offset the height of the left and right markers to introduce the asymmetry.                                                                                                                                                                                                 |

| **Foot Markers**              |                 |                                                                                                               |
| ----------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------- |
| Label                         | Related Segment | Description                                                                                                   |
| <p>LAnkleOut<br>RAnkleOut</p> | Lower Leg/Foot  | Place the marker on the protruding bone outside of the ankle joint; on the lateral end of the malleolus bone. |
| <p>LToeOut<br>RToeOut</p>     | Foot            | Place the marker just before the little toe joint; on the distal end of the fifth metatarsal bone.            |
| <p>LToeIn<br>RToeIn</p>       | Foot            | Place the marker just before the big toe joint; on the distal end of the first metatarsal bone.               |
