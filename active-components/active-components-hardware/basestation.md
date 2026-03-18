# BaseStation

The BaseStation is the active hardware component that links other active components to Motive. Using a radio frequency channel (RF channel) between 11-26, the BaseStation synchronizes OptiTrack cameras with Active Tags and Pucks. Once the BaseStation has the signal from the active component, it then sends that data to the Motive computer along the camera network. This allows Motive to recognize Active Pucks and Tags even with significant occlusion of the LED markers compared to passive markers.

If you use Active Tags or Pucks, at least one BaseStation is required per tracking system.

For larger volumes, the approximate range from BaseStation to Tags/Pucks is 100’.

For more information regarding the specifications of the BaseStation, please visit our [Support ](https://optitrack.com/support/accessories/active-basestation.html)section of the OptiTrack website.

![](<../../.gitbook/assets/image (2) (3) (1) (1) (1).png>)

## **BaseStation LEDs**

_Note: Behavior of the LEDs on the BaseStation is subject to be changed._

* **Communication Indicator LED:** When the BaseStation is successfully sending out the data and communicating with the Active Pucks, the LED closest to the antenna will blink in green. If this LED lights up in red, it indicates that the BaseStation has failed to establish a connection with Motive.
* **Interference Indicator LED:** The middle LED is an indicator for determining whether there are other signal-traffics on the respective radio channel and PAN ID that might be interfering with the active components. This LED should stay dark in order for the active marker system to work properly. If it flashes in red, consider switching both the channel and PAN ID on all of the active components.
* **Power Indicator LED:** The LED located at the corner indicates power for the BaseStation. This LED may be disabled on BaseStations with the latest firmware, but on older BaseStations, this LED may light up in red to indicate power.
