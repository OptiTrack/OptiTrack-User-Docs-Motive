# Active Puck

This page provides additional information for the Active pucks and instructions on how to use them.

## Active Markers

### LED Specification

The following specification applies for active IR LEDs on both the Tags and the Pucks.

* 850 nm IR spectrum.
* 8 LEDs with removable diffusers (9.5mm, 3/8", diameter) on four corner LED locations
* Illuminations synchronized with camera exposures
* Illumination angle:
  * With Diffuser: ±135°-Bare LED without diffuser: ±70°

## Active Puck

### Basic Specs

| Spec                 | Description                                                                                                                                                                                                                                                                                                                                                                               |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Puck Body Dimensions | <p><strong>Dimensions without diffusers</strong></p><ul><li>Width: 96mm (~3.75”)</li><li>Length: 96mm (~3.75”)</li><li>Height: 20mm (~0.75”)</li></ul><p><strong>Dimensions with diffusers</strong></p><ul><li>Width: 104mm (~4.10”)</li><li>Length: 104mm (~4.10”</li><li>Height: 20mm (~0.75”)</li></ul>                                                                                |
| Weight               | <ul><li>2.24 oz (64g)</li></ul>                                                                                                                                                                                                                                                                                                                                                           |
| Attachment           | <ul><li>Slots for (2) 7/8th inch velcro/elastic straps on the underside of the puck</li><li>¼ - 20 camera mount style thread on bottom for other convenient mounting solutions</li></ul>                                                                                                                                                                                                  |
| Battery              | <p><strong>1200 mAh Lithium polymer battery</strong></p><ul><li>Expected life 10 hrs at nominal operating conditions (cameras operating at 180Hz, with 500 𝞵s exposure setting). Lower frame rates or exposure times can extend battery life.</li></ul><p><strong>Charging</strong></p><ul><li>5V micro USB power source required to charge</li><li>~ 3hrs zero to full charge</li></ul> |

### Power Button

* **Power on:** Press down on the button for \~1 second to turn on the puck. It will illuminate the top LED in orange for a few seconds until it initializes.
* **Power off:** Hold down the button \~2 seconds
* **Battery status check:** Press down on the button while the puck is powered on to illuminate the battery status LED.

![Power button.](<../../.gitbook/assets/image (200).png>) ![Puck initializing.](<../../.gitbook/assets/image (706).png>) ![Powered on and connected to a Base Station.](<../../.gitbook/assets/image (663).png>)

{% hint style="info" %}
**Bootloader:** Pressing down on the button for longer than 3 seconds will set the puck at the bootloader state. At this state, both the top and bottom LED will turn orange, and the puck will not be operational. To exit out of this, you can just power off the puck and turn it back on.
{% endhint %}

### Status Indicator LEDs

![Three LEDs on the puck. This may be slightly different on the different revisions.](<../../.gitbook/assets/image (695).png>)

Three plainly visible status LEDs for indication of battery status, sync status, and charging status.

#### **1) Sync – (Bottom)**

The bottom LED indicates the sync status. When the puck is successfully synchronized with a base station, it will start receiving sync packets, and this bottom LED will start blinking green roughly at 10 Hz rate:

* Blinking green: Sync packets are being received.
* Red: The first sync packet has not been received yet. At this stage, the puck is waiting for the packet.
* Continuous green: The first packet was received for initial synchronization but sync packet is no longer being received.

#### **2) Power – (Top-Left)**

* Normal: illuminates in green and blinks every 5 seconds. You can also press on the power button to check the battery.
* Color indicator:
  * Green (Good charge) - battery sufficient
  * Yellow (getting low) - \~1 hour left
  * Red (extremely low) - \~20 minutes left until power is depleted

#### **3) Charging Status – (Top-Right)**

* Red: Charging / Idle
* Green: Fully Charged
* Yellow/orange: Bad battery. Stop using the puck and contact support.

![Connected to a base station. Bottom LED blinks in green indicating that it is actively communicating with the base station. If this LED lights up in continuous green, it means that the puck is no longer communicating with the base station after the initial connection.](<../../.gitbook/assets/image (239).png>) ![Not connected to a base station. Waiting for the first sync packet.](<../../.gitbook/assets/image (295).png>) ![Connected to a base station, but the battery is running low.](<../../.gitbook/assets/image (286).png>)

## Active Puck Accessories

Each Active Puck has four slots on the back where an accessory adaptor plate can be fitted into. These adapter plates can be purchased from our [webstore](https://optitrack.com/products/active-components/#active-puck-accessories), and they provide the Active Puck various mounting options for attaching onto different types of objects.

There are four different types of adapter plate accessories that can be fitted onto an Active Puck:

* Adapter plate with a 1/4-20 mount
* Adapter plate with a clip
* Adapter plate with a 1" strap slot
* Adapter plate with 22mm wristband socket.

![Active Puck 1/4-20 Mount Adapter.](<../../.gitbook/assets/image (235).png>) ![Active Puck Clip Adapter.](<../../.gitbook/assets/image (716).png>)

![Active Puck Strap Adapter.](<../../.gitbook/assets/image (265).png>) ![Active Puck 22mm Wristband Adapter.](<../../.gitbook/assets/image (203).png>)

### Mounting and Removing Adapter Plates

![Different types of adapter plates for various mounting options, and a removal tool for detaching the plates.](<../../.gitbook/assets/image (290).png>)

#### **Mounting**

To mount an adapter plate onto an Active Puck, simply insert the four T-shaped latches of the adapter plate into the four slots on the back of an Active puck. Once the latches have been fully inserted, slide the adapter plate towards the center of the puck until you hear a click.

![Active Puck 1/4-20 Mount Adapter.](<../../.gitbook/assets/image (216).png>)

#### **Removing**

Once an adapter plate is latched onto an Active Puck, a removal tool must be used to detach the adapter plate. To use the removal tool, insert the four hooks on the removal tool into the four slots on the adapter plate. Then use the attached removal tool to slide and pull the adapter plate out from the Active Puck.

![](<../../.gitbook/assets/image (202).png>)

### Adapter Plate CAD File

If any of the four adapter plate accessories do not fit for the object you are tracking, you can also use the attached CAD file to modify and 3D print customized adapter plates.

* Adapter Plate CAD file (STEP):

{% file src="../../.gitbook/assets/Puck Adapter Plate_20190319 (4).STEP" %}
