---
description: Details for using the tools available on the Info Pane.
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/info-pane
---

# Info Pane

## Overview

The Info pane can be accessed from the View tab or by clicking on the <img src="../.gitbook/assets/Screenshot 2023-09-08 114722.png" alt="A screenshot of the Info Pane button in Motive. " data-size="line"> icon in the toolbar.

The Info pane can be used to check tracking in Motive. There are three different tools available from this pane: measurement tools, Rigid Body information, and active debugging. You can switch between different types from the <img src="../.gitbook/assets/Motive Context Menu (11).png" alt="A screenshot of the three-dot context menu in Motive. " data-size="line"> context menu. The measurement tool allows you to use a calibration wand to check detected wand length and the error when compared to the expected wand length.

<div><figure><img src="../.gitbook/assets/image (1122).png" alt="A screenshot of the Info Pane in Motive with the Measurement Tools displayed. "><figcaption><p>Info pane in Motive.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Info Pane New Options Menu.png" alt="A screenshot of the three-dot menu options for the Motive Info Pane: Measurement Tools; Rigid Bodies; Active Debugging; and Close Pane. "><figcaption><p>Tool options shown in the menu.</p></figcaption></figure></div>

## Measurement Tool

The **Measurement Tool** is used to check calibration quality and tracking accuracy of a given volume. There are two tools in this: the Wand Validation tool and the Marker Movement tool.

<figure><img src="../.gitbook/assets/image (1082).png" alt="A screenshot of the Measurement Tools on the Motive Info Pane. "><figcaption><p>Measurement tools accessed from the Info pane.</p></figcaption></figure>

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

The Rigid Bodies tool under Info pane in Motive displays real-time tracking information of a Rigid Body selected in Motive. Reported data includes a total number of tracked Rigid Body markers, mean errors for each of them, and the 6 Degree of Freedom (position and orientation) tracking data for the Rigid Body.

<figure><img src="../.gitbook/assets/image (365).png" alt="A screenshot of the Rigid Body Tools on the Motive Info Pane. "><figcaption><p>Info pane displaying tracking information of a selected Rigid Body.</p></figcaption></figure>

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

## Active Debugging

Active Debugging is a troubleshooting tool that shows the number of IMU data packets dropped, the largest gap between IMU data packets being sent, and IMU misalignment.&#x20;

When any value exceeds the Maximum settings at the bottom of the pane, the text will turn magenta.&#x20;

<div><figure><img src="../.gitbook/assets/3.2 Info Pane Active Debugging No Errors.png" alt="A screenshot of the Active Debugging Tool on the Motive Info Pane, with no errors present. "><figcaption><p>Active Debugging Info Pane.</p></figcaption></figure> <figure><img src="../.gitbook/assets/3.2 Info Pane Active Debugging WITH Errors.png" alt="A screenshot of the Active Debugging Tool on the Motive Info Pane, with errors present. "><figcaption><p>Active Debugging Info Pane - with errors</p></figcaption></figure></div>

#### Drops

This column shows the number of drops that have occurred during the past 60 seconds.&#x20;

#### IMU % Drops

This column denotes the number of IMU packet drops that an IMU Tag is encountering over 60 frames.

#### Max Gap&#x20;

Max Gap denotes the number of frames between IMU data packets sent where the IMU packets were dropped. i.e. in the image above on the left, the maximum gap shows there were no frame gaps where IMU packets were either not sent or received. The image on the right has a gap of 4 frames where the IMU packets were either not sent or received.&#x20;

#### Alignment

This column shows the degree to which the alignment of the IMU varies from its expected alignment.&#x20;
