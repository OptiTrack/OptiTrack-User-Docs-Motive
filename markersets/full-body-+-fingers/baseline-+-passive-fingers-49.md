---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/markersets/full-body-+-fingers/baseline-+-passive-fingers-49
---

# Baseline + Passive Fingers (49)

![Front view of the Baseline + Passive Fingers (49) Marker Set.](<../../.gitbook/assets/image (1004).png>) ![Back view of the Baseline + Passive Fingers (49) Marker Set.](<../../.gitbook/assets/image (985).png>)

### Head Markers

| Label     | Related Segment | Description                                                                                                                                                                                  |
| --------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| HeadTop   | Head            | Place the marker on the head tip.                                                                                                                                                            |
| HeadFront | Head            | Place the marker at the center of the forehead.                                                                                                                                              |
| HeadSide  | Head            | Place the marker on the either side of the head, slightly above the ear. When capturing multiple actors with similar proportions, place the marker on opposite side for clearer distinction. |

### Torso Markers

| Label                        | Related Segment | Description                                                                                                                                                                                                                                                                                                                                      |
| ---------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| BackTop                      | Torso           | Place the marker on the spine right below the neck. For best results, LUArmHigh-LShoulderBack-BackTop-RshoulderBack-RUArmHigh markers should align roughly in a straight line when the actor is in T-pose. Also, note that this marker must be placed at an elevation higher than the chest marker for the torso segment to be tracked properly. |
| Chest                        | Torso           | Place the marker at the center of the sternum, about 5 cm below where the neck starts.                                                                                                                                                                                                                                                           |
| <p>BackLeft<br>BackRight</p> | Torso           | These two markers are located symmetrically on each side of the back, slightly below the lowest end of the shoulder blade (scapular bone).                                                                                                                                                                                                       |

### Waist Markers

Note that the waist markers are the key markers in modeling the pelvis bone, which is the major segment governing the other subsequent Skeleton segments. For best results, avoid placing the waist markers in a rectangle shape. When tracking multiple actors with similar proportions, introduce an offset to one of the WaistBack marker, or the WaistCMarker (included only with the 13 additional Marker Set), to create an asymmetrical arrangements.

| Label                             | Related Segment | Description                                                                                                                                                                               |
| --------------------------------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>WaistLFront<br>WaistRFront</p> | Pelvis          | Placed the marker on the protruding bone located on the front of the pelvis (left/right anterior iliac spine bone). The prominence can be palpated from left and right side of the waist. |
| <p>WaistLBack<br>WaistRBack</p>   | Pelvis          | Place the WaistLBack and WaistRBack markers above left/right hip; about 10 cm above the hip joint.                                                                                        |

### Shoulder Markers

