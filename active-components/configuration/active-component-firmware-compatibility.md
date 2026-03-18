# Active Component Firmware Compatibility

{% hint style="danger" %}
In most cases, you will not need to update the firmware on your Active components. The Active components you receive should work for your system without the need to update. In the event that you are advised to update your Active components, we strongly recommend doing so only under the guidance of a OptiTrack Support Engineer. Please contact [support](http://optitrack.com/support/) for instructions on how to update the firmware.
{% endhint %}

## Out of the Box

When you first receive your Active Tags and BaseStation they will be on firmware 1.1.0 unless otherwise setup with your Sales Engineer for very specific applications. Firmware version 1.1.0 is recommended for most applications. These will be RevG (revision G) for Active Tags and RevD for BaseStations. These should not need to be updated. Please contact [support](http://optitrack.com/support/) if you need assistance with your Active hardware.

{% hint style="info" %}
If your Active hardware is older than RevG for Active Tags and RevD for BaseStations, we recommend updating to RevG and RevD respectively.
{% endhint %}

## Additional Information

The information below is detailed information that is not intended for the average user. What you receive out of the box will work for the majority of applications based upon initial setup with a Sales Engineer.

### Firmware 1.x or above

* Active components that were shipped later than _September 2017_ uses the firmware 1.x or above.
* Requires Motive 2.0 Beta 2 or later versions.
* No longer requires eSync for synchronizing the BaseStation with the camera system.
* Support for user-defined camera framerates.
* The illumination time of active LEDs is synchronized to the camera exposure time.
* Allows changing the depth of illumination patterns, allowing a higher number of active markers to be actively labeled.
* Active tags with 1.x firmware and no IMU are compatible with BaseStations with 1.1.0 firmware (RevA, B, C, and D BaseStations are all compatible with 1.1.0 firmware)

## Advanced Versions

### Firmware 2.x

* RevA hardware version BaseStations are NOT compatible with 2.3.1 firmware.
* RevB, RevC, and RevD hardware version BaseStations are compatible with 2.3.1 firmware.
* IMU tags with 2.3.3 firmware are compatible with BaseStations with 2.3.1 firmware.

{% hint style="info" %}
- An IMU tag
  * Requires a BaseStation (RevB, RevC, RevD) with firmware 2.3.1.
  * Do NOT use with a BaseStation with 1.1.0 firmware.
- A non-IMU tag
  * Requires a BaseStation (RevA, RevB, RevC, RevD) with firmware 1.1.0
  * NOT compatible with a BaseStation with 2.3.1 firmware.

Essentially, if an Active Tag has the same firmware as a BaseStation it will be compatible with a few exceptions. For example, if you have an Active Tag with 1.x firmware and a BaseStation with 1.x firmware, they will be compatible.
{% endhint %}

## Firmware Compatibility

**Firmware Compatibility Chart**

Below is a chart to see which versions are compatible with which BaseStations and Active Tags/Pucks. Essentially, it is a one-to-one correlation between Active hardware and firmware versions with some exceptions. For Active Tags specifically, it boils down to: if it doesn't have an IMU then it's compatible with 1.x. If it has the first version of an IMU, then it is compatible with 2.x. And, if it has an upgraded IMU, then it is compatible with 3.x.

{% tabs %}
{% tab title="BaseStation Compatibility Flowchart" %}
![Click image to enlarge.](<../../.gitbook/assets/image (713).png>)
{% endtab %}

{% tab title="Active Tags and Pucks Compatibility Flowchart" %}
![Click image to enlarge.](<../../.gitbook/assets/image (231).png>)
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**BaseStation and Active Tag compatibility Simplified**

If you have a 1.x BaseStation you would use it with a 1.x Active Tag/Puck, if you have a 2.x Active Tag/Puck you would use it with a 2.x BaseStation and so on. The exception being that a 2.x BaseStation is compatible with both 2.x and 3.x Active Tags/Pucks.
{% endhint %}

## Archived Versions

These versions are outdated and no longer supported.

### Firmware v0.8

* Active components that were shipped prior to _September 2017_ uses the firmware v0.8.
* v0.8 BaseStation works only with v0.8 Tags.
* Firmware v0.8 requires an eSync to synchronize the BaseStation and the mocap system together.
* Whenever v0.8 BaseStation is power cycled, all of the v0.8 Tags must be power cycled as well.
* v0.8 BaseStation is not compatible with v1.0 Tags

### Using v0.8 Tags with v1.0 BaseStations

* v0.8 Tags needs to be power cycled each time you close and relaunch Motive.
* v0.8 Tags needs to be power cycled each time system frame rate has been changed in Motive.
