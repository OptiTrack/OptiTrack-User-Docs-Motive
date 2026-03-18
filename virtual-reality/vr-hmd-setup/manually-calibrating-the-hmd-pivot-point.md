# Manually Calibrating the HMD Pivot Point

{% hint style="danger" %}
This page covers manual positioning of HMD Rigid Bodies in Motive. This is an old workflow that a bit of time and effort to set up. With the [HMD Calibration tool](../../motive-ui-panes/builder-pane.md), you can create and auto-calibrate the HMD Rigid Bodies much easier and faster.
{% endhint %}

## HMD Marker Setup

When manually positioning the appropriate location of the Rigid Body pivot point, you will need to have landmark markers on specific locations.

#### Attachment

When attaching retroreflective markers, make sure markers are securely attached and readily captured by the cameras. For attaching the markers, we recommend using our 20 mm wide and 30 mm tall M4 threaded plastic marker bases with Acrylic adhesives, available at the [webstore](http://optitrack.com/products/motion-capture-markers), to attach the markers onto the HMD.

#### Placement

A markered HMD will be defined as a Rigid Body in Motive. When placing markers, make sure the placement [asymmetry](../../motive/rigid-body-tracking/#asymmetrical-marker-placements) is respected in the arrangement within the HMD. Also, the marker arrangements between multiple HMDs must be incongruent. For more details, read about marker placement from the [Rigid Body Tracking](../../motive/rigid-body-tracking/) page. Also, for tracking the HMD, two landmark markers must be placed in the following locations:

**Eye-level Side Markers (2)**

Place two markers on left and right side of the HMD, these markers will serve two additional purposes. First, they will indicate yaw of the HMD, and they will be used to align the Rigid Body orientation with the orientation of the actual HMD component. Thus, a line interconnecting the two markers must be parallel to the frontal plane, or the display, of the HMD. Second, these markers will be used to locate the elevation of the eyes when creating the Rigid Body in Motive. In summary, the two landmark markers must be carefully placed considering the following:

* The markers should **align along eye-level** of the user when the HMD is mounted.
* Most importantly, place these markers in the exactly same location of the left and right side so that they form a precisely symmetrical arrangement.
* Same dimension attachment bases must be used for both of the markers.

![Sample marker placement: Front view. The two side markers are placed parallel to the HMD display.](<../../.gitbook/assets/image (1075).png>) ![Sample marker placement: Top view.](<../../.gitbook/assets/image (815).png>)

![Sample marker placement: Side view. The two side markers are aligned along the eye-level of the user.](<../../.gitbook/assets/image (754).png>)

## Pivot Point Position

For best virtual experiences, the pivot point of the HMD Rigid Body, in Motive, needs to be positioned on the midpoint between two eyes, of the user when the HMD is put on. To locate this, use the side and top-center landmark markers as references. For more information on adjusting Rigid Body pivot points, please read through the [Rigid Body Tracking](../../motive/rigid-body-tracking/) page.

{% hint style="info" %}
**Gizmo Tool: Translate, Rotate, and Scale**

For Motive versions 2.1 and above, setting pivot point location is much easier using the GIZMO tools. Instructions on adjusting pivot point location using the GIZMO tool is detailed in the following page: [Gizmo Tool: Translate, Rotate, and Scale](../../motive/assets/gizmo-tool-translate-rotate-and-scale.md). Using this tool, you can select markers in the 3D viewport and easily place the Rigid Body pivot point onto a specific landmark marker, or onto a midpoint between the selected markers.
{% endhint %}

**1. Set the pivot point over the landmark marker.** Use the [Set Pivot Point to Selected Marker](../../motive/rigid-body-tracking/#resetting-the-pivot-point) feature to assign the pivot point to the marker. This will set the elevation of the pivot point along the eye-level.

![Top view: Rigid body pivot point is assigned to the left landmark marker.](<../../.gitbook/assets/image (1066).png>) ![Side view: Now both the landmark marker and the pivot point is positioned along the user's eye-level elevation.](<../../.gitbook/assets/image (830).png>)

**2. Place the pivot point at the midpoint between the two markers.** Enable _Two Marker Distance_ visual aid [![Viewport16.png](https://v30.wiki.optitrack.com/images/6/6d/Viewport16.png)](https://v30.wiki.optitrack.com/index.php?title=File:Viewport16.png) from the [perspective pane](../../motive-ui-panes/viewport.md#perspective-view), and select the two landmark markers in Motive. This will provide a distance between two markers. Then, using this information, translate the pivot point laterally by half of the distance so that it is placed right on the midpoint between two markers.

![Translating the pivot point by half of the measured distance to place it at the midpoint.](<../../.gitbook/assets/image (833).png>) ![Translating the pivot point by half of the measured distance to place it at the midpoint. Click image to enlarge.](<../../.gitbook/assets/image (807).png>)

**3. Translate the pivot point along the z-axis using the translation tool.** For the most accurate position, you may need to physically measure the sagittal, z-axis, distance from the landmark marker to the root of nose, and apply the measured offset.

![Pivot point translated along the z-axis.](<../../.gitbook/assets/image (758).png>) ![Perspective view of the adjusted pivot point position.](<../../.gitbook/assets/image (771).png>)

## Orientation

Now that you have translated the pivot point, you need to make detailed adjustments to the orientation using the [orientation transformation](../../motive/rigid-body-tracking/) tool. For best results, align the two front markers along the x-axis grid and roughly center the Rigid Body along the z-axis grid. Then, check to make sure that each of the Rigid Body orientation axes is parallel to the grids lines in Motive. If there is any deviation, apply rotation to adjust the offset. If needed, transparency of the axes and the grids can be adjusted from the Application settings.

* In Unreal Engine: the X-axis of the HMD Rigid Body must be directed forward.
* In Unity: the Z-axis of the HMD Rigid Body must be directed forward.

![Slight offset in the Rigid Body orientation.](<../../.gitbook/assets/image (1056).png>) ![After Adjusting, the Rigid Body orientation axes are precisely aligned with the global axes of Motive.](<../../.gitbook/assets/image (804).png>)

{% hint style="info" %}
**Tip:** Once you have the Rigid Body asset for the HMD configured, you can export the asset into a TRA file for future uses. Importing the TRA file (e.g. CV1.tra) will load the Rigid Body (HMD) asset and make it available for use; however, the marker placement **must** remain unchanged in order to re-load previously created Rigid Bodies.
{% endhint %}
