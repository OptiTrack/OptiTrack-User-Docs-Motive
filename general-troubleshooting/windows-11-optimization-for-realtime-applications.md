---
description: >-
  This document outlines recommended optimizations for a Motive PC operating in
  real-time interactive applications.
---

# Windows 11 Optimization for Realtime Applications

General Purpose Operating Systems (GPOS) like Windows are designed to maintain user responsiveness with many programs and services running, while real-time operating systems ([RTOS](https://en.wikipedia.org/wiki/Real-time_operating_system)) are designed to run critical applications reliably and with precise timing. A GPOS can handle multiple tasks concurrently but is not ideal for important, time-sensitive applications due to latency and synchronization issues. A GPOS can also operate without time constraints, so tasks may sometimes fail or take longer to execute. For this reason, it may be necessary to optimize Windows 11 to improve performance in Motive.

{% hint style="warning" %}
These optimizations involve disabling various Windows security features, so it is crucial to ensure that the PC is isolated from the internet or other potential sources of malware.
{% endhint %}

## Local Group Policy Editor

Many of the recommended optimizations are completed using Window’s _Local Group Policy Editor_. To open this program:

<figure><img src="../.gitbook/assets/Open Windows Local Group Policy Editor.png" alt="" width="438"><figcaption><p>Windows Command Prompt in Administrator mode.</p></figcaption></figure>

#### **Steps:**

1. From the Windows search bar, type _CMD_.
2. Run _Command Prompt_ as administrator.&#x20;
3. At the command line, type _gpedit.msc_ and press enter.
4. This will open the _Local Group Policy Editor_ window.&#x20;

{% hint style="danger" %}
Local Group Policy Editor is available only with a Windows Professional License.&#x20;
{% endhint %}

## Disable Firewall

Set a Local Group Policy to disable Private, Public, and Domain firewalls.&#x20;

{% hint style="warning" %}
Once these policies are implemented, the firewall cannot be re-enabled by any other means.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/Local GPEditor - Firewall.png" alt=""><figcaption><p>Local Group Policy Editor:  Windows Defender Firewall and Advanced Security Overview.</p></figcaption></figure>

#### **Steps:**

1. Open Window’s [Local Group Policy Editor](windows-11-optimization-for-realtime-applications.md#local-group-policy-editor).
2. Navigate to _Computer Configuration -> Windows Settings -> Security Settings -> Windows Defender Firewall with Advanced Security._
3. The Overview panel shows the current status of the firewall. Click _Windows Defender Firewall Properties_ to change the state of the _Domain, Private,_ and _Public_ profiles to _Off_ then click OK.

<div><figure><img src="../.gitbook/assets/Windows Firewall - Domain settings (3).png" alt=""><figcaption><p>Domain Profile settings.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Windows Firewall - Private settings (2).png" alt=""><figcaption><p>Private Profile settings.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Windows Firewall - Public settings  (1).png" alt=""><figcaption><p>Public Profile settings.</p></figcaption></figure></div>

## Disable Antivirus

Set a Local Group Policy to disable Microsoft Defender Antivirus.&#x20;

{% hint style="warning" %}
Once this policy is implemented, the Windows Defender Antivirus cannot be re-enabled in Virus & Threat Protection.
{% endhint %}

<figure><img src="../.gitbook/assets/LGPEditor - MS Anti-virus (1).png" alt="" width="563"><figcaption><p>Local Group Policy Editor:  Microsoft Defender Antivirus settings.</p></figcaption></figure>

#### **Steps:**

1. Open Window’s [Local Group Policy Editor](windows-11-optimization-for-realtime-applications.md#local-group-policy-editor).
2. Navigate to _Computer Configuration -> Administrative Templates -> Windows Components -> Microsoft Defender Antivirus_.
3. Double-click _Turn Off Microsoft Defender Antivirus_.
4. Select _Enabled_ and click OK.

<figure><img src="../.gitbook/assets/image (40).png" alt="" width="406"><figcaption><p>Turning off Microsoft Defender Antivirus.</p></figcaption></figure>

## Disable Anti-malware

Use the following processes to disable anti-malware services.

### Disable Real-time Protection

#### **Steps:**

1. Open Window’s [Local Group Policy Editor](windows-11-optimization-for-realtime-applications.md#local-group-policy-editor).
2. Navigate to:  _Computer Configuration -> Administrative Templates -> Windows Components -> Microsoft Defender Antivirus -> Real-time Protection._
3. Double-click _Turn off real-time Protection_.
4. Set the policy to Enabled and click OK.

<figure><img src="../.gitbook/assets/LGPEditor - turn off MS Antivirus property.png" alt="" width="506"><figcaption><p>Turning off Microsoft Defender Real-time Protection</p></figcaption></figure>

### Disable Defender Notifications With the _OptiTrack\_ForceDefenderOFF.bat_ Script&#x20;

Save the following script to a batch file named _OptiTrack\_ForceDefenderOFF.bat_, in the common Windows startup folder: _C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp_.

{% code overflow="wrap" %}
```powershell
@cmd /c schtasks /Query /TN PauseDef 2>nul && schtasks /Run /TN PauseDef || powershell -c "$q=\"`n`n`t`t PAUSE DEFENDER `n`n\"; echo $q; Start-Process cmd.exe -ArgumentList ('/q '+$q+' /c schtasks.exe /create /ru \"%username%\" /sc once /tn PauseDef /tr \"wmic.exe /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpPreference call set DisableRealtimeMonitoring=TRUE\" /sd 01/01/2030 /st 00:00:00 /it /rl highest /f & schtasks.exe /run /tn PauseDef') -Verb RunAs"
```
{% endcode %}

### Prevent Anti-malware Service Executable from Scanning its Own Folder

#### Steps:

1. Go to _Settings -> Update & security -> Windows Security -> Virus & Threat Protection_.
2. Click _Manage Settings_ at the bottom of the screen.
3. Scroll to the _Exclusions_ section and click _Add or remove exclusions_.
4. Navigate to _C:\Program Files\Windows Defender_.
5. Click the _Select Folder_ button.
6. Restart the computer to decrease the RAM usage by the _Antimalware Service Executable_ in Task Manager Processes.

<div><figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption><p>Windows Security Settings.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Win Security Virus Exclusions.png" alt=""><figcaption><p>Virus &#x26; threat protection settings:  Exclusions.</p></figcaption></figure></div>

### Disable Windows Notifications

Stop notifications from Windows and installed applications.

<figure><img src="../.gitbook/assets/Windows System Notifications (1).png" alt="" width="563"><figcaption><p>Windows System Notification Settings.</p></figcaption></figure>

#### Steps:

1. Right-click on the clock on the Task Bar to open the Notifications panel.
2. Select _Notification Settings_.
3. Set _Notifications_ to Off.
4. Turn _Do Not Disturb_ On.
5. Scroll through the list of _Notifications from apps and other senders_ and turn _Off_ any that are set to _On_.
6. At the bottom of the list, click _Additional Settings._
7. Deselect all options in the _Additional Settings_ list.&#x20;

<figure><img src="../.gitbook/assets/Windows Notifications Additional settings.png" alt="" width="563"><figcaption><p>Additional Notification Options for Windows.</p></figcaption></figure>

## Windows Task Scheduler

Stop scheduled tasks from running.

### Disable All Scheduled Tasks

#### Steps:

1. Open the _Windows Task Scheduler_ application.
2. Select all the task in the _Task Scheduler Library_ list.
3. Right-click and select _Disable_.

<figure><img src="../.gitbook/assets/image (43).png" alt="" width="544"><figcaption><p>Windows Task Scheduler Library.</p></figcaption></figure>

### Disable all Windows Defender Tasks

#### Steps:

1. Open the _Windows Task Scheduler_ application.
2. Navigate to _Microsoft -> Windows -> Windows Defender_.
3. Select all the tasks in the list.
4. Right-click and select _Disable_.

<figure><img src="../.gitbook/assets/image (44).png" alt="" width="563"><figcaption><p>Windows Task Scheduler:  Windows Defender Tasks.</p></figcaption></figure>

## Disable Startup Applications

Stop unnecessary applications from loading at startup.

#### Steps:

1. Open the _Windows Task Manager_ application.
2. Click the _Startup apps_ tab button.
3. Disable all unnecessary startup apps.

{% hint style="warning" %}
**DO NOT** disable _OptiTrack\_ForceDefenderOff.bat_.
{% endhint %}

<figure><img src="../.gitbook/assets/image (45).png" alt="" width="563"><figcaption><p>Task Manager:  Startup apps window.</p></figcaption></figure>

## Disc Drive Optimizations

* Turn off HDD/SSD Encryption (for example, BitLocker Drive Encryption Service).
* Turn off HDD/SSD Compression.

## OpenGL setting in NVIDIA Control Panel

1. Open Nvidia Control Panel and Navigate to _3D settings -> Manage 3D Settings_&#x20;
2. Select the _Global Settings_ tab.
3. Set _OpenGL rendering GPU_ to the dedicated GPU card.

<figure><img src="../.gitbook/assets/NVIDIA OpenGL Rendering.png" alt="" width="563"><figcaption><p>NVIDIA Control Panel:  Manage 3D Settings.</p></figcaption></figure>

## Network Settings

Use the recommended network configuration.

### Network Topology <a href="#nicsettings" id="nicsettings"></a>

* Use Static IPs for Camera and Streaming Network Interface Cards (NICs)
* Isolate the following on three different NICs:

1. Local Area Network
2. Incoming camera data
3. Outgoing streaming data

<figure><img src="../.gitbook/assets/image (47).png" alt="" width="563"><figcaption><p>Recommended Network Topology for OptiTrack systems.</p></figcaption></figure>

### Camera and Streaming Network Interface Card (NIC) Configuration Settings

Type _Network_ in the Windows search bar to find and open the Control Panel to _View Network Connections._ The image below shows the three NICs specified above.&#x20;

<figure><img src="../.gitbook/assets/image (1549).png" alt=""><figcaption><p>Isolated network connections for a Motive workstation.</p></figcaption></figure>

#### Configure Static IP

1. Double-click or right-click the NIC you wish to configure and select _Properties_.
2.  From the Properties screen, disable all protocols except IPv4.\
    <br>

    <figure><img src="../.gitbook/assets/NIC Protocols for Motive PC.png" alt=""><figcaption></figcaption></figure>
3. With IPv4 selected, click the _Properties_ button.
4. Select _Use the following IP address:_&#x20;
   1. For the NIC connected to the Camera network, enter IP address 192.168.10.1
   2. For the NIC connected to the realtime network, enter IP address 192.168.20.1
5. Enter 255.255.255.0 for the Subnet mask.
6. Click OK to save and return to the Properties window.&#x20;

<figure><img src="../.gitbook/assets/IP Settings for Motive PC.png" alt=""><figcaption><p>Static IP address configuration.</p></figcaption></figure>

#### Configure NIC settings

Set the following properties to the value specified:

* Interrupt Moderation = Disabled
* Interrupt Moderation Rate = Disabled
* Jumbo Packets = Disabled
* Max Number RSS Queues = 16
* Receive Buffers = 4096 (max)
* Receive Side scaling = Enabled
* Speed and Duplex = Auto-Negotiate
* Transmit Buffers = 16384 (max)

**Steps:**

<figure><img src="../.gitbook/assets/Network - Configure NIC.png" alt=""><figcaption></figcaption></figure>

1. From the Properties window, click the _Configure..._ button to customize NIC settings.
2.  Click the _Advanced_ tab. \
    <br>

    <figure><img src="../.gitbook/assets/image (1551).png" alt="" width="398"><figcaption><p>NIC Advanced Configuration Properties<br></p></figcaption></figure>
3. To update a setting, select it from the _Property:_ list and update the _Value_ field on the right.
4. Update all of the settings listed above.
5. Click the _Driver_ tab.
6. Click _Disable_, then _Enable_ to restart the NIC with the new settings.&#x20;

<figure><img src="../.gitbook/assets/NIC - Disable HIGHLIGHTED.png" alt="" width="317"><figcaption><p>NIC Advanced Configuration Properties</p></figcaption></figure>

{% hint style="warning" %}
Use the settings supplied by your IT department to connect to corporate or institutional networks.
{% endhint %}

## Set Motive.exe Priority

Customize the Motive desktop shortcut to launch the program with high priority.

<figure><img src="../.gitbook/assets/Motive Shortcut Properties.png" alt="" width="359"><figcaption><p>Motive shortcut properties window.</p></figcaption></figure>

* On the desktop, right-click the Motive shortcut and select _Properties_.
* Select the _Shortcut_ tab.
* Copy and paste the text below into the _Target_ field:

{% code overflow="wrap" %}
```
%windir%\system32\cmd.exe /c start "" /High /max "C:\Program Files\OptiTrack\Motive\Motive.exe"
```
{% endcode %}

* Set the _Run_ property to _Maximized_.
* Click _OK_ to save your changes and close the window.
