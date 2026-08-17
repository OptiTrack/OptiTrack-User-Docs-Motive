---
description: Motive's changelog history.
---

# Changelogs



<details>

<summary>Motive 3.5</summary>

### Motive 3.5.0 Beta 1

#### **Full Feature List** <a href="#text-full-feature-list-0" id="text-full-feature-list-0"></a>

* [**ActiveIO**](../activeio/) is OptiTrack’s next-generation active tracking platform. ActiveIO devices combine uniquely identifiable active markers with bidirectional communication, automatic firmware updates, onboard IMU data (Inertial Measurement Unit), GPIO support (General Purpose Input/Output), persistent device settings, and real-time device status information. For large-scale VR, simulation, ICVFX (In-Camera Visual Effects), stage tracking, and entertainment environments, ActiveIO makes active tracking easier to deploy, monitor, and manage.
  * **Uniquely Blinking (IO) Markers** - ActiveIO blinks the markers on/off (IO) in binary patterns to uniquely identify individual markers, even in environments with many active devices or IR light sources.
  * **Input and Output (IO) of Data** - Bidirectional communication from the tags allows them to send status and telemetry data back to Motive, including battery level, wireless signal information, and other device metrics. Motive can also send information back to the device, including selection state and configuration updates.
  * **Automatic Firmware Updates** - Motive can now manage firmware updates for ActiveIO devices automatically, helping users deploy new features, bug fixes, and device improvements more easily through Motive software updates.
  * **IMU Data on Every Device** - Every ActiveIO device includes onboard IMU capability for sensor fusion workflows. IMU data can be enabled or disabled depending on the needs of the application and the configuration/scale of the system.
  * **Quality of Service** - The tags now have the ability to send IMU data multiple times per frame while varying the radio channel. This means in environments with heavy wireless traffic, Faraday cages, and other RF interference, there is a tool to improve the connection quality of individual tags.
  * **Compatibility with Active Classic Devices** - ActiveIO devices use the same Pattern Group scheme for choosing marker IDs, enabling older Active Classic devices and newer ActiveIO devices to be used at the same time. Users should take care when configuring mixed systems, as older Active devices might not reliably report their Pattern Group.
  * **Claim, Advertise, and Release** - ActiveIO devices initialize in an advertising state, which means that any instance of Motive (or the Camera SDK) can see the device and claim it. When a device is claimed, that system is the only one that can use the device. Releasing the device puts it back into an advertising state so that a different instance of Motive can claim it. This workflow allows for ActiveIO devices to be moved between systems or locked to a particular system easily. Triple-clicking the device button releases the tag and returns it to advertising mode.
  * **Persistent Device Properties** - Configurations for claimed ActiveIO devices persist between Motive sessions, reducing repeated setup work and helping maintain consistent behavior across projects.
  * **RGB Status LEDs** - ActiveIO devices include three RGB status LEDs that use different colors to communicate device state, including selection, battery level, connection status, and other device information.
  * **Synchronization when Disconnected** - In the case where an ActiveIO device loses connection to the BaseStation, the LEDs remain synchronized with the camera system for several minutes before becoming unsynchronized from the camera frames.
  * **General Purpose Input/Output (IO)** - The GPIO pins on the Tag-8 can transmit back the data going into their ports. This enables things such as binary button presses or analog sensors to communicate data back to Motive. That data can be graphed, recorded, exported, and streamed out of the software.
* **Prime**<sup>**x**</sup>**&#x20;260 Camera Family Support** - Motive 3.5 adds support for [Prime<sup>x</sup> 260](../hardware/cameras/ethernet-cameras/primex-260.md), Prime<sup>x</sup> 260W, and Slim<sup>x</sup> 260 cameras. With 26 MP sensors, the 260 family is designed for premium tracking systems that require exceptional resolution, accuracy, and large-volume performance.
* **Slim**<sup>**x**</sup>**&#x20;22 Support** - Adds support for [Slim<sup>x</sup> 22](../hardware/cameras/ethernet-cameras/slimx-22.md), a compact high-speed camera designed for active tracking workflows. Slim<sup>x</sup> 22 extends the Slim<sup>x</sup> family with an active-only option for applications that prioritize speed, scale, and efficient deployment.
* **Deadband Filter** - The new rigid body deadband filter detects when rigid body motion falls below a defined threshold and holds the rigid body static. This is especially useful for ICVFX, broadcast, camera tracking, and other workflows where small fluctuations can become visible when projected over long distances.
* **New Streaming Types** - To support ActiveIO, we have added the ability to stream…
  * **Raw IMU data (inertial measurement unit)** - This unlocks workflows where sensor fusion can be done on the client side.
  * **GPIO data (General Purpose Input/Output)** - This unlocks workflows where button inputs are activated on ActiveIO devices, then sent to game engines or client applications where actions in the game can occur.
  * **Anchor Markers** - This unlocks the ability to better remotely monitor system health using a NatNet Client. A new example client for how to do this will be included with NatNet 4.5.
  * Added the ability to turn off streaming data for individual ActiveIO tag devices to optimize the data stream over NatNet.
  * Added the ability to turn on/off IMU and GPIO data entirely from streaming.
* **USD Export** - Export animation files to [OpenUSD](../motive/data-export/data-export-usd.md) for importing into game engines (for example, [Unreal Engine](../plugins/optitrack-unreal-engine-plugin/)) and other workflows such as the NVIDIA Omniverse.
* **STL Attached Geometries** - Users can now attach STL geometry files to rigid bodies for improved visualization in engineering workflows.
* **Passive or Active Only Modes** - Added back the ability to have Passive Only and Active Only markers.
* **Unlabeled Markers Visibility Toggle** - Added the ability to toggle the visibility of unlabeled markers in the 3D view.
* **Delete All Unlabeled Markers** - Added the ability to delete all unlabeled markers using a single button click in the Edit Tools pane.
* **Improved Color Decoding** - Rewrote the color video decoder module to use GPU when available. This allows for systems with more color cameras in the mix with as many as 18 [Prime Color](../hardware/cameras/ethernet-cameras/prime-color.md) cameras running at 250 Hz being an upper limit validated in the office.
* Added a hotkey option for making the working range match the selection range.
* Added the ability to not scroll the Graphs pane with Alt+Left click.
* Added a dropdown to the 3D Viewer for follow selected with rotation.
* Added an option to create skeletons with straight spines.
* Improved active marker tracking with dense or symmetric marker placements.
* Added the ability to use pixel inspector while in MJPEG.
* Added functionality to the skeleton creation process to auto detect existence of inside elbow/wrist/knee/ankle calibration markers for Core/Baseline skeletons and, if they exist, create the skeleton with them.
* Minor improvements to Motive taking a long time to open.
* Updated internally to Visual Studio 2022, which can affect some customer samples.
* Updated the link for the OptiTrack Forums.
* Added a hotkey to enable Local Coordinates.
* **Calibration**
  * **MCAL Human Readable Camera Names** - Added a subfield for the human readable camera name in (.mcal) calibration files.
  * **OpenCV Calibration Representation** - Added a new intrinsic representation in MCAL files that makes working with OpenCV easier.
* **NMotive / Motive Batch Processor**
  * Made the C3D export settings match Motive for NMotive / the Motive Batch Processor including Calculated Marker Positions.
  * Made the CSV export settings match Motive for NMotive / the Motive Batch Processor including Axis Convention settings and WriteQualityStats.
  * Added the ability to access the start time in milliseconds in an NMotive example.
  * Added the ability to export skeletons with Z-Up for the FBX exporter.

#### **Fixes** <a href="#text-fixes-2" id="text-fixes-2"></a>

* **Motive API Body License Fix** - Fix for a bug where the Motive API did not work with Body Licenses.
* Fix for external device data being dropped when 3D frame drops occur at higher frame rates such as 500 Hz.
* Fix for Continuous Mode for Flex cameras not working correctly and still strobing the IR ring light.
* Fix for a bug when doing a Range of Motion with skeletons that contain active finger markers.
* Fix for slow file open and recording start in some situations.
* Fix for comments in the MotiveAPI around the CurrentCalibrationQuality(…) function.
* Fix for the Motive API print statements around CurrentCalibrationQuality(…) not being clear.
* Fix for an issue where the VRPN streaming option stays toggled on reset but does not restart the connection.
* Fix for incorrect logic for toggling mode in the Devices Pane for the Flex 13, Flex 3, and Slim3U devices.
* Fix for not fixed width of the Video column in the Data Pane.
* Fix for not intuitive stepper amount for the Bone Translation Offset property.
* Fix for the add marker sticks in a line feature not being additive.
* Fix for an issue where setting the blue value for the LED status light for a Slim camera to 255 would set the value to 0 instead.
* Fix for inconsistent use of the term “Video Mode.”
* Fix for a small issue with overlapping text in the Cameras View with camera info enabled.
* Fix for a crash when running Motive on Windows Server.
* Fix for Motive API “markers” sample application giving the wrong Camera Count and hangs waiting for nonexistent cameras in some circumstances.
* Fix for a hang when solving skeleton under certain circumstances.
* Fix for an intermittent crash when fetching Unicast data subscription through NatNet.
* Fix when using custom constraints for skeleton creation. This causes the skeleton not to create for certain skeletons.
* Fix for a bug where the timeline was set to 1000 when revering a take.
* Fix for enable Min Ray Lengths appearing in the wrong place in the Settings Window.
* Fix for intermittent hang with the Range of Motion process.

#### **Known Issues** <a href="#text-known-issues-4" id="text-known-issues-4"></a>

* **Gradual Memory Leak:** There is a gradual memory leak when using some newer NVIDIA drivers. If this issue occurs, please roll back to NVIDIA drivers 32.0.15.5639, 23rd Oct 2024.
* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 may need to be loaded into Motive 2.0 before loading them into Motive 3.0.

</details>

<details>

<summary>Motive 3.4</summary>

### Motive 3.4.1 Final

#### **Fixes** <a href="#text-fixes-0" id="text-fixes-0"></a>

* Fix for external device data being dropped when 3D frame drops occur at higher frame rates such as 500 Hz.
* Fix for slow start record and file open in Motive.
* Fix for VRPN Enable stays toggled but does not reset connection.
* Updated the EULA (End User License Agreement) to Final.

#### Known Issues <a href="#text-known-issues-2" id="text-known-issues-2"></a>

* **Gradual Memory Leak:** There is a gradual memory leak when using some newer NVIDIA drivers. If this issue occurs, then please roll back to NVIDIA drivers 32.0.15.5639, 23rd Oct 2024.
* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 may need to be loaded into Motive 2.0 before loading them into Motive 3.0+

### Motive 3.4.0 Final

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Added a Sensor Fusion Param to Rigid Body Streaming** - The param value in NatNet can be used to inject data to the stream without modifying the bit stream, so no NatNet updates are required for this feature.
* **Export Relative to Rigid Body** - Added the ability to export all the data relative to a particular rigid body with the CSV exporter.
* **Unreal FBX Exporter** - Updated the FBX Exporter to include -Y forward bone rotations for Unreal Engine.
* **Constraint Weights** - Include the constraint weight values to skeleton xml files, so that templates can be defined using different weight presets.
* Added logic for 940nm ring lights for Versa products.
* Added Shift+O as a hotkey for Precision Mode.
* Updated the third party licenses distributed with Motive.
* Added more intuitive user interface features for default skeleton and rigid body names set through the Settings Window and displayed in the Builder Pane.
* Allow back waist marker to be placed at user preferred position for Core 50 skeleton.
* **Range of Motion**
  * Show the elapsed seconds during the Range of Motion calculation process.
  * More smoothly progress through the Range of Motion process without user interaction.
  * Better handle running the Range of Motion process on skeletons with finger tracking.
  * Moved the special poses in the Range of Motion to the top of the list.
  * Made updates to text during Range of Motion calculation stage.
  * Made updates to text better describing poses in the help popover.
  * Allow users to define the scaling of marker offsets and pose detection distances to better fine tune the Range of Motion process.

#### **Fixes** <a href="#text-fixes-2" id="text-fixes-2"></a>

* **Audio Playback** - Fix for audio playback sounding incorrect when the Live frame rate doesn’t match the playback rate of the take file.
* **Prime**<sup>**x**</sup>**&#x20;13 Circularity** - Fix for Prime<sup>x</sup> 13, 13W, and Slim<sup>x</sup> 13 cameras always reporting a circularity of 1.0 for objects.
* **Force Plate Origin C3D** - Fix for the force plate origin location being incorrect in the C3D exporter. This caused calculations including the center of pressure to be slightly incorrect in some force plates.
* **Graph Visuals** - Fix for the visuals tab in the Graphs Pane not setting values correctly.
* Fix for display board numbers on the Slim<sup>x</sup> 13.
* Fix for the X120 cameras being secretly set to MJPEG mode on startup in some scenarios.
* Fix for Motive:Tracker license not allowing creation of a markerset from selection.
* Fix for the 3D view in the Builder Pane being hidden after asset creation occasionally.
* Fix for resetting constraint values in the Constraints Pane setting incorrect values.
* Fix for the pattern based gap fill giving inconsistent results.
* Fix for history trajectory not continuing when the rigid body is occluded then comes back.
* Fix for turning the LEDs of all cameras off/on not working for every camera sometimes.
* **Range of Motion**
  * Fix for not showing the correct progress bars for skeletons that don’t contain certain bones or ability to do certain poses during the Range of Motion process.
  * Fix for twisted head position when running on some Range of Motion data sets.
  * Fix for an issue where feeding only a small number of high-error samples can make the result of a Range of Motion look worse than it is.
  * Fix for pelvis translation offset becoming 0 after a Range of Motion.
  * Fix for issue collecting samples for the Range of Motion process when in Edit 2D mode.
  * Fix for issues calculating when running a Range of Motion while in Edit 2D mode.
  * Fix for the Modify > Refine option disappearing when switching tabs of the Builder Pane.
  * Fix for bugs in take naming when performing a Range of Motion.
  * Fix for occasional freeze in the Range of Motion calculation process.
  * Fix for recording still starting when canceling a Range of Motion while a record delay is set.
  * Fix for text clipping in the Range of Motion description text.
