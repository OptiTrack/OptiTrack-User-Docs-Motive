# Info Pane

This page provides information on the Info pane, which can be accessed from the View tab or by clicking on the <img src="../.gitbook/assets/image (167).png" alt="" data-size="line"> icon on the toolbar.

## Overview

The Info pane can be used to check tracking in Motive. There are two different types of tools you can use from this pane: measurement tools and Rigid Body information. You can switch between different types from the <img src="../.gitbook/assets/Motive Context Menu (2).png" alt="" data-size="line"> context menu. The measurement tool allows you to use a calibration wand to check detected wand length and the error when compared to the expected wand length.

![Info pane in Motive.](<../.gitbook/assets/image (261).png>) ![Tool options shown in the menu.](<../.gitbook/assets/image (614).png>)

## Measurement Tool

The **Measurement Tool** is used to check calibration quality and tracking accuracy of a given volume. There are two tools in this: the Wand Validation tool and the Marker Movement tool.

![Measurement tools accessed from the Info pane.](<../.gitbook/assets/image (210).png>)

### Wand Validation

This tool works only with a fully calibrated capture volume and requires the calibration wand that was used during the process. It compares the length of the captured calibration wand to its known theoretical length and computes the percent error of the tracking volume. You can analyze the tracking accuracy from this.

#### **Steps**

* In Live mode, open the Measurements pane under the Tools tab.
* Access the Accuracy tools tab.
* Under the _Wand Measurement_ section, it will indicate the wand that was used for the volume calibration and its expected length (theoretical value) depending on the type of wand that was used during the system [calibration](../motive/calibration/).
* Bring the calibration wand into the volume.
* Once the wand is in the volume, detected wand length (observed value) and the calculated wand error will be displayed accordingly.

### Marker Movement

This tool calculates the measured displacement of a selected marker. You can use this tool to compare the calculated displacement in Motive against how much the marker has actually moved to check the tracking accuracy of the system.

#### **Steps**

* Place a marker inside the capture volume.
* Select the marker in Motive.
* Under the Marker Measurement section, press Reset. This zeroes the position of the marker.
* Slowly translate the marker, and the absolute displacement will be displayed in mm.

## Rigid Bodies

The Rigid Bodies tool under Info pane in Motive displays real-time tracking information of a Rigid Body selected in Motive. This lists out real-time tracking information for a selected Rigid Body in Motive. Reported data includes a total number of tracked Rigid Body markers, mean errors for each of them, and the 6 Degree of Freedom (position and orientation) tracking data for the Rigid Body.

![Info pane displaying tracking information of a selected Rigid Body.](<../.gitbook/assets/image (565).png>)

{% hint style="info" %}
**Euler Angles**

There are many potential combinations of Euler angles so it is important to understand the order in which rotations are applied, the handedness of the coordinate system, and the axis (positive or negative) that each rotation is applied about. The following conventions are used for representing Euler orientation in Motive:

* Rotation order: XYZ
* All coordinates are \*right-handed\*
* Pitch is degrees about the X axis
* Yaw is degrees about the Y axis
* Roll is degrees about the Z axis
* Position values are in millimeters
{% endhint %}
