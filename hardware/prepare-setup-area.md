# Prepare Setup Area

Before setting up a motion capture system, choose a suitable setup area and prepare it in order to achieve the best tracking performance. This page highlights some of the considerations to make when preparing the setup area for general tracking applications. Note that this page provides just general recommendations and these could vary depending on the size of a system or purpose of the capture.

## Indoor Tracking

### Pick a Setup Area

First of all, pick a place to set up the capture volume.

**Setup Area Size**

* System setup area depends on the size of the mocap system and how the cameras are positioned. To get a general idea, check out the [Build Your Own](http://www.optitrack.com/systems/) feature on our website.
* Make sure there is plenty of room for setting up the cameras. It is usually beneficial to have extra space in case the system setup needs to be altered. Also, pick an area where there is enough vertical spacing as well. Setting up the cameras at a high elevation is beneficial because it gives wider lines of sight for the cameras, providing a better coverage of the capture volume.

**Minimal Foot Traffic**

* After camera system calibration, the system should remain unaltered in order to maintain the calibration quality. Physical contacts on cameras could change the setup, requiring it to be re-calibrated. To prevent such cases, pick a space where there is only minimal foot traffic.

**Flooring**

* Avoid reflective flooring. The IR lights from the cameras could be reflected by it and interfere with tracking. If this is inevitable, consider covering the floor with surface mats to prevent the reflections.
* Avoid flexible or deformable flooring; such flooring can negatively impact your system's calibration.

![Rubber mats for covering reflective flooring.](<../.gitbook/assets/image (350).png>)

### Reducing IR Interference

For the best tracking performance, minimize ambient light interference within the setup area. The motion capture cameras track the markers by detecting reflected infrared light and any extraneous IR lights that exist within the capture volume could interfere with the tracking.

* **Sunlight:** Block any open windows that might let sunlight in. Sunlight contains wavelength within the IR spectrum and could interfere with the cameras.
* **IR Light sources:** Remove any unnecessary lights in IR wavelength range from the capture volume. IR lights could be emitted from sources such as incandescent, halogen, and high-pressure sodium lights or any other IR based devices.

All cameras are equipped with IR filters, so extraneous lights outside of the infrared spectrum (e.g. fluorescent lights) will not interfere with the cameras. IR lights that cannot be removed or blocked from the setup area can be masked in Motive using the [Masking Tools](../motive/calibration/) during the system calibration. However, this feature completely discards image data within the masked regions and an overuse of it could negatively impact tracking. Thus, it is best to physically remove the object whenever possible.

![Blocking the sunlight](<../.gitbook/assets/image (503).png>)

### IR White Objects

Dark-colored objects absorb most of the visible light, however, it does not mean that they absorb the IR lights as well. Therefore, the color of the material is not a good way of determining whether an object will be visible within the IR spectrum. Some materials will look dark to human eyes but appear bright white on the IR cameras. If these items are placed within the tracking volume, they could introduce extraneous reconstructions.

Since you already have the IR cameras in hand, use one of the cameras to check whether there are IR white materials within the volume. If there are, move them out of the volume or cover them up.

### Obstacles

* Remove any unnecessary obstacles out of the capture volume since they could block cameras' view and prevent them from tracking the markers. Leave only the items that are necessary for the capture.
* Remove reflective objects nearby or within the setup area since IR illumination from the cameras could be reflected by them. You can also use non-reflective tapes to cover the reflective parts.

## Outdoor Tracking

Prime 41 and Prime 17W cameras are equipped with powerful IR LED rings which enables tracking outdoors, even under the presence of some extraneous IR lights. The strong illumination from the Prime 41 cameras allows a mocap system to better distinguish marker reflections from extraneous illuminations. System settings and camera placements may need to be adjusted for outdoor tracking applications.

Please read through the [Outdoor Tracking Setup](../quick-start-guides/quick-start-guide-outdoor-tracking-setup.md) page for more information.
