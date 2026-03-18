# Data Recording

Once the capture volume is calibrated and all markers are placed, you are now ready to capture _Takes_. In this page, we will cover key concepts and tips that are important for the recording pipeline. For real-time tracking applications, you can skip this page and read through the [Data Streaming](../data-streaming.md) page.

## Live Mode and Edit Mode

There are two different modes in Motive: **Live mode** and **Edit mode**. You can toggle between two modes from the [Control Deck](../../motive-ui-panes/control-deck.md) or by using the (Shift + \~) hotkey.

**Live Mode**

The **Live mode** is mainly used when recording new _Takes_ or when streaming a live capture. In this mode, all of the cameras are continuously capturing 2D images and reconstructing the detected reflections into 3D data in real-time.

![Motive in Live Mode.](<../../.gitbook/assets/image (574).png>)

**Edit Mode**

The **Edit Mode** is used for playback of captured Take files. In this mode, you can playback, or stream, recorded data. Also, captured _Takes_ can be post-processed by fixing mislabeling errors or interpolating the occluded trajectories if needed.

![Motive in Edit Mode](<../../.gitbook/assets/image (429).png>)

{% hint style="info" %}
**Tip:** Prime series cameras will illuminate in blue when in live mode, in green when recording, and turned-off in edit mode. See more at [Camera Status Indicators](../../hardware/camera-status-indicators.md).
{% endhint %}

## Recording

Recording in Motive is triggered from the [Control Deck](../../motive-ui-panes/control-deck.md) when in the Live mode, and the recorded data

### Control Deck

In Motive, capture recording is controlled from the [Control Deck](../../motive-ui-panes/control-deck.md). In the Live mode, new _**Take**_\*\* name\*\* can be assigned in the name box or you can just simply start the recording and let Motive automatically generate new names on the fly. You can also create empty _Takes_ in the Data Management pane for a better organization. To start the capture, select Live mode and click the recording button (red). In the control deck, record time and frames are displayed in (Hour:Minute:Second:Frames).

{% hint style="info" %}
**Tip:** For Skeleton tracking, always start and end the capture with a T-pose or A-pose, so that the Skeleton assets can be redefined from the recorded data as well.
{% endhint %}

![Click image to enlarge.](<../../.gitbook/assets/image (604).png>)

### Recorded Data Management

In Motive, all of the recorded capture files are managed through the [Data pane](../../motive-ui-panes/data-pane.md). Each capture will be saved in a _Take_ (TAK) file, which can be played back in the Edit mode later. Related Take files can be grouped within _session folders_. Simply create a new folder in the desired directory and load the folder onto the [Data pane](../../motive-ui-panes/data-pane.md). Currently selected session folder is indicated with the flag symbol ([![SelectedFolder.png](https://v30.wiki.optitrack.com/images/e/e9/SelectedFolder.png)](https://v30.wiki.optitrack.com/index.php?title=File:SelectedFolder.png)), and all newly recorded _Takes_ will be saved in this folder.

![Click image to enlarge.](<../../.gitbook/assets/image (243).png>)

{% hint style="info" %}
**Tip: Efficient ways of managing Takes**

***

1. Always start by creating session folders for organizing related Takes. (e.g. name of the tracked subject).
2. Plan ahead and create a list of captures in a text file or a spreadsheet, and you can create empty takes by copying and pasting the list into the Data Management pane (e.g. walk, jog, run, jump).
3. Once pasted, empty Takes with the corresponding names will be imported.
4. Select one of the empty takes and start recording. The capture will be saved with the corresponding name.
5. If the capture was unsuccessful, simply record the same Take again and another one will be recorded with a incremented suffix added at the end of the given Take name (e.g. walk\_001, walk\_002, walk\_003). The suffix format is defined in the [Application Settings](../../motive-ui-panes/settings/).
6. When captured successfully, select another empty Take in the list and capture the next one.
{% endhint %}

![Managing Takes.](<../../.gitbook/assets/image (431).png>)

### Recorded Data Types

When a capture is first recorded, both 2D data and real-time reconstructed 3D data is saved onto the _Take_. For more details on each data type, refer to the [Data Types](data-types.md) page.

* **2D data:** The recorded Take file includes just the 2D object images from each camera.
* **3D data:** The recorded Take file also includes reconstructed 3D marker data in addition to 2D data.

## Marker Types in Motive

Throughout capture, you might recognize that there are different types of markers that appear in the [3D perspective view](../../motive-ui-panes/viewport.md#perspective-view). In order to correctly interpret the tracking data, it is important to understand the differences between these markers. There are three different displayed marker types: _markers_, _Rigid Body markers_, and _bone (or Skeleton) markers_.

### Unlabeled and Labeled

Marker data, labeled or unlabeled, represent the 3D positions of markers. These markers do not present Rigid Body or Skeleton solver calculations but locate the actual marker position calculated from the camera data. These markers are represented as a solid sphere in the viewport. By default, unlabeled markers are colored in white, and labeled markers will have colors that reflect the color setting in the Rigid Body or the corresponding bone.

![](<../../.gitbook/assets/image (460).png>)

{% hint style="info" %}
**Labeled Marker Colors:**

* Colors of the unlabeled markers can be changed from the [Application Settings](../../motive-ui-panes/settings/settings-views.md).
* Colors of the Rigid Body labeled markers can be changed from the properties of the corresponding asset.
* Colors of the markers can be changed from the Constraints XML file if needed.
{% endhint %}

### Marker Constraints: Rigid Body Markers and Bone Markers

![](<../../.gitbook/assets/image (399).png>)

Rigid Body markers or Skeleton bone markers are referred to as **Marker Constraints**. They appear as transparent spheres within a Rigid Body, or a Skeleton, and each sphere reflect the position that a Rigid Body, or a Skeleton, expects to find a 3D marker. When the asset definitions are created, it is assumed that the markers are fixed at the same location and does not move over the course of capture.

In order to view Marker Constraints, both the Marker Constraints visual aid option in the viewport and the Marker Constraints property on the corresponding asset must be enabled. This is enabled by default for Skeleton assets but this must be enabled for Rigid Bodies to view them. When the Rigid Body solver or Skeleton solver are tracking from the 3D markers, the marker reconstructions and Marker Constraints positions will closely align in the viewport.

For Rigid Body assets, when their asset definition is created, it expects the markers to be fixed in the same location and the object does not deform over the course of capture. Each Rigid Body is given a acceptable [deflection](../../motive-ui-panes/properties-pane/properties-pane-rigid-body.md) property value. As long as the actual marker position is within the allowable deflection from the Marker Constraints position, the marker will be labeled. For Skeleton assets, as the body segments are not perfectly rigid, some amount of offset from the model marker position is allowed.

![](<../../.gitbook/assets/image (566).png>)
