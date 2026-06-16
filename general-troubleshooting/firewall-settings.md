---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/general-troubleshooting/firewall-settings
---

# Firewall Settings

## Overview

When setting up your motion capture system, it is recommended that all Windows firewalls to be disabled from your Ethernet camera network. This ensures camera data is transported from the camera switches to the Motive computer or streamed from Motive to another application without dropped frames or lost data.

{% hint style="warning" %}
Basic firewall settings are simple to implement, and any typical user can do so. Advanced firewall settings are less intuitive and should be performed with caution and under the guidance of an OptiTrack Support Engineer or by an IT personnel within your company.
{% endhint %}

## Basic Windows Firewall Settings

To access basic Windows firewall settings in Windows 10:

* You can select the Windows icon from the taskbar then select the Settings cog.
  * From the Settings window you can then select Network and Internet
  * This will open the Status window, and from here you can scroll to the bottom to find 'Windows Firewall'
* Alternatively, you can either select the Windows icon from taskbar or press the Windows key on your keyboard and search for 'firewall' and select 'Windows Defender Firewall' (be sure to not select 'Windows Defender Firewall with Advanced Security')

<figure><img src="../.gitbook/assets/image (297).png" alt=""><figcaption></figcaption></figure>
