# Gizmo Tool: Translate, Rotate, and Scale

This page provides instructions on how to utilize the Gizmo tool for modifying asset definitions (Rigid Bodies and Skeletons) on the [3D Perspective View](../../motive-ui-panes/viewport.md) of Motive

{% hint style="danger" %}
**Edit Mode:** As of Motive 3.0, asset editing can only be performed in [Edit mode](../motive-basics.md)
{% endhint %}

{% hint style="danger" %}
**Solved Data:** In order to edit asset definitions from a recorded _Take_, corresponding [Solved Data](../data-recording/data-types.md) must be removed before making the edit, and then recalculated.
{% endhint %}

## Overview

The gizmo tools allow users to make modifications on reconstructed 3D markers, Rigid Bodies, or Skeletons for both real-time and post-processing of tracking data. This page provides instructions on how to utilize the gizmo tools.

![](<../../.gitbook/assets/image (634).png>)

## Rigid Body Assets

\
Using the gizmo tools from the perspective view options to easily modify the position and orientation of Rigid Body pivot points. You can translate and rotate Rigid Body pivot, assign pivot to a specific marker, and/or assign pivot to a mid-point among selected markers.

* Select Tool (Hotkey: Q): Select tool for normal operations.
* Translate Tool (Hotkey: W): Translate tool for moving the Rigid Body pivot point.
* Rotate Tool (Hotkey: E): Rotate tool for reorienting the Rigid Body coordinate axis.
* Scale Tool (Hotkey: R): Scale tool for resizing the Rigid Body pivot point.

{% hint style="info" %}
**Precise Position/Orientation:** When translating or rotating the Rigid Body, you can CTRL + select a 3D reconstruction from the scene to precisely position the pivot point, or align a coordinate axis, directly on, or towards, the selected marker. Multiple reconstructions can be also be selected and their geometrical center (midpoint) will be used as the target reference.
{% endhint %}

![](<../../.gitbook/assets/image (130).png>)

## Tutorial Videos

{% hint style="danger" %}
Please note that the following tutorial videos were created in an older version of Motive. The workflow in 3.0 is slightly different and only requires you to select Translate, Rotate, or Scale from the [3D Viewport Toolbar selection dropdown](gizmo-tool-translate-rotate-and-scale.md#overview) to begin manipulating your Asset.&#x20;
{% endhint %}

### Rigid Bodies

#### Translation

{% embed url="https://www.youtube.com/watch?v=C_ne0LIrizA" %}

#### Rotation

{% embed url="https://www.youtube.com/watch?feature=emb_logo&v=mCnSFPLXDqs" %}

#### Rescale

{% embed url="https://www.youtube.com/watch?t=1s&v=xZdV4-saZ3E" %}

### Skeleton Assets

You can utilize the gizmo tools to modify skeleton bone lengths, joint orientations, or scale the spacing of the markers. Translating and rotating the skeleton assets will change how skeleton bone is positioned and oriented with respect to the tracked markers, and thus, any changes in the skeleton definition will affect the realistic representation of the human movement.

#### Translation

{% embed url="https://www.youtube.com/watch?v=wZeqtVkj2A0" %}
\\
{% endembed %}

#### Rotation

{% embed url="https://www.youtube.com/watch?v=q1irsQlUZqE" %}

#### Scale

The scale tool modifies the size of selected skeleton segments.

![](<../../.gitbook/assets/image (149).png>)

## Reconstructed 3D Markers

The gizmo tools can also be used to edit positions of reconstructed markers.In order to do this, you must be working reconstructed 3D data in post-processing. In live-tracking or 2D mode doing live-reconstruction, marker positions are reconstructed frame-by-frame and it cannot be modified. The _Edit Assets_ must be disabled to do this (Hotkey: T).

**Translate**

Using the translate tool, 3D positions of reconstructed markers can be modified. Simply click on the markers, turn on the translate tool (Hotkey: W), and move the markers.

![](<../../.gitbook/assets/image (164).png>)

**Rotate**

Using the rotate tool, 3D positions of a group of markers can be rotated at its center. Simply select a group of markers, turn on the rotate tool (Hotkey: E), and rotate them.\\

![](<../../.gitbook/assets/image (192).png>)

**Scale**

Using the scale tool, 3D spacing of a group of makers can be scaled. Simply select a group of markers, turn on the scale tool (Hotkey: R) and scale their spacing.

![](<../../.gitbook/assets/image (159).png>)

## Cameras

Cameras can be modified using the gizmo tool if the Settings Window > General > Calibration > "Editable in 3D View" property is enabled. Without this property turned on the gizmo tool will not activate when a camera is selected to avoid accidentally changing a calibration. The process for using the gizmo tool to fix a misaligned camera is as follows:

1. Select the camera you wish to fix, then view from that camera (Hotkey: 3).
2. Select either the Translate or Rotate gizmo tool (Hotkey: W or E).
3. Use the red diamond visual to align the unlabeled rays roughly onto their associated markers.
4. Right lock then choose "Correct Camera Position/Orientation". This will perform a calculation to place the camera more accurately.
5. Turn on Continuous Calibration if not already done. Continuous calibration should finish aligning the camera into the correct location.

![](<../../.gitbook/assets/image (106) (1) (1) (1) (1) (1) (1) (1).png>) ![](<../../.gitbook/assets/image (151).png>)
