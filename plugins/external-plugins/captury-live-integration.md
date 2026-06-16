---
description: How to use the Captury Live software with an OptiTrack camera system.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/plugins/external-plugins/captury-live-integration
---

# Captury Live Integration

## Overview

The Captury Live software integrates with OptiTrack camera systems to provides real-time markerless tracking for up to three actors. This integration leverages Motive's Duplex and/or MJPEG modes to combine markerless skeleton tracking with optical tracking for rigid bodies and trained markersets.&#x20;

{% hint style="success" %}
Is your Captury Live system already configured and calibrated for Motive? [Click here](../../motive/skeleton-tracking.md) to jump to the Skeleton Tracking section.&#x20;
{% endhint %}

## Requirements

Captury Live integrates with OptiTrack cameras using either Duplex (preferred) or MJPEG mode.&#x20;

### Duplex Mode&#x20;

**Software**

* Duplex mode requires Motive version 3.3 with a _Motive:Body_ or _Motive:Unlimited_ license on the Motive PC. If PrimeX 13 cameras are included in the volume, use version 3.3.3 or later.&#x20;
* Install a version of Captury Live software that supports the Motive integration. We used version 270e in our testing and documentation.&#x20;

**Cameras**

* Duplex mode requires PrimeX, SlimX, or VersaX cameras. Duplex mode does _not_ work with Prime, Slim, or Flex cameras.&#x20;

{% hint style="info" %}
The number of cameras the system can support is a complicated equation involving the graphics card installed, and how many people, props, and cameras are used. In our testing, we saw issues with more than 12 PrimeX 41 cameras and 3 people.
{% endhint %}

**Synchronization**

When Captury and Motive are installed on the same PC, then only one may run at a time. However, no additional synchronization device is required to run either software.&#x20;

When Motive and Captury Live are running on different computers, then an eSync is required on each for cross-system synchronization.&#x20;

* Connect the output from the eSync connected to the Captury computer to an input port on the eSync connected to the Motive computer.&#x20;
* Set the eSync connected to the Captury computer as the master and set the eSync connected to the Motive PC to follow it.&#x20;
* If an eSync2 is not connected on both systems then Captury and Motive will not be able to synchronize their exposures and a light strobing effect will occur, where some frames are synchronized and others are not.&#x20;

**Computer**

