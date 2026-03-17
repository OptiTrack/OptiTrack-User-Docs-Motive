---
description: Configure a Netgear PoE++ switch to connect a PrimeX 120 camera.
---

# Switch Configuration for PrimeX 120

## Overview

The Link Layer Discovery Protocol (IEEE 802.1AB) advertises the major capabilities and physical descriptions of components on an 802 Local Area Network. This protocol provides network components from different vendors the ability to communicate with each other.&#x20;

LLDP also controls the Power over Ethernet (PoE) power allocation. In the case of the PrimeX 120 cameras, LLDP prevents the switch from providing sufficient power to the port where the camera is connected. For this reason, the LLDP protocol must be disabled on any port used to connect a PrimeX 120 to the camera network.

{% hint style="warning" %}
Not all PoE++ switches are the same. **PoE++ Type 3** switches provide only 60W of power per port, which is insufficient to power a PrimeX 120 camera. A **PoE++ Type 4** switch supplies 100W per port, providing the optimum power to each PrimeX 120 on the switch.&#x20;
{% endhint %}

## Configure Settings

1. From the Motive PC, launch any web browser and type http://169.254.100.100 to open the Management Console for the switch.&#x20;
2. This will open the login console.&#x20;
3. Login using the _Admin_ account.&#x20;
4. If the switch has already been configured, the password is _OptiPOE++._ Otherwise, leave the password blank.
5. Click Main UI Login.

<figure><img src="../../.gitbook/assets/Netgear login.png" alt=""><figcaption><p>The Netgear Managed Switch login screen.</p></figcaption></figure>

### PoE Port Configuration

Set the values necessary to ensure the PrimeX 120 receives sufficient power once the LLDP settings are turned off.&#x20;

<figure><img src="../../.gitbook/assets/Tabs and Menu - System and PoE selected.png" alt=""><figcaption><p>The Netgear Management Console: System menu options.</p></figcaption></figure>

1. On the _System_ tab, select the _PoE_ settings from the toolbar.
2. Click _Advanced_ in the navigation bar, on the left.
3. Click _PoE Port Configuration_.
4. Select the port(s) to update.&#x20;
5. Set the _Max Power (W)_ value to **99.9**.&#x20;
6. Set the _Power Limit Type_ to **User**.
7.  Click the _Apply_ button in the upper right corner to commit the changes in the current session.<br>

    <figure><img src="../../.gitbook/assets/Console toolbar.png" alt=""><figcaption></figcaption></figure>
8. Click the _Save_ <img src="../../.gitbook/assets/Netgear Save button.png" alt="" data-size="line"> button to save the changes to the startup configuration.&#x20;

{% hint style="danger" %}
Changes that are _Applied_ but not _Saved_ will remain in effect until the Switch is restarted, when the previous settings are restored. Configuration changes that are _Saved_ will remain in effect after a restart.
{% endhint %}

<figure><img src="../../.gitbook/assets/POE Port Config Settings (1).png" alt=""><figcaption><p>The Netgear Management Console: System configuration / PoE settings.</p></figcaption></figure>

### LLDP Configuration

Update settings to prevent LLDP from interfering with traffic from the PrimeX 120.&#x20;

1. On the _System_ tab, select the _LLDP_ settings from the toolbar.
2. From the Navigation bar, select _LLDP -> Interface Configuration_.
3. Disable _Transmit, Receive,_ and _Notify_ for all required ports.&#x20;
4. Click the _Apply_ button in the upper right corner to commit the changes in the current session.
5. Click the _Save_ <img src="../../.gitbook/assets/Netgear Save button.png" alt="" data-size="line"> button to save the changes to the startup configuration.&#x20;

<figure><img src="../../.gitbook/assets/Interface Configuration.png" alt=""><figcaption><p>The Netgear Management Console: System configuration / LLDP Settings.</p></figcaption></figure>

### Disable Storm Control

Storm control security features may throttle traffic from the PrimeX 120 cameras, affecting system performance.&#x20;

1. On the _Security_ tab, select the _Traffic Control_ settings from the toolbar.
2. From the Navigation bar, select _Storm Control -> Storm Control Global Configuration_.
3. Disable all Port Settings shown.
4. Click the _Apply_ button in the upper right corner to commit the changes in the current session.
5. Click the _Save_ <img src="../../.gitbook/assets/Netgear Save button.png" alt="" data-size="line"> button to save the changes to the startup configuration.&#x20;

<figure><img src="../../.gitbook/assets/Storm Control Config (1).png" alt=""><figcaption><p>The Netgear Management Console: Security configuration / Traffic Control Settings.</p></figcaption></figure>
