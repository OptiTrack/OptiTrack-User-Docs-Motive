---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/probe-pane
---

# Probe Pane

This page provides information on the Probe pane, which can be accessed under the _Tools_ tab or by clicking on the [![Toolbar Probe 30.png](https://v30.wiki.optitrack.com/images/f/f7/Toolbar_Probe_30.png)](https://v30.wiki.optitrack.com/index.php?title=File:Toolbar_Probe_30.png) icon from the toolbar.

## Overview

This section highlights what's in the Probe pane. For detailed instructions on how to use the Probe pane to collect measurement samples, read through [Measurement Probe Kit Guide](../motive/measurement-probe-kit-guide.md).

#### **Probe Calibration**

The _Probe Calibration_ feature under the Rigid Body edit options can be used to re-calibrate a pivot point of a measurement probe or a custom Rigid Body. This step is also completed as one of the calibration steps when first creating a measurement probe, but you can re-calibrate it under the _Modify tab_.

#### **Steps**

1. In Motive, select the Rigid Body or a measurement probe.
2. Bring out the probe into the tracking volume where all of its markers are well-tracked.
3. Place and fit the tip of the probe in one of the slots on the provided calibration block.
4. Click _Start_
5. Once it starts collecting the samples, slowly move the probe in a circular pattern while keeping the tip fitted in the slot; making a cone shape overall. Gently rotate the probe to collect additional samples.
6. When sufficient samples are collected, the mean error of the calibrated pivot point will be displayed.
7. Click _Apply_ to use the calibrated definition or click _Cancel_ to calibrate again.

#### **Digitized Points**

The Digitized Points section is used for collecting sample coordinates using the probe. You can select which Rigid Body to use from the drop-down menu and set the number of frames used to collect the sample. Clicking on the _Sample_ button will trigger Motive to collect a sample point and save it into the `C:\Users\[Current User]\Documents\OptiTrack\measurements.csv` file.

When needed, export the measurements of the accumulated digitized points into a separate CSV file, and/or clear the existing samples to start a new set of measurements

#### **Live Position**

Shows the live X/Y/Z position of the calibrated probe tip.

#### **Last Point**

Shows the live X/Y/Z position of the last sampled point.

#### **Live Distance**

Shows the distance between the last point and the live position of the probe tip.

#### **Distance**

Shows the distance between the last two collected samples.

#### **Angle**

Shows the angle between the last three collected samples

![Probe pane showing the measurements.](<../.gitbook/assets/image (102).png>)
