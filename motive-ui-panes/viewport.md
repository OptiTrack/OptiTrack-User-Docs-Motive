# Viewport

When using Motive, the main View pane will always be docked in the center. One Viewer pane can be divided up to four viewports, and if desired, additional Viewer panes can be opened under the [View tab](toolbar-command-bar.md#view) or by clicking the <img src="../.gitbook/assets/image (141).png" alt="" data-size="line"> icon on the main toolbar.

## Viewport Control

The following actions are useful for when navigating using the viewport. All of the mouse actions and keyboard hotkeys can be customized in the [Application Settings: Keyboard](settings/settings-mouse-and-keyboard.md) panel.

### Mouse Control

| Function                 | Default Control             |
| ------------------------ | --------------------------- |
| Rotate view              | Right + Drag                |
| Pan view                 | Middle (wheel) click + drag |
| Zoom in/out              | Mouse Wheel                 |
| Select in View           | Left mouse click            |
| Toggle Selection in View | CTRL + left mouse click     |

### Keyboard Control

| Function                   | Default Control                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Switch to Perspective View | Number 1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Switch to Camera View      | Number 2                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Switch to Reference View   | Number 3, while a camera is selected                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Split View                 | <p>Shift + 1: Show only one viewport</p><p><br>Shift + 2: Split the viewport into two horizontally</p><p><br>Shift + 3: Split the viewport into two vertically</p><p><br>Shift + 4: Split the Viewport into four</p><p><br><em>Additional options are available from</em> <a href="https://v30.wiki.optitrack.com/index.php?title=File:ContextMenu_dotdotdot.png"><img src="https://v30.wiki.optitrack.com/images/c/c4/ContextMenu_dotdotdot.png" alt="ContextMenu dotdotdot.png"></a> <em>icon on the top-right corner.</em></p> |
| Zoom                       | <p>F: Quickly zoom into a selected object(s) or camera(s) in the view.<br><br>Shift + F: Quickly zoom out to fit everything into the view.</p>                                                                                                                                                                                                                                                                                                                                                                                    |

## Perspective View

![3D Perspective View.](<../.gitbook/assets/image (945).png>)

### Toolbar Options

#### **Mouse Interactions** ![](<../.gitbook/assets/image (956).png>)

![Mouse action options.](<../.gitbook/assets/image (1029).png>)

From this icon, you can switch between different mouse interaction modes in the 3D viewport. You can either use the mouse actions to select objects in the scene, translate, rotate, scale assets, or use the Quick Label mode for labeling.

* **Select**: In selection mode, you can any objects in the scene, and their properties will be shown in the [Properties pane](properties-pane/).
* **Translate**: In translate mode, you can apply a translation to Rigid Body pivot points and Skeleton bones. In recorded data, you can also select a group of reconstructed 3D markers in the scene and apply translation along the global x-y-z axis. When the change is made to a Skeleton, the segment hierarchy will be modified and reflected on exported Skeleton bone data but the marker locations will remain the same.
* **Rotate**: In rotate mode, you can apply rotation to Rigid Body pivot points and Skeleton bones.
* **Scale**: In scale mode, you can scale the length of Skeleton bones or scale the size of the [geometry model](properties-pane/properties-pane-rigid-body.md#attached-geometry) attached to a Rigid Body.
* **Quick Label**: In [QuickLabel mode](../motive/labeling.md#quicklabel-mode), you can quickly reassign marker labels in the post-processing of recorded data.
* **Local Coordinates**: When enabled, translation, rotation, and scaling changes will be applied with respect to the local coordinate axis of the selected asset. When disabled, all changes will be applied to the global coordinate axis.
* **Symmetric Bones**: When enabled, any modifications on bone lengths and orientations are applied symmetrically on both the left and right side of a Skeleton.

#### **Zoom Actions** ![](<../.gitbook/assets/image (1023).png>)

Actions for zooming into a selected object or zooming out to fit all. You can also use "F" and "Shift + F" hotkeys for this.

**Visual Aids** ![](<../.gitbook/assets/image (1035).png>)

![Mouse action options.](<../.gitbook/assets/image (964).png>)

Opens a context menu to enable or disable visuals in the perspective viewports. From this menu, you can show or hide markers, marker labels, Rigid Bodies, Skeletons, tracked rays, and more.

_Visible_

Show, or hide, markers, cameras, or different types of assets from the perspective view. You can also hide Asset Model markers which are the expected marker positions that allow auto-labeling of markers for the assets.

_Marker_

* Labels: Show, or hide, marker labels for each marker on the perspective viewport
* Info: Show, or hide, marker info from the perspective view. Marker info includes x/y/z coordinate as well as the diameter of the marker.
* Color: When checked, Rigid Body and/or Skeleton markers will be colored according to the color of the related Rigid Body and/or Skeleton asset.
* Sticks: Show, or hide, Skeleton marker sticks from the perspective view. [Marker sticks](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#marker-colors-and-marker-sticks) help users to easily interpret the Skeleton marker labels from the viewport.
* History: Show, or hide, marker trajectory history from the perspective view.
* Distance: Show, or hide, marker distance information when two markerrs are selected in the perspective viewport.
* Angle: Show, or hide, angle information when three markers are selected in the perspective viewport.

_Rays_

* Tracked Rays: Show/Hide Tracked Rays from the view. Tracked rays are the marker centroid rays (available only in 2D data) from each camera that contributes to the 3D reconstruction.
* Untracked Rays: Show/Hide Untracked Rays from the view. Untracked Rays are the marker centroid rays (available only in 2D data) that are seen by each camera but does not contribute to the 3D reconstructions because the reconstruction requirements, usually the ray count, are not met.

_Heads Up Display_

* Marker Count: Show/Hide reconstructed and selected marker counts at the bottom-right corner of the view.
* Coordinate Axis: Show/Hide global coordinate axis at the left-bottom corner of the 3D view.

#### **Selection Lock** ![](<../.gitbook/assets/image (940).png>)

This tool locks the camera into the selected object(s) in the 3D perspective view, and the viewport will follow the selected object throughout the capture. For example, you can select a Rigid Body in the view, lock the selection, focus zoom into the object (Hotkey: F) have Motive follow the object.

#### **Selection** ![](<../.gitbook/assets/image (959).png>)

Enables, or disables, selection of specific objects in the 3D view. Only the items checked in the menu will be selectable in the perspective view.

## Cameras View

![](<../.gitbook/assets/image (971).png>)

### Hotkeys

| Function                                 | Default Control                                                                                                                              |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Switch selected cameras to Object mode   | O                                                                                                                                            |
| Switch selected camera to MJPEG mode     | I                                                                                                                                            |
| Switch selected camera to Grayscale mode | U                                                                                                                                            |
| Zoom                                     | <p>F: Quickly zoom into a selected camera(s) in the view.</p><p><br>Shift + F: Quickly zoom out to fit all of the cameras into the view.</p> |

### Toolbar Options

#### **Mouse Actions** ![](<../.gitbook/assets/image (1017).png>)

![Pixel inspector enabled in 2D view.](<../.gitbook/assets/image (1028).png>)

From this icon, you can switch between different mouse interaction modes in the camera viewport. In addition to simple Select mode, you can switch to the Pixel Inspector mode to check the brightness of individual pixels in the grayscale mode for inspecting the camera view, or you can also add/remove masking from the camera view.

_Pixel Inspection_

In pixel inspection mode, the viewport displays X,Y coordinates of the cursor location when hovering over a camera, and pixel brightness for selected pixels when a region is drag-selected. Inspecting pixel brightness can be useful during camera focusing, tuning, and aiming.

#### **Zoom Actions** ![](<../.gitbook/assets/image (961).png>)

Zoom to All: Zooms all cameras to fit the pane. (default hotkey: Shift + F)

Zoom to Selection: Zooms into selected cameras to fit the pane. (default hotkey: F)

#### **Visual Aids** ![](<../.gitbook/assets/image (1011).png>)

![Camera viewport visual aid options.](<../.gitbook/assets/image (982).png>)

Show or hide additional camera information from the camera viewport.

* Reticles: Show/Hide marker reticles to indicate where the reconstructed markers are located in respect to the camera view.
* Camera Info: Show/Hide camera specific information, including camera models, camera setting values, time, data transfer rate, frame ID, and sync methods. For Prime series cameras, image board temperature information will also be available. If there is any synchronization or hardware issues, they will also be indicated in the camera info.

_Markers_

* Coordinates: Show/Hide (x,y) coordinate information for the reflections that satisfy the 2D object filter.
* Centroids: Show/Hide centroid crosshairs for the reflections that satisfy the 2D object filter.
* Circularity: Show/Hide circularity value label for detected reflections. The label will appear red if the reflection does not satisfy the 2D filter setting.
* Size: Show/Hide number of pixels involved in each reflection. The label will appear red if the reflection does not satisfy the 2D filter setting.
* Labels: Shows whether the markers detected in the camera view is passive retroreflective marker or active markers. When the camera is detecting an active LED marker(s) corresponding label ID for each marker will be shown.

#### **Camera Masking Settings** ![](<../.gitbook/assets/image (1030).png>)

Using the masking settings context menu, you can re-apply auto-masking feature, clear masks, and/or perform other actions related to applying masks in the camera view.

* Mask All: Apply auto-masking to all of the connected cameras.
* Mask Selected: Apply auto-masking to only the selected cameras.
* Masking is Additive: When this is checked, all of the masks will be applied additively over the existing masks.
* Clear All: Clears all masks from the camera view.
* Clear Selected: Clears masks from selected cameras only.

### Right Click on Camera Settings

![Right clicking on camera in Camera Viewport opens this window to quickly change camera properties.](<../.gitbook/assets/image (5) (2) (1).png>)

#### Video Type

Select from the 4 video types:

* Object
* Precision
* Grayscale
* MJPEG

#### Hardware Mask

Mask Selected - Masks all the current IR data/reflections for camera selected

Clear Selected - Clears masks from the selected camera's Camera view

Mask Camera Light - Masks other camera's in the volume

#### Orientation

Angle - Changes the angle of the camera's view

Auto - Automatically changes the angle of the camera's view

Clear - Resets the orientation angle to 0

#### Frame Delivery Visual

This setting when selected overlays the frame delivery of each camera in the volume onto the selected camera's camera view. This information is useful to diagnose latency issues. The closer the lines are to straight, this means the frames are being delivered at the same time as other cameras. If, however, the lines are wavy or have spikes between cameras, this is an indication of an issue with synchronization.

![Frame Delivery Info overlay](<../.gitbook/assets/image (2) (2) (1).png>)

#### Correct Camera Position/Orientation

Auto corrects the camera's position/orientation. Typically this will be grayed out and is unnecessary for most workflows.

#### Save Image As...

Saves image of the camera's view as a Bitmap file.

#### Make Reference

Makes the selected camera a reference camera. You'll want to switch this camera to either MJPEG, grayscale, or color video (Prime color). See section below for more information.

## Reference View

The Reference View mode is used to monitor captured videos from the reference cameras. In order to view the reference view, the cameras must be recording either MJPEG, grayscale, or color video mode (Prime Color). In this mode, cameras, markers, and trackable assets can be overlaid over the reference view. To monitor the reference view, select one of the cameras and use Number 3 hotkey to view from the selected camera. This is a good way of monitoring events during the capture. All of the assets and trajectory histories under the Perspective view pane can be overlaid on the reference videos from this pane.

![Rigid body overlaid on reference view.](<../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png>) ![Skeleton and force vector overlaid on reference view.](<../.gitbook/assets/image (88).png>)

![Selecting reference view from the viewport options. Hotkey for this is 3 when a camera is selected.](<../.gitbook/assets/image (17) (1).png>)

### Export

Reference video can also be exported from Motive with the asset overlay. To export, simply right-click on the _Take_ that contains reference videos. Then select Export Video to export the video files. Then in the export options, you can select which assets to overlay in the video.

![Exporting recorded video from Data pane. Click image to enlarge.](<../.gitbook/assets/image (98).png>) ![Overlay options shown in the video export dialog window. Click image to enlarge.](<../.gitbook/assets/image (71).png>)

## Viewport Context Menu

### Selection: Camera

![Viewport context menu when a camera is selected.](<../.gitbook/assets/image (41).png>)

The following context menu appears when a camera is selected either in the perspective view or in the camera preview.

* **Video Type**: Sets [video types](../motive/camera-video-types.md) of the selected cameras.
* **Hardware Mask**: Sets masking of the selected cameras. You can apply auto-masks or clear existing masks.
* **Orientation**: Adjust display orientation of a camera in the 2D camera preview. It can be manually configured or set to a calculated orientation which is obtained from the system calibration.
* **Frame Delivery Visual**: Shows frame delivery graph for debugging camera synchronization problems. Available only in Cameras Viewport when in Live mode.
* **Save Image As...**: Saves the 2D view of the selected camera into a bitmap image.
* **Make Reference**: Switches the camera into reference mode for monitoring grayscale video and applying asset overlay. Available only in Cameras Viewport when in Live mode.
* **Zoom to All**: Zoom to fit all of the cameras in the viewport.
* **Zoom to Selection**: Zoom into the selected camera in the viewport.

### Selection: Markers

![Camera preview context menu.](<../.gitbook/assets/image (8) (1) (2).png>)

The following context menu appears when 3D reconstructed markers are selected in the perspective view.

* **Create** Marker Sets: Create a [Marker Set](../motive/labeling.md), a list of marker labels, from the selected markers for manual labeling on recorded data.
* **Create Rigid Body**: Create a [Rigid Body](builder-pane.md#rigid-body-create) asset from selected markers for tracking a markered object in the scene.
* **Create Skeleton**: Create a [Skeleton](builder-pane.md#Skeleton-create) asset from selected markers. When a group of marker is selected, matching Skeleton template will be listed next to this option.
* **Unlabel**: When marker label is already assigned, the assigned label can be removed using this option in the recorded data.

### Selection: Rigid Body

![Viewport context menu when a Rigid Body is selected.](<../.gitbook/assets/image (59).png>)

The following context menu appears when a Rigid Body is selected in the perspective view.

* **Reset Pivot**: Repositions the Rigid Body pivot point at the center of a Rigid Body.
* **Markers**: When a marker(s) is selected along with a Rigid Body, you can use this option to assign pivot point to a specific marker, or add/remove markers from the selected Rigid Body asset.
* **Make Reference**: Switch the viewport so that it looks at the perspective of the Rigid Body in the direction of its Z-axis.
* **Delete**: Delete the selected Rigid Body.

### Selection: Skeleton

![Viewport context menu when a Skeleton is selected.](<../.gitbook/assets/image (22) (1).png>)

The following context menu appears when a Skeleton asset is selected in the perspective view.

* **Recalibrate Skeleton**: Re-calibrate the Skeleton from its markers using the same Skeleton template.
* **Markers**: Add or remove selected Skeleton marker from the Skeleton asset definition.
* **Delete**: Delete selected Skeletons.

### Selection: Force Plate

![Camera preview context menu.](<../.gitbook/assets/image (97).png>)

The following context menu appears when a force plate is selected in the perspective view.

* **Set Position**: Repositions a force plate asset according to the location of the calibration square. This is used to calibrate the position of a selected force plate within Motive. For more information: [Force plate setup](../movement-sciences/) page.
* **Zero (all)**: Zeroes, or tares, all selected force plates.
* **Re-Sync (all)**: For triggered synchronization protocols, (e.g. force plates that syncs using the record trigger), this feature re-synchronizes force plates with the camera system. This will remove any sync offsets that may have increased gradually since the trigger.
