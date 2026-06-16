---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/viewport
---

# Viewport

When using Motive, the main Viewport will always be docked in the center. The Viewport can be divided into two, three, or four panes. If desired, additional Viewer panes can be opened by clicking the <img src="../.gitbook/assets/image (70).png" alt="" data-size="line"> icon on the main toolbar.&#x20;

## Viewport Control

The following actions are useful for when navigating using the viewport. All of the mouse actions and keyboard hotkeys can be customized in the [Application Settings: Keyboard](settings/settings-mouse-and-keyboard.md) panel.

### Mouse Control

| Function                        | Default Control             |
| ------------------------------- | --------------------------- |
| Rotate view                     | Right + Drag                |
| Pan view                        | Middle (wheel) click + drag |
| Zoom in/out                     | Mouse Wheel                 |
| Select in view                  | Left mouse click            |
| Select multiple objects in view | CTRL + left mouse click     |

### Keyboard Control

| Function                   | Default Control                                                                                                                                                                                                                                                                                                                                                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Switch to Perspective View | Number 1                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Switch to Camera View      | Number 2                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Switch to Reference View   | Number 3, while a camera is selected.                                                                                                                                                                                                                                                                                                                                                                                     |
| Split View                 | <p>Shift + 1: Show only one viewport.</p><p><br>Shift + 2: Split the viewport into two horizontally.</p><p><br>Shift + 3: Split the viewport into two vertically.</p><p><br>Shift + 4: Split the Viewport into four.</p><p><br><em>Additional options are available by clicking the</em> <img src="../.gitbook/assets/Motive Context Menu (17).png" alt="" data-size="line"> <em>button on the top-right corner.</em></p> |
| Zoom                       | <p>F: Quickly zoom into a selected object(s) or camera(s) in the view.<br><br>Shift + F: Quickly zoom out to fit everything into the view.</p>                                                                                                                                                                                                                                                                            |

## Perspective View

![3D Perspective View.](<../.gitbook/assets/image (174).png>)

{% hint style="info" %}
To set the floor plane to match the volume size, go to _Settings_ --> _View_ --> _3D Tab_ --> and adjust the _Grid Width_ and _Grid Length_ values.&#x20;
{% endhint %}

### Toolbar Options

#### **Mouse Interactions** ![](<../.gitbook/assets/image (177).png>)

