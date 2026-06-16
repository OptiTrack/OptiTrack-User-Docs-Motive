---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/hardware/aiming-and-focusing
---

# Aiming and Focusing

In order to ensure that every camera in a mocap system takes full advantage of its capability, they need to be focused and aimed at the target tracking volume. This page includes detailed instructions on how to adjust the focus and aim of each camera for an optimal motion capture. OptiTrack cameras are focused at infinity by default, which is generally sufficient for common tracking applications. However, we recommend users always double-check the camera view and make sure the captured images are focused when first setting up the system. Obtaining best quality image is very important as 3D data is derived from the captured images.

## General Steps

{% embed url="https://www.youtube.com/watch?t=94s&v=aK1cpr6ShPE" %}

1. Make sure that the [camera placement](camera-placement.md) is appropriate for your application.
2. Pick a camera to adjust the aim and focus.
3. Set the camera to the raw grayscale video mode (in Motive) and increase the camera exposure to capture the brightest image (These steps are accomplished by the [Aim Assist Button](aiming-and-focusing.md) on featured cameras).
4. Place one or more reflective markers in the tracking volume.
5. Carefully adjust the camera angle while monitoring the Camera Preview so that the desired capture volume is included within the camera coverage.
6. Within the [Camera Preview](../motive-ui-panes/viewport.md) in Motive, zoom in on one of the markers so that it fills the frame.
7. Adjust the focus (detailed instruction given below) so that the captured image is resolved as clearly as possible.
8. Repeat above steps for other cameras in the system.

## Aim Assist Button

Adjusting aim with a single person can be difficult because the user will have to run back and forth from the camera and the host PC in order to adjust the camera angle and monitor the 2D view at the same time. OptiTrack cameras featuring the Aim Assist button (Prime series and Flex 13) make this aiming process easier. With just one button-click, the user can set the camera to the grayscale mode and the exposure value to its optimal setting for adjusting both aim and focus. Fit the capture volume within the vertical and horizontal range shown by the virtual crosshairs that appear when Aim Assist mode is on. With this feature, the single-user no longer needs to go back to the host PC to choose cameras and change their settings. Settings for Aim Assist buttons are available from [Application Settings](../motive-ui-panes/settings/) pane.

## Adjusting Aiming

![Cameras — shows only one side — aimed to cover the main target volume.](<../.gitbook/assets/image (279).png>)

After all the cameras are placed at correct locations, they need to be properly aimed in order to fully utilize their capture coverage. In general, all cameras need to be aimed at the target capture volume where markers will be tracked. While cameras are still attached to the mounting structure, carefully adjust the camera clamp so that the camera field of view (FOV) is directed at the capture region. Refer to 2D camera views from the [Camera Preview](../motive-ui-panes/viewport.md) pane to ensure that each camera view covers the desired capture region.

![Grayscale camera view.](<../.gitbook/assets/image (654).png>)

## Adjusting Focus

All OptiTrack cameras (except the Duo 3 and Trio 3 tracking bars) can be re-focused to optimize image clarity at any distance within the tracking range. Change the camera mode to raw grayscale mode and adjust the camera setting, increase exposure and LED setting, to capture the brightest image. Zoom onto one of the reflective markers in the capture volume and check clarity of the image. Then, adjust the camera focus and find the point where the marker image is best resolved. The following images show some examples.

{% hint style="info" %}
**Auto-zoom using Aim Assist button**

Double-click on the aim assist button to have the software automatically zoom into a single marker near the center of the camera view. This makes the focusing process easier to accomplish for a single person.
{% endhint %}

![Out of Focus](<../.gitbook/assets/image (660).png>) ![Moderately Focused](<../.gitbook/assets/image (492) (1).png>) ![In-Focus](<../.gitbook/assets/image (284).png>)

### How to Change Focus

{% tabs %}
{% tab title="PrimeX 41/PrimeX 22" %}
**PrimeX 41 and PrimeX 22**

For PrimeX 41 and 22 models, camera focus can be adjusted by rotating the focus ring on the lens body, which can be accessed at the center of the camera. The front ring on the lens changes the focus of the camera, and the rear ring adjusts the F-stop of the lens. In most cases, it is beneficial to set the f-stop low to have the aperture at its maximum size for capturing the brightest image. Carefully rotate the focus ring while monitoring the 2D grayscale camera view for image clarity. Once the focus and f-stop have been optimized on the lens, it should be locked down by tightening the set screw. In default configuration, PrimeX 41 cameras are equipped with 12mm F#1.8 lens, and the PrimeX 22 cameras are equipped with 6.8mm F#1.6 lens.

![Focus and f-stop rung on the PrimeX 41 lens](<../.gitbook/assets/image (504).png>)
{% endtab %}

{% tab title="Prime 17W and 41" %}
**Prime 17W and 41\***

For Prime 17W and 41 models, camera focus can be adjusted by rotating the focus ring on the lens body, which can be accessed at the center of the camera. The front ring on the Prime 41 lens changes the focus of the camera, while the rear ring on the Prime 17W adjusts its focus. Set the aperture at its maximum size in order to capture the brightest image. For the Prime 41, the aperture ring is located at the rear of the lens body, where the Prime 17W aperture ring is located at the front. Carefully rotate the focus ring while monitoring the 2D grayscale camera view for image clarity. Align the mark with the infinity symbol when setting the focus back to infinity. Once the focus has been optimized, it should be locked down by tightening the set screw.

**\*Legacy camera models**

![](<../.gitbook/assets/image (657).png>)
{% endtab %}

{% tab title="PrimeX 13/PrimeX 13W" %}
**PrimeX 13 and 13W, and Prime 13\* and 13W\***

PrimeX 13 and PrimeX 13W use M12 lenses and cameras can be focused using custom focus tools to rotate the lens body. Focusing tools can be purchased on [OptiTrack’s Lens Accessories page](http://www.optitrack.com/products/lens-accessories-filters/), and they clip onto the camera lens and rotates it without opening the camera housing. It could be beneficial to lower the LED illumination to minimize reflections from the adjusting hand.

\*Legacy camera models

![Focus tool for PrimeX 13.](<../.gitbook/assets/image (634).png>) ![Focus tool for Prime 13W.](<../.gitbook/assets/image (496).png>)
{% endtab %}

{% tab title="SlimX 13" %}
**Slim Series**

SlimX 13 cameras also feature M12 lenses. The camera focus can be easily adjusted by rotating the lens without the need to remove the housing. Slim cameras support multiple lens types, including third-party lenses so focus techniques will vary. Refer to the lens type to determine how to proceed. (In general, M12 lenses will be focused by rotating the lens body, while C and CS lenses will be focused by rotating the focus ring).
{% endtab %}
{% endtabs %}
