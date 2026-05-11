---
description: A review of the functions available on the Builder pane.
---

# Builder Pane

## Overview

The Builder pane is accessed under the _View tab_ or by clicking the <img src="../.gitbook/assets/image (62).png" alt="" data-size="line"> icon on the main toolbar.

The **Builder pane** is used to create and edit trackable models, also called trackable assets:

* [**Rigid Body assets**](builder-pane.md#rigid-body-create) are created for tracking rigid objects.&#x20;
* [**Skeleton assets**](builder-pane.md#skeleton-create) are created for tracking human motions.&#x20;
* [**Trained Markerset assets**](../motive/trained-markersets.md) are used to track objects that are neither rigid nor human skeleton templates.&#x20;

When created, trackable models store the positions of markers on the target object and use the information to auto-label the markers in 3D space. During the auto-label process, a set of predefined labels are assigned to 3D points using the solver pipeline, and the labeled dataset is then used for calculating the position and orientation of the corresponding Rigid Bodies or Skeleton segments. Auto-labeling is not available for Trained Markersets.&#x20;

The trackable models can be used to auto-label the 3D capture both in Live mode (real-time) and in the Edit mode (post-processing). Each created trackable model will have its own properties which can be viewed and changed under the [Properties pane](properties-pane/). If new Skeletons or Rigid Bodies are created during post-processing, the _Take_ will need to be auto-labeled again in order to apply the changes to the 3D data.

![Marker labels shown on some of the markers on the Actor Skeleton.](<../.gitbook/assets/image (897).png>)

### Interface Overview

On the Builder pane, you can either create a new trackable asset or modify an existing one. Select the _Type_ of asset you wish to work on, and then select whether you wish to create or make modifications to existing assets. Create and Modify tools for different Asset types are explained in the sections below.

![Builder pane.](<../.gitbook/assets/image (276).png>)

### Post-Processing&#x20;

**Edit Mode** is used for playback of captured _Take_ files. In this mode, you can playback and stream recorded data and complete post-processing tasks, such as creating and modifying assets. The Cameras View displays the recorded 2D data while the 3D Viewport represents either recorded or real-time processed data as described below.

There are two modes for editing:

* **Edit:** Playback in standard Edit mode displays and streams the processed 3D data saved in the recorded _Take_. Changes made to settings and assets are not reflected in the Viewport until the _Take_ is [reprocessed](../motive/reconstruction-and-2d-mode.md#applying-changes-to-3d-data).&#x20;
* **Edit 2D:** Playback in Edit 2D mode performs a live reconstruction of the 3D data, immediately reflecting changes made to settings or assets. These changes are displayed in real-time but are not saved into the recording until the _Take_ is [reprocessed](../motive/reconstruction-and-2d-mode.md#applying-changes-to-3d-data) and saved. To playback in 2D mode, click the Edit button and select _Edit 2D_. &#x20;

<figure><img src="../.gitbook/assets/Live or Edit mode - switch to 2D (1).png" alt="" width="200"><figcaption><p>Click Edit to select the Edit mode.</p></figcaption></figure>

{% hint style="warning" %}
Regardless of the selected Edit mode, you must reprocess the _Take_ to create new 3D data based on the modifications made.&#x20;
{% endhint %}

Please see the [Data Editing ](../motive/data-editing.md)page for more information about editing _Takes_.&#x20;

{% hint style="info" %}
**Defining Assets in Edit mode:**

If the Rigid Bodies, or Skeletons, are created in Edit mode, the corresponding _Take_ needs to be [auto-labeled](../motive/labeling.md#auto-label). Only then will the Rigid Body markers be labeled using the Rigid Body asset and positions and orientations be computed for each frame. If the 3D data have not been labeled after edits on the recorded data, the asset may not be tracked.
{% endhint %}

## Rigid Body: Create

To create Rigid Bodies, select Rigid Body from the _Type_ option and click the _Create_ tab at the top. Here, you can create Rigid Body assets and track any markered-objects in the volume. In addition to standard Rigid Body assets, you can also create Rigid Body models for head-mounted displays (HMDs) and measurement probes as well

{% hint style="warning" %}
Tip: The recommended number of markers per Rigid Body is **4 \~ 12 markers**.&#x20;

You may encounter limits if using an excessive number of markers, or experience system performance issues when using the refine tool on such an asset. &#x20;
{% endhint %}

### Create a Rigid Body

* Select all associated Rigid Body markers in the [3D viewport](viewport.md#perspective-view).
* On the Builder pane, confirm that the selected markers match those on the object you want to define as the Rigid Body.&#x20;
* Click _Create_ to define a Rigid Body asset from the selected markers.

You can also create a Rigid Body using the following methods while the markers are selected:

* **Perspective View (3D viewport):** Right-click on the selected markers to access the context menu. Under the _Markers_ section, click _Create Rigid Body_.
* **Assets pane:** While the markers are selected in Motive, click on the add <img src="../.gitbook/assets/image (63).png" alt="" data-size="line"> button at the bottom of the [Assets pane](assets-pane.md).
* **Hotkey:** While the markers are selected, use the _Create Rigid Body_ hotkey (Default: Ctrl +T).

<div><img src="../.gitbook/assets/Create RB - Perspective view context menu.png" alt="Creating a Rigid Body from selected markers 
using the right-click context menu." width="265"> <img src="../.gitbook/assets/Rigid Body Bone - Unsolved (2).png" alt="Rigid body defined from the selected markers." width="263"></div>

Once the Rigid Body asset is created, the markers will be colored, labeled, and interconnected to each other. The newly created Rigid Body will be listed under the [Assets pane](assets-pane.md).

<figure><img src="../.gitbook/assets/Builder Pane - Create RB selected.png" alt="" width="563"><figcaption><p>Create a Rigid Body.</p></figcaption></figure>

### Create an HMD Rigid Body

#### Supported HMD Clips

Motive supports a variety of Head Mounted Display (HMD) clips, including VIVE Focus 3, Valve Index, and Varjo XR4, to name a few.&#x20;

To see all supported clips or to add a custom clip to your configuration, browse to this folder on the Motive PC:&#x20;

**C:\ProgramData\OptiTrack\Motive\HMD**

<figure><img src="../.gitbook/assets/HMD Configuration Files.png" alt="A screenshot of the Window c:\programdata\optitrack\motive\hmd, showing the various XML files saved with HMD configurations."><figcaption></figcaption></figure>

#### Create the HMD Rigid Body

For using OptiTrack system for VR applications, it is important that the pivot point of the HMD Rigid Body is placed at the appropriate location, at the root of the nose in between the eyes.&#x20;

When using the HMD clips, you can utilize the HMD creation tools in the Builder pane to have Motive estimate this spot and place the pivot point accordingly. Motive uses known marker configurations on the clip to precisely position the pivot point and set the desired orientation.

{% hint style="info" %}
HMDs with passive markers can utilize the [External Pivot Alignment](builder-pane.md) tool to calibrate the pivot point.
{% endhint %}

![Creating an HMD Rigid Body in the Builder pane.](<../.gitbook/assets/image (419) (1) (1) (1) (8).png>)

1. Make sure Motive is configured for tracking [active markers](../active-components/active-marker-tracking/#motive-settings).
2. Open the Builder pane under [View tab](toolbar-command-bar.md#view) and click _Rigid Bodies_.
3. Under the _Type_ drop-down menu, select HMD. This will bring up the options for defining an HMD Rigid Body.
4. If the selected marker matches one of the Active clips, it will indicate which type of Active Clip is being used.
5. Under the _Orientation_ drop-down menu, select the desired orientation of the HMD. The orientation used for streaming to Unity is +Z forward and Unreal Engine is +X forward, or you can also specify the expected orientation axis on the client plugin side.
6. Hold the HMD at the center of the tracking volume where all of the active markers are tracked well.
7. Select all **8** HMD active markers in the [3D viewport](viewport.md#perspective-view).
8. Click _Create_. An HMD Rigid Body will be created from the selected markers and it will initiate the calibration process.
9. During calibration, slowly rotate the HMD to collect data samples in different orientations.
10. Once all necessary samples are collected, the calibrated HMD Rigid Body will be created.

### Create a Measurement Probe Rigid Body

You can also define a measurement probe using the Builder pane. The measurement probe tool utilizes the precise tracking of OptiTrack mocap systems and allows you to measure 3D locations within a capture volume. _For more information, please read through the_ [_Measurement Probe Kit Guide_](../motive/measurement-probe-kit-guide.md)_._

![Calibrated probe in Motive.](<../.gitbook/assets/Builder Pane - Create Probe.png>)

#### **Creating a probe using the Builder pane**

1. Open the Builder pane under the [View tab](toolbar-command-bar.md#view) and click _Rigid Bodies_.
2. Bring the probe into the tracking volume and create a [Rigid Body](builder-pane.md#rigid-body-create) from the markers.
3. Under the _Type_ drop-down menu, select _Probe_. This will bring up the options for defining a Rigid Body for the measurement probe.
4. Select the Rigid Body created in step 2.
5. Place and fit the tip of the probe in one of the slots on the provided calibration block.
6. Note that there will be two steps in the calibration process: refining Rigid Body definition and calibration of the pivot point. Click the _Create_ button to initiate the probe refinement process.
7. Slowly move the probe in a circular pattern while keeping the tip fitted in the slot, making a cone shape overall. Gently rotate the probe to collect additional samples.
8. After the refinement, Motive will automatically proceed to the pivot point calibration.
9. Repeat the same movement to collect additional sample data for precisely calculating the location of the pivot or the probe tip.
10. When sufficient samples are collected, the pivot point will be positioned at the tip of the probe and the _Mean Tip Error_ will be displayed. If the probe calibration was unsuccessful, just repeat the calibration again from step 4.
11. Once the probe is calibrated successfully, a probe asset will be displayed over the Rigid Body in Motive, and live x/y/z position data will be displayed under the [Probe pane](probe-pane.md).

{% hint style="danger" %}
**Caution**

* The probe tip _MUST_ remain fitted securely in the slot on the calibration block during the calibration process.
* Do not press in with the probe since the deformation from compressing could affect the result.
{% endhint %}

{% hint style="info" %}
**Note: Custom Probes**

It's highly recommended to use the Probe kit when using this feature. With that being said, you can also use any markered object with a pivot arm to define a custom probe in Motive, but when a custom probe is used, it may have less accurate measurements; especially if the pivot arm and the object are not rigid and/or if any slight translation occurs during the probe calibration steps.
{% endhint %}

## Rigid Body: Modify

The Builder pane has tools to modify the tracking of a Rigid Body selected in Motive. To do so, select a single Rigid Body from the Viewport or Assets pane and click the _Modify_ tab to display the options for editing a Rigid Body.

<figure><img src="../.gitbook/assets/Builder Pane - Modify RB.png" alt=""><figcaption><p>Builder Modify pane - with a Rigid Body selected.</p></figcaption></figure>

### Refine

The Rigid Body refinement tool improves the accuracy of Rigid Body calculation in Motive. When a Rigid Body asset is initially created, Motive references only a single frame to define the Rigid Body. The Rigid Body refinement tool allows Motive to collect additional samples to achieve more accurate tracking results by improving the calculation of expected marker locations of the Rigid Body as well as the position and orientation of the Rigid Body itself.

<figure><img src="../.gitbook/assets/Builder Pane - Refine RB.png" alt=""><figcaption><p>Refine a Rigid Body from the Modify tab of the Builder pane.</p></figcaption></figure>

**Steps**

1. From the [View](toolbar-command-bar.md#view) menu, open the Builder pane, or click the <img src="../.gitbook/assets/Builder Pane button.png" alt="" data-size="line"> button on the toolbar.
2. Click on the Modify tab.
3. Select the Rigid Body to be refined in the Asset pane.&#x20;
4. To refine the asset in [Live mode](control-deck.md#live-and-edit-mode), hold the physical selected Rigid Body at the center of the capture volume so that as many cameras as possible can clearly capture the markers on the Rigid Body.
   1. In the **Refine** section of the Modify tab of the Builder pane, click _Start..._
   2. Slowly rotate the Rigid Body to collect samples at different orientations until the progress bar is full.
5. You can also refine the asset in Edit mode. Motive will automatically replay the current take file to complete the refinement process.&#x20;

<div><figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption><p>Rigid Body Refinement in Progress.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Refine RB - results.png" alt=""><figcaption><p>Rigid Body Refinement Results.</p></figcaption></figure></div>

### Probe Calibration

The _Probe Calibration_ feature under the Rigid Body edit options can be used to re-calibrate a pivot point of a measurement probe or a custom Rigid Body. This step is also completed as one of the calibration steps when first creating a measurement probe, but you can re-calibrate it under the _Modify tab_.

#### **Steps**

1. In Motive, select the Rigid Body or a measurement probe.
2. Bring out the probe into the tracking volume where all of its markers are well-tracked.
3. Place and fit the tip of the probe in one of the slots on the provided calibration block.
4. Click _Start._
5. Once it starts collecting the samples, slowly move the probe in a circular pattern while keeping the tip fitted in the slot, making a cone shape overall. Gently rotate the probe to collect additional samples.
6. When sufficient samples are collected, the mean error of the calibrated pivot point will be displayed.
7. Click _Apply_ to use the calibrated definition or click _Cancel_ to calibrate again.

### Location/Orientation

The _Modify_ tab is used to apply translation or rotation to the pivot point of a selected Rigid Body. A pivot point of a Rigid Body represents both position (x,y,z) and orientation (pitch, roll, yaw) of the corresponding asset.

{% hint style="info" %}
You can also use the [Gizmo tools](../motive/assets/gizmo-tool-translate-rotate-and-scale.md) to quickly modify the pivot point of a Rigid Body.
{% endhint %}

<div><figure><img src="../.gitbook/assets/Builder Pane - Modify RB - Location settings.png" alt=""><figcaption><p>Modify Rigid Body Location settings on the Builder pane. </p></figcaption></figure> <figure><img src="../.gitbook/assets/Builder Pane - Modify RB Orientation expanded.png" alt=""><figcaption><p>Modify Rigid Body Orientation settings on the Builder pane.</p></figcaption></figure></div>

#### **Location**

Use this tool to translate a pivot point in x/y/z axis (in mm). You can also reset the translation to set the pivot point back at the geometrical center of the Rigid Body.

#### **Orientation**

Use this tool to apply rotation to the local coordinate system of a selected Rigid Body. You can also reset the orientation to align the Rigid Body coordinate axis and the global axis. When resetting the orientation, the Rigid Body must be tracked in the scene.

### OptiTrack Clip Tool

The OptiTrack Clip Tool recalibrates an HMD with OptiTrack HMD Clips to position its pivot point at an appropriate location. The steps are the same as when first creating the [HMD Rigid Body](builder-pane.md#creating-hmd-rigid-body).

### Spherical Pivot Placement

This feature is useful when tracking a spherical object (e.g., a ball). It will assume that all of the markers on the selected Rigid Body are placed on a surface of a spherical object, and the pivot point will be calculated and re-positioned accordingly. Simply select a Rigid Body in Motive, open the Builder pane to edit Rigid Body definitions, and then click _Apply_ to place the pivot point at the center of the spherical object.

### Align To...

The Align To... section contains preset options for aligning the pivot point of a rigid body.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Modify RB Align To collapsed.png" alt=""><figcaption></figcaption></figure>

Click the <img src="../.gitbook/assets/Pane Items closed (1).png" alt="" data-size="line"> button to see the options available:

<figure><img src="../.gitbook/assets/Builder Pane - Modify RB Align to Options.png" alt=""><figcaption></figcaption></figure>

#### Align to Geometry

The Align to Geometry feature provides an option to align the pivot of a rigid body to a geometry offset. Motive includes several standard geometric objects that can be used, as well as the ability to import custom objects created in other applications. This allows for consistency between Motive and external rendering programs such as Unreal Engine and Unity.&#x20;

To use this feature, select the rigid body from the assets pane. In the Properties pane, click the <img src="../.gitbook/assets/Motive Context Menu (12).png" alt="" data-size="line"> button and select _Show Advanced_ if it is not already selected. &#x20;

Scroll to the _Visuals_ section of the asset's properties. Under _Geometry_, select the object type from the list.&#x20;

<figure><img src="../.gitbook/assets/Rigid Body Align to Geometry.png" alt=""><figcaption><p>Geometry Options for Assets.</p></figcaption></figure>

To import your own object, select _Custom Model_. This will open the _Attached Geometry_ field. Click on the file folder icon to select the .obj or .fbx file to import into Motive. &#x20;

<figure><img src="../.gitbook/assets/image (1494).png" alt=""><figcaption><p>Select custom Model. </p></figcaption></figure>

#### Align to Camera

To align an asset to a specific camera, select both the asset and the camera in the 3D Viewport. Click _Camera_ in the _Align to..._ field in the Modify tab.

#### Align to Rigid Body

To align an asset to an existing Rigid Body, you must be in 2D edit mode. Click the Edit button at the bottom left and select _EDIT 2D_ from the menu.&#x20;

<figure><img src="../.gitbook/assets/image (1511).png" alt=""><figcaption><p>Switch from 3D to 2D edit mode.</p></figcaption></figure>

The asset you wish to align must be unsolved. If necessary, right-click on the asset in the Assets pane and select _Remove Solve_ from the context menu.&#x20;

Once the asset is unsolved, select it in the 3D Viewport, then select the rigid body that you wish to align it to. Once both assets are selected, click _Rigid Body_ in the _Align To..._ field.&#x20;

#### Align to Marker

The Align to Marker feature sets the pivot point at the location of a specific marker. To use, select the asset from the Assets pane, select the marker you wish to align the pivot point with, then select _Align To...Marker_.&#x20;

{% hint style="warning" %}
Make sure only 1 marker is selected for proper alignment.&#x20;
{% endhint %}

To align the pivot point between a subset of markers, use the [Gizmo Tool](../motive/assets/gizmo-tool-translate-rotate-and-scale.md).&#x20;

#### Align to Origin

Stationary rigid bodies can be used to maintain a consistent global origin for a mocap volume. Once the pivot point of a rigid body is aligned to the origin, you can use that rigid body to set world origin each day. This option is also helpful if you do not have easy access to the floor.&#x20;

{% hint style="info" %}
Before using this feature, make sure the system has an exceptional calibration.&#x20;
{% endhint %}

Once you have the desired calibration, select the rigid bodies you wish to align then select _Align To...Origin_.&#x20;

#### Reset Pivot

The Reset Pivot feature returns the pivot point to the default location.&#x20;

### Asset Dropdown Menu

By default, the Modify tab of the Builder pane is locked to the asset selected in the 3D Viewport. To change the asset from the Builder pane instead, click the <img src="../.gitbook/assets/image (1496).png" alt="" data-size="line"> icon at the top of the Modify tab to unlock the drop-down list.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Modify RB Asset selection locked.png" alt=""><figcaption><p>Asset Selection dropdown in Builder Pane Modify tab.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Builder Pane - Modify RB unlock asset selection (1).png" alt=""><figcaption><p>Asset Selection dropdown - unlocked.</p></figcaption></figure>

{% hint style="warning" %}
To work with [Marker Constraints](builder-pane.md#marker-constraints) and/or [Marker Sticks](builder-pane.md#marker-sticks), you must select the items you wish to modify in the 3D viewport.&#x20;
{% endhint %}

## Skeleton: Create

{% hint style="info" %}
Skeleton tracking requires a _Motive:Body_ or _Motive:Body - Unlimited_ license.&#x20;
{% endhint %}

From the _Create_ tab, select the Skeleton option from the _Type_ dropdown menu. This allows you to select the [Skeleton Marker Set](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#placing-the-markers) to use, choose the calibration pose, and create the Skeleton model.

#### Select a Template

Select a [Skeleton Marker Set](../markersets/) template from the _Template_ drop-down menu. The Builder pane will display a Skeleton avatar that shows where to place the markers on the subject for the selected template.&#x20;

When the [6 Rigid Body Skeleton](../markersets/rigid-body-skeleton-markerset.md) template is selected, the display shows where to place the rigid bodies.&#x20;

Right-click and drag the mouse to rotate the model view to see other angles.

<figure><img src="../.gitbook/assets/Skeleton Joints.gif" alt="An animation of the Builder pane in Motive, with the Create Skeleton options displayed and the joint markers pulsing."><figcaption><p>Options to Create a Skeleton.</p></figcaption></figure>

#### **Place Markers on Actor**

Refer to the avatar and place the markers on the subject accordingly. For accurate placement, ask the subject to stand in the calibration pose while attaching the Skeleton markers. It is important to place markers at the right locations on the subject's body for the best Skeleton tracking. The markers on the avatar are color coded:&#x20;

* **Green markers** are placed on select joints, such as the elbows and knees, where precise placement is critical for proper skeleton calibration when using the full Range of Motion calibration method.&#x20;
* **White markers** are placed on the remaining joints, such as the shoulders and hips.  These markers should also be placed in the precise location shown.
* **Magenta markers** are segment markers that can be placed at a slightly different position within the segment to distinguish one skeleton from another.

#### **Confirm Marker Placement**

Double-check the marker counts and their placements. It may be easier to use the [3D viewport](viewport.md#perspective-view) in Motive to do this. The Builder pane will track the detected markers.

In the Builder pane, the _Create_ and _Create + Refine_ buttons become active once the number of _Markers Needed_ and _Markers Detected_ match,  If Skeleton markers are not automatically detected, manually select them from the [3D perspective view](viewport.md#perspective-view).

<figure><img src="../.gitbook/assets/Builder Pane and 3D Viewport - Skeleton Creation.png" alt="A screenshot of the Motive Builder pane, with the Skeleton Creation options displayed. To the right is the Motive 3D viewport, showing the markers for the undefined skeleton."><figcaption><p>Defining Skeleton from a Skelton Marker Set.</p></figcaption></figure>

#### Select Pose

Under the _Pose_ section drop-down menu, select the desired calibration pose for defining the Skeleton. This is set to the T-pose by default. Note that the image in the Builder pane remains in A-pose regardless of the selection.

{% hint style="info" %}
You have the option to calibrate the Skeleton with a full range of motion (ROM) during creation. See the [Create and Refine Skeleton](builder-pane.md#create-and-refine-skeleton) section, below, for more details.&#x20;
{% endhint %}

#### Select Constraints

The reconstructed 3D markers that comprise an asset are known as constraints in Motive. Skeleton templates include pre-defined labels that correspond to the marker's location and easily import into other pipelines for biomechanical analysis or animation. Set _Constraints_ to _Default_ to use these pre-defined labels.&#x20;

To import a custom XML file, select _Choose File..._ then browse to the file location. See the [Constraints XML Files](constraints-pane/constraints-xml-files.md) page for more information on using custom constraints.

Constraints can be relabeled using the[ Constraints pane](constraints-pane/) after the Skeleton is created.&#x20;

#### Select Model

Motive includes two spine models for skeletons:&#x20;

* The **Classic** model has two spine bones and one neck bone. This is the traditional model still used in many production workflows.&#x20;
* The **7 Segment Spine** model has five spine bones and two neck bones. This model accounts for the natural curves in the human spine and allows for better alignment between the Skeleton in Motive and the actor.&#x20;

<figure><img src="../.gitbook/assets/5 segment spine side view comparison to classic.png" alt="" width="488"><figcaption><p>The Classic Spine model (left) compared to the 5 Spine Segment model (right)</p></figcaption></figure>

The 7 Segment Spine is the default model. To change the default, to go [_Settings > Assets_](settings/settings-assets.md). On the _Assets tab_ under _Skeleton Creation_, change the Spine Type to the preferred default for your workflow.    &#x20;

#### Select Visual

Select how the Skeleton will display in the 3D perspective view.

* None: Displays only constraints and marker sticks.
* Segment: Displays Skeleton as individual Skeleton segments.
* Avatar (male): Displays Skeleton as a male avatar.
* Avatar (female): Displays Skeleton as a female avatar.
* Cycle Avatar: Motive assigns one of the two gendered avatars at random.

The visual can be changed after the skeleton is created in the [Skeleton properties](properties-pane/properties-pane-skeleton.md).&#x20;

#### Name the Skeleton

Assign a _Name_ to the skeleton. Motive will use this name as a prefix when creating skeleton marker labels. You can also assign custom labels during Skeleton creation by loading a previously prepared [Constraints XML](constraints-pane/constraints-xml-files.md) file, as noted above, or by [relabeling ](constraints-pane/#rename-constraints)the constraints from the [Constraints pane](constraints-pane/) after the Skeleton is created.&#x20;

#### **Create Skeleton**

Ask the subject to stand in the selected calibration pose. Standing in a proper calibration posture is important because the pose of the created Skeleton will be calibrated from it. For more details, read the [calibration pose](../motive/skeleton-tracking.md#calibration-pose) section of the [Skeleton Tracking](../motive/skeleton-tracking.md) page.

Click _Create_ to create the Skeleton without a full range of motion calibration. Once the Skeleton model has been defined, confirm all Skeleton segments and assigned markers are located at expected locations. If any of the Skeleton segments seem to be misaligned, delete and create the Skeleton again after adjusting the marker placements and the calibration pose.

{% hint style="info" %}
**In Edit Mode**

If you are creating a Skeleton in the post-processing of captured data, you will have to [auto-label](../motive/labeling.md#auto-label) the Take to see the Skeleton modeled and tracked in Motive.
{% endhint %}

#### **Create and Refine Skeleton - Range of Motion**

To calibrate the skeleton with a full range of motion during creation, click the _Create + Refine_ button.&#x20;

#### Range of Motion Take Files

By default, a Take with the name of the subject is recorded each time a Range of Motion calibration is completed in Live mode. This allows you to easily reprocess the skeleton if needed.&#x20;

To turn this setting off, go to _Settings > Assets._ On the _refinement_ ta&#x62;_,_ disable the _Record ROM_ settin&#x67;_._&#x20;

The Take is saved in the currently open data folder. If completing the ROM in edit mode, no additional recording is made.&#x20;

#### Range of Motion Settings

The _Assets_ tab of the _Settings_ panel has settings that pertain to skeleton creation.&#x20;

<figure><img src="../.gitbook/assets/image (1).png" alt="A screenshot of the Motive Settings Panel, Asset settings, Skeleton Creation options. "><figcaption></figcaption></figure>

The **Height Marker** setting ensures the solved skeleton matches the correct height for the actor.&#x20;

<div><figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM without Height Marker CROPPED.png" alt="An image of a tracked skeleton in Motive, where the head does not extend to the top marker. "><figcaption><p>Height Marker <br>NOT Enabled </p></figcaption></figure> <figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 3 near end of Collection CROPPED.png" alt="An image of a tracked skeleton in Motive, where the head properly extends to the top marker. "><figcaption><p>Height Marker<br>Enabled</p></figcaption></figure></div>

The _Assets_ tab of the _Settings_ panel includes a new **Refinement tab** with numerous advanced settings related to the Range of Motion, including the option to Solve Constraints Only, or to Use Constraint Weights. You can change these settings to more accurately calibrate the results to the subject when necessary.

<figure><img src="../.gitbook/assets/Settings - Assets Refinement tab Advanced Top.png" alt="A screenshot of the Motive Settings panel, Assets tab, with the top half of the Refinement subtab displayed."><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Settings - Assets Refinement tab Advanced Bottom.png.png" alt="A screenshot of the Motive Settings panel, Assets tab, with the bottom half of the Refinement subtab displayed."><figcaption></figcaption></figure>

#### How to Complete a Range of Motion Calibration

Watch this video for a demonstration of how to complete a full Range of Motion. The steps are detailed, below.

{% embed url="https://vimeo.com/1126271525/4b9455d21a?fe=ci&fl=cl&share=copy" %}

The Builder pane will display the ROM calibration settings. Have the subject stand in the middle of the volume in either a T-pose or an A-pose.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Prepare for Skeleton ROM.png" alt="A screenshot of the Motive builder pane with the Skeleton Range of Motion (or ROM) settings displayed. Below that are instructions to have the actor assume a calibration pose, then click start to begin."><figcaption></figcaption></figure>

To see a list of recommended poses for the calibration, click the <img src="../.gitbook/assets/Help button.png" alt="A screenshot of the Motive &#x22;Help&#x22; button." data-size="line"> help button:&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM HELP tips.png" alt="A screenshot of the Skeleton Range of Motion suggested poses list. "><figcaption></figcaption></figure>

When ready, click _Start_.

The Skeleton will appear in the 3D Viewport with the selected visual. Each bone segment will have a dark green hue at the beginning of sample collection.&#x20;

{% hint style="success" %}
_**Pro Tip:**_ You can assign a hotkey on the keyboard to the function "Create and Refine Skeleton" to create a skeleton and begin the Range of Motion calibration with a single keystroke. See [Settings: Mouse and Keyboard](settings/settings-mouse-and-keyboard.md) for instructions on assigning a hotkey.&#x20;
{% endhint %}

The builder pane shows the progress for each bone segment. This helps identify which body parts the subject needs to move for the best calibration.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 1 Start of Collection.png" alt="A screenshot of the Motive Builder pane and 3D Viewport, showing a skeleton at the beginning of Range of Motion data collection. "><figcaption></figcaption></figure>

You can see which segments have sufficient samples and which need more in the "Coverage" bar in the Builder pane. Additionally, the bone segment will turn bright green in the 3D Viewport.

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 2 midway thru Collection.png" alt="A screenshot of the Motive Builder pane and 3D Viewport, showing a skeleton in the middle of Range of Motion data collection. "><figcaption></figcaption></figure>

Note that the Start Calculation button appears early in the sample collection process. We recommend waiting until the coverage is complete for all bone segments before you begin calculating. However, if you are finding it difficult to achieve 100% coverage, and feel satisfied with the samples collected, you can click the _Start Calculation_ button at any time after it appears. &#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 3 near end of Collection.png" alt="A screenshot of the Motive Builder pane and 3D Viewport, showing a skeleton near the end of Range of Motion data collection. "><figcaption></figcaption></figure>

When Motive has collected sufficient samples for all bone segments, the Builder pane and the Skeleton will change from green to blue.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 4 Collection Done Calc in progress.png" alt="A screenshot of the Motive Builder pane and 3D Viewport, showing a skeleton at the completion of Range of Motion data collection, before the calculation is applied."><figcaption></figcaption></figure>

The updated color reflects the quality of the calibration for that bone segment:

<figure><img src="../.gitbook/assets/ROM Calibration Results Legend.png" alt="A screenshot of the legend for Skeleton Range of Motion calibration results. "><figcaption></figcaption></figure>

The calculation can take several minutes to run. When it completes, the results will display at the bottom of the Builder pane.

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 5 Calc Completed.png" alt="A screenshot of the Range of Motion calibration results for a newly created skeleton, showing an excellent calibration. "><figcaption></figcaption></figure>

If you are satisfied with the results, click _Apply_. Otherwise, click _Cancel_.&#x20;

{% hint style="info" %}
If you cancel the Range of Motion calculation instead of applying it, Motive will create the skeleton, calibrated to  the initial calibration pose. Use the Refine feature in the _Modify_ tab of the [Builder pane](builder-pane.md) to apply a new Range of Motion calibration to the existing skeleton.&#x20;
{% endhint %}

Once the ROM calibration is applied, the Builder pane will momentarily display "\[skeleton name] Created." The skeleton will appear in the 3D Viewport using the [visual](builder-pane.md#select-visual) selected during creation. &#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 6 Completed.png" alt="A screenshot of the Motive Builder pane and the 3D Viewport at the beginning of the skeleton creation and calibration phase, early in the sample collection. "><figcaption></figcaption></figure>

{% hint style="success" %}
The Refinement section of the Skeleton's Properties shows the date, time, quality, and constraint error of the Range of Motion applied to the skeleton.
{% endhint %}

<figure><img src="../.gitbook/assets/Properties Pane - Skeleton Refinement Not Done.png" alt="A screenshot of The Skeleton Refinement Properties,  prior to applying a Range of Motion calibration."><figcaption><p>The Skeleton Refinement Properties, <br>prior to applying a Range of Motion calibration.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Properties Pane - Skeleton Refinement Completed.png" alt="A screenshot of the Skeleton Refinement Properties,  After applying a Range of Motion calibration."><figcaption><p>The Skeleton Refinement Properties, <br>After applying a Range of Motion calibration.</p></figcaption></figure>

## Skeleton: Modify

<figure><img src="../.gitbook/assets/Builder Pane - Modify skeleton options.png" alt="A screenshot of the Motive Builder pane options to modify an existing skeleton. "><figcaption></figcaption></figure>

### Update From Selection

This function recalibrates existing Skeleton assets using the current Skeleton information. The update will be based on a single T-pose frame. To calibrate the skeleton using a full Range of Motion (ROM), use the [Refine ](builder-pane.md#refine-1)feature instead.&#x20;

To recalibrate a Skeleton, select all of the associated Skeleton markers from the perspective view. Make sure the selected Skeleton is in a calibration T-pose, and click the <img src="../.gitbook/assets/Pane Items closed.png" alt="" data-size="line"> button to see the available options.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Modify Skeleton from Selection expanded CROPPED.png" alt="A screenshot of the &#x22;Update from Selection&#x22; option in the Motive Builder pane, modify skeleton options. "><figcaption></figcaption></figure>

* **Bones and Constraints:** This option recalibrates the selected skeleton using the same Skeleton Marker Set and refreshes the constraint locations. This can also be done using the **Ctrl + R** hotkey.
* **Constraints Only:** This options recalibrates the selected skeleton's constraints based on the current location of the markers, without recalibrating bones.&#x20;

You can also update the skeleton from the context menu in the [Assets pane](assets-pane.md) or in the [3D Viewport](viewport.md#perspective-view).&#x20;

{% hint style="danger" %}
Skeleton recalibration does not work with Skeleton templates that include additional markers.
{% endhint %}

#### Refine

The Refine function allows you to apply a Range of Motion (ROM) calibration to a skeleton anytime after it's been created, including in post-production. See the section [Create and Refine Skeleton - Range of Motion](builder-pane.md#create-and-refine-skeleton-range-of-motion) for details on how to use to use this tool.&#x20;

Motive has the option to save a backup copy of the original skeleton for comparison purposes when completing a Live Range of Motion calibration on an existing skeleton asset. To turn this setting on, go to  _Settings > Assets_ and enable the setting _Save Unrefined Skeleton_ on the _Refinement_ tab.&#x20;

## Trained Markersets: Create

Users can create assets from any object that is not a Rigid Body or a pre-defined Skeleton using the Trained Markersets feature. This article will cover the basics of creating and modifying a Trained Markerset asset from the Builder pane. Please refer to the [Trained Markersets](../motive/trained-markersets.md) article for more information on using this feature.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Create Trained Markerset.png" alt="A screenshot of the Motive Builder pane and the 3D Viewport showing a trained markerset about to be created. "><figcaption><p>Create a Trained Markerset asset from the Build pane.</p></figcaption></figure>

#### Steps

1. Attach an adequate number of markers to your flexible object. This is highly dependent on the object but should cover at least the outline and any internal flex points. e.g., if it's a mat, the mat should have markers along the edges as well as dispersed markers in the middle in an asymmetrical pattern.
2. Record the movements you want of the object, trying to get as much of the full range of motion as possible.&#x20;
3. In Edit mode, select the markers attached to the object.&#x20;
4. From the _Create_ tab of the Builder pane, select _Markerset_ as the Type. Name the asset, then click _Create from Selection_.&#x20;

### Trained Markersets: Train and Modify

Once the asset is created, use the Training function so Motive can learn the object's full range of motion and how it moves through 3D space. Click _Train from Take_ then playback the .tak file created in step 2 of the asset creation. Use the _Clear_ button to remove the asset's existing training.

<figure><img src="../.gitbook/assets/Screenshot 2023-09-14 183317 (1).png" alt=""><figcaption><p>Builder Pane Modify Options for Trained Markersets.</p></figcaption></figure>

### Bones

In Motive, a Bone is a virtual structure that connects two joints and represents a segment of a virtual skeleton or Trained Markerset. To access these functions, select either the entire asset (to use the auto-generate option), or select the specific markers or bones that you would like to modify in the 3D Viewport.&#x20;

<figure><img src="../.gitbook/assets/image (1498).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="100">Button</th><th>Function</th></tr></thead><tbody><tr><td><img src="../.gitbook/assets/image (1499).png" alt="" data-size="line"></td><td>Auto-generates bones at flex points for the selected asset.</td></tr><tr><td><img src="../.gitbook/assets/image (1500).png" alt="" data-size="line"></td><td>Adds (+) or Removes (-) the selected bone(s).</td></tr><tr><td><img src="../.gitbook/assets/image (1501).png" alt="" data-size="line"></td><td>Adds a bone chain between two selected bones. Whichever bone is selected first becomes the parent bone, the second becomes the child bone.</td></tr><tr><td><img src="../.gitbook/assets/image (1502).png" alt="" data-size="line"></td><td>Unparents the selected bone or bones. This removes the bone chain between the bones.</td></tr><tr><td><img src="../.gitbook/assets/image (1503).png" alt="" data-size="line"></td><td>Reroots the selected child bone and makes it the parent in the bone chain. </td></tr></tbody></table>

### Marker Constraints

<figure><img src="../.gitbook/assets/Screenshot 2023-09-14 154223.png" alt=""><figcaption></figcaption></figure>

You can add or remove marker constraints (referred to as [asset model markers](../motive/data-recording/#marker-types-in-motive) in version 3.0 and earlier) from an asset using the Builder pane.&#x20;

#### **Steps**

1. From the Viewport visual options, enable selection of Marker Constraints.
2. Access the Modify tab on the Builder pane.
3. Select the asset whose marker constraints you wish to modify.
4. in the 3D Viewport, CTRL + left-click on a marker constraint that's associated with the selected asset. Click the <img src="../.gitbook/assets/Add button.png" alt="" data-size="line"> button to add the marker constraint to the asset definition. To remove it, click the <img src="../.gitbook/assets/image (60).png" alt="" data-size="line"> button.
5. On the Marker Constraints section of the Builder pane, click + to add the marker to the definition or - to remove the marker.
6. Use the Constraints pane to modify marker label and/or colors.

### Marker Sticks

<figure><img src="../.gitbook/assets/Builder Pane Marker Sticks.png" alt=""><figcaption></figcaption></figure>

Motive includes the ability to modify Marker Sticks for all asset types, directly from the Builder pane. Select two or more of the asset's markers in the 3D Viewport to activate this tool set.&#x20;

<table><thead><tr><th width="100" align="center">Button</th><th>Function</th></tr></thead><tbody><tr><td align="center"><img src="../.gitbook/assets/Screenshot 2023-09-14 163616 (1).png" alt="" data-size="line"></td><td>Changes the color of the selected Marker Stick(s).</td></tr><tr><td align="center"><img src="../.gitbook/assets/Screenshot 2023-09-14 163633.png" alt="" data-size="line"></td><td>Autogenerates Marker Sticks for the selected Trained Markerset asset. </td></tr><tr><td align="center"><img src="../.gitbook/assets/Screenshot 2023-09-14 163124.png" alt="" data-size="line"></td><td>Connects all of the selected Markers to each other.</td></tr><tr><td align="center"><img src="../.gitbook/assets/Screenshot 2023-09-14 163644.png" alt="" data-size="line"></td><td>Creates Marker Sticks based on the order in which the markers were selected.</td></tr><tr><td align="center"><img src="../.gitbook/assets/Screenshot 2023-09-14 154836.png" alt="" data-size="line"></td><td>Removes the selected Marker Stick(s).</td></tr></tbody></table>