When placing the shoulder markers, ask the actor to stand in the [T-pose](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#calibration-pose) in order to place the markers on accurate locations. It could also be helpful to ask the actor to do few rounds of arm abduction and adduction to palpate for the shoulder axis. These markers determine the width of the shoulder and respective relationship with the upper arm segment.

| Label                                 | Related Segment | Description                                                                                                                                                                                                                                                                    |
| ------------------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <p>LShoulderBack<br>RShoulderBack</p> | Shoulder        | Place the marker on the shoulder joint (glenohumeral joint) on the back.                                                                                                                                                                                                       |
| <p>LShoulderTop<br>RShoulderTop</p>   | Shoulder        | Place the marker at the top of each shoulder where you can palpate the protruding bone, which is usually located just before where the upper arm start when in T-pose. More specifically, the prominence is on the distal end of the clavicle bone (acrominoclavicular joint). |

### Arm Markers

| Label                         | Related Segment | Description                                                                                                                                                                                                                                                                                                                                        |
| ----------------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>LElbowOut<br>RElbowOut</p> | Upper Arm       | Place the marker on the lateral side of the elbow joint, slightly towards the upper arm. More specifically, on the lateral epicondyle of the distal end of the humerous. Ask the actor to flex and extend the arm few times to confirm that markers are placed along the elbow axis and maintain stationary throughout the range of motion cycles. |
| <p>LUArmHigh<br>RUArmHigh</p> | Upper Arm       | Place the marker on the back of the upper arm near the groove between the triceps. For best results, LUArmHigh, LShoulderBack, BackTop, RshoulderNack, and RUArmHigh should align roughly in a straight line when in T-pose.                                                                                                                       |

### Hand + Finger Markers

Finger Marker Sets include extra markers on the fingers, and the finger tracking is done by analyzing the kinematics of the hand and estimating the pose of each finger. The WristIn marker is removed and replaced by a forearm marker. Attaching finger markers uses mocap Velcro gloves and hand markers, which can be found from our [webstore](http://optitrack.com/products/motion-capture-suits/).

![](<../../.gitbook/assets/image (1039).png>) ![](<../../.gitbook/assets/image (974).png>) ![](<../../.gitbook/assets/image (1036).png>)

| Label                         | Related Segment | Description                                                                                                                                                                                                                                                       |
| ----------------------------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>LFArm<br>RFArm</p>         | Forearm         | Place the marker on the front side of the forearm while in T-pose. For best results, slightly offset the left and right forearm markers to introduce the asymmetry on each side.                                                                                  |
| <p>LWristOut<br>RWristOut</p> | Fore Arm / Hand | This marker is not included in the finger Marker Sets. Place the marker on the outside (lateral side) of the wrist axis. (distal end of the radius bone). Note that the wrist axis is not always located on the protruding bone but 1-2 cm more towards the hand. |
| <p>LThumb<br>RThumb</p>       | Hand            | Place the marker on the side of the thumb joint.                                                                                                                                                                                                                  |
| <p>LIndex<br>RIndex</p>       | Hand            | Place the marker on the side of the index finger joint (proximal interphalangeal joint).                                                                                                                                                                          |
| <p>LPinky<br>RPinky</p>       | Hand            | Place the marker on the side of the pinky finger joint (proximal interphalangeal joint).                                                                                                                                                                          |
| <p>LHandIn<br>RHandIn</p>     | Hand            | Place the marker on the knuckle of the index finger, but slightly towards the side.                                                                                                                                                                               |
| <p>LHandOut<br>RHandOut</p>   | Hand            | Place the marker on the knuckle of the pinky finger, but slightly towards the side.                                                                                                                                                                               |

### Leg Markers

| Label                             | Related Segment | Description                                                                                                                                                                                                                                                                                                                                                                |
| --------------------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>LThighFront<br>RThighFront</p> | Upper Leg       | Place the marker on the front side of the thigh, along the midline. For best results, slightly offset the height of the left and right markers to introduce the asymmetry.                                                                                                                                                                                                 |
| <p>LKneeOut<br>RKneeOut</p>       | Upper Leg       | Place the marker on the outter prominence of the knee joint; on the lateral epicondyle of the femur. Palpate the knee for the protruding bone from the upper leg, and place it right on the axis. Ask the actor to flex and extend the knee few times to confirm that the markers are placed along the axis and maintain stationary throughout the range of motion cycles. |
| <p>LShin<br>RShin</p>             | Lower Leg       | Place the marker on the shin bone; on the midline of the lower leg. For best results, slightly offset the height of the left and right markers to introduce the asymmetry.                                                                                                                                                                                                 |

### Foot Markers

| Label                         | Related Segment | Description                                                                                                   |
| ----------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------- |
| <p>LAnkleOut<br>RAnkleOut</p> | Lower Leg/Foot  | Place the marker on the protruding bone outside of the ankle joint; on the lateral end of the malleolus bone. |
| <p>LToeOut<br>RToeOut</p>     | Foot            | Place the marker just before the little toe joint; on the distal end of the fifth metatarsal bone.            |
| <p>LToeIn<br>RToeIn</p>       | Foot            | Place the marker just before the big toe joint; on the distal end of the first metatarsal bone.               |

### Hinged Toe Markers

Hinged toe Marker Sets create toe segments in the Skeleton. Two additional markers are added to each foot, one on the toe-tip and another on the heel. The hinged toe markers are included in all baseline Marker Sets except for Baseline (37) and Upper Body Marker Sets.

| Label                     | Related Segment | Description                                                         |
| ------------------------- | --------------- | ------------------------------------------------------------------- |
| <p>LHeel<br>RHeel</p>     | Foot            | Place at the center of the heel.                                    |
| <p>LToeTip<br>RToeTip</p> | Toe             | Place the marker on the tip of the second toe; next to the big toe. |
