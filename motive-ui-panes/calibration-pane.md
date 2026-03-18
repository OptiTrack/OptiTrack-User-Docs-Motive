# Calibration Pane

The Calibration pane is used to calibrate the capture volume for accurate tracking. This pane is typically a default pane when first starting Motive. Otherwise, you can access this pane either via the command bar View > Calibration, or the ![](<../.gitbook/assets/image (1050).png>) icon. This page provides instructions and tips on how to efficiently use all the functionalities of the Calibration pane.

## Overview

Calibration is essential for high quality optical motion capture systems. During calibration, the system computes position and orientation of each camera and amounts of distortions in captured images, and they are used constructs a 3D capture volume in Motive. This is done by observing 2D images from multiple synchronized cameras and associating the position of known calibration markers from each camera through triangulation.

Please note that if there is any change in a camera setup over the course of capture, the system must be recalibrated to accommodate for changes. Moreover, even if setups are not altered, calibration accuracy may naturally deteriorate over time due to ambient factors, such as more or less light entering the capture volume as the day progresses and fluctuation in temperature. Thus, for accurate results, it is recommended to periodically calibrate the system.

To learn more about Calibration outside of the pane functionality, please visit the [Calibration ](../motive/calibration/)page on this wiki.

## Starting a New Calibration

![The Calibration pane upon initial startup of Motive or when creating a new calibration.](<../.gitbook/assets/image (1089).png>)

### New Calibration

To begin a new Calibration click New Calibration

### Load Calibration

* If you already have a previous calibration you wish to load, click Load Calibration.
* This will open the Calibrations folder.
* From here you can choose a Calibration you wish to load.
* Each time you create a new calibration in Motive, it will automatically save in the Calibrations folder.

![Calibrations Folder in Motive.](<../.gitbook/assets/image (1107).png>)

### Open Calibration Folder

If you wish to view calibrations in File Explorer, click the Open Calibration Folder. You cannot load a calibration from this window. The purpose of opening the Calibration folder is to manipulate the files separately from Motive. For instance, you may want to delete old Calibrations that are no longer relevant to your current camera setup.

![Calibration Folder in File Explorer.](<../.gitbook/assets/image (1073).png>)

### ![](<../.gitbook/assets/image (1100).png>) Button

This icon will open the [Calibration ](../motive/calibration/)page in the wiki for reference.

### Place your cameras

This link will direct you to the [Camera Placement](../hardware/camera-placement.md) page in the wiki for reference.

### Aim and Focus

This link will direct you to the [Aiming and Focusing](../hardware/aiming-and-focusing.md) page in the wiki for reference.

## Masking

Before performing system calibration, all extraneous reflections or unnecessary markers should ideally be removed or covered so that they are not seen by the cameras. If this is not possible, extraneous reflections can be ignored by applying _masks_ over them in Motive.

