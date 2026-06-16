---
description: Highlights of new features in Motive 3.5
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/whats-new/whats-new-in-motive-3.4
---

# What's New in Motive 3.5

{% embed url="https://youtu.be/bGtbZ7snhe0" %}

## ActiveIO

In our next generation of technology, ActiveIO takes tracking to the next level with automatic firmware updates, input and output (IO) of data from the tags to give battery life and other metrics, as well as all of the classic on/off (IO) blinking markers to uniquely identify individual markers.

See the [ActiveIO Configuration](../activeio/activeio-configuration.md) page for details on how to setup and use your ActiveIO device in Motive. See The [ActiveIO Hardware section](../activeio/activeio-hardware/) for details on each device, including quick start and setup instructions, indicator lights, and product specifications.&#x20;

## PrimeX 260 Camera

The new [PrimeX 260](../hardware/cameras/ethernet-cameras/primex-260.md) is our camera with the most MegaPixels yet. With 26 MegaPixels, this camera is ideal for premium configurations where only the highest level of accuracy and precision is acceptable.

## Deadzone Smoothing

This new option for rigid bodies detects when the movement for an object has gone below a specified threshold. Once below that threshold, the movement of the rigid body is made completely static. This is most useful when projecting the angle of the rigid bodies long distances like in InCamera VFX workflows.

## New Data Streaming Types

To support ActiveIO we have added the ability to stream additional data types.&#x20;

#### **Raw IMU data (inertial measurement unit)**

Streaming of raw IMU data from ActiveIO devices allows for workflows where sensor fusion can be done on the client side.

#### **GPIO data (General Purpose Input/Output)**&#x20;

This unlocks workflows where button inputs are activated on ActiveIO devices, then sent to game engines or client applications where actions in the game can occur.

#### **Anchor Markers**&#x20;

Streaming of Anchor Markers allows users to better remotely monitor system health using a NatNet Client. A new example client for how to do this is included with NatNet 4.5.

For more detail, please see the [Data Streaming](../motive/data-streaming.md) page.&#x20;

## Other Highlights

**USD Export** - Export animation files to the OpenUSD format for importing into game engines and other workflows like the NVIDIA Omniverse.

**STL Attached Geometries** - Enable CAD workflows by attaching STL files onto rigid bodies for better visualization of your engineering project.

**Passive or Active Only Modes** - Added back the ability to have Passive Only and Active Only markers.

{% hint style="info" %}
**For More Information:**

Visit our website for more detail on the new version:

* What's New: [https://www.optitrack.com/software/motive/](https://www.optitrack.com/software/motive/)
* Change log and Download link: [https://www.optitrack.com/support/downloads/](https://www.optitrack.com/support/downloads/)
{% endhint %}
