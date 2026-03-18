# Skeleton Tracking

In Motive, Skeleton assets are used for tracking human motions. These assets auto-label specific sets of markers attached to human subjects, or actors, and create skeletal models. Unlike Rigid Body assets, Skeleton assets require additional calculations to correctly identify and label 3D reconstructed markers on multiple semi-Rigid Body segments. In order to accomplish this, Motive uses pre-defined Skeleton Marker Set templates, which is a collection of marker labels and their specific positions on a subject. According to the selected Marker Set, retroreflective markers must be placed on pre-designated locations of the body. This page details instructions on how to create and use Skeleton assets in Motive.

{% hint style="info" %}
**Note**:

* **Motive license:** Skeleton features are supported only in Motive:Body or Motive:Body - Unlimited.
* **Skeleton Count:** Standard Motive:Body license supports up to 3 Skeletons. For tracking higher number of Skeletons, activate with Motive: Body - Unlimitted license.
* **Height requirement:** For Skeleton tracking, the subject must be between 1'7" \~ 9' 10" tall.
* Use the default _create_ layout to open related panels that are necessary for Skeleton creation. (CTRL + 2).
{% endhint %}

## Skeleton Marker Placement

When it comes to tracking human movements, a proper marker placement becomes especially important. Motive utilizes pre-programmed Skeleton Marker Sets, and each marker is used to indicate anatomical landmarks when modeling the Skeleton. Thus, all of the markers must be placed at their appropriate locations. If any of markers are misplaced, the Skeleton asset may not be created, and even if it is created, bad marker placements may lead to [labeling](labeling.md) problems. Thus, taking extra care in placing the markers on intended locations is very important and can save time in post-processing of the data.

Attaching markers directly onto a person’s skin can be difficult because of hair, oil, and moisture from sweat. Plus, dynamic human motions tend to move the markers during capture, so use appropriate skin adhesives for securing marker bases onto the skin. Alternatively, mocap suits allow velcro marker bases to be used.

### Select a Marker Set

Open [Builder pane](../motive-ui-panes/builder-pane.md) and go to the Skeleton creation feature. Select the Marker Set you desire to use from the drop-down menu. A total number of required markers for each Skeleton is indicated in the parenthesis after each Marker Set name, and corresponding marker locations are displayed over an avatar displayed in the [Builder pane](../motive-ui-panes/builder-pane.md). Instruct the subject to strike a calibration pose (T-pose or A-pose) and carefully follow the figure and place retroreflective markers at corresponding locations of the actor or the subject.

![The marker arrangement displayed over an avatar in the Builder pane, Skeleton creation options.](<../.gitbook/assets/image (397).png>)

![Markers placed accordingly.](<../.gitbook/assets/image (435).png>) ![Placing a joint marker on the elbow joint axis.](<../.gitbook/assets/image (449).png>)

### Placing the Markers

All markers need to be placed at respective **anatomical** locations of a selected Skeleton as shown in the [Builder pane](../motive-ui-panes/builder-pane.md). Skeleton markers can be divided into two categories: markers that are placed along joint axes (joint markers) and markers that are placed on body segments (segment markers).

**Joint Markers**

Joint markers need to be placed carefully along corresponding joint axes. Proper placements will minimize marker movements during a range of motions and will give better tracking results. To accomplish this, ask the subject to flex and extend the joint (e.g. knee) a few times and palpate the joint to locate the corresponding axis. Once the axis is located, attach the markers along the axis where skin movement is minimal during a range of motion.

#### **Segment Markers**

Segment markers are markers that are placed on Skeleton body segments, but not around a joint. For best tracking results, each segment marker placement must be incongruent to an associated segment on the opposite side of the Skeleton (e.g., left thigh and right thigh). Also, segment markers must be placed asymmetrically within each segment for the best tracking results. This helps the Skeleton solve to thoroughly distinguish, left-side and right-side of the corresponding Skeleton segments throughout the capture. This asymmetrical placement is also emphasized in the avatars shown in the Builder pane. Segment markers that can be slightly moved to different places on the same segment are highlighted on the 3D avatar in the Skeleton creation window on the [Builder pane](../motive-ui-panes/builder-pane.md).

