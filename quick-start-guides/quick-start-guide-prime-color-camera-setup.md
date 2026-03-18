# Quick Start Guide: Prime Color Camera Setup

Below is a quick start guide for most Prime Color and Prime Color FS setups. This setup and settings optimize the Prime Color Camera systems and are strongly recommended for best performance. Please see our full [Prime Color Camera](../movement-sciences/prime-color-camera-setup/) pages for more in-depth information on each topic.

## 1-2 Color Camera Setup Hardware Requirements

| PC                                                                                     | Network Devices                       |
| -------------------------------------------------------------------------------------- | ------------------------------------- |
| Windows 10 or 11 Professional (64 Bit)                                                 | Designated 1Gbps NIC w/drivers        |
| CPU: Intel i9 or better 3.5GHz+                                                        | Network switch with 1Gbps uplink port |
| RAM: 16GB+ of memory                                                                   |                                       |
| GPU: GTX 1050 or better with latest drivers and supports OpenGL version 4.0 or higher. |                                       |
| M.2 SSD                                                                                |                                       |

## 3+ Color Camera Setup Hardware Requirements

| PC                                                                                     | Network Devices                         |
| -------------------------------------------------------------------------------------- | --------------------------------------- |
| <p>Windows 10 or 11 Professional (64 Bit)<br>Windows IoT (Contact Support)</p>         | Designated 10Gbps+ NIC w/drivers        |
| CPU: Intel i9 or better 3.5GHz+                                                        | Network switch with 10Gbps+ uplink port |
| RAM: 32GB+ of memory                                                                   |                                         |
| GPU: RTX 2070 or better with latest drivers and supports OpenGL version 4.0 or higher. |                                         |
| M.2 SSD                                                                                |                                         |

