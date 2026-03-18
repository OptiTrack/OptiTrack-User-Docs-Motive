# Labels Pane

In Motive, the Labeling pane can be accessed under the View tab or by clicking [![Toolbar Labeling Icon.png](https://v30.wiki.optitrack.com/images/d/df/Toolbar_Labeling_Icon.png)](https://v30.wiki.optitrack.com/index.php?title=File:Toolbar_Labeling_Icon.png) icon on the main toolbar.

For more explanation on the labeling workflow, read through the [Labeling](../motive/labeling.md) workflow page.

## Overview

![](<../.gitbook/assets/image (237).png>)

| Function             | Icon                                      | Description                                                                                                                                                                                                                                                                                                            |
| -------------------- | ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Selection Mode       | ![](<../.gitbook/assets/image (559).png>) | Options for switching between select mode and QuickLabel mode. Select mode is used for normal operations, and QuickLabel mode allows assigning each selected label with just one-click.                                                                                                                                |
| Increment Options    | ![](<../.gitbook/assets/image (585).png>) | <p>Options for selection increment behavior when labeling:</p><ul><li>Do not increment: Selection stays the same after labeling</li><li>Go to next label: Selection advances to the next label on the list</li><li>Go to next unlabeled marker: Selection advances to the next unlabeled marker on the list.</li></ul> |
| Unlabeled Selected   | ![](<../.gitbook/assets/image (543).png>) | Unlabels selected trajectories.                                                                                                                                                                                                                                                                                        |
| Label List Options   | ![](<../.gitbook/assets/image (613).png>) | Splits the list of labels into two columns for organization purposes. Unlabeled trajectories will be sorted on the right column, and the selected marker set labels are sorted on the left column.                                                                                                                     |
| Link to 3D Selection | ![](<../.gitbook/assets/image (255).png>) | When this button is enabled, marker label selection will be linked to the selection from the [Perspective viewport](viewport.md#perspective-view).                                                                                                                                                                     |
| Show Range Settings  | ![](<../.gitbook/assets/image (571).png>) | When enabled, shows the range settings to determine which frames of the recorded data the label will get applied to.                                                                                                                                                                                                   |

## Marker Labels

Labeling pane includes a list of marker labels that are associated with the capture. The color of each label tells whether the marker is tracked in the current frame, and the corresponding gap percentage is indicated next to each label. When a marker set is chosen under the Marker Set dropdown menu, only associated labels will be listed. In addition, the marker set selection can also be linked to 3D selection in the perspective view pane when the **Link to 3D** button [![Label LinkTo3D 30.png](https://v30.wiki.optitrack.com/images/d/de/Label_LinkTo3D_30.png)](https://v30.wiki.optitrack.com/index.php?title=File:Label_LinkTo3D_30.png) is enabled.

## Labeling Settings

### Labeling Range Settings

#### All/Selected

Assign labels to a selected marker for all, or selected, frames in a capture.

![Labeling entire range of a trajectory using the All/Selected setting.](<../.gitbook/assets/image (553).png>)

![Labeling only selected range of a trajectory using the All/Selected setting.](<../.gitbook/assets/image (201).png>)

#### Spike/Fragment

Applies labels to a marker within the frame range bounded by trajectory gaps and spikes (erratic change). The Max Spike value sets the threshold for spikes which will be used to set the labeling boundary. The Max Gap size determines the tolerable gap size in a fragment, and trajectory gaps larger than this value will set the labeling boundary. This setting is efficient when correcting labeling swaps.

#### **Max Gap**

This sets the tolerable gap sizes for both gap ends of the fragment labeling.

#### **Max Spike**

Sets the max allowable velocity of a marker (mm/frame) for it to be considered as a spike.

![A trajectory fragment bounded by gaps.](<../.gitbook/assets/image (294).png>)

![A trajectory fragment bounded by spikes.](<../.gitbook/assets/image (610).png>)

#### Apply Labels

When using the _Spike or Fragment_ range setting, the label will be applied until the marker trajectory is discontinued with a gap that is larger than the maximum gap defined above. When using the _All or Selected_ range setting, the label will be applied to the entire trajectory or just the selected ranges.

#### **Forwards**

Assigns the selected label onto a marker for current frame and frames forward.

#### **Backwards**

Assigns selected label onto a marker for current frame and frames backward.

#### **Forwards & backwards**

Assigns selected label onto the marker for current frame, frames forward, and frames backward.
