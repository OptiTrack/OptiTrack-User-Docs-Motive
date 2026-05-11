---
description: An overview of common features available in the Properties Pane.
---

# Properties Pane

The Properties pane can be accessed by clicking on the <img src="../../.gitbook/assets/Properties Pane button (1).png" alt="Toolbar Properties Icon.png" data-size="line"> icon on the toolbar.

## Overview

The Properties pane is used to view and modify properties associated with _Takes_, assets, and devices that determine how the corresponding items are displayed and tracked. Properties can be modified both in Live and Edit mode. Default creation properties are listed under the [Application Settings](../settings/).

This page covers features and functions common to the Property pane regardless of what is selected. For a detailed description of each property, please see the following pages:

* [Properties: Take](properties-pane-take.md)
* [Properties: Trained Markerset](properties-pane-trained-markerset.md)
* [Properties: Rigid Body](properties-pane-rigid-body.md)
* [Properties: Skeleton](properties-pane-skeleton.md)
* [Properties: Camera](properties-pane-camera.md)
* [Properties: eSync](properties-pane-esync2.md)
* [Properties: Force Plates](properties-pane-force-plates.md)
* [Properties: NI-DAQ](properties-pane-ni-daq.md)



{% embed url="https://vimeo.com/259377119/3582eb0dcd" %}

The Properties pane is accessed by clicking the <img src="../../.gitbook/assets/Properties Pane button.png" alt="" data-size="line"> icon on the toolbar. The pane is blank if nothing is selected, or when items that do not have any common properties are selected.&#x20;

<img src="../../.gitbook/assets/Properties - nothing selected.png" alt="Properties pane when nothing is selected." width="310">

When a single Take, asset, or device is selected, the Properties pane displays properties specific to the selection. See image at left, below.

When multiple items are selected, only common properties are displayed; properties that are not shared are not included. Where the selected assets have different values, Motive displays the text _Mixed_ or places the toggle button in the middle position <img src="../../.gitbook/assets/Properties - Mixed values for toggle switch (2).png" alt="" data-size="line">.&#x20;

{% hint style="warning" %}
Changes made in the Properties pane are applied to all selected objects.&#x20;
{% endhint %}

<div><figure><img src="../../.gitbook/assets/Properties - Rigid Body standard (1).png" alt="" width="311"><figcaption><p>Standard Properties for a Rigid Body.</p></figcaption></figure> <figure><img src="../../.gitbook/assets/Properties - standard mixed assets.png" alt="" width="312"><figcaption><p>Common properties for a Rigid Body and a Skeleton.</p></figcaption></figure></div>

## Pane Options

Buttons at the top of the Properties pane control what is displayed. Click the <img src="../../.gitbook/assets/Motive Context Menu (20).png" alt="" data-size="line"> button in the top right corner to see all options.

<figure><img src="../../.gitbook/assets/Properties Pane - Show Advanced (1).png" alt="" width="152"><figcaption></figcaption></figure>

### **Lock Selection**

Click the lock icon to lock the display to the currently selected item. The pane will continue to display those properties until the lock is removed, regardless of what is selected in the [3D Viewport](../viewport.md) or the [Assets pane](../assets-pane.md). When unlocked (the default position), the pane updates to reflect the current active selection.

<div><figure><img src="../../.gitbook/assets/Properties - unlocked to selection.png" alt=""><figcaption><p>Display unlocked.</p></figcaption></figure> <figure><img src="../../.gitbook/assets/Properties - locked to selection.png" alt=""><figcaption><p>Display locked.</p></figcaption></figure></div>

### **Show Advanced**

The Properties pane contains advanced settings that are hidden by default. To access these settings, click the <img src="../../.gitbook/assets/Motive Context Menu (19).png" alt="" data-size="line"> button on the top-right corner of the pane and select _Show Advanced._&#x20;

### **Edit Advanced**&#x20;

Customize the Standard view to show only the settings that are needed specifically for your capture application. Click the <img src="../../.gitbook/assets/Motive Context Menu (19).png" alt="" data-size="line"> button on the top-right corner of the pane and select _Edit Advanced._&#x20;

Checked items will appear in the Standard view while unchecked items will only be visible when _Show Advanced_ is selected.&#x20;

<figure><img src="../../.gitbook/assets/Properties - Edit Advanced.png" alt="" width="314"><figcaption><p>Properties pane: Edit Advanced. </p></figcaption></figure>

### Reset All

This option removes all customizations made to the properties of the selected asset. Use with caution.
