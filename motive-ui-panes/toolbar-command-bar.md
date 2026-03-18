# Toolbar/Command Bar

This page lists out the options that are available on the toolbar and the command bar of Motive.

## Toolbar

![](<../.gitbook/assets/image (937).png>)

![The Motive Toolbar](<../.gitbook/assets/image (1010).png>)

| Icon                                       | Function                              | Description                                                                                                                                                      |
| ------------------------------------------ | ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![](<../.gitbook/assets/image (1001).png>) | Open File                             | Open Motive files: Project (TTP), Calibration (CAL), Takes (TAK), Rigid bodies (TRA), Skeletons (SKL).                                                           |
| ![](<../.gitbook/assets/image (1022).png>) | Save Current Take                     | Save currently opened Take.                                                                                                                                      |
| ![](<../.gitbook/assets/image (966).png>)  | Save All Takes                        | Save all of the Takes that are loaded in the [Data pane](data-pane.md).                                                                                          |
| ![](<../.gitbook/assets/image (963).png>)  | [Application Settings](settings/)     | Opens Application Setting pane for software preferences. Reconstruction settings will also be modified in this pane.                                             |
| ![](<../.gitbook/assets/image (1024).png>) | Hide all panes                        | Closes all the panes in the layout, leaving only the main viewport.                                                                                              |
| ![](<../.gitbook/assets/image (973).png>)  | [Devices pane](devices-pane.md)       | Opens the Devices (Cameras) Pane.                                                                                                                                |
| ![](<../.gitbook/assets/image (1009).png>) | [Calibration](calibration-pane.md)    | Opens Calibration Pane.                                                                                                                                          |
| ![](<../.gitbook/assets/image (978).png>)  | [Data pane](data-pane.md)             | Opens the [Data pane](data-pane.md) for managing takes.                                                                                                          |
| ![](<../.gitbook/assets/image (965).png>)  | [Assets pane](assets-pane.md)         | Opens the [Assets pane](assets-pane.md) for managing the list of tracked assets as well as integrated devices such as force plates and data acquisition devices. |
| ![](<../.gitbook/assets/image (949).png>)  | [Properties pane](properties-pane/)   | Opens the [Properties pane](properties-pane/) for managing the properties of selected items in Motive.                                                           |
| ![](<../.gitbook/assets/image (1018).png>) | [Builder pane](builder-pane.md)       | Opens the [Builder pane](builder-pane.md) for defining or modifying Rigid Body or Skeleton assets in Motive.                                                     |
| ![](<../.gitbook/assets/image (992).png>)  | [Constraints pane](constraints-pane/) | Opens the Marker Sets pane for creating and configuring constraints for markers labels associated each assets.                                                   |
| ![](<../.gitbook/assets/image (991).png>)  | [Edit Tools Pane](edit-tools-pane.md) | Opens Edit Tools for post-processing pipelines.                                                                                                                  |
| ![](<../.gitbook/assets/image (1025).png>) | [Labeling Pane](labels-pane.md)       | Opens the Labeling pane for labeling the markers.                                                                                                                |
| ![](<../.gitbook/assets/image (975).png>)  | [Graph View pane](graph-view-pane.md) | Opens [Graph View pane](graph-view-pane.md) for monitoring the channel data.                                                                                     |
| ![](<../.gitbook/assets/image (1000).png>) | [Log pane](log-pane.md)               | Opens the Status Log for monitoring the activity.                                                                                                                |
| ![](<../.gitbook/assets/image (962).png>)  | [Viewport](viewport.md)               | Adds extra Viewports.                                                                                                                                            |
| ![](<../.gitbook/assets/image (951).png>)  | [Probe pane](probe-pane.md)           | Opens the [Probe pane](probe-pane.md) for collecting sample points using the [Probe](../motive/measurement-probe-kit-guide.md).                                  |
| ![](<../.gitbook/assets/image (967).png>)  | [Info pane](info-pane.md)             | Opens the [Info pane](info-pane.md) for monitoring real-time tracking data of a selected Rigid Body in Motive.                                                   |

## Command Bar

![Options under the File tab.](<../.gitbook/assets/image (997).png>)

### File

#### **Open File**

Prompts user to select a file to open. Applicable files include Take files (.tak), Camera Calibration files (.cal), Motive user profile (.motive), Rigid Body definitions (.tra _deprecated_), Skeleton defintions (.skl _deprecated_).

#### **Open Folder**

Imports a session folder into Motive. All of the TAK files within the session folder will be loaded in the [Data pane](data-pane.md).

#### **Import CSV**

Import a list of _Take_ names to record from a CSV file that contains _Take_ names on each row. This allows users to plan which motions to capture ahead of the time (See: [Data Recording](../motive/data-recording/) page). Import CSV can also be used to load a [Rigid Body](../motive/rigid-body-tracking/) that has been exported to CSV format from the [Assets pane](assets-pane.md).

#### **Open Recent**

Shows a list of Motive compatible files that were recently loaded into Motive.

#### **Save Take**

Saves currently opened _Take_.

#### **Save Take As...**

Prompts the user to select a filename and a directory to save the current _Take_.

#### **Save All Takes**

Save all _Takes_ from all of the sessions loaded in the [Data pane](data-pane.md).

#### **Export Tracking Data...**

Exports tracking data from a selected Take into the desired output format. See: [Data Export](../motive/data-export/).

#### **Export Video...**

Exports reference video to an AVI file. To play this file in Windows Media Player, a codec needs to be installed.

#### **Export Audio...**

**E**xports audio to into a WAV file. See: [Audio Recording in Motive](../motive/audio-recording.md).

