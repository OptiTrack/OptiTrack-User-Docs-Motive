---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/trained-markersets
---

# Trained Markersets

## Quick Start Guide

Trained Markersets allow you to create Assets from any object that is not a Rigid Body or a pre-defined Skeleton. This allows you to track anything from a jump rope, to a dog, to a flag, to anything in between.&#x20;

Please follow the steps below to get started.&#x20;

<figure><img src="../.gitbook/assets/image (72).png" alt=""><figcaption><p>Trained Markerset:  Auto-Generate Asset </p></figcaption></figure>

### Auto-Generate Asset

{% hint style="warning" %}
In order to get the best training data, it is imperative to record markers with little to no occlusion and arrange markers asymmetrically. If you do have occlusions, it is important to fill in gaps using the Edit Tool in Edit mode. &#x20;
{% endhint %}

* Attach an adequate number of markers to your flexible object. This is highly dependent on the object but should cover at least the outline and any internal flex points. e.g., if it's a mat, the mat should have markers along the edges as well as dispersed markers in the middle in an asymmetrical pattern. If it's an animal or something that has real-life bones, try to add markers on either side of any joints just like you see on the Skeleton marker sets.&#x20;
* Record the movements you want of the object, trying to get as much of the full range of motion as possible.&#x20;
* In Edit mode, select the markers attached to the object.&#x20;
* Right-click and select _Create Markerset_.
* Right-click the newly created asset and select _Training -> Auto-Generate Asset._&#x20;

<figure><img src="../.gitbook/assets/image (73).png" alt=""><figcaption><p>Select Auto-Generate Asset from Training Options.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (74).png" alt=""><figcaption><p>After Auto-Generate is complete, training and marker sticks should be generated.</p></figcaption></figure>

### Adding Bones

To add Bones from the 3D viewport:

1. First make sure the Markerset is selected in the Assets pane, then hold down CTRL while selecting the markers from which you wish to make a bone.&#x20;
2. Right click on one of the markers and select _Bone(s) -> Add From Marker(s)_.

{% hint style="info" %}
**Tips for making bones:**

* Make sure the asset has enough markers to make all the bones track well.
* Choose markers that are semi-rigid relative to one another when possible for bone constraints.

A bone can be made from one or more markers:

* A bone made from 3+ markers will track with 6 Degrees of Freedom (DoF). Use this type of bone for end effectors and generally whenever possible.&#x20;
* A bone made from 2 markers will track with 5 Degrees of Freedom and a bone made from 1 marker will track with 3 Degrees of Freedom (only positional data). This means that rotational values may turn out strange if it is not connected to a 6 DoF bone on either end. This type is well-suited for under-constrained segments like an elbow with only one or two markers on it.
{% endhint %}

<div><figure><img src="../.gitbook/assets/image (75).png" alt=""><figcaption><p>Markerset selected and markers selected.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Bones from markers.webp" alt=""><figcaption></figcaption></figure></div>

<figure><img src="../.gitbook/assets/image (77).png" alt=""><figcaption><p>Markerset is not selected when highlighted in Cyan.</p></figcaption></figure>

Once you are finished adding the necessary bones you can create Bone Chains to connect bones:

1. Select at least 1 bone (if you have multiple selected make sure the one you select first is the one you wish to make the first 'parent' bone then any subsequent children/parent bones should follow).&#x20;
2.  Right click in 3D viewport and select _Bone(s) -> Add Bone Chain_.\
    <br>

    <figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>
3. Solve your Markerset:  right click on asset in asset pane and select Solve. You can now export, or stream, or do whatever else you'd like in Edit.&#x20;
4. If you would like your Asset to be available in Live, simply right click on the Markerset in the Assets pane and select Copy Asset to Live.&#x20;
5. And voilà, you have a Markerset you can track and record in Live.&#x20;

## Training Options

<figure><img src="../.gitbook/assets/image (80).png" alt=""><figcaption><p>Training Options Submenu.</p></figcaption></figure>

#### Auto-Generate Asset

This adds marker training and Auto-Generates Marker Sticks. This function only needs to be performed once after a Markerset has been created.

#### Add Marker Training

Add Marker Training goes through and adds a learned model of the Markerset. It's best to train the Markerset based on a full Range of Motion of the object you would like to track. This means moving the object to the limits of how it can move for one take, then labeling that take as well as you can, then running this training method on it.&#x20;

{% hint style="info" %}
Add the Training Count column to the Asset pane to show how many times you've used the Add Marker Training command on a Markerset.
{% endhint %}

#### Remove Marker Training

This removes any marker training that was added either by Auto-Generate Asset or Add Marker Training. This is useful if you changed labels and wanted to reapply new marker training based on the new labels.&#x20;

#### Auto-Generate Bones

This automatically generates bones at flex points. This is why recording a full range of motion of your object is important so these bones can be added correctly.&#x20;

#### Refine Bone Positions

This applies another round of Marker Training and refines Bone positions based on new training information.&#x20;

#### Refine Constraints Positions

This applies another round of Marker Training and refines Constraint positions based on new training information.&#x20;

## 3D View Context Menu Bone Options

<figure><img src="../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

#### Add from Marker(s)

This is how you can create Bones manually from selected markers.&#x20;

#### Remove

This removes the Bone from the Markerset and 3D viewport.&#x20;

#### Add Bone Chain

This adds a parent/child relationship to bones.&#x20;

<figure><img src="../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

#### Unparent Bone(s)

This removes the Bone Chain between bones.&#x20;

#### Reroot Bones

When a child bone is selected, you can select Reroot Bones to make a child bone the parent. i.e. Bone 002 is a child of Bone 001 and Bone 001 (the root bone) is a child to Markerset 001. After selecting Bone 002 and Reroot bones, Bone 002 is now the parent to Bone 001 and the child to Markerset 001.&#x20;

<figure><img src="../.gitbook/assets/image (83).png" alt=""><figcaption><p>Before Reroot Bones.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (84).png" alt=""><figcaption><p>After Reroot Bones.</p></figcaption></figure>

#### Align to Camera

This will align the selected Bone to a selected camera.

#### Align to Other Bone

This will align the selected Bone to another selected Bone.

#### Reset Location

If the Bone position was altered by either the Gizmo Tool or by Align to Camera/Other Bone, you can reset its default position with Reset Location.&#x20;
