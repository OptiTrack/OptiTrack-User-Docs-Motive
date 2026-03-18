# Installation and License Activation

{% hint style="warning" %}
#### Motive 3.0.2 Update:

Following the Motive 3.0.2 release, an internet connection is no longer required for initial use of Motive. If you are currently using Motive 3.0.1 or older, please install this new release from our [Software ](https://optitrack.com/support/downloads/motive.html)webpage. Please note that an internet connection is still required to download Motive.exe from the OptiTrack website.&#x20;
{% endhint %}

{% hint style="info" %}
**Important Update:**

* New licensing system in Motive 3. Please check the [OptiTrack website](https://www.optitrack.com/software/motive/pricing.html) for details on Motive licenses.
* **Security Key (Motive 3.x):** Starting with version 3.0, a USB C Security Key is available to use with Motive.&#x20;
* **Hardware Key (all versions):** USB A Hardware keys designed for Motive 2.x versions are now compatible with all versions of Motive. To use a Hardware key, the optional USB drivers must be installed.&#x20;
{% endhint %}

{% hint style="danger" %}
**USB Cameras**

USB cameras, including Flex series, tracking bars, and Slim3U, cameras are not supported in 3.x versions currently. For USB camera systems, please use Motive 2.x versions. Go to [Motive 2.3 documentation](https://v23.wiki.optitrack.com/).
{% endhint %}

## Installation

### Host PC Requirements

Required PC specifications may vary depending on the size of the camera system. Generally, you will be required to use the recommended specs with a system with more than 24 cameras.

| Recommended                                                                                                                                                                                                                                                                                                         | Minimum                                                                                                                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li>OS: Windows 10, 11 (64-bit)</li><li>CPU: Intel i7 or better, running at 3 GHz or greater</li><li>RAM: 16GB of memory</li><li>GPU: GTX 1050 or better with the latest drivers and support for OpenGL 3.2+</li><li>USB C port to connect the Security Key or USB A port to connect the Hardware Key</li></ul> | <ul><li>OS: Windows 10, 11 (64-bit)</li><li>CPU: Intel i7, 3 GHz </li><li>RAM: 4GB of memory</li><li>GPU that supports OpenGL 3.2+</li><li>USB C port or an adapter for USB A to USB C to connect the Security Key, or a USB A port to connect the Hardware Key</li></ul> |

### Download

To install Motive, you must first download the Motive installer from our website. Follow the Downloads link under the Support page ([http://optitrack.com/downloads/](http://optitrack.com/downloads/)), and you will be able to find the newest version of Motive or the previous releases if needed. Both Motive: Body and Motive: Tracker use the same software installer.

### Installation Steps

**1. Run the Installer**

When the download is complete, run the installer to initiate the installation process.

**2. Install the USB Driver and Dependencies**

If you are installing Motive for the first time, it will prompt you to install the OptiTrack USB Driver. This driver is required for all OptiTrack USB devices including the Security or Hardware Key. You may also need to install other dependencies such as the C++ redistributable. After all dependencies have been installed, continue onto installing Motive.

**3. Install Motive**

Follow the installation prompts and install Motive in your desired file directory. We recommend installing the software in the default directory, `C:\Program File\OptiTrack\Motive`.

![Installer Wizard for Motive](<../.gitbook/assets/image (197).png>)

**4. OptiTrack Peripheral Module**

At the Custom Setup section of the installation process, you will be asked to choose whether to install the Peripheral Devices along with Motive. If you plan to use force plate, NI-DAQ, or EMG devices along with the motion capture system, then make sure the Peripheral Device is installed. If you are not going to be using these devices, you may skip to the next step.

{% hint style="info" %}
**Peripheral Module NI-DAQ**

If you decided to install the Peripheral Device, then you will be prompted to install the OptiTrack Peripherals Module along with NI-DAQmx driver at the end of the Motive installation. Press Yes to install the plugins and the NI-DAQmx driver. This may take a few minutes to install. This only needs to be done one time.
{% endhint %}

![Peripheral module installation](<../.gitbook/assets/image (101) (1).png>) ![NI-DAQmx driver installation](../.gitbook/assets/375px-DAQmxInstall.gif)

**5. Finish Installation**

After you have completed all the steps above, Motive will be installed. If you want to use additional plugins, visit the [downloads](http://optitrack.com/downloads/plugins.html) page.

### Host PC Setup

**Firewall / Anti-Virus**

* Make sure all antivirus software on the Host PC allows Motive.
* For Ethernet cameras, make sure the windows firewall is configured to allow the camera network to be recognized. Disabling the firewall entirely is another option.

{% hint style="warning" %}
During installation, some antivirus programs (i.e. BitDefender and McAfee) may block Motive from being downloaded. Our software directly downloaded from [OptiTrack.com/downloads](https://optitrack.com/support/downloads/) is safe for use and will not harm your computer. \
\
If an antivirus program allows Motive to download, but you're still unable to view cameras in the Devices pane, or you are seeing frame/data drops, you'll need to reverify that your antivirus or firewall settings are allowing all traffic from your camera network to Motive and vice versa. \
\
In some rare cases with some antivirus software, you may need to completely uninstall the antivirus software if it continues to interfere with camera communication.&#x20;
{% endhint %}

**High-Performance**

Windows power saving mode limits CPU usage. In order to best utilize Motive, set this mode to the _High Performance_ mode and remove the limitations. You can configure the _High Performance Mode_ from _`Control Panel → Hardware and Sound → Power Options`_ as shown in the image below.

![Notification to enable the high performance mode.](<../.gitbook/assets/image (158).png>) ![Enabling the high performance mode. Click image to enlarge.](<../.gitbook/assets/image (175).png>)

**Graphics Card Settings**

**This is only for computers with integrated graphics.**

For computers with integrated graphics, please make sure Motive is set to run on the dedicated graphics card. If the host computer has integrated graphics on the CPU, the PC may switch to using integrated graphics when the computer goes to sleep mode, and when this happens, the viewport may go unresponsive when it exits out of sleep mode. If you have integrated graphics on the computer, go to the Graphics Settings on Windows, and browse Motive to set it as high-performance graphics.

![Setting preferred graphics processor from Graphics Settings in Windows 10](<../.gitbook/assets/image (125).png>)

## License Activation

Once Motive is installed, the next step is to activate the software using the Motive 3.x license information provided at the time of purchase, and attach either the USB Security or Hardware Key. The Security Key attaches to the Host PC either through a USB C port or using an adapter for USB A to USB C. The Hardware Key attaches to the Host PC through a USB A port.

<div><figure><img src="../.gitbook/assets/Security Key.png" alt=""><figcaption><p>Security Key</p></figcaption></figure> <figure><img src="../.gitbook/assets/Hardware Key.png" alt=""><figcaption><p>Hardware Key</p></figcaption></figure></div>

### Security Key vs. Hardware Key

OptiTrack introduced a new licensing option with Motive 3.&#x20;

* **Security Key (Motive 3.x and above):** Beginning with version 3.0, a USB C Security Key is now available.&#x20;
* **Hardware Key (Motive 2.x or below):** The USB A Hardware Key works with all versions of Motive. Motive 2.x versions and earlier require the USB A Hardware Key.&#x20;

{% hint style="warning" %}
To use a Hardware Key in Motive 3.0, make sure to include the USB drivers during installation.&#x20;
{% endhint %}

Only one key should be connected at a time.&#x20;

Security Keys are purchased separately. For more information, please see the following page: [https://optitrack.com/accessories/license-keys/](https://optitrack.com/accessories/license-keys/)

To replace your Hardware Key with a Security Key, please [contact our Technical Sales group](https://www.optitrack.com/contact/).

### License Types

There are five different types of Motive licenses: **Motive:Body-Unlimited, Motive:Body, Motive:Tracker, Motive:Edit-Unlimited, and Motive:Edit**. Each license unlocks different features in the software depending on the use case that the license is intended to facilitate.

* The Motive:Body and Motive:Body-Unlimited licenses are intended for either small (up to 3) or large-scale Skeleton tracking applications.
* The Motive:Tracker license is intended for real-time Rigid Body tracking applications.
* The Motive:Edit and Motive:Edit Unlimited licenses are intended for users modifying data after it has been captured already.

For more information on different types of Motive licenses, check the software comparison table on our [**website**](http://optitrack.com/software/compare/) or in the table below.

| License           | Motive Edit | Motive Edit Unlimited | Motive Tracker | Motive Body | Motive Body Unlimited |
| ----------------- | ----------- | --------------------- | -------------- | ----------- | --------------------- |
| Live Rigid Bodies | 0           | 0                     | Unlimited      | Unlimited   | Unlimited             |
| Live Skeletons    | 0           | 0                     | 0              | Up to 3     | Unlimited             |
| Edit Rigid Bodies | Unlimited   | Unlimited             | Unlimited      | Unlimited   | Unlimited             |
| Edit Skeletons    | Up to 3     | Unlimited             | 0              | Up to 3     | Unlimited             |

### Activation Steps

**Step 1. Launch Motive**

First, launch Motive.

**Step 2. Activate**

The Motive splash screen will pop up and it will indicate that the license is not found. Click to open the license tool and fill out the following fields using provided license information. You will need the _License Serial Number_ and _License Hash_ from your order invoice and the _Hardware Key Serial Number_ indicated on the USB security key or the hardware key. Once you have entered all the information, click Activate. If you have already activated the license before on another machine, make sure the same name is entered when activating.

![Motive splash screen: License activation. Click image to enlarge.](<../.gitbook/assets/image (119).png>) ![Motive License Tool. Click image to enlarge.](<../.gitbook/assets/image (161).png>)

{% hint style="info" %}
**Online Activation Tool**

The Motive License can also be activated from online using the Online License Activation tool. When you use the online License Activation Tool, you will receive the license file via email. In this case, you will have to place the file in the license folder. Once the license file is placed, insert the corresponding USB Security or Hardware Key to use Motive.
{% endhint %}

![](<../.gitbook/assets/image (104) (1) (1) (1) (1) (1) (1) (1).png>)

**Step 3. License File**

If Motive is activated properly, license files will be placed in the license folder. This folder can be accessed from the splash screen or by navigating to `Start Menu → All Programs → OptiTrack → OptiTrack License Folder`.

License Folder: `C:\ProgramData\OptiTrack\License`

**Step 4. Security Key**

If not already done, insert the corresponding Security Key that was used to activate the license. The matching security key must be connected to the computer in order to use Motive.

{% hint style="warning" %}
**Notes on Connecting the Security or Hardware Key**

* Connect the Security or Hardware Key to a USB port where the USB bus does not have a lot of traffic. This is especially important if you have other peripheral devices that connect to the computer via USB ports. If there is too much other data flowing through the USB bus used by the Security or Hardware Key, Motive might not be able to detect the key.
* Make sure only one key is plugged in. If both a Hardware Key and a Security Key are connected to the same computer, Motive may not activate properly.
{% endhint %}

![](<../.gitbook/assets/image (107) (1).png>)

**About Motive**

You can also check the status of the activated license from the _About Motive_ pop-up. This can be accessed in the splash screen when it fails to detect a valid license, or it can be accessed from the _`Help`_` ``→`` `_`About Motive`_ menu in Motive.

{% hint style="info" %}
**License Data:**

In this panel, you can also export license data into a TXT file by clicking on the _License Data..._. If you are having any issues with activating Motive, please export and attach the license data file in the email.
{% endhint %}

![About Motive window listing all of the detected licenses. Click image to enlarge.](<../.gitbook/assets/image (797).png>) ![When no licenses are detected. Click image to enlarge.](<../.gitbook/assets/image (152).png>)

## Using Activated Software on a Different Computer

***

OptiTrack software can be used on a new computer by reactivating the license, using the same license information. When reactivating, make sure to enter the same name information as before. After the license has been reactivated, the corresponding USB Security Key needs to be inserted into the PC in order to verify and run the software.

Another method of using the license is by copying the license file from the old computer to the new computer. The license file can be found in the OptiTrack License folder which can be accessed through the Motive Splash Screen or top Help menu in Motive.

## More Questions?

### General Questions

For more information on licensing of Motive, refer to the Licensing FAQs from the OptiTrack website:

* [http://optitrack.com/support/faq/licensing.html](http://optitrack.com/support/faq/licensing.html)

For more questions, contact our Support:

* [http://optitrack.com/support/](http://optitrack.com/support/)
* When contacting support, please attach the license data (TXT) file exported from the _About Motive_ panel as a reference.

### Troubleshooting: Licensing

<details>

<summary><strong>Q :</strong> License Not Found</summary>

A: Use the license check tool to check the valid date of the license. Make sure the license can be used for the version of Motive you are trying to activate. Any licenses that were expired prior to the release date cannot be used to activate newer versions of Motive.

* First of all, if you haven't already done so, make sure you have [activated](installation-and-activation.md) the software license. If you have successfully activated the license, there should be a license file (DAT) placed under the license folder directory `C:\ProgramData\OptiTrack\License`
* Then, check to make sure the matching USB Security Key is plugged into the computer. You may want to open up the _About Motive_ pop-up to check if all of the license files and the security key are being recognized by Motive.
* If Motive still doesn't open up even with the license file and the Security Key set up properly, try deleting the existing license file and reactivating using the license information and the serial number on the Security Key.

</details>

<details>

<summary><strong>Q :</strong> Cameras do not appear on Motive</summary>

A:Make sure Security Key is connected to the computer and try restarting Motive.

* If the Security Key is already connected, try connecting onto a different USB port, which doesn't have much data traffic on the USB bus.
* If it's first time using the camera system with the key, make sure the computer has access to the Internet for the camera to go through the initial [registration](installation-and-activation.md) with the security key.

</details>

<details>

<summary><strong>Q :</strong> USB Security Key is not detected</summary>

A: Make sure the USB Security Key is properly plugged in. You may also want to try using a different USB port.

* Make sure there is no USB Hardware key plugged along with the USB Security Key. Only one key must be connected in order for Motive to recognize.
* Check if there are a lot of USB devices on the USB bus that may be transferring a lot of data, use a USB port on a bus that doesn't have a lot of devices connected.

</details>
