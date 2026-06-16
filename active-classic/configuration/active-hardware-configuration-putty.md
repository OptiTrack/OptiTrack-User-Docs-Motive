---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/active-components/configuration/active-hardware-configuration-putty
---

# Active Hardware Configuration: PuTTY

{% hint style="danger" %}
**We strongly recommend you use our Active Batch Programmer instead of PuTTY. Instructions on how to use the Active Batch Programmer can be found here:** [**Using Active Batch Programmer**](active-batch-programmer.md)**. Our Active Batch Programmer automates many of the settings found below and therefore is safer and more convenient for use.**
{% endhint %}

{% hint style="danger" %}
This guide is intended for advanced users or those under the guidance of the OptiTrack Support Team. Your OptiTrack Active hardware should arrive fully configured and ready for immediate use. In most cases, you should not need to modify its configuration. If configured incorrectly, tracking may perform poorly, or may cease to function entirely. **Do not attempt to modify the configurations of your OptiTrack Active hardware unless you have been instructed on how to do so by an OptiTrack Support Engineer**.
{% endhint %}

The BaseStation and Active Tag can both be connected to a computer via USB, and expose a virtual serial port. You can connect to this serial port using a terminal application in order to view and modify the configuration of the devices.

A popular choice of terminal application for Windows is the freely available PuTTY, which the latest version can be downloaded [here](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) and will be used in this guide.

{% hint style="info" %}
Note that the UI of PuTTY may look slightly different for each version, however, all of the relevant settings will be present.
{% endhint %}

## Initial Setup in PuTTY

### PuTTY Saved Sessions

After a successful download of PuTTY, we'll want to create a saved session that we can use every time we boot up PuTTY for our Active hardware configurations.

![PuTTY view from Session and Serial panes.](<../../.gitbook/assets/image (1303).png>)

**Instructions**

1. Start PuTTY.
2. Choose the **Serial** option under the "Connection Type" section.
3. Enter 115200 into the **Speed** field.
4. Under **Saved Sessions** enter an appropriate name like "Active" or "Tag Settings".
5. After everything is entered correctly click the **Save** button. This will populate your saved name below **Default Settings**.
6. The next time you boot up PuTTY you can select the saved session and click **Load** to load the settings we set up above.\
   You can access more detail information about the serial connection by clicking the Connection > Serial option in the Category section on the left.

When connecting to an OptiTrack Active device you'll need to input the correct COM# port into the "Serial Line" section.

### Device Manager and COM Ports

When you're ready to start programming your Active tags you need to verify their class-compliant virtual serial port to enter into the **Serial line** in PuTTY. To do this you'll need navigate to the **Device Manger** for any Windows machine.

![Devices manger on Windows with COM ports](<../../.gitbook/assets/image (677).png>)

1. From the **Device Manger** window you can click the dropdown arrow for **Ports**. This will show a list of all the COM ports that are plugged into your machine.
2. The easiest way to find out which COM number is associated with your Active Tag is to plug in the Active Tag and see which new COM port appears.
3. Once you have this number (ie. COM3, COM4, etc.), you can navigate back to PuTTY to enter this port into the **Serial line** text field.

## Configuration

Now that we have all the settings we need to properly interface with Active Tags and BaseStations, we can open a PuTTY session.

* To do this we simply load the settings configured above and then click **Open**.
* This will open a command terminal where we can implement commands to configure both the Active Tags and BaseStations.

### Terminal Commands

There are three serial commands that we'll be concerned about for this application: **d**, **s**, and **v**.

#### **d**

* This command takes no parameters, and outputs a listing of all configuration options and their current values. Each configuration option is listed on its own line, starting with its ID (surrounded by square brackets), followed by its name, and finally its current value.
* The ID is used to refer to the options when modifying their values (described below); if the ID is displayed as a dash, this means the value cannot be changed.
* If the value begins with the prefix “0x”, this means the value is displayed in hexadecimal (base 16); otherwise, the value is a regular decimal (base 10) number.

#### **s**

* This command takes two parameters (separated by spaces), and is used to modify the value of a configuration option.
* The first parameter, as described above, is the ID of the configuration option you want to modify.
* The second parameter is the new value to use for the specified option. The new value can be provided in either decimal or hexadecimal; if hexadecimal, the value should be prefixed with “0x”.
* As an example, the command s 1 2 will set the option with ID 1 to the value of 2. Similarly, the command s 1 0xF will set the option with ID 1 to the value of 0xF (hexadecimal), or 15 (decimal).

#### **v**

* This command takes no parameters, and writes the current configuration to the flash memory of the device. This should always be performed before closing a PuTTY session if you wish to save the configuration.

