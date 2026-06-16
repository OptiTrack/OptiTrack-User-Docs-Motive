---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/movement-sciences/prime-color-camera-setup/prime-color-camera-setup-prime-color-fs-calibration
---

# Prime Color Camera Setup: Prime Color FS Calibration

In order to calibrate the color camera into the 3D capture volume, the Prime Color camera must be equipped with an IR filter switcher. Prime Color cameras without IR filter switcher cannot be calibrated, and can only be used as a reference camera to monitor the reference views in the [2D Camera View pane](../../motive-ui-panes/viewport.md#cameras-view) or in the [Cameras viewport](../../motive-ui-panes/viewport.md#cameras-view).

{% hint style="danger" %}
When loaded into Motive, Prime Color cameras without IR filter switcher will be hidden in the [3D viewport](../../motive-ui-panes/viewport.md#perspective-view). Only Prime Color FS cameras with the filter switcher will be shown in the 3D space.
{% endhint %}

### Prime Color FS Calibration

The Prime Color FS is equipped with a filter switcher that allows the cameras to detect in IR spectrum. The Prime Color FS can be calibrated into the 3D capture volume using an active calibration wand with the IR LEDs. Once calibrated, the color camera will be placed within the 3D viewport along with other tracking cameras, and 3D assets (markers, Rigid Bodies, Skeletons, cameras) can be overlaid as shown in the image.

To calibrate the camera, switch the Prime Color FS to the [Object mode](../../motive/camera-video-types.md) in the [Camera Preview](../../motive-ui-panes/viewport.md#cameras-view) pane. This will switch the Color camera to detect in the IR spectrum, and then use the active wand to follow the standard [Calibration](../../motive/calibration/) process. Once the calibration is finished, you can switch the camera back to the _Color Video Mode_.

![Reference video zoomed into a Rigid Body.](<../../.gitbook/assets/image (544).png>)

{% hint style="info" %}
**Active Wand:**

Currently, we only take custom orders for the active wands, but in the future, this will be available for sale. For additional questions about active wands, please [contact us](http://optitrack.com/contact/).
{% endhint %}
