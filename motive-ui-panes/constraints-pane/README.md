# Constraints Pane

This page provides instructions on how to use the Constraints pane in Motive.

## **Overview**

The Constraints pane is intended to allow further optimization around the solver constraints which currently only includes asset model markers. It also allows users to change the name and color of markers for an asset. The asset that you are working with is linked to the selection in Motive unless the “Link to 3D Selection” toggle next to the asset name is turned off.

## Setting Constraints

The default view of the Constraints pane shows the labels and color either of which can be modified to customize your asset. You can also enable three other columns that help control how the solver interacts with markers. The sections below the details for each of these columns.

### Changing Marker Names

**Constraints (Names)**

The “Constraint” column lists the labels of asset model markers associated with an asset. Labels can be modified in the Constraints pane by slow clicking or right-clicking (context menu). You can sort the “Constraint” column alphabetically ascending or descending. However, by default, this column sorts by the asset definition. This uses the internal asset definition to order the constraints and allows you to change this order using the context menu. Changing the order of the constraints will also change the order of the asset model marker names in the Labels pane. This can be helpful to define custom marker ordering for manual labeling.

![](<../../.gitbook/assets/image (622).png>)

### Changing Marker Colors

**Color**

The color column allows you to change the color of a constraint. This allows you to assign custom colors to different markers associated with an asset. The constraint’s color property has a “rainbow” macro available. This allows you to link the color of the marker to the color defined by the asset.

![Rigid body with blue colors assigned for all of its markers.](<../../.gitbook/assets/image (384).png>)

![Changing three of the markers to green using the Constraints pane. Yellow highlight indicates the selected constraint.](<../../.gitbook/assets/image (300) (1).png>)

### Changing Marker IDs

#### **Member ID**

The _MemberID_ column is mostly just used to view unique ID values assigned to each constraint. It typically is just a reflection of the original ordering of the constraints.

#### **Active ID**

The _ActiveID_ column allows you to view and modify Active Marker ID values. Typically Active ID values are automatically assigned on asset creation or when adding a marker, but this gives you a higher level of insight and control in the process.

![Member IDs and Active IDs shown in the Constraints pane.](<../../.gitbook/assets/image (313).png>)

### Changing Solver Weight

#### **Weight**

The _Weight_ column allows you to tell the solver to prefer a marker when solving the asset data with less than an optimal amount of marker information. For example, the hands are weighted slightly higher for the baseline and core Marker Sets to help preference the end effectors. However, editing this property is not typically recommended.

## Modifying Constraints using the Properties Pane

You can also view and modify the constraints setting from the [Properties pane](../properties-pane/). When you select a constraint from the list, the properties of the selected constraints will be listed under the [Properties pane](../properties-pane/). This is just another way to interface with the same information, but in addition, you can also modify XYZ location of the asset model markers on a Rigid Body or a skeletal bone. Note that these position values are in respect to the local coordinate system of the corresponding Rigid Body or the bone.

![](<../../.gitbook/assets/image (298) (1).png>)

## Export/Import Constraints

You can also export configured constraints, or import them, using the Constraints pane. To do this, simply click on the [![ContextMenu dotdotdot.png](https://v30.wiki.optitrack.com/images/c/c4/ContextMenu_dotdotdot.png)](https://v30.wiki.optitrack.com/index.php?title=File:ContextMenu_dotdotdot.png), and there will be options to export, import, and generate constraints.

Exporting constraints makes an XML file containing the names, colors, and marker stick definitions for manual editing. Importing reads the (.xml) files made when exporting. Generating constraints resets the asset back to the default state, if applicable.

![](<../../.gitbook/assets/image (609).png>)
