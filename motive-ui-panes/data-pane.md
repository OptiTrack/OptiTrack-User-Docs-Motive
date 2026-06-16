---
description: An overview of the Data pane and its contents.
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/data-pane
---

# Data Pane

## Overview

The Data pane is used to manage the Take files. This pane can be accessed under the [View tab](toolbar-command-bar.md#view) in Motive or by clicking the <img src="../.gitbook/assets/image (1470).png" alt="" data-size="line"> icon on the main toolbar.

<figure><img src="../.gitbook/assets/Data Pane - Advanced layout explained (2).png" alt="An annotated screenshot from Motive of the Data pane."><figcaption><p>Click image to enlarge.</p></figcaption></figure>

### Pane Options menu

Click the <img src="../.gitbook/assets/Motive Context Menu (31).png" alt="A screenshot from Motive of the Data Pane context menu button." data-size="line"> button in the top right corner of the pane to open the Pane Options menu.&#x20;

<figure><img src="../.gitbook/assets/Data Pane Menu Options 3.3.png" alt="A screenshot from Motive of of the Data Pane Options menu."><figcaption><p>Data Pane options.</p></figcaption></figure>

<details>

<summary>Simple</summary>

Use the simplest data management layout.

</details>

<details>

<summary>Advanced</summary>

Includes additional column headers in the layout.

</details>

<details>

<summary>Custom Layouts (Optional)</summary>

Any custom layouts created by the user are available in the menu directly under the Advanced option, using the name selected by the user (_Custom 1_ in the example, above.)&#x20;

</details>

<details>

<summary>New...</summary>

Create a new custom layout.&#x20;

</details>

<details>

<summary>Rename</summary>

Rename a custom layout.

</details>

<details>

<summary>Delete</summary>

Delete a custom layout.

</details>

<details>

<summary>Import Shot List...</summary>

Import a list of empty _Take_ names and notes from either a CSV or XML file. This is helpful when you plan a list of shots in advance to the capture.&#x20;

</details>

<details>

<summary>Export Shot List...</summary>

Exports a list of Take information into either a CSV or XML file. Included elements are name of the session, name of the take, file directory, involved assets, notes, time range, duration, and number of frames included.

</details>

## List of Session Folders

The leftmost section of the Data pane is used to list the sessions that are loaded in Motive. Session folders in Motive group multiple associated _Take_ files, and they can be imported simply by dragging-and-dropping or importing <img src="../.gitbook/assets/Data Pane - Import Folder.png" alt="A screenshot from Motive of the &#x22;Open Session folder&#x22; icon." data-size="line"> a folder into the data management pane. When a session folder is loaded, all of the _Take_ files within the folder are loaded altogether.

In the list of session folders, the currently loaded session folder will be denoted with a flag symbol <img src="../.gitbook/assets/Data Pane - Flag for current folder.png" alt="A screenshot from Motive of the flag icon that denotes the currently open session folder." data-size="line"> , and the selected session folder will be highlighted in white.

**Session Folder Buttons**

* <img src="../.gitbook/assets/Data Pane - Add session folder.png" alt="A screenshot from Motive of the Data pane button to add a new session folder." data-size="line">  Add a new session folder. The new folder will be saved in the Motive's default location.&#x20;
* <img src="../.gitbook/assets/Data Pane - Data Mgmt Pane.png" alt="A screenshot from Motive of the Data pane button to toggle on/off the viewing of the Sessions folders list. " data-size="line"> Collapse the session folder sidebar.

<figure><img src="../.gitbook/assets/image (259).png" alt="A screenshot from Motive of the Data pane with the list of loaded session folders highlighted. The current session folder is noted with a flag icon."><figcaption><p>List of loaded session folders. Current session folder is noted with a flag icon.</p></figcaption></figure>

### Context Menu Options

Right-click on any session folder to see the following options:&#x20;

<figure><img src="../.gitbook/assets/Data Pane - Session list context menu.png" alt="A screenshot from Motive of the Session Folder context menu."><figcaption><p>Session Folder context menu.</p></figcaption></figure>

<details>

<summary><strong>Create Sub-Folder</strong></summary>

This creates a new folder under the selected directory.

</details>

<details>

<summary>Show Folder Location</summary>

Opens the session folder from Windows File Explorer.

</details>

<details>

<summary>Remove</summary>

Removes the selected session folder from the list without deleting them.&#x20;

</details>

<details>

<summary>Delete</summary>

Deletes the session folder. All of the folder's contents will be deleted as well.

</details>

## List of Takes

When a session folder is selected, associated _Take_ files and their descriptions are listed in a table format on the right side of the Data pane. For each _Take_, general descriptions and basic information are shown in the columns of the respective row.&#x20;

To view additional fields, click on the pane menu, select _new_ to create a custom view, and all of the possible fields will be available to add to the new view. Right-click on the column header to select the columns to display. For each of the enabled columns, you can click on the arrow next to it to sort up/down the list of _Takes_ depending on the category.

<figure><img src="../.gitbook/assets/image (395).png" alt="A screenshot from Motive of the data pane, with the list of take names section highlighted."><figcaption></figcaption></figure>

### Take Information

The following information about each take is available in the Data pane. To see all data, create a custom view that includes all fields.&#x20;

<details>

<summary>Best</summary>

The star icon ![](<../.gitbook/assets/image (1476).png>) allows users to mark the best _Takes_. Simply click on the star icon and mark the successful _Takes_.

</details>

<details>

<summary>Health</summary>

The <img src="../.gitbook/assets/image (1471).png" alt="" data-size="line"> health status column of the _Takes_ indicates the user-selected status of each take:

* <img src="../.gitbook/assets/image (1472).png" alt="" data-size="line"> : Excellent capture
* <img src="../.gitbook/assets/image (1473).png" alt="" data-size="line"> : Okay capture
* ![](<../.gitbook/assets/image (1475).png>) : Poor capture

</details>

<details>

<summary>Progress</summary>

The progress indicator is used to track processing of the _Takes_. Use the indicators to track the workflow-specific progress of each _Take_. Right-click to select:&#x20;

* Ready
* Recorded
* Reviewed
* Labeled
* Cleaned
* Exported

</details>

<details>

<summary>Name</summary>

Shows the name of the Take.

</details>

<details>

<summary>2D</summary>

Indicates whether [2D data](https://v30.wiki.optitrack.com/index.php?title=Data_Types#2D_Data) exists on the corresponding _Take._

</details>

<details>

<summary>3D</summary>

Indicates whether reconstructed [3D data](../motive/data-recording/data-types.md) exists on the corresponding _Take_.&#x20;

If 3D data does not exist on a _Take_, it can be derived from 2D data by performing the **reconstruction** pipeline. Please see the [Reconstruction](../motive/reconstruction-and-2d-mode.md#post-processing-reconstruction) page for more details.

</details>

<details>

<summary>Video</summary>

Indicates whether [reference videos](../motive/camera-video-types.md#reference-videos) exist in the _Take_. Reference videos are recorded from cameras that are set to either MJPEG grayscale, raw grayscale, or Duplex modes.

</details>

<details>

<summary>Solved</summary>

Indicates whether any of the assets have [solved data](../motive/data-recording/data-types.md#solved-data) baked into them.

</details>

<details>

<summary>Audio</summary>

Indicates whether synchronized audio data have been recorded with the _Take_. See: [Audio Recording in Motive](../motive/audio-recording.md).

</details>

<details>

<summary>Analog</summary>

Indicates whether analog data recorded using a data acquisition device exists in the _Take_. Please see the [NI-DAQ Setup](../movement-sciences/movement-sciences-hardware/ni-daq-setup.md) page for more information on working NI-DAQ devices.

</details>

<details>

<summary>Date Recorded</summary>

Shows the time and the date when the _Take_ was recorded.

</details>

<details>

<summary>Frame Rate</summary>

Shows the camera system frame rate which the _Take_ was recorded in.

</details>

<details>

<summary>Duration</summary>

Time length of the _Take._

</details>

<details>

<summary>Total Frames</summary>

Total number of captured frames in the _Take._

</details>

<details>

<summary>Notes</summary>

Comments and notes on each _Take._

</details>

<details>

<summary>Start Timecode</summary>

Timecode stamped to the starting frame of the _Take_. Available only if a [timecode](../synchronization/optitrack-timecode.md) signal was integrated to the system.

</details>

<details>

<summary>Captured in Version</summary>

Motive version used to record the _Take_.

</details>

<details>

<summary>Last Saved in Version</summary>

Motive version used to edit or save the _Take_.

</details>

### Search Bar

The search bar is located at the bottom of the Data pane. You can search a _selected_ session folder using any number of keywords and search filters. Motive will use the search text to list the matching _Takes_ from the selected session folder. Unless otherwise specified, the search filter will scope to all of the data pane columns.&#x20;

**Search for exact phrase**

* Wrap your search text in quotation marks.
* e.g., Search `"shooting a gun"` for searching a file named _Shooting a Gun.tak_.

**Search specific fields**

* To limit the search to specific columns, type `field:`, plus the name of a column enclosed with quotation marks, and then the value or term you're searching for.
* Multiple fields and/or values may be specified in any order.
* e.g. `field:"name" Lizzy`, `field:"notes" Static capture`.

**Search for true/false values**

* To search specific binary states from the Take list, type the name of the field followed by a colon (:), and then enter either true (\[t], \[true], \[yes], \[y]) or false (\[f], \[false], \[no], \[n]).
* e.g. `Best:[true]`, `Solved:[false]`, `Video:[T]`, `Analog:[yes]`

<figure><img src="../.gitbook/assets/image (1074).png" alt="A screenshot from Motive of the Data Pane with Takes that have been partially processed. "><figcaption><p>Searching for Takes that contains solved assets data.</p></figcaption></figure>

### Customizing Table Layout

The table layout can be customized for the user's specific needs.&#x20;

From the [pane options menu](data-pane.md#pane-options-menu), select _New_ or any of the previously customized layouts. Once you are in a customizable layout, right-click on the top header bar and add or remove categories from the table.

<figure><img src="../.gitbook/assets/Data Pane - Select columns custom view.png" alt="A screenshot from Motive showing the columns available when creating a custom layout for the data pane. "><figcaption><p>Customizing header categories.</p></figcaption></figure>

### Import an Empty Shot List

A list of take names is known as a shot list. Shot lists can be imported from either a CSV or XML file or by copying text that contains a take name on each line, separated by carriage returns. This feature allows you to plan, organize, and create a list of capture names ahead of actual recording. Once a shot list has been imported, a list of _empty_ takes with the corresponding names will be listed for the selected session folder.

**Copy From a Text File**

Take lists can be imported by copying a list of take names and pasting them onto the Data pane. Each take name must be on its own line.&#x20;

<figure><img src="../.gitbook/assets/image (397).png" alt="2 screenshots - the image on the left shows the data pane in Motive with a list of simple take names. The image on the right shows the same list in a text file, with the context menu open and Copy selected. "><figcaption></figcaption></figure>

**From a CSV File**

Take lists can be imported from a CSV file that contains take names on each row. To import, click on the top-right menu icon <img src="../.gitbook/assets/Motive Context Menu (7).png" alt="" data-size="line"> and select _Import Shot List..._

<figure><img src="../.gitbook/assets/Data Pane - Import CSV without notes.png" alt="2 screenshots. The one on the left shows a simple Excel file with a list of take names. The image on the right shows the same list imported into the data pane in Motive, along with the pane menu with the Import Shot List... option highlighted. "><figcaption><p>Empty <em>Takes</em> imported from CSV. </p></figcaption></figure>

{% hint style="warning" %}
Excel has several CSV file formats to choose from. Make sure to select _CSV (Comma Delimited)_ when saving your file for import.&#x20;
{% endhint %}

#### Import a CSV Shot List with Notes

* To display the Take Notes in the Data pane, create a custom layout that includes the Notes field.
* To import multiple columns, the CSV file must contain a header row with column names that match the column headings in Motive, i.e., Name and Notes.&#x20;

{% hint style="info" %}
When preparing the CSV file for import:&#x20;

* The import will fail if there is no column labeled _Name_.&#x20;
* The import will skip the _Notes_ column with an error if it's not correctly labeled.
{% endhint %}

<figure><img src="../.gitbook/assets/Data Pane - Import CSV with notes.png" alt="2 screenshots - 1 of an excel file with a sample list of take names and notes and the other from Motive, showing the same file&#x27;s contents imported into the data pane."><figcaption><p>Empty <em>Takes</em> imported from CSV with Notes included.  </p></figcaption></figure>

#### Import from an XML File

Shot Management Systems often include the ability to export data to an XML file, which can then be imported into Motive. The following XML fields can be imported:

* \<Name>
* \<Notes>

You can still import an XML file into Motive if it contains more fields than those allowed for import. If extra fields are detected, Motive will return the following error message:

<figure><img src="../.gitbook/assets/Import Shot List from prior export.png" alt="A screenshot from Motive of the error message when importing an XML file to the data pane that has more fields than the 2 allowed for import."><figcaption><p>Error message when additional form fields are included in the import file.</p></figcaption></figure>

Click OK to clear the message and continue importing the valid fields.

## Export a Shot List

The Shot List export option provides data on each take in the session folder in either a CSV or XML format. The shot list includes the take Name and the Notes field as well as other information contained in the Data pane such as the [Best ](data-pane.md#best)or [Progress ](data-pane.md#progress)fields. It also includes a list of assets in the take, the duration, number of frames, and other information related to the take.&#x20;

<figure><img src="../.gitbook/assets/Export Shot List - XML data for a take.png" alt="A screenshot of data from an XML file that contains Take information, exported from Motive. "><figcaption><p>Take information exported to an XML file. </p></figcaption></figure>

{% hint style="info" %}
Note that the export contains fields that cannot be imported back into Motive, which allows only the Name and Notes fields to import. See the example in the[ Import from an XML File](data-pane.md#import-from-an-xml-file) section of this document.
{% endhint %}

## Take Menu

Open the context menu for captured _Takes_ by clicking the <img src="../.gitbook/assets/Motive Context Menu (8).png" alt="A screenshot from Motive of the button to open a context menu." data-size="line"> icon to the right of the _Take_ name or by right-clicking on the selected _Take(s)_.&#x20;

The context menu lists options used to perform post-processing pipelines on the selected _Take(s)_. The menu contains essential pipelines such as reconstruction, auto-label, data export and many others. Available options are listed below.

### Context Menu Options

<figure><img src="../.gitbook/assets/Data Pane - Take file context menu.png" alt="A screenshot from Motive of the Context menu for Takes, available from the Data pane."><figcaption><p>Data pane context menu for a selected Take.</p></figcaption></figure>

<details>

<summary>Save</summary>

Saves the selected take.

</details>

<details>

<summary>Revert</summary>

Reverts any changes that were made. This does not work on the currently opened Take.

</details>

<details>

<summary>Make Current</summary>

Selects the current take and loads it for playback or editing.

</details>

<details>

<summary>Rename</summary>

Allows the current take to be renamed.

</details>

<details>

<summary>Show File Location</summary>

Opens an Explorer window to the folder that contains the selected _Take_. This can be helpful when backing up, transferring, or exporting data.

</details>

<details>

<summary>Reconstruct</summary>

Separate reconstruction pipeline without the auto-labeling process. Reconstructs 3D data using the 2D data. Reconstruction is required to export Marker data.&#x20;

</details>

<details>

<summary>Auto-label</summary>

Separate auto-labeling pipeline that labels markers using the existing tracking asset definitions. Available only when 3D data is reconstructed for the _Take_. Auto-label is required to export Markers labeled from Assets.&#x20;

</details>

<details>

<summary><strong>Reconstruct and Auto-label</strong></summary>

Combines 2D data from each camera in the system to create a usable 3D take. It also incorporates assets in the _Take_ to auto-label and create rigid bodies, skeletons, and trained markersets in the Take. Reconstruction is required to export Marker data and Auto-label is required when exporting Markers labeled from Assets.&#x20;

</details>

<details>

<summary><strong>Solve All Assets</strong></summary>

Solves 6 DoF tracking data of skeletons, rigid bodies, and trained markersets and bakes them into the _Take_. When the assets are solved, Motive reads from the recorded Solve instead of processing the tracking data in real-time. Solving is required prior to exporting Assets.&#x20;

</details>

<details>

<summary><strong>Reconstruct, Auto-label, and Solve</strong></summary>

Performs all three reconstruct, auto-label, and solve pipelines in consecutive order. This recreates 3D data from recorded 2D camera data.

</details>

<details>

<summary><strong>Export Tracking Data</strong></summary>

Opens the Export dialog window to select and initiate file export. Valid formats for export are CSV, C3D, FBX, BVH.&#x20;

Reconstruction is required to export Marker data, Auto-label is required when exporting Markers labeled from Assets, and Solving is required prior to exporting Assets.

{% hint style="info" %}
Please note that if you have Assets that are unsolved and just wish to export reconstructed Marker data, you can toggle off Rigid Bodies and Bones (Skeletons) from the Export window (see image below). For more information please see our [Data Export](../motive/data-export/) page.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/Export Options to exclude unsolved assets MARKED UP.png" alt="A screenshot of the Data Export screen in Motive, with CSV export selected and the options to include Rigid Body Bones and Skeleton and Markerset Bones are both disabled. "><figcaption><p>The Motive export window, with the options to export assets disabled. </p></figcaption></figure>

</details>

<details>

<summary><strong>Export Video</strong></summary>

Opens the export dialog window to initiate scene video export to AVI.

</details>

<details>

<summary><strong>Export Audio</strong></summary>

Exports an audio file when selected _Take_ contains audio data.

</details>

<details>

<summary><strong>Delete 2D / Video / Audio Data</strong></summary>

Opens the Delete 2D Data pop-up where you can select to delete the 2D data, Audio data, or reference video data. Read more in [Deleting 2D data](../motive/data-recording/data-types.md#deleting-2d-video-audio-data).

</details>

<details>

<summary><strong>Delete 3D Data</strong></summary>

Permanently deletes the 3D data from the _Take_. This option is useful if reconstruction or editing causes damage to the data.

</details>

<details>

<summary><strong>Delete Marker Labels</strong></summary>

Unlabels all existing marker labels in 3D data. If you wish to re-auto-label markers using modified asset definitions, first unlabel markers for the respective assets.

</details>

<details>

<summary><strong>Delete All Solved Asset Data</strong></summary>

Deletes 6 DoF tracking data that was solved for skeleton and rigid bodies.&#x20;

When Solved data doesn't exist, Motive calculates tracking of the objects from recorded 3D data in real-time.

</details>

<details>

<summary><strong>Archive Take</strong></summary>

Archives the original take file and creates a duplicate version. We recommend archiving all _Takes_ prior to completing any post-production work. &#x20;

</details>

<details>

<summary><strong>Delete Takes</strong></summary>

Opens a dialog box to confirm permanent deletion of the _take_ and all associated 2D, 3D, and Joint Angle Data from the computer. This option cannot be undone.

</details>

<details>

<summary><strong>Delete All Assets from Take</strong></summary>

Deletes all assets that were recorded in the _Take_.

</details>

<details>

<summary>Enable All Assets in Selected Take</summary>

Enables all assets within the selected _Take_.&#x20;

</details>

<details>

<summary><strong>Copy Assets to Take</strong></summary>

Copies the assets from the current capture to the selected _Takes_.

</details>
