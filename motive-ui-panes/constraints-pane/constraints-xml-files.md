---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/constraints-pane/constraints-xml-files
---

# Constraints XML Files

## **Overview**

This page includes detailed step-by-step instructions on customizing constraint XML files for assets. In order to customize the marker labels, marker colors, marker sticks, and weights for an asset, a constraint XML file may be exported, customized, and loaded back into Motive. Alternately, the [Constraints pane](./) can be used to modify the marker names, color, and weight and the [Builder pane](../builder-pane.md) can be used to customize marker sticks directly in Motive. This process has been standardized between asset types with the only exception being that marker sticks for Rigid Bodies does not work in Motive 3.0.

## Steps

### 1. Export a Constraint XML File

**a)** First, create an asset using the [Builder pane](../builder-pane.md) or the 3D context menu.

**b)** Right-click on the asset in the [Assets pane](../assets-pane.md) and select _Export Markers_. Alternately, you can click the "..." menu at the top of the [Constraints pane](./).

**c)** In the export dialog window, select a directory to save the constraints XML file. Click _Save_ to export.

![Export Markers option shown in the Assets pane.](<../../.gitbook/assets/image (923).png>)

### 2. Customize a Constraint XML File

#### **Customize Marker Labels**

**a)** Open the exported XML file using a text editor. It will contain corresponding marker label information under the \<marker\_names> section.

**b)** Customize the marker labels from the XML file. Under the \<marker\_names> section of the XML, modify labels for the _name_ variables with the desired name, but do not change labels for _old\_name_ variables. The order of the markers should remain the same unless you would like to change the labeling order.

**c)** If you changed marker labels, the corresponding marker names must also be renamed within the \<marker\_colors> and \<marker\_sticks> sections as well. Otherwise, the marker colors and marker sticks will not be defined properly.

![Modifying marker labels. Default HeadTop marker label is changed to NewHeadTop for Skeletons using the XML template file.](<../../.gitbook/assets/image (402).png>)

#### **Customize Marker Sticks and Colors**

**a)** To customize the marker colors, sticks, or weight, open the exported XML file using a text editor and scroll down to the \<marker\_colors> and/or \<marker\_sticks> sections. If the \<marker\_colors> and/or \<marker\_sticks> sections do not exist in the exported XML file, then you could be using an old Skeleton created before Motive 1.10. [Updating](../../motive/skeleton-tracking.md) and exporting the old Skeleton will provide these sections in the XML.

![MarkerColors definition section in the Skeleton template XML file.](<../../.gitbook/assets/image (370).png>) ![MarkerSticks definition section in the Skeleton template XML file.](<../../.gitbook/assets/image (427).png>)

**b)** You can customize the marker colors and the marker sticks in these sections. For each marker name, you must use exactly same marker labels that were defined by the \<marker\_names> section of the same XML file. If any marker label was changed in the \<marker\_names> section, the changed name must be reflected in the respective colors and sticks definitions as well. In other words, if a _Custom\_Name_ was assigned under _name_ for a label in the \<marker\_names> section _\<marker name="Custom\_Name" old\_name="Name" />_, the same _Custom\_Name_ must be used to rename all the respective marker names within \<marker\_colors> and/or \<marker\_sticks> sections of the XML.

* **Marker Colors:** For each marker in a Skeleton, there will be a respective name and color definitions under the \<marker\_colors> section of the XML. To change corresponding marker colors for the template, edit the RGB parameter and save the XML file.
* **Marker Sticks:** A marker stick is simply a line interconnecting two labeled markers within the Skeleton. Each marker stick definition consists of two marker labels for creating a marker stick and a RGB value for its color. To modify the marker sticks, edit the marker names and the color values. You can also define additional marker sticks by copying the format from the other marker stick definitions.

### 3. Import a Constraint XML File

#### **Creating Skeletons with Custom Constraints**

Now that you have customized the XML file, it can be loaded each time when creating new Skeletons. In the [Builder pane](../builder-pane.md) under Skeleton creation options, select the corresponding Marker Set. Next, under the Constraints drop down menu, select "Choose File..." to find and import the XML file. When you [Create](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#creating-Skeletons) the Skeleton, the custom marker labels, marker colors, and marker sticks will be applied.

If you manually [added extra markers](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md#adding-removing-Skeleton-markers) to a Skeleton, then you must import the constraint XML file after adding the extra markers or just modify the extra markers using the [Constraints pane](./) and [Builder pane](../builder-pane.md).

{% hint style="info" %}
Note: For Skeletons, modified Marker XML files can only be used with the same Marker Set template. In other words, if you exported a [Baseline (41) Skeleton](../../markersets/full-body/baseline-41.md) and modified the constraints XML file, the same Baseline (41) Marker Set will need to be created in order to import the customized XML file.
{% endhint %}

![Loading Skeleton XML when creating a new Skeleton.](<../../.gitbook/assets/image (1258).png>) ![Customized Skeleton markers labels.](<../../.gitbook/assets/image (1105).png>)

#### **Import Constraints for Existing Assets**

You can also apply a customized constraint XML file to an existing asset using the import constraints feature. Right-click on an asset in the Assets pane (or click the "..." menu in the Constraints pane) and select **Import Constraints** from the menu. This will bring up a dialog window for importing a constraint XML file. Import the customized XML template and the modifications will be applied to the asset. This feature must be used if extra markers were added to the default XML template.

![Renaming existing Skeleton by importing a XML template file.](<../../.gitbook/assets/image (1107).png>)
