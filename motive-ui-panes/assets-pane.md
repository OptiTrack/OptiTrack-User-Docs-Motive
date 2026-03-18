# Assets Pane

The Assets pane in Motive lists out all of the assets involved in the Live, or recorded, capture and allows users to manage them. This pane can be accessed under the [View tab](toolbar-command-bar.md#view) in Motive or by clicking the <img src="../.gitbook/assets/Assets Pane button.png" alt="Screenshot of the Assets Pane button from the Motive toolbar. " data-size="original"> icon on the main toolbar.

{% embed url="https://vimeo.com/259377033/8f5fd829ab?embedded=true&owner=15736845&source=vimeo_logo" %}

## Overview

![](<../.gitbook/assets/image (478).png>)

## Assets (Current Take)

A list of all assets associated with the take is displayed in the Assets pane. Here, view the assets and you can right click on an asset to export, remove, or rename selected asset from the current take.

You can also enable or disable assets by checking or unchecking, the box next to each asset. Only enabled assets will be visible in the 3D viewport and used by the [auto-labeler](../motive/labeling.md#auto-label) to label the markers associated with respective assets.

## Context Menu Options

In the Assets pane, the context menu for involved assets can be accessed by clicking on the <img src="../.gitbook/assets/image (124).png" alt="" data-size="line"> context menu or by right-clicking on a selected _Take(s)_. The context menu lists out available actions for the corresponding assets.

### All Assets

![Context menu of a Skeleton asset.](<../.gitbook/assets/image (477).png>)

#### **Export Asset**

Exports selected Rigid Bodies into either a Motive file (.motive) or CSV. Exports selected Skeletons into either Motive file (.motive) or an FBX file.

#### **Export Constraints**

Exports Skeleton marker template constraint XML file. The exported constraints files contain marker can be modified and imported again.

#### **Import Constraints**

Imports Skeleton marker template constraint XML file onto the selected asset. If you wish to apply the imported XML for labeling, all of the Skeleton markers need to be unlabeled and auto-labeled again.

#### **Generate Constraints**

Imports the default Skeleton marker template constraint XML files. This basically colors the labeled markers and creates marker sticks that inter-connects between each of consecutive labels.

#### **Solve**

This is only possible when post-processing a recorded TAK. Solving an Asset bakes its 6 DoF data into the recording. Once the asset is solved, Motive plays back the recording from the recorded _Solved_ data.

### For Skeleton Assets

#### **Recalibrate From Markers**

Exports FBX actor of the Skeleton.

#### **Recalibrate From Markers**

Re-calibrates an existing Skeleton. This feature is essentially same as re-creating a Skeleton using the same Skeleton Marker Set. See [Skeleton Tracking](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md) page for more information on using the Skeleton template XML files.