{% hint style="danger" %}
The **v** command is required to preserve any changes you’ve made to the configuration since the last time you saved. If you do not issue the save command, your configuration changes will be lost the next time the device is powered off.
{% endhint %}

## Firmware Version 1.x

Some of the options in PuTTY change depending on the firmware version you use with Active hardware. These options are for Firmware Version 1.x.

### BaseStation Configuration

When configuring a BaseStation there are only a couple of options we would need to worry about for most setups. It's good practice to first configure a BaseStation and then program Active Tags around the BaseStation's settings.

![1.x BaseStation PuTTY command terminal view.](<../../.gitbook/assets/image (1265).png>)

**BaseStation Commands**

**\[1]: rfPanId**

Default: 0x0001

This is the 16-bit PAN (personal area network) identifier used for wireless communication.

The PAN ID is used to filter traffic at the hardware level, and different PANs may be used to partition a single wireless channel into multiple separate logical networks. This may, for example, be useful if you needed to use two separate OptiTrack Active systems in close proximity. However, in general, the use of different wireless channels (see option \[3]: rfChan below) should be preferred, rather than using multiple PANs on same wireless channel.

The PAN ID and channel values configured on the BaseStation must match the values configured for every Tag that is intended to be used with that BaseStation.

**\[2]: rfSrcAddr**

Default: 0xABCD

This is the 16-bit wireless address of the BaseStation. You should not need to change this.

**\[3]: rfChan**

Default: 20

This is the radio channel used for wireless communication. The range of valid channels is 11-26. The frequency in MHz for the channel ch is given by 2405 + 5 · (ch - 11).

You may wish to change the radio channel if you have determined that you’re encountering poor RF performance due to external interference, or if you want to operate multiple OptiTrack Active systems in close proximity.

{% hint style="info" %}
The PAN ID and channel values configured on the BaseStation must match the values configured for every Active Tag that is intended to be used with that BaseStation.
{% endhint %}

### Active Tag Configuration

When configuring Active Tags, you'll want to match the rfPanId and rfChan to the BaseStation. If these do not match then the Active Tags will not properly synchronize to your OptiTrack system.

![1.x Active Tag PuTTY command terminal view.](<../../.gitbook/assets/image (1282).png>)

**Active Tag Commands**

**\[1] rfPanId**

Default: 0x0001

Refer to the description in the section above: Firmware Version 1.x > BaseStation Commands > rfPanID.

The PAN ID and channel values configured on the BaseStation must match the values configured for every Tag that is intended to be used with that BaseStation.

**\[2] rfSrcAddr**

Default: 0x5678

This is the 16-bit wireless address of the Tag. You should not need to change this.

**\[3] rfChan**

Default: 20

Refer to the description in the section above: Firmware Version 1.x > BaseStation Commands > rfChan.

The PAN ID and channel values configured on the BaseStation must match the values configured for every Tag that is intended to be used with that BaseStation.

**\[D0] led0Id … \[D7] led7Id**

Default: 0x0 (0)

These settings are used to specify the active ID for each of the 8 active marker LEDs connected to the Active Tag. The default value of 0 is a special value indicating that the LED is not actively labeled and behaves as though it were a passive marker (with its LED on time synchronized with the exposure of the cameras).

The LED IDs are preprogrammed when they are sent out. The [Active Batch Programmer](active-batch-programmer.md) is the best way to change these settings. Only use this setting under the guidance of an OptiTrack Support Engineer.

## Firmware Version 2.x

### BaseStation Configuration

![2.x BaseStation PuTTY command terminal view.](<../../.gitbook/assets/image (712).png>)

**BaseStation Commands**

**\[1]: rfChannel**

Default: 20

This is the radio channel used for wireless communication. The range of valid channels is 11-26. The frequency in MHz for the channel ch is given by 2405 + 5 · (ch - 11).

You may wish to change the radio channel if you have determined that you’re encountering poor RF performance due to external interference, or if you want to operate multiple OptiTrack Active systems in close proximity.

### Active Tag Configuration

When configuring Active Tags, you'll want to match the rfChannel to the BaseStation. If the two devices do not match then the Active Tags will not properly synchronize to your OptiTrack system.

![2.x Active Tag PuTTY command terminal view.](<../../.gitbook/assets/image (1311).png>)

**Active Tag Commands**

**\[2]: uplinkId**

Default: 0

The uplinkId identifies the Active Tag label class that the Tag belongs to. This allows for Active Tags to be uniquely identified when there are multiple Active Tags with the same form factor in the same volume.

**\[3] rfChan**

Default: 20

Refer to the description in the section above: Firmware Version 2.x > BaseStation Commands > rfChannel.

**\[4] ledBrightness**

Default: 20

