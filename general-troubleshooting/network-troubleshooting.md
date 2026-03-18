# Network Troubleshooting

## Overview

Typically, system issues can be boiled down to issues with the network. Below are some general steps to take when troubleshooting your network and isolating the cause of the issue.&#x20;

## How to Isolate the Cause of an Issue

When working with network hardware, it's always a good rule to start with an easy fix and work your way up.&#x20;

#### 1. Check your [Firewall settings](firewall-settings.md) along with any Antivirus software

* First and foremost, you'll want to verify that your network can communicate with Motive.&#x20;
* We always firmly suggest that you disable the firewall on your camera network and disable or allow Motive on your Antivirus software.&#x20;

#### 2. Make sure your camera network is isolated&#x20;

* You'll want to make sure that there isn't any other hardware hooked up to your camera network outside of provided sync devices or other OptiTrack approved hardware.&#x20;
  * i.e. eSync 2, BaseStations, some biomechanics hardware, etc.,  are all acceptable to live on your camera network.&#x20;
* Make sure that you are using a designated NIC on an available PCI/e slot on your computer's motherboard as opposed to the NIC that is soldered onto your computer's motherboard. This will insure isolation from things like Wi-Fi or hardwired Internet.&#x20;

#### 3. Check your cables

* If you're noticing a camera is either not receiving power or not showing up in Motive, try testing with a new Ethernet cable.&#x20;
* You can also try a cable that you're using for another camera that is powered and showing up in Motive to guarantee that it is indeed a cable issue.&#x20;
* If you've determined that you have a bad cable, remove the cable from the system and replace it with another available cable.&#x20;

<figure><img src="../.gitbook/assets/image (11) (1) (3).png" alt=""><figcaption><p>Camera powered, but not connected to Motive. Indicated by small white dot in bottom left. </p></figcaption></figure>

{% hint style="info" %}
Be sure to test the new cable before it lands at it's final position within your setup.&#x20;
{% endhint %}

#### 4. Check your network switch ports

* Verify that the port is receiving PoE and a data transfer signal. For most switches, this is indicated by a green light associated with the port.&#x20;
* Try another available port, preferably one that is working with a different camera.&#x20;
* If you've determined a bad port or multiple bad ports, please contact support@optitrack.com for a potential replacement.&#x20;

#### 5. Verify if it's a camera authentication issue

{% hint style="warning" %}
#### Motive 3.0.2 Update:

Following the Motive 3.0.2 release, users will no longer need to authenticate their cameras. Since this is no longer required, users can authenticate their license without the need of an internet connection. If you are currently using Motive 3.0.1 or below, please install this new release from our [Software ](https://optitrack.com/support/downloads/motive.html)webpage. Please note that an internet connection is still required to download Motive.exe from the OptiTrack website.&#x20;
{% endhint %}

* If cameras are powered, but are unable to be seen in Motive you may need to verify that your cameras have been authenticated.&#x20;

## Contact Support

If you have gone through the above network troubleshooting steps, please reach out to our [Support ](https://optitrack.com/support/)team for more advanced troubleshooting.&#x20;