#### **Export Calibration...**

Exports the current system calibration file(.cal) to a desired location.

#### **Export Profile As...**

Exports the current software configurations into an application profile (MOTIVE).

{% hint style="info" %}
**Profile (MOTIVE) files:** MOTIVE profile stores software configurations. Software setting such as applications settings, streaming setting, trackable assets, synchronization configurations, and/or device configurations can be saved into this file. This file can be exported and imported to configurations in Motive.
{% endhint %}

#### **Export Assets...**

Export just the [assets](../motive/assets/) (Rigid Bodies, Skeletons, Marker Sets) to a MOTIVE file.

#### **Export Device Info...**

Exports the devices currently connected to Motive into a CSV file (ie. Cameras and their serial numbers).

#### **Update Default Profile**

Manually update the current software configurations onto the [default system profile](../motive/motive-basics.md). Which loads up at first when launching Motive and located under `C:\ProgramData\OptiTrack\MotiveProfile.motive`.

#### **Exit**

Closes the Motive application.

### Edit

![Options under the Edit tab.](<../.gitbook/assets/image (972).png>)

#### **Undo**

Reverts data processing actions (i.e. deleting data, merging markers, filling gaps).

#### **Redo**

Reverts an Undo.

#### **Trim Current Take**

Archives the original take file and crops out the working range selected in the [Graph View pane](graph-view-pane.md). For more information, read through the [Trimming Captured Takes](../motive/data-editing.md#trimming-captured-takes).

#### **Settings**

Opens the Application Settings pane.

#### **Reset Settings**

Sets all application settings to the default setting.

### View

![Options under the View tab.](<../.gitbook/assets/image (955).png>)

#### **Hide All**

This closes all of Motive's panes except the main viewport.

#### **Devices**

Opens the [Devices pane](devices-pane.md) for controlling cameras and other devices in the system

#### **Calibration**

Opens the [Calibration](calibration-pane.md) for calibrating the camera system.

#### **Data**

Opens the [Data pane](data-pane.md) for managing the recorded captures.

#### **Assets**

Opens the [Assets pane](assets-pane.md) for managing the list of tracked assets as well as integrated devices such as force plates and data acquisition devices.

#### **Properties**

Opens the [Properties pane](properties-pane/) for managing the properties of selected items in Motive.

#### **Info**

Opens the [Info pane](info-pane.md) for monitoring real-time tracking data of a Rigid Body.

#### **Builder**

Opens the [Builder pane](builder-pane.md) for creating trackable models or assets. Specifically, this pane is used for creating [Rigid Body](builder-pane.md#rigid-body-create) models and [Skeleton](builder-pane.md#Skeleton-create) models in Motive.

#### **Constraints**

Opens the [Constraints pane](constraints-pane/) for managing selected Marker Sets assets.

#### **Edit Tools**

Opens the [Edit Tools pane](edit-tools-pane.md). For post-processing recorded marker data.

#### **Labels**

Opens the [Labels pane](labels-pane.md). For monitoring, assigning, and/or modifying marker labels.

#### **Graph 1 & Graph 2**

Opens [Graph View pane](graph-view-pane.md) for monitoring the channel data.

#### **Viewer**

Opens an additional [Viewport](viewport.md) for additional viewports for monitoring 3D tracking and camera views.

#### **Data Streaming pane**

Opens the Data Streaming pane. See: [Data Streaming](../motive/data-streaming.md)

#### **Log**

Opens the [Log pane](log-pane.md) for status messages.

#### **Probe**

Opens the [Probe pane](probe-pane.md) for using the [Measurement Probe](../motive/measurement-probe-kit-guide.md).

#### **Toolbar**

Toggles display of the Toolbar on/off.

### Layout

![Options under the Layout tab.](<../.gitbook/assets/image (970).png>)

{% hint style="danger" %}
**Note:** Layouts created versions prior to 2.0 are not compatible. Please re-create and update the layouts for use.
{% endhint %}

#### **Calibrate**

Displays panes applicable to system calibration. (Cameras, Perspective View, Camera Preview, Camera Calibration, Reconstruction)

#### **Create**

Displays panes applicable to asset creation and modification. (Project, Perspective View, Timeline, Skeleton, Rigid Bodies)

#### **Capture**

Displays panes applicable to capturing a take. (Project, Perspective View, Timeline)

#### **Edit**

Displays panes applicable to editing a take. (Project, Perspective View, Timeline, Edit Tools).

#### **Create Layout**

Saves the current layout. Saved custom layouts can be accessed from the drop-down menu located at the top-right corner of Motive.

#### **Delete Layout**

Deletes the saved custom layout.

#### **Update Current**

Updates the selected custom layout from the drop-down menu located at the top-right corner of Motive.

#### **Set as Default**

Sets the current layout as a default layout setup for starting Motive.

#### **Custom Layouts**

List of custom layouts that are created by the user. In the screenshot, Label Fix and Skeleton Label layouts are added as an example

### Help

![Options under the Help tab.](<../.gitbook/assets/image (1019).png>)

#### **Contact Support...**

Opens the OptiTrack support site.

#### **OptiTrack Forums...**

Opens the OptiTrack community forum

#### **Quick Start**

Links you to our Quick Start Guide.

#### **Wiki...**

Links you to the online documentation.

#### **Product...**

Links you to our Quick Start Guide.

#### **News...**

Opens NaturalPoint's news feed.

#### **Startup News Check**

This is a toggle for receiving notifications for Motive updates.

#### **License Folder**

Opens the folder location of your license files.

#### **About Motive**

Displays information about the version of Motive currently running.
