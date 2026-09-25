---
description: >-
  This guide covers configuration of OptiTrack's OpenXR Plugin with a
  head-mounted device made by Varjo.
---

# OpenXR Plugin: Configure with a Varjo HMD

### Requirements

* Varjo Base
* Motive 3.3 or later
* OptiTrack OpenXR Plugin 1.3.0 or later

### Setup

* Complete the step called [Setting Up the OpenXR Plugin Config App](https://docs.optitrack.com/plugins/optitrack-openxr-plugin#setting-up-the-openxr-plugin-config-app) in the OptiTrack OpenXR Plugin guide.
*   Launch Varjo Base and access the Settings tab from the ribbon menu at the top of the application.

    * From this menu, navigate to the System tab in the side window.

    <figure><img src="../../.gitbook/assets/OpenXR Screen 01 Settings System.png" alt="The top left corner of the Varjo Base app with Settings and Systems highlighted."><figcaption></figcaption></figure>



    * Enable OpenVR and OpenXR using the switches on their menu items in the Compatibility section.

    <figure><img src="../../.gitbook/assets/OpenXR Screen 01 OpenVR OpenXR 01.jpg" alt="Varjo Base application Compatibility section with switches for OpenVR and OpenXR highlighted."><figcaption></figcaption></figure>

{% hint style="info" %}
**Note:** If you are using the Varjo OpenXR runtime, you do _not_ need to launch SteamVR to use the OptiTrack OpenXR plugin. This is the method we found most successful.

If you prefer to use SteamVR’s OpenXR runtime with your Varjo headset instead, you can do so by following the step called [SteamVR Setup](https://docs.optitrack.com/plugins/optitrack-openxr-plugin#steam-vr-setup) in the OptiTrack OpenXR Plugin guide. The settings in Varjo Base do not need to be adjusted.

When SteamVR is properly configured, the Compatibility section of the system settings in Varjo Base will look like the the image below.
{% endhint %}

<figure><img src="../../.gitbook/assets/SteamVR Compatibility.jpg" alt=""><figcaption></figcaption></figure>

* In the Compatibility section, under the OpenXR API layers menu item, press Open.

<figure><img src="../../.gitbook/assets/SteamVR Compatibility Open.jpg" alt=""><figcaption></figcaption></figure>

* Then, from the OpenXR API layers window, ensure the `XR_APILAYER_OPTITRACK_tracking_override` option is enabled.

<figure><img src="../../.gitbook/assets/OpenXR Screen 02 Enabled.jpg" alt="Varjo Base application, OpenXR API Layers section, with the XR_APIPLAYER_OPTITRACK_tracking_override option enabled."><figcaption></figcaption></figure>

* Return to the Headset tab from the ribbon menu at the top left corner of the application. The default startup screen should appear.
* The Varjo runtime is now configured with the OptiTrack OpenXR plugin.