* **Character Handling**
  * Fix for a crash when recording with Japanese asset names.
  * Fix for Save As… outputting corrupted asset names in take files with asset using non-English characters.
  * Fix for allowing forbidden characters (including /\\;.) in asset names.
  * Fix for not being able to type colon “:” in settings for gloves.

#### Known Issues <a href="#text-known-issues-4" id="text-known-issues-4"></a>

* **Gradual Memory Leak:** There is a gradual memory leak when using some newer NVIDIA drivers. If this issue occurs, then please roll back to NVIDIA drivers 32.0.15.5639, 23rd Oct 2024.
* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 may need to be loaded into Motive 2.0 before loading them into Motive 3.0+.

### Motive 3.4.0 Beta 1

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Range of Motion**
  * **Range of Motion (Bone Refinement) -** Motive now lets you refine joint placement and scale bones on the skeleton so they better match a real performer’s movement. During setup, the actor completes a guided Range of Motion routine that moves each tracked bone to compute more accurate joint locations. These joint locations can be reused across multiple sessions by updating the constraint locations (not bone lengths) using the associated tool in Motive.
  * **Key Pose Detection -** Specific poses are used to help better define certain joints such as elbows, wrists, knees, shoulder, neck, spine, and other bones. This patent pending technique better detects real-world joint locations.
  * **Fully Automated Workflow** - The range of motion process progresses automatically between steps to make the process simple for a single person to perform.
  * **Backup Take Recorded -** Unless otherwise specified, a take with the name of the subject is recorded each time a range of motion is performed. This allows you to easily reprocess the skeleton if needed.
  * **Extra Settings -** Lots of small extra settings have been included to let you customize the experience or debug issues if needed. For instance, you may refine only the constraint locations if bone lengths need to remain fixed.
  * **ROM Quality Properties -** The skeleton asset stores the last range of motion quality as a property for reference.
  * **ROM Hotkey -** Added a hotkey for creating a skeleton and starting the range of motion process at the same time.
  * **Instructions -** There is a small pop-up help window with icons to demonstrate how to use the new range of motion feature as well as an instructional video online.
  * **ROM 3D Visuals -** Live skeleton updates in 3D show the range of motion progress and quality.
  * Added a Refinement tab to the Settings Window > Assets tab for all related properties.
  * Added an option to save the original skeleton when doing range of motion for comparison purposes.
* **Builder**
  * **Improved Marker Placement Guide -** The builder pane has a new green marker visual as well as joint axis lines to help more easily define where markers should be placed.
  * Renamed the “5 Segment Spine (five spine, two neck bone)” model to just the “7 Spine Segment” model.
  * Made the 7 spine segment model the default bone structure.
* **In-Camera VFX Improvements**
  * **Max Ray Length -** The Max Ray Length solver setting is back, which can exclude long rays in big spaces to reduce jitter and improve tracking stability.
  * Max Drift Correction has been updated from an advanced property to a standard setting for easier sensor-fusion optimization.
  * Added an IMU sensor fusion pause property for rigid bodies.
* **NMotive / Motive Batch Processor**
  * Added an example FBX Binary script that allows you to specify the location of the output file.
  * Added a line promoting the Motive Batch Processor to the Quick Start Window.
  * Added exporting FBX and C3D options to the Entertainment Script example.
* **Licensing**
  * **Licensing restricts only Trained Markersets** - Motive:Tracker licenses now support standard (nontrained) markersets.
  * Improved the License Tool by removing extra spaces in the text inputs.
  * Updated the OptiTrack logo on the License Tool.
* **Continuous Calibration Pane -** Split the Continuous Calibration section out of the Info Pane into its own pane.
* Renamed the Active “Group” property to “Pattern.”
* Added the ability to display the distance between any selected 3D objects instead of just for markers.
* Added a user definable Notes property to hardware devices.
* Added a settings to adjust reference video brightness.
* Added an option to not stream rigid body data via VRPN when it is not tracked.
* Added a new property to turn off sending camera descriptions for NatNet. This allows you to stream more skeleton assets to certain programs like MotionBuilder.
* Motive now adds the take name as a suffix to FBX exports when Individual Assets is enabled.
* Added a warning message for Versa<sup>x</sup> cameras when their ring light and body have mismatched light wavelengths.
* Removed the XML option in the File > Open menu.
* Added the ability for 940 nm Versa<sup>x</sup> cameras to identify correctly in the software.
* Added better linting for forbidden characters in the Assets pane.
* Allow a max wand length of 3 meters for calibration
* Updated wrist marker locations for a few skeleton models.

#### **Fixes** <a href="#text-fixes-2" id="text-fixes-2"></a>

* **Motive Batch Processor Entertainment Script -** Fix for a crash when running the entertainment script on a long list of takes.
* **VRPN Not Streaming after Restart -** Fixed an issue where VRPN was not able to connect after a Motive restart.
* **Audio at High Frame Rates Fix -** Fix for robotic sounding audio with recording over about 100 Hz on take playback.
* Fix for a bug here turning all LEDs on and off sometimes leaves a handful of cameras in the previous state.
* Fix for some skeleton tracking issues by updating the degrees of freedom values.
* Fix for a crash when importing a Motive profile with a Wired AnchorPuck or Wired CinePuck connected.
* Fix for the Device Pane camera mode icon failing to switch properly when using Motive:Tracker licenses.
* Fix for an export issue where files would not export when there was both a camera in Duplex Mode and one in color video mode at the same time.
* Fix for swapped toe labels in the Biomech 57 markerset.
* Fix for small user interface glitch when changing the Min Pixel Threshold in Live Pipeline settings window.
* Fix for occasional incorrect thumb creation with skeletons that contain fingertip markers.
* Fix for not being able to create a bone with a single constraint for a markerset in the Builder pane.
* Fix for a refresh issue with the 3D avatar view in the Builder pane.
* Fix for Continuous Calibration sampling even when there is no base calibration loaded.
* Fixes and improvements for several minor areas in the Motive API.
* Fix for missing arrow in the calibration pop-up help menus.
* Fix for occasional finger marker swaps with the Baseline 49 and Core 54 skeletons on initial creation.
* Fix for Flex 13 cameras showing precision mode output when set to grayscale or MJPEG video modes.
* Fix for some issues when running with large numbers of cameras.
* Fix for issue where the Take Name text box moves the cursor involuntarily.

#### **Known Issues** <a href="#text-known-issues-4" id="text-known-issues-4"></a>

* **Gradual Memory Leak:** There is a gradual memory leak when using some newer NVDIA drivers. If this issue occurs, then please roll back to NVIDIA drivers 32.0.15.5639, 23rd Oct 2024.
* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 may need to be loaded into Motive 2.0 before loading them into Motive 3.0.

</details>

<details>

<summary>Motive 3.3</summary>

### Motive 3.3.4 Final

#### Fixes <a href="#text-fixes-0" id="text-fixes-0"></a>

* Fix for a crash when importing a profile while a Wired AnchorPuck or Wired CinePuck is connected.
* Fix for a bug where VRPN is secretly not on after a Motive restart.
* For for a crash in the Motive API relating to tracking bars.

### Motive 3.3.3 Final

#### Features <a href="#text-features-0" id="text-features-0"></a>

* Added support for Duplex mode for the Prime<sup>x</sup> 13, Prime<sup>x</sup> 13W, and Slim<sup>x</sup> 13 cameras.

### Motive 3.3.2 Final

#### Fixes <a href="#text-fixes-0" id="text-fixes-0"></a>

* Fix for Flex cameras not displaying MJPEG and Grayscale data correctly in Live mode.

### Motive 3.3.1 Final

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Increased the Maximum Pixel Threshold upper limit to 18,000.
* Changed the language on the license tool to just say “License Key” due to hardware keys also being available to use in Motive 3.1+.
* Improved the warning message when importing shot lists (.xml or .csv) that have extra unused fields.

#### **Fixes** <a href="#text-fixes-2" id="text-fixes-2"></a>

* **Duplex Mode Export** - Fix for a bug causing Duplex mode video to not export.
* **High Resolution MJPEG Export** - Fix for issue when exporting high quality MJPEG video with the X120 cameras.
* **Tracking Bar Data not Loading** - Fix for Duo / Trio take files recorded with Motive 3.1.4 having data missing in newer versions of Motive.
* **Anchor Puck Frame Rate** - Fix for an issue where the frame rate for AnchorPucks was not being set correctly on system startup.
* Fix for incorrect spine names in steamed skeleton data using the new skeleton spine segments.
* Fix for issue in the MotiveAPI where you can't poll frames in some workflows.
* Fix for crash in the MotiveAPI when a Duo/Trio is connected on launch.
* Remove the notification about Security Keys not being connected with demo licenses.

#### **Known Issues** <a href="#text-known-issues-4" id="text-known-issues-4"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0+.

### Motive 3.3.0 Final

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Duplex Mode** - Duplex Mode adds the ability to capture object mode and MJPEG mode from the same camera at the same time. This allows cameras to be used for both tracking and reference video, unlocking post production markerless workflows.
  * Devices Pane now toggles between Object, MJPEG, and Duplex modes when clicking the mode icon. Added a new icon for Duplex mode in the Devices pane.
  * Enabled changing the Duplex mode colors in Motive and on the ring light.
  * Restricted Duplex mode to only work with Motive:Body and Motive:Body-Unlimited.
  * Added a hotkey for Duplex mode (Y).
* **Kistler SDK Update** - Added the latest Kistler SDK to support their newest force plates in Motive.
* **Bertec SDK Update** - Added the latest Bertec SDK to support tracking 5+ force plates at one time.
* **Spine Segment Options** - Added an option to the Builder pane to use an alternate model with 5 spine bones and 2 neck bones. Defaults to the classic configuration.
* **Better Shot List Management** - Added the ability to import and export both XML and CSV files for managing take names and notes for large shot lists through both the “…” menu and drag-and-drop.
* **Prime**<sup>**x**</sup>**&#x20;120 Full Resolution MJPEG** - Allows for full resolution MJPEG in the Prime<sup>x</sup> 120 cameras. (This is not currently available with Duplex mode.)
* Removed the Security Key Not Found notification when using a demo license.
* Added the ability to send commands over NatNet to both reset the orientation and location of a rigid body.
* Added the ability to download calibration files from tracking bars using the Motive API.
* Added improvements to the Motive API to make it more more powerful to integrate with by adding access to asynchronous camera frames.

#### **Fixes** <a href="#text-fixes-2" id="text-fixes-2"></a>

* **Toe Tracking Improvements** - Fix for toes on skeletons not animating well when they lose all their constraints.
* **FBX Exporter NMotive Options Fix** - Fix for missing FBX exporter options in the Motive Batch Processor / NMotive.
* **HMD Creation License Fix** - Fix for a couple of issues around HMD clip creation where a skeleton was created instead of a rigid body, not allowing them to be used in Motive:Tracker.
* Fix for sensor fusion resetting when the Bone Position History property is changed.
* Fix for occasional crash or failure when streaming VRPN data in Edit mode.
* Fix for crash when undoing skeleton creation.
* Fix for crash when attempting to add constraints to Trained Markersets in Live mode.
* Fix for Motive API samples closing too quickly in some cases.
* Fix for image issues with the Prime<sup>x</sup> 120 cameras at certain gain levels.
* Fix for Prime<sup>x</sup> 120 cameras not maintaining state across power or Motive cycle.
* Fix for rigid body name not appearing in the Calibration ground plane tools when changing selection.
* **Data Pane**
  * Fix for the Name column in the Data Pane getting squished in some modes.
  * Fix for notes clearing in the Data pane in empty takes on record.

#### **Known Issues** <a href="#text-known-issues-4" id="text-known-issues-4"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

</details>

<details>

<summary>Motive 3.2</summary>

### Motive 3.2.0 Final

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Versa**<sup>**x**</sup>**&#x20;Cameras** - Added the Versa<sup>x</sup> camera camera line.
  * This includes the following variants of devices: Versa<sup>x</sup> 22, Versa<sup>x</sup> 22W, Versa<sup>x</sup> 41, Versa<sup>x</sup> 41N, Versa<sup>x</sup> 41W.
  * Versa<sup>x</sup> cameras are modular, water resistance, and have extra mounting options for specialized use cases.
* Reversed the order of the multiplier vs divisor for the eSync to be in a more intuitive order.
* Removed the dropped frames metrics from the Control Deck popover menu. The graphs option for this still exists.
* Renamed the Tracking Bars in the software to not include the “V120” at the beginning.
* Re-implemented internal NatNet fuctions for trained markersets to allow them to work in Unity.
* Updated properties meant to improve issues with frame drops to have the optimal settings by default. This might increase the memory footprint of Motive for some users.
* Updated the ReconstructAutoLabel scripts in the Motive Batch Processor to use the Reconstruct and Auto-Label action by default instead.

#### **Fixes** <a href="#text-fixes-2" id="text-fixes-2"></a>

