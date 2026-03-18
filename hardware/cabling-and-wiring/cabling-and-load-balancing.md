# Cabling and Load Balancing

## Overview

Below are a couple of diagrams to properly setup your network. These setups are strongly advised and have been tested for optimal use and safety.&#x20;

#### Ethernet Camera System

_Ethernet Camera Models: PrimeX series and SlimX 13 cameras. Follow the below wiring diagram and connect each of the required system components._

{% tabs %}
{% tab title="One to Two PoE Switch(es)" %}
<figure><img src="../../.gitbook/assets/image (12) (5).png" alt=""><figcaption></figcaption></figure>

* **Connect PoE Switch(s) into the Host PC:** Start by connecting a PoE switch into the host PC via an Ethernet cable. Since the camera system takes up a large amount of data bandwidth, the Ethernet camera network traffic must be separated from the office/local area network. If the computer used for capture is connected to an existing network, you will need to use a second Ethernet port or add-on network card for connecting the computer to the camera network. When you do, make sure to turn off your computer's firewall for the particular network under Windows Firewall settings.
* **Connect the Ethernet Cameras to the PoE Switch(s):** Ethernet cameras connect to the host PC via PoE/PoE+ switches using Cat 6, or above, Ethernet cables.
* **Power the Switches:** The switch must be powered in order to power the cameras. To completely shut down the camera system, the network switch needs to be powered off.
* **Ethernet Cables:** Ethernet cable connection is subject to the limitations of the PoE (Power over Ethernet) and Ethernet communications standards, meaning that the distance between camera and switch can go up to about 100 meters when using Cat 6 cables (Ethernet cable type Cat5e or below is not supported). For best performance, do not connect devices other than the computer to the camera network. Add-on network cards should be installed if additional Ethernet ports are required.

{% hint style="danger" %}
On smaller systems you may not need to use the **SFP ports** to uplink your data. The SFP port on the switch with the SFP module provided by OptiTrack are specific for heavily loaded systems (i.e. larger camera counts, Prime Color Camera systems).&#x20;



In the event that SFP ports are NOT used, please use one of the standard Ethernet ports on your switch to uplink data to Motive. If you're unsure if you'll require to use the SFP port and SFP module,  please reach out to either our [Sales ](https://optitrack.com/contact/)or [Support](https://optitrack.com/support/#contact-support) teams.&#x20;
{% endhint %}

{% hint style="info" %}
**Ethernet Cable Requirements**

**Cable Type**

There are multiple categories for Ethernet cables, and each has different specifications for maximum data transmission rate and cable length. For an Ethernet based system, category 6 or above Gigabit Ethernet cables should be used. 10 Gigabit Ethernet cables – Cat6a or above— are recommended in conjunction with a 10 Gigabit uplink switch for the connection between the uplink switch and the host PC in order to accommodate for the high data traffic. A 10GB uplink and NIC are recommended for multi-switch setups or when using Prime Color cameras.

**Electromagnetic Shielding**

Also, please use a cable that has electromagnetic interference shielding on it. If cables without the shielding are used, cables that are close to each other could interfere and cause the cameras to drop frames in Motive.
{% endhint %}

* **External Sync:** If you wish to connect external devices, use the eSync synchronization hub. Connect the eSync into one of the PoE switches using an Ethernet cable, or if you have a multi-switch setup, plug the eSync into the aggregation switch.
{% endtab %}

{% tab title="Multiple Poe Switch (High camera counts)" %}
![Click image to enlarge.](<../../.gitbook/assets/image (1052).png>)

* **Uplink Switch:** For systems with higher camera counts that uses multiple PoE switches, use an uplink Ethernet switch to link and connect all of the switches to the Host PC. In the end, the switches must be connected in a star topology with the uplink switch at the central node connecting to the host PC. **NEVER** daisy chain multiple PoE switches in series because doing so can introduce latency to the system.
* **High Camera Counts:** For setting up more than 24 Prime series cameras, we recommend using a 10 Gigabit uplink switch and connecting it to the host PC via an Ethernet cable that supports 10 Gigabit transfer rate — Cat6a or above. This will provide larger data bandwidth and reduce the data transfer latency.
{% endtab %}

{% tab title="Switch Power Budget and Camera Power Requirements" %}
![Click image to enlarge.](<../../.gitbook/assets/image (1064).png>)

* **PoE switch requirement:** The PoE switches must be able to provide 15.4W power to every port simultaneously. PrimeX 41, PrimeX 22, and Prime Color camera models run on a high power mode to achieve longer tracking ranges, and they require 30W of power from each port. If you wish to operate these cameras at standard PoE mode, set the [LLDP (PoE+) Detection](../../motive-ui-panes/settings/settings-general.md) setting to false under the application settings. For network switches provided by OptiTrack, refer to the label for the number of cameras supported for each switch.
{% endtab %}
{% endtabs %}

#### **Power over Ethernet (PoE/PoE+) Switches**

OptiTrack’s Ethernet cameras require PoE or PoE+ Gigabit Ethernet switches, depending on the camera's power requirement. The switch serves two functions: transfer camera data to a host PC, and supply power to each camera over the Ethernet cable (PoE).

The switch must provide consistent power to every port simultaneously in order to power each camera. Standard PoE switches must provide a full 15.4 watts to every port simultaneously. PrimeX 41, PrimeX 22, and Prime Color cameras have stronger IR strobes which require higher power for the maximum performance.

In this case, these cameras need to be routed through PoE+ switches that provide a full 30 watts of power to each port simultaneously. Note that PoE Midspan devices or power injectors are not suitable for Ethernet camera systems.

#### **Redundant Power Systems for Larger Camera Setups**

{% hint style="info" %}
The following is generally used for large PoE+ camera setups with multiple camera switches. Please refer to the **Switch Power Budget and Camera Power Requirements** tab above for more information.
{% endhint %}

Some switches are only allotted a power budget smaller than what is needed depending on which OptiTrack cameras are being used. For larger camera setups this can cause multiple switches that can only use a portion of their available ports. In this case, we recommend an Redundant Power System (RPS) to extend the power budget of your switch. For example, a 24-port switch may have a 370W power budget which only supports 12 PoE+ cameras that require 30W to power. If, however, you have the same 24-port switch with a RPS, you can now power all 24 PoE+ cameras with a 30W power requirement utilizing all 24 of the PoE ports on the switch.

### **eSync2**

The eSync is used to enable synchronization and timecode in Ethernet-based mocap systems. Only one device is needed per system, and it enables you to link the system to almost any signal source. It has multiple synchronization ports which allow integrating external signals from other devices. When an eSync is used, it is considered as the master in the synchronization chain.

![The eSync 2 output and input ports descriptions](<../../.gitbook/assets/image (356).png>)

{% hint style="info" %}
With large camera system setups, you should connect the eSync onto the aggregator switch via a standard Ethernet port for more stable camera synchronization. If PoE is not supported on the aggregator switch, the sync hub will need to be powered separately from a power outlet.
{% endhint %}

### Final Steps

At this point, all of the connected cameras will be listed on the [Devices pane](../../motive-ui-panes/devices-pane.md) and the [3D viewport](../../motive-ui-panes/viewport.md) when you start up Motive. Check to make sure all of the connected cameras are properly listed in Motive.

Then, open up the Status Log panel and check there are no 2D frame drops. You may see a few frame drops when booting up the system or when switching between Live and Edit modes; however, this should only occur just momentarily. If the system continues to drop 2D frames, it indicates there is a problem with how the system is delivering the camera data. Please refer to the troubleshooting section for more details.

![](<../../.gitbook/assets/image (500) (1).png>)
