# NETGEAR ProSafe GSM7228S: Disabling the Broadcast Storm Control

## Overview

When enabled, the Broadcast Storm Control feature on the NETGEAR ProSafe GSM7228S may interfere with the transmission of data from OptiTrack Ethernet cameras. While this feature is critical to a corporate LAN or other network with internet access, it can cause dropped frames, loss of frame data, camera disconnection, and other issues on a camera system.&#x20;

For proper system operations, the Storm Control feature must be disabled for all ports used in this aggregator switch. OptiTrack switches ship with these management features disabled.&#x20;

## Temporarily change the IP Address to Access the Uplink Switch&#x20;

Type _Network_ in the Windows search bar to find and open the Control Panel to _View Network Connections._ The image below shows the three NICs specified above.&#x20;

<figure><img src="../../.gitbook/assets/image (1549).png" alt=""><figcaption><p>Isolated network connections for a Motive workstation.</p></figcaption></figure>

* Double-click or right-click the NIC used to connect to the camera network and select _Properties_.
* With IPv4 selected, click the _Properties_ button.

<figure><img src="https://v21.wiki.optitrack.com/images/0/00/Netgear_IPv4_Properties.png" alt=""><figcaption><p>Windows Networking Properties for a selected NIC.</p></figcaption></figure>

* **Write down the IP address currently assigned to the Motive PC.** You will need to change the address back to this once the switch configuration is updated.&#x20;
* Change the IP address to **169.254.100.200.**
* Enter 255.255.255.0 for the Subnet mask.
* Click _OK_ to save and return to the Properties window.&#x20;

<figure><img src="https://v21.wiki.optitrack.com/images/7/77/Netgear_IPv4_Address.png" alt=""><figcaption><p>IP address to connect to the Uplink switch.</p></figcaption></figure>

## Configure the Switch

* Open a browser window, enter **169.254.100.100,** and press enter.&#x20;
* This will open the Admin Console for the switch.&#x20;

<figure><img src="https://v21.wiki.optitrack.com/images/8/8a/Netgear_Explorer.png" alt=""><figcaption></figcaption></figure>

* Login to the switch with Username 'admin', and leave Password blank.

<figure><img src="https://v21.wiki.optitrack.com/images/1/19/Netgear_login.png" alt=""><figcaption></figcaption></figure>

* On the _Security_ tab, click the _Traffic Control_ subtab.&#x20;
* Select _Storm Control -> Storm Control Global Configuration_ from the menu on the left.
* Disable everything in the _Port Settings_ options.

<figure><img src="https://v21.wiki.optitrack.com/images/e/e8/Netgear_StormControl.png" alt=""><figcaption></figcaption></figure>

* Click the _Maintenance_ tab and select the _Save Config_ subtab.&#x20;
* Select Save Configuration from the menu on the left.
* Check the 'Save Configuration' check box. This will update the configuration and retain the new settings the next time the system is restarted.&#x20;
* Log out of the switch by closing the browser window.

<figure><img src="https://v21.wiki.optitrack.com/images/b/bf/Netgear_SaveConfig.png" alt=""><figcaption></figcaption></figure>

## Restore the IP Address

Repeat [the steps above](netgear-prosafe-gsm7228s-disabling-the-broadcast-storm-control.md#temporarily-change-the-ip-address-to-access-the-uplink-switch) to access and change the network settings for the NIC used to access the switch. Set the IP address back to the address it was originally.&#x20;