* **Audio Fixes** - Fix for issue with audio export not working correctly. Fix for dropped frames is newly recorded takes with audio.
* **Streaming On State Persists** - Fixed an issue where the streaming Enabled button said it was on but wasn’t because it was not persisting correctly.
* **Color Video Fixes** - Fix for an issue loading older color camera data. Fix for color camera properties not being recorded correctly.
* **NMotive Processing Slowdown** - Fix for certain take files causing a x3 slowdown when using the reconstruct and auto-label function in the Motive Batch Processor / NMotive.
* Fix for an issue where the OptiHub had too many options on the output type.
* Fix for exporting live pipeline settings and live camera settings not working.
* Fix for creating a new layout and setting to default crashing Motive.
* Fix for issue that broke layouts when making panes visible with custom layouts.
* Fix for a freeze when using VRPN with skeletons.
* Fix for not allowing asset definition to be modified using the 3D gizmo tool on solved data in 2D mode.
* Fix for specific files causing Motive to crash.
* Fix for a crash when streaming 9+ force plates at one time for several minutes.
* Fix for data marshaling issues when streaming 9+ force plates.
* Fix for the active tag debugging table not updating.
* Fix for IMU constraints not persisting correctly.
* Fix for timecode not appearing in some exported C3D files.
* Fix for a crash when cloning a graph and taking some specific steps afterwards.

#### **Known Issues** <a href="#text-known-issues-4" id="text-known-issues-4"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### **Motive 3.2.0 Beta 1**

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Recalibrate Bone Positions** - Added the ability to update bone positions for skeletons without rescaling the bones, which works towards having one skeleton forever for actors. You can still do the original action of updating both marker positions and bone scaling as well.
* **Larger Pixel Sizes for Prime**<sup>**x**</sup>**&#x20;120 Cameras** - Adjusted the Max Pixel Size to accommodate the Prime<sup>x</sup> 120 with objects up to 128 x 128 in size to allow for higher accuracy with close up objects.
* **Edit Mode Masking** - Added the ability to draw masks in Edit mode.
* Added the ability to filter log messages based on severity in the Log Pane.
* Added a PoE++ visual in the Cameras view for the X120 cameras.
* Changed the USB drivers to be mandatory during installation.
* NatNet SDK now supports rotational offset for bones.
* **Active**
  * **Sensor Fusion Bump Correction** - Added advanced IMU sensor fusion controls such as Impulse Correction Angle. These properties help handle edge cases especially around sudden impacts and recoil.
  * **Sensor Fusion Progress indicator** - Added a progress indicator element for IMU and optical alignment to help in the setup process. The visual shows when to keep rotating the device for alignment until 100% of samples are gathered.
  * Added new columns and controls to the devices pane for Active devices.
  * Added an alignment quality indicator to the Info pane under that Active Debugging section.
  * Added a debugging property for tag devices showing the number of currently connected LEDs.
  * Improved the default property view in the Devices pane for active devices.
  * Added the ability to assign Group ID values for some active products.
  * Added the Auto-Group button to automatically assign Group ID values with multiple Active devices.
  * Added a warning when the Group ID is larger than the Active Pattern Depth property.
  * Small improvement to the log message checking that Kistler Force Plates work with DataServer.dll.
* **Exporters**
  * **Human Readable Calibration Files** - Added human readable XML calibration files as (.mcal) files. These can be manually modified or examined. These files also include OpenCV compatible lens intrinsic information for research projects.
  * **Increased Video Exporter File Sizes** - The Maximum File Size for video exporters now has a range of as large as 20 GB for larger video files and machine vision applications.
  * Added the ability to export camera data to CSV files.
  * Added parent/child bone relationships to the CSV exporter.
  * Motive now has the option to export error metrics for markers or assets in the CSV exporter.
  * Added the option to export Markers as Optical Marker Data to the FBX Binary exporter.
  * Added the option to move Marker gaps to the origin of the scene in the FBX Binary exporter.
  * Increased the maximum number of characters per marker to 127 when exporting to C3D.
  * Added a JSON calibration exporter.
  * Added the FILM designation to C3D exports when using 24 Hz timecode.
* **Properties and Settings**
  * Added a Sensor Fusion section to Rigid Body Properties.
  * Flex 3 and Slim 3U camera series now uses microseconds for exposure.
  * Added a Continuous Illumination property for Flex cameras to allow for always on infrared LEDs.
  * Increased the maximum amount of Minimum Rays to Continue to 10.
  * Updated the Default Joint Diameter and Default Joint Length to use meters for scaling.
  * Added properties for setting the minimum marker size and roundness while calibrating the system.
  * Cleaned up the Settings > Views > Graphs options.
  * Changed Deflection Ratio to a non-advanced property.
  * Added Firmware Version and Logic Version as advanced properties.
* **Builder**
  * **HMD Clip Tool XML Files** - Changed the HMD clip tool so that it loads external XML files to allow for custom models.
  * Added an Align to … dropdown with additional options of Marker and Origin.
  * Added the HTC Vive Focus 3 Clip as a supported HMD clip tool option.
  * Added the XR-4 Steam Clip as a supported HMD clip tool option.
* **NMotive / Motive Batch Processor**
  * Added a Last Frame option to the video exporter in NMotive.
  * Added an option to the FBX Binary Exporter to change marker name separator in NMotive.
  * Added the option to the FBX Binary Exporter to export Markers as Optical Marker Data.
  * Added the option to the FBX Binary Exporter to move Marker gaps to the origin of the scene.
* **Motive API**
  * Added the ability to specify the calibration wand length for the Motive API.
  * Added a function to get the wand sample render location to the Motive API.
  * Added the ability to upload calibrations to a tracking bar via the Motive API (only works with certain hardware states).
  * Added improvements to getting the calibration state.
  * Added the ability to turn on eSync 2 output ports manually.
  * Improvements to failure cases around licensing or when no devices are connected.

#### **Fixes** <a href="#text-fixes-2" id="text-fixes-2"></a>

* **Solver Quality Improvements** - Fixed solver quality regressions especially around shoulder rotations and for finger markersets.
* **Improved Dropped Frame Issue** - Mostly resolved an issue with dropped frames with larger amounts of data throughput.
* **VRPN Streaming** - Fixed an issue where VRPN was not streaming data correctly. Additionally addressed an issue with needing to re-toggle VRPN when streaming to any port other than the default 3883.
* Improved software stability over long periods of time.
* Moved the MotiveProfile.motive to the Motive folder in the application ProgramData folder.
* Renamed Wiki ... to Documentation... in the Help dropdown.
* Fixed an issue in the Constraints Pane where the asset shown at the top did not respect the primary selection.
* Fixed an issue with some clipped text in the Builder Pane when running the probe creation tool.
* Fixed an issue where zooming in on cameras pane for Flex13 duo made images disappear and turn gray.
* Fixed an issue where Frame ID was not updating when single stepping in edit mode.
* Fixed an issue where the Prime Color FS camera was not showing in the proper position in older .tak files.
* Fixed an issue where changing the ground plane with a vertical offset did not raise the ground plane off by the amount of the entered number.
* **Active**
  * Fixed an issue creating performance issues when many pucks were plugged in.
  * Fixed an issue where active tags would populate incorrectly on the device list when multiple tags were connected.
  * Fixed an issue where the Active Tag device list property column width now displays the full property names.
  * Fixed an issue where active markers would not reconstruct in older (.tak) files.
  * Fixed an issue caused by a nullptr error when using certain Active device.
  * Fixed an issue where active tag names were being applied incorrectly to constraints.
  * Fixed an issue where rigid body names were not being removed when unpaired with active tags.
  * Fixed an issue causing extra active tags to be created when playing frames in edit mode.
  * Fixed an issue where the “aligned” icon in the Active Tag Table was not properly recognizing the alignment state.
  * Fixed an issue where IMU related menu options would populate without detecting an IMU.
* **Assets**
  * Fixed an issue where solving from Assets Pane would not replace existing solved data.
  * Fixed an issue where Make a Copy for a rigid body would not work with Motive:Body licenses when there were three skeletons or markersets in the scene.
  * Fixed an issue where the Solve() function was not working properly in the Motive Batch Processor.
* **Exporters**
  * Fixed an issue where the UID values for multiple skeletons in the CSV exporter were not unique.
  * Fixed a crash in the CSV exporter with a specific file.
* **Log Pane**
  * Fixed the history in the Log pane to retain log messages.
  * Fixed an issue with the Log Pane where Missing 2D Frame messages would get stuck in Live mode if camera IDs matched between Live and Edit.
* **Properties and Settings**
  * Fixed an issue that caused input validation to reject negative or decimal values.
  * Fixed an issue where the text size was incorrect when zooming into a marker on a camera image.
  * Fixed an issue so that the Visual3D Compatible setting no longer makes labeled marker ID invalid.
  * Fixed an issue where the History section was showing improper values.
  * Fixed an issue where the Min Alignment Count property was set to an incorrect default value.
  * Fixed an issue where the Property pane and columns were not correctly reflecting the display, values, and properties of edit mode.
  * Fixed an issue where properties were displaying incorrectly for older tags.
  * Fixed an issue where a warning was thrown incorrectly that the number of markers had changed when it had not.
  * Fixed an issue where StretchSense gloves would not properly report their properties.
  * Fixed an issue where the color camera section would display for non-color cameras.
  * Fixed an issue where the camera model would show up as “0” in older takes.
  * Fixed alignment issues in the Edit Tools pane.
  * Fixed minor issues in the color controls in the graphs pane.
* **Serial Numbers**
  * Fixed an issue where camera serial numbers were being treated inconsistently.
  * Fixed an issue where the Active Puck had an M prefix instead of an A.
  * Fixed an issue so that serial numbers not beginning with M now behave correctly.
  * Fixed an issue where serial numbers for certain cameras had an incorrect prefix.

#### **Known Issues** <a href="#text-known-issues-4" id="text-known-issues-4"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

</details>

<details>

<summary>Motive 3.1</summary>

### Motive 3.1.4 Final

#### **Fixes** <a href="#text-fixes-0" id="text-fixes-0"></a>

* Fixed an issue with the take.Solve() function in the Motive Batch Processor and NMotive where skeleton bones were not solving.

#### **Known Issues** <a href="#text-known-issues-2" id="text-known-issues-2"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### Motive 3.1.3 Final

#### **Fixes** <a href="#text-fixes-0" id="text-fixes-0"></a>

* Fixed an issue with the Prime<sup>x</sup> 120 and Prime<sup>x</sup> 120W where large numbers of the cameras on the same switch would cause them to drop out.

#### **Known Issues** <a href="#text-known-issues-2" id="text-known-issues-2"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### Motive 3.1.2 Final

#### **Fixes** <a href="#text-fixes-0" id="text-fixes-0"></a>

* Fixed a issue with the eSync 2 firmware version to allow PTP with a Time Machine TM 2500C.
* Fixed a memory leak when streaming Trained Markersets via NatNet.

#### **Known Issues** <a href="#text-known-issues-2" id="text-known-issues-2"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### Motive 3.1.1 Final

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Completed adding support for Precision Time Protocol for the eSync 2.
* Added the MachineID to the About Motive window for demo licenses.
* Added advanced properties for enabling or disabling the degree of freedom limits in a skeleton.
* Added advanced properties to set the maximum and minimum limits for the spine and shoulders to stretch or shrink.

#### **Fixes** <a href="#text-fixes-2" id="text-fixes-2"></a>

* Fix for shoulders popping very noticeable during some motions.
* Fix for hands bending upward or downward when the arms are stretched.
* Fix for hands bending at the wrist when the hands are rotated.
* Fix for spine scaling pop during some motions.
* Fix for feet slide on the floor when rotating knees from left to right.
* Fix for a visual issue with the X120 cameras when running at gain 8.
* Fix for not being able to create a second 6 Rigid Body Skeleton.
* Fix for marker ordering that caused issues with the MotionBuilder Optical Plugin.
* Fix for a bug with NMotive where the AllSkeletons().Active flag was not working.
* Fix for an issue where deleting a number would not work in the Properties pane.
* Fix for an memory leak that would occur quickly with a lot of frame drops.
* Fix for the Control Deck time not reporting correctly on recording.

#### **Known Issues** <a href="#text-known-issues-4" id="text-known-issues-4"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### Motive 3.1.0 Final

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Added full support for the Prime<sup>x</sup> 120, Prime<sup>x</sup> 120W, and Slim<sup>x</sup> 120 cameras.

#### **Fixes** <a href="#text-fixes-2" id="text-fixes-2"></a>

* **IMU Sensor Fusion Fixes**
  * Fixed an issue with the IMU label stating "aligning" when it is not tracked and the rigid body is toggled off, then on.
  * Fixed the scale of the sensor fusion slider to be more reasonable at higher values.
  * Fixed an issue where auto-pair sometimes would not work correctly if multiple tags were present and one had ID 1.
  * Fixed an issue where sensor fusion would start applying before it was fully aligned.
  * Fixed an issue where the active tag reported the incorrect serial number for its associated BaseStation.
  * Fixed a crash when adding training data to a sensor fused rigid body.
* **Prime**<sup>**x**</sup>**&#x20;120 Cameras**
  * Fixed an issue where the Prime<sup>x</sup> 120 cameras would not fully mask the image with large numbers of necessary masks.
  * Fixed an issue where the Prime<sup>x</sup> 120/W ring lights would not illuminate four of the color LEDs during calibration.
* **Calibration**
  * Fixed a regression where calibrations take longer to process in Motive 3.1.0 than in previous versions.
  * Fixed an edge case with certain large volumes not updating with Continuous Calibration.
  * Fixed an issue where a Continuous Calibration log file was being output on public versions of the software.