Allows you to switch between different mouse interaction modes in the 3D viewport. Please see [Gizmo Tool:  Translate, Rotate, and Scale](../motive/assets/gizmo-tool-translate-rotate-and-scale.md) for more information on using the translate, rotate and scale tools, and [Quick Label](../motive/labeling.md#quicklabel-mode) for more information on the quick label tool.

![Mouse action options.](<../.gitbook/assets/Gizmo Tool in 3D Viewport (3).png>)

* **Select**: In selection mode, left-click to select an object in the Viewport. left-click and drag or use shift + left-click to select multiple objects. The currently selected object will display a cyan border. If multiple objects are selected, the final one selected will have the cyan border and the others will have a yellow border. Properties for the selected objects are shown in the [Properties pane](properties-pane/).&#x20;

<figure><img src="../.gitbook/assets/Rigid Body with 3 Markers Selected (1).png" alt=""><figcaption><p>Rigid Body with 3 markers selected.</p></figcaption></figure>

* **Translate**: manually adjust the location of Rigid Body pivot points and Skeleton bones with the translate tool. In recorded data, you can also select a group of reconstructed 3D markers in the scene and apply translation along the global x-y-z axis. When the change is made to a Skeleton, the segment hierarchy will be modified and reflected on exported Skeleton bone data but the marker locations will remain the same.
* **Rotate**: This tool rotates the orientation of Rigid Body pivot points and Skeleton bones.
* **Scale**: Proportionately increases or decreases the length of Skeleton bones or the size of the [geometry model](/broken/pages/sQK8scBDhFagaBZY6IVS#attached-geometry) attached to a Rigid Body.
* **Quick Label**:  The [QuickLabel mode](../motive/labeling.md#quicklabel-mode) tool allows users to easily reassign marker labels in post-processing.
* **Local Coordinates**: When enabled, translation, rotation, and scaling changes will be applied with respect to the local coordinate axis of the selected asset. When disabled, all changes will be applied to the global coordinate axis.
* **Symmetric Bones**: When enabled, any modifications on bone lengths and orientations are applied symmetrically on both the left and right side of a Skeleton.

#### **Zoom Actions** ![](<../.gitbook/assets/image (129).png>)

Actions for zooming in to a selected object or zooming out to fit all. You can also use "F" and "Shift + F" hotkeys for this.

#### **Visual Aids** ![](<../.gitbook/assets/image (163).png>)

Opens a menu to enable or disable visuals in the perspective viewport. From this menu, you can show or hide markers, marker labels, Rigid Bodies, Skeletons, tracked rays, and more.

![Visual Aids menu.](<../.gitbook/assets/ViewPort Visual Options.png>)

**Visible**&#x20;

Select what to show in the 3D Viewport.&#x20;

* **Markers:** &#x20;
  * **Show:** Display all markers.
  * **Hide for Disabled Assets:** Hide markers for assets that are not selected in the Asset pane.&#x20;
  * **Hide all:**  do not display any markers.&#x20;

{% hint style="info" %}
**Pro Tip:** Use the _Hide for Disabled Assets_ option then disable assets when you are done labeling and editing them to better focus on the remaining unlabeled assets. To disable an asset, uncheck the <img src="../.gitbook/assets/image (1538).png" alt="" data-size="line"> box to the left of the asset name in the Asset pane.&#x20;
{% endhint %}

* **Cameras:**  Display all visible cameras.&#x20;
* **Rigid Bodies:**  Display the marker sticks, constraints, and bones of rigid bodies.&#x20;
* **Marker Constraints:**  Constraints are the calculated marker positions for assets.
  * **Current Properties:**  Constraints will be displayed only if the option to display them is selected in the properties for the selected asset.
  * **Show All:**  Display all constraints regardless of the setting in the asset properties.
  * **Hide All:**  Hide all constraints regardless of the setting in the asset properties. Markers will still be visible.&#x20;
* **Skeletons:**&#x20;
  * **Current Properties:**  Skeletons will display with the visual aid set in the properties for the selected asset. Options are Segment, Avatar (by gender), or none.&#x20;
  * **Bones Only:**  Display all skeletons as bone segments regardless of the setting in the asset properties.
  * **Segments Only:**  Display all skeletons as geometric segments regardless of their individual properties.
  * **Avatars Only:**  Display skeletons as avatars regardless of their individual properties.
  * **Hide All:**  Hide all skeletons. Skeleton markers will still be visible.&#x20;

**Marker**

* **Labels:**  Show marker labels for selected markers. Marker labels include the name of the asset unless Simplify Labels is turned on.
* **Simplify Labels:**  Show the marker label for selected markers without including the asset name in the label.&#x20;
* **Info:**  Show marker x/y/z coordinates and the diameter of the marker.
* **Active IDs:**  Adds the Active ID number to the marker label. Marker labels must be turned on to see this information.
* **Color:**  When checked, each marker will display with the color shown on the constraints tab. When unchecked, markers will display as white.&#x20;
* **Sticks:** Show marker sticks. [Marker sticks](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#marker-colors-and-marker-sticks) connect markers to each other and can be used to define the shape of an asset (e.g., connecting a knee marker to a hip marker but not to an elbow marker).
* **History:** Show marker trajectory history. Includes a trail for selected markers in playback.
* **Distance:**  Show marker distance information when two markers are selected.
* **Angle:** Show angle information when three markers are selected.

**Rays**

* **Tracked Rays:**  Tracked rays are the marker centroid rays from each camera that contribute to the 3D reconstructions.
* **Untracked Rays:**  Untracked Rays are the marker centroid rays that do not contribute to the 3D reconstructions because the reconstruction requirements, usually the ray count, are not met.

**Heads Up Display**

* **Marker Count:** Show total and selected marker counts at the bottom right corner.
* **Coordinate Axis:**  Show the global coordinate axis at the bottom left corner.

**Other**

* **Capture Volume:** Display a 3D grid to show where 3 or more cameras converge in the volume.
* **Constraint Graph:** Display an overlay of marker sticks connecting the constraints of an asset.
* **Floor Plane:** Display the floor plane of the volume in light gray.
* **Shadow:**  Add a projected shadow graphic to the floor pane for objects in the take. The Floor Plane visual must be on to see shadows.

#### **Selection Lock** ![](<../.gitbook/assets/image (88).png>)

This tool locks the focus on the selected object(s), moving the viewport to follow the selection throughout the capture.&#x20;

#### **Selection** ![](<../.gitbook/assets/image (161).png>)

Enables selection of specific objects in the 3D view. Only the items checked in the menu will be selectable in the perspective view.

<figure><img src="../.gitbook/assets/Viewport - Enable Selection menu.png" alt=""><figcaption><p>Selection Menu.</p></figcaption></figure>

### Context Menus in the Perspective Viewport

Right-click an asset, marker, or camera in the Perspective Viewport to open a context menu specific to the selection. The menu displays the number of objects (markers, rigid bodies, etc.) that will be affected by any changes made.&#x20;

{% hint style="info" %}
Motive will stack the context menus if multiple object types are selected.&#x20;
{% endhint %}

#### Marker Context Menu

The following context menus appear when 3D reconstructed markers are selected.

<div><figure><img src="../.gitbook/assets/Context Menu - Markers only selected.png" alt=""><figcaption><p>Marker Context Menu.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Context Menu - Markers to create Skeleton selected.png" alt=""><figcaption><p>Marker Context Menu: Skeleton detected.</p></figcaption></figure></div>

* **Create** **Markerset:**  Create a [trained markerset](../motive/trained-markersets.md) from the selected markers. This option will be available on the menu if at least one marker is selected.&#x20;
* **Create Rigid Body:**  Create a [Rigid Body](builder-pane.md#rigid-body-create) asset from the selected markers. This option is grayed out if the markers are already part of an existing asset.
* **Create Skeleton:**  Create a [Skeleton](builder-pane.md#Skeleton-create) asset from the selected markers. This option is grayed out unless Motive detects the minimum number of markers needed to create a skeleton asset. Click _Create Skeleton_ for a pop-out menu of skeleton templates that match the marker layout.
* **Unlabel:**  remove the assigned labels to the selected markers.&#x20;
* **Mask:**  mask the selection so it is no longer detected.&#x20;
* **Select Contributing Cameras:**  Selects all the cameras in both the 3D Viewport and the Cameras Viewport that contribute to the 3D reconstruction of the marker location.&#x20;
* **Zoom to All:**  Quickly zoom out to fit everything into the view.
* **Zoom to Selection:**  Quickly zoom to the selected objects.

#### Marker Constraints Context Menu

The following context menus appear when marker constraints are selected.

<figure><img src="../.gitbook/assets/image (1539).png" alt=""><figcaption><p>Marker Constraint Context Menu.</p></figcaption></figure>

* **Set Key:**  Align the marker with its constraint.&#x20;
* **Zoom to All:**  Quickly zoom out to fit everything into the view.
* **Zoom to Selection:**  Quickly zoom to the selected objects.

{% hint style="info" %}
The [selection](viewport.md#selection) of Marker Constraints must be enabled to see this menu.
{% endhint %}

#### Asset(s) Context Menus

The following context menus appear when an asset (skeleton, rigid body, or trained markerset) is selected. If markers are also selected, the _Markers_ context menu is included. If marker constraints are selected, the _Marker Constraints_ menu is included.&#x20;

<div><figure><img src="../.gitbook/assets/Context Menu - Rigid Body selected no markers.png" alt=""><figcaption><p>Context Menu with Rigid Body <br>and No Markers selected.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Context Menu - Skeleton selected.png" alt=""><figcaption><p>Context menu with skeleton, bones, <br>and markers selected.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Context Menu - Skeleton markers and marker constraints selected.png" alt=""><figcaption><p>Context menu with skeleton, bones, markers, <br>and marker restraints selected.</p></figcaption></figure></div>

* **Markers:**  When markers are selected along with an asset, the Markers menu option will be available, along with the number of markers selected. Click this to access Marker options:
  * **Add Constraint:** Add the selected marker(s) to the asset.&#x20;
  * **Remove Constraint:**  Remove the selected constraint(s) from the asset.
  * **Set Bone Position:**  Align the bone or pivot point of the asset with the selected marker. If multiple markers are selected, align to the marker selected last.
* **Bones:**  In Motive, a Bone is a virtual structure that connects two joints and represents a segment of a virtual skeleton or Trained Markerset or the pivot point of a rigid body.
  * **Add from Marker(s):**  Create a new bone segment from the selected markers.
  * **Remove:**  Delete the selected bone(s).
  * **Add Bone Chain:**  Add a bone chain between two selected bones. Whichever bone is selected first becomes the parent bone, the second becomes the child bone.
  * **Unparent Bone(s):**  Unparent the selected bone or bones. This removes the bone chain between the bones.
  * **Reroot Bones:**  Reroot the selected child bone and make it the parent in the bone chain.&#x20;
  * **Align to Camera:**  Align the bone or pivot point of a rigid body to the selected camera. Camera must be selected in the 3D viewport.
  * **Align to Other Bone:**  Align the bone or pivot point of a rigid body to another. The asset to be aligned must be unsolved; right-click the asset in the Assets Pane and select _Remove Solve_ if necessary. Select the bone or rigid body to be aligned first, and the alignment bone or rigid body last.
  * **Reset Location:**  Restore the bone to its original location. &#x20;
* **Training:** Use the [Training function](../motive/trained-markersets.md#training-options) to show Motive how a markerset moves through 3D space. Read the page on [trained markersets](../motive/trained-markersets.md) for more details on the options below.
  * **Auto-Generate Asset:**  Add marker training and Auto-Generate Marker Sticks. This function only needs to be performed once after a Markerset has been created.
  * **Add Marker Training:**  Add a learned model of the Markerset.&#x20;
  * **Remove Marker Training:**  Remove all marker training previously applied.
  * **Auto-Generate Bones:**  Automatically generate bones at flex points. This is why recording a full range of motion of your object is important so these bones can be added correctly.&#x20;
  * **Refine Bone Positions:**  Apply another round of Marker Training and refine Bone positions based on new training information.&#x20;
  * **Refine Constraint Positions:**  Apply another round of Marker Training and refine Constraint positions based on new training information.&#x20;
* **Active Tags:**  Active tags provide _synchronized_ tracking through active LED markers and an internal Inertial Measurement Unit (IMU). Read the articles [IMU Sensor Fusion](/broken/pages/ysdyrsuQyF9qn6xMu4ix) and [Active Marker Tracking](../active-classic/active-marker-tracking/) for more details on the actions below.&#x20;
  * **Auto Configure Active Tags:**  Pair and align the Rigid Body to the IMU Tag all in one step.
  * **Set Auto Pair:**  The Rigid Body will search for an IMU pair. Once paired, this will be indicated in the _3D Viewport_ IMU visual as 'IMU Paired', the _Devices_ pane Active Tag 'Paired Asset' column, and in the _Assets_ pane's 'Active Tag' column.&#x20;
  * **Unpair Active Tag:**  Remove a paired Tag from the Rigid Body.&#x20;
  * **Align:**  Manually align the Tag to the Rigid Body after they are paired.
  * **Remove Alignment:**  Remove alignment from the Rigid Body while still paired to the IMU.&#x20;
  * **Orient Pivot to IMU:  Set the** Pivot orientation of the Rigid Body to reflect the orientation of the (internal) IMU.)
* **Make Reference:**  Set the 3D Viewport to the perspective of the selected Asset.&#x20;
* **Skeletons:**&#x20;
  * **Recalibrate from Selection:**  Update the skeleton's calibration based on the current positions of the selected markers, using the same skeleton template.
  * **Remove Calibration Markers:**  Remove markers from the skeleton calibration.
* **Delete:**  Delete the selected asset(s).

#### Force Plate Context Menu

The following context menu appears when a force plate is selected.

![Force Plate context menu.](<../.gitbook/assets/image (1166).png>)

* **Set Position**:  Reposition a force plate asset according to the location of the calibration square. This is used to calibrate the position of a selected force plate within Motive. For more information, please see the [Force plate setup](../movement-sciences/) page.
* **Zero (all)**:  Zero, or tare, all selected force plates.
* **Re-Sync (all)**:  For triggered synchronization protocols, (e.g. force plates that sync using the record trigger), this feature re-synchronizes force plates within the camera system. This will remove any sync offsets that may have increased gradually since the trigger.

## Cameras View

![](<../.gitbook/assets/image (111).png>)

### Hotkeys

| Function                                 | Default Control                                                                                                                              |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Switch selected cameras to Object mode   | O                                                                                                                                            |
| Switch selected camera to MJPEG mode     | I                                                                                                                                            |
| Switch selected camera to Grayscale mode | U                                                                                                                                            |
| Zoom                                     | <p>F: Quickly zoom into a selected camera(s) in the view.</p><p><br>Shift + F: Quickly zoom out to fit all of the cameras into the view.</p> |

### Toolbar Options

#### **Mouse Actions** <img src="../.gitbook/assets/Select or Edit 3D Object (2).png" alt="" data-size="line">

From this icon, you can switch between different mouse interaction modes in the camera viewport. This allows you to select objects, inspect pixels, and add or remove masks from the camera view.

<figure><img src="../.gitbook/assets/Camera Mouse Actions menu (1).png" alt=""><figcaption><p>Camera Mouse Actions menu.</p></figcaption></figure>



![Pixel inspector enabled in 2D view.](<../.gitbook/assets/image (142).png>)

#### **Pixel Inspection**

In pixel inspection mode, the camera viewport displays the X,Y coordinates of the cursor location, and pixel brightness for selected pixels when a region is drag-selected. Inspecting pixel brightness can be useful during camera focusing, tuning, and aiming.

#### Add/Remove Masking

To mask an area not previously masked, select Ellipse, Rectangle, or Pencil. When using Ellipse or Rectangle, click and drag to select the area to be masked. Pencil mode creates a fine line following the cursor movement.&#x20;

To unmask a previously masked area, use the Erase Rectangle, Erase Ellipse, or Eraser functions.&#x20;

#### **Zoom Actions** ![](<../.gitbook/assets/image (86).png>)

Zoom to All:  Zooms all cameras to fit the pane. (default hotkey: Shift + F)

Zoom to Selection:  Zooms into selected cameras to fit the pane. (default hotkey: F)

#### **Visual Aids** ![](<../.gitbook/assets/image (133).png>)

![Camera viewport visual aid options.](<../.gitbook/assets/image (257).png>)

Show or hide additional camera information from the camera viewport.

* **Reticles:**  Show marker reticles to indicate where the reconstructed markers are located in respect to the camera view.
* **Camera Info:** Show camera specific information, including camera models, camera setting values, time, data transfer rate, frame ID, and sync methods. For Prime series cameras, image board temperature information is also available. If there are any synchronization or hardware issues, they will also be indicated in the camera info.

_**Markers**_&#x20;

Zoom in to a camera in object mode to view the following marker data in the 3D Viewport. Information is shown for all markers in the Viewport.&#x20;

* **Coordinates:** Show (x,y) coordinate information for the reflections that satisfy the 2D object filter.
* **Centroids:**  Show centroid crosshairs for the reflections that satisfy the 2D object filter.
* **Circularity:** Show circularity value labels for detected reflections. The label will appear red if the reflection does not satisfy the 2D filter setting.
* **Size:**  Show number of pixels involved in each reflection. The label will appear red if the reflection does not satisfy the 2D filter setting.
* **Labels:**  Show whether the markers detected in the camera view are passive retroreflective marker or active markers. When the camera detects an active LED marker the corresponding label ID for each marker will be shown.

#### **Camera Masking Settings** ![](<../.gitbook/assets/image (123).png>)

Using the masking settings context menu, you can re-apply auto-masking feature, clear masks, and/or perform other actions related to applying masks in the camera view.

* **Mask All:**  Apply auto-masking to all of the connected cameras.
* **Mask Selected:** Apply auto-masking to the selected cameras only.
* **Mask Cameras:**  Detect and mask camera LED ring lights. &#x20;
* **Masking is Additive:**  When selected, new masks are added to existing masks. If this setting is unchecked, Motive will remove and replace all masks each time a mask is applied.
* **Clear All:**  Clear all masks from all of the connected cameras.
* **Clear Selected:**  Clear masks from the selected cameras only.

### Camera Settings

Right-click on a camera in either the Cameras Viewport or the 3D Viewport to open the Camera Settings menu.

<figure><img src="../.gitbook/assets/Camera Viewport Context Menu (3).png" alt="Context Menu from the Cameras Viewport."><figcaption><p>Camera Settings menu.</p></figcaption></figure>

{% hint style="info" %}
By default, Motive labels cameras by location. To use custom labeling, go to _Settings_ --> _General_ --> _Camera Settings_ and select _Custom Number_ from the dropdown list. This will open the Camera Number field for editing in the camera properties pane.&#x20;
{% endhint %}

#### Video Type

Select from [4 video types](../motive/camera-video-types.md):

* **Tracking:**  Tracking modes capture the 2D marker data used in the reconstruction of 3D data.&#x20;
  * **Object mode:** Performs on-camera detection of centroid location, size, and roundness of the markers, and sends respective 2D object metrics to Motive to calculate the 3D data. Recommended as the default mode for recording.&#x20;
  * **Precision mode:** Performs on-camera detection of marker reflections and their centroids and sends the respective data to Motive to determine the precise centroid location. Precision mode is more processing intensive than Object mode.&#x20;
* **Reference Modes:**  Reference modes capture grayscale video as a visual aid during the take. Cameras in these modes do not contribute to the reconstruction of 3D data.
  * **Grayscale:**  Raw grayscale is intended for aiming and monitoring the camera views and diagnosing tracking problems and includes aiming crosshairs by default. Grayscale video cannot be exported.&#x20;
  * **MJPEG:**  A reference mode that captures grayscale frames, compressed on-camera for scalable reference videos. MJPEG videos can be [exported ](../motive/data-export/#reference-video-export)along with overlay information such as markers, rigid bodies, and skeleton data.&#x20;

#### Hardware Mask

* **Mask Selected:** Mask all the current IR data/reflections for the selected camera.
* **Clear Selected:**  Clear masks from the selected camera's view.
* **Mask Camera Light:**  Mask other cameras in the volume.

#### Orientation

* **Angle:** Change the angle of the camera's view.
* **Auto:**  Automatically change the angle of the camera's view.
* **Clear:** Reset the camera's orientation angle to 0.

#### Frame Delivery Visual

Overlay the frame delivery of each camera in the volume onto the selected camera's view. This information is useful to diagnose latency issues. Straight lines indicate that frames are being delivered at the same time as other cameras. Lines that are wavy or have spikes between cameras point to an issue with synchronization.

![Frame Delivery Info overlay](<../.gitbook/assets/image (659).png>)

#### Correct Camera Position/Orientation

Auto correct the camera's position/orientation. This is often grayed out and is unnecessary for most workflows.

#### Save Image

Save an image of the camera's view as a Bitmap file to a folder called _Screenshots_ in the [currently loaded session folder](data-pane.md#list-of-session-folders).&#x20;

#### Save Image As...

Save an image of the camera's view as a Bitmap file to the file name and location of your choice.

#### Make Reference

Makes the selected camera a reference camera. Set the video type for reference cameras to MJPEG, grayscale, or color video if using a Prime Color Camera. Only MJPEG and Color videos are exportable.&#x20;

## Reference View

Reference View mode is used to monitor captured videos from the reference cameras. Reference cameras must be recording in either MJPEG or color video mode (Prime Color). In this mode, cameras, markers, and trackable assets can be overlaid over the reference view. To monitor the reference view, select one of the cameras and use the Number 3 hotkey to view from the selected camera. All of the assets and trajectory histories under the Perspective view pane can be overlaid on the reference videos.

![Rigid body overlaid on reference view.](<../.gitbook/assets/image (1247).png>) ![Skeleton and force vector overlaid on reference view.](<../.gitbook/assets/image (1216).png>)

![Selecting reference view from the viewport options. Hotkey for this is 3 when a camera is selected.](<../.gitbook/assets/image (1244).png>)

### Export

Reference video can be exported from Motive with the asset overlay. To export, right-click the _Take_ and select Export Video. In the export options, select the assets to overlay in the video. Please see the [Reference Video Export](../motive/data-export/#reference-video-export) section of the [Data Export page](../motive/data-export/) for more information on exporting reference videos.

![Exporting recorded video from Data pane. Click image to enlarge.](<../.gitbook/assets/image (1239).png>) ![Overlay options shown in the video export dialog window. Click image to enlarge.](<../.gitbook/assets/Data Export - Video overlay options (2).png>)

###
