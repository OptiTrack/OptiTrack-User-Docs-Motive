---
description: This page provides instructions for using the Constraints pane in Motive.
---

# Constraints Pane

## **Overview**

The reconstructed 3D markers that comprise an asset are known as constraints in Motive. The Constraints pane provides information and tools for working with solver constraints for all asset types:  [Rigid Bodies](../../motive/rigid-body-tracking/), [Skeletons](../../motive/skeleton-tracking.md), and [Trained Markersets](../../motive/trained-markersets.md).&#x20;

To open, click the <img src="../../.gitbook/assets/Constraints Pane button.png" alt="" data-size="line"> button on the Motive toolbar.

<figure><img src="../../.gitbook/assets/Constraints Pane - All assets.png" alt="" width="309"><figcaption><p>The Constraints pane. </p></figcaption></figure>

## Asset Selection

By default, the Constraints pane will display the constraints for the asset(s) selected in either the [3D Viewport](../viewport.md) or the [Assets Pane](../assets-pane.md). If none is selected, the pane will display the constraints for _-All-_ the assets in the Live volume or in the _TAKE_, when in edit mode.&#x20;

The pane is locked to the selection whenever the <img src="../../.gitbook/assets/Link to 3D selection button (2).png" alt="" data-size="line"> button is active. Click the button to open the menu to select a different asset.&#x20;

<figure><img src="../../.gitbook/assets/Constraints Pane - unlock asset selection.png" alt="" width="308"><figcaption><p>Selecting an Asset from the Constraints Pane.</p></figcaption></figure>

## Customize Pane Columns

The default view of the Constraints pane includes the Constraint (or label), Type, and Color. Right click the column header to add or remove columns from the view.

<figure><img src="../../.gitbook/assets/Constraints - Customize columns.png" alt="" width="308"><figcaption><p>Select columns to display.</p></figcaption></figure>

#### **Constraint**

The Constraint column displays the marker labels associated with an asset. When the Asset selection is set to _-All-_, the asset name is included as a prefix to the marker label.

{% hint style="info" %}
* Skeleton templates include pre-defined labels that correspond to the marker's location and easily import into other pipelines for biomechanical analysis or animation.&#x20;
* Rigid Bodies and Trained Markersets are auto-labeled with generic, sequential labels.
{% endhint %}

#### MemberID

The MemberID column displays the unique ID value assigned to each constraint. Typically, this is the original order of the constraints.

#### Type

There are four types of constraints:

* **Marker:**  The constraint is associated with either a passive or active marker. Designated with the <img src="../../.gitbook/assets/Constraints Pane - Marker Type (2).png" alt="" data-size="line"> icon in the _Type_ column.
* **Calibration Marker:**  Some biomechanical skeleton templates use calibration markers during asset creation that are subsequently removed prior to motion capture. In the 3D viewport, the constraints for these markers appear in red. Designated with the <img src="../../.gitbook/assets/Constraints Pane - Marker Type (2).png" alt="" data-size="line"> icon in the _Type_ column.
* **6 DoF:**  The constraint formed by a Rigid Body on a skeleton created using a Rigid Body Skeleton template. Designated with the <img src="../../.gitbook/assets/Constraints Pane - 6 DoF Type.png" alt="" data-size="line"> icon in the _Type_ column.
* **IMU:**  The constraint associated with a [sensor-fused IMU](/broken/pages/ysdyrsuQyF9qn6xMu4ix) in a rigid body. Designated with the <img src="../../.gitbook/assets/Constraints Pane - IMU Type.png" alt="" data-size="line"> icon in the _Type_ column.

#### Color

The color column displays the color assigned to the constraint. The option with a <img src="../../.gitbook/assets/Color linked to Asset (1).png" alt="" data-size="line"> rainbow effect links the constraint to the color defined by the asset.

#### ActiveID

The _ActiveID_ column allows you to view and modify Active Marker ID values. Active ID values are automatically assigned during asset creation or when adding a marker, but this gives you a higher level of insight and control over the process.

#### Weight

Weight is the degree to which an individual constraint influences the 3D solve of an asset. Specifically, adjusting the weight tells the solver to prefer that marker when solving the asset data with less than an optimal amount of marker information. For example, the hands are weighted slightly higher for the baseline and core skeleton Marker Sets to preference the end effectors.&#x20;

Editing this property is not typically recommended.

## Modify Constraints

{% hint style="info" %}
To see constraints as well as markers in the 3D Viewport, click the Visual Aids <img src="../../.gitbook/assets/Motive Visual Options button.png" alt="" data-size="line"> button and select _Marker Constraints_ _-> Show All_.&#x20;
{% endhint %}

### Add or Remove Constraints

Select the marker(s) to add to or remove from the asset definition in the 3D Viewport then click either the Add <img src="../../.gitbook/assets/Add Button - Active.png" alt="" data-size="line"> button or the Remove <img src="../../.gitbook/assets/Remove button - active.png" alt="" data-size="line"> button at the bottom of the pane.