![](<../.gitbook/assets/image (438).png>)

#### **Additional Placement Tips**

* Wipe off any moisture or oil on the skin before attaching the marker.
* Avoid wearing clothing or shoes with reflective materials since they can introduce extraneous reflections.
* Tie back hair which can occlude the markers around the neck.
* Remove reflective jewelry.
* Place markers in an asymmetrical arrangement by offsetting the related segment markers (markers that are not on joints) at slightly different height.
* See also: [Baseline Marker Set Placements](../markersets/full-body/baseline-41.md)

### Biomechanics Marker Sets

When using the biomechanics Marker Sets, markers must be placed precisely with extra care because these placements directly relate to coordinate system definition of each respective segment, affecting the resulting biomechanical analysis. The markers need to be placed on the skin for direct representation of the subject’s movement. Mocap suits are not suitable for biomechanic applications. While the basic marker placement must follow the avatar in the Builder pane, additional details on the accurate placements can be found on the following page: [Biomechanics Marker Sets](../movement-sciences/movement-sciences-markersets/biomechanics-markersets.md).

{% hint style="info" %}
**Additional Tips**

* All markers need to be placed at the respective anatomical landmarks.
* Place markers where you can palpate the bone or where there is less soft tissue in between. These spots have fewer skin movements and provide secure marker attachment.
* Joint markers are vulnerable to skin movements because of the range of motion in the flexion and extension cycle. In order to minimize the influence, a thorough understanding of the biomechanical model used in the post-processing is necessary. In certain circumstances, the joint line may not be the most appropriate location. Instead, placing the markers slightly superior to the joint line could minimize the soft tissue artifact, still taking care to maintain parallelism with the anatomical joint line.
* Use appropriate adhesives to place markers and make sure they are securely attached.
{% endhint %}

## Creating Skeletons

### Skeleton Creation Steps

![Defining Skeleton from a Skeleton Marker Set.](<../.gitbook/assets/image (458).png>)

**Step 1.**

From the Skeleton creation options on the [Builder pane](../motive-ui-panes/builder-pane.md), select a Skeleton Marker Set template from the _Template_ drop-down menu. This will bring up a Skeleton avatar displaying where the markers need to be placed on the subject.

**Step 2.**

Refer to the avatar and place the markers on the subject accordingly. For accurate placements, ask the subject to stand in the calibration pose while placing the markers. It is important that these markers get placed at the right spots on the subject's body for the best Skeleton tracking. Thus, extra attention is needed when placing the [Skeleton markers](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#Skeleton-marker-placement).

