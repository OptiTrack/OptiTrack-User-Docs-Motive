# NETGEAR ProSafe GSM7228S: Disabling the Broadcast Storm Control

When enabled, the Broadcast Storm Control feature on the NETGEAR ProSafe GSM7228S may interfere with the synchronization mechanism used by OptiTrack Ethernet cameras. For proper system operations, the Strom Control features must be disabled for all of the ports used in this aggregator switch.

## Steps

**Step 1. Access the IPv4 settings on the network card that the camera network is connected to.**

* On windows, open the _Network and Sharing Center_ and access _Change adaptor settings_.
* Right-click on the adapter that the network switch is connected to and access its properties.
* Among the list of items, select the _Internet Protocol Version 4 (TCP/IPv4)_ and access its properties by clicking the _Properties_ button.

<figure><img src="https://v21.wiki.optitrack.com/images/0/00/Netgear_IPv4_Properties.png" alt=""><figcaption></figcaption></figure>

**Step 2. Make a note of the IP address settings for the network card connected to the switch.**

**Step 3. Change the IP address of the network card connected to the switch to 169.254.100.200. As shown below.**

<figure><img src="https://v21.wiki.optitrack.com/images/7/77/Netgear_IPv4_Address.png" alt=""><figcaption></figcaption></figure>

**Step 4. Open windows explorer, and access 169.254.100.100**

<figure><img src="https://v21.wiki.optitrack.com/images/8/8a/Netgear_Explorer.png" alt=""><figcaption></figcaption></figure>

**Step 5. Log into the switch with Username 'admin', and leave Password blank**

<figure><img src="https://v21.wiki.optitrack.com/images/1/19/Netgear_login.png" alt=""><figcaption></figcaption></figure>

<br>

**Step 6. Navigate to Security->Traffic Control->Storm Control->Storm Control Global Configuration**

<figure><img src="https://v21.wiki.optitrack.com/images/e/e8/Netgear_StormControl.png" alt=""><figcaption></figcaption></figure>

**Step 7. Ensure that all storm control options are disabled**

**Step 8. Navigate to Maintenance->Save Config->Save Configuration**

**Step 9. Check the 'Save Configuration' check box**

<figure><img src="https://v21.wiki.optitrack.com/images/b/bf/Netgear_SaveConfig.png" alt=""><figcaption></figcaption></figure>

**Step 10. Log out of the switch, or just close the browser window**

**Step 11. Restore the IP address settings noted in Step 2 for the network card connected to the switch**