* **Settings Window**
  * Fixed an issue where graphs preferred layouts weren't working.
  * Change the streaming name from Flexibodies to Trained Markersets.
  * Fixed an issue where marker data and bone data weren't separate options for streaming Trained Markerset data.
  * Fixed a bug in the Settings > General tab where text fields would trigger a .txt file export.
* Fixed an issue in NMotive/Motive Batch Processor where the Timecode.Subframe didn't output a valid number.
* Fixed an issue where Motive would become slow because of 1000 log pane events being refreshed every UI update.
* Fixed an issue where Trained Markersets did not retain the training count when the sets were loaded from .motive profiles.
* Fixed an issue where physically rotating a rigid body while attempting to rotate the pivot in software would cause additional rotations to be applied.
* Fixed an issue where the Graphs Pane would show the incorrect working range when using a custom Duration value to record.
* Fixed an issue with the sizing of the Name column in the Data pane.
* Fixed a crash that would happen when attempting to set the frame rate from the Devices pane if the eSync 2 was driving the rate.
* Fixed an issue where a tooltip appeared in the Assets pane that should not have appeared.
* Fixed an issue where custom camera numbers were not persisting between sessions of Motive.
* Fixed an issue where the No. column in the Devices pane was not sorting correctly when custom numbers were applied.

#### **Known Issues** <a href="#text-known-issues-4" id="text-known-issues-4"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### **Motive 3.1.0 Beta 3**

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Added initial support for the Prime<sup>x</sup> 120W.
* **IMU Sensor Fusion**
  * Added a property to control how quickly sensor fusion corrects to optical rotation.
  * Changed the IMU alignment process into a state that waits until enough samples are gathered to make setup easier.
  * Simplified the Auto-Configure option to just run Auto-Pair, then Align.
  * Added a popup when choosing the Active Tag options that perform an algorithm in Edit Mode to prevent confusion.
  * Added improvements to sensor fused rigid body tracking when IMU data drops for 30 or more frames.
* Added the ability to get/set asset properties in the Motive API.
* Turned the Symmetric Bones option on by default.
* Change the name of Stick Skeleton Mesh to Skeletal Mesh in the FBX Binary exporter.
* Added a streaming option for Unreal Engine bone naming conventions.

#### **Fixes** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **IMU Sensor Fusion**
  * Fixed an issue where a subset of the maximum number of Active Tags appeared in the Devices pane.
  * Fixed an issue where modifying the pivot of a sensor fused rigid body with the 3D gizmo tool or builder pane wouldn't update the IMU constraint and break sensor fusion.
  * Fixed an issue where custom selection groups could not be created for Active Tags.
* **Skeleton Solver**
  * Fixed an issue where the straight arms setting was not working as well as in Motive 3.0.x.
  * Fixed an issue where the toe bone was not bending.
* **NMotive / Motive Batch Processor**
  * Fixed an issue with the Motive Batch Processor Solve( ) function.
  * Fixed an issue where C3D files exported with the Motive Batch Processor were 1-frame shorter than C3Ds exported from Motive itself.
* **Builder Pane**
  * Fixed an issue where the Probe creation Refine and Create buttons were dependent on the same buttons in rigid body creation and would mix up text states because of it.
  * Fixed an issue with the active state of the Train from Take and Clear buttons for trained markersets.
  * Fixed an issue where the name in the builder pane was not being applied to newly created assets.
* **3D Viewer**
  * Fixed an issue where the Coordinate Axis and Marker Details properties in the settings pane weren't being respected in the 3D viewports.
  * Fixed an issue where the rigid body pivot snapped to 3D origin after removing the solve data.
  * Fixed an issue where the OptiTrack Logo 3D view option didn't make the logo appear consistently.
* **Licensing**
  * Fixed an issue where you can't export a rigid body, then import it if you have 3 skeleton/rigid bodies and a Body license.
  * Fixed an issue where Trained Markersets worked in Motive:Tracker when they should not.
* **Calibration**
  * Fixed an issue where active anchor markers are not used for Bumped Camera calculation if they are created in an off frame.
  * Fixed an issue where running a calibration from take file does not apply the result afterwards.
* **Assets**
  * Fixed an issue where you can add training data to rigid bodies and skeletons, but can't remove it.
  * Fixed an issue where exporting rigid bodies to CSV files, then importing those files did not work.
* **Graph Pane**
  * Fixed an issue where particularizing channels onto a device creates duplicate channels in the graphs.
  * Fixed an issue where the RigidBody default graphing options were configured incorrectly.
  * Fixed an issue where certain telemetry graph types were visible when they should not be.
* **Cameras**
  * Fixed an issue with the Flex 13 frame rates.
  * Fixed an issue where Object mode reported 0 for circularity in Flex cameras.
* Fixed an issue where video exporters only exported the first frame of the video.
* Fixed an issue where incrementing a numeric text input would corrupt the value.
* Fixed an issue where Auto-Label had a pop-up window when it should not.

#### **Known Issues** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### **Motive 3.1.0 Beta 2**

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Added initial support for the Prime<sup>x</sup> 120, Prime<sup>x</sup> 120W, and Slim<sup>x</sup> 120 cameras.
* Added support for a third variant of the Flex 3 and Slim 3U cameras.
* Added an FBX Binary Exporter option to allow individual Assets to export as .fbx files within a named "take" folder to facilitate Unreal Engine workflows.
* Added an FBX Binary Exporter option to Remove Bone Name Prefixes for better Unreal Engine workflows when working with single assets.
* Added an option to control the sampling duration for very large spaces struggling to get Continuous Calibration to make updates.
* Added a sampling time visual in the partitions section of the Info Pane.
* Added a warning when trying to turn on Continuous Calibration in Edit mode.
* Added a right click option to select cameras that have contributing rays for selected markers.
* Improved speed for the glove solve due to unnecessary actions.
* Added an average marker size function to the MotiveAPI for lens focusing.
* Added the ability to see tags with divisor rates 4, 5, and 6 for debugging purposes.
* Added a new Varjo XR4 clip to the HMD tool.
* Added a Save Image As ... action that can be assigned a hotkey.
* Added an Align to Rigid Body button to the Builder pane for consistency.
* Defaulted the Max Pixel Threshold to 3000 px to better support X120 cameras.

#### **Fixes** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Fix for a hang when setting the ground plane while the eSync 2 is using any source other than Internal Clock.
* Fix for a broken take Solve() function in NMotive (or the Motive Batch Processor).
* Fix for Prime Color camera presets not working as expected.
* Fix for a crash caused by saving and loading skeleton bone definitions.
* Fix for crash when two or more cameras are in MJPEG mode on Duo or Trio devices.
* Fix for calibrating selected cameras causing a crash.
* Fix for crash when closing Motive if USB cameras are connected.
* Fix for intermittent hang when creating a rigid body during playback mode.
* Fix for being unable to open .tak files with a Motive:Edit license.
* Fix for long standing issue where the incorrect VS redistributables are installed with Motive.
* Fix for issue where Slim 3U devices were only running at 60 Hz even when reporting otherwise.
* Fix for disabled assets still continuing to be processed for tracking.
* Fix for the spherical placement tool giving an incorrect center location.
* Fix for issue when loading files from certain versions of Motive.
* Fix for a licensing display issue where update licenses activated after the previous license expired show an incorrect date in the About Motive window.
* Fix for incorrect origin when setting the ground plane using a rigid body.
* Fixed outdated Builder pane message when nothing is selected.
* Fix for incorrect rigid body pivot location when auto-creating a 6 Rigid Body Skeleton.
* Fix for a missing filter switcher option for Flex 3 cameras that have them.
* Fix for clicking away while editing a constraint name in the Constraints pane is not setting the name.
* Fix for the Labels column not resizing with the Labels pane.
* Fix for slowdown when reconstructing markers with 200+ tracking cameras.
* Fix for allowing incompatible USB cameras rates.
* Fix for Flex 3 and Slim 3U cameras starting at too high of an exposure value.
* Fix for calibrating from wand take file failing for precision mode cameras due to object's roundness not being calculated.
* Fix for undo/redo actions not working on groups of assets and instead undoing 1 asset at a time.
* Fix for being allowed into Edit mode if there are no takes.
* Fix for dropped frames with large numbers of untracked rays.
* Fix for the smoothing property not applying at the value set in the user interface.
* **Continuous Calibration**
  * Fix for Bumped Camera that allows it to correct with large numbers of passive markers and untracked rays.
  * Fix for Info Pane camera list not clearing when disabling Bumped Camera.
  * Fix for Bumped Camera not working on some edge cases where less than 3 rays were used in the calculation.
  * Fix for not being able to rename Anchor Markers.
  * Fix for losing the Active ID for an Anchor Marker between Motive sessions.
  * Fix for inconsistencies when enabling Continuous Calibration in Live vs Edit modes.
  * Fix for multiple calibration updated notifications being sent out, causing Motive to freeze for larger camera count volume.
  * Updated anchor marker CSV export to include active IDs and camera visibility info.
  * Fix for being unable to delete anchor markers in live mode with the delete key.
  * Fix for Continuous Calibration updating too frequently by adding in a slight delay between sampling periods.
* **Exporters**
  * Fix for FBX Binary Exporter where Motion Builder skeleton names are incorrect.
  * Fix for issues exporting Markersets to CSV.
  * Fix for video files exporting over the maximum file size.
* **Streaming**
  * Fix for the ParentID property not streaming for Trained Markerset bones making it difficult to associate bones in client applications.
  * Fix for Trained Markersets not updating bone names until it's toggled.
  * Fix for streaming not working when the Skeleton as Rigid Bodies option is enabled.
  * Fix for NatNet not being able to set some eSync settings due to duplicated property names.
* **Devices and Assets**
  * Fix for column sizing issues in the Devices and Assets pane.
  * Fix for creating rigid bodies having different naming conventions based on how it was created.
  * Fix for deleting multiple assets at once causes some of them to remain.
  * Fix for selection issues when selecting between a BaseStation and a camera.
* **Motive API**
  * Fix for missing header files in installer.
  * Fix for the Motive API throwing errors when connecting to cameras.
  * Fix for crash in both the Markers and Projections examples on startup.
* **Peripheral API**
  * Removed x86 configurations from the Peripheral API.
  * Fix for typo in the filename for the glove device example in the Peripheral API.
* **Graphs**
  * Fix for telemetry graphs graphing at twice the rate of data due to double updates being sent.
  * Fix for graph labels not displaying rigid body names.
* **Viewer**
  * Reduced the memory usage when using a large number of cameras in the 2D camera view.
  * Disabled the Orient Pivot to IMU option when solved data exists.
  * Fix for uncalibrated camera getting incorrectly selected in 3D viewport under certain circumstances.
  * Fix for Save Image As ... for a camera in object mode creating a blank image.

#### **Known Issues** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### **Motive 3.1.0 Beta 1**

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Application**
  * **USB Cameras** - Added back support for all USB cameras. This includes the Flex 3, Flex 13, Slim 3U, Duo, and Trio cameras.
  * **Closing when Streaming Popup** - Added a popup to confirm that you wish to close Motive when streaming to prevent accidental closures.
  * **4K Monitor Support** - Added better support for high DPI and 4K monitors.
  * Cameras no longer require internet connection on first connection.
  * Added the ability to have a primary selection in Live mode.
  * Active marker selection now persists through occlusions.
  * Created a new default layout that showcases the wide view of the Data pane with the Advanced layout.
  * Renamed Label Graph to Constraints Graph everywhere in the application.
  * Renamed Bones to Joints everywhere in the application.
  * ​Renamed Marker Sets to Markersets everywhere in the application.
  * Updated the help folder to include all newly included third party libraries.
  * Added a modified 54 marker markerset with finger markers moved slightly.
  * Set Active Pattern Depth property to read-only for recorded takes.
  * The Motive icon in the About Motive window now changes when in Super User mode.
  * Updated the links in the Quick Start Menu to point to the new documentation.
  * Added the ability to install multiple versions of Motive 3.x at the same time by renaming the installation folder.
* **Assets Pane**
  * Add a new state/icon for Markersets that have been trained.
  * Cleaned up the asset right click menus to be more consistent between assets types and the 3D view.
  * Added a Color column to quickly view and change asset colors.
  * Modified all of the "+" actions in the Assets Pane to go to the builder pane for that asset type.
  * Renamed the Kind column to Type.
  * Made the action of resetting constraints also reset their weight values.
* **Assets and Constraints**
  * **Trained Markersets** - Added the ability to train a generic markerset and track most objects that you can imagine. Some examples of this include horses, floor mats, faces, and custom marker arangements. Markersets can be trained multiple times to allow the creation of generic tracking assets for custom marker arrangements. Added support for these new types of assets in exporters and streaming data.
  * **IMU Sensor Fusion** - Added back IMU Sensor Fusion for the CinePuck and rigid bodies containing IMU data. This allows for smoother overall tracking as well as features such as tracking full 6 degrees of freedom with only a single marker. Large changes were made to the workflow for using IMUs which allow for an easier setup, more understandable instructions, and the ability to debug issues.
  * **6 Rigid Body Skeletons** - Added back the ability to track 6 Rigid Body Skeletons. This also includes the ability to generically use a rigid body to drive any bone arrangement on a trained markerset or skeleton.
  * **Solved Data Recorded** - Brought back the functionality where solved asset joint data is recorded by default.
  * **Skeleton Limit on Body License Applies to Trained Markersets** - Added restrictions on the number of Trained Markersets available for use. This means a total of three skeletons and/or Trained Markersets can be used at any time.
  * Standardized asset and constraint definitions in (.motive) XML files.
  * Added the ability to undo and redo modifications to constraints.
  * Better handling when loading a (.motive) file with duplicated assets.
  * Improved speed when enabling/disabling large numbers of assets.
  * Renamed Asset Model Markers to Marker Constraints everywhere in the application.
  * Avoid swapping with identical rigid bodies with both passive and active markers.
  * Added an option for Min Active Markers to Boot for rigid bodies with both active and passive markers.
  * Better support for booting large assets with lower threshold settings.