{% hint style="info" %}
The magenta markers indicate the [segment markers](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#placing-the-markers) that can be placed at a slightly different position within the same segment.
{% endhint %}

**Step 3.**

Double-check the marker counts and their placements. It may be easier to use the [3D viewport](../motive-ui-panes/viewport.md#perspective-view) in Motive to do this. The system should be tracking the attached markers at this point.

**Step 4.**

In the Builder pane, make sure the numbers under the _Markers Needed_ and _Markers Detected_ sections are matching. If the Skeleton markers are not automatically detected, manually select the Skeleton markers from the [3D perspective view](../motive-ui-panes/viewport.md#perspective-view).

**Step 5.**

Select a desired set of marker labels under the _Labels_ section. Here, you can just use the _Default_ labels to assign labels that are defined by the Marker Set template. Or, you can also assign custom labels by loading previously prepared [marker-name XML](../motive-ui-panes/constraints-pane/constraints-xml-files.md) files in the label section.

**Step 6.**

Next step is to select the Skeleton creation pose settings. Under the _Pose_ section drop-down menu, select the desired calibration post you want to use for defining the Skeleton. This is set to the T-pose by default.

**Step 7.**

Ask the subject to stand in the selected calibration pose. Here, standing in a proper calibration posture is important because the pose of the created Skeleton will be calibrated from it. For more details, read the [calibration poses](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#calibration-pose) section.

**Step 8.**

Click Create to create the Skeleton. Once the Skeleton model has been defined, confirm all Skeleton segments and assigned markers are located at expected locations. If any of the Skeleton segment seems to be misaligned, delete and create the Skeleton again after adjusting the marker placements and the calibration pose.

{% hint style="info" %}
**In Edit Mode**

If you are creating a Skeleton in the post-processing of captured data, you will have to [auto-label](labeling.md#auto-label) the Take to see the Skeleton modeled and tracked in Motive.
{% endhint %}

{% hint style="info" %}
**Reset Skeleton Tracking**

When Skeleton tracking is not acquired successfully during the capture for some reason, you can use the CTRL + R hotkey to trigger the solver to re-boot the Skeleton asset.
{% endhint %}

### Skeleton Properties

By configuring [Skeleton Properties](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive-ui-panes/properties-pane/properties-pane-Skeleton.md), you can modify the display settings as well as Skeleton creation pose settings for Skeleton assets. For newly created Skeletons, default Skeleton creation properties are configured under the [Application Settings](../motive-ui-panes/settings/) pane. Properties of existing, or recorded, Skeleton assets are configured under the [Properties pane](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive-ui-panes/properties-pane/properties-pane-Skeleton.md) while the respective Skeletons are selected in Motive.

![Example of the Visual property set to Segment under Skeleton properties.](<../.gitbook/assets/image (403).png>) ![Properties of the selected Skeleton is listed the Properties pane.](<../.gitbook/assets/image (615).png>)

### Calibration Pose

A proper calibration posture is necessary because the pose of the created Skeleton will be calibrated from it. Read through the following explanations on proper T-poses and A-poses.

**T pose**

The T-pose is commonly used as the reference pose in 3D animation to bind two characters or assets together. Motive uses this pose when creating Skeletons. A proper T-pose requires straight posture with back straight and head looking directly forward. Both arms are stretched to each side, forming a “T” shape. Both arms and legs must be straight, and both feet need to be aligned parallel to each other.

![Front view of the T-pose.](<../.gitbook/assets/image (569).png>) ![Back view of the T-pose.](<../.gitbook/assets/image (423).png>)

**A pose**

The A-pose is another type of calibration pose that is used to create Skeletons. Set the Skeleton Create Pose setting to the A-pose you wish to calibrate with. This pose is especially beneficial for subjects who have restrictions in lifting the arm. Unlike the T-pose, arms are abducted at approximately 40 degrees from the midline of the body, creating an A-shape. There are three different types of A-pose: Palms down, palms forward, and elbows bent. [↑](https://v30.wiki.optitrack.com/index.php?title=Skeleton_Tracking#top)

* **Palms Down:** Arms straight. Abducted, sideways, arms approximately 40 degrees, palms facing downwards.
* **Palms forward:** Arms straight. Abducted, sideways, arms approximately 40 degrees, palms facing forward. Be careful not to over rotate the arm.
* **Elbows Bent:** Similar to all other A-poses. arms approximately 40 degrees, bend elbows so that forearms point towards the front. Palms facing downwards, both forearms aligned.

![Front view of the A-pose.](<../.gitbook/assets/image (452).png>) ![Back view of the A-pose.](<../.gitbook/assets/image (406).png>)

### Calibration Markers

{% hint style="info" %}
Calibration markers exists only in the biomechanics Marker Sets.
{% endhint %}

Many Skeleton Marker Sets do not have medial markers because they can easily collide with other body parts or interfere with the range of motion, all of which increase the chance of marker occlusions.

However, medial markers are beneficial for precisely locating joint axes by associating two markers on the medial and lateral side of a joint. For this reason, some biomechanics Marker Sets use medial markers as _calibration markers_. Calibration markers are used only when creating Skeletons but removed afterward for the actual capture. These calibration markers are highlighted in red from the 3D view when a Skeleton is first created.

After creating a Skeleton from the [Builder pane](../motive-ui-panes/builder-pane.md), calibration markers need to be removed. First, detach the calibration markers from the subject. Then, in Motive, right-click on the Skeleton in the perspective view to access the context menu and click _Skeleton → Remove Calibration Markers_. Check the [assigned marker positions](data-recording/) to make sure that the Skeleton no longer expects markers in the corresponding medial positions.

![A Skeleton asset with calibration markers.](<../.gitbook/assets/image (457).png>) ![Calibration markers removed.](<../.gitbook/assets/image (487).png>)

### Recalibrating Skeleton

Existing Skeleton assets can be recalibrated using the existing Skeleton information. Basically, the recalibration recreates the selected Skeleton using the same Skeleton Marker Set. This feature recalibrates the Skeleton asset and refreshes expected marker locations on the assets.

To recalibrate Skeletons, select all of the associated Skeleton markers from the perspective view and click _Recalibrate From Markers_ which can be found in the Skeleton context menu from either the [Assets pane](../motive-ui-panes/assets-pane.md) or the [Perspective View pane](../motive-ui-panes/viewport.md#perspective-view). When using this feature, select a Skeleton and the markers that are related to the corresponding asset.

{% hint style="danger" %}
Skeleton recalibration does not work with Skeleton templates with added markers.
{% endhint %}

![Recalibrate from selected marker in the Assets pane.](<../.gitbook/assets/image (430).png>) ![Recalibrate from selected marker in the Perspective View pane.](<../.gitbook/assets/image (635).png>)

## Marker Colors and Marker Sticks

Skeleton marker colors and marker sticks can be viewed in the [perspective view](../motive-ui-panes/viewport.md#perspective-view) pane. They provide color schemes for clearer identification of Skeleton segments and individual marker labels from the perspective viewport. To make them visible, enable the Marker Sticks and Marker Colors under the visual aids <img src="../.gitbook/assets/Motive Visual Options button.png" alt="" data-size="line"> in the [perspective view](../motive-ui-panes/viewport.md#perspective-view) pane. A default color scheme is assigned when creating a Skeleton asset. To modify marker colors and labels, you can use the [Constraints pane](../motive-ui-panes/constraints-pane/).

Constraints store information on marker labels, colors, and marker sticks which can be modified, exported and re-imported as needed. For more information on doing this, please refer to the [Constraints XML Files](../motive-ui-panes/constraints-pane/constraints-xml-files.md) page.

![(Left) Marker colors enabled in the perspective view. (Right) Both marker sticks and marker colors enabled in the perspective view.](<../.gitbook/assets/image (415).png>) ![Generating constraints will update the Skeleton markers with the default constraints template.](<../.gitbook/assets/image (466).png>)

## Adding/Removing Skeleton Markers

![Related markers for a Skeleton segment indicated when Marker Lines advanced Skeleton property is enabled.](<../.gitbook/assets/image (455).png>)

Skeleton Marker Sets can be modified slightly by adding or removing markers to or from the template. Follow the below steps for adding/removing markers. Note that modifying, especially removing, Skeleton markers is not recommended since changes to default templates may negatively affect the Skeleton tracking when done incorrectly. Removing too many markers may result in poor Skeleton reconstructions while adding too many markers may lead to labeling swaps. If any modification is necessary, try to keep the changes minimal.

{% hint style="info" %}
When adding, or removing, markers in the Edit mode, the Take needs to be [auto-labeled](labeling.md#auto-label) again to re-label the Skeleton markers.
{% endhint %}

### Steps

You can add or remove Marker Constraints from a Rigid Body or a Skeleton using the Builder pane. This is basically adding or removing markers to the existing Rigid Body and/or Skeleton definition. Follow the below steps to add or remove markers:

**To Add**

1. Access the Modify tab on the [Builder pane](../motive-ui-panes/builder-pane.md).
2. Select a Skeleton segment that you wish to add extra markers onto.
3. Then, CTRL + left-click on the marker that you wish to add to the template.
4. On the Marker Constraints tool in the Builder pane, click + to add and associate the selected marker to the selected segment.
5. Reconstruct and Auto-label the Take.
6. When you add extra markers to Skeletons, the markers will be labeled as _Skeleton\_CustomMarker#_. You can use the [Constraints pane](../motive-ui-panes/constraints-pane/) to change the label as needed.

**To Remove**

1. Enable selection of Marker Constraints from the visual aids option in [perspective view](../motive-ui-panes/viewport.md#perspective-view).
2. \[Optional] Under the advanced properties of the target Skeleton, enable Marker Lines property to view which markers are associated with different Skeleton bones.
3. Access the Modify tab on the [Builder pane](../motive-ui-panes/builder-pane.md).
4. Select the Skeleton segment that you wish to modify and select the associated Marker Constraints that you wish to dissociate.
5. Delete the association by clicking on the "-" in the Constraints pane while a marker is selected in the Constraints pane.
6. Reconstruct and Auto-label the Take.

![Adding an extra chest marker to a Skeleton. Click image to enlarge.](<../.gitbook/assets/image (476).png>) ![Changing the name of newly added marker from the Constraints pane.](<../.gitbook/assets/image (486).png>)

## Export Assets&#x20;

Assets can be exported into the Motive user profile (.MOTIVE) file if it needs to be re-imported. The [user profile](motive-basics.md#motive-user-profile-.motive) is a text-readable file that contains various configuration settings in Motive, including the asset definitions.

When asset definitions are exported to a MOTIVE user profile, the profile stores marker arrangements calibrated in each asset, and they can be imported into different takes without creating a new asset in Motive. Note that these files specifically store the spatial relationship of each marker, and therefore, only the identical marker arrangements will be recognized and defined with the imported asset.

To export the assets, go to _Files_ tab → _Export Assets_ to export all of the assets in the Live-mode or in the current TAK file. You can also use the _File menu_ → _Export Profile_ to export other software settings including the assets.

![Exporting Assets into the User Profile.](<../.gitbook/assets/image (140) (1) (1) (1) (1) (1) (1) (1).png>) ![Exporting user profile that includes assets. This dialogue window is from the Export Profile As... option.](<../.gitbook/assets/image (124) (1) (1) (1) (1) (1) (1) (5).png>)

![Exporting from Assets pane.](<../.gitbook/assets/image (471).png>)

## Relative Skeleton Joint Angles

There are two ways of obtaining Skeleton joint angles. Rough representations of joint angles can be obtained directly from Motive, but the most accurate representations of joint angles can be obtained by pipelining the tracking data into a third-party biomechanics analysis and visualization software (e.g. [Visual3D](https://www.c-motion.com/) or [The MotionMonitor](http://www.innsport.com/)).

For biomechanics applications, joint angles must be computed accurately using the respective Skeleton model solve, which can be accomplished by using biomechanical analysis software. [Export C3D files](data-export/data-export-c3d.md) or stream tracking data from Motive and import into an analysis software for further calculation. From the analysis, various biomechanics metrics, including the joint angles can be obtained.

**Joint angles generated and exported from Motive are intended for basic visualization purposes only and should not be used for any type of biomechanical or clinical analysis.** A rough representation of joint angles can be obtained by either exporting or streaming the Skeleton Rigid Body tracking data. When exporting the tracking data into CSV, set the [Use World Coordinates](data-export/data-export-csv.md) export setting to _Local_ to obtain bone segment position and orientation values in respect to its parental segment, roughly representing the joint angles by comparing two hierarchical coordinate systems. When streaming the data, set [Local Rigid Bodies](data-streaming.md) to true in the streaming settings to get relative joint angles.

## Constraints XML: Customize Marker Labels, Colors, and Sticks

Each Skeleton asset has its marker templates stored in an XML file. By exporting, customizing, and importing the constraint XML files, a Skeleton Marker Set can be modified. Specifically, customizing the XML files will allow you to modify Skeleton marker labels, marker colors, and marker sticks within a Skeleton asset. For detailed instructions on modifying Skeleton XML files, read through [Constraints XML Files](../motive-ui-panes/constraints-pane/constraints-xml-files.md) page.

**To export Skeleton constraints XML file**

To export a Skeleton XML file, right-click on a Skeleton asset under the Assets pane and use the [Export Constraints](../motive-ui-panes/assets-pane.md#for-Skeleton-assets) feature to export corresponding Skeleton marker XML file.

**To import Skeleton constraints XML file**

You can import marker XML file under the _Labels_ section of the [Builder pane](../motive-ui-panes/builder-pane.md) when first creating a new Skeleton. To import a constraints XML file on an existing Skeleton, right-click on a Skeleton asset under the Assets pane and click _Import Constraints_.
