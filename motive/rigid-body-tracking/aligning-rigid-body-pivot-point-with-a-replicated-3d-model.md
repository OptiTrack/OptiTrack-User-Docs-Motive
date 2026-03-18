# Aligning Rigid Body Pivot Point with a Replicated 3D Model

This page provides some information on aligning a Rigid Body pivot point with a real object replicated 3D model.

{% hint style="danger" %}
Screenshots used on this page was captured in Motive 2.x. In Motive 3.x, translation of Rigid Body pivot point can be done by using the Rigid Body translations from the [Builder pane](../../motive-ui-panes/builder-pane.md). See below image for a screenshot of 3.x for the Builder and Properties pane of a Rigid Body.
{% endhint %}

![Builder and Properties pane for Rigid Bodies in 3.0 for reference.](<../../.gitbook/assets/image (443).png>)

## Overview

When using streamed Rigid Body data to animate a real-life replicate 3D model, the alignment of the pivot point is necessary. In other words, the location of the Rigid Body pivot coincides with the location of the pivot point in the corresponding 3D model. If they are not aligned accurately, the animated motion will not be in a 1:1 ratio compared to the actual motion. This alignment is commonly needed for real-time VR applications where real-life objects are 3D modeled and animated in the scene. The suggested approaches for aligning these pivot points will be discussed on this page.

## Aligning Rigid Body Pivot Point

There are two methods for doing this. Using a measurement probe to sample 3D points to reference from, or simply using a reference grayscale view to align. The first method of creating and using a measurement probe is most accurate and recommended.

### Method 1: Using Measurement Probe Feature

**Step 1. Create a Rigid Body of the target object**

First of all, create a Rigid Body from the markers on the target object. By default, the pivot point of the Rigid Body will be positioned at the geometrical center of the marker placement. Then place the object onto somewhere stable where it will stay stationary.

**Step 2. Create a measurement probe.**

For instructions on creating a measurement probe, please refer to [Measurement Probe](../measurement-probe-kit-guide.md) page. You can purchase our probe or create your own. All you need is 4 markers with a static relationship to a projected tip.

**Step 3. Collect data points to outline the silhouette**

Use the created measurement probe to collect [sample data points](../measurement-probe-kit-guide.md#step-2-sample-collection) that outlines the silhouette of your object. Mark all of the corners and other key features on the object.

![](<../../.gitbook/assets/image (602).png>)

**Step 4. Attach 3D model**

After 3D data points have been generated using the probe, attach your game geometry (obj file) to the Rigid Body by turning on the [Model Replace](https://v30.wiki.optitrack.com/index.php?title=Properties:_Rigid_Body#Model_Replace) property and importing the geometry under [Attached Geometry](../../motive-ui-panes/properties-pane/properties-pane-rigid-body.md#attached-geometry) property.

![Click image to enlarge.](<../../.gitbook/assets/image (567).png>)

{% hint style="info" %}
From the sampled 3D points, You can also export markers created from the probe to Maya or other content creation packages to generate models guaranteed to scale correctly.
{% endhint %}

**Step 5. Translate the pivot point**

Next step is to translate the 3D model so that the attached model aligns with the silhouette sample that we collected in Step 3. The model can be easily translated and rotated using the [GIZMO tool](../assets/gizmo-tool-translate-rotate-and-scale.md). Move, rotate, and scale the asset unit it is aligned with the silhouette.

For accurate alignment, it will be easier to decrease the size of the marker visual. This can be changed from the [Marker Diameter](../../motive-ui-panes/settings/) setting under the application settings panel.

![Click image to enlarge.](<../../.gitbook/assets/image (393).png>)

**Step 6. Copy transformation values**

After you have translated, rotated, and scaled the pivot point of the Rigid Body to align the attached 3D model with the sampled data points, the transformation values will be shown under the [Attached Geometry](../../motive-ui-panes/properties-pane/properties-pane-rigid-body.md#attached-geometry) property.

Copy and paste this transformation parameter onto the Rigid Body location and orientation options under the Edit tab in the [Builder pane](../../motive-ui-panes/builder-pane.md). This will translate the pivot point of the Rigid Body in Motive, and align it with the pivot point of the 3D model.

**Step 7. Zero all transformation values in the Attached Geometry section**

Once the Rigid Body pivot point has been moved using the Builder pane, zero all of the transformation configurations under the _Attached Geometry_ property for the Rigid Body.

![Click image to enlarge.](<../../.gitbook/assets/image (408).png>)

### Method 2: Using Reference Grayscale View

Alternatively, if probe method is not applicable, you can also switch one of the cameras into grayscale view, right click on the camera in the **Cameras** view and select **Make Reference**. This will create a Rigid Body overlay in the [Camera view pane](../../motive-ui-panes/viewport.md#cameras-view) to align the Rigid Body pivot using the similar approach as above.

![](<../../.gitbook/assets/image (612).png>)
