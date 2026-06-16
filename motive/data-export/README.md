---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/data-export
---

# Data Export

Various types of files, including the tracking data, can be exported out from Motive. This page provides information on what file formats can be exported from Motive and instructions on how to export them.

## Tracking Data Export

Once captures have been recorded into _Take_ files and the corresponding 3D data have been reconstructed, tracking data can be exported from Motive in various file formats.

**Exporting Tracking Data**

<figure><img src="../../.gitbook/assets/image (775).png" alt=""><figcaption></figcaption></figure>

[**Reconstruction** ](../../motive-ui-panes/data-pane.md#reconstruct)is required to export Marker data, [**Auto-label**](../../motive-ui-panes/data-pane.md#auto-label) is required when exporting Markers labeled from Assets, and [**Solving** ](../../motive-ui-panes/data-pane.md#solve-all-assets)is required prior to exporting Assets.

If the recorded _Take_ includes Rigid Body or Skeleton trackable assets, make sure all of the Rigid Bodies and Skeletons are _Solved_ prior to exporting. The solved data will contain positions and orientations of each Rigid Body and Skeleton. If changes have been made to either the Rigid Body or Skeleton, you will need to solve the assets again prior to exporting.&#x20;

{% hint style="info" %}
Please note that if you have Assets that are unsolved and just wish to export reconstructed Marker data, you can toggle off Rigid Body and Skeleton Bones from the Export window (see image below).&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Data Export - Bones excluded.PNG" alt=""><figcaption><p><em>Save As</em> a CSV file, <em>Specific</em> settings shown, and <em>Rigid Body Bones</em> and <em>Skeleton and Markerset Bones</em> highlighted. </p></figcaption></figure>

### Export Settings

In the export dialog window, the frame rate, the measurement scale and type (meters, centimeters or millimeters), the Axis convention, and the frame range of exported data can be configured. Additional export settings are available for each export file formats. Read through below pages for details on export options for each file format:

* [Data Export: CSV](data-export-csv.md)
* [Data Export: C3D](data-export-c3d.md)
* [Data Export: FBX](data-export-fbx.md)
* [Data Export: BVH](data-export-bvh.md)
* [Data Export: TRC](data-export-trc.md)

![Tracking data export dialogue window in Motive. CSV export is selected, and corresponding General options are displayed.](<../../.gitbook/assets/Data Export - CSV General Settings.png>)

### Tracking Data Export Steps

**Exporting a Single Take**

**Step 1.** Open and select a _Take_ to export from the [Data pane](../../motive-ui-panes/data-pane.md). The selected _Take_ must contain reconstructed 3D data.

**Step 2.** Under the _File_ tab on the command bar, click _File → Export Tracking Data_. This can also be done by right-clicking on a selected _Take_ from the [Data pane](../../motive-ui-panes/data-pane.md) and clicking _Export Tracking Data_ from the context menu.

**Step 3.** On the export dialogue window, select a file format and configure the corresponding export settings.

* To export the entire frame range, set _Start Frame_ and _End Frame_ to _Take First Frame_ and _Take Last Frame_.
* To export a specific frame range, set _Start Frame_ and _End Frame_ to _Start of Working Range_ and _End of Working Range_.

**Step 4.** Click _Save_.

![Make sure all Rigid Bodies are solve prior to export.](<../../.gitbook/assets/image (922).png>)

{% hint style="info" %}
**Working Range:**

The working range (also called the playback range) is both the view range and the playback range of a corresponding _Take_ in Edit mode. Only within the working frame range will recorded tracking data be played back and shown on the graphs. This range can also be used to output specific frame ranges when exporting tracking data from Motive.

The working range can be set from the following places:

* In the navigation bar of the Graph View pane, you can drag the handles on the scrubber to set the working range.
* You can also use the navigation controls on the Graph View pane to zoom in or zoom out on the frame ranges to set the working range. See: [Graph View pane](../../motive-ui-panes/graph-view-pane.md) page.
* Start and end frames of a working range can also be set from the [Control Deck](../../motive-ui-panes/control-deck.md) when in the Edit mode.
{% endhint %}

![Working range (48 \~ 345) shown on the navigation bar at the bottom of the Graph View pane.](<../../.gitbook/assets/image (921).png>)

**Exporting Multiple Takes**

**Step 1.** Under the [Data pane](../../motive-ui-panes/data-pane.md), shift + select all the _Takes_ that you wish to export.

**Step 2.** Right-click on the selected _Takes_ and click _Export Tracking Data_ from the context menu.

**Step 3.** An export dialogue window will display to batch export tracking data.

**Step 4.** Select the desired output format and configure the corresponding export settings.

**Step 5.** Select frame ranges to export under the _Start Frame_ and the _End Frame_ settings. You can either export entire frame ranges or specified frame ranges on all of the Takes. When exporting specific ranges, desired working ranges must be set for each respective Takes.

* To export entire frame ranges, set _Start Frame_ and _End Frame_ to _Take First Frame_ and _Take Last Frame_.
* To export specific frame ranges, set _Start Frame_ and _End Frame_ to _Start of Working Range_ and _End of Working Range_.

**Step 6.** Click _Save_.

{% hint style="info" %}
**Motive Batch Processor:**

Exporting multiple Take files with specific options can also be done through a [Motive Batch Processor](../motive-batch-processor.md) script. For example, refer to the _FBXExporterScript.cs_ script found in the MotiveBatchProcessor folder.
{% endhint %}

### File Formats

Motive exports reconstructed 3D tracking data in various file formats and exported files can be imported into other pipelines to further utilize capture data. Available export formats include CSV, C3D, FBX, BVH, and TRC. Depending on which options are enabled, exported data may include reconstructed marker data, 6 Degrees of Freedom (6 DoF) Rigid Body data, or Skeleton data. The following chart shows what data types are available in different export formats:

<table><thead><tr><th align="center">Tracking Data Type</th><th width="100" align="center">CSV</th><th width="100" align="center">C3D</th><th width="100" align="center">FBX</th><th width="100" align="center">BVH</th><th width="100" align="center">TRC</th></tr></thead><tbody><tr><td align="center">Reconstructed 3D Marker Data</td><td align="center">•</td><td align="center">•</td><td align="center">•</td><td align="center"></td><td align="center">•</td></tr><tr><td align="center">6 Degrees of Freedom Rigid Body Data</td><td align="center">•</td><td align="center"></td><td align="center">•</td><td align="center"></td><td align="center"></td></tr><tr><td align="center">Skeleton Data</td><td align="center">•</td><td align="center">•</td><td align="center">•</td><td align="center">•</td><td align="center">•</td></tr></tbody></table>

{% hint style="info" %}
CSV and C3D exports are supported in both Motive Tracker and Motive Body licenses. FBX, BVH, and TRC exports are only supported in Motive Body.
{% endhint %}

## Camera Calibration Export

A calibration definition of a selected take can be exported from the _Export Camera Calibration_ under the _File_ tab. Exported calibration (CAL) files contain camera positions and orientations in 3D space, and they can be imported in different sessions to quickly load the calibration as long as the [camera setup](../../hardware/) is maintained.

Read more about calibration files under the [Calibration](../calibration/) page.

![Export Calibration window. ](<../../.gitbook/assets/image (909).png>)

## Export Assets Definition

Assets can be exported into the Motive user profile (.MOTIVE) file if it needs to be re-imported. The [user profile](../motive-basics.md#motive-user-profile-.motive) is a text-readable file that contains various configuration settings in Motive, including the asset definitions.

When an asset definition is exported to a MOTIVE user profile, it stores marker arrangements calibrated in each asset, and they can be imported into different takes without creating a new one in Motive. Note that these files specifically store the spatial relationship of each marker, and therefore, only the identical marker arrangements will be recognized and defined with the imported asset.

To export the assets, go to the _File menu_ and select _Export Assets_ to export all of the assets in the Live-mode or in the current TAK file(s). You can also use _File_ → _Export Profile_ to export other software settings including the assets.

![Exporting Assets into the User Profile.](<../../.gitbook/assets/image (140) (1) (1) (2).png>) ![Exporting user profile that includes assets. This dialogue window is from the Export Profile As... option.](<../../.gitbook/assets/image (453) (2).png>)

## Analog Data Export

***

Recorded NI-DAQ analog channel data can be exported into **C3D** and **CSV** files along with the mocap tracking data. Follow the tracking data export steps outlined above and any analog data that exists in the TAK will also be exported.

**C3D Export:** Both mocap data and the analog data will be exported onto a same C3D file. Please note that all of the analog data within the exported C3D files will be logged at the same sampling frequency. If any of the devices are captured at different rates, Motive will automatically resample all of the analog devices to match the sampling rate of the fastest device. More on C3D files: [https://www.c3d.org/](https://www.c3d.org/)

**CSV Export:** When exporting tracking data into CSV, additional CSV files will be exported for each of the NI-DAQ devices in a _Take_. Each of the exported CSV files will contain basic properties and settings at its header, including device information and sample counts. The voltage amplitude of each analog channel will be listed. Also, mocap frame rate to device sampling ratio is included since analog data is usually sampled at higher sampling rates.

### **Common Axis Conventions**

<figure><img src="../../.gitbook/assets/image (1512).png" alt=""><figcaption><p>C3D export setting for applications using z-up right-handed coordinate systems.</p></figcaption></figure>

Motive uses a different coordinate system than the system used in common biomechanics applications. To update the coordinate system to match your 3D analysis software during export, select the appropriate Axis Convention from the Export window.&#x20;

* For CSV, BVH, TRC formats, select _Entertainment, Measurement_, or _Custom_
* For C3D format, select _Visual 3D/Motion Monitor, MotionBuilder_, or _Custom_

{% hint style="info" %}
FBX formats do not include the option to change the Axis Convention.&#x20;
{% endhint %}

### Custom Axis&#x20;

<div><figure><img src="../../.gitbook/assets/Data Export - Custom Axis Convention.png" alt=""><figcaption><p>Edit the X/Y/Z axis directly using the <em>Custom</em> Axis Convention option. </p></figcaption></figure> <figure><img src="../../.gitbook/assets/Data Export - Custom Axis set default.png" alt=""><figcaption><p>Reset or Set as Default.</p></figcaption></figure></div>

Select the Custom axis convention to open up the X/Y/Z axis for editing. This creates a drop-down menu next to each axis that allows you to change it.&#x20;

Click the curved arrow to the right of the field to reset the axis to its previous value, or to make your selection the default option. &#x20;

## Reference Video Export

When there is an MJPEG reference camera or a color camera in a _Take_, its recorded video can be exported into an AVI file or into a sequence of JPEG files. The _Export Video_ option is located under the _File_ menu, or you can also right-click on a TAK file from the [Data pane](../../motive-ui-panes/data-pane.md) and export from there. Read more about recording reference videos on the [Data Recording](../data-recording/) page.

{% hint style="danger" %}
**Reference Video Type:** Only compressed MJPEG reference videos or color camera videos can be recorded and exported from Motive. Export for raw grayscale videos is not supported.
{% endhint %}

{% hint style="danger" %}
**Media Player:** The exported videos may not be playable on Windows Media Player, please use a more robust media player (e.g. VLC) to play the exported video files.
{% endhint %}

![Export video dialog window - General Options.](<../../.gitbook/assets/Export Video Options.png>)

### Video Export General Options

| Option                 | Description                                                                                                                                                                                                                                                                                                                                                                                                           |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Frame Resampling       | Adjusts the frame rate of the exported video from full (every frame) to half, quarter, 1/8 or 1/16 of the original.                                                                                                                                                                                                                                                                                                   |
| Start Frame            | Start frame of the exported data. You can set it to the recorded first frame of the exported _Take_ (the default option)_,_ to the start of the working range (or scope range), as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) or in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md), or select _Custom_ to enter a specific frame number.                             |
| End Frame              | End frame of the exported data. You can set it to the recorded end frame of the exported _Take_ (the default option)_,_ to the end of the working range (or scope range), as configured under the [Control Deck](../../motive-ui-panes/control-deck.md) of in the [Graph View pane](../../motive-ui-panes/graph-view-pane.md), or select _Custom_ to enter a specific frame number.                                   |
| Playback Rate          | Sets the playback speed for the exported video. Options are Full Speed (default), half speed, quarter speed, and 1/8 speed.                                                                                                                                                                                                                                                                                           |
| Video Format           | Reference videos can be exported into AVI files using either H.264 or MJPEG compression formats, or as individual JPEG files (JPEG sequence). **The H.264 format will allow faster export of the recorded videos and is recommended.**                                                                                                                                                                                |
| Maximum File size (MB) | Sets the maximum size for video export files, in megabytes. Large videos will be separated into multiple files, which will not exceed the size value set here.                                                                                                                                                                                                                                                        |
| Dropped Frames         | Determines how dropped frames will be handled in the video output. _Last Frame_ (the default) will display the last good frame through the end of the video. _Black Frame_ will replace each dropped frame with a black frame. Both of these options will preserve the original video length, whereas _Drop Frame_ will truncate the video at the first dropped frame.                                                |
| Naming Convention      | Sets the naming convention for the video export. The _Standard_ naming convention is _Take\_Name (Camera Serial Number)_ e.g., Skeleton\_Walking (M21614). The _Prefix Camera ID_ convention will include the number assigned to the camera in Motive at the beginning, followed by the Take name e.g., Cam\_1\_Skeleton\_Walking. This latter option will also create a separate folder for each camera's AVI file.  |
| Camera                 | Select the camera(s) for the video export:  All reference cameras, or custom.                                                                                                                                                                                                                                                                                                                                         |

### Video Export Overlay Options

<figure><img src="../../.gitbook/assets/Data Export - Video overlay options (1).png" alt=""><figcaption><p>Overlay options for reference video exports.</p></figcaption></figure>

{% hint style="info" %}
Overlay options add layers of information to the exported video.&#x20;
{% endhint %}

| Overlay       | Description                                                                        |
| ------------- | ---------------------------------------------------------------------------------- |
| Time Data     | Includes the frame reference number in the bottom left corner.                     |
| Cameras       | Labels all cameras visible in the reference video with the Motive-assigned number. |
| Markers       | Displays markers using the color scheme assigned in Motive.                        |
| Rigid Bodies  | Shows the Rigid Body bone and constraints for all solved Rigid Bodies in the take. |
| Skeletons     | Displays bones for all solved skeletons.                                           |
| Markersets    | Displays bones for all solved trained markersets.                                  |
| Force Plates  | Displays force plate(s) used in the take.                                          |
| Marker Sticks | Displays the marker sticks for all solved assets used in the take.                 |
| Logo          | Adds the OptiTrack logo to the top right corner of the video.                      |

## Audio Export

When a recorded capture contains audio data, an audio file can be exported through the _Export Audio_ option on the File menu or by right-clicking on a Take from the [Data pane](../../motive-ui-panes/data-pane.md).

## Export Skeleton Marker Labels

Skeletal marker labels for Skeleton assets can be exported as XML files (example shown below) from the [Data pane](../../motive-ui-panes/data-pane.md). The XML files can be imported again to use the stored marker labels when creating new Skeletons.

For more information on Skeleton XML files, read through the [Skeleton Tracking](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md) page.

![Exporting Skeleton marker XML template from the Asset Pane (left) or the Constraints Pane (right).](<../../.gitbook/assets/Export Skeleton Constraints from Assets or Constraints.png>)

**Sample Skeleton Label XML File**

```cpp
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

## Export Device Info

Cameras and other devices can now be exported to a CSV file. From the _File_ menu, select _Export Device Info..._

<figure><img src="../../.gitbook/assets/Data Export - FILE menu and excel export of devices.png" alt=""><figcaption><p>Export Device Info from the File menu (left) with resulting CSV file (right).</p></figcaption></figure>

The CSV file includes the device serial number and name.&#x20;

* For Cameras, the name is pre-defined and includes the camera model and serial number.&#x20;
* For all other devices, Motive will export the product serial number along with the name assigned in the device's properties. If no name is entered, the field will be left blank.&#x20;

<figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption><p>Properties pane for a Force Plate asset.</p></figcaption></figure>
