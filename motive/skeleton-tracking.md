---
description: Detailed instructions for creating and using Skeleton assets in Motive.
---

# Skeleton Tracking

In Motive, Skeleton assets are used for tracking human motions. These assets auto-label specific sets of markers attached to human subjects, or actors, and create skeletal models.&#x20;

Unlike Rigid Body assets, Skeleton assets require additional calculations to correctly identify and label 3D reconstructed markers on multiple semi-Rigid Body segments. To accomplish this, Motive uses pre-defined Skeleton Marker Set templates that define a collection of marker labels and their specific positions on a subject.&#x20;

{% hint style="info" %}
**Notes**:

* **Motive license:**  Skeleton features are supported only in _Motive:Body_ or _Motive:Body - Unlimited_.
* **Skeleton Count:**  The standard _Motive:Body_ license supports up to 3 Skeletons. To track more Skeletons, a _Motive:Body - Unlimited_ license is required.
* **Height range:**  Skeleton actors must be between 1'7" and 9' 10" tall.
* Use the default _create_ layout to open related panels that are necessary for Skeleton creation. (CTRL + 2).
{% endhint %}

## Skeleton Marker Placement

When it comes to tracking human movements, proper marker placement is especially important. In Motive's pre-programmed Skeleton Marker Sets, each marker indicates an anatomical landmark, such as left elbow out, right hip, etc., when modeling the Skeleton. If markers are misplaced, the Skeleton asset may not be created, or bad marker placements may result in [labeling](labeling.md) problems, creating extra work in post-processing of the data.

Attaching markers directly to a person’s skin can be difficult due to hair, oil, and moisture from sweat. For this reason, we recommend mocap suits that allow Velcro marker bases. In instances where markers must be attached directly, make sure to use appropriate skin adhesives to secure the marker bases as dynamic human motions tend to move the markers during capture.

### Select a Marker Set

* Open the Create tab on the [Builder pane](../motive-ui-panes/builder-pane.md).&#x20;
* From the _Type_ drop-down list, select Skeleton.
* &#x20;Select a Marker Set to use from the drop-down menu. The number of required markers for each Skeleton is shown in parenthesis after the Marker Set name.&#x20;
* When a Marker Set is selected, the corresponding marker locations are displayed over an avatar in the [Builder pane](../motive-ui-panes/builder-pane.md). Right-drag to rotate the avatar to see the location of all the markers.

<figure><img src="../.gitbook/assets/Skeleton Joints (1).gif" alt="A gif of the Motive  Builder Pane set to Skeleton creation, with the markers displayed on the avatar and the skeleton settings below. "><figcaption><p>The marker arrangement displayed over an avatar <br>in the Builder pane, Skeleton creation options.</p></figcaption></figure>

### Placing the Markers

All markers need to be placed at respective **anatomical** locations of a selected Skeleton as shown in the [Builder pane](../motive-ui-panes/builder-pane.md). Skeleton markers can be divided into two categories: markers that are placed along joint axes (joint markers) and markers that are placed on body segments (segment markers).

Refer to the avatar and place the markers on the subject accordingly. For accurate placement, ask the subject to stand in the calibration pose while attaching the markers. It is important to place markers at the right locations on the subject's body for the best Skeleton tracking.&#x20;

The markers on the avatar are color coded as follows:&#x20;

* **Green markers** are placed on select joints, such as the elbows and knees, where precise placement is critical for proper skeleton calibration when using the full Range of Motion calibration method.&#x20;
* **White markers** are placed on the remaining joints, such as the shoulders and hips.  These markers should also be placed in the precise location shown.&#x20;
* **Magenta markers** are segment markers that can be placed at a slightly different position within the segment to distinguish one skeleton from another.

<div><figure><img src="../.gitbook/assets/image (663).png" alt="Photo of an actor in a MoCap suit with markers placed, standing in a T-Pose."><figcaption><p>Markers placed accordingly.</p></figcaption></figure> <figure><img src="../.gitbook/assets/image (952).png" alt="A photo of a person applying a marker directly to the skin on an elbow joint."><figcaption><p>Placing a joint marker on the elbow joint axis.</p></figcaption></figure></div>

#### **Joint Markers**

Joint markers need to be placed carefully along corresponding joint axes. Proper placements will minimize marker movements during a range of motions and will give better tracking results. To accomplish this, ask the subject to flex and extend the joint (e.g., knee) a few times and palpate the joint to locate the corresponding axis. Once the axis is located, attach the markers along the axis where skin movement is minimal during a range of motion.

