# Graph View Pane

The _Graph View pane_ is used to visualize the tracking data in Motive. This pane can be accessed from the command bar (_View tab > Graph_) or simply by clicking on the <img src="../.gitbook/assets/Graph View Pane 1 Button.png" alt="" data-size="line"> icon. This page provides instructions and tips on how to efficiently utilize the Graph View pane in Motive.

## Overview

Using the _Graph View pane_, you can visualize and monitor multiple data channels including 3D positions of reconstructed markers, 6 Degrees of Freedom (6 DoF) data of trackable assets, and signals from integrated external devices (e.g. force plates or NI-DAQ). Graph View pane offers a variety of graph layouts for the most effective data visualization. In addition to the basic layouts (channel, combined, gapped), custom layouts can also be created for monitoring specific data channels only. Up to 9 graphs can be plotted in each layout and up to two panes can be opened simultaneously in Motive.

Graphs can be plotted in both Live and Edit mode.

* **In Live Mode, the following data can be plotted in real-time:**
  * Rigid body 6 DoF data (Position and Orientation)
  * Force Plate Data (Force and Moment)
  * Analog Data
* **In Edit Mode, the graphs can be used to review and post-process the captured data:**
  * 3D Positions of reconstructed markers
  * Rigid body 6 DoF data (Position and Orientation)
  * Force Plate Data (Force and Moment)
  * Analog Data

