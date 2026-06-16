---
description: Learn how to work with different types of trackable assets in Motive.
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/assets
---

# Assets

## Overview

In Motive, an Asset is a set of markers that define a specific object to be tracked in the capture. Asset tracking data can be sent to other pipelines (e.g., animations and biomechanics) for extended applications.&#x20;

When an asset is created, Motive automatically applies a set of predefined labels to the reconstructed trajectories (markers) using Motive's tracking and labeling algorithms. Motive calculates the position and orientation of the asset using the labeled markers.&#x20;

There are three types of assets, covering a full range of tracking needs:

* [Rigid Bodies: ](../rigid-body-tracking/) used to track rigid, unmalleable, objects.&#x20;
* [Skeletons:](../skeleton-tracking.md)  used to track human motions.&#x20;
* [Trained Markersets:  ](../trained-markersets.md)used to track any object that is not a Rigid Body or a pre-defined Skeleton.&#x20;

This article provides an introduction to working with existing assets. For information specific to each asset type, click the links in the list above. Visit the [Builder pane ](../../motive-ui-panes/builder-pane.md)page for detailed instructions to create and modify each asset type.

<div><figure><img src="../../.gitbook/assets/Rigid Body in Viewport with Labels (3).png" alt="" width="377"><figcaption><p>An auto-labeled Rigid Body. </p></figcaption></figure> <figure><img src="../../.gitbook/assets/Skeleton Labels displayed (2).png" alt="" width="454"><figcaption><p>An auto-labeled skeleton.</p></figcaption></figure></div>

<figure><img src="../../.gitbook/assets/Trained Markerset with labels (1).png" alt="" width="283"><figcaption><p>An auto-labeled Trained Markerset</p></figcaption></figure>

{% hint style="info" %}
Assets can be created in _Live_ mode (before capture) or in post-production (_Edit_ mode, using a loaded _TAKE_).&#x20;

If new assets are created during post-production, the take must be [reconstructed and auto-labeled](../reconstruction-and-2d-mode.md) to apply the changes to the 3D data.
{% endhint %}

### Video Quick Start Guide:  Asset Creation&#x20;

The following video demonstrates the asset creation workflow.&#x20;

{% embed url="https://youtu.be/HyrHhaRVOaM?si=zNe9sj79g_IIYLuE&t=185" %}

## Assets Pane

Assets used in the current _TAKE_ are displayed in and managed from the [Assets pane](../../motive-ui-panes/assets-pane.md). To open the Assets pane, click  the <img src="../../.gitbook/assets/Assets Pane button (1).png" alt="" data-size="line"> icon.

<figure><img src="../../.gitbook/assets/Assets Pane - Skellies and RBs (1).png" alt="" width="311"><figcaption><p>The Assets Pane.</p></figcaption></figure>

When an asset is selected, either from the Assets pane or from the [3D Perspective view](../../motive-ui-panes/viewport.md#perspective-view), its related properties are displayed in the [Properties pane](/broken/pages/sQK8scBDhFagaBZY6IVS).

## Copying Assets

Follow these steps to copy an asset to other recorded _TAKES_ or to the Live capture.&#x20;

### **Copy Assets to a Recorded&#x20;**_**Take**_

1. Right-click the desired _Take_ to open the context menu.
2. Select _Copy Assets to Takes._&#x20;
3. This will bring up a dialog window to select the assets to move.
4. Select the assets to copy and click _Done_.

<figure><img src="../../.gitbook/assets/Copy Assets to Take.png" alt="" width="319"><figcaption><p>Copy Asset Dialog Box</p></figcaption></figure>

### **Copy Assets to Multiple Recorded&#x20;**_**Takes**_

1. Use shift-click or ctrl-click to select _Takes_ from the [Data pane](../../motive-ui-panes/data-pane.md) until all the desired _Takes_ are selected.&#x20;
2. Right-click any of the selected _Takes_. This should copy the assets you selected to all the selected _Takes_ in the _Data_ pane to open the context menu.
3. Select _Copy Assets to Takes._&#x20;
4. This will bring up a dialog window to select the assets to move.
5. Select the assets to copy and click _Done_.

### **Copy Assets from a Recorded&#x20;**_**Take**_ to the Live Capture

1. To copy multiple assets, use shift-click or ctrl-click to select all of them in the [Assets pane](../../motive-ui-panes/assets-pane.md).
2. Right-click (one of) the asset(s).
3. Select _Copy Assets to Live._
4. The asset(s) will now appear in the Assets pane in Live mode. Motive will recognize the asset when  it enters the volume, based on its unique marker placement.&#x20;

## Exporting Assets

Assets can be exported into the Motive user profile file (.MOTIVE), where they can then be imported into different takes without creating a new asset.&#x20;

The [user profile](../motive-basics.md) is a text-readable file that contains various configuration settings, including the asset definitions. With regard to assets, profiles specifically store the spatial relationship of each marker in the asset, ensuring that only the identical marker arrangement will be recognized and defined with the imported asset.

#### To Export Assets:

1. From the _File_ menu, select _Export Assets..._
2. This will copy all the asset definitions in either Live-mode or in the current _Take_ file into the user profile.&#x20;

<figure><img src="../../.gitbook/assets/File Menu - Export Assets selected (1).png" alt="" width="165"><figcaption><p>The Motive File Menu.</p></figcaption></figure>

#### Export User Profile

The option to export the user profile allows Motive users to save custom profiles as part of their project folders.&#x20;

To export a user profile:

1. From the _File_ menu, select _Export Profile_ As...
2. The _Export Profile_ window will open.
3. Navigate to the folder where you want the exported profile stored, or use the Motive default folder.
4. Select the profile elements to export. Options are: Properties, Hotkeys/Mouse Controls, Sessions, and Assets.&#x20;
5. Name the file, using the File Type: _Motive User Profile (\*.motive)_.
6. Click Export.&#x20;

![Exporting user profile options.](<../../.gitbook/assets/image (124) (1) (1) (1) (4).png>)

