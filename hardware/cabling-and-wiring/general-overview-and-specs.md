# General Overview and Specs

This page provides the general specifications for an OptiTrack camera setup. Please see our [Windows 10 Network Settings](windows-10-network-settings.md) and [Cabling and Load Balancing](cabling-and-load-balancing.md) pages for more detailed instructions on how to setup your Ethernet camera system.

## Ethernet Camera System

An Ethernet camera system networks via Ethernet cables. Ethernet-based camera models include **PrimeX series** (PrimeX 13, 13W, 22, 41), **SlimX 13**, and **Prime Color** models. Ethernet cables not only offer faster data transfer rates, but they also provide power over Ethernet to each camera while transferring the data to the host PC. This reduces the number of required cables and simplifies the overall setup. Furthermore, Ethernet cables have much longer length capability (up to 100m), allowing the systems to cover large volumes.

### **Main Components**

* Host PC with an isolated network (PCI/e NIC)
* Ethernet Cameras
* Ethernet cables
* Ethernet PoE/PoE+ Switches
* Uplink switch (for large camera count setup)
* The eSync (optional for synchronizations)

### Ethernet Cable Requirements

**Cable Type**

There are multiple categories for Ethernet cables, and each has different specifications for maximum data transmission rate and cable length. For an Ethernet based system, Cat6 or above Gigabit Ethernet cables should be used. 10 Gigabit Ethernet cables – Cat6a or above — are recommended in conjunction with a 10 Gigabit uplink switch for the connection between the uplink switch and the host PC in order to accommodate for high data traffic.

{% hint style="info" %}
**Note**

10Gb uplink switches, NICs, and cables are recommended for large camera counts or high data cameras like the Prime Color cameras. Typically 1Gb switches, NICs, and cables should be enough to accommodate smaller and moderately sized systems. If you're unsure of whether or not you need more than 1Gb, please contact one of our Sales Engineers [here](https://optitrack.com/contact/) or see our [Cabling and Load Balancing](cabling-and-load-balancing.md) page for more information.
{% endhint %}

**Electromagnetic Shielding**

We recommend using only cables that have electromagnetic interference shielding. If unshielded cables are used, cables in close proximity to each other have the potential to create data transfer interference and cause cameras to stall in Motive.

{% hint style="danger" %}
Unshielded cables do not protect the cameras from Electrostatic Discharge (ESD), which can damage the camera. Do not use unshielded cables in environments where ESD exposure is a risk.&#x20;
{% endhint %}

### Network Switch Requirement and Setup

Our current general standard for network switches are:

* PoE ports with at least 1GB of data transfer for each port.
* A power budget that is able to support the desired amount of cameras. If the desired amount of cameras exceeds the power budget of a single switch, additional switches may be used. Please see the [Cabling and Load Balancing](cabling-and-load-balancing.md) section below for more information.

{% hint style="warning" %}
For specific brands/models of switches, please [contact us](https://optitrack.com/contact/).
{% endhint %}

#### Switch Setup

For the most part, the switches provided by OptiTrack are ready to go without any need for additional settings or configurations. If you're having issues with setting up your switches provided by OptiTrack please see the Cabling and Load Balancing section below or contact our [support team](https://optitrack.com/support/).

{% hint style="info" %}
If you have a switch that is _not_ purchased from OptiTrack, these are not supported by our support team.
{% endhint %}

## General Questions

<details>

<summary><strong>Q : Which camera models can be used together in the same system?</strong></summary>

A: OptiTrack camera models can be categorized by their connector cable types: USB and Ethernet. Generally, cameras sharing the same cable type and sync mode can operate together within the same system, with the Flex 13 being the only exception.

In Motive 3.0, however, only the Ethernet cameras are compatible with the software. As far as camera to camera compatibility, any PrimeX Series of cameras can be used together along with SlimX 13 and Prime Color cameras. Older Prime models are also compatible with newer PrimeX series cameras.

</details>

## Troubleshooting

<details>

<summary><strong>Q : [Ethernet Cameras] PrimeX series, or SlimX 13, cameras dropping 2D frames.</strong></summary>

A: 2D frame drops are logged under the [Log pane](../../motive-ui-panes/log-pane.md) and it can also be seen in the [Devices pane](../../motive-ui-panes/devices-pane.md). It will be indicated with a warning sign (<img src="../../.gitbook/assets/image.png" alt="" data-size="line">) next to the corresponding camera. You may see a few frame drops when booting up the system or when switching between Live and Edit modes; however, this should occur only momentarily. If the system continues to drop 2D frames, it means there is a problem with receiving the camera data. In many cases, this occurs due to networking problems.

To narrow down the issue, you would want to disable the [real-time reconstruction](../../motive/reconstruction-and-2d-mode.md) and check if the frames are still dropping. If it stops, the problem is associated with either software configurations or CPU processing. If it continues to drop, then the problem could be narrowed down to the network configuration, which may be resolved by doing the following:

* Disable any firewall or anti-virus software on the host PC. Often, these software interferes with the camera network and cause frame drops.
* Use a dedicated network interface controller (NIC) card for uplinking the camera system to the host PC. Ethernet adapters on common motherboards are not well suited for receiving camera data.
* Update network cade driver to up-to-date.
* If you have an eSync in the system, connect it to the aggregator switch. It will provide more stable synchronization between the cameras.

</details>

<details>

<summary><strong>Q : [Ethernet cameras] Cameras not detected at all.</strong></summary>

A: If you have all of the cameras connected as instructed and cameras are still not showing up in Motive. Run _ipconfig_ on command window and check if an IPv4 IP is assigned to the network adapter that connects to the camera switch. If no IP is assigned, check the following:

* Disable any firewall or anti-virus software and check again to see if it resolves. Often, these software blocks the camera network.
* Update the network card driver.
* Make sure nothing is misconfigured on the network switches. Some switches have its own traffic control tools that might interfere with how the camera data and the sync signals are transmitted.
* If the cameras are still not detected, contact tech support. When doing so, launch Motive and take a note of the behavior of how the back LED lights on the cameras are flashing. This would be helpful when troubleshooting the issue.

</details>
