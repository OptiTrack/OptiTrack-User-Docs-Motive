---
description: Highlights of new features in Motive 3.4
---

# What's New in Motive 3.4

{% embed url="https://vimeo.com/1126271450/a695992bb7?fe=ci&fl=cl&share=copy" %}

## Camera SDK for Linux

The Camera SDK now supports both Ubuntu and Fedora operating systems. A new easy-to-use sample is included to make integrating cameras into your own software solution easier than ever.

* **Supports All Modes** - PrimeX, VersaX, and SlimX cameras support all video modes including the new Duplex Mode.
* **Easy to Setup** - Easy-to-setup examples and build instructions allow you to get started developing as quickly as possible.
* **Color Camera Support** - Prime Color cameras work in the example application with no additional modifications.
* **Simple Example** - An additional simple application exists for stripped down reference code including debugging information for the eSync 2.

See the [Camera SDK for Linux](../developer-tools/camera-sdk-linux/) page for more details.&#x20;

## Range of Motion (Bone Refinement)

Motive now lets you refine joint placement and scale bones on the skeleton so they better match a real performer’s movement. During setup, the actor completes a guided Range of Motion routine that moves each tracked bone to compute more accurate joint locations. These joint locations can be reused across multiple sessions by updating the constraint locations (not bone lengths) using the associated tool in Motive.

Watch the video below, or see the [Skeleton Tracking](../motive/skeleton-tracking.md) page or the [Builder Pane](../motive-ui-panes/builder-pane.md) page for detailed instructions on completing a Range of Motion refinement.&#x20;

{% embed url="https://vimeo.com/1126271525/4b9455d21a?fe=ci&fl=cl&share=copy" %}

## Improved Marker Placement Guide

The Builder pane has a new green marker visual as well as joint axis lines to more easily define where joint markers should be placed.

<figure><img src="../.gitbook/assets/Skeleton Joints.gif" alt=""><figcaption></figcaption></figure>

See the [Skeleton Tracking](../motive/skeleton-tracking.md) page or the [Builder Pane](../motive-ui-panes/builder-pane.md) page for more information on the different marker types used to create a skeleton.  &#x20;

## Licensing Updates

_Motive:Tracker_ licenses now support standard (non-trained) markersets. Please see our [website](https://optitrack.com/software/motive/specs.html?versions=621&617&606&619&608) for more detail on the features available with each license type.&#x20;

## Max Ray Length

The _Max Ray Length_ solver setting is back! This allows you to exclude long rays in big spaces to reduce jitter and improve tracking stability.

Please see the [Settings: Live Pipeline](../motive-ui-panes/settings/settings-live-pipeline.md) page for more information.

## Continuous Calibration Pane

Previously part of the Info pane, Continuous Calibration now has its own pane. See the [Continuous Calibration page](../motive/calibration/continuous-calibration.md) for more detail.&#x20;

## Other Highlights

* The new skeleton spine model introduced in version 3.3 has been renamed to 7 Spine Segment, and is now the default when creating new skeletons.
* Added the ability to display the distance between any selected 3D objects. Previously, this displayed only when markers were selected.
* A user definable Notes property is now available for all hardware devices.
* And more!&#x20;

{% hint style="info" %}
**For More Information:**

Visit our website for more detail on the new version:

* What's New: [https://www.optitrack.com/software/motive/](https://www.optitrack.com/software/motive/)
* Change log and Download link: [https://www.optitrack.com/support/downloads/](https://www.optitrack.com/support/downloads/)
{% endhint %}
