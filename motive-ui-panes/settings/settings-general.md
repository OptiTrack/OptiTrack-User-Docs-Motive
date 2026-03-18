# Settings: General

In Motive, the Application Settings can be accessed under the [View tab](../toolbar-command-bar.md#view) or by clicking [![Toolbar AppSettings 20.png](https://v30.wiki.optitrack.com/images/8/8e/Toolbar_AppSettings_20.png)](https://v30.wiki.optitrack.com/index.php?title=File:Toolbar_AppSettings_20.png) icon on the main toolbar. Default Application Settings can be recovered by Reset Application Settings under the Edit Tools tab from the main [Toolbar](../toolbar-command-bar.md).

![](<../../.gitbook/assets/image (353).png>)

## Basic Settings

#### **Take Suffix**

Sets the separator (\_) and string format specifiers (%03d) for the suffix added after existing file names.

#### **Auto Archive Takes**

Enable/Disable auto-archiving of _Takes_ when [trimming _Takes_](../../motive/data-editing.md#trimming-captured-takes).

#### **Persistent Data Folders**

When enabled, all of the session folders loaded in the [Data pane](../data-pane.md) will be persisted when exiting and launching Motive again next time.

#### **Device Profile**

\_\[Advanced]\_Sets the default device profile, XML format, to load onto Motive. The device profile determines and configures the settings for peripheral devices such as force plates, NI-DAQ, or navigation controllers.

#### **Glove Server Address**

_\[Advanced]_ Enter IP address of glove. Leave blank to use Local Host IP.

### Camera Displays

#### **Numeric LEDs**

Enable or disable the LED panel in front of cameras that displays assigned camera numbers.

#### **Camera ID**

Sets how Camera IDs are assigned for each camera in a setup. Available options are _By Location_ and _By Serial Number_. When assigning by location, camera IDs will be given following the positional order in clockwise direction, starting from the -X and -Z quadrant in respect to the origin.

### Status Rings

Controls the color of the [RGB Status Indicator Ring LEDs](../../hardware/camera-status-indicators.md) (Prime Series cameras only). Options include distinct indications for Live, Recording, Playback, Selection and Scene camera statuses, and you can choose the color for the corresponding camera status.

#### **Live**

(Default: Blue) Sets the indicator ring color for cameras in Live mode.

#### **Recording**

(Default: Green) Sets the indicator ring color for cameras when recording a capture.

#### **Playback**

(Default: Black) Sets the indicator ring color for cameras when Motive is in playback mode.

#### **Selection**

(Default: Yellow) Sets the indicator ring color for cameras that are selected in Motive.

#### **Video Mode**

(Default: Orange) Sets the indicator ring color for cameras that are set as the reference camera in Motive.

#### **Hibernation Visual**

(Default: Enabled) Controls whether the hibernation light turns on for the cameras when Motive is closed.

### Aim Assist

#### **Switch to Video when Aiming**

Configures the Aim Assist button. Sets whether the button will switch the camera to MJPEG mode and back to the default camera group record mode. Valid options are: True (default) and False.

#### **Aiming Crosshairs**

(Default: Grayscale Only) Sets whether the camera button will display the aiming crosshairs on the the camera. Options: None, Grayscale Only, All Modes.

#### **Aiming Button LED**

Enables or disables LED illumination on the Aim Assist button behind Prime Series cameras.

## Advanced Settings

#### **Device Profile**

Sets the default device profile, XML format, to load onto Motive. The device profile determines and configures the settings for peripheral devices such as force plates, NI-DAQ, or navigation controllers.

#### **Glove Server Address**

Enter IP address of glove. Leave blank to use Local Host IP.

#### Log File Name

Shows which log file is loaded into Motive and displayed in the log pane. There is also a folder icon in order to change or add a log file.

### Calibration

#### **Bumped Camera**

Enable or disable continuous calibration for bumped cameras. When enabled, Motive will continuously monitor the calibration and update it as necessary. When this is set to true, calibration updates more invasively to accommodate for camera position/orientation changes. In general, if camera is significantly moved or displaced, it's suggested to calibrate the system again. For more information, refer to the [Continuous Calibration](../../motive/calibration/continuous-calibration.md) page.

#### **Restrict Camera Movement**

Restrict camera translation during continuous calibration.

#### **Restore Calibration on Startup**

Automatically loads the previous, or last saved, calibration setting when starting Motive.

#### **Auto-Mask Duration**

The time duration, in seconds, that the camera system will auto-detect the existing extraneous reflections in order to apply masks during [Calibration](../../motive/calibration/) process.

#### **Suggested Samples**

Number of samples suggested for calibration. Depending on this setting, the sample count feedback will be colored differently during the [Calibration](../../motive/calibration/) process.

#### **Calibration Visual**

During the calibration wanding process, informative visuals are drawn over the camera view to show successfully collected wand samples and also to mark any extraneous reflections that appear. This is enabled by default. Disabling this will hide those calibration visuals.

#### **Editable in 3D View**

When enabled, you can edit the camera calibration position with the 3D Gizmo tool.

#### **Correction Tool Max Translation**

Max distance cameras are translated by the position correction tool in mm.

### Networking

#### **LLDP (PoE+) Detection**

Enables detection of PoE+ switches by High Power cameras (Prime 17W, PrimeX 22, Prime 41, and PrimeX41). LLDP allows the cameras to communicate directly with the switch and determine power availability to increase output to the IR LED rings. When using Ethernet switches that are not PoE+ Enabled or switches that are not LLDP enabled, cameras will not go into the high power mode even with this setting enabled.