* **Builder Pane**
  * **Markerset Training Tools** - Added tools to add or remove training data from Markersets.
  * **Marker Stick Manipulation Tools** - Added tools to modify asset marker sticks by adding, removing, and changing their colors. Trained Markersets also have the ability to auto-generate their marker sticks intelligently to make setup easier.
  * **Joint Manipulation Tools** - Added tools to modify joints for trained markersets by adding, removing, parenting, unparenting, and re-rooting joint configurations.
  * **Asset Dropdown Menu** - Added a dropdown asset selection menu to the Modify tab to allow you to edit assets other than the currently selected one.
  * **Visuals for 6RB Placements** - Added active puck object models for 6RB skeleton to help with rigid body placement.
  * **Align to Geometry** - Added an option to align the pivot of a rigid body to the geometry offset. This enabled quickly making the pivot location consistent between Motive and an external rendering programs like Unreal or Unity.
  * **Align to Rigid Body** - Added the ability to align the pivot of a rigid body to the same location as another rigid body.
  * **Align to Camera** - Added the ability to align the pivot for a rigid body to the same location as a camera.
  * Added the ability to align a rigid body pivot to a camera's location and orientation.
  * Added a Markersets type in the Create Tab.
  * Added the ability to modify marker stick colors and arrangements for rigid bodies.
  * Renamed the Spherical Pivot Placement tool to the Spherical Joint Placement tool.
  * Added back the 6 Rigid Body and related IK skeletons as skeleton creation options.
  * Moved the Refine option to a location in the list.
  * Removed the 3D view for rigid bodies in the Builder pane.
* **Calibration Pane**
  * **Volume Scale Tool** - Added a tool for setting the volume scale based on two markers of a known length.
  * Added the ability to undo ground plane actions.
  * Added the ability to add masks on the starting page of the calibration pane.
  * Added the ability to undo/redo ground plane modifications.
  * Added a Continuous Calibration statistics exporter.
* **Constraints Pane**
  * **Drag and Drop to Reorder** - Added the ability to drag and drop to reorder marker labels for asset in the Constraints Pane. This allows labeling order to be quickly changed.
  * **Rigid Body Constraints** - Rigid bodies can now be added and removed as constraints types. This allows the creation of custom IK skeleton models.
  * **IMU Constraints** - IMUs can be paired with rigid bodies as part of the sensor fusion workflow.
  * **Paste Label Names** - Added back the ability to paste a list into the constraints pane. This helps for quickly adding marker names for a Markerset.
  * Added a column for displaying different types of constraints to distinguish between marker, IMU, and rigid body constraints. Each constraint has their own icon for quick identification.
  * Duplicated the Builder Pane's marker sticks control in the Constraints Pane for easier asset editing.
  * Added a right click menu option to get back to sorting by the asset's custom labeling order.
  * Renamed the Generate Constraint actions to Reset Constraints.
* **Control Deck**
  * **Timecode in the Control Desk** - Added an option to replace the regular time visuals in the bottom bar with timecode values instead for users that have workflows revolving around timecode.
  * **2D Mode Indication** - Added the ability to right-click the Edit button in the Control Deck to quickly switch between 2D/3D modes and quickly tell which mode you are currently using.
* **Data Pane**
  * Added back the ability to drag and drop (.tak) files from one session to another in Motive.
  * Performance improvements when navigating folders containing thousands of subfolders.
  * Added a control to directly navigate to the current folder's subfolders.
  * Added a warning when copying the same assets into takes.
  * Reworded the helper message when no takes are in the Data pane.
* **Devices Pane**
  * **Active Devices** - Added the ability to view your connected BaseStation and Active Tags in Motive (only works with firmware 2.x+).
  * **Color Camera Presets** - Added right click menus for color cameras in the Devices pane for a one click setup process.
  * **Auto-pair IMU Devices** - Added the ability to automatically detect what rigid body is associated with a particular IMU and pair them automatically.
  * Lowered the default bitrate to 30 MB/s for Prime Color cameras.
  * Updated the Force Plate status icons to match IMU status icons.
  * Added a Partition ID column option for Tracking cameras.
* **Exporters**
  * **Export Markersets** - Added the ability to export markersets with bones to multiple exporters.
  * **Export Camera Locations** - Added the ability to export all camera locations to FBX Binary.
  * **Export Long Videos** - Added the ability to export long video files by splitting up the recording into 2 GB chunks.
  * Added joint naming conventions (Motive, FBX, Unreal Engine) to binary FBX exporter.
  * Removed export warning when attempting to export takes to FBX with no assets in them, but asset export options are on.
  * Added the ability to export markersets to video exports.
  * Improved the tool tip description for the BVH Hands Downward option.
  * Added more significant figures to the Time column for CSV exports.
  * Change Bones to Joints everywhere in the CSV export.
  * Added the ability to export out raw IMU data to CSV.
  * Made small changes to the take list XML export's formatting around date recorded, asset types, and timecode values.
  * Updated the name of Stick Skeleton to Meshed Skeleton for the FBX exporter.
* **Graphs Pane**
  * **Telemetry Graphs** - Added the ability to graph telemetry such as latency, data rate, and other system metrics.
  * **Skeleton Graphs** - Added the ability to graph skeleton joint data.
  * **IMU Graphs** - Added the ability to graph IMU data for debugging purposes.
  * Added the ability to collapse graph groups such as marker data, joint data, and force plate data.
  * Added the ability to change the significant figures for the graphs.
* **Info Pane**
  * **Continuous Calibration Bumped Camera** - Added the ability to correct the position of cameras that have been severely bumped if the camera(s) can see either active markers or anchor markers (if setup before the bump).
  * **Continuous Calibration Pane** - Added a Continuous Calibration diagnostic section to the Info Pane. This allows you to enable Continuous Calibration, monitor what cameras need samples, manipulate anchor markers, and view information about Continuous Calibration partitions if you are using them. Using this pane, you can now view a list of Anchor Marker, rename them, select them, and export/import them for more detailed control. This is also how you control settings around the new feature Bumped Camera.
  * **IMU Debugging Pane** - Added a section of the Info Pane for helping to diagnose issues and monitor the health of IMU signals.
* **Labels Pane**
  * When switching between sorting by the Gaps and Labels columns in the Labels pane the software now retains the default ordering for Labels.
  * Quick Label mode no longer also selects markers.
* **Log Pane**
  * **Log Pane** - Redesigned the log pane to use more standard Motive styling.
  * Made the error message for missing glove devices more relevant.
  * Added back the Unicast Log messages for detailed network diagnosis.
* **Motive API + NMotive + Peripheral API**
  * **Example Glove Integration** - Added an Example Glove Device for the Peripheral API.
  * 2D Projection Motive API Example - Added a Motive API example to demonstrate how to map a marker into camera 2D space and back.
  * Added easier access to camera properties through the Motive API.
  * Added a function that returns the currently detected ground plane in the Motive API.
  * Added the ability to query the working range from a take in NMotive.
  * Added the ability to set asset properties directly through the Motive API.
* **NatNet Streaming**
  * **NatNet Recalibrate from Marker Remotely** - Added the ability to Recalibrate from Markers over NatNet allowing 6RB skeletons to be re-scaled remotely.
  * **NatNet Trained Markerset Support** - Added support for streaming Trained Markersets.
  * Added the ability for a client to request the current NatNet bitstream version for better confidence for direct depacketizers.
  * Changed the default Bone Naming Convention to FBX.
  * Remotely changing eSync 2 settings is easier to do now, since the serial number is no longer required in the name field.
  * Made some improvements to NatNet to allow data repeaters.
  * Renamed Asset Markers to Marker Constraints in the streaming settings.
  * Added length values to streamed description and data packets for quicker parsing of data in direct depacketizing clients.
  * Added a steaming placeholder for PTP data.
* **Properties**
  * **Camera Locations Listed** - Camera locations are now listed in the properties pane when selected.
  * **Generic Geometry Visuals** - Added the ability to apply generic geometry visuals to joints such as spheres, cubes, cylinders, and more.
  * Added a separate date/time take property to indicate when Continuous Calibration last updated.
  * Added the ability to view both the name of a particular joint and the asset name at the same time.
  * Property validation happens after inputting a values, which makes setting high values easier to do.
  * The date/time values for properties now match regional formatting standards.
  * Added properties for asset joints.
  * Renamed the asset property Comment to Notes to be consistent with other properties.
  * Added properties for active tags and BaseStations.
  * Added missed MB/s for the bit rate property on color cameras.
  * Added a property for controlling the joint length for the last joint in a chain.
  * Updated the logic around how default properties work.
* **Settings Window**
  * **One Button Camera Lights Turn Off** - Added a single button to turn off all physical status lights on all cameras.
  * Added hotkeys for adding and removing sticks from assets.
  * Added data playback hotkeys similar to ones used in YouTube.
  * Added hotkeys for navigating around the asset joint hierarchy.
  * Added a read-only property to display the XML Broadcast port for streaming diagnosis.
  * Set a maximum value of the Minimum Rays to Continue property to be at most the value of the Minimum Rays to Start.
* **Viewer**
  * **Visualize Solved Asset Data** - The 3D View now shows the solve locations for assets. This means that after an asset has been solved, the exported data exactly matches what is shown in the 3D view. All assets now use the same visuals to show solved state.
  * **New Outline Selection Visual** - Update the selection visual to use a yellow border that doesn't change size based on the zoom level. The primary selected object is shown in Cyan.
  * **IMU Status Visual** - Added a new IMU sensor fusion status visual that describes in words the state of the sensor fusion algorithm.
  * **Hide Asset Markers** - Added the ability to hide all markers associated with a particular skeleton or assets. This improves labeling workflows by being able to hide markers when you are done labeling a particular asset.
  * **Custom Camera Numbers** - Added the ability to assign custom camera ID numbers to cameras. This appears in the 3D View as well as on the number on the physical camera.
  * **Asset Visuals More Consistent** - Worked towards making all asset types (markerset, rigid body, skeleton) have common properties. This allows you to bulk change visuals for different asset types and also makes the visual language more consistent. All assets now use the same visuals to show solved state. All right click context menus are now consistent between asset types.
  * **Skeleton Debugging Visual Improvement** - Added a new option for the Quality Visual that highlights the skeleton joint blue when a degree of freedom limit is reached.
  * **Ground Plane Length and Width** - Split the Grid Size setting into two properties to control the length and width of the 3D view ground plane grid.
  * **FBX Import for Geometry** - Added the ability import (.fbx) objects for Replace Geometry instead of just (.obj) files.
  * Rotation now follows a hierarchy (assets > markers/asset model markers > cameras) for deciding how to rotate the 3D view when different things are selected. This also allows you to now rotate the scene using camera location.
  * Changed the Asset Model Marker visual to use a wireframe sphere.
  * Added the ability to align a rigid body pivot location to the location of a camera.
  * Added the ability to select Anchor Markers.
  * When in quick label mode with labels on, Motive now only shows the labels for the selected asset in the 3D View.
  * Added a new visual option for indicating the Degree of Freedom for a particular joint.
  * Improve camera selection visual for 4K monitors when in the 2D Cameras view.
  * Added global controls for showing/hiding marker constraints in the 3D View.
  * Selecting hidden Marker Constraints using the constraints pane or other methods makes the constraints visible in the 3D view regardless of their current visible state.
  * Added a new option to allow a simplified marker name to be shown in the 3D View to reduce clutter.
  * Changed the default joint color to gray for skeletons and markersets.
  * Added the option to make anchor markers selectable in the 3D view.
  * Made a minimum pixel diameter when viewing from a camera to make manual camera adjustments easier when markers are far away.
  * Added a visual for showing the IMU axis relative to a joint's axis.
  * Added an Attach View to Selection hotkey option that locks both the position and orientation for a follow selected view.
* **Viewer - Gizmo**
  * **Single Joint Skeleton Modifications** - Improved the 3D gizmo tool for editing skeleton definition by holding child joints in their original locations.
  * **Directly Modify the Rigid Body with Geometry** - Added the ability to either edit the underlying rigid body or the geometry file.
  * Added back the ability to scale the rigid body joint visual.
  * Added the ability to edit the position of anchor markers with the Gizmo tool.

#### **Fixes** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Application**
  * Fixed issue with File > Undo text missing a starting double quotation mark.
  * Fixed intermittent hang after a few attempts of Solve All Assets.
  * Fixed issues with undoing the delete action for assets.
  * Fixed a hang when toggling between Genlock and Internal Clock for the eSync 2 input.
* **Builder Pane**
  * Fixed the Rizzoli (43) skeleton missing markersticks and colors by default.
  * Fixed an issue where the rigid body name property was not linked between the Builder Pane and the Settings Window.
  * Fixed the tooltips formatting in the Builder Pane.
* **Calibration Pane**
  * Fixed occasional hang when giving the calibration algorithm mostly samples that are only seen by a few cameras at a time.
  * Fixed volume flip issue when using the classic L-Frame calibration square.
  * Fixed a long standing crash when there are too many samples given to some cameras and standard number for other cameras.
* **Constraints Pane**
  * Fixed bug when using the arrow keys while renaming a constraint.