![Graph View pane in Motive. Click image to open the image's page, click the image again to enlarge. Click image to enlarge.](<../.gitbook/assets/image (552).png>)

### Toolbar

![](<../.gitbook/assets/image (591).png>)

| Icon                                      | Name                                   | Description                                                                                                                                                                                                                                                                                |
| ----------------------------------------- | -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ![](<../.gitbook/assets/image (544).png>) | Graph Editor                           | This opens up the sidebar for customizing a selected graph within a layout.                                                                                                                                                                                                                |
| ![](<../.gitbook/assets/image (551).png>) | Autoscale Graph                        | Toggle to autoscale X/Y/Z graphs.                                                                                                                                                                                                                                                          |
| ![](<../.gitbook/assets/image (639).png>) | <p>Zoom Fit</p><p>(selected range)</p> | Zooms into selected frame region and centers the timeline accordingly.                                                                                                                                                                                                                     |
| ![](<../.gitbook/assets/image (562).png>) | Lock Cursor Centered                   | Locks the timeline scrubber at the center of the view range.                                                                                                                                                                                                                               |
| ![](<../.gitbook/assets/image (631).png>) | Delete Selected Keys                   | Delete selected frame region.                                                                                                                                                                                                                                                              |
| ![](<../.gitbook/assets/image (564).png>) | Move Selected Keys                     | Translates trajectories in selected frame region. Select a range and drag up and down on a trajectory.                                                                                                                                                                                     |
| ![](<../.gitbook/assets/image (542).png>) | Draw Keys                              | Manual draw trajectory by clicking and dragging on a selected trajectory in the Editor.                                                                                                                                                                                                    |
| ![](<../.gitbook/assets/image (589).png>) | Merge Keys Up                          | Merges two trajectories together. This feature is useful when used with the [Tracks View](graph-view-pane.md#tracks-view) graphs. Select two trajectories and click this button to merge the bottom trajectory into the top trajectory.                                                    |
| ![](<../.gitbook/assets/image (588).png>) | Merge Keys Down                        | Merges two trajectories together. This feature is useful when used with the [Tracks View](graph-view-pane.md#tracks-view) graphs. Select two trajectories and click this button to merge the top trajectory into the bottom trajectory.                                                    |
| ![](<../.gitbook/assets/image (603).png>) | Lock Selection                         | Locks the current selection (marker, Rigid Body, Skeleton, force plates, or NI-DAQ) onto all graphs on the layout. This is used to temporarily hold the selections. Locked selections can later be fixed by taking a snapshot of the layout. This is elaborated more in the later section. |

### Pane Menu Options

![Graph View pane menu](<../.gitbook/assets/image (573).png>)

#### **Create Layout**

Creates a new graph layout.

#### **Delete Layout**

Deletes the current graph layout.

#### **Update Layout**

Saves the changes to the graph layout XML file.

#### **Particularize Layout**

Takes an XML snapshot of the current graph layout. Once a layout has been particularized, both the layout configuration and the item selection will be fixed and it can be exported and imported onto different sessions.

#### **Edit Layout**

Opens the layout XML file of the current graph layout for editing.

#### **Show Layout**

Opens the file location of where the XML files for the graph layouts are stored.

## Graph Navigation

### Basic Navigation

#### _On the Graph_

#### **Navigate Frames (Alt + Left-click + Drag)**

Alt + left-click on the graph and drag the mouse left and right to navigate through the recorded frames. You can do the same with the mouse scroll as well.

#### **Panning (Scroll-click + Drag)**

Scroll-click and drag to pan the view vertically and horizontally throughout plotted graphs. Dragging the cursor left and right will pan the view along the horizontal axis for all of the graphs. When navigating vertically, scroll-click on a graph and drag up and down to pan vertically for the specific graph.

#### **Zooming (Right-click + Drag)**

Right-click and drag on a graph to free-form zoom in and out on both vertical and horizontal axis. If the _Autoscale Graph_ <img src="../.gitbook/assets/Graph Pane - Auto Extent graphs.png" alt="" data-size="line"> is enabled, the vertical axis range will be fixed according to the max and min value of the plotted data.

{% hint style="info" %}
**Other Ways to Zoom:**

* Press "Shift + F" to zoom out to the entire frame range.
* Zoom into a frame range by Alt + right-clicking on the graph and selecting the specific frame range to zoom into.
* When a frame range is selected, press "F" to quickly zoom onto the selected range in the timeline.
{% endhint %}

#### **Selecting Frame Range (Left-click + Drag)**

The frame range selection is used when making post-processing edits on specific ranges of the recorded frames. Select a specific range by left-clicking and dragging the mouse left and right, and the selected frame ranges will be highlighted in yellow. You can also select more than one frame ranges by shift-selecting multiple ranges.

#### _On the Navigation Bar_

#### **Navigate Frames (Left-click)**

Left-click and drag on the nav bar to scrub through the recorded frames. You can do the same with the mouse scroll as well.

#### **Pan View Range**

Scroll-click and drag to pan the view range range.

#### **Frame Range Zoom**

Zoom into a frame range by re-sizing the scope range using the navigation bar handles. You can also easily do this by **Alt + right-clicking** on the graph and selecting a specific range to zoom into.

### Navigation Bar

![Changing the working range from the Control Deck.](<../.gitbook/assets/image (641).png>)

![Changing the working range from the Graph pane.](<../.gitbook/assets/image (620).png>)

#### **Working Range / Playback range**

The working range (also called the playback range) is both the view range and the playback range of a corresponding _Take_ in Edit mode. Only within the working frame range will recorded tracking data be played back and shown on the graphs. This range can also be used to output a specific frame range when exporting tracking data from Motive.

The working range can be set from different places:

* In the navigation bar of the Graph View pane, you can drag the handles on the scrubber to set the working range.
* You can also use the navigation controls on the Graph View pane to zoom in or zoom out on the frame ranges to set the working range.
* Start and end frames of a working range can also be set from the [Control Deck](control-deck.md) when in the Edit mode.

#### **Selection Range**

The selection range is used to apply post-processing edits only onto a specific frame range of a Take. Selected frame range will be highlighted in yellow on both the Graph View pane as well as the Timeline pane.

**Gap indication**

When playing back a recorded capture, the red colors on the navigation bar indicate the number of occlusions from labeled markers. Brighter red means that there are more markers with labeling gaps.

### Frame Range Selection

![](<../.gitbook/assets/image (594).png>)

Left-click and drag on the graph to select a specific frame range. Frame range selection can be utilized for the following workflows:

* **Zooming**: Zoom quickly into the selected range by clicking on the <img src="../.gitbook/assets/image (206).png" alt="" data-size="line"> button or by using the _F_ hotkey.
* **Tracking Data Export**: Exporting tracking data for selected frame ranges.
* **Reconstruction**: Performing the post-processing reconstruction (Reconstructing / Reconstruct and Auto-labeling) pipeline on selected frame ranges.
* **Labeling**: Assigning marker labels, modifying marker labels, or running the auto-label pipeline on selected ranges only.
* **Post-processing data editing**: Applying the editing tools on selected frame ranges only. Read more: [Data Editing](../motive/data-editing.md)
* **Data Deleting**: Deleting 3D data or marker labels on selected ranges.

## Layouts

![](<../.gitbook/assets/image (616).png>)

![](<../.gitbook/assets/image (554).png>)

### System Layouts

The layouts feature in the Graphs View pane allows users to organize and format graph(s) to their preference. The graph layout is selected under the drop-down menu located at the top right corner of the Graph View pane.

In addition to default graph layouts (channels view, combined view, and tracks view) which have been migrated from the previous versions of Motive, custom layouts can also be created. With custom layouts, users can specify which data channels to plot on each graph, and up to 9 graphs can be configured on each layout. Furthermore, asset selections can be locked to labeled markers or assets.

{% hint style="info" %}
Layouts under the _System Layouts_ category are the same graphs that existed in the old timeline editor.
{% endhint %}

#### **Channel View**

The Channel View provides X/Y/Z curves for each selected marker, providing verbose motion data that highlights gaps, spikes, or other types of noise in the data.

![System Layouts: Channel View](<../.gitbook/assets/image (638).png>)

#### **Combined View**

The Combined View provides X/Y/Z curves for each selected markers at same plot. This mode is useful for monitoring positions changes without having to translate or rescale the y-axis of the graph.

![System Layout: Combined View.](<../.gitbook/assets/image (624).png>)

#### **Tracks View**

The Tracks View is a simplified view that can reveal gaps, marker swaps, and other basic labeling issues that can be quickly remedied by merging multiple marker trajectories together. You can select a specific group of markers from the drop down menu. When two markers are selected, labels can be merged by using the Merge Keys Up <img src="../.gitbook/assets/Graph Pane - Merge Keys Up.png" alt="" data-size="line"> and Merge Keys Down <img src="../.gitbook/assets/Graph Pane - Merge Keys Down.png" alt="" data-size="line"> buttons.

![System Layout: Tracks View.](<../.gitbook/assets/image (256).png>)

### Custom Layouts

In the new Graphs View pane, the graph layout can be customized to monitor data from channels involved in a capture. Create a new layout from the <img src="../.gitbook/assets/Motive Context Menu (1).png" alt="" data-size="line"> menu > _Create New Layout_ option or right-click on the pane and click _Create New Layout_ option.

Graph layout customization is further explained on the later section: Customizing Layout.

## Customizing Graph Layout

### General Steps

#### **Step 1. Create New Layout**

New layouts can be created by clicking on the _Create Graph Layout_ from the pane menu <img src="../.gitbook/assets/Motive Context Menu (1) (1).png" alt="" data-size="line">  located on the top-right corner.

#### **Step 2. Set the number of graphs**

Right-click on the graph, go to the _Grid Layout_, and choose the number of rows and columns that you wish to put in the grid. (max 9 x 9)

![Choosing desired number of rows and columns on a newly created layout.](<../.gitbook/assets/image (626).png>)

#### **Step 3. Open the Graph Editor**

Expand the Graph Editor by clicking on the <img src="../.gitbook/assets/Graph Pane - Edit Graph.png" alt="" data-size="line">  icon on the tool bar.

#### **Step 4. Select a graph**

Click on a graph from the grid. The graph will be highlighted in yellow. Within the grid, only the selected graph will be edited when making changes using the Graph Editor.

#### **Step 5. Pick Data Channels**

Next, you need to pick data channels that you wish to plot. You can do this by checking the desired channels under the _data_ tab while a graph is selected. Only the checked channels will be plotted on the selected graph. Here, you can also specify which color to use when plotting corresponding data channels.

![Data Editor in the Graph View pane.](<../.gitbook/assets/image (288).png>)

#### **Step 6. Format visuals**

Then under the _Visual_ tab, format the style of the graph. You can configure the graph axis, assign name for the graph, display values, and etc. Most importantly, configure the _View Style_ to match desired graph format.

{% hint style="info" %}
When plotting live tracking data in the Live Mode, set the _View Style_ to _Live_. Frame range of the Live mode graphs can be adjusted by changing the [scope duration](settings/) under application settings.
{% endhint %}

#### **Step 7. Repeat**

Repeat the above steps 5 \~ 6 and configure each of the graphs in the layout.

#### **Step 8. Make selection**

Select an asset (marker, Rigid Body, Skeleton, force plate, or NI-DAQ channel) that you wish to monitor.

#### **Step 9. Lock selection to graph(s)**

Lock selection for graphs that need to be linked to the selection. Individual graphs can be locked from the context menu (right-clicking on the graph > Lock Selection) or all graphs can be locked by clicking <img src="../.gitbook/assets/image (1) (1).png" alt="" data-size="line"> on the toolbar.

#### **Step 10. Repeat lock selection**

Once all related graphs are locked, move on to next selection and lock the corresponding graph.

![The lock symbol indicates the selection has been locked on the graph.](<../.gitbook/assets/image (244).png>)

#### **Step 11. Update the layout**

When you have the layout configured with the locked selections you can save the configurations as well as the implicit selections temporarily to the layout. Until the layout is particularized onto the explicit selections, you will need to select the related items in Motive to plot the respective graphs.

#### **Step 12. Particularize the layout**

The last step is to make the selection explicit by particularizing the layout. You can do this by clicking the _Particularize_ option under the pane menu once the layout is configured and desired selections are locked. This will fix the explicit selection onto the layout XML file, and the layout will always look for specific items with the same name from the Take. Particularized graphs will be indicated by <img src="../.gitbook/assets/image (1) (1) (1).png" alt="" data-size="line"> at the top-right corner of the graph.

![Particularized graph. Fz force data from OR6-7-1000 plate, explicitly, will be plotted on the graph.](<../.gitbook/assets/image (632).png>)

### Particularizing a Layout

It is important to particularize the customized layout once all of the graphs are configured. This action will save and explicitly _fix_ the locked selections that the graphs are locked onto. Once the layouts have been _particularized_, you can re-open the same layout on different sessions and plot the data channels from the same subject without locking the selection again. Specifically, the particularized layout will try to look for items (labeled marker, Rigid Body, Skeleton, force plate, or analog channels) with the same names that the layout is particularized to.

## Graph Editor Sidebar

The Graph Editor can be expanded by clicking on the <img src="../.gitbook/assets/Graph Pane - Edit Graph (1).png" alt="" data-size="line"> icon from the toolbar. When this sidebar is expanded, you can select individual graphs but other navigation controls will be disabled. Using the graph editor, you can select a graph, choose which data channels to plot, and format the overall look to suit your need.

### Data tab

![](<../.gitbook/assets/image (263).png>)

Only enabled, or checked, data channels will be plotted on the selected graph using the specified color. Once channels are enabled, an asset (marker, Rigid Body, Skeleton, force plate, or DAQ channel) must be selected and locked.

#### **Marker**

Plot 3D position (X/Y/Z) data of selected, or locked, marker(s) onto the selected graph.

#### **Rigid Body**

Plot pivot point position (X/Y/Z), rotation (pitch/yaw/roll), or mean error values of selected, or locked, Rigid Body asset(s) onto the selected graph.

#### **Device**

Plot analog data of selected analog channel(s) from a data acquisition (NI-DAQ) device onto the selected graph.

#### **Force Plate**

Plot force and moment (X/Y/Z) of selected force plate(s). Plotted graph respects coordinate system of the force platforms (z-up).

{% hint style="info" %}
Using the black color (0,0,0) for the plots will set the graph color to the color of the Rigid Body asset shown in the 3D viewport, which is set under the [Rigid Body properties](properties-pane/properties-pane-rigid-body.md).
{% endhint %}

### Visual tab

![](<../.gitbook/assets/image (637).png>)

#### **Graph Name**

Labels the selected graph.

#### **View Style**

Configures the style of the selected graph:

* Channel: Plots selected channels onto the graph.
* Combined: Plots X/Y/Z curves for each selected markers fixed on the same plot.
* Gap: The Tracks View style allows you to easily monitor the occluded gaps on selected markers.
* Live: The Live mode is used for plotting the live data.

#### **Range Handles**

Enables/disables range handles that are located at the bottom of the frame selection.

#### **Row Stretch**

Sets the height of the selected row in the layout. The height will be determined by a ratio to a sum of all stretch values: `(row stretch value for the selected row)/(sum of row stretch values from all rows) * (size of the pane)`.

#### **Column Stretch**

Sets the width of the selected column in the layout. The width size will be determined by a ratio to a sum of all values: `(column stretch value for the selected column)/(sum of column stretch values from all columns) * (size of the pane)`.

#### **Show Values**

Display current frame values for each data set.

#### **Show Labels**

Display name of each plotted data set.

#### **Show Primary Selection Only**

Plots data from the primary selection only. The primary selection is the last item selected from Motive.

#### **Show X Grid**

Shows/hides x grid-lines.

#### **Show Y Grid**

Shows/hides y grid-lines.

#### **Major Y**

Sets the size of the major grid lines, or tick marks, on the y-axis values.

#### **Minor Y**

Sets the size of the minor grid lines, or tick marks, on the y-axis values.

#### **Min Y**

Sets the minimum value for the y-axis on the graph.

#### **Max Y**

Sets the maximum value for the y-axis on the graph.
