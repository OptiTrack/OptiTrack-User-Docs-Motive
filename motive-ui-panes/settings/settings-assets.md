# Settings: Assets

## **Overview**

Use the Application Settings panel to customize Motive and set default values. This page will cover the items available on the Assets tab. Properties are Standard unless noted otherwise.&#x20;

Please see the following pages for descriptions of the settings on other tabs:

* [Settings: General](settings-general.md)
* [Settings: Live Pipeline](settings-live-pipeline.md)
* [Settings: Streaming](settings-streaming.md)
* [Settings: Views](settings-views.md)
* [Settings: Mouse and Keyboard](settings-mouse-and-keyboard.md)
* [Settings: Audio](settings-audio.md)

Application Settings can be accessed from the [View menu](../toolbar-command-bar.md#view) or by clicking the <img src="../../.gitbook/assets/Settings button (9).png" alt="A screenshot of the Settings button from the Motive toolbar. " data-size="line"> icon on the main toolbar.&#x20;

<figure><img src="../../.gitbook/assets/Settings Assets Standard top.png" alt="A screenshot of the basic settings on the Motive Settings: Assets pane. "><figcaption><p>Assets tab in Application Settings - basic settings shown.</p></figcaption></figure>

{% hint style="info" %}
**Advanced Settings**

The Settings panel contains advanced settings that are hidden by default. To access these settings, click the <img src="../../.gitbook/assets/Motive Context Menu (25).png" alt="A screenshot of the menu button from the Settings panel in Motive. " data-size="line"> button in the top right corner.&#x20;

Use the _Edit Advanced_ option to customize which settings are in the _Advanced Settings_ category and which appear in the standard view, to show only the settings that are needed specifically for your capture application.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Settings - Show or Edit advanced (1).png" alt="A screenshot of the Motive Settings panel menu: Show Advanced and Edit Advanced.  "><figcaption><p>Show or Edit Advanced Settings.</p></figcaption></figure>

{% hint style="info" %}
To restore all settings to their default values, select _Reset Settings_ from the Edit menu.
{% endhint %}

## Assets Tab

The assets tab contains settings that apply either to all assets or to assets of a specific type, such as Rigid Body, Skeleton, and Trained Markerset assets. These values can be changed on the asset after creation from the [Properties pane](../properties-pane/).&#x20;

### Asset Defaults

The Asset Defaults section contains settings that apply to all assets at creation.&#x20;

<figure><img src="../../.gitbook/assets/Settings - Assets Asset Defaults Advanced.png" alt=""><figcaption><p>Standard and Advanced <em>Asset Defaults</em> Assets settings. </p></figcaption></figure>

<details>

<summary>Minimum Markers to Boot</summary>

The minimum number of markers that must be labeled in order for the respective asset to be booted.

</details>

<details>

<summary>Minimum Markers to Continue</summary>

The minimum number of markers that must be labeled in order for the respective asset to be tracked.

</details>

<details>

<summary>Asset Scale (Advanced)</summary>

The size of the asset in relation to the captured data, set at 100% by default for a one-to-one scale. Adjust the percentage value to increase or shrink the asset size proportionately.&#x20;

</details>

<details>

<summary>Label</summary>

Toggle to enable. Displays the asset's name over the corresponding asset in the 3D viewport.

</details>

<details>

<summary>IMU Label</summary>

Select the label type to display for assets that include an IMU. Options are:&#x20;

* None. No IMU data will be displayed.&#x20;
* Text. The label will display the tag name and sensor fusion status in text form.
* Icons. The label will display sensor fusion status as an icon.

See the [IMU Sensor Fusion](../../motive/imu-sensor-fusion.md#id-3d-viewport) page for more detail about IMU labels.&#x20;

{% hint style="info" %}
The [Label](settings-assets.md#label) must be enabled in the Asset properties to see the IMU label. &#x20;
{% endhint %}

</details>

### Rigid Body Creation

The Rigid Body Creation section contains settings applicable to the creation of new rigid bodies. These properties are applied only when Rigid Bodies are created, and can be modified during the creation process and after the Rigid Body is created through the [Properties pane](../properties-pane/).&#x20;

For descriptions of the Rigid Body properties, please see the [Properties: Rigid Body](../properties-pane/properties-pane-rigid-body.md) page.

<figure><img src="../../.gitbook/assets/Settings - Assets Advanced RB creation.png" alt="A screenshot of the Rigid Body Creation settings from the Motive Settings panel, Assets tab. "><figcaption><p>Standard and Advanced <em>Rigid Body Creation</em> Assets settings. </p></figcaption></figure>

<details>

<summary>Default Name </summary>

This setting establishes the naming convention for Rigid Bodies when they are created. For instance, if it is set to RigidBody, the first Rigid Body will be named RigidBody when created. Subsequent Rigid Bodies will be named RigidBody 001, RigidBody 002, and so on. The default is set to _Rigid Body_.&#x20;

</details>

<details>

<summary>Creation Color</summary>

Select the default color a Rigid Body will have upon creation. Select Rainbow to cycle through a different color each time a new Rigid Body is created.

</details>

### Skeleton Creation

The Skeleton Creation section contains settings applicable to the creation of new skeleton assets. These properties are applied only during creation and can be modified either during the creation process from the [Builder pane](../builder-pane.md#skeleton-create) or after the Skeleton is created through the [Properties pane](../properties-pane/properties-pane-skeleton.md).&#x20;

For descriptions of the Skeleton properties, please see the [Properties: Skeleton](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive-ui-panes/properties-pane/properties-pane-Skeleton.md) page.

<figure><img src="../../.gitbook/assets/Settings - Assets Advanced Skeleton Creation.png" alt="A screenshot of the Skeleton Creation settings from the Motive Settings panel, Assets tab.  "><figcaption><p>Standard and Advanced <em>Skeleton Creation</em> Assets settings. </p></figcaption></figure>

<details>

<summary>Default Name</summary>

This setting establishes the naming convention for Skeletons when they are created. For instance, if it is set to Skeleton (the default), the first Skeleton will be named Skeleton when created. Subsequent Skeletons will be named Skeleton 001, Skeleton 002, and so on. &#x20;

</details>

<details>

<summary>Creation Color</summary>

Select the default color a Skeleton will have upon creation. Select Rainbow to cycle through a different color each time a new Skeleton is created.

</details>

<details>

<summary>Straight Arms</summary>

Straighten each arm along the line from shoulder to wrist, regardless of the position of the elbow markers.

</details>

<details>

<summary>Straight Legs</summary>

Straighten each leg along the line from hip to ankle, regardless of the position of the knee markers.

</details>

<details>

<summary>Feet On Floor</summary>

Scale the shin bone length to align the bottom of foot with the floor, regardless of the ankle marker height.

</details>

<details>

<summary>Head Upright</summary>

Create the skeleton with the head upright, removing tilt or bend, regardless of the head marker positions.

</details>

<details>

<summary>Spine Type (Advanced)</summary>

Motive includes two spine models for Skeletons:

* The **Classic** model has two spine bones and one neck bone. This is the traditional model still used in many production workflows.
* The **7 Segment Spine** model has five spine bones and two neck bones. This model accounts for the natural curves in the human spine and allows for better alignment between the Skeleton in Motive and the actor.

The selected type will be the default option when creating new Skeletons, and can be changed as needed from the [Builder pane](../builder-pane.md#skeleton-create).&#x20;

</details>

<details>

<summary>Height Marker</summary>

Scale the skeleton model so the top of the head aligns with the top head marker.

</details>

<details>

<summary>Vertical Hand Adjustment</summary>

Apply a Height offset to hands to account for markers placed above the wrist and knuckle joints.

</details>

<details>

<summary>Spine Shrink Limit (Advanced)</summary>

Set the maximum amount of shrinkage permitted across all four of the bones that comprise the spine: Abdomen, chest, neck, and head. This property allows for the adjustment of shrinkage that can occur normally in the human spine. This property can be changed for individual Skeletons through the [Solver settings](../properties-pane/properties-pane-skeleton.md#solver-advanced-settings) in the [Skeleton's Properties pane](../properties-pane/properties-pane-skeleton.md).

{% hint style="danger" %}
#### Shrink and Stretch Limits: A Warning

The default values are sufficient for most mocap applications and we recommend NOT changing them. Change these values only if you encounter issues with the solver such as shoulder popping or hand misalignment when an actor is pushing the typical limits, such as hanging by their arms, for example.
{% endhint %}

</details>

<details>

<summary>Spine Stretch Limit (Advanced)</summary>

Set the maximum amount of stretch permitted across all four of the bones that comprise the spine: Abdomen, chest, neck, and head. This property allows for the adjustment of stretching that can occur normally in the human spine. This property can be changed for individual Skeletons through the [Solver settings](../properties-pane/properties-pane-skeleton.md#solver-advanced-settings) in the [Skeleton's Properties pane](../properties-pane/properties-pane-skeleton.md).

{% hint style="danger" %}
#### Shrink and Stretch Limits: A Warning

The default values are sufficient for most mocap applications and we recommend NOT changing them. Change these values only if you encounter issues with the solver such as shoulder popping or hand misalignment when an actor is pushing the typical limits, such as hanging by their arms, for example.
{% endhint %}

</details>

<details>

<summary>Shoulder Shrink Limit (Advanced)</summary>

Set the maximum amount of shrinkage permitted in the shoulder width. This property allows for the adjustment of shrinkage that can occur normally in the human shoulders. This property can be changed for individual Skeletons through the [Solver settings](../properties-pane/properties-pane-skeleton.md#solver-advanced-settings) in the [Skeleton's Properties pane](../properties-pane/properties-pane-skeleton.md).

{% hint style="danger" %}
#### Shrink and Stretch Limits: A Warning

The default values are sufficient for most mocap applications and we recommend NOT changing them. Change these values only if you encounter issues with the solver such as shoulder popping or hand misalignment when an actor is pushing the typical limits, such as hanging by their arms, for example.
{% endhint %}

</details>

<details>

<summary>Shoulder Stretch Limit (Advanced)</summary>

Set the maximum amount of stretch permitted in the shoulder width. This property allows for the adjustment of stretching that can occur normally in the human shoulders. This property can be changed for individual Skeletons through the [Solver settings](../properties-pane/properties-pane-skeleton.md#solver-advanced-settings) in the [Skeleton's Properties pane](../properties-pane/properties-pane-skeleton.md).

{% hint style="danger" %}
#### Shrink and Stretch Limits: A Warning

The default values are sufficient for most mocap applications and we recommend NOT changing them. Change these values only if you encounter issues with the solver such as shoulder popping or hand misalignment when an actor is pushing the typical limits, such as hanging by their arms, for example.
{% endhint %}

</details>

### Markerset Creation

The Markerset Creation section contains settings applicable to the creation of new Trained Markerset assets. These properties are applied only during creation and can be modified either during the creation process from the [Builder pane](../builder-pane.md#trained-markersets-create) or after the Trained Markerset is created through the [Properties pane](../properties-pane/properties-pane-trained-markerset.md).&#x20;

For descriptions of the Trained Markerset properties, please see the [Properties Pane: Trained Markerset](../properties-pane/properties-pane-trained-markerset.md) page.

<figure><img src="../../.gitbook/assets/Settings - Assets Standard Markerset Creation.png" alt=""><figcaption><p>Standard and Advanced <em>Markerset Creation</em> Assets settings. </p></figcaption></figure>

<details>

<summary>Default Name</summary>

This setting establishes the naming convention for Trained Markersets when they are created. For instance, if it is set to Markerset (the default), the first Markerset will be named Markerset when created. Subsequent Markerset will be named Markerset 001, Markerset 002, and so on. &#x20;

</details>

## Refinement Tab

The Refinement tab contains settings that apply when refining Skeleton assets.&#x20;

{% hint style="danger" %}
The most commonly adjusted Refinement settings are available as standard settings. Use caution when changing advanced settings. These values should only be adjusted to correct issues with the solved data.
{% endhint %}

<figure><img src="../../.gitbook/assets/Settings - Assets Refinement Tab Standard .png" alt="A screenshot of the Standard settings available on the Refinement tab of the Motive Applications settings, Assets panel. "><figcaption><p>Standard settings available on the Refinement tab of the Assets pane in the Settings panel. </p></figcaption></figure>

### General Settings

The General settings affect how Motive completes the Range of Motion (ROM) calculation. These are standard settings unless otherwise noted.&#x20;

For more information on the Skeleton Range of Motion (ROM), please see the [Create Skeleton](../builder-pane.md#create-skeleton) section of the [Builder pane](../builder-pane.md) page.&#x20;

<figure><img src="../../.gitbook/assets/Settings - Assets Refinement tab Advanced General.png" alt="A screenshot of the Motive Settings panel, Standard and Advanced General Settings on the Assets Tab Refinement tab. "><figcaption><p>Standard and Advanced <em>General</em> Refinement settings. </p></figcaption></figure>

<details>

<summary>Start ROM Delay</summary>

Set a delay for the ROM to allow the actor to get into position before the Range of Motion (ROM) calibration begins. This is similar to setting a [recording delay](../control-deck.md#recording-delay) when capturing live data.&#x20;

</details>

<details>

<summary>Record ROM</summary>

When enabled, Motive records a _Take_ with the name of the subject each time a Range of Motion (ROM) is performed. This allows you to easily reprocess the Skeleton if needed.

</details>

<details>

<summary>Sample Count</summary>

The maximum number of samples Motive will use for the Range of Motion (ROM) calculations.&#x20;

{% hint style="danger" %}
In most cases, increasing the sample count will cause the collection and calibration process to take longer without noticeable improvements in the quality of the Skeleton solve.&#x20;
{% endhint %}

</details>

<details>

<summary>Auto Start Calculation (Advanced)</summary>

When enabled, Motive will begin calculating the Range of Motion (ROM) once sufficient samples are collected.&#x20;

</details>

<details>

<summary>Calculation Thread Count</summary>

Set the maximum number of CPU threads to use to calculate the ROM. A value of 0 will allow Motive to use the maximum number of CPU cores available in PC.&#x20;

Adjust this value only if the ROM calculation causes slowness issues or frame drops that impact system performance. If changes are made, we recommend setting this to a low value, e.g., 5-10.&#x20;

</details>

<details>

<summary>Save Unrefined Skeleton (Advanced)</summary>

When enabled, Motive will save the original Skeleton prior to completing the Range of Motion (ROM), for comparison purposes.

</details>

### Solver Settings

Solver Settings allow you to control how specific Skeleton joints are solved. Most of these are advanced settings that will not need to be adjusted, in most use cases. &#x20;

<figure><img src="../../.gitbook/assets/Settings - Assets Refinement tab Advanced Solver Settings.png" alt="A screenshot of the standard and advanced Solver Settings from the Motive Application Settings, Assets tab, refinement tab. "><figcaption><p>Standard and Advanced <em>Solver Settings</em> Refinement settings. </p></figcaption></figure>

<details>

<summary>Solve Constraints Only</summary>

Calibrates the Skeleton's constraint offsets only without changing any bone offsets or lengths.&#x20;

</details>

<details>

<summary>Use Constraint Weights (Advanced) </summary>

When enabled, Motive uses the weights assigned to each constraint in the Constraints pane to solve the Skeleton.&#x20;

Please see the [Constraints pane](../constraints-pane/#weight) for more information on editing constraint weights.&#x20;

</details>

<details>

<summary>Spring Weight Scale (Advanced) </summary>

Adjust the influence of default joint angles on solved pose for calibrated Skeletons. Lower values can result in a better match between the skeleton pose and the marker positions.&#x20;

</details>

<details>

<summary>Straighten Elbows / Straighten Knees (Advanced) </summary>

Straighten the selected joint based on the data from the original T or A pose.&#x20;

</details>

<details>

<summary>Flatten Feet (Advanced) </summary>

Set the feet parallel to the ground based on the data from the original T or A pose.&#x20;

</details>

<details>

<summary>Head Upright (Advanced) </summary>

Adjust the angle of the head to be upright when in the T or A pose.&#x20;

</details>

### Pose Assisted Solve Settings

Pose Assisted Solve Settings allow you to customize specific parameters in the Range of Motion to accommodate variances in Skeleton assets during creation.&#x20;

{% hint style="warning" %}
These are all advanced properties and should only be adjusted as needed for specific use cases.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Settings - Assets Refinement Adv Pose Assisted Solve Settings .png" alt="A screenshot of the Pose Assisted Solve Settings section of the Motive Application Settings panel, Asset Tab, Refinement Tab. "><figcaption><p>Advanced <em>Pose Assisted Solve Settings</em> Refinement settings. </p></figcaption></figure>

<details>

<summary>Pose Detection Duration (Advanced)</summary>

The length of time a pose needs to be held for Motive to detect it.&#x20;

</details>

<details>

<summary>Palms Together Pose (Advanced) </summary>

This value specifies how strongly the solver will enforce the Palms Together pose during the Range of Motion (ROM) calibration.&#x20;

</details>

<details>

<summary>Wrist Distance (Advanced) </summary>

The distance between the wrists when the hands are in the Palms Together pose.&#x20;

</details>

<details>

<summary>Wrist Angle (Advanced) </summary>

Setting to add a slight downward angle to the wrist to account for the palm being thicker at the wrist than it is at the knuckles.&#x20;

</details>

<details>

<summary>Elbows Together Pose (Advanced) </summary>

This value specifies how strongly the solver will enforce the Elbows Together pose during the Range of Motion (ROM) calibration.&#x20;

</details>

<details>

<summary>Elbow Distance (Advanced) </summary>

The distance between the elbows when the arms are in the Elbows Together pose.&#x20;

</details>

### Joint Marker Settings

Joint Marker Settings allow you to adjust specific joints in the Range of Motion to accommodate variances in Skeleton assets during creation.&#x20;

{% hint style="warning" %}
These are all advanced properties and should only be adjusted as needed for specific use cases.&#x20;
{% endhint %}

The default values produce the best solve results when working with standard Skeletons. Adjust these values only if necessary to improve the Skeleton calibration.&#x20;

<figure><img src="../../.gitbook/assets/Settings - Assets Refinement tab Advanced Joint Marker Settings.png" alt="A screenshot of the Joint Marker Settings, advanced settings from the Motive Applications Settings panel, Asset tab, Refinement tab. "><figcaption><p>Advanced <em>Joint Marker Settings</em> Refinement settings. </p></figcaption></figure>

<details>

<summary>Joint From Markers (Advanced) </summary>

For each joint type, set how much the joint markers should be factored into calculating the joint's location.&#x20;

</details>

<details>

<summary>Shoulder Width From Markers (Advanced) </summary>

Set how much the joint markers are factored into the shoulder width calculation.&#x20;

</details>

<details>

<summary>Face Forward From Markers (Advanced) </summary>

Determine how much the head makers are used to calculate the forward direction of the Skeleton's head.&#x20;

</details>

<details>

<summary>Thickness Scale (Advanced) </summary>

Scale the offset used to calculate the position of the selected joint from its joint markers. This value can be adjusted to account for a person with thicker or thinner limbs.

</details>