{% hint style="info" %}
If you experience latency or camera drops, you may need to increase the specifications on certain components, especially if your setup includes larger Prime Color camera counts. Please reach out to our [Support ](https://optitrack.com/support/)team, if you are experiencing any of these issues even after upgrading the following specifications above and setup below.&#x20;
{% endhint %}

## Quick Start Hardware Setup

### Cabling

#### **Power**

Each Prime Color camera must be uplinked and powered through a standard PoE connection that can provide at least 15.4 watts to each port simultaneously.

{% hint style="warning" %}
Please note that if your aggregation switch is PoE, you can plug your Prime Color Cameras **directly** into the aggregation switch. PoE injectors are **optional** and will only be required if your aggregation switch is not PoE.
{% endhint %}

{% tabs %}
{% tab title="One or Two Color Cameras" %}
Prime Color cameras connect to the camera system just like other Prime series camera models. Simply plug the camera onto a PoE switch that has enough available bandwidth and it will be powered and synchronized along with other tracking cameras. When you have two color cameras, they will need to be distributed evenly onto different PoE switches so that the data load is balanced out.

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
For 1-2 Prime Color Cameras it is recommended to use 1Gbps network switch with 1Gbps uplink port and a 1Gpbs NIC or higher. For 3+ Prime Color Cameras it is required to use network switches with a 10Gbps uplink port in conjunction with a 10Gbps designated NIC and their appropriate drivers.&#x20;

NIC drivers may need to be installed via disc or downloaded from the manufacture's support website. If you're unsure of where to find these drivers or how to install them, please reach out to our [Support ](https://optitrack.com/support/)team.
{% endhint %}
{% endtab %}

{% tab title="Multiple Color Cameras" %}
When using multiple Prime Color cameras, we recommend connecting the color cameras directly into the 10-gigabit aggregation (uplink) switch, because such setup is best for preventing bandwidth bottleneck. A PoE injector will be required if the uplink switch does not provide PoE. This allows the data to travel directly onto the uplink switch and to the host computer through the 10-gigabit network interface. This will also separate the color cameras from the tracking cameras.

<figure><img src="../.gitbook/assets/image (17) (3).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

## Windows Setup

### Debloat Windows

You'll want to remove as much bloatware from your PC in order to optimize your system and make sure minimal unnecessary background processes are running. Background process can take up valuable CPU resources from Motive and cause frame drops while running your camera system.&#x20;

There are many external resources in order to remove unused apps and halt unnecessary background processes, so they will not be covered within the scope of this page.&#x20;

### Windows Settings

#### Firewall and Antivirus Settings

As a general rule for all OptiTrack camera systems, you'll want to disable all Windows firewalls and either disable or remove any Antivirus software. If firewalls and Antivirus software is enabled, this will cause frame drops while running your camera system.&#x20;

<figure><img src="../.gitbook/assets/image (16) (1).png" alt=""><figcaption></figcaption></figure>

#### Priority&#x20;

In order for Motive to run above other processes, you'll need to change the Priority of Motive.exe to High.&#x20;

* Right Click on the Motive shortcut from your Desktop
* In the Target: text field enter the below path, this will allow Motive to run at High Priority that will persist from closing and reopening Motive.

C:\Windows\System32\cmd.exe /C start "" /high "C:\Program Files\OptiTrack\Motive\Motive.exe"

{% hint style="danger" %}
Please refrain from setting the priority to Realtime. If Realtime is selected, this can cause loss of input control (mouse, keyboard, etc.) since Windows can prioritize Motive above input processes.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/image (25) (2).png" alt=""><figcaption></figcaption></figure>

#### Processor Affinity (Optional)

If you're running a system with a CPU with a lower core count, you may need to disable Motive from running on a couple of cores. This will help stabilize the overall system and free up some cores for other Windows required processes.&#x20;

* From the Task Manager, navigate to the Details tab and right click on Motive.exe
* Select Set Affinity&#x20;
* From this window, uncheck the cores you wish to disallow Motive.exe to run on.&#x20;
* Click OK

{% hint style="danger" %}
Please note that you should only ever disable **2 cores or less** to insure Motive still runs smoothly.&#x20;
{% endhint %}

{% hint style="info" %}
We recommend that you start with only one core and work your way up to two if you're still experiencing frame drop issues with your camera system.
{% endhint %}

<div><figure><img src="../.gitbook/assets/image (2) (3) (1) (1).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (21) (2).png" alt=""><figcaption></figcaption></figure></div>

### Windows IoT Version

Windows IoT is a stripped down version of Windows OS. This can offer many benefits in terms of running a smooth system with very little 'extras' that come standard with more commercial versions of Windows. Windows IoT can aid further in terms of Prime Color Camera system performance.

{% hint style="info" %}
&#x20;If you're still experiencing issues with dropped frames even after altering the settings above, please reach out to our [Support ](https://optitrack.com/support/#contact-support)team for more information regarding Windows IoT.&#x20;
{% endhint %}

## Network Setup in Windows

### Switch Settings

In most cases your switch settings will not be required to be altered. However, if your switch has built in [Storm Control](../hardware/cabling-and-wiring/netgear-prosafe-gsm7228s-disabling-the-broadcast-storm-control.md), you'll want to disable this feature.&#x20;

### NIC Settings

#### NIC

Your Network Interface Card has a few settings that you'll need to change in order to optimize your system and reduce issues when capturing Prime Color Camera video.

To navigate to the camera network's NIC:

* Open Windows Settings
* Select Ethernet from the navigation sidebar
* Under Related settings select Change adapter options
* From the Network Connections pop up window, right click on your NIC and select Properites
* Select the Configure... button and navigate to the Advanced tab

<figure><img src="../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (23) (2).png" alt=""><figcaption></figcaption></figure>

<div><figure><img src="../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (22) (2).png" alt=""><figcaption></figcaption></figure></div>

#### Speed & Duplex

For the Speed and Duplex property, you'll want to change this to the highest throughput of your NIC. If you have a 10Gbps NIC, you'll want to make sure that 10Gbps Full Duplex is selected. This property allows the NIC to operate at it's full range. If this setting is not altered to Full, Windows has the tendency to throttle the NIC throughput causing a 10Gbps NIC to only be sending data at 2Gbps.&#x20;

<figure><img src="../.gitbook/assets/image (18) (1).png" alt=""><figcaption></figcaption></figure>

#### Interrupt Moderation

Interrupt Moderation allows the NIC to moderate interrupts. When there is a significant amount of data being uplinked to Motive, this can cause more interrupts to occur thus hindering the system performance. You'll want to **Disable** this property.&#x20;

<figure><img src="../.gitbook/assets/image (3) (3).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
After the above properties have been applied, the NIC will need to go through a reboot process. This process is automatic, however, it will make it appear that your camera network is down for a few minutes.  This is normal and once the NIC is rebooted, should begin to work as expected.&#x20;
{% endhint %}

#### NIC Adapters (Laptop)

Although not recommended, you may use a laptop PC to run Prime Color Camera system. When using a laptop PC, you'll need to use an external network adapter for. The above settings will typically not apply to these types of adapters, so no properties will need to changed.

{% hint style="info" %}
It is important to use a Thunderbolt port adapter with corresponding Thunderbolt ports on your laptop as opposed to a standard USB-C adapters/ports.&#x20;
{% endhint %}

## Motive Setup

### Prime Color Settings

#### Bit Rate

By default this value is set to 50, however, depending on the specifications of your particular system this value may need to be lower or can be raised higher so long as your system can handle the increased data output.&#x20;

#### Resolution

By default this value is set to full resolution of 1920 x 1080p. Typically you will not need to alter this setting.

#### Closing Camera's View

It is recommended to close the [Camera's View](../motive-ui-panes/viewport.md#cameras-view) during recording. This further stabilizes Motive minimizing lag and less frame drops.