{% hint style="success" %}
Proper placement of Joint Markers improves auto-labeling and reduces post-production processing time.
{% endhint %}

#### **Segment Markers**

Segment markers are placed on Skeleton body segments, but not around a joint. For best tracking results, place segment markers asymmetrically within each segment. This helps the Skeleton solve to thoroughly distinguish left from right for the corresponding Skeleton segments throughout the capture. This asymmetrical placement is also emphasized in the avatars shown in the Builder pane.&#x20;

<figure><img src="../.gitbook/assets/image (862).png" alt="A screenshot from Motive showing the segment markers on the upper thigh of the Skeleton Avatar from the Builder pane, showing the 2 segment markers placed in different locations."><figcaption></figcaption></figure>

#### **Additional Placement Tips**

* If attaching markers directly to skin, wipe off any moisture or oil before attaching the marker.
* Avoid wearing clothing or shoes with reflective materials that can introduce extraneous reflections.
* Tie up hair, which can occlude markers around the neck.
* Remove reflective jewelry.
* Place markers in an asymmetrical arrangement by offsetting the related segment markers (markers that are not on joints) at slightly different height.
* In the Builder pane, the number of _Markers Needed_ and _Markers Detected_ must match. If the Skeleton markers are not automatically detected, manually select the Skeleton markers from the [3D perspective view](../motive-ui-panes/viewport.md#perspective-view).
* Find detailed descriptions of each template in the section [Skeleton Marker Sets](../markersets/).

### Biomechanics Marker Sets

* [Biomechanics Marker Sets](../movement-sciences/movement-sciences-markersets/biomechanics-markersets.md) require precise placement of markers at the respective anatomical landmarks. The markers directly relate to the coordinate system definition of each respective segment, affecting the resulting biomechanical analysis.
* The markers need to be placed on the skin for direct representation of the subject’s movement. Use appropriate adhesives to place markers and make sure they are securely attached.
* Place markers where you can palpate the bone or where there is less soft tissue in between. These spots have fewer skin movements and provide more secure marker attachment.
* While the basic marker placement must follow the avatar in the Builder pane, additional details on the accurate placements can be found on the [Biomechanics Marker Sets](../movement-sciences/movement-sciences-markersets/biomechanics-markersets.md) page.

{% hint style="info" %}
Joint markers are vulnerable to skin movements because of the range of motion in the flexion and extension cycle. To minimize the influence, a thorough understanding of the biomechanical model used is necessary in the post-processing.&#x20;

In certain circumstances, the joint line may not be the most appropriate location. Instead, placing the markers slightly superior to the joint line could minimize the soft tissue artifact, still taking care to maintain parallelism with the anatomical joint line.
{% endhint %}

### Calibration Markers

{% hint style="info" %}
Calibration markers exist only in the biomechanics Marker Sets.
{% endhint %}

Many Skeleton Marker Sets do not have medial markers because they can easily collide with other body parts or interfere with the range of motion, all of which increase the chance of marker occlusions.

However, medial markers are beneficial for precisely locating joint axes by associating two markers on the medial and lateral side of a joint. For this reason, some biomechanics Marker Sets use medial markers as _calibration markers_. Calibration markers are used only when creating Skeletons but removed afterward for the actual capture. These calibration markers are highlighted in red from the 3D view when a Skeleton is first created.

After creating a Skeleton from the [Builder pane](../motive-ui-panes/builder-pane.md), calibration markers need to be removed. First, detach the calibration markers from the subject. Then, in Motive, right-click on the Skeleton in the perspective view to access the context menu and click _Skeleton → Remove Calibration Markers_. Check the [assigned marker positions](data-recording/) to make sure that the Skeleton no longer expects markers in the corresponding medial positions.

<div><figure><img src="../.gitbook/assets/image (1529).png" alt="A screenshot of a Motive skeleton in segment view, with the calibration markers still attached. The calibration markers are highlighted with red circles." width="450"><figcaption><p>A Skeleton asset with calibration markers.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Skeleton without Calibration Markers.png" alt="A screenshot of a Motive skeleton in segment view, with the calibration markers removed." width="450"><figcaption><p>A Skeleton asset with the calibration markers removed.</p></figcaption></figure></div>

### Calibration Pose

A proper calibration posture is necessary because the pose of the created Skeleton will be calibrated from it.&#x20;

{% hint style="warning" %}
The avatar in the Builder pane does not change to reflect the selected pose.&#x20;
{% endhint %}

#### **T pose**

The T-pose is commonly used as the reference pose in 3D animation to bind two characters or assets together. Motive uses this pose when creating Skeletons. A proper T-pose requires straight posture with back straight and head facing directly forward. Both arms are parallel to the ground, forming a “T” shape, with the palms facing downward. Both arms and legs must be straight, and both feet need to be aligned parallel to each other.

<div><figure><img src="../.gitbook/assets/image (1530).png" alt="" width="210"><figcaption><p>Front View of a T-Pose.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Back view of T Pose.png" alt="" width="216"><figcaption><p>Back View of a T-Pose.</p></figcaption></figure></div>

#### **A pose**

The A-pose is especially beneficial for subjects who have restricted mobility in one or both arms. Unlike the T-pose, arms are abducted at approximately 40 degrees from the midline of the body, creating an A-shape. There are three different types of A-pose:  Palms down, palms forward, and elbows bent.

<div><figure><img src="../.gitbook/assets/image (1531).png" alt="" width="164"><figcaption><p>Front view of the A-Pose.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Back view of the A Pose.png" alt="" width="144"><figcaption><p>Back view of the A-Pose.</p></figcaption></figure></div>

* **Palms Down:** Arms straight. Abducted, sideways, arms approximately 40 degrees, palms facing downwards.
* **Palms forward:** Arms straight. Abducted, sideways, arms approximately 40 degrees, palms facing forward. Be careful not to over rotate the arm.
* **Elbows Bent:** Similar to all other A-poses. arms approximately 40 degrees, bend elbows so that forearms point towards the front. Palms facing downwards, both forearms aligned.

## Creating Skeletons

<figure><img src="../.gitbook/assets/Builder Pane and 3D Viewport - Skeleton Creation (1).png" alt="A screenshot of the Motive Builder Pane, set to Create a Skeleton, with the 3-D Viewport showing the skeleton markers. "><figcaption><p>Defining Skeleton from a Skeleton Marker Set.</p></figcaption></figure>

### Skeleton Creation Steps

Once the skeleton markers are [correctly placed](skeleton-tracking.md#placing-the-markers) for the selected template, it's time to finish creating the skeleton.

1. Select the calibration _Pose_ you plan to use to define the Skeleton from the drop-down menu. This is set to the T-pose by default.
2. The _Constraints_ drop-down allows you to assign labels that are defined by the Marker Set template (Default) or to assign custom labels by [loading a previously prepared XML](../motive-ui-panes/constraints-pane/constraints-xml-files.md) file of constraint names.&#x20;
3. Select the skeleton _Model_ to use for the spine. The default is the 7 Segment spine, but the classic 3 segment spine is also available for workflows that rely on this model. To change the default to the classic model, go to _Settings > Assets_. On the _Assets_ tab under _Skeleton Creation_, change the _Spine Type_ to your preferred default.
4. Select the _Visual_ template to apply to the skeleton. Options are:  Segment; Avatar - male; Avatar - female; None; or Cycle Avatar, which randomly assigns one of the two gendered avatars. This value can be changed later in the [Skeleton Properties](../motive-ui-panes/properties-pane/properties-pane-skeleton.md).&#x20;
5. Enter a unique name for the skeleton. The skeleton name is included as a prefix in the label for each of the skeleton markers.&#x20;
6. &#x20;Ask the subject to stand in the selected [calibration pose](skeleton-tracking.md#calibration-pose), feet shoulder-width apart. The T-pose should be done with palms downward.&#x20;
7. Click _Create_ to create a skeleton without the full Range of Motion. Once the Skeleton model has been defined, confirm all Skeleton segments and assigned markers are located at the expected locations. If any of the Skeleton segments seem to be misaligned, delete and create the Skeleton again after adjusting the marker placements and the calibration pose.

{% hint style="info" %}
**In Edit Mode**

If you are creating a Skeleton in the post-processing of captured data, you will have to [auto-label](labeling.md#auto-label) the Take to see the Skeleton modeled and tracked in Motive.
{% endhint %}

{% hint style="info" %}
**Reset Skeleton Tracking**

When Skeleton tracking is not acquired successfully during the capture for some reason, you can use the CTRL + R hotkey to trigger the solver to re-boot the Skeleton asset.
{% endhint %}

### **Create and Refine Skeleton - Range of Motion**

To calibrate the skeleton with a full range of motion during creation, click the _Create + Refine_ button.&#x20;

#### Range of Motion Take Files

By default, a Take with the name of the subject is recorded each time a Range of Motion calibration is completed in Live mode. This allows you to easily reprocess the skeleton if needed.&#x20;

To turn this setting off, go to _Settings > Assets._ On the _refinement_ ta&#x62;_,_ disable the _Record ROM_ settin&#x67;_._&#x20;

The Take is saved in the currently open data folder. If completing the ROM in edit mode, no additional recording is made.&#x20;

#### Range of Motion Settings

The _Assets_ tab of the _Settings_ panel has settings that pertain to skeleton creation.&#x20;

<figure><img src="../.gitbook/assets/Settings - Assets Skeleton Creation.png" alt="A screenshot of the Skeleton Creation settings from the Motive Settings panel, Assets pane. "><figcaption></figcaption></figure>

The **Height Marker** setting ensures the solved skeleton matches the correct height for the actor.&#x20;

<div><figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM without Height Marker CROPPED.png" alt="An image of a Motive Skeleton solved without the Height Marker setting enabled. "><figcaption><p>Height Marker <br>NOT Enabled</p></figcaption></figure> <figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 3 near end of Collection CROPPED.png" alt="An image of a Motive Skeleton solved with the Height Marker setting enabled. "><figcaption><p>Height Marker<br>Enabled</p></figcaption></figure></div>

The _Assets_ tab of the _Settings_ panel includes a new **Refinement tab** with numerous advanced settings related to the Range of Motion, including the option to Solve Constraints Only, or to Use Constraint Weights. You can change these settings to more accurately calibrate the results to the subject when necessary.

<figure><img src="../.gitbook/assets/Settings - Assets Refinement tab Advanced Top.png" alt="A screenshot of the Motive Settings panel, Assets Tab, with the top half of the Refinement subtab open. Settings categories are General, Solver Settings, and a portion of the Pose Assisted Solve Settings. " width="491"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Settings - Assets Refinement tab Advanced Bottom.png.png" alt="A screenshot of the Motive Settings panel, Assets Tab, with the bottom half of the Refinement subtab open. Settings categories are a portion of the Pose Assisted Solve Settings and the Joint Marker Settings. " width="491"><figcaption></figcaption></figure>

#### How to Complete a Range of Motion Calibration

Watch this video for a demonstration of how to complete a full Range of Motion. The steps are detailed, below.

{% embed url="https://vimeo.com/1126271525/4b9455d21a?fe=ci&fl=cl&share=copy" %}

The Builder pane will display the ROM calibration settings. Have the subject stand in the middle of the volume in either a T-pose or an A-pose.&#x20;

To see a list of recommended poses for the calibration, click the <img src="../.gitbook/assets/Help button.png" alt="A screenshot of the Motive &#x22;Help&#x22; button." data-size="line"> help button:&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM HELP tips.png" alt="A screenshot of the Skeleton Range of Motion suggested poses list. "><figcaption></figcaption></figure>

The Skeleton will appear in the 3D Viewport with the selected visual. Each bone segment will have a dark green hue at the beginning of sample collection.&#x20;

{% hint style="success" %}
_**Pro Tip:**_ You can assign a hotkey on the keyboard to the function "Create and Refine Skeleton" to create a skeleton and begin the Range of Motion calibration with a single keystroke. See [Settings: Mouse and Keyboard](../motive-ui-panes/settings/settings-mouse-and-keyboard.md) for instructions on assigning a hotkey.&#x20;
{% endhint %}

The builder pane shows the progress for each bone segment. This identifies which body parts the subject needs to move for the best calibration.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 1 Start of Collection.png" alt="A screenshot of the Motive Builder pane and 3D Viewport, showing a skeleton at the beginning of Range of Motion data collection. "><figcaption></figcaption></figure>

You can see which segments have sufficient samples and which need more in the "Coverage" bar in the Builder pane. Additionally, the bone segment will turn bright green in the 3D Viewport.

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 2 midway thru Collection.png" alt="A screenshot of the Motive Builder pane and 3D Viewport, showing a skeleton in the middle of Range of Motion data collection. "><figcaption></figcaption></figure>

Note that the Start Calculation button appears early in the sample collection process. We recommend waiting until the coverage is complete for all bone segments before you begin calculating. However, if you are finding it difficult to achieve 100% coverage, and feel satisfied with the samples collected, you can click the _Start Calculation_ button at any time after it appears. &#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 3 near end of Collection.png" alt="A screenshot of the Motive Builder pane and 3D Viewport, showing a skeleton near the end of Range of Motion data collection. "><figcaption></figcaption></figure>

When Motive has collected sufficient samples for all bone segments, the Builder pane and the Skeleton will change from green to blue as the Calibration moves to the Refinement phase.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 4 Collection Done Calc in progress.png" alt="A screenshot of the Motive Builder pane and 3D Viewport, showing a skeleton at the completion of Range of Motion data collection, before the calculation is applied."><figcaption></figcaption></figure>

The updated color reflects the quality of the calibration for that bone segment:

<figure><img src="../.gitbook/assets/ROM Calibration Results Legend.png" alt="A screenshot of the legend for Skeleton Range of Motion calibration results. "><figcaption></figcaption></figure>

The calculation can take several minutes to run. When it completes, the results will display at the bottom of the Builder pane.

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 5 Calc Completed.png" alt="A screenshot of the Range of Motion calibration results for a newly created skeleton, showing an excellent calibration. "><figcaption></figcaption></figure>

If you are satisfied with the results, click _Apply_. Otherwise, click _Cancel._&#x20;

{% hint style="info" %}
If you cancel the Range of Motion calculation instead of applying it, Motive will create the skeleton, calibrated to  the initial calibration pose. Use the Refine feature in the _Modify_ tab of the [Builder pane](../motive-ui-panes/builder-pane.md) to apply a new Range of Motion calibration to the existing skeleton.&#x20;
{% endhint %}

Once the ROM calibration is applied, the Builder pane will momentarily display "\[skeleton name] Created." The skeleton will appear in the 3D Viewport using the [visual](skeleton-tracking.md#select-visual) selected during creation. &#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Skeleton ROM 6 Completed.png" alt="A screenshot of the Motive Builder pane and the 3D Viewport at the beginning of the skeleton creation and calibration phase, early in the sample collection. "><figcaption></figcaption></figure>

{% hint style="success" %}
The Refinement section of the Skeleton's Properties shows the date, time, quality, and constraint error of the Range of Motion applied to the skeleton.
{% endhint %}

<figure><img src="../.gitbook/assets/Properties Pane - Skeleton Refinement Not Done (1).png" alt="A screenshot from Motive the Skeleton properties pane, Refinement Section, showing that the skeleton has not had a Range of Motion calibration applied. "><figcaption><p>The Skeleton Refinement Properties, <br>prior to applying a Range of Motion calibration.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Properties Pane - Skeleton Refinement Completed (1).png" alt="A screenshot from Motive the Skeleton properties pane, Refinement Section, showing that the skeleton had a Range of Motion calibration applied on 10/6/25 at 4:30 pm, with Great Quality and Constraint error of 7.16 mm."><figcaption><p>The Skeleton Refinement Properties, <br>After applying a Range of Motion calibration.</p></figcaption></figure>

## Modifying Skeletons

Several changes can be made to Skeleton assets from the Modify tab of the Builder pane, or through the context menus available in the 3D Viewport and the Assets Pane.&#x20;

Skeleton marker colors and marker sticks can be viewed in the 3D Viewport. They provide color schemes for clearer identification of Skeleton segments and individual marker labels. To make them visible, enable _Marker Sticks_ and _Marker Colors_ under the visual aids <img src="../.gitbook/assets/Motive Visual Options button (2).png" alt="" data-size="line"> in the [perspective view](../motive-ui-panes/viewport.md#perspective-view) pane.&#x20;

### Calibrate an Existing Skeleton

Skeleton assets can be recalibrated using the existing Skeleton information. Recalibration recreates the selected Skeleton using the same Skeleton Marker Set and refreshes expected marker locations on the assets.

{% hint style="danger" %}
Skeleton recalibration does not work for Skeleton templates with added markers.
{% endhint %}

There are several ways to recalibrate a Skeleton:

* **From the Viewport:** Select all of the associated Skeleton markers in the 3D Viewport, right-click and select _Skeletons > Update from Selection - Bones and Constraints_ or _Update from Selection -  Constraints Only._ See [Update from Selection](skeleton-tracking.md#update-from-selection), below, for more detail on these options.&#x20;

<figure><img src="../.gitbook/assets/Viewport - Context Menu Skeleton recalibration.png" alt="A screenshot of the Motive Viewport with the markers of a skeleton selected and the Context menu displayed. Skeletons (1) is selected on the menu with the options to Update from Selection are displayed. "><figcaption></figcaption></figure>

* **From the Assets pane:** Right-click the skeleton in the Assets pane and select _Skeletons >_ _Update from Selection - Bones and Constraints_ or _Update from Selection -  Constraints Only._ See [Update from Selection](skeleton-tracking.md#update-from-selection), below, for more detail on these options.&#x20;

<figure><img src="../.gitbook/assets/Assets Pane - Skeleton Recalibration.png" alt="A screenshot of the Motive Assets pane, with a skeleton selected and the context menu displayed. The Skeletons item is selected and the submenu to Update from Selection is displayed. "><figcaption></figcaption></figure>

* **From the Builder pane:** Open the Modify tab of the Builder pane for all Skeleton recalibration options.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Modify skeleton options.png" alt="A screenshot of the Motive Builder Pane Modify tab with the following options for editing a skeleton: Update from Selection, Refine, Marker Constraints, and Marker Sticks. "><figcaption><p>Builder Pane:  Modify Skeleton.</p></figcaption></figure>

#### Update From Selection

This function recalibrates existing Skeleton assets using the current Skeleton information. The update will be based on a single T-pose frame. To calibrate the skeleton using a full Range of Motion (ROM), use the [Refine ](skeleton-tracking.md#refine-1)feature instead.&#x20;

To recalibrate a Skeleton, select all of the associated Skeleton markers from the perspective view. Make sure the selected Skeleton is in a calibration T-pose, and click the <img src="../.gitbook/assets/Pane Items closed.png" alt="A screenshot of the Expand Display button in Motive. " data-size="line"> button to see the available options.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane - Modify Skeleton from Selection expanded CROPPED.png" alt="A screenshot of the &#x22;Update from Selection&#x22; option in the Motive Builder pane, modify skeleton options. "><figcaption></figcaption></figure>

* **Bones and Constraints:** This option recalibrates the selected skeleton using the same Skeleton Marker Set and refreshes the constraint locations. This can also be done using the **Ctrl + R** hotkey.
* **Constraints Only:** This options recalibrates the selected skeleton's constraints based on the current location of the markers, without recalibrating bones.&#x20;

{% hint style="danger" %}
Skeleton recalibration does not work with Skeleton templates that include additional markers.
{% endhint %}

#### Refine

The Refine function allows you to apply a Range of Motion (ROM) calibration to a skeleton anytime after it's been created, including in post-production. See the section [Create and Refine Skeleton - Range of Motion](skeleton-tracking.md#create-and-refine-skeleton-range-of-motion) for details on how to use to use this tool.&#x20;

Motive has the option to save a backup copy of the original skeleton for comparison purposes when completing a Live Range of Motion calibration on an existing skeleton asset. To turn this setting on, go to  _Settings > Assets_ and enable the setting _Save Unrefined Skeleton_ on the _Refinement_ tab.&#x20;

{% hint style="info" %}
**Post-Processing: Working with Recording&#x20;**_**Takes**_&#x20;

**Edit Mode** is used for playback of captured _Take_ files. In this mode, you can playback and stream recorded data and complete post-processing tasks. The Cameras View displays the recorded 2D data while the 3D Viewport represents either recorded or real-time processed data as described below.

There are two modes for editing:

* **Edit:** Playback in standard Edit mode displays and streams the processed 3D data saved in the recorded _Take_. Changes made to settings and assets are not reflected in the Viewport until the _Take_ is [reprocessed](reconstruction-and-2d-mode.md#applying-changes-to-3d-data).&#x20;
* **Edit 2D:** Playback in Edit 2D mode performs a live reconstruction of the 3D data, immediately reflecting changes made to settings or assets. These changes are displayed in real-time but are not saved into the recording until the _Take_ is [reprocessed](reconstruction-and-2d-mode.md#applying-changes-to-3d-data) and saved. To playback in 2D mode, click the Edit button and select _Edit 2D_. &#x20;

Regardless of the selected Edit mode, you must reprocess the _Take_ to create new 3D data based on the modifications made.&#x20;
{% endhint %}

#### Marker Constraints

Constraints store information on marker labels, colors, and marker sticks which can be modified, exported and re-imported as needed. For more information on exporting and importing constraints, please refer to the [Constraints XML Files](../motive-ui-panes/constraints-pane/constraints-xml-files.md) page.

To modify marker colors and labels, use the [Constraints pane](../motive-ui-panes/constraints-pane/).

Right-click the skeleton in the asset pane and select _Constraints >_ _Reset Constraints to Default_ to update the Skeleton markers with the default constraints template.

![(Left) Marker colors enabled in the perspective view. (Right) Both marker sticks and marker colors are enabled in the perspective view.](<../.gitbook/assets/image (943).png>) ![Constraints context menu in the asset pane. ](<../.gitbook/assets/Asset Context Menu - Reset constraints.png>)

#### Add or Remove Constraints

Skeleton Marker Sets can be modified slightly by adding or removing markers to or from the template. Follow the below steps for adding/removing markers.&#x20;

{% hint style="warning" %}
Modifying, especially removing, Skeleton markers is not recommended since changes to default templates may negatively affect the Skeleton tracking if done incorrectly.&#x20;

Removing too many markers may result in poor Skeleton reconstructions, while adding too many markers may lead to labeling swaps.&#x20;

If any modification is necessary, try to keep the changes minimal.
{% endhint %}

![Related markers for a Skeleton segment indicated when Marker Lines advanced Skeleton property is enabled.](<../.gitbook/assets/image (917).png>)

{% hint style="info" %}
When adding, or removing, markers in the Edit mode, the Take needs to be [auto-labeled](labeling.md#auto-label) again to re-label the Skeleton markers.
{% endhint %}

#### Add Marker Constraints

1. Open the Modify tab on the [Builder pane](../motive-ui-panes/builder-pane.md).
2. In the 3D Viewport, select the Skeleton segment that you are adding add the extra markers to.
3. CTRL + left-click on the marker that you wish to add to the skeleton.
4. On the _Marker Constraints_ tool in the Builder pane, click <img src="../.gitbook/assets/Add Button - Active (3).png" alt="" data-size="line"> to add and associate the selected marker to the selected segment.
5. You can also add Constraints from the Constraints pane.&#x20;
6. Reconstruct and Auto-label the Take.
7. Extra markers added to Skeletons will be labeled as _Skeleton\_CustomMarker#_. Use the [Constraints pane](../motive-ui-panes/constraints-pane/) to change the label as needed.

#### **Remove Marker Constraints**

1. Enable selection of Marker Constraints from the visual aids option in [perspective view](../motive-ui-panes/viewport.md#perspective-view).
2. \[Optional] Under the advanced properties of the target Skeleton, enable the _Marker to Constraint Lines_ property to view which markers are associated with different Skeleton bones.
3. Open the Modify tab on the [Builder pane](../motive-ui-panes/builder-pane.md).
4. Select the Skeleton segment to modify and the Marker Constraints you wish to dissociate.
5. Delete the association by clicking on the <img src="../.gitbook/assets/Remove button - active (2).png" alt="" data-size="line"> in the _Constraints_ section.
6. Alternately, you can click <img src="../.gitbook/assets/Remove button - active (3).png" alt="" data-size="line"> to remove selected markers from the Constraints pane.
7. From the [Data pane](../motive-ui-panes/data-pane.md), right click the _Take_ and select _Reconstruct and Auto-label_.&#x20;

![Adding an extra chest marker to a Skeleton. Click image to enlarge.](<../.gitbook/assets/image (925).png>) ![Changing the name of newly added marker from the Constraints pane.](<../.gitbook/assets/image (936).png>)

#### Marker Sticks

A Marker stick connects two markers to create a visible line. Marker sticks define the shape of an asset, showing which markers connect to each other, such as knee to hip, and which don't, such as hand to foot. Skeleton Marker Sets include the placement of marker sticks.&#x20;

<figure><img src="../.gitbook/assets/Builder Pane Marker Sticks (1).png" alt=""><figcaption><p>Modify Marker Sticks from the Builder Pane. </p></figcaption></figure>

<table><thead><tr><th width="100">Button</th><th>Function</th></tr></thead><tbody><tr><td><img src="../.gitbook/assets/Builder Pane - Marker Sticks Change color.png" alt="" data-size="original"></td><td>Changes the color of the selected Marker Stick(s).</td></tr><tr><td><img src="../.gitbook/assets/Builder Pane - Auto button inactive.png" alt="" data-size="original"></td><td>Autogenerates Marker Sticks for the selected Trained Markerset asset. Does not apply to skeleton assets.</td></tr><tr><td><img src="../.gitbook/assets/Builder Pane - Connect all markers.png" alt="" data-size="original"></td><td>Connects all of the selected Markers to each other. Not recommended for skeleton assets. </td></tr><tr><td><img src="../.gitbook/assets/Builder Pane - Add Bones in order.png" alt="" data-size="original"></td><td>Creates Marker Sticks based on the order in which the markers were selected.</td></tr><tr><td><img src="../.gitbook/assets/Remove button - active (4).png" alt="" data-size="original"></td><td>Removes the selected Marker Stick(s).</td></tr></tbody></table>

### Skeleton Properties

For newly created Skeletons, default Skeleton creation properties are configured under the [Application Settings pane](../motive-ui-panes/settings/settings-assets.md). Click the <img src="../.gitbook/assets/Settings button (7).png" alt="" data-size="line"> button and select _Assets_.&#x20;

Properties of existing, or recorded, Skeleton assets are configured under the [Properties pane](../motive-ui-panes/properties-pane/properties-pane-skeleton.md) while the respective Skeletons are selected.

To configure Advanced properties, click the <img src="../.gitbook/assets/Motive Context Menu (16).png" alt="" data-size="line"> button in the top right corner of the pane.&#x20;

<figure><img src="../.gitbook/assets/image (1532).png" alt="" width="563"><figcaption><p>Selected Skeleton with Properties Pane.</p></figcaption></figure>

## Export Assets&#x20;

Assets can be exported into the Motive user profile (.MOTIVE file) if they need to be re-imported. The [user profile](motive-basics.md#motive-user-profile-.motive) is a text-readable file that contains various configuration settings in Motive, including the asset definitions.

When asset definitions are exported to a MOTIVE user profile, the profile stores the marker arrangements calibrated in each asset, which can be imported into different takes without creating a new asset in Motive.&#x20;

The user profile stores the spatial relationship of each marker to the others in the asset. Only the identical marker arrangement will be recognized and defined with the imported asset.

To export all of the assets in Live-mode or in the current _TAKE_ file, go to _File_ menu and selected _Export Assets._ You can also select the _File_ menu → _Export Profile_ option to export other software settings as well as the assets.

![Exporting Assets into the User Profile.](<../.gitbook/assets/image (424) (1).png>) ![Options when exporting the user profile. ](<../.gitbook/assets/image (124) (1) (1) (2).png>)

![Exporting from Assets pane.](<../.gitbook/assets/Context Menu - Export Skeleton Asset.png>)

## Relative Skeleton Joint Angles

There are two ways of obtaining Skeleton joint angles. Rough representations of joint angles can be obtained directly from Motive, but the most accurate representations of joint angles can be obtained by pipelining the tracking data into a third-party biomechanics analysis and visualization software (e.g. [Visual3D](https://www.c-motion.com/) or [The MotionMonitor](http://www.innsport.com/)).

For biomechanics applications, joint angles must be computed accurately using the respective Skeleton model solve, which can be accomplished by using biomechanical analysis software. [Export C3D files ](data-export/data-export-c3d.md)or stream tracking data from Motive and import into an analysis software for further calculation. From the analysis, various biomechanics metrics, including the joint angles, can be obtained.

**Joint angles generated and exported from Motive are intended for basic visualization purposes only and should not be used for any type of biomechanical or clinical analysis.** A rough representation of joint angles can be obtained by either exporting or streaming the Skeleton Rigid Body tracking data. When exporting the tracking data into CSV, set the [Use World Coordinates](data-export/data-export-csv.md) export setting to _Local_ to obtain bone segment position and orientation values in respect to its parental segment, roughly representing the joint angles by comparing two hierarchical coordinate systems. When streaming the data, set [Local Rigid Bodies](data-streaming.md) to true in the streaming settings to get relative joint angles.

## Constraints XML: Customize Marker Labels, Colors, and Sticks

Each Skeleton asset has its marker templates stored in a Constraints XML file. A Skeleton Marker Set can be modified by exporting, customizing, and importing the Constraints XML files. Specifically, customizing the XML files will allow you to modify Skeleton marker labels, marker colors, and marker sticks within a Skeleton asset. For detailed instructions on modifying Skeleton XML files, read the [Constraints XML Files](../motive-ui-panes/constraints-pane/constraints-xml-files.md) page.

**To export Skeleton constraints XML file**

To export a Skeleton XML file, right-click on a Skeleton asset under the Assets pane and select _Constraints -->_ [_Export Constraints_](../motive-ui-panes/assets-pane.md#for-Skeleton-assets) to export corresponding Skeleton marker XML file.

**To import Skeleton constraints XML file**

When creating a new Skeleton, you can import a constraints XML file under the _Labels_ section of the [Builder pane.](../motive-ui-panes/builder-pane.md) To import a constraints XML file to an existing Skeleton, right-click on a Skeleton asset under the Assets pane and select _Constraints -->_ _Import Constraints_.
