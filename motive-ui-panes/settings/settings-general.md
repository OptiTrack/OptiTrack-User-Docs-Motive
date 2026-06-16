---
description: Motive's General Settings defined.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive-ui-panes/settings/settings-general
---

# Settings: General

Use the Application Settings panel to customize Motive and set default values. This page will cover the items available on the General tab. Properties are Standard unless noted otherwise.&#x20;

Please see the following pages for descriptions of the settings on other tabs:

* [Settings: Assets](settings-assets.md)
* [Settings: Live Pipeline](settings-live-pipeline.md)
* [Settings: Streaming](settings-streaming.md)
* [Settings: Views](settings-views.md)
* [Settings: Mouse and Keyboard](settings-mouse-and-keyboard.md)
* [Settings: Audio](settings-audio.md)

Application Settings can be accessed from the [View menu](../toolbar-command-bar.md#view) or by clicking the <img src="../../.gitbook/assets/Settings button (9).png" alt="" data-size="line"> icon on the main toolbar.&#x20;

<img src="../../.gitbook/assets/Settings - General No Advanced.png" alt="Standard Settings on the General Tab of the Settings Panel." width="563">

{% hint style="info" %}
**Advanced Settings**

The Settings panel contains advanced settings that are hidden by default. To access these settings, click the <img src="../../.gitbook/assets/Motive Context Menu (25).png" alt="" data-size="line"> button in the top right corner.&#x20;

Use the _Edit Advanced_ option to customize which settings are in the _Advanced Settings_ category and which appear in the standard view, to show only the settings that are needed specifically for your capture application.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/Settings - Show or Edit advanced (1).png" alt=""><figcaption><p>Show or Edit Advanced Settings.</p></figcaption></figure>

{% hint style="info" %}
To restore all settings to their default values, select _Reset Settings_ from the Edit menu.
{% endhint %}

## General Settings

The following items are available in the top section of the General section. Settings are Standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/Settings - General Tab General advanced.png" alt="" width="325"><figcaption><p>General Settings - Standard and Advanced.</p></figcaption></figure>

#### **Take Suffix**

Set the separator (\_) and string format specifiers (%03d) for the suffix added after existing file names.

#### **Auto Archive Takes**

Enable auto-archiving of _Takes_ when [trimming _Takes_](../../motive/data-editing.md#trimming-captured-takes).

#### **Device Profile&#x20;**_**(Advanced Setting)**_

Set the default device profile, in XML format, to load into Motive. The device profile determines and configures the settings for peripheral devices such as force plates, NI-DAQ, or navigation controllers.

#### **Persistent Data Folders**

When enabled, all of the session folders loaded in the [Data pane](../data-pane.md) when exiting will be available again when launching Motive the next time.

#### **Glove Server Address&#x20;**_**(Advanced Setting)**_

Enter the IP address of the glove server, if one is used. Leave blank to use the Local Host IP.

#### Log Filename _(Advanced Setting)_

Click the folder icon to the right of the field to select a text file to write the Motive event log to. This allows you to maintain a continuous log that persists between sessions, which can be helpful for troubleshooting.&#x20;

### Camera Displays

The following items are available in the Camera Displays section. Settings are Standard unless noted otherwise.&#x20;

<figure><img src="../../.gitbook/assets/Settings General Tab - Camera Advanced.png" alt="" width="410"><figcaption><p>Camera Displays Settings - Standard and Advanced.</p></figcaption></figure>

#### **Numeric LEDs&#x20;**_**(Advanced Setting)**_

Display the assigned camera number on the front of each camera.

#### **Camera ID**

Set how Camera IDs are assigned for each camera in a setup. Available options are:

* **By Location:**  Follows the positional order in a clockwise direction, starting from the -X and -Z quadrant with respect to the origin.
* **By Serial Number:**  Numbers the cameras in numerical order by serial number.
* **Custom:** Opens the _Number_ property field for editing in the _Camera Properties_ pane.

<figure><img src="../../.gitbook/assets/Properties - Camera Custom Number.png" alt="" width="309"><figcaption><p>Camera Properties with Custom Camera Number.</p></figcaption></figure>

### Status Rings

Set the color of the [RGB Status Indicator Ring LEDs](../../hardware/camera-status-indicators.md) (Prime Series cameras only) to indicate various camera statuses in Motive.

<figure><img src="../../.gitbook/assets/Settings - Status Rings.png" alt="" width="340"><figcaption><p>Status Ring settings - Standard and Advanced. </p></figcaption></figure>

**Live**

(Default: Blue) Camera is in Live mode.

#### **Recording**

(Default: Green) Camera is recording a capture.

#### **Playback**

(Default: Black) Camera is idle while Motive is in playback mode.

#### **Selection**

(Default: Yellow) Camera is selected.

#### **Video Mode**

(Default: Orange) Camera is in video (reference) mode.

#### **Hibernation Visual**

(Default: Enabled) Enable the hibernation light for all cameras when Motive is closed.

#### Calibration Camera Visuals _(Advanced Setting)_

(Default:  Enabled) Display visuals of wanding coverage in the Camera Viewport during calibration.&#x20;

#### Disable All Lights

(Default:  Off) Turn off all numeric LEDs and ring lights on all cameras in the system.

### Aim Assist

All of the Aim Assist settings are standard settings.

<figure><img src="../../.gitbook/assets/Settings - General Aim Asst.png" alt=""><figcaption><p>Aim Assist Settings. </p></figcaption></figure>

#### **Switch to Video when Aiming**

(Default:  On) Set the Aim Assist button on the back of the camera to toggle the camera between MJPEG mode and back to the default camera group record mode.&#x20;

#### **Aiming Crosshairs**

(Default: Grayscale Only) Display aiming crosshairs on the the camera in the Camera Viewport. Options are None, Grayscale Only, All Modes.

#### **Aiming Button LED**

(Default:  On) Enable the LED light on the Aim Assist button on the back of the Prime Series cameras.

### Calibration Settings _(Advanced)_

All calibration settings are part of the General tab's Advanced Settings.&#x20;

<figure><img src="../../.gitbook/assets/Settings - General Calibration.png" alt="" width="448"><figcaption><p>Calibration settings.</p></figcaption></figure>

### Calibration

#### **Restore Calibration on Startup**

(Default:  On) Automatically load the previous, or last saved, calibration file when starting Motive.

#### **Auto-Mask Duration**

(Default:  1 s) The duration, in seconds, that the camera system will auto-detect extraneous reflections for masking during [Calibration](../../motive/calibration/) process.

#### **Suggested Samples**

(Default:  1,000) Number of samples suggested for calibration. During the [wanding](../../motive/calibration/#wanding) process, the camera status in the [Calibration pane](../calibration-pane.md) will turn bright green as cameras reach this target.

#### Record Calibration Samples

(Default:  On) Save two _TAKE_ files in the current data folder every time a calibration is performed:  one for the calibration wanding and one for the ground plane. &#x20;

#### **Calibration Visual**

(Default:  On) Display visuals of wanding coverage in the Camera Viewport during calibration.&#x20;

#### **Editable in 3D View**

(Default:  Off) Allows editing of the camera calibration position with the 3D Gizmo tool.

#### **Bumped Camera Correction Mode**

(Default:  Disabled) Select the default mode for Bumped Camera correction. Options are _Disabled, Camera Samples,_ and _Selected Camera._ Please see the page [Continuous Calibration (Info Pane) ](../../motive/calibration/continuous-calibration-pane.md)for more information on these settings and the Bumped Camera tool.&#x20;

#### **Correction Tool Max Translation**

(Default:  100 mm) The maximum distance cameras can be translated by the position correction tool, in mm.

#### Continuous Calibration Max Sampling Period

(Default:  120) The maximum length, in seconds, that samples are collected during continuous calibration.&#x20;

#### Continuous Calibration While Recording

(Default:  Off) Allows Continuous Calibration to continue running while recording is in progress.

### Network _(Advanced)_

The Network setting is part of the General tab's Advanced Settings.&#x20;

<figure><img src="../../.gitbook/assets/Settings - General Networking.png" alt="" width="360"><figcaption><p>Network Settings.</p></figcaption></figure>

#### **LLDP (PoE+) Detection**

(Default:  Override) Enable detection of PoE+ switches by High Power cameras (Prime 17W, PrimeX 22, Prime 41, and PrimeX41). LLDP allows the cameras to communicate directly with the switch and determine power availability to increase output to the IR LED rings.&#x20;

{% hint style="warning" %}
When using Ethernet switches that are not PoE+ enabled or switches that are not LLDP enabled, cameras will not go into high power mode even with this setting on.
{% endhint %}

### Editing

All of the Editing settings are standard settings.

<figure><img src="../../.gitbook/assets/Settings - General Editing (1).png" alt="" width="389"><figcaption><p>Editing Settings.</p></figcaption></figure>

#### Take Auto-Save

(Default:  Always Ask) Set Motive's default behavior when changes are made to a _TAKE_ file.  Options are:&#x20;

* Do Not Auto-Save:  Changes made to _TAKE_ files must be manually saved.
* Auto-Save:  Updates the _TAKE_ file as changes are made.&#x20;
* Always Ask:  Prompts the user to save _TAKE_ files upon exit. &#x20;

