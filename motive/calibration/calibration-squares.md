---
description: Options for setting the ground plane and global coordinates in Motive.
---

# Calibration Squares

During the [Calibration](./) process, a calibration square is used to define the global coordinate axes as well as the ground plane for the capture volume. This page covers the various calibration squares available.&#x20;

Each calibration square has a different vertical offset value. When defining the ground plane, Motive will recognize the square and ask the user whether to change the value to the matching offset.

| Square Type                                    | Descriptions                                                                                                                                                                                                                                                                                                        |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](<../../.gitbook/assets/image (157).png>)   | <p></p><p>CS-100: <br><br>Used to define a ground plane in a small, precise motion capture volumes.</p><ul><li>Long arm: Positive z</li><li>Short arm: Positive x</li><li>Vertical offset: 11.5 mm</li><li>Marker size: 9.5 mm (diameter)</li></ul>                                                                 |
| ![](<../../.gitbook/assets/image (162).png>)   | <p>CS-200:</p><ul><li>Long arm: Positive z</li><li>Short arm: Positive x</li><li>Vertical offset: 19 mm</li><li>Marker size: 14 mm (diameter)</li></ul>                                                                                                                                                             |
| ![](<../../.gitbook/assets/image (186).png>)   | <p>CS-400: <br><br>Used for general for common mocap applications. Contains knobs for adjusting the balance as well as slots for aligning with a force plate.</p><ul><li>Long arm: Positive z</li><li>Short arm: Positive x</li><li>Vertical offset: 45 mm</li><li>Marker size: 19 mm (diameter)</li></ul>          |
| ![](<../../.gitbook/assets/image (741).png>)   | <p>Legacy L-frame square: <br><br>Legacy calibration square designed before changing to the Right-hand coordinate system.</p><ul><li>Long arm: Positive z</li><li>Short arm: Negative x</li></ul>                                                                                                                   |
| ![](<../../.gitbook/assets/image (1) (6).png>) | <p>Custom Calibration square: <br><br>Position three markers in your volume in the shape of a typical calibration square (creating a ~90 degree angle with one arm longer than the other). Then select the markers to set the ground plane.</p><ul><li>Long arm: Positive z</li><li>Short arm: Negative x</li></ul> |

{% hint style="info" %}
When creating a custom ground plane, you can use Motive to help you move the markers to create approximately 90 degree between the 3 markers. This is of course contingent on how good your calibration is, however, this will still give you a fairly accurate starting point when setting your ground plane.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/image (8) (4).png" alt=""><figcaption></figcaption></figure>

## Coordinate System (Motive 1.7+)

For Motive 1.7 or higher, Right-Handed Coordinate System is used as the standard, across internal and exported formats and data streams. As a result, Motive 1.7 now interprets the L-Frame differently than previous releases:

![Motive 1.7+ L-Frame long (marked Z) "leg" interpreted as +Z, L-Frame short (unlabeled) leg interpreted as -X](<../../.gitbook/assets/image (134).png>)
