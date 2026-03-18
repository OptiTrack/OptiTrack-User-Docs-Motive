# Assets

This page covers basic types of trackable assets in Motive. The assets in Motive are used for both tracking of the objects and [labeling](../labeling.md) of 3D markers in Motive, and they are managed under the Assets pane which can be opened by clicking on the [![Toolbar Assets Icon.png](https://v30.wiki.optitrack.com/images/2/2c/Toolbar_Assets_Icon.png)](https://v30.wiki.optitrack.com/index.php?title=File:Toolbar_Assets_Icon.png) icon. Each type of asset is further explained in the [related pages](./#related-pages).

## Overview

![A Rigid Body in Motive with auto-labeled markers](<../../.gitbook/assets/image (127).png>) ![A Skeleton in Motive with auto-labeled markers](<../../.gitbook/assets/image (774).png>)

Once Motive is prepared, the next step is to place markers on the subject and create corresponding **assets**. There are three different types of assets in Motive:

* Marker Set
* Rigid Body
* Skeleton

For each Take, involved assets are displayed in the [Assets pane](../../motive-ui-panes/assets-pane.md), and the related properties show up at the [Properties pane](../../motive-ui-panes/properties-pane/properties-pane-rigid-body.md) when an asset is selected within Motive.

The Marker Set is a list of marker labels that are used to annotate reconstructed markers. Marker Sets should only be used in situations where it is not possible to define a Rigid Body or Skeleton. In this case, the user will manually label markers in post-processing. When doing so, having a defined set of labels (Marker Set) makes this process much easier. Marker Sets within a _Take_ will be listed in the [Labels pane](../../motive-ui-panes/labels-pane.md), and each label can be assigned through the [Labeling](../labeling.md) process.

**Rigid body** and **Skeleton** assets are the _Tracking Models_. Rigid bodies are created for tracking rigid objects, and Skeleton assets are created for tracking human motions. These assets automatically apply a set of predefined labels to reconstructed trajectories using Motive's tracking and labeling algorithms, and Motive uses the labeled markers to calculate the position and orientation of the Rigid Body or Skeleton Segment. Both Rigid Body and Skeleton tracking data can be sent to other pipelines (e.g. animations and biomechanics) for extended applications. If new Skeletons or Rigid Bodies are created during post-processing, the take will need to be [reconstructed and auto-labeled](../reconstruction-and-2d-mode.md) in order to apply the changes to the 3D data.

{% embed url="https://www.youtube.com/watch?t=184s&v=aK1cpr6ShPE" %}
Motive Quick Start - Subject Setup
{% endembed %}

{% hint style="info" %}
Assets may be created during both Live (before capture) or Post (after capture, from a loaded TAK) captures.
{% endhint %}

## Copying Assets

The [Assets pane](../../motive-ui-panes/assets-pane.md) lists out all assets that are available in the current capture. You can easily copy these assets onto other recorded Take(s) or to the live capture by doing the following:

**Copying Assets to a Recorded \_Take**\_

In order to copy and paste assets onto another _Take_, right-click on the desired _Take_ to bring up the context menu and choose **Copy Assets to Takes**. This will bring up a dialog window for selecting which assets to move.

**Copying Assets to Multiple Recorded \_Take(s)**\_

If you wish to copy assets to multiple _Takes_, select multiple takes from the _Data_ pane until the desired takes are all highlighted. Repeat the steps you took above for copying a single _Take_ by right-clicking on any of the selected _Takes_. This should copy the assets you selected to all the selected _Takes_ in the _Data_ pane.

**Copying Assets from a Recorded \_Take**\_\*\* to the Live Capture\*\*

If you have a list of assets in a Take that you wish to import into the live capture, you can simply do this by right-clicking on the desired assets on the [Assets pane](../../motive-ui-panes/assets-pane.md), and selecting Copy Assets to Live.

![Copying assets to multiple Takes](<../../.gitbook/assets/image (160).png>)

{% hint style="info" %}
For selecting multiple items, use Shift-click or Ctrl-click.
{% endhint %}

## Exporting Assets

Assets can be exported into Motive user profile (.MOTIVE) file if it needs to be re-imported. The [user profile](../motive-basics.md) is a text-readable file that can contain various configuration settings in Motive; including the asset definitions.

When the asset definition(s) is exported to a MOTIVE user profile, it stores marker arrangements calibrated in each asset, and they can be imported into different takes without creating a new one in Motive. Note that these files specifically store the spatial relationship of each marker, and therefore, only the identical marker arrangements will be recognized and defined with the imported asset.

To export the assets, go to _Files_ tab → _Export Assets_ to export all of the assets in the Live-mode or in the current TAK file. You can also use _Files_ tab → _Export Profile_ to export other software settings including the assets.

![Exporting Assets into the User Profile.](<../../.gitbook/assets/image (140) (1) (1) (1) (1) (1) (1) (5).png>) ![Exporting user profile that includes assets. This dialogue window is from the Export Profile As... option.](<../../.gitbook/assets/image (124) (1) (1) (1) (1) (1) (1) (6).png>)
