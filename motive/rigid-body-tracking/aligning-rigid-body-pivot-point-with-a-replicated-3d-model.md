---
description: >-
  This page provides instructions for aligning a Rigid Body pivot point with a
  real object replicated 3D model.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/rigid-body-tracking/aligning-rigid-body-pivot-point-with-a-replicated-3d-model
---

# Aligning Rigid Body Pivot Point with a Replicated 3D Model

## Overview

When using streamed Rigid Body data to animate a real-life replicated 3D model, it's critical that the  Rigid Body's pivot point aligns with the location of the pivot point in the corresponding 3D model. If they are not aligned, the animated motion will not be in a 1:1 ratio to the actual motion.&#x20;

This alignment is critical for real-time VR applications where real-life objects are 3D modeled and animated in the scene.&#x20;

### Live and Edit Modes

These steps can be completed in Live or Edit mode.&#x20;

There are two modes for editing:

* **Edit:** Playback in standard Edit mode displays and streams the processed 3D data saved in the recorded _Take_. Changes made to settings and assets are not reflected in the Viewport until the _Take_ is [reprocessed](../reconstruction-and-2d-mode.md#applying-changes-to-3d-data).&#x20;
* **Edit 2D:** Playback in Edit 2D mode performs a live reconstruction of the 3D data, immediately reflecting changes made to settings or assets. These changes are displayed in real-time but are not saved into the recording until the _Take_ is [reprocessed](../reconstruction-and-2d-mode.md#applying-changes-to-3d-data) and saved. To playback in 2D mode, click the Edit button and select _Edit 2D_. &#x20;

<figure><img src="../../.gitbook/assets/Live or Edit mode - switch to 2D (1).png" alt="" width="200"><figcaption><p>Click Edit to select the Edit mode.</p></figcaption></figure>

{% hint style="info" %}
Regardless of the selected Edit mode, you must reprocess the _Take_ to create new 3D data based on the modifications made.&#x20;
{% endhint %}

## Aligning Rigid Body Pivot Point

There are two methods to align the pivot point of a rigid body. We recommend using the measurement probe method as it is the most accurate.&#x20;

### Measurement Probe

#### **Step 1. Create a Rigid Body of the target object**

[Create a Rigid Body](./) from the markers on the target object. By default, Motive will position the pivot point of the Rigid Body at the geometric center of the marker placements. Once the Rigid Body has been created, place the object in a stable location where it will remain stationary.

#### **Step 2. Create a measurement probe asset**

Please refer to [Measurement Probe](../measurement-probe-kit-guide.md) page for instructions to create a measurement probe asset in Motive.&#x20;

You can purchase an OptiTrack probe or create your own.&#x20;

<figure><img src="../../.gitbook/assets/Create Probe.jpeg" alt=""><figcaption><p>Creating a Probe Asset to collect data samples. </p></figcaption></figure>

#### **Step 3. Collect data points to outline the silhouette**

Use the created measurement probe to collect [sample data points](../measurement-probe-kit-guide.md#step-2-sample-collection) that outline the silhouette of the object. Mark all corners and other key features on the object.

![Collecting Sample Data Points with a Probe.](<../../.gitbook/assets/Set Points with Probe.jpeg>)

#### **Step 4. Attach 3D model**

After generating 3D data points using the probe, attach the game geometry (obj file) to the Rigid Body.&#x20;

1. Select the Rigid Body in either the Devices pane or the 3D Viewport to show its properties in the Properties pane.
2. In the Visuals section, select _Custom Model_ under the Geometry property. (Note: this is an Advanced setting.)
3. This will open the Attached Geometry field. Click the folder to the right of the field to browse to the location of your 3D model.&#x20;

![Attaching a custom geometry model. Click image to enlarge.](<../../.gitbook/assets/3 Attach Geometry.png>)

{% hint style="info" %}
From the sampled 3D points, You can also export markers created from the probe to Maya or other content creation packages to generate models guaranteed to scale correctly.
{% endhint %}

#### **Step 5. Translate the pivot point**

Next, use the [GIZMO tool](../assets/gizmo-tool-translate-rotate-and-scale.md) to translate the 3D model to align with the silhouette sample collected in Step 3. Move, rotate, and scale the model until it is perfectly aligned with the silhouette.

{% hint style="info" %}
Decrease the size of the marker visual to improve accuracy when aligning the object. To change the marker size, click the <img src="../../.gitbook/assets/Settings button (2).png" alt="" data-size="line"> button to open the Application Settings panel. Go to _View -> 3D View -> Markers -> Custom Size_.&#x20;
{% endhint %}

![Use the GIZMO tool to translate the 3D model. Click image to enlarge.](<../../.gitbook/assets/4 Geometry attached unaligned.png>)

#### **Step 6. Align to Geometry**

1. With both the Rigid Body and the 3D model selected, open the Modify tab in the Builder pane.
2. In the _Align to..._ section, select _Geometry_.&#x20;
3. The pivot point for the Rigid Body will snap to align with the pivot point for the 3D model.

![Click image to enlarge.](<../../.gitbook/assets/5 Align to Geometry.png>)

### Reference Grayscale View

Use a reference camera when the option to use the probe method is not available.

1. Change the Video Type for one of the cameras to grayscale mode.
2. Right-click the camera and select Make Reference.&#x20;
3. This will create a Rigid Body overlay in the [Camera view pane](../../motive-ui-panes/viewport.md#cameras-view). Follow steps [4](aligning-rigid-body-pivot-point-with-a-replicated-3d-model.md#step-4.-attach-3d-model), [5](aligning-rigid-body-pivot-point-with-a-replicated-3d-model.md#step-5.-translate-the-pivot-point), and [6](aligning-rigid-body-pivot-point-with-a-replicated-3d-model.md#step-6.-align-to-geometry) above using the reference video to align the Rigid Body pivot.

![Aligning a Rigid Body pivot point using a reference camera.](<../../.gitbook/assets/6 Reference Grayscale view.png>)
