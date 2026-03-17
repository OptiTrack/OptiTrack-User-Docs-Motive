---
description: Recommended network settings for Prime Color Camera systems.
---

# Prime Color Camera Setup: Windows Network Settings

These settings can be used with any OptiTrack camera system, but are generally not required. For systems that include Prime Color cameras, these changes can resolve dropped frames and other similar network issues.&#x20;

## Disable Windows Firewall

Firewalls can cause connection issues and frame drops. We recommend disabling the Windows firewall on the camera network.

{% hint style="warning" %}
If the Motive PC is connected to multiple networks, leave the firewalls enabled for all the other networks, especially the network used to connect to the internet.
{% endhint %}

### Windows 10

1. Navigate to _Control Panel -> System and Security -> Windows Defender Firewall_
2. The camera network is typically labeled "Unidentified Network" under the _Guest or public networks_ group.
3. Select _Turn Windows Defender Firewall on or off_ in the sidebar.
4. From this window, select _Turn off Windows Defender Firewall_ for the network group that the camera network is on.&#x20;
5. Click _OK_ to return to the main firewall page.&#x20;

<figure><img src="../../.gitbook/assets/image (1382).png" alt=""><figcaption><p>Windows 10: Customize Windows Firewall Settings</p></figcaption></figure>

The network group will be tagged with a red 'x' shield:

<figure><img src="../../.gitbook/assets/image (1158).png" alt=""><figcaption><p>Windows 10:  A Network group with Windows Firewall Disabled</p></figcaption></figure>

### Windows 11

#### Windows 11 Local Group Policy Editor

Many of the recommended optimizations are completed using Window’s _Local Group Policy Editor_. To open this program:

1. From the Windows search bar, type _CMD_.
2. Run _Command Prompt_ as administrator.&#x20;
3. At the command line, type _gpedit.msc_ and press enter.
4. This will open the _Local Group Policy Editor_ window.

{% hint style="warning" %}
Once these policies are implemented, the firewall cannot be re-enabled by any other means.
{% endhint %}

#### Disable Firewall

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

1. Open Window’s [Local Group Policy Editor](windows-10-network-settings.md#local-group-policy-editor).
2. Navigate to _Computer Configuration -> Windows Settings -> Security Settings -> Windows Defender Firewall with Advanced Security._
3. The Overview panel shows the current status of the firewall. Click _Windows Defender Firewall Properties_ to change the state of the _Private_ and _Public_ profiles to _Off_ then click OK.

{% hint style="danger" %}
#### Advanced Firewall Settings

Only change Advanced Firewall settings under the guidance of a Support Engineer or your organization's IT department. Changes can cause breaches in security if done incorrectly.&#x20;

Please contact our [Support team](https://optitrack.com/support/) if you are having connectivity issues.
{% endhint %}

## Ethernet Settings

{% hint style="info" %}
Please see our [Quick Start Guide: Prime Color Camera Setup](../../quick-start-guides/quick-start-guide-prime-color-camera-setup.md) page for more information regarding Ethernet Settings within Windows.
{% endhint %}

###
