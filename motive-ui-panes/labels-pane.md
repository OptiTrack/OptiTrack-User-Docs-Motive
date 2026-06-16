---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/labels-pane
---

# Labels Pane

The Labels pane is used to assign, remove, and edit marker labels in the [3D data](../motive/data-recording/data-types.md#3d-data) and is used along with the [Editing Tools](../motive/data-editing.md) for complete post-processing. For a detailed explanation of the labeling workflow, read the [Labeling](../motive/labeling.md) page.

Open the Labels pane from the View menu or by clicking the <img src="../.gitbook/assets/Labels Pane button.png" alt="" data-size="line"> button on the main toolbar.

## Overview

<img src="../.gitbook/assets/Labels Pane - Overview.png" alt="The Labels pane." width="563">

<table><thead><tr><th width="100">Icon</th><th width="206">Function</th><th>Description</th></tr></thead><tbody><tr><td><img src="../.gitbook/assets/image (437).png" alt=""></td><td>Mouse Actions</td><td>Switch between Select mode (Hotkey: Q) for normal operations, and <a href="../motive/labeling.md#quicklabel-mode">Quick Label</a> mode (Hotkey: D), to manually assign labels with just one-click. <br><br>These options are also available from the Mouse Actions button in the <a href="viewport.md">3D Viewport</a>.</td></tr><tr><td><img src="../.gitbook/assets/image (394).png" alt=""></td><td>Increment Options</td><td><p>Determines how the Quick Label mode should behave after a label is assigned:</p><ul><li><strong>Do Not Increment</strong> keeps the same label attached to the cursor. </li><li><strong>Go To Next Label</strong> automatically advances to the next label in the list, even if it is already assigned to a marker in the current frame. This is the default option. </li><li><strong>Go To Next Unlabeled Marker</strong> advances to the next label in the list that is not assigned to a marker in the current frame. </li></ul></td></tr><tr><td><img src="../.gitbook/assets/image (373).png" alt=""></td><td>Unlabel Selected</td><td>Removes the label from the selected trajectories.</td></tr><tr><td><img src="../.gitbook/assets/labels pane - Autolabel button.png" alt="" data-size="line"></td><td>Auto-Label</td><td>Options to <strong>Reconstruct, Auto-label</strong> or <strong>Reconstruct and Auto-label.</strong> Use caution as these processes overwrite the 3D data, discarding any post-processing edits on trajectories and marker labels.</td></tr><tr><td><img src="../.gitbook/assets/image (387).png" alt=""></td><td>Pane View Options</td><td><p>Provides different layout options:</p><ul><li><strong>Labeled Only:</strong> Displays only markers with labels; unlabeled markers are not shown. This is the default view.</li><li><strong>Split:</strong> Displays labeled markers on the left and unlabeled markers on the right. </li><li><strong>Split (Left/Right):</strong>  Sorts skeleton labels into columns based on marker location. Unspecified markers (e.g., head, chest, etc.) are listed in the left column.</li><li><strong>Stacked:</strong>  Displays labeled markers on the top and unlabeled markers on the bottom. </li><li>Combo:  Displays the labeled markers in the Split (Left/Right) view with unlabeled markers stacked below.</li></ul></td></tr><tr><td><img src="../.gitbook/assets/image (1111).png" alt=""></td><td>Link to 3D Selection</td><td>When this button is enabled, asset selection is locked to the selection from the <a href="viewport.md#perspective-view">Perspective viewport</a>. When toggled off, the Asset Selection drop-down menu in the Labels pane becomes active. </td></tr><tr><td><img src="../.gitbook/assets/image (1429).png" alt=""></td><td>Show Range Settings</td><td>The Range Settings determine which frames of the recorded data the label will be applied to. </td></tr></tbody></table>

## Marker Labels

* Labels shown in white are tracked in the current frame. Labels shown in magenta are not.&#x20;
* The **Gaps** column shows the _percentage of occluded gaps_ values. If the trajectory has no gaps (100% complete), no number is shown.&#x20;

## Labeling Settings

### Labeling Range Settings

#### All or Selected

Assign labels to a selected marker for all, or selected, frames in a capture.

![Labeling entire range of a trajectory using the All/Selected setting.](<../.gitbook/assets/image (399).png>)

![Labeling only selected range of a trajectory using the All/Selected setting.](<../.gitbook/assets/image (1075).png>)

#### Spike or Fragment

Apply labels to a marker within the frame range bounded by trajectory gaps and spikes (erratic change). The Max Spike value sets the threshold for spikes which will be used to set the labeling boundary. The Max Gap size determines the tolerable gap size in a fragment, and trajectory gaps larger than this value will set the labeling boundary.&#x20;

#### **Swap Spike or Fragment**

Apply labels only to spikes created by labeling swaps.  This setting is efficient when correcting labeling swaps.

#### **Max Gap**

This sets the tolerable gap sizes for both gap ends of the fragment labeling.

#### **Max Spike**

Sets the max allowable velocity of a marker (mm/frame) for it to be considered as a spike.

![A trajectory fragment bounded by gaps.](<../.gitbook/assets/image (956).png>)

![A trajectory fragment bounded by spikes.](<../.gitbook/assets/image (260).png>)

#### Apply Labels

When using the _Spike or Fragment_ range setting, the label will be applied until the marker trajectory is discontinued with a gap that is larger than the maximum gap defined above. When using the _All or Selected_ range setting, the label will be applied to the entire trajectory or just the selected ranges.

#### **Forwards**

Assigns the selected label onto a marker for current frame and frames forward.

#### **Backwards**

Assigns selected label onto a marker for current frame and frames backward.

#### **Forwards & backwards**

Assigns selected label onto the marker for current frame, frames forward, and frames backward.
