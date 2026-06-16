---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/markers
---

# Markers

OptiTrack motion capture systems can use both passive and active markers as indicators for 3D position and orientation. An appropriate marker setup is essential for both tracking the quality and reliability of captured data. All markers must be properly placed and must remain securely attached to surfaces throughout the capture. If any markers are taken off or moved, they will become unlabeled from the Marker Set and will stop contributing to the tracking of the attached object. In addition to marker placements, marker counts and specifications (sizes, circularity, and reflectivity) also influence the tracking quality. Passive (retroreflective) markers need to have well-maintained retroreflective surfaces in order to fully reflect the IR light back to the camera. Active (LED) markers must be properly configured and synchronized with the system.

## Retroreflective Markers

OptiTrack cameras track any surfaces covered with retroreflective material, which is designed to reflect incoming light back to its source. IR light emitted from the camera is reflected by passive markers and detected by the camera’s sensor. Then, the captured reflections are used to calculate the 2D marker position, which is used by Motive to compute 3D position through reconstruction. Depending on which markers are used (size, shape, etc.) you may want to adjust the camera filter parameters from the _Live Pipeline_ settings in [Application Settings](../motive-ui-panes/settings/settings-live-pipeline.md).

#### **Marker Size**

The size of markers affects visibility. Larger markers stand out in the camera view and can be tracked at longer distances, but they are less suitable for tracking fine movements or small objects. In contrast, smaller markers are beneficial for precise tracking (e.g. facial tracking and microvolume tracking), but have difficulty being tracked at long distances or in restricted settings and are more likely to be occluded during capture. Choose appropriate marker sizes to optimize the tracking for different applications.

#### **Circularity**

If you wish to track non-spherical retroreflective surfaces, lower the Circularity value in [2D object filter](../motive-ui-panes/settings/) in the application settings. This adjusts the circle filter threshold and non-circular reflections can also be considered as markers. However, keep in mind that this will lower the filtering threshold for extraneous reflections as well. If you wish to track non-spherical retroreflective surfaces, lower the Circularity value from the [cameras tab](../motive-ui-panes/settings/) in the application settings.

![2D reflections filtered by the Size and Roundness (circularity) filter](<../.gitbook/assets/image (549).png>)

#### **Worn markers**

All markers need to have a well-maintained retroreflective surface. Every marker must satisfy the brightness _Threshold_ defined from the [camera properties](../motive-ui-panes/properties-pane/properties-pane-camera.md) to be recognized in Motive. Worn markers with damaged retroreflective surfaces will appear to a dimmer image in the camera view, and the tracking may be limited.

{% hint style="info" %}
**Pixel Inspector:** You can analyze the brightness of pixels in each camera view by using the pixel inspector, which can be enabled from the [Application Settings](../motive-ui-panes/settings/).
{% endhint %}

{% hint style="info" %}
Please contact our [Sales team](https://optitrack.com/contact/) to decide which markers will suit your needs.
{% endhint %}

## Custom Markers

***

OptiTrack cameras can track any surface covered with retro-reflective material. For best results, markers should be completely spherical with a smooth and clean surface. Hemispherical or flat markers (e.g. retro-reflective tape on a flat surface) can be tracked effectively from straight on, but when viewed from an angle, they will produce a less accurate centroid calculation. Hence, non-spherical markers will have a less trackable range of motion when compared to tracking fully spherical markers.

## Active Markers

### OptiTrack Active Markers

OptiTrack's active solution provides advanced tracking of IR LED markers to accomplish the best tracking results. This allows each marker to be labeled individually. Please refer to the [Active Marker Tracking](../active-classic/active-marker-tracking/) page for more information.

### Custom Active Markers

![Ultra Wide Angle 850 nm LEDs](<../.gitbook/assets/image (680).png>)

Active (LED) markers can also be tracked with OptiTrack cameras when properly configured. We recommend using OptiTrack’s Ultra Wide Angle 850nm LEDs for active LED tracking applications. If third-party LEDs are used, their illumination wavelength should be at 850nm for best results. Otherwise, light from the LED will be filtered by the band-pass filter.

If your application requires tracking LEDs outside of the 850nm wavelength, the OptiTrack camera should not be equipped with the 850nm band-pass filter, as it will cut off any illumination above or below the 850nm wavelength. An alternative solution is to use the 700nm short-pass filter (for passing illumination in the visible spectrum) and the 800nm long-pass filter (for passing illumination in the IR spectrum). If the camera is not equipped with the filter, the Filter Switcher add-on is available for purchase at our [webstore](http://optitrack.com/products/motion-capture-markers/#led1010). There are also other important considerations when incorporating active markers in Motive:

* Place a spherical diffuser around each LED marker to increase the illumination angle. This will improve the tracking since bare LED bulbs have limited illumination angles due to their narrow beamwidth. Even with wide-angle LEDs, the lighting coverage of bare LED bulbs will be insufficient for the cameras to track the markers at an angle.
* If an LED-based marker system will be strobed (to increase range, offset groups of LEDs, etc.), it is important to synchronize their strobes with the camera system. If you require a LED synchronization solution, please contact one of our [Sales Engineers](http://optitrack.com/contact/) to learn more about OptiTrack’s RF-based LED synchronizer.
* Many applications that require active LEDs for tracking (e.g. very large setups with long distances from a camera to a marker) will also require active LEDs during calibration to ensure sufficient overlap in-camera samples during the wanding process. We recommend using OptiTrack’s Wireless Active LED Calibration Wand for best results in these types of applications. Please contact one of our Sales Engineers to order this calibration accessory.

## Marker Placement

Proper marker placement is vital for quality of motion capture data because each marker on a tracked subject is used as indicators for both position and orientation. When an asset (a Rigid Body or Skeleton) is created in Motive, its unique spatial relationships of the markers are calibrated and recorded. Then, the recorded information is used to recognize the markers in the corresponding asset during the [auto-labeling](data-recording/data-types.md) process. For best tracking results, when multiple subjects with a similar shape are involved in the capture, it is necessary to offset their marker placements to introduce the **asymmetry** and avoid the congruency.

Read more about marker placements from the [Rigid Body Tracking](rigid-body-tracking/) page and the [Skeleton Tracking](skeleton-tracking.md) page.

{% hint style="info" %}
**Asymmetry**

Asymmetry is the key to avoiding the congruency for tracking multiple Marker Sets. When there are more than one similar marker arrangements in the volume, marker labels may be confused. Thus, it is beneficial to place segment makers — joint markers must always be placed on anatomical landmarks — in asymmetrical positions for similar Rigid Bodies and Skeletal segments. This provides a clear distinction between two similar arrangements. Furthermore, avoid placing markers in a symmetrical shape within the segment as well. For example, a perfect square marker arrangement will have ambiguous orientation and frequent mislabels may occur throughout the capture. Instead, follow the rule of thumb of placing the less critical markers in asymmetrical arrangements.
{% endhint %}

### Marker Bases and Adhesives

Prepare the markers and attach them on the subject, a Rigid Body or a person. Minimize extraneous reflections by covering shiny surfaces with non-reflective tapes. Then, securely attach the markers to the subject using enough adhesives suitable for the surface. There are various types of adhesives and marker bases available on our [webstore](http://optitrack.com/products/motion-capture-markers/) for attaching the marker: Acrylic, Rubber, Skin adhesive, and Velcro. Multiple types of marker bases are also available: carbon fiber filled bases, Velcro bases, and snap-on plastic bases.