* **Control Deck**
  * Fixed an issue where more than 6 digits could not be input into the frame values.
  * Fixed an issue where the control deck timeline would stutter if the Labels Pane wasn't open with some takes.
* **Data Pane**
  * Fixed Delete All Solve Assets Data not also saying Selected Range when there is a range selected.
* **Devices Pane**
  * Fixed a bug with the color camera's multiplier setting when running at 1000 Hz.
  * Fixed an issue where the sync output port on the Prime Color cameras was not working.
* **Exporters**
  * Fixed an issue where the Y-Axis of rotation for passive finger marker skeletons doesn't animate as expected.
  * Fixed an issue where renaming a channel name of a DAQ or EMG would remove the channel data from the take file and break C3D export.
  * Fixed a duplicate pop-up message for each unsolved take during export.
* **Graphs Pane**
  * Fixed an occasional gap in the Graphs pane.
  * Fixed extra bar at the top of the pane.
* **Log Pane**
  * Fixed a software hang when selecting a 2D frame drop log message.
* **Motive API + NMotive**
  * Fixed a crash when calling TT\_Initialize(...) after TT\_Shutdown(...).
* **NatNet Streaming**
  * Fixed a force plate count out of range error in NatNet.
* **Settings Window**
  * Fixed a visualization issue with the " hotkey in the Keyboard hotkey manager.
  * Fixed a bug with the Asset > Visuals > Marker Constraints property not functioning correctly and updated the tooltip.
* **Viewer**
  * Fixed coloring issue for skeleton in the Orthographic Back view.
  * Fixed an issue where you could rename probe points, but the 3D view wouldn't display their names.
  * Fixed marker constraint sometimes getting visually clipped by the skeleton mesh.
  * Fixed minor render order issues between asset types.
  * Fixed rendering issue with a specific HMD object file.
  * Fixed an issue while using both the gizmo tool and taking a screenshot.

#### **Known Issues** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

</details>

<details>

<summary>Motive 3.0</summary>

### Motive 3.0.3 Final

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Added support for Prime<sup>x</sup> 41 and Prime<sup>x</sup> 22 cameras over serial number M99450+
* Added advanced properties for a given camera's model and subtype.

#### **Known Issues** <a href="#text-known-issues-2" id="text-known-issues-2"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### Motive 3.0.2 Final

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Cameras no longer require internet connection on first connection.
* Updates to Continuous Calibration to make it work better for a more diverse set of camera configurations.
* Added the ability to include a basic mesh to the FBX exporter for better Unreal Engine support.
* Added the Varjo HMD clip to Motive.
* Motive now saves the calibration info for disconnected cameras with the auto-saved calibration file.
* Added a third decimal place for the Input Monitor section for the eSync 2.
* Disabled the active pattern depth property in Edit to prevent confusion.
* Added reporting through the Log pane when a partition does not have enough cameras in it.

#### **Fixes** <a href="#text-fixes-2" id="text-fixes-2"></a>

* Fix for issue where camera LEDs were off even though Motive showed them as being on.
* Fix for an issue where the time it takes to start recording scaled based on the number of cameras.
* Fix for not being able to re-run calibration (.tak) files using the calibration pane.
* Fix for not being able to debug code for the Peripheral API and Motive API.
* Fix for hang when exporting multiple tak files with reference video.
* Fix for a memory leak when exporting videos using NMotive.
* Fix for a crash on startup for some users while using the Motive Batch Processor.
* Fix for an issue where the Settings Pane would go stale and stop updating if left open for a long time.
* Fix for an issue where the BaseStation was not showing the serial number in the Devices Pane.
* Fix for video export issue where color reference data was about 1 frame behind the tracking data.
* Fix for several display issues when showing tool tips.
* Fix for missing tool tips for some settings.
* Fix for outdated OptiTrack documentation links.
* Fix for Motive not always closing as a task.
* Fix for bad finger data with takes containing Manus data recorded in Beta versions of Motive 3.0.
* Fix for Use World Coordinates property not working on bones with the CSV exporter.
* Fix for FBX exporter issue with some specific files.
* Fix for edge case Continuous Calibration Partition IDs causing issues in the Log Pane.

#### **Known Issues** <a href="#text-known-issues-4" id="text-known-issues-4"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### **Motive 3.0.1 Final**

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Changed the unlabeled color to light magenta in the Labels pane.

#### **Fixes** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Fixed the pattern-based fill tool.
* Fixed the selection order for pattern-based tool to use the last selected marker.
* Fixed an issue where several gap filling hotkeys were missing.
* Fixed an issue where the fill gap hotkey did not respect the selected range.
* Fixed the Delete context menu option in the labels pane by making it delete all marker data.
* Fixed an issue where Motive kept takes in memory after exporting data.
* Fixed the tracked rays option, so that it persists between Motive sessions.
* Fixed an issue where custom zoom mouse actions would sometimes pan.
* Fixed an inconsistent scrolling speed issue with zoom mouse actions.
* Fixed an issue where the camera gain would be set to 4 between sessions.
* Fixed an issue in the Motive API example code where the camera indexing started at 0, which didn't match the Motive user interface.
* Fixed an issue where the origin would revert sometimes after the ground plane was applied.
* Fixed an issue where continuous calibration would alter some calibrations directly after loading them.

#### **Known Issues** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* Files: Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### **Motive 3.0.0 Beta 3**

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Mask Individual Markers** - Added the ability to select a marker and mask _only that marker_ for all cameras.
* **Mask Visible Cameras** - Added the ability to mask other visible cameras by using their 3D location relative to one another. This does _not_ mask other markers in the scene.
* **Gizmo Fine Edits** - Press Shift while editing to the location of an object to make more defined edits.
* Motive and the Batch Processor can now be run simultaneously.
* Users can now directly access the license folder (and export license information) in the 'About Motive' window.
* Added the ability to exclude finger joints during skeleton export.
* Added a 'deflection ratio' property to improve tracking when assets don't fit the 3D models very well (typically on large objects).
* Pressing the next/previous gap buttons (_Z, Shift + Z_) places the time cursor just before the gap (instead of in the middle) to simplify labeling.
* Cameras that are actively being viewed from may now be selected.
* The action of snapping a camera to markers (after making manual adjustments with the gizmo tool) can now be mapped to a hotkey.
* Updated the allow/deny list feature to allow users to specify cameras to include or exclude.

#### **Fixes** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Security Keys Connect to Motive Better** - This should resolve connection issues for some users.
* **Fixed Speed Regression** - Data playback is back to full speed after having slowed down for a breather in Beta 2.
* **No Longer Record Solved Data** - This helps users who might not have known to re-solve data after making marker edits.
* **Increased Flexibility for Skeletons** - Actors now track better while performing certain actions such as stretching.
* Fix for issue on startup where cameras in Object mode didn't activate the physical IR LEDs.
* Fixed the Peripheral API example project so that it works without any modification.
* Fixed an issue where cameras would show up on top of one another at the origin.
* Fixed an issue where the 'Recalibrate from Selection' action didn't work for certain takes.
* Fixed a potentially 'painful' issue where passive finger skeletons could have unnatural finger bends. They are all better now!
* Fixed an issue where hands appeared too large for Baseline 49 skeletons.
* Fixed an issue where creating a skeleton from the hotkey or context menu didn't use the custom Constraints file.
* Fixed an incorrect warning message, "Test Error," when deleting video data.
* Fixed a crash with the Go to Next Unlabeled Marker operation on the right side of Split (Left/Right) view mode in the Labels pane.
* Fixed an issue with a specific take that would not allow you to label a marker.
* Updated the camera authorization message to be more informative.
* Fixed an issue where undoing a labeling operation didn't move the selection in the Labels pane back to the previous label.
* Fixed an issue where renaming a channel of the DAQ prevented data collection.
* Fixed a crash with grayscale camera mode in some scenarios.
* **Exporters**
  * Fixed an issue where the total length of exported files did not match the file length in Motive.
  * Fixed end bone names not matching the names of the rest of the skeleton for FBX binary exports.
  * Fixed an issue where FBX Binary files loaded into MoBu would state they only had 1 frame due to file type duplication issue.
  * Fixed an issue with the end time of FBX files exported through the Batch processor. \\
  * Fixed inconsistency in UTF versions between the profile and the take list exporter.
  * Fixed an issue where a specific file wouldn't export data to FBX binary.
  * Fixed an issue with device data exported to CSV data from a take file recorded in an unsupported version of Motive.
  * Fixed an issue where 3D overlays for rigid bodies were not shown on exported video
* **Manus Gloves**
  * Possible fix for dropped 3D marker frames when glove data is missing in Live.
  * Fixed an issue where the final frame rate of data going through Motive was negatively affected.
* **Edit Tools**
  * Fixed an issue where the pattern fill target properties disappeared.
  * Fixed an issue where the Unlimited gap size property didn't work.
  * Fixed an issue where the Maximum Gap Size did not persist between sessions of Motive.
  * Fixed several issues with how the dropdown/text fields in the Edit Tools pane behave.
  * Fixed the height of the Gaps section in the Edit Tools pane.
* **Graphs**
  * Fixed an issue in the Graphs pane where Alt-dragging on graph view moves the current time immediately to the end of the timeline.
  * Fixed a crash in the Graphs pane visual tab while graphing certain device data.
  * Fixed an issue where renaming marker labels was not updating the marker labels in the Graphs pane.
* **Calibration**
  * Fixed an issue where a selected camera calibration never completes if Camera 1 doesn't receive any samples.
  * Fixed an issue where disabling a camera did not remove it from continuous calibration.
* **Property Bugs**
  * **Fixed DAQ** - Fixed an issue where DAQs wouldn't enable. Also fixed some styling issues with the DAQ popover.
  * Fixed the Local Interface, which is the streaming IP address, not changing its value.
  * Fixed a crash when setting a value in the Fragment tool in the Edit Tools pane.
  * Fixed a crash when editing the Advanced state of properties on an asset.
  * Fixed an issue where the eSync would not change its Type property.
  * Fixed issues with the properties in the export window not applying correctly, macros names not matching, and properties allowing negative values that would crash Motive if used.
  * Fixed the property macros wording to correctly match the options.
  * Fixed an issue causing several take properties to not display any information.
  * Fixed the serial number on cameras that don't appear in the Properties pane.
  * Fixed an issue where the 'Tab' button didn't iterate through properties.
  * Fixed an issue where read-only text could not be selected.
  * Fixed an issue with undoing changes to number fields.
  * Fixed a variety of issues with constraint properties.
  * Fixed a bug with incorrectly bound translation dampening properties.Fixed an issue where force plate coordinates could not be manually adjusted and the visual would disappear.

#### **Known Issues** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### **Motive 3.0.0 Beta 2**

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Manually Adjust Cameras** - Add the ability to use the gizmo to adjust camera positions and snap into a best guess location for the camera. This allows continuous calibration to do the rest of the work to update your camera into position.
* **Continuous Calibration Improvements** - Added better log message stating which cameras need more samples. Added the ability to use passive Anchor Markers.
* **Reconstruction Bounds** - Added back the ability to not create marker data outside of a predefined area.
* Added back the ability to apply calibrations early, but only after 10 minutes.
* Added the option to not export fingers for BVH and FBX Binary files.
* Added an option to export 3DS Max biped compliant names to BVH files.
* Added an option to export classic bone naming convention for CSV files.
* Added date/time values to exported log files.

#### **Fixes** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Fix for calibration samples not collecting after performing "Edit > Reset Settings."
* Fix for pattern based filling only works with 4 markers. It now works down to 2 markers.
* Updated the Replace Geometry tool to use centimeters for scale of object models.
* Fix for placing the skeleton at the origin when performing a Ctrl+R skeleton reset.
* Fix for the hotkeys controlling object visibility both hiding and deselecting object instead of just hiding/showing them.
* Fix for the Rizzoli Lower markerset not containing a marker stick model.
* Fix for the wireless signal value not matching Manus's software.
* Added back the ability to add constraints to markersets even when markers aren't selected.
* Fix for reference overlay not lining up over the native frame rate.
* Fix for crash when pressing Alt+Tab on empty assets pane.
* Fix for custom default layouts not working.
* Updated the First Time Using Motive language a bit.
* Fix for possible crash when using Pattern based fills with Unlimited time ranges.
* **Licensing and Security**
  * Fix for Security Keys not connecting sometimes.
  * Fix for Retry in the Splash Screen not checking for a Security Key again.
  * Fix for a display issue with demo license end dates.
  * Fix for Motive only checking if the Security Key is connected on startup.
  * Fix for an occasional crash when playing back takes without security key connected.
* **Batch Processing**
  * Fix for the action Reconstruct and Auto-label not working with the batch processor.
  * Fix for not being able to start both Motive and the Batch Processor at the same time.
  * Fix for takes containing finger data not batch processing with some scripts.
  * Fix for the NMotive CodeExample.sln project not working without modification.
* **Streaming**
  * Fixed the Broadcast Sample - Fixed an issue where remote triggering used the Data Port instead of the Command Port.
  * Fixed Markerset Markers - This allows the MotionBuilder Optical plugin to get better data from Motive, but using the Asset Model Marker locations when a marker goes missing.
  * Fix for skeleton joints not populating their mean error value for NatNet.
  * Fix for the residual not streaming with sMarker data.
  * Fix for issue where Motive sent the same frame twice.
* **Data**
  * Fix for subfolders not appearing in quick folder selection dropdown menu in the Data pane.
  * Fix for mislabeled operation when performing the Solve All Assets action.
* **Settings and Properties**
  * Reduced the number of ways to enable/disable Continuous Calibration to just one.
  * Hid some Legacy properties on the eSync 2 that should not be visible.
  * Set the Boot Residual Percent property to advanced.
  * Possible fix for editing decimal values in languages that use commas instead of dots for decimals.
