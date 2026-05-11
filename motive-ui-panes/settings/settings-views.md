---
description: Motive's Views Settings defined.
---

# Settings: Views

Use the Application Settings panel to customize Motive and set default values. This page will cover the items available on the View tab. Properties are Standard unless noted otherwise.&#x20;

Please see the following pages for descriptions of the settings on other tabs:

* [Settings: General](settings-general.md)
* [Settings: Assets](settings-assets.md)
* [Settings: Live Pipeline](settings-live-pipeline.md)
* [Settings: Streaming](settings-streaming.md)
* [Settings: Mouse and Keyboard](settings-mouse-and-keyboard.md)
* [Settings: Audio](settings-audio.md)

Application Settings can be accessed from the [View menu](../toolbar-command-bar.md#view) or by clicking the <img src="../../.gitbook/assets/Settings button (10).png" alt="" data-size="line"> icon on the main toolbar.&#x20;

{% hint style="info" %}
**Advanced Settings**

The Settings panel contains advanced settings that are hidden by default. To access these settings, click the <img src="../../.gitbook/assets/Motive Context Menu (25).png" alt="" data-size="line"> button in the top right corner.&#x20;

Use the _Edit Advanced_ option to customize which settings are in the _Advanced Settings_ category and which appear in the standard view, to show only the settings that are needed specifically for your capture application.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Settings - Show or Edit advanced (2).png" alt=""><figcaption><p>Show or Edit Advanced Settings.</p></figcaption></figure>

{% hint style="info" %}
To restore all settings to their default values, select _Reset Settings_ from the Edit menu.
{% endhint %}

## 2D View Settings

The 2D tab of the Views settings contains display settings for the [Cameras View](../viewport.md#cameras-view) in Motive. These are all standard settings.&#x20;

<img src="../../.gitbook/assets/Settings - Views 2D Standard CROPPED.png" alt="2D view settings from the Application Settings panel." width="563">

#### **Background**

(Default: Black) Set the background color of the [Camera View](../viewport.md#cameras-view).

#### **Back-project Selected Markers**

(Default: On) Display yellow crosshairs in the 2D camera view based on the calculated position of the markers selected in the 3D Perspective View.&#x20;

Crosshairs that are not directly over the marker may indicate occlusion or poor camera calibration.

![Markers selected in the perspective view are marked&#x20;
with yellow crosshairs in the Cameras view.](<../../.gitbook/assets/image (864).png>)

#### **Show Camera Filters**

(Default: On) When enabled, the Cameras View displays a red graphic over markers filtered out by the camera's circularity and size filters. This is useful for determining why certain cameras are not tracking specific markers in the view.

![Reflection in Object mode that did not pass the Circle Filter.](<../../.gitbook/assets/image (1423).png>) ![Grayscale view of the filtered reflection.](<../../.gitbook/assets/image (1414).png>)

## 3D View Settings

The 3D tab contains display settings for the [Perspective View](../viewport.md#perspective-view) in Motive. Settings are Standard unless noted otherwise.&#x20;

<img src="../../.gitbook/assets/Settings - Views 3D Standard (1).png" alt="3D view settings from the Application Settings panel." width="563">

### Basic 3D Settings

This section contains settings that control the look of the 3D Perspective View. All are standard settings.

#### **Background**

(Default: black) Set the background color of the Perspective View.

#### **Fog Effect**

(Default: off) Turn on a gradient “fog” effect.

#### **Grid Color**

(Default: white) Set the color of the ground plane grid.

#### **Grid Width**

(Default: 6 meters) Set the width, in meters, of the ground plane grid.

#### **Grid Length**

(Default: 6 meters) Set the length, in meters, of the ground plane grid.

#### **Floor Plane**

(Default: off) Display the floor plane in the Perspective View. When disabled, only the floor grid is visible.

#### Floor Plane Color

(Default: gray) Set the color for the floor plane. This option is only available when the Floor Plane setting is enabled.

#### **Selection Color**

(Default: yellow) Set the color of selected objects in the 3D Viewport. This color is applied to secondary items when multiple items are selected.

#### Primary Selection Color

(Default: cyan) Set the color of the primary selected object in the 3D Viewport. When multiple objects are selected, the primary selection is the object that was selected last.&#x20;

### Heads Up Display

Settings in this section determine which informational overlays to include in the 3D Viewport. All settings are standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/Settings - Views 3D Heads Up Display.png" alt="" width="404"><figcaption><p>Applications Settings:  Views - 3D Tab Heads Up Display.</p></figcaption></figure>

#### **Coordinate Axis**

(Default: on) Display the coordinate axis in the lower left corner. This overlay can also be toggled on or off from the Visuals menu <img src="../../.gitbook/assets/Viewport Visual Options button (6).png" alt="" data-size="line"> in the 3D Viewport.

#### **Timecode**

When using an external timecode signal through an eSync device, this setting determines where to display the timecode:

* Show in 3D View:  Display the timecode at the bottom of the 3D Viewport. This is the default setting.
* Show in Control Deck:  Display the timecode in the control deck below the 3D Viewport.&#x20;
* Do not Show:  Hide the timecode.&#x20;

#### **Precision Timestamp&#x20;**_**(Advanced)**_

Determine where to display the timecode for Precision Time Protocol (PTP) devices, if in use:

* Show in 3D View:  Display the PTP timecode at the bottom of the 3D Viewport.
* Show in Control Deck:  Display the PTP timecode in the control deck below the 3D Viewport.&#x20;
* Do not Show:  Hide the PTP timecode. This is the default setting.

#### **Marker Details**

(Default: on) Show marker count details in the bottom-right corner:

* Total markers tracked
* Total markers selected

This overlay can also be toggled on or off from the Visuals menu <img src="../../.gitbook/assets/Viewport Visual Options button (6).png" alt="" data-size="line"> in the 3D Viewport.

#### **OptiTrack Logo**

(Default: off) Display the OptiTrack logo in the top right corner.&#x20;

#### **Frame Rate**

(Default: off) Display the refresh rate in the top left corner.

### Markers

Settings in this section determine how markers are displayed in the 3D Viewport. All settings are standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/Settings - Views 3D Markers.png" alt="" width="450"><figcaption><p>Applications Settings:  Views - 3D Tab, Markers settings.</p></figcaption></figure>

#### **Size**

(Default: custom) Determine whether markers are represented by the calculated size or overwritten with a set diameter (custom).

#### **Custom Size**

(Default: 14mm) Determines the fixed diameter of all 3D markers when the marker Size is set to _Custom_.

#### **Labeled**

(Default: white) Set the color for labeled markers. Markers labeled using either a Rigid Body or Skeleton solve are colored according to their asset properties.

#### **Passive**

(Default: white) Set the color for passive markers. Retro-reflective markers or continuously illuminating IR LEDs are recognized as passive markers in Motive.

#### **Active**

(Default: cyan) Set the color for [active markers](../../active-components/active-marker-tracking/).

#### Intermediate _(Advanced)_

(Default: white) Set the color for active markers that have yet to be identified in Motive. The marker color will change to the Active color once the marker is identified.&#x20;

{% hint style="info" %}
To adjust the number of frames it takes for Motive to identify an active marker, go to [_Settings -> Live Pipeline -> Solver -> Live Pipeline Presets -> Active Pattern._ ](settings-live-pipeline.md#active-pattern-depth)
{% endhint %}

#### **Measurement**

(Default: white) Set the color for measurement points created using the [Measurement Probe](../../motive/measurement-probe-kit-guide.md).&#x20;

{% hint style="info" %}
The Measurement Probe is used to collect the x/y/z coordinates of a fixed point in the capture volume that is not linked to a physical marker.
{% endhint %}

#### Solved Asset Marker Opacity

(Default: 70) Set the opacity level for markers in a solved asset. Lower values reduce the brightness and color of the markers in the 3D Viewport.

#### Label Visual

Determine whether marker labels displayed in the 3D Viewport will include the Asset name (the default setting) or just the marker label name.&#x20;

#### **Marker Info**

(Default: off) Display the 3D positions and estimated diameter of selected markers. If the marker label visual is also enabled, the marker info will display at the end of the label.&#x20;

<img src="../../.gitbook/assets/Settings - Views 3D Marker Info.png" alt="A Solved Rigid Body with Marker History displayed
for the selected marker." width="335">

#### **Marker History**

(Default: on) Display a trail to show the history of marker positions over time. When the marker is selected, the trail will use the color chosen in the Selection Color setting (yellow by default). The trail for unselected markers will follow the color of the marker itself.&#x20;

#### **Only Selected History**

(Default: on) When marker history is selected, this setting restricts the marker history trails to only the markers selected in the 3D Viewport.

#### **History Length**

(Default: 250) Set the number of past frames to include in the marker history.

#### Untracked Stick Opacity

(Default: 50) Set the opacity level for marker sticks when their markers are not being tracked. Lower values reduce the brightness and color of the sticks in the 3D Viewport.

### Cameras

Settings in this section determine how cameras are displayed in the 3D Viewport. All settings are standard.&#x20;

<figure><img src="../../.gitbook/assets/Settings - View 3D Cameras.png" alt="" width="335"><figcaption><p>Applications Settings:  Views - 3D Tab, Cameras settings.</p></figcaption></figure>

#### **Tracking**

(Default: teal) Set the color of tracking cameras in the 3D Perspective View. Tracking cameras are set to [Object mode or Precision mode](../../motive/camera-video-types.md).

#### **Reference**

(Default: magenta) Set the color of reference cameras in the 3D Perspective View. Reference cameras are set to capture MJPEG grayscale videos or color videos (Prime Color series).

#### Camera Partitions

(Default: off) Use color to distinguish cameras by partitions rather than function.&#x20;

### Rays

Cameras detect reflected rays of infrared light to track objects in the capture volume. Settings in this section determine how camera rays are displayed in the 3D Viewport. All settings are standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/Settings - Views 3D Rays.png" alt="" width="377"><figcaption><p>Applications Settings:  Views - 3D Tab, Rays settings.</p></figcaption></figure>

#### **Tracked**

(Default: green) Set the color for Tracked Rays, which are rays that connect a camera to a marker.

#### **Unlabeled&#x20;**_**(Advanced)**_

(Default: green) Set the color for rays that are tracked but connect to unlabeled markers.

#### **Untracked**

(Default: red) Set the color for untracked rays, which are rays that do not connect to a marker.

#### All Tracked Rays _**(Advanced)**_

(Default: off) Display all tracked rays. Additional options to display tracked rays are available from the [Visual Aids ](../viewport.md#visual-aids)Menu in the 3D Viewport. Click the <img src="../../.gitbook/assets/Viewport Visual Options button (8).png" alt="" data-size="line"> button and select Tracked Rays to see more.&#x20;

### Capture Volume

The 3D Viewport Visual Aids includes an option to view the Capture Volume. Settings in this section determine how the Capture Volume visual displays. All settings are standard.&#x20;

<figure><img src="../../.gitbook/assets/Settings - Views 3D Capture Volume.png" alt="" width="417"><figcaption><p>Applications Settings:  Views - 3D Tab, Capture Volume settings.</p></figcaption></figure>

#### **Color**

(Default: checkered blue) Set the color used to visualize the capture volume.&#x20;

#### **Overlap**

(Default: 3) Set the minimum number of cameras required to form a field of view (FOV) overlap when visualizing the parameters of the capture volume.

## Graphs View Settings

The Graphs tab under the Views settings contains display settings for the [Graph Pane](../graph-view-pane.md). These are all standard settings.&#x20;

<figure><img src="../../.gitbook/assets/Settings - View Graphs Default values.png" alt=""><figcaption><p>Applications Settings:  Views - Graph Tab, All settings.</p></figcaption></figure>

#### **Color Scheme**

(Default: dark) Set the color to use for the plot guidelines.

#### **Background**

(Default: black) Set the background color to use for the plots.

#### **Autoscale**

(Default: on) When enabled, the y-axis of each plot will autoscale to fit all the data in the view, and zoom automatically for best visualization. For fixed y-plot ranges, this setting can be disabled. See the [Graph View pane](../graph-view-pane.md) page for more information.

#### **Preferred Live Layout**

(Default: _none_) Preferred [graph layout](../graph-view-pane.md#layouts) used for Live mode. Enter the name of the layout you wish to use exactly as it appears on the layout menu. Both System layouts and User layouts can be used.&#x20;

#### **Preferred Edit Layout**

(Default: _none_) Preferred [graph layout](../graph-view-pane.md#layouts) used for Edit mode. Enter the name of the layout you wish to use exactly as it appears on the layout menu. Both System layouts and User layouts can be used.&#x20;

<figure><img src="../../.gitbook/assets/Settings - Views  Graphs with Preferred Graph layouts.png" alt=""><figcaption><p>Applications Settings:  Views - Graph Tab, with Preferred Layouts selected.</p></figcaption></figure>

{% hint style="info" %}
Graph layouts are .xml files saved in **C:\ProgramData\OptiTrack\Motive\GraphLayouts.**&#x20;

You can copy the .xml files to your project folders for sharing and later use. Copy them back into the _GraphLayouts_ folder when needed to make them available in Motive.&#x20;
{% endhint %}

#### **Scope Duration**

(Default: 1000) The scope, in frames, of the domain range used for plotting graphs.

![Plotting 6 DoF data for a Rigid Body in the Graph View pane.](<../../.gitbook/assets/image (340).png>)