When the cameras detect reflections in their view, it will be indicated with a warning sign [![Calibration Warning 30.png](https://v30.wiki.optitrack.com/images/3/34/Calibration_Warning_30.png)](https://v30.wiki.optitrack.com/index.php?title=File:Calibration_Warning_30.png) to alert which cameras are seeing reflections; for Prime series cameras, the indicator LED ring will also light up in white.

Masks can be applied by clicking _Mask_ in the calibration pane, and it will apply red masks over all of the reflections detected in the 2D camera view. Once masked, the pixels in the masked regions will entirely be filtered out from the data. Please note that Masks get applied additively, so if there are already masks applied in the camera view, clear them out first before applying a new one.

![](<../.gitbook/assets/image (1037).png>)

### Clear Masks

* If masks were previously applied during another calibration or manually via the [2D viewport](viewport.md#camera-masking-settings), you have the option of clearing these masks.
* This will help remove masks that are no longer useful or need to be reset in order to cover new reflections.

### Cancel

This button will allow you go back to the Calibration pane's default window.

### Mask

* This button will auto-apply masks to objects in the capture volume.
* You can always click Clear Masks then Mask again to reapply new Masks if you're unhappy with the initial masking or to reset the masks from a previous calibration.

### Continue

This button will continue with the Calibration process with the masks applied.

## Wand the Volume

![](<../.gitbook/assets/image (1090).png>)

### Calibration Type:

Full

* When Full is chosen from the dropdown, this will allow for a full volume calibration where each camera is used for the calibration.

Refine

* When Refine is chosen from the dropdown, this will allow for only specific cameras to be calibrated. For more information regarding Refine calibrations please visit our [Calibration ](../motive/calibration/#calibration-types)wiki page.

### Wand:

This dropdown allows you to select which wand you'll be using to calibrate your volume. Please refer to the [Wand Types](../motive/calibration/#wand-types) section on the [Calibration ](../motive/calibration/)page of this wiki.

### Cancel

This button allows you to go back to the masking window incase you need to make changes to your masks.

### Start Wanding

This button will initiate the calibration with all previous settings applied.

Once you begin to wand the camera squares in the Calibration pane will turn dark green when a camera has begun successfully collecting samples, but still does not have a sufficient amount of samples collected. Once there is a sufficient amount of samples collected the square will turn light green. Once all the camera squares have filled in light green the Start Calculating button will be enabled.

![Camera squares changing from grey (no samples taken) to dark green (some samples taken) to light green (sufficient amount of samples taken).](<../.gitbook/assets/image (1079).png>)

#### Show list

This will show the amount of samples a camera has captured. Typically you want around 1,000-4,000 samples. Samples above this threshold are unnecessary and can oftentimes be detrimental to a calibration's accuracy.

![Adequate samples collected for 3 cameras.](<../.gitbook/assets/image (1095).png>)

### Start Calculating

This button will start calculating the samples taken during the wanding stage. During this the camera squares will cycle through red, dark cyan, and light cyan.

#### Red

Calibration samples were Poor and have a high Mean Ray Error.

#### Light Red

#### Grey

Calibration samples are Good

#### Dark Cyan

Calibration samples are Excellent.

#### Light Cyan

Calibration samples are Exceptional.

![Successful calibration in Motive.](<../.gitbook/assets/image (171).png>)

## Setting the Ground Plane

![](<../.gitbook/assets/image (1043).png>)

### Type of Ground Plane

### Auto (default setting)

When chosen from the dropdown, Motive will automatically recognize the ground plane you are using.

#### Detected Device

On occasion Motive will recognize a ground plane as a different ground plane. When this occurs, you can choose the appropriate ground plane from the Detected Device's dropdown.

### Custom

You can create your own custom ground plane by positioning three markers in a right triangle shape. To refine the position, change the vertical offset (how far from the ground are the markers on its base.

![](<../.gitbook/assets/image (1085).png>)

### Rigid Body

It is also possible to create a ground plane from a Rigid Body. Select the Rigid Body you wish to use. Motive will use the pivot point of the Rigid Body as the ground plane.

### Refine Ground Plane

By toggling the white dot at the bottom of the Calibration pane, you can access the Refine Ground Plane window.

It is possible to refine the ground plane. To do this, you'll want to lay out additional markers in the capture volume. It is important to use markers of the same dimension and height for an accurate refinement. This allows Motive to make sure that the ground plane is level.

![](<../.gitbook/assets/image (1038).png>)

### Translate and Rotate

By further toggling the white dot at the bottom of the Calibration pane, you can access the Translate and Rotate window.

To further position the ground plane, you can manually enter translate and rotate values. This step is typically not necessary for an accurate ground plane placement.

![](<../.gitbook/assets/image (1068).png>)

## Continuous Calibration

### Enabled

This toggle enables [Continuous Calibration](../motive/calibration/continuous-calibration.md).

### Status

#### Idle

When the status is Idle, Motive is waiting to initiate continuous calibration.

#### Sampling

Motive is sampling the position of at least four markers.

#### Evaluating

Motive is calculating the newly acquired samples.

![](<../.gitbook/assets/image (1040).png>)

### Anchor Markers

By toggling the white dot at the bottom of the Calibration pane, you can switch to the anchor marker window.

Active anchor markers can be set up in Motive to further improve continuous calibration. When properly configured, anchor markers improve continuous calibration updates, especially on systems that consists of multiple sets of cameras that are separated into different tracking areas, by obstructions or walls, without camera view overlap. It also provides extra assurance that the global origin will not shift during each updates; although the continuous calibration feature itself already checks for this\_.\_

For more information regarding anchor markers, visit the [Anchor Marker Setup](../motive/calibration/continuous-calibration.md#anchor-marker-setup) section of this wiki.

![](<../.gitbook/assets/image (785).png>) ![](<../.gitbook/assets/image (187).png>)
