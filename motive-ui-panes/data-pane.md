# Data Pane

The Data pane is used for managing the Take files. This pane can be accessed under the [View tab](toolbar-command-bar.md#view) in Motive or by clicking the <img src="../.gitbook/assets/image (140).png" alt="" data-size="line"> icon on the main toolbar.

{% embed url="https://vimeo.com/259377051/78cc5c9ada?embedded=true&owner=15736845&source=vimeo_logo" %}

## Overview

![Click image to enlarge.](<../.gitbook/assets/image (243).png>)

### Pane menu

| Option              | Description                                                                                                                                                                                                                                                                                                                                                              |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Simple              | Use the simplest data management layout.                                                                                                                                                                                                                                                                                                                                 |
| Advanced            | Additional column headers are added to the layout.                                                                                                                                                                                                                                                                                                                       |
| Classic             | Use the classic Motive layout where Take name, availability of 2D data and 3D data is listed.                                                                                                                                                                                                                                                                            |
| New...              | Create a new customizable layout.                                                                                                                                                                                                                                                                                                                                        |
| Rename              | Rename a custom layout.                                                                                                                                                                                                                                                                                                                                                  |
| Delete              | Delete a custom layout.                                                                                                                                                                                                                                                                                                                                                  |
| 2D Mode             | In the Edit mode, when this option is enabled, Motive will access the recorded 2D data of a current _Take_. In this mode, Motive will be live-reconstructing from recorded 2D data and you will be able to inspect the reconstructions and marker rays from the view ports. For more information: [Reconstruction and 2D Mode](../motive/reconstruction-and-2d-mode.md). |
| Import Shot List... | Import a list of empty _Take_ names from a CSV file. This is helpful when you plan a list of shots in advance to the capture.                                                                                                                                                                                                                                            |
| Export Take Info... | Exports a list of Take information into an XML file. Included elements are name of the session, name of the take, file directory, involved assets, notes, time range, duration, and number of frames included.                                                                                                                                                           |

![Data management pane options.](<../.gitbook/assets/image (617).png>)

## List of Session Folders

The left section of the Data pane is used to list out the sessions that are loaded in Motive. Session folders group multiple associated _Take_ files in Motive, and they can be imported simply by dragging-and-dropping or importing a folder into the data management pane. When a session folder is loaded, all of the _Take_ files within the folder are loaded all together.

The session folder can be opened or closed using the <img src="../.gitbook/assets/Data Pane - Data Mgmt Pane.png" alt="" data-size="line"> button at the bottom left corner.&#x20;

In the list of session folders, a currently loaded session folder is noted with a flag symbol <img src="../.gitbook/assets/Data Pane - Flag for current folder.png" alt="" data-size="line"> and a selected session folder will be highlighted in white. To add a new folder, click the <img src="../.gitbook/assets/Add button (1).png" alt="" data-size="line"> button.&#x20;

{% hint style="info" %}
What happened to the Project TTP Files?

The TTP project file format is deprecated starting from the 2.0 release. Now, recorded Takes will be managed by simply loading the session folders directly onto the new Data pane. For exporting and importing the software setting configurations, the Motive profile file format will replace the previous role of the TTP file. In the Motive profile, software configurations such as reconstruction settings, application settings, data streaming settings, and many other settings will be contained. Camera calibration will no longer be saved in TTP files, but they will be saved in the calibration file (CAL) only. TTP files can still be loaded in Motive 2.0. However, we suggest moving away from using TTP files.
{% endhint %}

![List of loaded session folders. Current session folder is noted with a flag icon.](<../.gitbook/assets/image (600).png>)

### Context Menu Options

#### **Set as Current**

Set the selected session as the current session.

#### **Rename**

Rename the session folder.

#### **Create Sub-folder**

This creates a folder under the selected directory.

#### **Show Folder Location**

Opens the session folder from the file explorer

#### **Delete**

Delete the session folder. All of its contents will be deleted as well.

![Context menu on session folders.](<../.gitbook/assets/image (597).png>)

## List of Takes

When a session folder is selected, associated _Take_ files and their descriptions are listed in a table format on the right-hand side of the Data pane. For each _Take_, general descriptions and basic information are shown in the columns of the respective row. To view additional descriptions, click on the pane menu, select the _Advanced_ option, and all of the descriptions will be listed. For each of the enabled columns, you can click on the arrow next to it to sort up/down the list of _Takes_ depending on the category.

![](<../.gitbook/assets/image (621).png>)

### Take Information

| Category       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Best           | The star mark <img src="../.gitbook/assets/image (4) (1).png" alt="" data-size="line"> allows users to mark the best _Takes_. Simply click on the star icon and mark the successful _Takes_.                                                                                                                                                                                                                                                                                            |
| Health         | <p>The <img src="../.gitbook/assets/image (11).png" alt="" data-size="line"> health status column of the <em>Takes</em> indicates the user-selected status of each take:</p><ul><li><img src="../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt="" data-size="line"> : Excellent capture</li><li><img src="../.gitbook/assets/image (3) (1).png" alt=""> : OK capture</li><li><img src="../.gitbook/assets/image (2) (1) (1).png" alt="" data-size="line"> : Poor capture</li></ul> |
| Progress       | <p>The progress indicator can be used to track the process of the <em>Takes</em>. Use the indicators to track down the workflow specific progress of the<em>Takes</em>.</p><ul><li>Ready</li><li>Recorded</li><li>Reviewed</li><li>Labeled</li><li>Cleaned</li><li>Exported</li></ul>                                                                                                                                                                                                   |
| Name           | Shows the name of the Take.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| 2D             | Indicates whether [2D data](https://v30.wiki.optitrack.com/index.php?title=Data_Types#2D_Data) exists on the corresponding _Take_                                                                                                                                                                                                                                                                                                                                                       |
| 3D             | <p>Indicates whether the reconstructed <a href="../motive/data-recording/data-types.md">3D data</a> exists on the corresponding <em>Take</em>.</p><p><br>If 3D data does not exist on a <em>Take</em>, it can be derived from 2D data by performing the <strong>reconstruction</strong> pipeline. See <a href="../motive/reconstruction-and-2d-mode.md#post-processing-reconstruction">Reconstruction</a> page for more details.</p>                                                    |
| Video          | Indicates whether [reference videos](../motive/camera-video-types.md#reference-videos) exist in the _Take_. Reference videos are recorded from cameras that are set to either MJPEG grayscale or raw grayscale modes.                                                                                                                                                                                                                                                                   |
| Solved         | Indicates whether any of the assets have [solved data](../motive/data-recording/data-types.md#solved-data) baked into it.                                                                                                                                                                                                                                                                                                                                                               |
| Audio          | Indicates whether synchronized audio data have been recorded with the _Take_. See: [Audio Recording in Motive](../motive/audio-recording.md)                                                                                                                                                                                                                                                                                                                                            |
| Analog         | Indicates whether analog data recorded using a data acquisition device exists in the _Take_. See: [NI-DAQ Setup](../movement-sciences/movement-sciences-hardware/ni-daq-setup.md) page.                                                                                                                                                                                                                                                                                                 |
| Data Recorded  | Shows the time and the date when the _Take_ was recorded.                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Frame Rate     | Shows the camera system frame rate which the _Take_ was recorded in.                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Duration       | Time length of the _Take._                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Total Frames   | Total number of captured frames in the _Take._                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Notes          | Section for adding commenting on each _Take_.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Start Timecode | Timecode stamped to the starting frame of the _Take_. This is available only if there was [timecode](../synchronization/optitrack-timecode.md) signal integrated to the system.                                                                                                                                                                                                                                                                                                         |

### Search Bar

A search bar is located at the bottom of the Data pane, and you can search a _selected_ session folder using any number of keywords and search filters. Motive will use the text in the input field to list out the matching _Takes_ from the selected session folder. Unless otherwise specified, the search filter will scope to all of the columns.

**Search for exact phrase**

* Wrap your search text in quotation marks.
* e.g. Search `"shooting a gun"` for searching a file named _Shooting a Gun.tak_.

**Search specific fields**

* To limit the search to specific columns, type `field:`, plus the name of a column enclosed with quotation marks, and then the value or term you're searching for.
* Multiple fields and/or values may be specified in any order.
* e.g. `field:"name" Lizzy`, `field:"notes" Static capture`.

**Search for true/false values**

* To search specific binary states from the Take list, type the name of the field followed by a colon (:), and then enter either true (\[t], \[true], \[yes], \[y]) or false (\[f], \[false], \[no], \[n]).
* e.g. `Best:[true]`, `Solved:[false]`, `Video:[T]`, `Analog:[yes]`

![Searching for Takes that contains solved assets data.](<../.gitbook/assets/image (287).png>)

### Customizing Table Layout

The table layout can also be customized. To do so, go to the pane menu and select _New_ or any of the previously customized layouts. Once you are in a customizable layout, right-click on the top header bar and add or remove categories from the table.

![List of layouts from the Data pane menu.](<../.gitbook/assets/image (238).png>)

![Customizing header categories.](<../.gitbook/assets/image (611).png>)

### Importing a List of Empty Takes

A list of take names can be imported from either a CSV file or carriage return texts that contain a take name on each line. Using this feature, you can plan, organize, and create a list of capture names ahead of actual recording. Once take names have been imported, a list of _empty_ takes with the corresponding names will be listed for the selected session folder.

**From Text**

Take lists can be imported by copying a list of take names and pasting them onto the Data pane. Take names must be separated by carriage returns; in other words, each take name must be in a new line.

![](<../.gitbook/assets/image (618).png>)

**From a CSV File**

Take lists can be imported from a CSV file that contains take names on each row. To import, click on the top-right menu icon <img src="../.gitbook/assets/Motive Context Menu.png" alt="" data-size="line"> and select Import Shot List.

![](<../.gitbook/assets/image (259).png>)

## Take Menu

In the Data pane, context menu for captured _Takes_ can be brought up by clicking on the [![ContextMenu dotdotdot.png](https://v30.wiki.optitrack.com/images/c/c4/ContextMenu_dotdotdot.png)](https://v30.wiki.optitrack.com/index.php?title=File:ContextMenu_dotdotdot.png) icon or by right-clicking on a selected _Take(s)_. The context menu lists out the options which can be used to perform corresponding pipelines on the selected _Take(s)_. The menu contains a lot of essential pipelines such as reconstruction, auto-label, data export and many others. Available options are listed below.

### Context Menu Options

![Data pane context menu for a selected Take.](<../.gitbook/assets/image (281).png>)

#### **Save**

Saves the selected take

#### **Revert**

Reverts any changes that were made. This does not work on the currently opened Take.

#### **Make Current**

Selects the current take and loads it for playback or editing.

#### **Rename**

Allows the current take to be renamed.

#### **Show File Location**

Opens an explorer window to the current asset path. This can be helpful when backing up, transferring, or exporting data.

#### **Reconstruct**

Separate reconstruction pipeline without the auto-labeling process. Reconstructs 3D data using the 2D data. Reconstruction is required to export Marker data.&#x20;

#### **Auto-label**

Separate auto-labeling pipeline that labels markers using the existing tracking asset definitions. Available only when 3D data is reconstructed for the _Take_. Auto-label is required to export Markers labeled from Assets.&#x20;

#### **Reconstruct and Auto-label**

Combines 2D data from each camera in the system to create a usable 3D take. It also incorporates assets in the Take to auto-label and create rigid bodies and skeletons in the Take. Reconstruction is required to export Marker data and Auto-label is required when exporting Markers labeled from Assets.&#x20;

#### **Solve All Assets**

Solves 6 DoF tracking data of skeletons and rigid bodies and bakes them into the TAK recording. When the assets are solved, Motive reads from recorded Solve instead of processing the tracking data in real-time. Solving is required prior to exporting Assets.&#x20;

#### **Reconstruct, Auto-label, and Solve**

Performs all three reconstruct, auto-label, and solve pipelines in consecutive order. This basically recreates 3D data from recorded 2D camera data.

#### **Export Tracking Data**

Opens the Export dialog window to select and initiate file export. Valid formats for export are CSV, C3D, FBX, BVH.&#x20;

Reconstruction is required to export Marker data, Auto-label is required when exporting Markers labeled from Assets, and Solving is required prior to exporting Assets.

{% hint style="info" %}
Please note that if you have Assets that are unsolved and just wish to export reconstructed Marker data, you can toggle off Rigid Bodies and Bones (Skeletons) from the Export window (see image below). For more information please see our [Data Export](../motive/data-export/) page.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/image (3) (9).png" alt=""><figcaption></figcaption></figure>

#### **Export Video**

Opens the export dialog window to initiate scene video export to AVI.

#### **Export Audio**

Exports an audio file when selected Take contains audio data.

#### **Delete 2D / Video / Audio Data**

Opens the Delete 2D Data pop-up where you can select to delete the 2D data, Audio data, or reference video data. Read more in [Deleting 2D data](../motive/data-recording/data-types.md#deleting-2d-video-audio-data).

#### **Delete 3D Data**

Permanently deletes the 3D data from the take. This option is useful in the event reconstruction or editing causes damage to the data.

#### **Delete Marker Labels**

Unlabels all existing marker labels in 3D data. If you wish to re-auto-label markers using modified asset definitions, you will need to first unlabel markers for respective assets.

#### **Delete All Solved Asset Data**

Deletes 6 DoF tracking data that was solved for skeleton and rigid bodies. If Solved data doesn't exist, Motive instead calculates tracking of the objects from recorded 3D data in real-time.

#### **Archive Take**

Archives the original take file and creates a duplicate version. Recommended prior to completing any post-production work on the take file. &#x20;

#### **Delete Takes**

Opens a dialog box to confirm permanent deletion of the take and all associated 2D, 3D, and Joint Angle Data from the computer. This option cannot be undone.

#### **Delete All Assets from Take**

Deletes all assets that were recorded in the take.

#### **Copy Assets to Take**

Copies the assets from the current capture to the selected _Takes_.
