# Baseline (41)

![](<../../.gitbook/assets/image (970).png>) ![](<../../.gitbook/assets/image (1028).png>)

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

| Label                                 | Related Segment | Description                                                                                                                                                                                                                                                                   |
| ------------------------------------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>LShoulderBack<br>RShoulderBack</p> | Shoulder        | Place the marker on the shoulder joint (glenohumeral joint) on the back.                                                                                                                                                                                                      |
| <p>LShoulderTop<br>RShoulderTop</p>   | Shoulder        | Place the marker at the top of each shoulder where you can palpate the protruding bone, which is usually located just before where the upper arm start when in T-pose. More specifically, the prominence is on the distal end of the clavicle bone (acromioclavicular joint). |

### Arm Markers

| Label                         | Related Segment | Description                                                                                                                                                                                                                                                                                                                                       |
| ----------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>LElbowOut<br>RElbowOut</p> | Upper Arm       | Place the marker on the lateral side of the elbow joint, slightly towards the upper arm. More specifically, on the lateral epicondyle of the distal end of the humerus. Ask the actor to flex and extend the arm few times to confirm that markers are placed along the elbow axis and maintain stationary throughout the range of motion cycles. |
| <p>LUArmHigh<br>RUArmHigh</p> | Upper Arm       | Place the marker on the back of the upper arm near the groove between the triceps. For best results, LUArmHigh, LShoulderBack, BackTop, RshoulderNack, and RUArmHigh should align roughly in a straight line when in T-pose.                                                                                                                      |

### Hand Markers

For best results, place the hand markers so that the shape of the marker arrangement is asymmetrical itself and also unique to the shape on the other hand. Since the wrist marker placement is fixed along the wrist axis, offset the HandOut or the HandIn markers to create the unique arrangements. For more robust and simple tracking, hand rigid-bodies can be attached on the hand to replace the markers and guarantee the asymmetrical and non-deforming marker placement.

| Label                         | Related Segment | Description                                                                                                                                                                                                |
| ----------------------------- | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>LWristOut<br>RWristOut</p> | Fore Arm / Hand | Place the marker on the outside (lateral side) of the wrist axis. (distal end of the radius bone). Note that the wrist axis is not always located on the protruding bone but 1-2 cm more towards the hand. |
| <p>LWristIn<br>RWristIn</p>   | Fore Arm / Hand | Place the marker on the inner prominence (medial side) of the wrist axis (distal end of the ulnar bone).                                                                                                   |
| <p>LHandOut<br>RHandOut</p>   | Hand            | Place the marker slightly below the pinky knuckle. More specifically, between distal end of the fifth and fourth metacarpal bones.                                                                         |

### Leg Markers

| Label                             | Related Segment | Description                                                                                                                                                                                                                                                                                                                                                               |
| --------------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>LThighFront<br>RThighFront</p> | Upper Leg       | Place the marker on the front side of the thigh, along the midline. For best results, slightly offset the height of the left and right markers to introduce the asymmetry.                                                                                                                                                                                                |
| <p>LKneeOut<br>RKneeOut</p>       | Upper Leg       | Place the marker on the outer prominence of the knee joint; on the lateral epicondyle of the femur. Palpate the knee for the protruding bone from the upper leg, and place it right on the axis. Ask the actor to flex and extend the knee few times to confirm that the markers are placed along the axis and maintain stationary throughout the range of motion cycles. |
| <p>LShin<br>RShin</p>             | Lower Leg       | Place the marker on the shin bone; on the midline of the lower leg. For best results, slightly offset the height of the left and right markers to introduce the asymmetry.                                                                                                                                                                                                |

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