<figure><img src="../../.gitbook/assets/Constraints - Add or remove.png" alt=""><figcaption><p>Click to Add selected markers.</p></figcaption></figure>

### Rename Constraints

To give a marker constraint a more meaningful name than the one auto-assigned when the asset is created, right-click the constraint name and select _Rename_ from the context menu. Alternately, click twice on the constraint name to open the field for editing.

{% hint style="info" %}
We recommend using the single asset view rather than _-All-_ when relabeling markers from the Constraints pane.
{% endhint %}

You can also import a list of constraint properties, including names, for all asset types. See the section [Export/Import Constraints](./#export-import-constraints), below and the page [Constraints XML Files](constraints-xml-files.md) for more details.

#### Trained Markerset Copy and Paste

Import label names for Trained Markerset assets with a quick copy and paste of text. This is useful if you've already mapped out the asset, either during the design phase or while placing the markers.&#x20;

1. Copy the desired labels to the clipboard.
2. Select the Markerset so the Constraints pane displays only its marker constraints. Alternately,  click the <img src="../../.gitbook/assets/Link to 3D selection button.png" alt="" data-size="line"> button to deselect _Lock Selection to Asset_, and select the Markerset from the dropdown list.&#x20;
3. Left click the Constraints Pane.
4. Use _Ctrl + V_ to paste the label names to the pane.&#x20;

<figure><img src="../../.gitbook/assets/Constraints Pane - Imported labels for TM.png" alt=""><figcaption><p>Constraints Pane with new label names pasted in.</p></figcaption></figure>

The pasted labels will display at the bottom of the list. Click the <img src="../../.gitbook/assets/Select or Edit 3D Object.png" alt="" data-size="line"> Mouse Control button in the 3D Viewport or use the _D hotkey_ to open the [Quick Label](../../motive/labeling.md#quick-label-mode) tool to quickly assign the copied labels to the correct markers.&#x20;

Please see the [Labeling](../../motive/labeling.md) page for more information on using the Quick Labels tool.

### Sort and Reorder Constraints

By default, the _Constraints_ column sorts by the asset definition, or the order in which the markers were selected when the asset was created. Click the column header to sort the column alphabetically in ascending or descending order, then click again to return to the default.&#x20;

<figure><img src="../../.gitbook/assets/Constraints Pane - context menu.png" alt="" width="312"><figcaption><p>Right-click Context menu.</p></figcaption></figure>

There are two methods to change the order of the constraints in the internal asset definition:

* Right-click a constraint label and select an option to move up or down from its present location.
* Drag and drop labels into the desired order.

Reordering constraints helps to define custom marker sequences for manual labeling. Changes made to the order will also be reflected in the [Labels pane](../labels-pane.md).&#x20;

### Change Marker Color

By default, constraints use the color selected in the asset properties, as indicated by the rainbow <img src="../../.gitbook/assets/Color linked to Asset.png" alt="" data-size="line"> color icon.&#x20;

<div><img src="../../.gitbook/assets/Constraints - RB with Asset color.png" alt="Rigid body with all constraints set to use the default asset color." width="563"> <figure><img src="../../.gitbook/assets/Constraints - RB with custom colors.png" alt="" width="563"><figcaption><p>Rigid Body with custom colors assigned to four markers.</p></figcaption></figure></div>

## Modify Constraints from the Properties Pane

You can modify the following additional constraint settings from the [Properties pane](../properties-pane/) when a constraint is selected in the Constraints pane.

* Position and Rotation:  adjust the x/y/z coordinates of the constraint, in respect to the local coordinate system of the corresponding asset or bone.

{% hint style="warning" %}
Before making any changes to the x/y/z coordinates, save the current values by clicking the <img src="../../.gitbook/assets/Motive Context Menu (1).png" alt="" data-size="line"> button to the right of the fields. Select _Set as default._ This will change the reset value from the Motive global default to the specific coordinates for the constraints.&#x20;
{% endhint %}

<div><figure><img src="../../.gitbook/assets/Constraint Properties - Set Default position (1).png" alt=""><figcaption><p>Reset Position to Motive global default.</p></figcaption></figure> <figure><img src="../../.gitbook/assets/Constraint Properties - new Default position.png" alt=""><figcaption><p>Reset Position after saving position coordinates.</p></figcaption></figure></div>

* Marker Diameter:  view or change the diameter of an individual marker.
* Constraint Type:  Motive assigns the constraint type during the auto-label process. The user should not need to adjust this property.

![Constraint Properties.](<../../.gitbook/assets/Properties - constraint.png>)

## Export/Import Constraints

You can also export configured constraints, or import them, using the Constraints pane. To do this, simply click on the <img src="../../.gitbook/assets/image (1469).png" alt="" data-size="line"> context menu. There are options to export, import, and generate constraints.

Exporting constraints makes an XML file containing the names, colors, marker stick definitions, and weights for manual editing. Importing reads the (.xml) files made when exporting. Generating constraints resets the asset back to the default state, if applicable.

Please see the page [Constraints XML Files](constraints-xml-files.md) for more information on working with these files.

![](<../../.gitbook/assets/image (429).png>)