* **Devices**
  * Fix for older takes not loading device data correctly into Motive 3.0.
  * Fix for force plates not using rounded device rates in some situations.
  * Fix for issue where the mixed states don't appear correctly for a collapsed the force plate group in the Devices pane.
* **Exporters**
  * Fix for an issue where the "File > Export Calibration" didn't export the calibration for the currently loaded take.
  * Increase the height of the video exporter pop-up dialog to show more of the Overlay section.
  * Fix for timecode not exporting to CSV files.
  * Fix for incorrect date recorded property with take data export and Japanese language computers.
* **Viewer**
  * Fix for issue where dragging in the color picker for skeletons creates a refresh rate issue.
  * Fix for an issue where jogging the timeline with Alt+Left in the 3D view will cause the timeline to the opposite of expected.
  * Made asset model markers more transparent to help with visibility issues.
  * Fix for viewport issue correctly framing markers when one marker is very far away causing the view to not be able to return to the origin.
  * Fix for the create skeleton context menu not matching the name in the Builder pane.
  * Fix for issue where scaling marker data would cause the markers to all go to the same point.
* **Builder**
  * Fix for the builder pane does not auto-incrementing the skeleton name.
  * Fix for the ( ? ) help popup not staying up when hovering over it.
  * Clear custom constraint options when they no longer exist on the file system.

#### **Known Issues** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

### **Motive 3.0.0 Beta 1**

#### **New Features** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **New Solver**
  * **Tracking Made Easy** - Quality tracking out of the box with little to no property changes. For example, active and passive markers now track without changing a single setting.
  * **Improved Solve Speed** - Large numbers of rigid bodies or skeletons now track with decreased latency.
  * **Robust Solve Quality** - Extremely high-quality marker, rigid body, and skeleton data even in difficult tracking situations with high amounts of occlusion.
* **Application**
  * **Manus Finger Tracking** - Added support for Manus VR finger tracking in Motive.
  * **Prime**<sup>**x**</sup>**&#x20;Camera Support** - Prime<sup>x</sup> cameras feature increased tracking range, the capability to capture at higher frame rates (up to 1000 Hz with reduced image resolutions), and the ability to capture beautiful full-resolution MJPEG video.
  * **Refactored Pipeline** - Allows tracking data to flow smoothly through Motive. This provides benefits such as showing marker sticks and colors in Live Mode and allows cameras to run perpetually in Live mode for data processing and continuous calibration. This change also provides the basis for major updates on the data processing planned for future releases of Motive.
  * **More Than 250 Cameras at a Time** - Users can now run Motive with more than 250 cameras/devices connected at a time, with only one PC.
  * **Updated Licensing** - A Security Key device is now required instead of the previous Hardware Key. New licenses now exclusively either work with Motive 3.X+ or Motive 2.X (and earlier). The Motive:Body license now supports only as many as 3 skeletons. A new Motive:Body-Unlimited license type has been added that enables an unlimited number of assets at one time.
  * **Live Mode Always Running** - Motive now runs Live mode separate to Edit mode. This allows the user to modify or export takes without loading the file. It also keeps the cameras warmed up even while reviewing recorded data.
  * **No Installer Dependencies** - Removed the DirectX 9 dependency in Motive allowing the software to be installed on computers without an internet connection.
  * **Simplified File Menus** - Simplified most of the menus on the toolbar including the File, Panes, and Help menus.
  * **Updated the Default Layouts** - Updated the default layouts to be the same for all licenses and camera systems.
  * **Quick Start Window** - Added dismissable links on startup to learn about Motive file types and how to manage them, improving the overall experience for new and existing users alike.
  * **Constraints Pane** - Generalized the old Markersets pane to work for all asset types allowing the first steps toward totally customizable assets.
  * **Probe Pane** - Redesigned the interface for using the Digitizing Probe.
  * **Info Pane** - Rearranged some of the tools for visualizing rigid body settings and for testing the rough accuracy of the camera volume.
  * Deprecated support for Visual Studio 2008 and 2010 in Motive and all of the other supporting applications.
  * Unnecessary camera error notifications no longer appear when first starting Motive.
  * Added a pop-up notification to alert users if they are about to record data with a camera set in grayscale mode.
  * Updated the icon visual of the TAK files to better stand out on white backgrounds.
  * The File menu at the top of Motive now uses standard windows hotkeys.
  * Updated all pop-up menus to use the new user interface style.
  * Added a pop-up notification to alert users if they start streaming data with rigid bodies that have duplicate streaming IDs.
  * When saving out a take using the Save Current Take As ... option, Motive loads the saved take file immediately.
  * Added a subtle hover state to all buttons.
  * Standardized the checkbox visual among all instances.
  * Added an option to export license information as a text file from the About Motive window.
  * Increased the size of the "x" icon in the About Motive window to match other windows.
  * Standardized the formatting of the progress bar messages when performing "reconstruct," "auto-label," and "solve" actions.
  * Added the ability to use Shift+Home and Shift+End as hotkeys to navigate lists.
  * Small clarifying update to the Licensee Product definition in the EULA.
  * Added a camera list exporter for getting a CSV file containing all of your devices.
* **Movement Sciences**
  * **Delsys EMG integration** - Motive now supports the digital integration of Delsys Trigno EMG platforms using Trigno Avanti sensors. Through this, users can collect synchronized EMG data alongside motion capture data.
  * **Force Plate Clock Syn**c - All force plates (AMTI, Bertec, Kissler) now support Reference Clock Synchronization allowing per-frame synchronization with motion capture data.
  * **Simplified Setup** - The eSync, force plates, and DAQ devices can be set up quickly and easily by right-clicking the devices and choosing new quick setup options.
  * **Improved DAQ Popover** - Added Select All option, clicking on channel numbers no longer drags the popover, and it never appears below the screen.
  * **Device only Recording** - There is no longer a requirement to have marker data present to record with devices. This allows for workflows such as recording color video and force plate data without tracking data.
  * Added instructional pop-up messages when configuring force plate and DAQ devices the first time.
  * Removed recording delay with Bertec plates by using reference clock sync, it also improves recording reliability with back to back recordings.
  * Improvements in configuring properties for a group of similar force plates.
  * Added the ability to specify a fixed offset value for a channel of data in a graph, either via the XML graph specification and/or through the UI.
  * The graphs pane now handles enabling/disabling DAQ channels better.
  * Prevented naming multiple DAQ channels to avoid multiple channels with conflicting configurations.
  * Now allow for multiple plates to be positioned at the same time.
  * The scale property is now hidden for devices that do not require it.
  * Added lateral fibula epicondyle markers to the Rizzoli Lower Feet (42) markerset.
  * Corrected the marker placement representation of the Rizzoli Left/Right Foot (16) markerset in the Builder pane by moving the marker visuals down slightly.
* **Viewer Pane**
  * **Viewer Pane** - Updated 3D viewport rendering to OpenGL and added a variety of visual improvements such as including the ability to split the viewport and improved context menu options.
  * **New Asset Visuals** - Added a new skinned mesh for visualizing skeletons and updated the rigid body pivot point to an octahedron visual.
  * **Live Marker Sticks** - The marker stick visual now shows up in both Live and Edit modes.
  * **Reference Camera Visuals** - Reference video cameras now appear as a different color in the 3D view, so that they can be quickly identified.
  * **Simplified Skeleton Creation** - Added a new hotkey and a context menu option for creating skeletons from a selection of markers.
  * **Updated Marker Visuals** - Updated the default marker color options for passive (white), active (cyan), and labeled (other colors) markers.
  * Assigned hotkeys to the visibility options for markers, rigid bodies, skeletons, cameras, and marker sticks.
  * Changed visual of probe sample points to use crosshairs instead of the same visual as markers.
  * Added the pixel inspector as an option to the Cameras view.
  * Added meter marks to the ground plane grid and made setting the ground plane more intuitive.
  * Modified the capture volume visual to not extend below the floor.
  * Allowed click-and-drag mouse action in the camera view for selecting multiple cameras altogether.
  * Made several updates to the Heads Up Display in the 3D perspective view.
  * Updated the Marker Label visuals and extended support for this feature to show the name of Asset Model Markers.
  * Revealed the Marker Info visual for all users.
  * Added the ability to turn on/off the visuals for all asset model markers regardless of asset properties and added a hotkey for controlling this.
  * Added options to visualize tracked rays for either all of the markers or only the selected markers in the perspective view.
  * Added the ability to add a single frame of data to asset model marker locations as a temporary replacement for the model-fill.
  * Removed the ability to hide the mask visuals in the camera views to avoid confusion.
  * The Show Field of View option for Prime<sup>x</sup> cameras changes based on the region of interest shown on the camera.
  * Added the ability to show the distance between any two selected asset model markers.
  * Updated the aim assist reticle to prevent having a single camera with a lingering reticle at the end of the setup.
  * Added a notification pop-up when deleting a labeled marker without a range selected to avoid accidentally deleting entire marker data.
  * Added the ability to change the floor color in the perspective view.
  * Patched the holes in the skeleton segment mesh when using a partial skeleton.
* **Settings Window**
  * **Settings Window** - Consolidated all the properties and controls that are not changed frequently into one location. This combines the application settings, streaming settings, mouse controls, keyboard hotkeys, and audio settings into one window.
  * **Hotkey Editor** - Radically redesigned the hotkey editor allowing users to easily assign different hotkeys and save them out to their own profiles.
  * The hotkeys have been renamed to be more understandable and searchable. A variety of useful default hotkeys and assignable hotkeys have also been added.
  * Added a warning to the Live pipeline settings to help users change the pipeline settings in the correct location.
  * Merged the Block Width and Mask Height properties into a single property.
  * Added a Max Colors option to skeleton color preset macro to increase the number of different skeleton colors that are automatically assigned upon creation.
  * Added a disclaimer to the audio section that links to the wiki.
* **Calibration**
  * **Large Volume Continuous Calibration** - Improved continuous calibration for systems with any number of cameras.
  * **Redesigned Calibration Pane Visuals** - The calibration pane is now self contained, meaning that users can perform a calibration with only the calibration pane up. The new visuals include step-by-step instructions that guide new users through the calibration process. These visuals easily scale as many as 300 cameras.
  * **Automatically Save Calibrations** - After a calibration is completed the calibration file is automatically saved into a default folder for easy recovery.
  * **Active Anchor Markers for Continuous Calibration** - Active markers can now be added to the scene to both aid continuous calibration with disconnected volumes and provide peace of mind regarding origin drift.
  * Added the ability to set the ground plane using any rigid body.
  * Updated the 2D/3D calibration visuals in the Viewer pane.
  * Moved and added specialized calibration options to the Settings window.
* **Edit Tools and Labels**
  * **Labels Pane** - The labeling pane now features a compact design with several different layout configurations for optimizing manual labeling workflow. This also includes other visual enhancements such as inverting the % meaning of the gaps column as well as other improved visuals. The rendering performance of the labels pane has been significantly improved.
  * **Edit Tools Pane** - Controls are simplified to display the frame ranges of data to which the edit actions will be applied. Visuals have been standardized with other parts of Motive. Added a Fragment tool to quickly delete markers that only exist for a few frames.
  * Added the ability to sort the data based on the asset definitions or on the alphabetical order.
  * Added new context menus for labeled and unlabeled markers including a Go to Next Tail option.
  * Added the ability to pattern-fill all selected markers.
  * The smart trim feature is now disabled by default.
  * Set the default label range to "All or Selected."
* **Exporters - General**
  * **Export Progress Indicator** - Added new progress indicator visual for processing take files or exporting data.
  * **Devices Only Export** - Supported exporting device data to CSV and C3D even without marker data.
  * All of the exporters can now be used in both Live and Edit mode.
  * Added more decimal places to the scale option on all of the exporters.
  * Lower body only skeletons no longer export the upper body for FBX, BVH, and CSV data.
  * The following formats can now be exported with Z+ up coordinate axis: CSV, TRC, BVH, and C3D (already supported).
  * Grouped and rearranged the exporter properties to improve readability.
* **Exporters - CSV**
  * Updated the default units in the CSV exporter to millimeters.
  * Added a Free-Moment data column to the CSV export for force plates.
  * Added the ability to include system latency metrics in the CSV export.
  * Upsampled marker data is now interpolated correctly in the CSV export.
  * Removed the marker quality column from the CSV exporter as it is no longer applicable to the new solver.
* **Exporters - FBX and BVH**
  * **BVH Multiple File Export** - The BVH exporter now exports a file per skeleton listed.
  * Add end-joints to the BVH and FBX exporters to better visualize skeletons in other third-party software down the pipeline.
  * Standardized the bone hierarchy export format between BVH and FBX files.
  * Added the ability to export 6 Rigid Body skeletons to BVH and FBX files.
  * Added the ability to export out the Field of View and position of color cameras to FBX.
  * Added the ability to export the data just for a single asset when exporting into FBX binary format.
  * Added a marker name separator option to the FBX Binary exporter.
  * Rigid bodies now export as both nulls and bones in the FBX Binary exporter.
  * Assets with an "\_" in their name now export correctly in both FBX exporters.
  * Added an option to use the Asset Model Marker data instead of the marker data with the FBX Ascii marker exporter.
* **Exporters - C3D**
  * Removed the device number after the DAQ channels to clean up the list of devices in the exported C3D file.
  * Added a potential fix to the C3D exporter where it exports only up to 65534 frames in some cases.
  * Improved how recorded force plate data gets exported into C3D so that they can be imported into more applications.
  * Specified the units for force plate data in exported C3D files.
