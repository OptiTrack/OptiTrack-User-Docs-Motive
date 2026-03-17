---
description: >-
  General specifications to setup an OptiTrack camera system on an Ethernet
  network.
---

# General Overview and Specs

Please see our [Windows 10 Network Settings](windows-10-network-settings.md) and [Cabling and Load Balancing](cabling-and-load-balancing.md) pages for detailed setup instructions for an Ethernet camera system.

## Ethernet Camera System

An Ethernet camera system uses Ethernet switches and cables to connect to the Motive PC.  Ethernet-based camera models include **PrimeX series** (PrimeX 13, 13W, 22, 41, 120), **SlimX series** (SlimX 13, 120), and **Prime Color** models.&#x20;

Ethernet cables not only offer faster data transfer rates, but they also provide power over Ethernet to each camera while transferring the data to the host PC. This reduces the number of cables required and simplifies the overall setup. With a maximum length of 100m, Ethernet cables allow coverage over large volumes.

### **Main Components**

* Host PC with an isolated network card for the camera system (PCI/e NIC)
* Ethernet Cameras
* Ethernet cables
* Ethernet PoE/PoE+/PoE++ Switch(es)
* Uplink switch (for a large camera count setup)
* The eSync2 (optional for synchronizations)

### Ethernet Cable Requirements

**Cable Type**

There are multiple categories of Ethernet cables, and each has different specifications for maximum data transmission rate and cable length. For an Ethernet based system, Cat6 or above Gigabit Ethernet cables should be used. 10 Gigabit Ethernet cables – Cat6a or above — are recommended in conjunction with a 10 Gigabit uplink switch for the connection between the uplink switch and the host PC in order to accommodate for high data traffic.

{% hint style="info" %}
**Note**

10Gb uplink switches, NICs, and cables are recommended for large camera counts or high data cameras like the Prime Color cameras. Typically 1Gb switches, NICs, and cables should be enough to accommodate smaller and moderately sized systems. If you're unsure whether you need more than 1Gb, please contact one of our [Sales Engineers](https://optitrack.com/contact/) or see our [Cabling and Load Balancing](cabling-and-load-balancing.md) page for more information.
{% endhint %}

**Electromagnetic Shielding**

We recommend using only cables that have electromagnetic interference shielding. If unshielded cables are used, cables in close proximity to each other have the potential to create data transfer interference and cause cameras to stall in Motive.

{% hint style="danger" %}
Unshielded cables do not protect the cameras from Electrostatic Discharge (ESD), which can damage the camera. Do not use unshielded cables in environments where ESD exposure is a risk.&#x20;
{% endhint %}

### Network Switch Requirement and Setup

Our current general standard for network switches are:

* PoE ports with at least 1 Gigabit of data transfer for each port.
* A power budget that is able to support the desired number of cameras. If the number of cameras exceeds the power budget of a single switch, additional switches may be used, with an uplink switch to connect the switches. Please see the [Cabling and Load Balancing](cabling-and-load-balancing.md) page for more information.

{% hint style="warning" %}
For specific brands/models of switches, please [contact us](https://optitrack.com/contact/).
{% endhint %}

#### Switch Setup

We thoroughly test and validate the switches we offer for quality and load balancing, and ship all products pre-configured for easy installation right out of the box.&#x20;

For product specifications, please visit the [Sync and Networking Accessories](https://optitrack.com/accessories/sync-networking/) section of our website. [Contact Sales](https://optitrack.com/contact/) for additional information.&#x20;

For issues connecting the cameras to the switches provided by OptiTrack, please see the [Cabling and Load Balancing](cabling-and-load-balancing.md) page or contact our [support team](https://optitrack.com/support/).

{% hint style="info" %}
Our team cannot support switches that were not purchased from OptiTrack.
{% endhint %}

## General Questions

<details>

<summary><strong>Q : Which camera models can be used together in the same system?</strong></summary>

A: OptiTrack camera models are categorized by the connector cable type: USB or Ethernet. Generally, cameras that use the same cable type and sync mode can operate together within the same system.&#x20;

Any PrimeX Series of cameras can be used together along with SlimX 13 and Prime Color cameras. Older Prime models are also compatible with newer PrimeX series cameras.

</details>

## Troubleshooting

<details>

<summary><strong>Q : [Ethernet Cameras] PrimeX series, or SlimX 13, cameras dropping 2D frames.</strong></summary>

A: 2D frame drops are logged under the [Log pane](../../motive-ui-panes/log-pane.md) and can also be seen in the [Devices pane](../../motive-ui-panes/devices-pane.md). It will be indicated with a warning sign next to the corresponding camera. If the system continues to drop 2D frames, it means there is a problem with receiving the camera data. In many cases, this occurs due to networking problems.

To narrow down the issue, disable the [real-time reconstruction](../../motive-ui-panes/properties-pane/properties-pane-camera.md#reconstruction) in the Properties pane for that camera and check if the frames are still dropping. If it stops, the problem is associated with either the software configuration or CPU processing. If frames continue to drop, then the problem could be narrowed down to the network configuration, which may be resolved by doing the following:

* Disable any firewall or anti-virus software on the host PC, which can interfere with the camera network and cause frame drops.
* Use a dedicated network interface controller (NIC) card to uplink the camera system to the host PC. Ethernet adapters on common motherboards are ill-suited for receiving camera data.
* Ensure the network card (NIC) driver is to up-to-date.
* If you have an eSync in the system, connect it to the aggregator switch, where it will provide more stable synchronization between the cameras.

</details>

<details>

<summary><strong>Q : [Ethernet cameras] Cameras not detected at all.</strong></summary>

A: If you have all of the cameras connected as instructed and cameras are still not showing up in Motive, run _ipconfig_ from a command window and check if an IPv4 IP is assigned to the network adapter that connects to the camera switch.&#x20;

**If no IP is assigned,** check the following:

* Disable any firewall or anti-virus software and check again to see if it resolves. Often, these software blocks the camera network.
* Update the network card driver.
* Make sure nothing is misconfigured on the network switches. Some switches have its own traffic control tools that might interfere with how the camera data and the sync signals are transmitted.
* If the cameras are still not detected, [contact OptiTrack support](https://help.naturalpoint.com/new-ticket). Launch Motive and note how the back LED lights on the cameras are flashing. This will help Support troubleshoot the issue.

**If an IP address is assigned,** make sure the installed version of Motive supports the cameras. If the cameras are not compatible with the version in use, they will not appear in Motive.&#x20;

* Check the serial numbers for the cameras against the compatibility notes for your version on our [Motive Downloads](https://optitrack.com/support/downloads/motive.html) page.&#x20;
* download and install a compatible version. &#x20;

</details>
