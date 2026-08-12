---
description: Configuration options for exporting data to the USD format.
---

# Data Export: USD

## Overview

Universal Scene Description, or OpenUSD, is an open source framework developed by Pixar Animation Studios that provides an efficient method for working with and compiling 3D content across applications. Export tracking data from Motive into the USD format for use with other applications, such as Blender, Unreal Engine, Godot, CAD systems, and other design software.

Please visit the [Alliance for OpenUSD](https://aousd.org/) for more information on the OpenUSD format and its various uses.&#x20;

{% hint style="info" %}
The USD export option is available with the Motive Body license only.&#x20;
{% endhint %}

## General Export Options

The general export options set the basic parameters of the export. To change any of these parameters, click the ![The ellipses button that allows a user to update a setting in Motive. ](<../../.gitbook/assets/Settings Change Button.png>) button to the right of the option.&#x20;

<figure><img src="../../.gitbook/assets/USD Data Export Options TOP.png" alt="Motive&#x27;s USD Export options, showing all of the General options and some of the specific options. "><figcaption></figcaption></figure>

<details>

<summary>Frame Rate</summary>

The number of samples included per second of exported data. The default option is to use the current frame rate. Click the ellipses to the right to set a custom frame rate.&#x20;

</details>

<details>

<summary>Start Frame</summary>

Starting frame of the exported data. Set to one of the following:

* The recorded first frame of the exported _Take_ (the default option).
* The start of the working range (or scope range) as configured under the [Control Deck](https://docs.optitrack.com/motive-ui-panes/control-deck) in the [Graph](https://docs.optitrack.com/motive-ui-panes/graph-view-pane) [View pane](https://docs.optitrack.com/motive-ui-panes/graph-view-pane).
* _Custom_ to enter a specific frame number.

</details>

<details>

<summary>End Frame</summary>

End frame of the exported data. Set to one of the following:

* The recorded end frame of the exported _Take_ (the default option).
* The end of the working range (or scope range) as configured under the [Control Deck](https://docs.optitrack.com/motive-ui-panes/control-deck) in the [Graph](https://docs.optitrack.com/motive-ui-panes/graph-view-pane) [View pane](https://docs.optitrack.com/motive-ui-panes/graph-view-pane).
* _Custom_ to enter a specific frame number.

</details>

<details>

<summary>Scale</summary>

Apply scaling to the coordinates/distance of tracked assets in the exported tracking data.

</details>

<details>

<summary>Units</summary>

Set the measurement units to use for exported data.

</details>

## Specific Export Options

Specific options determine which data to include in the export.&#x20;

{% hint style="success" %}
Assets must be solved and enabled in Motive to include in the USD export.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/USD Data Export Options BOTTOM.png" alt="Motive&#x27;s USD Export options, showing all of the Specific options. "><figcaption></figcaption></figure>

<details>

<summary>Export Skeletons</summary>

Enables the export of skeleton data. Skeleton assets must be solved and enabled in Motive to be included in the export. &#x20;

</details>

<details>

<summary>Skeleton Names</summary>

Select the specific skeletons to include in the export. Note that the skeleton must be solved and enabled in Motive to be included in the export.&#x20;

* **All Skeletons** exports all enabled skeletons included in the _Take._ This is the default option.&#x20;
* **Selected Skeletons** exports only the skeletons selected from either the Assets pane or the 3D viewport in Motive.&#x20;
* **Custom** allows you to specify which of the skeletons included in the _Take_ to export.

{% hint style="info" %}
This option is only available when _Export Skeletons_ is enabled.
{% endhint %}

</details>

<details>

<summary>Bone Naming Convention</summary>

The Bone Naming Convention determines the format to use for exported Skeleton data so each segment can be properly recognized by the client application. The naming convention must match the format used in the client application.

* **Motive:** Uses the standard Motive bone naming convention.
* **FBX:** Used for importing into Autodesk pipelines, such as MotionBuilder or Maya.
* **UnrealEngine:** Used for importing into UnrealEngine.

</details>

<details>

<summary>Export Rigid Bodies</summary>

Enables the export of Rigid Bodies from the selected _Take_. Rigid Body assets must be solved and enabled in Motive to be included in the export.&#x20;

</details>

<details>

<summary>Rigid Body Names</summary>

Select the specific Rigid Bodies to include in the export. Note that the Rigid Body must be solved and enabled in Motive to be included in the export.&#x20;

* **All Rigid Bodies** exports all solved and enabled Rigid Bodies included in the _Take._ This is the default option.
* **Selected Rigid Bodies** exports only the Rigid Bodies selected in the Assets pane or the 3D Viewport in Motive.&#x20;
* **Custom** allows you to specify which of the Rigid Bodies included in the _Take_ to export.

{% hint style="info" %}
This option is only available when _Export Rigid Bodies_ is enabled.
{% endhint %}

</details>

<details>

<summary>Export Markersets</summary>

Enables the export of Trained Markerset data from the selected _Take_. Trained Markerset assets must be solved and enabled in Motive to be included in the export. &#x20;

</details>

<details>

<summary>Markerset Names</summary>

Select the specific Trained Markersets to include in the export. Note that the Trained Markerset must be solved and enabled in Motive to be included in the export.&#x20;

* **All Markersets** exports all enabled Trained Markersets included in the _Take._ This is the default option.
* **Selected Markersets**  exports only the Trained Markersets selected in the Assets pane or the 3D Viewport in Motive.&#x20;
* **Custom** allows you to specify which of the Trained Markersets included in the _Take_ to export.

{% hint style="info" %}
This option is only available when _Export Markersets_ is enabled.
{% endhint %}

</details>

<details>

<summary>Export Markers</summary>

Enables the export of labeled marker data from the selected _Take._&#x20;

</details>

<details>

<summary>Export Unlabeled Markers</summary>

Enables the export of unlabeled marker data from the selected _Take._&#x20;

</details>

<details>

<summary>Exclude Fingers</summary>

Enables the export of skeleton data without including data for the fingers.&#x20;

{% hint style="info" %}
This option is only available when _Export Skeletons_ is enabled.
{% endhint %}

</details>

<details>

<summary>Cameras</summary>

Enables the export of 2D camera data. Select **All Cameras** or **Color Cameras** from the dropdown list.   &#x20;

</details>

<details>

<summary>Skeletal Mesh</summary>

Enables the export of the Motive skeletal mesh along with the skeleton data.&#x20;

</details>

<details>

<summary>Z-up Skeleton</summary>

Enables the export of Skeleton data using the Z-up coordinate system.&#x20;

</details>
