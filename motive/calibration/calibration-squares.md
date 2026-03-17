# Calibration Squares

During [Calibration](./) process, a calibration square is used to define global coordinate axes as well as the ground plane for the capture volume. Each calibration square has different vertical offset value. When defining the ground plane, Motive will recognize the square and ask user whether to change the value to the matching offset.

| Square Type                                   | Descriptions                                                                                                                                                                                                                                                                                                        |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](<../../.gitbook/assets/image (710).png>)  | 82404ec08b4c4bbabff5652a7153ece0                                                                                                                                                                                                                                                                                    |
| ![](<../../.gitbook/assets/image (348).png>)  | <p>CS-200:</p><ul><li>Long arm: Positive z</li><li>Short arm: Positive x</li><li>Vertical offset: 19 mm</li><li>Marker size: 14 mm (diameter)</li></ul>                                                                                                                                                             |
| ![](<../../.gitbook/assets/image (1054).png>) | <p>CS-400: <br><br>Used for general for common mocap applications. Contains knobs for adjusting the balance as well as slots for aligning with a force plate.</p><ul><li>Long arm: Positive z</li><li>Short arm: Positive x</li><li>Vertical offset: 45 mm</li><li>Marker size: 19 mm (diameter)</li></ul>          |
| ![](<../../.gitbook/assets/image (708).png>)  | <p>Legacy L-frame square: <br><br>Legacy calibration square designed before changing to the Right-hand coordinate system.</p><ul><li>Long arm: Positive z</li><li>Short arm: Negative x</li></ul>                                                                                                                   |
| ![](<../../.gitbook/assets/image (1221).png>) | <p>Custom Calibration square: <br><br>Position three markers in your volume in the shape of a typical calibration square (creating a ~90 degree angle with one arm longer than the other). Then select the markers to set the ground plane.</p><ul><li>Long arm: Positive z</li><li>Short arm: Negative x</li></ul> |

{% hint style="info" %}
When creating a custom ground plane, you can use Motive to help you move the markers to create approximately 90 degree between the 3 markers. This is of course contingent on how good your calibration is, however, this will still give you a fairly accurate starting point when setting your ground plane.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/image (1235).png" alt=""><figcaption></figcaption></figure>

## Vertical Offset

The Vertical Offset is the distance between the center of the markers on the [calibration square](calibration-squares.md) and the actual ground and is a required value in setting the global origin.&#x20;

Motive accounts for the vertical offset when using a standard OptiTrack calibration square, setting the origin at the bottom corner of the calibration square rather than the center of the marker.&#x20;

<div><figure><img src="../../.gitbook/assets/Ground plane offset.png" alt=""><figcaption><p>Vertical offset of the CS-400 calibration square.</p></figcaption></figure> <figure><img src="../../.gitbook/assets/Calibration marker vs global origin.png" alt=""><figcaption><p>Ground plane marker is offset from the global origin after calibration.</p></figcaption></figure></div>

When using a custom calibration square, measure the distance between the center of the marker and the lowest tip at the vertex of the calibration square. Enter this value in the _Vertical Offset_ field in the Calibration pane.&#x20;

{% hint style="info" %}
The **Vertical Offset** property can also be used to place the ground plane at a specific elevation. A positive offset value will set the plane below the markers, and a negative value will set the plane above the markers.
{% endhint %}

## Coordinate System&#x20;

The Right-Handed Coordinate System is used as the standard, across internal and exported formats and data streams.&#x20;
