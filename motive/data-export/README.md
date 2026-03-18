# Data Export

Various types of files, including the tracking data, can be exported out from Motive. This page provides information on what file formats can be exported from Motive and instructions on how to export them.

## Tracking Data Export

Once captures have been recorded into _Take_ files and the corresponding 3D data have been reconstructed, tracking data can be exported from Motive in various file formats.

**Exporting Tracking Data**

<figure><img src="../../.gitbook/assets/image (2) (3) (1) (1) (2).png" alt=""><figcaption></figcaption></figure>

[**Reconstruction** ](../../motive-ui-panes/data-pane.md#reconstruct)is required to export Marker data, [**Auto-label**](../../motive-ui-panes/data-pane.md#auto-label) is required when exporting Markers labeled from Assets, and [**Solving** ](../../motive-ui-panes/data-pane.md#solve-all-assets)is required prior to exporting Assets.

If the recorded _Take_ includes Rigid Body or Skeleton trackable assets, make sure all of the Rigid Bodies and Skeletons are _Solved_ prior to exporting. The solved data will contain positions and orientations of each Rigid Body and Skeleton. If changes have been made to either the Rigid Body or Skeleton, you will need to solve the assets again prior to exporting.&#x20;

{% hint style="info" %}
Please note that if you have Assets that are unsolved and just wish to export reconstructed Marker data, you can toggle off Rigid Bodies and Bones (Skeletons) from the Export window (see image below).&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/image (3) (4).png" alt=""><figcaption></figcaption></figure>

### Export Settings

In the export dialog window, the frame rate, the measurement scale, and the frame range of exported data can be configured. Additional export settings are available for each export file formats. Read through below pages for details on export options for each file format:

* [Data Export: CSV](data-export-csv.md)
* [Data Export: C3D](data-export-c3d.md)
* [Data Export: FBX](data-export-fbx.md)
* [Data Export: BVH](data-export-bvh.md)
* [Data Export: TRC](data-export-trc.md)

![Tracking data export dialogue window in Motive. CSV export is selected and corresponding options are displayed.](<../../.gitbook/assets/image (410).png>)

### Tracking Data Export Steps

**Exporting a Single Take**

**Step 1.** Open and select a _Take_ to export from the [Data pane](../../motive-ui-panes/data-pane.md). The selected _Take_ must contain reconstructed 3D data.

**Step 2.** Under the _File_ tab on the command bar, click _File → Export Tracking Data_. This can also be done by right-clicking on a selected _Take_ from the [Data pane](../../motive-ui-panes/data-pane.md) and clicking _Export Tracking Data_ from the context menu.

**Step 3.** On the export dialogue window, select a file format and configure the corresponding export settings.

* To export the entire frame range, set _Start Frame_ and _End Frame_ to _Take First Frame_ and _Take Last Frame_.
* To export a specific frame range, set _Start Frame_ and _End Frame_ to _Start of Working Range_ and _End of Working Range_.

**Step 4.** Click _Save_.

![Make sure all Rigid Bodies are solve prior to export.](<../../.gitbook/assets/image (485).png>)

{% hint style="info" %}
**Working Range:**

The working range (also called the playback range) is both the view range and the playback range of a corresponding _Take_ in Edit mode. Only within the working frame range will recorded tracking data be played back and shown on the graphs. This range can also be used to output specific frame ranges when exporting tracking data from Motive.

The working range can be set from the following places:

* In the navigation bar of the Graph View pane, you can drag the handles on the scrubber to set the working range.
* You can also use the navigation controls on the Graph View pane to zoom in or zoom out on the frame ranges to set the working range. See: [Graph View pane](../../motive-ui-panes/graph-view-pane.md) page.
* Start and end frames of a working range can also be set from the [Control Deck](../../motive-ui-panes/control-deck.md) when in the Edit mode.
{% endhint %}

![Working range (48 \~ 345) shown on the navigation bar at the bottom of the Graph View pane.](<../../.gitbook/assets/image (620).png>)

**Exporting Multiple Takes**

**Step 1.** Under the [Data pane](../../motive-ui-panes/data-pane.md), shift + select all the _Takes_ that you wish to export.

**Step 2.** Right-click on the selected _Takes_ and click _Export Tracking Data_ from the context menu.

**Step 3.** An export dialogue window will show up for batch exporting tracking data.

**Step 4.** Select the desired output format and configure the corresponding export settings.

**Step 5.** Select frame ranges to export under the _Start Frame_ and the _End Frame_ settings. You can either export entire frame ranges or specified frame ranges on all of the Takes. When exporting specific ranges, desired working ranges must be set for each respective Takes.

* To export entire frame ranges, set _Start Frame_ and _End Frame_ to _Take First Frame_ and _Take Last Frame_.
* To export specific frame ranges, set _Start Frame_ and _End Frame_ to _Start of Working Range_ and _End of Working Range_.

**Step 6.** Click _Save_.

{% hint style="info" %}
**Motive Batch Processor:**

Exporting multiple Take files with specific options can also be done through a [Motive Batch Processor](../motive-batch-processor.md) script. For example, refer to _FBXExporterScript.cs_ script found in the MotiveBatchProcessor folder.
{% endhint %}

### File Formats

Motive exports reconstructed 3D tracking data in various file formats and exported files can be imported into other pipelines to further utilize capture data. Available export formats include CSV, C3D, FBX, BVH, and TRC. Depending on which options are enabled, exported data may include reconstructed marker data, 6 Degrees of Freedom (6 DoF) Rigid Body data, or Skeleton data. The following chart shows what data types are available in different export formats:

<table><thead><tr><th align="center">Tracking Data Type</th><th width="88" align="center">CSV</th><th width="87" align="center">C3D</th><th width="66" align="center">FBX</th><th width="83" align="center">BVH</th><th width="100" align="center">TRC</th></tr></thead><tbody><tr><td align="center">Reconstructed 3D Marker Data</td><td align="center">•</td><td align="center">•</td><td align="center">•</td><td align="center"></td><td align="center">•</td></tr><tr><td align="center"><p>6 Degrees of Freedom </p><p>Rigid Body Data</p></td><td align="center">•</td><td align="center"></td><td align="center">•</td><td align="center"></td><td align="center"></td></tr><tr><td align="center">Skeleton Data</td><td align="center">•</td><td align="center"></td><td align="center">•</td><td align="center">•</td><td align="center"></td></tr></tbody></table>

{% hint style="info" %}
CSV and C3D exports are supported in both Motive Tracker and Motive Body licenses. FBX, BVH, and TRC exports are only supported in Motive Body.
{% endhint %}

## Camera Calibration Export

A calibration definition of a selected take can be exported from the _Export Camera Calibration_ under the _File_ tab. Exported calibration (CAL) files contain camera positions and orientations in 3D space, and they can be imported in different sessions to quickly load the calibration as long as the [camera setup](../../hardware/) is maintained.

Read more about calibration files under the [Calibration](../calibration/) page.

![Export Calibration window. ](<../../.gitbook/assets/image (416).png>)

## Export Assets Definition

Assets can be exported into the Motive user profile (.MOTIVE) file if it needs to be re-imported. The [user profile](../motive-basics.md#motive-user-profile-.motive) is a text-readable file that contains various configuration settings in Motive, including the asset definitions.

When an asset definition is exported to a MOTIVE user profile, it stores marker arrangements calibrated in each asset, and they can be imported into different takes without creating a new one in Motive. Note that these files specifically store the spatial relationship of each marker, and therefore, only the identical marker arrangements will be recognized and defined with the imported asset.

To export the assets, go to the _File menu_ and select _Export Assets_ to export all of the assets in the Live-mode or in the current TAK file(s). You can also use _File_ → _Export Profile_ to export other software settings including the assets.

![Exporting Assets into the User Profile.](<../../.gitbook/assets/image (140) (1) (1) (1) (1) (1) (1) (4).png>) ![Exporting user profile that includes assets. This dialogue window is from the Export Profile As... option.](<../../.gitbook/assets/image (124) (1) (1) (1) (1) (1) (1) (3).png>)

## Analog Data Export

***

Recorded NI-DAQ analog channel data can be exported into **C3D** and **CSV** files along with the mocap tracking data. Follow the tracking data export steps outlined above and any analog data that exists in the TAK will also be exported.

**C3D Export:** Both mocap data and the analog data will be exported onto a same C3D file. Please note that all of the analog data within the exported C3D files will be logged at the same sampling frequency. If any of the devices are captured at different rates, Motive will automatically resample all of the analog devices to match the sampling rate of the fastest device. More on C3D files: [https://www.c3d.org/](https://www.c3d.org/)

**CSV Export:** When exporting tracking data into CSV, additional CSV files will be exported for each of the NI-DAQ devices in a _Take_. Each of the exported CSV files will contain basic properties and settings at its header, including device information and sample counts. The voltage amplitude of each analog channel will be listed. Also, mocap frame rate to device sampling ratio is included since analog data is usually sampled at higher sampling rates.

{% hint style="info" %}
**Note**

The coordinate system used in Motive (y-up right-handed) may be different from the convention used in the biomechanics analysis software.
{% endhint %}

**Common Conventions**

Since Motive uses a different coordinate system than the system used in common biomechanics applications, it is necessary to modify the coordinate axis to a compatible convention in the C3D exporter settings. For biomechanics applications using z-up right-handed convention (e.g. Visual3D), the following changes must be made under the custom axis.

* X axis in Motive should be configured to positive X
* Y axis in Motive should be configured to negative Z
* Z axis in Motive should be configured to positive Y.

This will convert the coordinate axis of the exported data so that the x-axis represents the anteroposterior axis (left/right), the y-axis represents the mediolateral axis (front/back), and the z-axis represents the longitudinal axis (up/down).

![C3D export setting for applications using z-up right-handed coordinate systems.](<../../.gitbook/assets/image (1055) (1) (1) (1) (1) (1) (1) (4).png>)

## Reference Video Export

When there is an MJPEG reference camera in a _Take_, its recorded video can be exported into an AVI file or into a sequence of JPEG files. The _Export Video_ option is located under the _File tab_ or you can also right-click on a TAK file from the [Data pane](../../motive-ui-panes/data-pane.md) and export from there. At the bottom of the export dialog, the frame rate of the exported AVI file can be set to a full-frame rate or down-sampled to half, quarter, 1/8, or 1/16 ratio framerate. You can also adjust the playback speed to export a video with a slower or faster playback speed. The captured reference videos can be exported into AVI files using either H.264 or MJPEG compression format. The H.264 format will allow faster export of the recorded videos and is recommended. Read more about recording reference videos on [Data Recording](../data-recording/) page.

{% hint style="danger" %}
**Reference Video Type:** Only compressed MJPEG reference videos can be recorded and exported from Motive. Export for raw grayscale videos is not supported.
{% endhint %}

{% hint style="danger" %}
**Media Player:** The exported videos may not be playable on Windows Media Player, please use a more robust media player (e.g. VLC) to play the exported video files.
{% endhint %}

![Export video dialog window.](<../../.gitbook/assets/image (414).png>)

## Audio Export

When a recorded capture contains audio data, an audio file can be exported through the _Export Audio_ option on the File menu or by right-clicking on a Take from the [Data pane](../../motive-ui-panes/data-pane.md).

## Export Skeleton Marker Labels

Skeletal marker labels for Skeleton assets can be exported as XML files (example shown below) from the [Data pane](../../motive-ui-panes/data-pane.md). The XML files can be imported again to use the stored marker labels when creating new Skeletons.

For more information on Skeleton XML files, read through the [Skeleton Tracking](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md) page.

![Exporting Skeleton marker XML template.](<../../.gitbook/assets/image (550).png>)

**Sample Skeleton Label XML File**

```
 <Asset version="1.0">
    <MarkerNames ReorderMarkers="true">
        <Marker name="NewHeadTop" oldName="HeadTop" />
        <Marker name="NewHeadFront" oldName="HeadFront" />
        <Marker name="NewHeadSide" oldName="HeadSide" />
        ...
        <Marker name="RToeIn" oldName="RToeIn" />
        <Marker name="RToeTip" oldName="RToeTip" />
        <Marker name="RToeOut" oldName="RToeOut" />
    </MarkerNames>
    <MarkerColors>
        <Marker name="WaistLFront" color="75 225 255" movable="false" />
        <Marker name="WaistRFront" color="225 75 255" movable="false" />
        <Marker name="WaistLBack" color="75 225 255" movable="false" />
        ...
        <Marker name="RToeIn" color="225 75 255" movable="false" />
        <Marker name="RToeOut" color="75 75 255" movable="false" />
        <Marker name="RHeel" color="225 75 255" movable="false" />
        <Marker name="RToeTip" color="0 150 0" movable="false" />
    </MarkerColors>
    <MarkerSticks>
        <MarkerStick origin="WaistLFront" end="WaistLBack" color="140 45 225" />
        <MarkerStick origin="WaistLFront" end="LThigh" color="110 210 240" />
        <MarkerStick origin="WaistRFront" end="WaistRBack" color="140 45 225" />
        ...
        <MarkerStick origin="RToeTip" end="RToeIn" color="60 210 60" />
        <MarkerStick origin="LToeTip" end="LToeOut" color="110 210 240" />
        <MarkerStick origin="RToeTip" end="RToeOut" color="60 210 60" />
    </MarkerSticks>
 </Asset>
```