You can choose to increase or decrease the LED brightness on each Active Tags active markers collectively. This will control the brightness of all of the LEDs together as a unit incase the cameras are having difficulty tracking. However, it is recommended to change physical characteristics of the cameras (ie. aperture), or of the volume (ie. blocking out excess light), or increase the exposure of the cameras in Motive prior to altering this setting.

**\[5] onWhileCharging**

Default: 1

This setting allows for a powered Active Tag to remain on when plugged into power. It is useful in setups where the Active Tag is mounted to an object that can supply power, thus ensuring the Active Tag will not turn off or run out of battery.

1 denotes that a powered Active Tag remains on when plugged into power, 0 denotes that when a powered Active Tag is plugged into power, it will shut off while charging.

**\[D0] led0Id … \[D7] led7Id**

Default: 0x0 (0)

These settings are used to specify the active ID for each of the 8 active marker LEDs connected to the Active Tag. The default value of 0 is a special value indicating that the LED is not actively labeled and behaves as though it were a passive marker (with its LED on time synchronized with the exposure of the cameras).

The LED IDs are preprogrammed when they are sent out. The [Active Batch Programmer](active-batch-programmer.md) is the best way to change these settings. Only use this setting under the guidance of an OptiTrack Support Engineer.

## Firmware Version 3.x

### BaseStation Configuration

Currently, there is not a 3.x firmware version for BaseStations. Please refer to 2.x instructions above.

### Active Tag Configuration

When configuring Active Tags, you'll want to match the rfPanId and rfChan to the BaseStation. If these do not match then the active tags will not properly synchronize to your OptiTrack system.

![3.x Active Tag PuTTY command terminal view](<../../.gitbook/assets/image (727).png>)

**Active Tag Commands**

**\[2]: uplinkId**

Default: 0

The uplinkId identifies the Active Tag label class that the Tag belongs to. This allows for Active Tags to be uniquely identified when there are multiple Active Tags with the same form factor in the same volume.

**\[3] rfChan**

Default: 20

Refer to the description in the section above: Firmware Version 1x > BaseStation Commands > rfChan.

**\[4] ledBrightness**

Default: 20

You can choose to increase or decrease the LED brightness on each Active Tags active markers collectively. This will control the brightness of all of the LEDs together as a unit incase the cameras are having difficulty tracking. However, it is recommended to change physical characteristics of the cameras (ie. aperture), or of the volume (ie. blocking out excess light), or increase the exposure of the cameras in Motive prior to altering this setting.

**\[5] onWhileCharging**

Default: 1

This setting allows for a powered Active Tag to remain on when plugged into power. It is useful in setups where the Active Tag is mounted to an object that can supply power, thus ensuring the Active Tag will not turn off or run out of battery.

1 denotes that a powered Active Tag remains on when plugged into power, 0 denotes that when a powered Active Tag is plugged into power, it will shut off while charging.

**\[7] imuDecimationsRate**

The ADIS16505 sample rate is 2000 Hz. The decimation, dec, can is used to smooth and decrease the effective sample rate using averages. Applying the decimation rate dec yields a nominal sample rate of 2000/(dec + 1).

You should not have to change this setting.

**\[8] imuFilterLevel \[0-6]**

Default: 5

This controls the level of filtering and smoothing. 0 means no filtering, 6 means maximum filtering. We recommend level 5 as the best option.

**\[9] imuBurstMode**

Default: 32

This setting should not be changed as this version of the firmware only supports 32-bits mode when filtering.

**\[A] imuBiasUpdateCount**

Default: 1000

Controls the number of IMU samples between IMU bias updates. If this value is N a bias update procedure will be initiated after every N samples.

**\[D0] led0Id … \[D7] led7Id**

Default: 0x0 (0)

These settings are used to specify the active ID for each of the 8 active marker LEDs connected to the Active Tag. The default value of 0 is a special value indicating that the LED is not actively labeled and behaves as though it were a passive marker (with its LED on time synchronized with the exposure of the cameras).

The LED IDs are preprogrammed when they are sent out. The [Active Batch Programmer](active-batch-programmer.md) is the best way to change these settings. Only use this setting under the guidance of an OptiTrack Support Engineer.

## Firmware 3.0.6

<figure><img src="../../.gitbook/assets/image (467).png" alt=""><figcaption></figcaption></figure>

#### \[9] rfTxPower(1, 6)

Beginning with firmware version 3.0.6, there is an additional setting that changes the radio frequency power intensity.

This setting applies to both BaseStations and Active Tags/Pucks. Below is a chart of the power that corresponds to the 1-6 range.

|   |        |
| - | ------ |
| 6 | 17 dBm |
| 5 | 16 dBm |
| 4 | 14 dBm |
| 3 | 11 dBm |
| 2 | -1 dBm |
| 1 | -8 dBm |
