# Biomechanics Marker Sets

In a Motive Body license, there are a number of Skeleton Marker Set templates for biomechanics tracking applications. When attaching the markers, reference the Skeleton avatar from the [Builder pane](https://v30.wiki.optitrack.com/index.php?title=Builder_pane#Skeleton:_Create) for relative locations. Then refer to the corresponding Marker Set pages, or related reference materials, for additional descriptions on where each marker must be placed on the subject.

![Biomechanical Marker Set marker placements: Biomech (57).](<../../.gitbook/assets/image (532).png>)

**Biomechanics** Marker Sets\*\*:\*\*

* Helen Hayes Lower Body
* [Biomech (57)](../../markersets/full-body/biomech-57.md)
* [Rizzoli (43)](rizzoli-markersets.md)
* [Rizzoli Lower (30)](rizzoli-markersets.md)
* Rizzoli Lower Feet (44)
* [Rizzoli Upper (15)](rizzoli-markersets.md)
* [Rizzoli Left Foot (16)](rizzoli-markersets.md)
* [Rizzoli Right Foot (16)](rizzoli-markersets.md)
* Conventional Full Body (39)
* Conventional Upper Body (27)
* Conventional Lower Body (16)

{% hint style="info" %}
**Biomechnical Analysis**

Biomechanical analysis requires advanced computations in order to obtain most accurate biomechanical data. However, joint angles generated and exported from Motive are intended for basic visualization purposes only and should not be used for any type of biomechanical or clinical analysis. To use captured tracking data for such applications, the 3D markers data must be pipelined down to a biomechanical analysis software (STT InSight, Visual3D or The MotionMonitor) for further analysis.
{% endhint %}

{% hint style="info" %}
**Asymmetry**

Asymmetry is the key to avoiding the congruency for tracking multiple Marker Sets. When there are more than one similar marker arrangements in the volume, marker labels may be confused. Thus, it is beneficial to place segment makers — joint markers must always be placed on anatomical landmarks — in asymmetrical positions for similar rigid bodies and skeletal segments. This provides a clear distinction between two similar arrangements. Furthermore, avoid placing markers in a symmetrical shape within the segment as well. For example, a perfect square marker arrangement will have ambiguous orientation and frequent mislabels may occur throughout the capture. Instead, follow the rule of thumb of placing the less critical markers in asymmetrical arrangements.
{% endhint %}
