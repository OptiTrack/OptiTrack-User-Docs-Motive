# Prime Color Camera Setup: Windows 10 Network Settings

These settings are applicable to all camera networks, but for most camera setups, are not required. For Prime Color Cameras, however, these are effective tools to help with dropped frames and other similar network issues.&#x20;

## Disabling Windows Firewall

You'll want to turn off your Windows firewalls on your camera network.

{% hint style="warning" %}
Leaving firewalls enabled can cause connection issues and frame drops.

If your machine is running multiple networks, you can leave those firewalls enabled. i.e. The network associated with an Internet connection can remain enabled.
{% endhint %}

To turn off your Windows firewall please follow the steps below:

1. Navigate to Control Panel > System and Security > Windows Defender Firewall
2. Find where the camera network is located in the network groups. Typically your camera network will be labeled 'Unidentified Network' and located under the **Guest or public networks**.
3. Once verified as to which network group your camera network is on, select **Turn Windows Defender Firewall on or off** in the sidebar.
4. From this window select **Turn off Windows Defender Firewall** for the network group that your camera network is on. Typically your camera network will be on Guest or Public Networks.
5. Click **OK**
6. After you click OK, the window will revert back to the main firewall page. You can verify that this change has been made if the network group you selected has a red 'x' shield icon next to it.
7. You can close this window and continue setting up your camera network.

<figure><img src="../../.gitbook/assets/image (1) (1) (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

### Advanced Firewall Settings

{% hint style="danger" %}
It is recommended to only change Advanced Firewall settings under the guidance of a Support Engineer or your organization's IT department. Some settings can cause breaches in security if not done correctly. Please contact our [Support team](https://optitrack.com/support/) if you are having connectivity issues.
{% endhint %}

## Ethernet Settings

{% hint style="info" %}
Please see our [Quick Start Guide: Prime Color Camera Setup](../../quick-start-guides/quick-start-guide-prime-color-camera-setup.md) page for more information regarding Ethernet Settings within Windows.
{% endhint %}

###