* **Exporters - Video and Audio**
  * **Asset Overlay for Video Export** - Reference MJPEG video data can now be exported with the 3D visuals overlaid on top of the video.
  * **Fast MJPEG Export** - Significantly sped up MJPEG video exporter. This is now the default export method.
  * Added a Last Frame option to the Dropped Frame video export settings for preserving the exact number of frames while keeping the exported video to look smooth.
  * Allowed frame rate metadata for exported videos to be non-integer values.
  * Added the frame number to video exports that have timecode overlay.
  * Added an option to export video data into a sequence of JPEG images.
  * Updated descriptions for video export options for increased clarity.
  * Allow timecode overlay to work with takes not containing timecode by overlaying the frame number instead.
  * Added the ability to batch export audio files without repeated pop-up messages.
* **Data Pane**
  * **Decreased Loading Times** - Significantly decreased the amount of time it takes to load large folders into the data pane.
  * **Visible Folder is Current Folder** - The currently selected folder in the data pane is now always the folder that captured data records into.
  * **New Default Folder Location** - Updated the default save location workflow and added a way to generate daily folders to record data into.
  * Added the ability to revert the current take.
  * Decreased the minimum height of the pane to fit into tight layouts.
  * Added the ability to select multiple session folders in the data pane for quick folder management.
  * Added a column option to show the version of Motive that each take was captured in.
  * Allowed the Best, Health, and Progress properties to be changed on a group of selected takes.
  * Made small visual improvements such as making the current take indicator wider and standardizing the search bar.
  * Improved the double-clicking action to make it work more consistently.
  * Clarified how to delete 2D/Video/Audio data through the context menu and cleaned up the pop-up menu.
  * Added the ability to quickly generate new session folders to record the data into.
  * Added other column values to the take info exporter.
  * Added a column for the Last Saved in Version property.
  * Removed the default Classic layout option.
* **Control Deck**
  * **Dynamic Scaling** - The Control Deck now scales based on the resolution of the monitor being used.
  * **Record Duration** - Record Added the ability to record for a predetermined amount of time.
  * **Streaming Status Icon** - Added a streaming status icon that reports if unicast clients are connected to Motive and opens the streaming settings.
  * Improved workflow for how take names are auto-generated in the control deck and added a button to clear the current take name.
  * Added streaming metrics to the status panel popover.
  * Updated the status panel to work with the new solver.
  * The mouse now loops when scrubbing the timeline using the alt hotkey.
  * Visual update icons for the working range and record button.
  * Made the mouse wheel action consistent by making it only move 1 frame at a time in the control deck timeline.
  * Added the ability to select the take name in Edit.
  * Updated the power mode notifications to work with newer power modes.
  * Simplified the streaming metrics in the status panel popover.
* **Properties Pane**
  * **Added Units and Number Controls** - Remade number field property types to indicate units, and also included a stepper, a slider, or a dropdown menu depending on the property type.
  * **Upgraded the Color Picker** - The color picker control received several upgrades and fixes such as custom color preset, better default colors, more compact view, opacity control, and rainbow color macro values that help choose some special color values throughout the software.
  * **Lock Selection** - Added the ability to lock the properties pane to the currently selected object.
  * Added properties for Asset Model Markers - This standardizes asset model markers between asset types and allows properties to be changed in bulk if needed.
  * Reversed the logic for how editing advanced properties work so that you add properties from the advanced options instead of removing them.
  * Always show the "..." icon for properties with Macros.
  * Reorganized and modified the properties that appear for assets, devices, and takes.
  * Persist the Show Advanced is on or off for the properties pane and settings window.
* **Devices and Devices Pane**
  * **Prime**<sup>**x**</sup>**&#x20;Camera Support** - Prime<sup>x</sup> cameras feature increased tracking range, the capability to capture at higher frame rates (with reduced image resolutions), and the ability to capture full-resolution MJPEG video.
  * **Lowered Prime Camera Minimum Rate** - Lowered the minimum frame rate to 20 Hz for Prime cameras.
  * **Single User Camera Focusing Workflow Improved** - You can now double-click on the aim assist button to have the software automatically zoom into a single marker near the center of the camera view. This makes the focusing process a lot easier to accomplish for a single person.
  * **New and Improved Preset Context Menu Options** - Right clicking devices now gives more helpful preset options for all device types. This is exceptionally helpful for setting up Movement Sciences devices.
  * Updated the prime color preset settings for better out of the box visuals.
  * Added a click-and-hold option for changing camera modes in the Devices pane.
  * Updated designs for creating device groups in the devices pane.
* **Graphs Pane**
  * **Graphs Work in both Live/Edit** - All graphs now work in both Live and Edit mode, except for the gaps view.
  * **Live Marker Graphs** - Added the ability to graph marker positions in Live mode.
  * Updated the default graph layouts to work with markers, rigid bodies, or force plates.
  * Double-clicking in the graphs no longer zooms out.
  * Added the ability to clone the current layout.
  * Updated the default Rigid Body graph layout.
* **Streaming**
  * **Unicast Data Subscription** - Added the ability for a given steaming client to configure the tracking data that it receives. For example, each client can now subscribe only to specific rigid bodies and receive tracking data over unicast; making the streaming faster for each client. This change can help cut down the latency for large VR installations.
  * Added a streaming option to toggle the device data, which includes data for force plate, DAQ, EMG, and glove devices.
  * The bitstream version can now be configured to work with multiple clients running different versions of NatNet.
  * Added more informative error messages when Motive tries to connect to a client with wrong settings, and improved connection reliability.
  * Increase the maximum number of force plates in the data stream to 32.
  * Added the ability to query some camera location information.
  * Added the ability for NatNet to get/set the frame rate of Motive.
  * Added support for remotely getting, and setting, properties that have vector3/4 types, such as colors.
  * Added the ability to recalibrate 6RB skeletons over NatNet.
  * Added the ability to reset the orientation of rigid bodies over NatNet.
  * Added a Live/Edit param to sFrameOfMocapData.
  * Added the ability to query the start and end time/timecode for a loaded take over NatNet.
  * Increaseed the keep alive timer from 5 seconds to 10 seconds for unicast connections on noisy networks.
* **Motive API**
  * **Calibrate using the Motive API** - Added the ability to perform a system calibration using just the Motive API.
  * Added the ability to query camera properties.
  * Added methods to retrieve ray length and number of rays contributing to a marker in the Motive API
  * Added a frame buffering mechanism to prevent frame drops when running the system at a higher frame rate now allowed by Prime<sup>x</sup> cameras.
  * Standardized functions that return NPRESULT to use enum values instead of #defines.
* **NMotive**
  * **Added Entertainment Script** - Added a sample script for entertainment customers cleaning up skeleton tracking data; this works with the baseline/core skeletons without modification.
  * Added several features around working with takes containing audio data including the ability to export, check if audio data exists, and remove audio data from a take.
  * Added a sample script that performs a pattern-based fill on all baseline/core skeletons in the take.
  * Added the ability to export marker nulls using the FBX Exporter class.
  * Exposed an option to export the timecode.
  * Added the ability to trim takes and added an example script to demonstrate.
  * Updated the icon and copyright notes for the Batch Processor.
* **Asset Definitions**
  * **Merged Some Rigid Body and Skeleton Properties** - Started the process of giving all assets a similar list of properties and standardizing the underlying asset definition.
  * **Added Axis-Specific Dampening** - This allows rigid body assets to lock or dampen movement in a specific axis to simulate steady camera movements.
  * All skeletons containing hands now contain hand bones for use with Manus gloves.
  * The rigid body visual has been completely separated from the attached geometry function; each can be configured independently.
  * Renamed the Active property for all assets to Enabled to avoid confusion with the Active marker terminology.
  * Updated the marker stick models for all of the standard skeleton models to make labeling easier.
  * We now use the terminology "Asset Model Markers" to refer to the expected location of markers defined by assets.
  * Added hotkeys to Select Parent Node and Select Child Node for an asset definition.
  * Removed the 20 marker limit for rigid bodies.
  * Added a property to apply a manual offset to the wrist location of a skeleton on creation.
* **Assets Pane**
  * **Added a Streaming ID Column** - Added a Streaming ID column that can be used to sort and modify rigid bodies according to their streaming ID values.
  * Added a "..." menu option for deleting all assets.
  * Rename the Active column to Enabled for clarity with other products.
  * Added a notification that lets the user know when loading a rigid body asset into an instance of Motive that already has a rigid body with an overlapping Streaming ID.
  * Added columns for the Active Tag ID and RF Channel properties for rigid body assets.
  * Renamed the marker color/stick context menu options to match the new Constraints pane.
* **Builder Pane**
  * **Improved Creation Properties** - Added the ability to select the creation color through the create tab of the Builder pane. Improved the skeleton creation defaults by defaulting to a random color and avatar visual unless otherwise specified.
  * **Added Marker Visuals and Legend** - Added 3D visuals showing calibration markers and markers that are required to use active markers for skeletons. Added a legend explaining what each of the marker visuals means in the Builder pane's skeleton creation viewport.
  * **Marker Sticks** - Added the ability to modify marker sticks using the Builder pane.
  * Simplified the Builder pane by replacing the Rigid Body / Skeleton icons at the bottom with a Type dropdown.
  * Updated the list of skeleton markersets. Added active finger markersets, removed markersets that are rarely used, and rearranged the groups also.
  * Enhanced the Location and Orientation tools to be more compact.
  * Updated the external pivot calibration tool to support the pivot calibration of Vive/Index controllers.
  * Mouse actions in the Builder pane now match the 3D viewport when actions are modified in the Settings window.
  * Corrected the position of the top\_shoulder markers for the Baseline skeletons shown in the placement guide.
  * Updated the probe creation/calibration tool to work in the 2D playback mode.
  * Updated the Core 50 marker placement guide to prevent symmetric hand marker placement.
  * An existing rigid body asset can now be selected and refined directly from the creation tab.
  * Renamed the Edit tab to be the Modify tab.
  * Asset Model Markers can now be selected and removed directly using the Selected Marker(s) tool in the builder pane.
  * Added a way to exit the External Pivot Alignment tool.
  * Removed the External Pivot Alignment tool.
  * Added left and right hand skeletons.

#### **Fixes** <a href="#text-new-features-0" id="text-new-features-0"></a>

* Fix for a bug where the 3D gizmo tool would disappear when the model replace property was turned on.
* Fix for a bug where the OBJ file would disappear when switching between layouts.
* Fix for an issue with tooltips appearing in odd locations while scrolling.
* Fix for an issue where trimming a take doesn't also trim the device channel data.
* Fix for a bug where the wand measurement tool doesn't work with non-500mm wands.
* Fix for an issue where the application hangs when holding down the spacebar while in the Bounce playback mode.
* Fix for the spacebar hotkey not respecting the Reverse option in the Control Deck.
* Removed the Orientation History visualization property for rigid bodies.
* Fixed a small style issue with the notes column in the Data pane.
* Fixed an issue where takes with "..." at the end of the file name don't record correctly.
* Fix for an issue with corrupted files crashing Motive.
* Fix for ocasional dropped audio samples when using WASAPI drivers with external audio card.
* **Movement Sciences**
  * Force plate locations no longer adjust when calibrating.
  * Fixed an issue with the external synchronization where some of the system rate values locked to a floating-point number instead of an integer.
  * Fixed an issue where sampling rates on Bertec force plates would not be correctly loaded on startup in some cases.
  * Fixed an issue where the order of DAQ channels would get messed up when enabling/disabling channels in the graphs pane.
* **Viewer**
  * Fixed an issue where skeleton bones can't be selected unless using drag-select; now a single-click properly selects bones.
  * Fixed an issue where selected cameras wouldn't show a yellow border in the cameras views on 4K monitors.
  * Fix for a bug where disabled cameras can still be selected in the 3D view.
* **Exporters**
  * Fix for the CSV exporter not associating correct motion capture frames to the exported force plate data for some take files.
  * Fix for the C3D exporter putting a colon in incorrect locations with assets that contain an underscore (\_) in their name.
  * Fix for the C3D exporter where DAQ channels would not number correctly if they were not the first few channels.
  * Fix for some naming mismatches in the C3D data export when using a large number of devices.
  * Fix for incorrect sampling rate property in the C3D header when using high sampling rates.
  * Fixed a gimbal lock issue when exporting recorded data into FBX binary from specific takes.
  * Fixed an issue where Motive was unable to export some types of audio files.
* **Motive API**
  * Made the Motive API marker sample run without any additional configuration.
  * Fixed some issues with loading profiles and calibration files into the Motive API.
  * Removed a few references to internally used environment variables from the Motive API.
  * Fix for an issue where the Motive API does not correctly save/load the continuous calibration state through the profile.
  * Fixed an occasional issue where the Motive API markers sample would crash on exit.
* **Streaming**
  * Fix for remote record triggering not working when the eSync is put into a ready state.
  * Fix for negative streaming ID values in some instances.
  * Fix for incorrect Streaming Duplicate Frame error messages when streaming via unicast to multiple clients on the same computer.
  * Fixed an issue where some labeled marker tags were not working correctly.

#### **Known Issues** <a href="#text-new-features-0" id="text-new-features-0"></a>

* **Force Plates:** Force plate data will not be recorded when camera frames are dropped.
* **Cameras:** Cameras operating in Reference video modes (including MJPEG, Grayscale, and Color Video) may not run at a faster frame rate than the cameras in Tracking video modes.
* **Files:** Take files recorded in Motive versions older than 1.7 might need to be loaded into Motive 2.0 before loading them into Motive 3.0.

</details>
