---
description: >-
  Learn how to use the Active Puck Static Meshes included in the Live Link
  Plug-in Content folder.
---

# Live Link Content:  Active Puck Static Meshes

## Overview

OptiTrack's plugin for Unreal Engine includes an array of content options. the 5.3 plugin includes the following new content:

* ActivePuckMesh
* CinePuckMesh
* MotiveAvatarMesh
* MotiveSkeletalMesh
* MotiveSkeleton

This page covers the Active Puck and CinePuck static meshes, using the Active Puck as the example.&#x20;

<div><figure><img src="../../../.gitbook/assets/Active Puck Mesh CROPPED.png" alt=""><figcaption><p>Scaled-to-fit Active Puck.</p></figcaption></figure> <figure><img src="../../../.gitbook/assets/CinePuck mesh CROPPED.png" alt=""><figcaption><p>Scaled-to-fit CinePuck.</p></figcaption></figure></div>

The Active Puck Mesh provides a couple of different use cases:

1. Data validation. Tracking an active puck in the physical volume using the OptiTrack Live Link display provides a point of reference that allows you to validate rotation, placements, and even the scale of your volume.
2. Lens calibration device. Because the static mesh is the same scale as a real puck, its markers can be used for calibration purposes. Please see the section [Create a Lens Calibration Device](live-link-content-active-puck-static-meshes.md#create-a-lens-calibration-device), below, for more details.&#x20;

{% hint style="info" %}
We used the standard _InCameraVFX_ template in Unreal Engine for our sample project. The template includes all the necessary macros and assets needed for virtual production.&#x20;

This template is located under _Film / Video & Live Events_ in the Unreal Project Browser. &#x20;
{% endhint %}

## Add a Puck to an Unreal Engine Project

This section walks the user through adding the puck static mesh to a project and aligning it with the puck streaming from Motive.&#x20;

### Show Plugin Content

* From the Content Browser window, click the <img src="../../../.gitbook/assets/UE Content Browser Settings.png" alt="" data-size="original"> button.
* Check the boxes for _Show Engine Content_ and _Show Plugin Content_.

<figure><img src="../../../.gitbook/assets/UE Content Browser Settings Menu.png" alt="" width="158"><figcaption><p>Content Browser Settings in UE.</p></figcaption></figure>

* The Content Browser’s Navigation pane will now show the Engine Content, where the Plugins folder resides.
* Open the OptiTrack—Live Link Content folder.

<figure><img src="../../../.gitbook/assets/Live Link Content folder.png" alt="" width="563"><figcaption><p>OptiTrack's Live Link Content for Unreal Engine.</p></figcaption></figure>

* Open the _ActivePuckMesh_ folder. If using a CinePuck, open the _CinePuckMesh_ folder .

### Create Labeled Markers

The Live Link asset automatically aligns with its source in Motive. The _Markers_ settings display a visual map of the marker locations. This map is helpful for confirming the alignment of a static mesh to a streamed asset.&#x20;

* In the Live Link pane, select _OptiTrack_.
* In the _Markers_ section of the OptiTrack Properties pane, set _Create Labeled Markers_ to true.

{% hint style="info" %}
To open the Live Link pane, select _Virtual Production → Live Link_ from the _Window_ menu.
{% endhint %}

<figure><img src="../../../.gitbook/assets/Live Link Create Labeled Markers.png" alt="" width="500"><figcaption><p>Live Link Pane in Unreal Engine: Create Labeled Markers. </p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Active Puck Markers aligned.png" alt="" width="206"><figcaption><p>Labeled Live Link Markers in UE.</p></figcaption></figure>

### Create Blueprint Class

* Right click in the Content Browser to open the menu.
* Under _Create Basic Asset_, select _Blueprint Class_.

<figure><img src="../../../.gitbook/assets/Live Link Create Blueprint Class.png" alt="" width="258"><figcaption><p>Create Blueprint Class from Content Browser menu in UE.</p></figcaption></figure>

* Select Actor as the Parent Class.
* Double-click the name to give it a more meaningful name. In our example, we renamed the component _BP\_CalibratorPuck._ We will use this puck later to create a [Lens Calibration Device](live-link-content-active-puck-static-meshes.md#create-a-lens-calibration-device).&#x20;

<figure><img src="../../../.gitbook/assets/Create Blueprint - Pick parent class.png" alt="" width="463"><figcaption><p>Unreal Engine: Pick Parent Class for a new blueprint.</p></figcaption></figure>

### Add the Static Mesh

* Open the newly created Blueprint linked to the puck streaming from Motive. &#x20;
* This will open a new tab. Click the <img src="../../../.gitbook/assets/Live Link Add Component button (2).png" alt="" data-size="line"> _Add_ button in the top left of the Component pane and select _Static Mesh_ from the list of options.

<figure><img src="../../../.gitbook/assets/UE - Component add static mesh.png" alt="" width="191"><figcaption><p>Add components menu in UE.</p></figcaption></figure>

* Double-click the newly created static mesh in the list of components to rename it. In our example, we called it _ActivePuck_.
* Select the static mesh in the Components pane to display its properties in the Details pane.&#x20;
* Click the Static Mesh property (set to None by default) to select the asset to use.&#x20;
* Select _SM\_ActivePuck\_Opti_ for the Active Puck, or _SM\_CinePuck\_Opti_ if using a CinePuck.

<figure><img src="../../../.gitbook/assets/UE Static Mesh - link to puck.png" alt="" width="409"><figcaption><p>Details for a Static Mesh component in UE.</p></figcaption></figure>

The Active Puck static mesh will now appear in the scene.&#x20;

## Create a Lens Calibration Device&#x20;

An Active Puck can serve as a lens calibration device in Unreal Engine by aligning calibration points to the markers at each of the four corners. &#x20;

For accuracy and precision, use the _Top_ view in the UE Viewport.&#x20;

<figure><img src="../../../.gitbook/assets/UE Change Viewport perspective (1).png" alt=""><figcaption><p>Change the Viewport angle in UE.</p></figcaption></figure>

### Add Calibration Points

* Select the Active Puck in the Viewport and click the <img src="../../../.gitbook/assets/Live Link Add Component button (3).png" alt="" data-size="line"> Add button on the Components tab.&#x20;
* Search for and select _Calibration Point_ from the list of options.&#x20;

<figure><img src="../../../.gitbook/assets/UE Add Calibration Point.png" alt=""><figcaption><p>Top down view of the Active Puck Static Mesh in Unreal Engine. </p></figcaption></figure>

* Click to rename the Calibration point. We recommend using names that match the point's location, such as top left, bottom right, etc.&#x20;
* Drag the newly created point to align it with the center of the corner marker.

<figure><img src="../../../.gitbook/assets/UE Place Calibration Pt 1.png" alt="" width="300"><figcaption><p>Adding a Calibration Point to the Active Puck Static Mesh in UE.</p></figcaption></figure>

* Use **Ctrl + D** to _Duplicate_ the point to make the next one.&#x20;
* Rename the second point and drag it to the appropriate location, aligning it with the previously placed point on either the X or Y axis.&#x20;
* Repeat these last two steps until each of the four corners has a Calibration Point at its center.
* Select the ActivePuck in the list of components. The four calibration points should be nested underneath.&#x20;
* Click the _Compile_ button on the main toolbar, then _Save_ and Close the tab for the Blueprint.

<figure><img src="../../../.gitbook/assets/UE Compile Components.png" alt="" width="323"><figcaption><p>Compile changes to the Static Mesh in UE.</p></figcaption></figure>

### Link the Static Mesh to the Live Link Asset

* In the project, click and drag the Blueprint created in the prior steps into the project.&#x20;
* In the Outliner pane, drag the Blueprint under _OptiTrackLiveLinkDisplay._
* &#x20;In the Transform Section of the Details pane, click the <img src="../../../.gitbook/assets/UE Reset values button.png" alt="" data-size="line"> button to the right of the Location settings to reset all location values to zero.&#x20;

<figure><img src="../../../.gitbook/assets/UE Puck Reset location Before 2.png" alt=""><figcaption></figcaption></figure>

* Click the <img src="../../../.gitbook/assets/Live Link Add Component button (4).png" alt="" data-size="line"> Add button in the Details pane. Search for and select _Live Link Controller_.&#x20;
* Under Subject Representation, click and select _ActivePuck_ from the list of available assets (below, left).
* This will link the static mesh to the puck. The Labeled Markers setting shows the device properly aligned (below, right).

{% hint style="info" %}
Use the translate tool to reorient the static mesh if the OptiTrack brand and the status lights on the mesh do not align with those on the physical puck.&#x20;
{% endhint %}

* Having confirmed the alignment is correct, you can turn off the [Labeled Marker](live-link-content-active-puck-static-meshes.md#create-labeled-markers) display. The Live Link display settings can also be closed.&#x20;
* The puck is now available as a tracked calibrator tool that can be used in conjunction with a lens file in Unreal Engine for lens calibration.

<div><figure><img src="../../../.gitbook/assets/UE Puck LL Add Subject.png" alt="" width="506"><figcaption><p>Select a Subject Representation for the <br><em>LiveLinkComponentController</em> in UE.</p></figcaption></figure> <figure><img src="../../../.gitbook/assets/UE Puck aligned with Mesh.png" alt="" width="404"><figcaption><p>A fully aligned Active Puck Static Mesh in UE.</p></figcaption></figure></div>

### Create a Lens File

* Right click in the  Content Browser in the folder where you'd like to save the lens file.
* Search for and select Lens File from the list of Content types and give the file an appropriate name, such as _35mm\_Lens_.&#x20;
* Open the Lens File.

<figure><img src="../../../.gitbook/assets/UE Lens File Add Lens Distortion.png" alt=""><figcaption><p>Lens File settings in Unreal Engine.</p></figcaption></figure>

* Click _Lens Distortion_ on the _Calibration Steps_ tab.
* In the _Lens Distortion Algo_ setting on the right, select _Lens Distortion Points Method_.&#x20;
* The _Calibrator_ setting will default to the calibrator puck.&#x20;
* Select the current calibrator point in the camera viewport to complete the alignment.
