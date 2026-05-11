---
description: Instructions and tips on using the Graph View pane to visualize tracking data.
---

# Graph View Pane

## Overview

The Graph View pane allows you to visualize and monitor multiple data channels, in both Live and Edit mode.&#x20;

In **Live Mode**, the following data can be plotted in real-time:

* Rigid body 6 DoF data (Position and Orientation)
* IMU data (Orientation)
* Force Plate Data (Force and Moment)
* Analog Data
* Telemetry Data

In **Edit Mode**, graphs are used to review and post-process the captured data. In addition to the graphs available in Live mode, edit mode includes the ability to graph 3D positions of reconstructed markers.

In addition to the standard graph [layouts ](graph-view-pane.md#layouts)(channel, combined, tracked), the user can create custom layouts to monitor specific data channels only. Motive allows up to 9 graphs plotted in each layout and up to two graph view panes to be opened simultaneously.

### Pane Layout

To open a Graph View pane, click either the <img src="../.gitbook/assets/Graph Pane 1 Button.png" alt="" data-size="line"> or the <img src="../.gitbook/assets/Graph Pane 2 Button.png" alt="" data-size="line"> icon on the main toolbar, or select _Graph 1_ or _Graph 2_ from the View menu.&#x20;

Select a marker, bone, or asset in the 3D Viewport to display its data on the graph.&#x20;

![](<../.gitbook/assets/Graph View Pane Annotated.png>)

### Toolbar

![](<../.gitbook/assets/image (416).png>)

| Icon                                                                                         | Name                                   | Description                                                                                                                                                                                                                             |
| -------------------------------------------------------------------------------------------- | -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](<../.gitbook/assets/image (420).png>)                                                    | Graph Editor                           | Opens the Data and Visuals sidebar to customize a selected graph within a layout.                                                                                                                                                       |
| ![](<../.gitbook/assets/image (432).png>)                                                    | Auto Extents                           | Toggle to autoscale X/Y/Z graphs.                                                                                                                                                                                                       |
| ![](<../.gitbook/assets/image (360).png>)                                                    | <p>Zoom Fit</p><p>(selected range)</p> | Zooms into selected frame region and centers the timeline accordingly.                                                                                                                                                                  |
| ![](<../.gitbook/assets/image (445).png>)                                                    | Lock Cursor Centered                   | Locks the timeline scrubber at the center of the view range.                                                                                                                                                                            |
| ![](<../.gitbook/assets/image (357).png>)                                                    | Delete Selected Keys                   | Deletes the selected frame region.                                                                                                                                                                                                      |
| ![](<../.gitbook/assets/image (433).png>)                                                    | Move Selected Keys                     | Translates trajectories in selected frame region. Select a range and drag up and down on a trajectory.                                                                                                                                  |
| ![](<../.gitbook/assets/image (384).png>)                                                    | Draw Keys                              | Manually draw trajectory by clicking and dragging a selected trajectory in the Editor.                                                                                                                                                  |
| ![](<../.gitbook/assets/image (376).png>)                                                    | Merge Keys Up                          | Merges two trajectories together. This feature is useful when used with the [Tracks View](graph-view-pane.md#tracks-view) graphs. Select two trajectories and click this button to merge the bottom trajectory into the top trajectory. |
| ![](<../.gitbook/assets/image (391).png>)                                                    | Merge Keys Down                        | Merges two trajectories together. This feature is useful when used with the [Tracks View](graph-view-pane.md#tracks-view) graphs. Select two trajectories and click this button to merge the top trajectory into the bottom trajectory. |
| ![](<../.gitbook/assets/image (363).png>)                                                    | Lock Selection                         | Locks the current selection (marker, Rigid Body, Skeleton, force plates, or NI-DAQ) onto all graphs on the layout. This is used to temporarily hold the selections.                                                                     |
| <img src="../.gitbook/assets/Graph Pane - Layout displayed.png" alt="" data-size="original"> | Select Layout                          | Displays the name of the system or user defined [Layout ](graph-view-pane.md#layouts)currently in use. When clicked, opens the Layout menu.                                                                                             |
| <img src="../.gitbook/assets/Motive Context Menu (28).png" alt="" data-size="line">          | Context Menu                           | Opens the Pane Options menu.                                                                                                                                                                                                            |

### Pane Options Menu&#x20;

Click the <img src="../.gitbook/assets/Motive Context Menu (6).png" alt="" data-size="line"> context menu button in the top right corner of the Graph View pane to select layout options.&#x20;

![Graph View pane menu.](<../.gitbook/assets/Graph Pane - Layout Menu.png>)

#### **Create Layout**

Creates a new graph layout.

#### Clone Layout

Creates a new graph layout based on the current layout.&#x20;

#### **Delete Layout**

Deletes the current graph layout.

#### **Update Layout**

Saves the changes to the graph layout XML file.

#### **Particularize Layout**

Takes an XML snapshot of the current graph layout. Once a layout has been particularized, both the layout configuration and the item selection will be fixed and it can be exported and imported onto different sessions.

#### **Show File Location**

Opens the file location where the XML files for the graph layouts are stored.

## Graph Navigation

### Navigating from the Graph

#### **Navigate Frames (Alt + Left-click + Drag)**

Alt + left-click on the graph and drag the mouse left and right to navigate through the recorded frames. You can do the same with the mouse scroll wheel as well.

#### **Pan (Scroll-click + Drag)**

Scroll-click and drag to pan the view vertically and horizontally throughout plotted graphs. Dragging the cursor left and right will pan the view along the horizontal axis for all of the graphs. When navigating vertically, scroll-click on a graph and drag up and down to pan vertically for the specific graph.

#### **Zoom (Right-click + Drag)**

Right-click and drag on a graph to free-form zoom in and out on both vertical and horizontal axis. If the _Auto Extents Graph_ <img src="../.gitbook/assets/image (49).png" alt="" data-size="line">  is enabled, the vertical axis range will be fixed according to the max and min value of the plotted data.

{% hint style="info" %}
**Other Ways to Zoom:**

* Press _Shift + F_ to zoom out to the entire frame range.
* To zoom into a frame range,  _Alt + right-click_ on the graph and select the specific frame range to zoom into.
* When a frame range is selected, press _F_ to zoom to the selected range in the timeline.
{% endhint %}

#### **Select Frame Range (Left-click + Drag)**

Frame range selection is used when making post-processing edits to specific ranges of the recorded frames. Select a range by left-clicking and dragging the mouse left or right. The selected frame ranges are highlighted in yellow. You can also select more than one frame ranges by shift-selecting multiple ranges.

### Navigation Bar

#### **Navigate Frames (Left-click)**

Left-click and drag on the navigation bar to scrub through the recorded frames. You can do the same with the mouse scroll as well.

#### **Pan View Range**

Scroll-click and drag to pan the view range range.

#### **Frame Range Zoom**

Zoom into a frame range by re-sizing the scope range using the navigation bar handles. You can also  **Alt + right-click** on the graph to select a specific range to zoom to.

![Changing the working range from the Control Deck.](<../.gitbook/assets/image (446).png>)

![Changing the working range from the Graph pane.](<../.gitbook/assets/image (921).png>)

#### **Working Range / Playback range**

The working range (also called the playback range) is both the view range and the playback range of a corresponding _Take_ in Edit mode. Only within the working frame range will recorded tracking data be played back and shown on the graphs. This range can also be used to output a specific frame range when exporting tracking data from Motive.

The working range can be set from different places:

* In the navigation bar of the Graph View pane, drag the handles on the scrubber to set the working range.
* Use the navigation controls on the Graph View pane to zoom in or zoom out on the frame ranges to set the working range.
* The working range can also be set from the [Control Deck](control-deck.md) when in the Edit mode.

#### **Selection Range**

The selection range is used to apply post-processing edits only onto a specific frame range of a Take. Selected frame range will be highlighted in yellow on both the Graph View pane and the [Timeline ](control-deck.md#timeline-controls)in the Control Deck.

**Gap indication**

When playing back a recorded capture, the red shading on the navigation bar indicates the number of occlusions from labeled markers. Brighter red means that there are more markers with labeling gaps in that section.

### Frame Range Selection

<img src="../.gitbook/assets/Graph with Frame Range Selected.png" alt="Graph View Pane with frames 522 - 772 selected." width="442">

Left-click and drag over the graph to select a specific frame range. Frame range selection are used in the following workflows:

* **Zooming**: Zoom to the selected range by clicking on the <img src="../.gitbook/assets/image (50).png" alt="" data-size="line"> button or by using the _F_ hotkey.
* **Tracking Data Export**: Restrict exported tracking data to the selected range for easier analysis.
* **Reconstruction**: Focus on a specific frame range during the post-processing reconstruction pipeline (Reconstructing / Reconstruct and Auto-labeling).
* **Labeling**: Assign or modify marker labels, or run the auto-label pipeline on selected ranges only.
* **Post-processing data editing**: Apply editing tools to the selected frame range only. Please see the [Data Editing](../motive/data-editing.md) page for more detail.
* **Data Clean-up**: Delete 3D data or marker labels on selected ranges.

### Graph Context Menus

Right-click on any graph pane to open a Context menu with View options. From here, you can show or hide the Toolbar and Navbar, or create new layouts (covered in the [Customize Graph Layout](graph-view-pane.md#customize-graph-layout) section, below).&#x20;

Options are limited when using a System Layout. User-defined Layouts include more options, and will display the data included in the selected graph panel. This allows the user to quickly remove data from graph by unchecking the data type to remove it. Once removed, use the the [Graph Editor Sidebar](graph-view-pane.md#graph-editor-sidebar) to add it again.&#x20;

<div><figure><img src="../.gitbook/assets/Graph View Pane Context Menu for System graphs.png" alt=""><figcaption><p>System Layout <br>Context Menu.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Graph Pane - Right click context menu 2.png" alt=""><figcaption><p>User Layout context menu with<br>nothing selected in the Viewport.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Graph Pane - Right click context menu.png" alt=""><figcaption><p>User Layout context menu<br>with plotted data.</p></figcaption></figure></div>

## Layouts

The layouts feature allows users to organize and format graphs to suit their individual needs. The following layouts are available by default:

* Channel
* Combined
* Tracks
* Combined-primary
* Force plates
* Rigid body/bone

![Menu of Pre-defined Layouts.](<../.gitbook/assets/Graph Pane - System and User Layouts.png>)

Users can also create and save custom layouts of up to 9 graphs each, specifying which data channels to plot on each graph. This section will focus on the system layouts and standard User Layouts. Please see the section [Customize Graph Layout](graph-view-pane.md#customize-graph-layout), below, for instructions to create custom graphs.

### System Layouts

Commonly used layouts are available under System Layouts.&#x20;

{% hint style="info" %}
Layouts under the _System Layouts_ category are the same graphs that existed in the old timeline editor.
{% endhint %}

#### **Channel View**

The Channel View provides X/Y/Z curves for each selected marker, providing verbose motion data that highlights gaps, spikes, or other types of noise in the data.

![System Layouts: Channel View](<../.gitbook/assets/image (424).png>)

#### **Combined View**

The Combined View provides X/Y/Z curves for each selected marker at same plot. This mode is useful for monitoring positions changes without having to translate or rescale the y-axis of the graph.

![System Layout: Combined View.](<../.gitbook/assets/image (368).png>)

#### **Tracks View**

The Tracks View is a simplified view that can reveal gaps, marker swaps, and other basic labeling issues that can be quickly remedied by merging multiple marker trajectories together. You can select a specific group of markers from the drop-down menu. When two markers are selected, you can merge labels by using the Merge Keys Up <img src="../.gitbook/assets/Graph Pane - Merge Keys Up.png" alt="" data-size="line"> and Merge Keys Down <img src="../.gitbook/assets/Graph Pane - Merge Keys Down.png" alt="" data-size="line"> buttons.

![System Layout: Tracks View.](<../.gitbook/assets/image (1155).png>)

### User Layouts

#### Combined-Primary View

The Combined-Primary view graphs the data in a single plot, similar to the Combined view, but this view only displays the data for the final marker selected (known as the _Primary selection_ in Motive). Changes made to the data based on this view (e.g., filling gaps or smoothing ranges) will apply to all the selected markers, even those not displayed on the graph. &#x20;

#### Force Plates View

The Force Plates View plots six variables for the selected Force Plate:  Ground Reaction Forces on the left (Fx/Fy/Fz) and Rotational moments (Mx/My/Mz) on the right.&#x20;

<figure><img src="../.gitbook/assets/image (1504).png" alt=""><figcaption><p>System Layout: Force Plates view.</p></figcaption></figure>

#### Rigid Body / Bone View

The Rigid Body / Bone View plots pivot point position (X/Y/Z), rotation (pitch/yaw/roll), or mean error values of the selected Rigid Body asset(s). Use the Lock Selection button to keep the graph locked to the selected asset(s).&#x20;

<figure><img src="../.gitbook/assets/Graph Pane - Rigid Body Bone.png" alt=""><figcaption><p>System Layout: Rigid Body / Bone view.</p></figcaption></figure>

To add IMU data in the graph, click the <img src="../.gitbook/assets/Graph Pane - Edit Graph (2).png" alt="" data-size="line"> Edit Graph button. On the Data tab, scroll to the IMU section and select the data you wish to plot.&#x20;

<figure><img src="../.gitbook/assets/image (1510).png" alt=""><figcaption></figcaption></figure>

#### Template View

<figure><img src="../.gitbook/assets/Graph Pane - Template.png" alt=""><figcaption><p>System Layout: Template view.</p></figcaption></figure>

The template view is a nine-panel sample layout that includes a variety of graph options.&#x20;

* To replace any of the pre-set graphs, right-click in the panel with the graph you want to replace and select _Clear Graph_.&#x20;
* To remove a panel altogether, right-click and select _Remove Graph_.&#x20;
* If all three graphs in a column are removed, the remaining two columns will resize to fit the pane.&#x20;

Click in any of the graph panels then click the <img src="../.gitbook/assets/image (1506).png" alt="" data-size="line"> _Edit Graph_ button to select the data to plot in that panel. Click in another panel to select the data to plot there and continue these steps until all the data you wish to plot is selected.

### Custom Layouts

The graph layout can be customized to monitor data from channels involved in a capture, as explained in the next section. Once a custom layout is created, it appears in the User Layouts section.  &#x20;

## Customize Graph Layout

Custom layouts can serve as templates that require the user to make a selection  in the 3D viewport, or they can be [particularized ](graph-view-pane.md#particularizing-a-layout)to permanently lock the graph to a specific object or objects.&#x20;

#### **Step 1. Create New Layout**

Select _Create Graph Layout_ from the pane menu <img src="../.gitbook/assets/Motive Context Menu (14).png" alt="" data-size="line"> located on the top-right corner.

<figure><img src="../.gitbook/assets/Graph Pane - Layout Menu options (1).png" alt=""><figcaption><p>Graph View Pane layout menu.</p></figcaption></figure>

#### **Step 2. Set the number of graphs**

Right-click on the graph. Under _Grid Layout,_ choose the number of rows and columns for the grid. The maximum allowed is 3 x 3.&#x20;

![Choosing desired number of rows and columns on a newly created layout.](<../.gitbook/assets/image (378).png>)

#### **Step 3. Open the Graph Editor**

Expand the Graph Editor by clicking on the <img src="../.gitbook/assets/Graph Pane - Edit Graph.png" alt="" data-size="line"> icon on the tool bar.

#### **Step 4. Select a graph**

Click on a graph from the grid to select it (it will appear highlighted). Edits made using the Graph Editor will apply only to the selected graph.&#x20;

#### **Step 5. Select Data Channels**

Next, check the data channels to plot from the _Data tab_ of the Graph Editor.  You can also change the color to use when plotting the corresponding data channel by clicking the color box to the right of the selection.

![Data Editor for Markers and Rigid&#x20;
Bodies in the Graph View pane.](<../.gitbook/assets/Graph Pane - Graph Editor Data tab CROPPED.png>)

#### **Step 6. Format visuals**

Format the style of the graph using the _Visuals_ tab. See the [Visuals tab](graph-view-pane.md#visual-tab) section below for more information the available settings.&#x20;

{% hint style="info" %}
To change the frame range of Live mode graphs, adjust the [scope duration](settings/settings-views.md#scope-duration) in application settings. Go to _Settings -> Views -> Graphs_ tab. &#x20;
{% endhint %}

#### **Step 7. Repeat for each grid in the layout**&#x20;

Repeat steps 4 through 6 until each of the graphs in the layout is configured.

#### **Step 8. Select  the object to graph**

Select one or more markers or assets (Rigid Bodies, Skeletons, force plates, or NI-DAQ channels) to monitor.

#### **Step 9. Lock selection to graph(s)**

Lock the selection for any graphs that should stay linked to the current selection. Individual graphs can be locked from the context menu (right-click on the graph and select _Lock Selection_) or all graphs can be locked by clicking the <img src="../.gitbook/assets/image (1507).png" alt="" data-size="line"> button on the toolbar.&#x20;

Once all related graphs are locked, move on to next selection and lock the corresponding graph. Repeat as needed.&#x20;

![The lock symbol indicates the selection&#x20;
has been locked on the graph.](<../.gitbook/assets/image (1093).png>)

#### **Step 11. Update the layout**

When you have the layout configured with the selections locked, you can save the configurations as well as the implicit selections (i.e. what data to graph) temporarily to the layout. However, unless the layout is [particularized ](graph-view-pane.md#particularizing-a-layout)to the explicit selections (i.e. the asset being graphed), you will need to select the items in Motive to plot the respective graphs each time you load the layout.

To update the layout, right-click in any of the graph panes and select _Update Layout._

### Particularizing a Layout

This action saves and explicitly _fixes_ the selections that the graphs are locked to in an XML file. Once a layout has been _particularized_, you can re-open it in different sessions and plot the data channels from the same subject without locking the selection again. When the particularized layout is selected again, it looks for items in the _Take_ (labeled markers, Rigid Bodies, Skeletons, force plates, or analog channels) with the same names as those contained in the particularized layout.

Click the <img src="../.gitbook/assets/Motive Context Menu.png" alt="" data-size="line"> button in the top right corner of the pane and select _Particularize layout_.&#x20;

<figure><img src="../.gitbook/assets/Graph Pane - Layout Menu options.png" alt=""><figcaption><p>Graph View Pane layout menu.</p></figcaption></figure>

Particularized graphs are indicated by an <img src="../.gitbook/assets/image (1508).png" alt="" data-size="line"> icon at the top-right corner of the graph.

![Particularized graph. Fz force data from OR6-7-1000 plate, explicitly, will be plotted on the graph.](<../.gitbook/assets/image (366).png>)

## Preferred Layouts

The Preferred Layout settings allow you to select graph defaults for both Live and Edit modes. These can be System layouts or custom layouts.&#x20;

To select a layout:

1. Click the <img src="../.gitbook/assets/Settings button (14).png" alt="" data-size="line"> icon on the main toolbar to open the _Settings_ panel.&#x20;
2. Click the _Views_ settings.
3. On the Graphs tab, enter the name of the layout you wish to use exactly as it appears on the layout menu into the _Preferred Live Layout_ and the _Preferred Edit Layout_ fields.&#x20;

<figure><img src="../.gitbook/assets/Settings - Views  Graphs with Preferred Graph layouts (1).png" alt=""><figcaption><p>Settings Panel: View tab, Graphs settings.</p></figcaption></figure>

{% hint style="info" %}
Graph layouts are .xml files saved in **C:\ProgramData\OptiTrack\Motive\GraphLayouts.**&#x20;

You can copy the .xml files to your project folders for sharing and later use. Copy them back into the _GraphLayouts_ folder when needed to make them available in Motive.&#x20;
{% endhint %}

## Graph Editor

Use the Graph Editor to choose which data channels to plot (on the Data tab) and to format the overall look of the graph (from the Visuals tab). &#x20;

When the Editor sidebar is expanded, one of the graph panes will change color to indicate the current selection. Changed made in the graph editor will apply only to this pane. After configuring the pane to your needs, left click in any other to change the selection. Continue until each pane is configured.&#x20;

{% hint style="warning" %}
Navigation controls are disabled while the Graph Editor is open.&#x20;
{% endhint %}

Open the Graph Editor by clicking the <img src="../.gitbook/assets/Graph Pane - Edit Graph (1).png" alt="" data-size="line"> icon on the main toolbar.&#x20;

### Data tab

The categories shown on the Data tab reflect the assets available in the _Take_ or Live capture environment. Device, Force Plate, and IMU channels are shown only when such assets are present.&#x20;

Only enabled, or checked, data channels will be plotted on the selected graph using the color specified. Once channels are enabled, one or more objects (marker, Rigid Body, Skeleton, force plate, or DAQ channel) must be selected (or locked) to display data in the graph.

![Graph View Data Pane.](<../.gitbook/assets/Graph Pane - Data tab - Marker RB FP and Device.png>)

#### **Marker**

Plot the 3D position (X/Y/Z) data of selected, or locked, marker(s) onto the selected graph.

#### **Rigid Body / Bone**

Plot pivot point position (X/Y/Z), rotation (pitch/yaw/roll), or mean error values of the selected Rigid Body or Skeleton asset(s) onto the selected graph. The asset must be solved.&#x20;

#### **Device**

Plot analog data of selected analog channel(s) from a data acquisition (NI-DAQ) device onto the selected graph.

#### **Force Plate**

Plot force and moment (X/Y/Z) of selected force plate(s). The plotted graph respects the coordinate system of the force platforms (z-up).

#### IMU

Plot rotation (pitch/yaw/roll) values of the IMU in the selected Rigid Body, solved or unsolved.&#x20;

### Telemetry Graphs

Telemetry graphs provide information useful for monitoring performance of the Live system.&#x20;

In Edit mode, the graph displays data from the original capture and is not affected by changes made to the _Take_ in post production such as adding or deleting assets. This allows OptiTrack Support Engineers to observe system information from a recorded _Take_ while troubleshooting issues that occurred during a capture.&#x20;

Telemetry graphs can be selected from the Data tab of the Graph Editor or by right-clicking on a user layout and selecting _Telemetry_, which displays the menu shown below.&#x20;

<figure><img src="../.gitbook/assets/Graph Pane - Telemetry Graph Options.png" alt=""><figcaption><p>Telemetry Graph Options</p></figcaption></figure>

{% hint style="success" %}
In Motive, latency values are measured, not calculated, resulting in precise and accurate values. See our [Latency Measurements](../developer-tools/natnet-sdk/latency-measurements.md) page for more information.&#x20;
{% endhint %}

#### Reconstruction Latency

The point cloud reconstruction processing time (in ms).&#x20;

#### RigidBody Latency

Rigid Body solving processing time (in ms).  &#x20;

#### Skeleton Latency

The cumulative solving processing time for skeleton and trained markerset (in ms).

#### Peripheral Latency

Peripheral device solving processing time (in ms).

#### Software Latency

Software pipeline processing time from synchronized camera frame group arrival time to data streaming out (measured, in ms).

#### System Latency

Total system processing time from camera mid-exposure to streaming out (measured, in ms.)

#### Streaming Rate

NatNet streaming data rate (frames/sec).

#### Peripheral Rate

Peripheral device sampling rate (frames/sec).

#### Final Rate

The calculated frame rate (frames/second).

#### Streaming Data Rate

NatNet per-frame streaming packet size (bytes/Mocap frame).

#### Average Camera Temperature

The average camera temperature as measured from each camera's temperature sensor (in degrees Celsius).&#x20;

#### Camera Data Rate

The cumulative data rate for all cameras in the frame group for the selected frame (Measured in KBps/frame).&#x20;

A frame group is the set of cameras that contribute data to the current frame. This may include all the cameras in the system, or a subset.

#### Max Camera Frame Pool Size

The largest allocated camera frame buffer (pool size) among all cameras (camera frames).

#### Min Camera Frame Pool Size

The smallest allocated camera frame buffer (pool size) among all cameras (camera frames).

#### Ave Camera Frame Pool Size

The average allocated camera frame buffer (pool size) among all cameras (camera frames).

### Visual tab

The Visual tab has settings that affect the overall look and style of the graph. Like the settings on the Data tab, Visuals are set independently for each of the panels in the graph pane. &#x20;

![Graph Editor  - Visuals tab.](<../.gitbook/assets/Graph Pane - Edit Graph Visuals.png>)

#### **Graph Name**

Labels the selected graph.

#### **View Style**

Configures the style of the selected graph:

* Channel: Plots selected channels onto the graph.
* Combined: Plots X/Y/Z curves for each selected markers fixed on the same plot.
* Gap: Plots markers as tracks along the timeline to easily monitor and fix occluded gaps on selected markers.

#### **Range Handles**

Enables or disables the range handles located at the bottom of the frame selection.

#### **Row Stretch**

Sets the height of the selected row in the layout. The height is determined by a ratio to a sum of all stretch values:

`(row stretch value for the selected row)/(sum of row stretch values from all rows) * (size of the pane)`.

#### **Column Stretch**

Sets the width of the selected column in the layout. The width size is determined by a ratio to a sum of all values:&#x20;

`(column stretch value for the selected column)/(sum of column stretch values from all columns) * (size of the pane)`.

#### **Show Values**

Displays the current frame values for each data set.

#### **Show Labels**

Displays the name of each plotted data set.

#### **Only Primary Marker**

Plots data from the primary selection only. The primary selection is the last item selected in the Assets pane or the 3D Viewport.

#### **Show X Grid**

Shows or hides the x gridlines.

#### **Show Y Grid**

Shows or hides the y gridlines.

#### **Major Y**

Sets the size of the major grid lines, or tick marks, on the y-axis values.

#### **Minor Y**

Sets the size of the minor grid lines, or tick marks, on the y-axis values.

#### **Min Y**

Sets the minimum value for the y-axis on the graph.

#### **Max Y**

Sets the maximum value for the y-axis on the graph.

#### Stacked Offset

Creates vertical distance between the plotted points when tracking multiple markers or assets in a single graph.&#x20;

#### Significant Figures

Sets the number of decimal places to show in the graph values. The default value of -1 will show 2 decimal places. Set the value to 0 to round to the nearest whole number.&#x20;