* To run Motive with cameras in Duplex mode requires our [standard PC specifications](../../quick-start-guides/quick-start-guide-getting-started.md#host-pc-requirements) for the CPU.
* Captury Live requires the best graphics card available. An NVIDIA 4090 or better is recommended.&#x20;

**Networking and Miscellaneous**

* As with all OptiTrack systems, you need a standalone Ethernet network. Please see our standard requirements for [networking](../../hardware/cabling-and-wiring/general-overview-and-specs.md) for more detail.&#x20;
  * Dual NICs are _not_ required.&#x20;
  * The switch may need to have jumbo packets enabled.&#x20;
* OptiTrack calibration tools, markers for rigid bodies, and other standard OptiTrack accessories are also required.

### MJPEG Mode

OptiTrack cameras can be used with MJPEG mode in Captury Live. This works with all modern cameras, with the exception of the Duo 3 and Trio 3 tracking bars. This includes the Flex, Slim, Prime, PrimeX, SlimX, and VersaX camera lines.

{% hint style="warning" %}
Flex, Slim, and Prime cameras are not the preferred choice even without Duplex mode due to the following performance issues: &#x20;

* Flex cameras will experience issues when a larger number of cameras are in MJPEG mode due to USB data throughput limitations.&#x20;
* Older Prime and Slim cameras downsize the resolution in MJPEG mode.
{% endhint %}

## Calibrate the Volume

To integrate Captury Live with Motive, the system is calibrated in Motive, and the calibration file imported into Captury Live.

* In Motive, complete a full system calibration. Please see the [Calibration page](../../motive/calibration/) for instructions on performing a [full calibration](../../motive/calibration/#starting-a-new-calibration).&#x20;
* Export the calibration results by selecting _Export Camera Calibration_ from the _File_ menu. By default, Motive will save the results as an XML file with an .mcal extension.&#x20;
* Once the file is exported, close Motive. Motive and Captury Live cannot run simultaneously.&#x20;

{% hint style="info" %}
Calibration files can also be exported and imported as .cal files. You can export the same calibration as both an .mcal and a .cal file, and import either type into Captury.
{% endhint %}

## Configure Captury for Motive

Install the Captury Live software and license according to the [manufacturer's instructions](http://doc.captury.com/CapturyLive/index.html).&#x20;

#### Initialize Captury Live

Open the Captury Live application to complete the AI initialization process. The first time the program runs, AI initialization will create the files needed to run the program, some of which need to be configured for use with Motive.&#x20;

While Captury Live is opening, the AI initialization will display in a separate window.&#x20;

<figure><img src="../../.gitbook/assets/Captury - AI Initialization window CROPPED.png" alt="A screenshot of a window displaying code running while Captury Live software is loading."><figcaption></figcaption></figure>

Once the program loads, the AI initialization may continue to run in the background. Check the status by clicking the green AI button in the top right corner of the screen.&#x20;

<figure><img src="../../.gitbook/assets/Captury - AI Initialization status button.png" alt="A screenshot of a set of buttons from the Captury Live software. The buttons are, from left to right: Latency (with value displayed); Iter; and AI. The mouse hovers over the AI button."><figcaption></figcaption></figure>

The GPU and AI Status window will open. This window displays the Detected GPUs and driver version as well as the AI initialization status. Once the AI initialization process is finished, close Captury Live.&#x20;

<figure><img src="../../.gitbook/assets/Captury - AI Initialization status CROPPED.png" alt="A screenshot of the GPU and AI status window from Captury Live. The screen shows a detected NVIDIA GPU and the driver version installed, as well as the status of the AI initialization. "><figcaption></figcaption></figure>

#### Edit the Captury.ini File

The CapturyLive.ini file contains settings to run the Captury Live application. This file must be edited for the OptiTrack cameras to be recognized in Captury Live.&#x20;

* The quickest way to find the .ini file, is to enter %AppData% in the Run command, which will open the AppData folder. The .ini file is in the folder _AppData > Roaming > theCaptury._&#x20;

<figure><img src="../../.gitbook/assets/Captury - setup - search for Ini CROPPED.png" alt="A screenshot of the Windows &#x22;Run&#x22; window, with %appdata% entered in the Run field and the mouse hovering over the OK button."><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Captury - setup - Ini File Location.png" alt="A screenshot of a Windows File Manager window, showing the CapturyLive.ini file inside the folder:  (blanked out) user profile > App?Data > Roaming > theCaptury"><figcaption></figcaption></figure>

* Open the .ini file with Notepad or your preferred text editor.&#x20;
* Search for _Motive_ to find the \[devices] section.
* The properties in this section determine whether devices are enabled in Captury. Set the following properties to true:&#x20;
  * enableOptiTrack=true
  * enableMotive=true
* Set the following properties to false:
  * enableSpinnaker=false
  * enableQualisys=false

<figure><img src="../../.gitbook/assets/Captury - setup - ini edits CROPPED.png" alt="A screenshot of a Notepad window showing the Navigation and Devices sections of the CapturyLive.ini file. The word &#x22;Motive&#x22; is highlighted as a search result. "><figcaption></figcaption></figure>

* Once the properties are updated, save and close the CapturyLive.ini file.&#x20;
* Re-launch Captury Live. Motive will initialize as the application loads:&#x20;

<figure><img src="../../.gitbook/assets/Captury - Motive initializing CROPPED.png" alt="a screenshot of a window that displays when Captury is loading, showing the lines where Motive is initialized and the license loaded. "><figcaption></figcaption></figure>

## Import Calibration into Captury

The next step after Motive is initialized is to import the calibration done in Motive into Captury Live.

* From the File menu, select _Import > Import Calibration..._
* Browse to and select the .mcal file exported earlier.&#x20;

<figure><img src="../../.gitbook/assets/Captury - Import calibration 1 CROPPED.png" alt="A screenshot of the Captury Live File Menu, with the mouse hovering over the Import command, and &#x22;Import Calibration...&#x22; displayed on the callout menu."><figcaption></figcaption></figure>

* Once the calibration file is loaded, the cameras will show in the 3D viewport:

<figure><img src="../../.gitbook/assets/Captury - Calibration import complete BLURRED.png" alt="A screenshot of the Captury Live application with OptiTrack cameras displayed on the left and a fully calibrated volume in the main viewport. "><figcaption></figcaption></figure>

### Captury Panels

From the View menu, select Panels to include additional components in the layout.

<figure><img src="../../.gitbook/assets/Captury - Panel options CROPPED.png" alt="A screenshot of the Captury View menu, with Panels selected, and the Panels callout menu displayed. "><figcaption></figcaption></figure>

### Camera Settings

There are a few properties you can adjust in Captury Live from the Camera Settings panel. Note that these settings apply to all cameras in the volume.

<figure><img src="../../.gitbook/assets/Captury - modify camera settings CROPPED.png" alt="A screenshot of the Captury Live Camera Settings panel."><figcaption></figcaption></figure>

#### LED:&#x20;

This property displays as a percentage, but is actually an on/off setting. A value of zero (0) is _off_, and any value greater than zero is _on_.&#x20;

#### Framerate:

Adjust the camera frame rate directly in Captury. Our tester was able to successfully track with using a framerate of 60 fps, but results may vary.

## Skeleton Tracking

Now that your Captury Live system is configured to work with Motive, you're ready to start tracking! Click the TRACK button in the Captury Live toolbar to get started.

<figure><img src="../../.gitbook/assets/Captury - Track on menu CROPPED.png" alt="A screenshot of the Captury Live menu bar and tool bar, with the mouse hovering over the TRACK button. "><figcaption></figcaption></figure>

When Tracking is turned on, a circle will display in the center of the volume. Have the subject stand in the center of the circle, in a [T-pose](../../motive/skeleton-tracking.md#t-pose).&#x20;

<figure><img src="../../.gitbook/assets/Captury - Volume with tracking pane and cameras CROPPED.png" alt="A screenshot of the Captury Live viewport, showing the cameras in the volume, and the circle in the middle where subjects will stand to begin skeleton tracking. No skeletons are shown. "><figcaption></figcaption></figure>

In the Tracking Pane, click and drag the text _\<drag new skeleton>_ over the subject. &#x20;

<figure><img src="../../.gitbook/assets/Captury - Track pane create new skeleton.png" alt="A screenshot of the Captury Live Tracking Pane, with the mouse hovering over the &#x22;Drag to create new skeleton&#x22; button."><figcaption></figcaption></figure>

The subject will appear as a thick red point cloud in the viewport.

<figure><img src="../../.gitbook/assets/Captury - Skeleton point cloud CROPPED.png" alt="A screenshot from Captury Live, showing the subject in the volume as a point cloud and a skeleton behind them."><figcaption></figcaption></figure>

The Viewport will update to show the tracked skeleton rather than the point cloud.&#x20;

<figure><img src="../../.gitbook/assets/Captury - Skeleton in shot CROPPED.png" alt="A screenshot of the Captury Live viewport, showing a single tracked skeleton with one hand on its hip and the other giving a thumbs up."><figcaption></figcaption></figure>

## Rigid Body Tracking

In addition to markerless skeleton tracking, Captury Live can track markered rigid bodies.&#x20;

* Place the rigid body in the circle in the center of the Captury Live volume. &#x20;
* Select the rigid body's markers. &#x20;
* Right-click in the list of tracked assets and select _Init Marker Prop_ from the menu.

<figure><img src="../../.gitbook/assets/Captury - Rigid Body Tracking.png" alt=""><figcaption></figcaption></figure>

## Shot Management

In Captury, you must create the folder and name the shot in the Shot Management pane before you can begin recording.&#x20;

<figure><img src="../../.gitbook/assets/Captury - create a shot SHOT MGMT CROPPED.png" alt="A screenshot of the Captury Live Shot Management pane, with a newly created shot folder highlighted. "><figcaption></figcaption></figure>

### Record

Once you are ready to begin, click the Record button in the bottom right corner of the Shot Management Pane. Click the button again to stop recording when done.

<figure><img src="../../.gitbook/assets/Captury - RECORD BUTTON.png" alt="A screenshot of the Record button from the Captury Live Shot Management panel."><figcaption></figcaption></figure>

The recorded files will be large, with even a short recording producing gigabytes of data. While it's not possible to fully quantify this, since you can change the compression rate and the number of skeletons, our tests yielded the following results:&#x20;

* Eight PrimeX 22 cameras recording one skeleton for one minute was 2.1 GB of data.&#x20;
* Twelve PrimeX 41 cameras recording one skeleton for one minute resulted in 3.7 GB of data.&#x20;

### Export

Captury Live creates a number of files during the recording process. Right-click on the shot to see all the export options.&#x20;

<figure><img src="../../.gitbook/assets/Captury - export options CROPPED.png" alt="A screenshot of the Captury Live Shot Management context menu, with the Export call-out menu shown. "><figcaption></figcaption></figure>

{% hint style="info" %}
The quickest way to access the shot data is to click _Show in File Manager._ This opens the folder where the video and CSV files created during the shot are saved. &#x20;
{% endhint %}

### Reprocessing

Data recorded through Captury Live can be streamed to another application, such as Unreal Engine or Unity, or the data can be reprocessed in Captury Live. This data cannot be loaded into Motive.&#x20;

Use the Retarget panel to complete reprocessing of the shot in Captury Live. For more information on using the Captury Live software, please visit the [Captury Live documentation site](http://doc.captury.com/CapturyLive/index.html).&#x20;

## Troubleshooting

<details>

<summary>Warning Message: Another instance of the software is already running</summary>

Only one application can have control of the OptiTrack cameras at any time. If you open Captury Live while Motive is open, the warning "Another instance of the software is already running" will display.

Close both Captury Live and Motive. Once both are closed, open only the application you need for the current task.&#x20;

</details>

<details>

<summary>Cameras connect in Motive but not in Captury Live</summary>

If the cameras appear and work in Motive but not in Captury Live, check the [CapturyLive.ini file](https://app.gitbook.com/o/6K2GcxpSS9y4e9SRLTrx/s/M6DLKAZnkJZyY3rN2hqt/plugins/external-plugins/edit-the-captury.ini-file) to ensure the settings are correct.If the settings are correct, confirm that the "Streaming Network" appears in the Captury network settings and the status is UP.

<figure><img src="../../.gitbook/assets/Captury - Network settings.png" alt="Screenshot of the Captury network settings window.  "><figcaption></figcaption></figure>

</details>

<details>

<summary>Calibration offset from reference view</summary>

A couple of customers have reported calibrations that are offset from the reference view. If this occurs:&#x20;

* In Motive, export the calibration file as both an .mcal and a .cal file.&#x20;
* Ensure the contrast/brightness are set correctly (0.5ms and 50Hz, respectively).
* Import the .mcal file first, then import the .cal file.&#x20;
* The positioning of the markers should now be correct. &#x20;

</details>

<details>

<summary>Other issues</summary>

Check the [GPU and AI Status pane](captury-live-integration.md#initialize-captury-live) for any of the following issues:&#x20;

1. The graphics card does not meet the [minimum specifications](captury-live-integration.md#requirements) for Captury Live.
2. The latest NVIDIA drivers are not installed.
3. AI local optimization has not happened or is not finished.&#x20;

</details>
