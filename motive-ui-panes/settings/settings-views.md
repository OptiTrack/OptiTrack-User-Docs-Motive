# Settings: Views

In Motive, the Application Settings can be accessed under the [View tab](../toolbar-command-bar.md#view) or by clicking [![Toolbar AppSettings 20.png](https://v30.wiki.optitrack.com/images/8/8e/Toolbar_AppSettings_20.png)](https://v30.wiki.optitrack.com/index.php?title=File:Toolbar_AppSettings_20.png) icon on the main toolbar. Default Application Settings can be recovered by Reset Application Settings under the Edit Tools tab from the main [Toolbar](../toolbar-command-bar.md).

## 2D View Settings

2D tab under the view settings lists out display settings for the [Camera View](../viewport.md#cameras-view) in Motive.

#### **Background**

Sets the background color of the [Camera View](../viewport.md#cameras-view).

#### **Backproject Selected Marker**

Enables markers selected from the 3D Perspective View to be also highlighted with yellow crosshairs in the 2D camera view, based on calculated position. Crosshairs that are not directly over the marker tend to indicate occlusion or poor camera calibration.

![2D view settings from the Application Settings panel.](<../../.gitbook/assets/image (371).png>)

![Markers selected in the perspective view get marked with yellow crosshairs.](<../../.gitbook/assets/image (473).png>)

#### **Show Camera Filters**

When enabled, Camera View shows which markers have been filtered out by the camera's circularity and size filter. This is enabled by default and is useful for inspecting why certain cameras are not tracking a specific markers in the view.

![Reflection seen from a camera that has been filtered by circle.](<../../.gitbook/assets/image (328).png>) ![Grayscale view of the filtered reflection.](<../../.gitbook/assets/image (331).png>)

## 3D View Basic Settings

3D tab under the view settings lists out display settings for the [Perspective View](../viewport.md#perspective-view) in Motive.

![3D view settings from the Application Settings panel.](<../../.gitbook/assets/image (468).png>)

#### **Background**

Sets the background color of the Perspective View.

#### **Fog Effect**

Turns a gradient “fog” effect on in the Perspective View.

#### **Grid Color**

Selects the color of the ground plane grid in the Perspective View.

#### **Grid Size**

Selects the size of the ground plane grid in the Perspective View. Specifically, it sets the number of grids along the positive and negative direction in both the X and Z axis. Each grid represents 20cm x 20cm in size within a calibrated volume.

#### **Floor Plane**

When enabled, Motive will display the floor plane in the Perspective View. This is disabled by default to only show the floor grid.

#### **Selection Color**

Sets the color of selections in the 3D view port.

### Heads Up Display

#### **Coordinate Axis**

Displays the coordinate axis in the 3D view port.

#### **Timecode**

Determines where timecode gets displayed in Motive. Timecode can be displayed either on the Perspective View or the Control Deck or hidden entirely. Timecode will be available only when the timecode signal is inputted through the eSync.

#### **Marker Details**

Show or hide marker count report located at the bottom-right corner of the Perspective View.

#### **OptiTrack Logo**

Overlays the OptiTrack logo over top of the Perspective View.

#### **Frame Rate**

Overlays refresh rate of the display on the Perspective View.

### Markers

#### **Size**

Determines whether marker sizes in the 3D Perspective View are represented by the calculated size or overwritten with a set diameter.

#### **Custom Size**

When the Marker Size setting above is set to _Custom_, the diameter of the 3D markers will all be fixed to the inputted diameter.

#### **Passive**

Sets the color for passive markers in the 3D viewport. Retro-reflective markers or continuously illuminating IR LEDs will be recognized as passive markers in Motive.

#### **Active**

Sets the color for [active markers](../../active-components/active-marker-tracking/) in the 3D viewport.

#### **Measurement**

Sets the color for measurement markers that are sampled using the [Measurement Probe](../../motive/measurement-probe-kit-guide.md).

#### **Marker Info**

When this is set to true. 3D positions and estimated diameter of selected markers will be displayed on the 3D viewport.

![](<../../.gitbook/assets/image (326).png>)

#### **Marker History**

Displays a history trail of marker positions over time.

#### **Only Selected History**

When both the marker history and this setting is enabled, marker history trail will be shown for only selected markers in the viewport.

#### **History Length**

Number of past frames for showing the marker history.

### Cameras

#### **Tracking**

Sets the color of tracking cameras in the 3D Perspective View. Cameras that are set to [Object mode or Precision mode](../../motive/camera-video-types.md) will be considered as tracking cameras in Motive.

#### **Reference**

Sets the color of reference cameras in the 3D Perspective View. Cameras that are capturing reference MJPEG grayscale videos or color videos, for Prime Colors, will be considered as reference cameras.

### Rays

#### **Tracked**

Sets the color for Tracked Rays in the 3D Perspective View.

#### **Unlabeled**

Sets the color for unlabeled rays in the 3D Perspective View.

#### **Untracked**

Sets the color for untracked rays in the 3D Perspective View.

### Capture Volume

#### **Color**

Sets the color used for visualizing the capture volume.

#### **Overlap**

Minimum number of cameras required for their FOV to overlap when visualizing the capture volume.

## 3D View Advanced Settings

### Markers

#### **Labeled**

Sets the color for labeled markers. Markers that are labeled using either Rigid Body or Skeleton solve will be colored according to their asset properties.

### Rays

#### Unlabeled

Shows rays stemming from camera to markers that have not been labeled.

#### All Tracked Rays

Displays all tracked rays.

## Graphs View Settings

![Plotting 6 DoF data for a Rigid Body in the Graph View pane.](<../../.gitbook/assets/image (325).png>)

#### **Color Scheme**

Colors used for plot guidelines in the [Graph View pane](../graph-view-pane.md).

#### **Background**

Background color used for the plots.

#### **Autoscale**

When enabled, y-axis of each plot will autoscale to fit all the data in the view. It will also zoom automatically for best visualization. For fixed y-plot ranges, this setting can be disabled. See [Graph View pane](../graph-view-pane.md) for more information.

#### **Preferred Live Layout**

Preferred [graph layout](../graph-view-pane.md#layouts) used for Live mode.

#### **Preferred Edit Layout**

Preferred [graph layout](../graph-view-pane.md#layouts) used for Edit mode.

#### **Scope Duration**

The scope of domain range, in frames, used for plotting graphs.
