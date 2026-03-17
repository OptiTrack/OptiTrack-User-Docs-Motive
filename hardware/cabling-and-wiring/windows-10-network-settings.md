# Windows 10 Network Settings

## General Windows Setup

### Debloat Windows

You'll want to remove as much bloatware from your PC in order to optimize your system and make sure minimal unnecessary background processes are running. Background process can take up valuable CPU resources from Motive and cause frame drops while running your camera system.&#x20;

There are many external resources in order to remove unused apps and halt unnecessary background processes, so they will not be covered within the scope of this page.&#x20;

### Windows Settings

#### Firewall and Antivirus Settings

As a general rule for all OptiTrack camera systems, you'll want to disable all Windows firewalls and either disable or remove any Antivirus software. If firewalls and Antivirus software is enabled, this will cause frame drops while running your camera system.&#x20;

<figure><img src="../../.gitbook/assets/image (824).png" alt=""><figcaption></figcaption></figure>

#### Priority&#x20;

In order for Motive to run above other processes, you'll need to change the Priority of Motive.exe to High.&#x20;

* Right Click on the Motive shortcut from your Desktop
* In the Target: text field enter the below path, this will allow Motive to run at High Priority that will persist from closing and reopening Motive.

C:\Windows\System32\cmd.exe /C start "" /high "C:\Program Files\OptiTrack\Motive\Motive.exe"

{% hint style="danger" %}
Please refrain from setting the priority to Realtime. If Realtime is selected, this can cause loss of input control (mouse, keyboard, etc.) since Windows can prioritize Motive above input processes.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/image (812).png" alt=""><figcaption></figcaption></figure>

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

<div><figure><img src="../../.gitbook/assets/image (773).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image (846).png" alt=""><figcaption></figcaption></figure></div>

## Network Setup in Windows

{% hint style="danger" %}
The settings below are generally for **larger** camera setups and **Prime Color** camera setups. Typically, smaller systems will not need to use the settings below. When in doubt, please reach out to our [Support ](https://optitrack.com/support/#contact-support)team.&#x20;
{% endhint %}

### Switch Settings

{% hint style="info" %}
In most cases your switch settings will not be required to be altered. However, if your switch has built in [Storm Control](netgear-prosafe-gsm7228s-disabling-the-broadcast-storm-control.md), you'll want to disable this feature.&#x20;
{% endhint %}

### NIC Settings

#### NIC

Your Network Interface Card has a few settings that can change in order to optimize your system.&#x20;

To navigate to the camera network's NIC:

* Open Windows Settings
* Select Ethernet from the navigation sidebar
* Under Related settings select Change adapter options
* From the Network Connections pop up window, right click on your NIC and select Properites
* Select the Configure... button and navigate to the Advanced tab

<figure><img src="../../.gitbook/assets/image (776).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (809).png" alt=""><figcaption></figcaption></figure>

<div><figure><img src="../../.gitbook/assets/image (823).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image (796).png" alt=""><figcaption></figcaption></figure></div>

#### Speed & Duplex

For the Speed and Duplex property, you'll want to change this to the highest throughput of your NIC. If you have a 10Gbps NIC, you'll want to make sure that 10Gbps Full Duplex is selected. This property allows the NIC to operate at it's full range. If this setting is not altered to Full, Windows has the tendency to throttle the NIC throughput causing a 10Gbps NIC to only be sending data at 2Gbps.&#x20;

<figure><img src="../../.gitbook/assets/image (788).png" alt=""><figcaption></figcaption></figure>

#### Interrupt Moderation

Interrupt Moderation allows the NIC to moderate interrupts. When there is a significant amount of data being uplinked to Motive, this can cause more interrupts to occur thus hindering the system performance. You'll want to **Disable** this property.&#x20;

<figure><img src="../../.gitbook/assets/image (774).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
After the above properties have been applied, the NIC will need to go through a reboot process. This process is automatic, however, it will make it appear that your camera network is down for a few minutes.  This is normal and once the NIC is rebooted, should begin to work as expected.&#x20;
{% endhint %}

#### NIC Adapters (Laptop)

Although not recommended, you may use a laptop PC to run a larger or Prime Color Camera system. When using a laptop PC, you'll need to use an external network adapter for. The above settings will typically not apply to these types of adapters, so no properties will need to changed.

{% hint style="info" %}
It is important to use a Thunderbolt port adapter with corresponding Thunderbolt ports on your laptop as opposed to a standard USB-C adapters/ports.&#x20;
{% endhint %}
