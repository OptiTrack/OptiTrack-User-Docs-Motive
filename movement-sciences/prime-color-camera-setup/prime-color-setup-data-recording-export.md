---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/movement-sciences/prime-color-camera-setup/prime-color-setup-data-recording-export
---

# Prime Color Setup: Data Recording / Export

Once you have set up the system and configured the cameras correctly, Motive is now ready to capture _Takes_. Recorded TAK files will contain color video along with the tracking data, and you can play them back in Motive. Also, the color reference video can be exported out from the TAK.

## Data Recording

Once the camera is set up, you can start recording from Motive. Captured frames will be stored within the TAK file and you can access them again in Edit mode. Please note that capture files with Prime Color video images will be much larger in file size.

![](<../../.gitbook/assets/image (522).png>)

## Video Export

Once the color videos have been saved onto TAK files, the captured reference videos can be exported into AVI files using either H.264 or MJPEG compression format. The H.264 format will allow faster export of the recorded videos and is recommended. Video for the current TAK can be exported by clicking _File tab -> Export Video_ option in Motive, or you can also export directly from the [Data pane](../../motive-ui-panes/data-pane.md) by right-clicking on the Take(s) and clicking Export Video from the context menu. The following export dialogue window will open and you will be able to configure the export settings before outputting the files:

![](<../../.gitbook/assets/image (565).png>)

### **Dropped Frames**

<figure><img src="../../.gitbook/assets/image (828).png" alt=""><figcaption></figcaption></figure>

#### Drop Frame

When this is set to _Drop Frame_, Motive will remove any dropped frames in the color video upon export. This will only occur on cameras that have dropped frames, thus resulting in varying video lengths for each camera.&#x20;

{% hint style="warning" %}
With this option, any dropped frames will be completely removed. The exact frames in the exported file may not match the frames in the corresponding Motive recording.
{% endhint %}

#### Black Frame

If required, you can set this export option to _Black Frame_ to insert black, or blank, frames in place of the dropped frames in the exported video. This will allow for each recording to be the same length.

#### Last Frame

This export setting allows for a dropped frame to use a previous frame to fill in the dropped frame. This will allow for each recording to be the same length. Last Frame is recommended over Black Frame especially for markerless applications.&#x20;

### **Exporting from Multiple TAKs**

If there are multiple TAK files containing reference video recordings, you can export the videos all at once in the [Data pane](../../motive-ui-panes/data-pane.md) or through the [Motive Batch Processor](../../motive/motive-batch-processor.md). When exporting directly from the Data pane, simply CTRL-select multiple TAK files together, right-click to bring up the context menu, and click _Export Video_. When using the batch processor (NMotive), the VideoExporter class can be used to export videos from loaded TAK files.

### Re-encoding Exported Video

The size of the exported video file can be re-encoded and compressed down further by additional subsampling. This can be achieved using a third-party video processing software, and doing so can hugely reduce the size of the exported file; almost in orders of two magnitudes. This is supported by most of the high-end video editing software, but **Handbrake** ([https://handbrake.fr/](https://handbrake.fr/)) is a freely available open-source software that is also capable of doing this. Since the exported video file can be large in size, we suggest using one of the third-party software to re-encode the exported video file.
