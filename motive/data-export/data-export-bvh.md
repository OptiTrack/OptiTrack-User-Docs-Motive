# Data Export: BVH

## BVH File Format

Motive can export tracking data in BioVision Hierarchy (BVH) file format. Exported BVH files do not include individual marker data. Instead, a selected skeleton is exported using hierarchical segment relationships. In a BVH file, the 3D location of a primary skeleton segment (Hips) is exported, and data on subsequent segments are recorded by using joint angles and segment parameters. Only one skeleton is exported for each BVH file, and it contains the fundamental skeleton definition that is required for characterizing the skeleton in other pipelines.

{% hint style="danger" %}
**Notes on relative joint angles generated in Motive:** Joint angles generated and exported from Motive are intended for basic visualization purposes only and should not be used for any type of biomechanical or clinical analysis.
{% endhint %}

General Export Options

|               Option              | Description                                                                                                                                                                                                                                                                                                           |
| :-------------------------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|             Frame Rate            | Number of samples included per every second of exported data.                                                                                                                                                                                                                                                         |
|            Start Frame            | Start frame of the exported data. You can either set it to the recorded first frame of the exported _Take_ or to the start of the working range, or scope range, as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) or in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md). |
|             End Frame             | End frame of the exported data. You can either set it to the recorded end frame of the exported _Take_ or to the end of the working range, or scope range, as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) of in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md).       |
|               Scale               | Apply scaling to the exported tracking data.                                                                                                                                                                                                                                                                          |
|               Units               | Sets the length units to use for exported data.                                                                                                                                                                                                                                                                       |
|          Axis Convention          | Sets the axis convention on exported data. This can be set to a custom convention, or preset conventions for exporting to Motion Builder or Visual3D/Motion Monitor.                                                                                                                                                  |
| <p>X Axis<br>Y Axis<br>Z Axis</p> | Allows customization of the axis convention in the exported file by determining which positional data to be included in the corresponding data set.                                                                                                                                                                   |

BVH Specific Export Options

|        Option       |                                                                             Description                                                                             |
| :-----------------: | :-----------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|  Single Joint Torso | When this is set to true, there will be only one skeleton segment for the torso. When set to false, there will be extra joints on the torso, above the hip segment. |
|    Hands Downward   |                                                  Sets the exported skeleton base pose to use hands facing downward.                                                 |
| MotionBuilder Names |                                Sets the name of each skeletal segment according to the bone naming convention used in MotionBuilder.                                |
|    Skeleton Names   |                                                         Set this to the name of the skeleton to be exported.                                                        |

![MotionBuilder BVH Naming Conventions and Segments Hierarchy (1)](<../../.gitbook/assets/image (636).png>) ![MotionBuilder BVH Naming Conventions and Segments Hierarchy (2)](<../../.gitbook/assets/image (407).png>)
