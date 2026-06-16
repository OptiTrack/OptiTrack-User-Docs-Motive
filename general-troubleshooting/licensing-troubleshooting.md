---
description: Common licensing problems and how to address them.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/general-troubleshooting/licensing-troubleshooting
---

# Licensing Troubleshooting

## Common Licensing Issues

Issues with licensing can prevent the operation of Motive. This list identifies possible causes for various licensing errors that can occur, and how to resolve them.

#### License File Location

The Motive license folder is located at **C:\ProgramData\OptiTrack\License**. You can also open the License folder using the link on the Motive splash screen.&#x20;

### License Not Found

There are several potential causes when the _License not found_ message appears.

<figure><img src="../.gitbook/assets/License not found - cropped.png" alt=""><figcaption><p>Error message when launching Motive<br>without a valid license.</p></figcaption></figure>

#### License File Did Not Download After Activating

Check the license folder. If there is no license file in the folder, download it by running the License Activation Tool, available on the Motive splash page. Alternately, you can run the tool from C:\Program Files\OptiTrack\Motive\LicenseTool, or from the [OptiTrack Support page](https://optitrack.com/support/).&#x20;

***

#### License is Registered to a Different USB Security or Hardware Key

Check the license folder. The license file name contains the 6-digit serial number of the USB Security or Hardware Key associated with it. Confirm that this number matches the number on the actual Key attached to the computer. If the key and the license are mismatched, contact support.

***

#### Initial License for a Maintenance License isn't in the License Folder

Maintenance Licenses extend the term of the license purchased with the OptiTrack system, which is referred to as the Initial License. For a maintenance license to work, both it and the initial license must be in the Motive license folder. &#x20;

Check the license folder. The name of the license file will indicate whether the license is an initial or maintenance license.&#x20;

If the Initial License is missing, use the License Activation Tool to download it again. You will need the licensing information provided on the License card when the system was purchased to do so. This will download the initial license and all associated maintenance licenses.&#x20;

[Contact support](https://optitrack.com/support/) for your initial license information if you are unable to find it.

***

#### The Version Downloaded was Released After the License Maintenance Period Ended

Use the "Check My License" tool at the bottom of the online license tool on the [Support page](https://optitrack.com/support/) to verify the end date of the license maintenance period.&#x20;

<figure><img src="../.gitbook/assets/Check my license- expired.png" alt=""><figcaption><p>Check my License results for an expired license.</p></figcaption></figure>

On the [downloads](https://optitrack.com/support/downloads/) page, find the version of Motive that was valid before the license maintenance period ended. Click to expand the _Previous Releases_ section for either 3.x.x or 2.x.x, depending on which license you have.&#x20;

Expand the _Details & Requirements_ section for any release to see the license effective date.&#x20;

<figure><img src="../.gitbook/assets/Previous Releases of Motive (1).png" alt=""><figcaption><p>Click to see previous releases.          </p></figcaption></figure>

Motive release dates are also shown at-a-glance on the list of Changelogs:&#x20;

<figure><img src="../.gitbook/assets/Previous Releases and dates (1).png" alt=""><figcaption><p>Motve 3.x changelogs and release dates.</p></figcaption></figure>

***

#### Wrong USB Key for the Version of Motive Installed

USB Security Keys only work with Motive 3.x and higher. USB Hardware Keys work with all versions of Motive.&#x20;

***

#### Multiple Initial licenses in the License Folder

Check the license folder and move or delete either the oldest license or the one that is not needed.

***

### USB Key is not detected

If Motive does not detect the attached USB security or hardware key, check Windows Device Manager to see if the key is recognized by Windows.&#x20;

If the key is not detected in Device Manager, try reseating it or use a different USB port.&#x20;

{% hint style="info" %}
Type _Device Manager_ in the Windows Search bar to find and open the Device Manager.
{% endhint %}

#### Hardware Key in Windows Device Manager

The OptiTrack Hardware Key, when detected, is listed under _NaturalPoint Devices_.&#x20;

<figure><img src="../.gitbook/assets/Device Manager with Hardware Key with Detail.png" alt=""><figcaption><p>Detected Hardware Key<br>in Device Manager. </p></figcaption></figure>

#### Security Key in Windows Device Manager

* Expand the list of _Human Interface Devices_.
* The OptiTrack Security Key is listed as an _HID-compliant vendor-defined device_. There will likely be several of these on a user's system. If the security key is recognized by Windows, it is often the first in the list.&#x20;
* To identify a key that is plugged in and recognized as a security key, open the Device Properties and select the _Details_ tab.&#x20;
* Select the _Hardware Ids_ property. If the device is a security key, The first two values will begin with HID\VID\_131D\&PID\_2702.&#x20;

<figure><img src="../.gitbook/assets/Device Manager and detail.png" alt=""><figcaption><p>Security key in the list of Human Interface devices.</p></figcaption></figure>

***

#### Security or Hardware Key Requires a Driver Update

If an error symbol is displayed next to the device in Device Manager, the USB driver needs an update. [Contact support](https://optitrack.com/support/) to update the driver.

***

#### USB Key is not Plugged in Properly

If the USB Security or Hardware Key is not listed, try reconnected the device or using a different USB port. Use a port on the back of the PC if one of the ports on the front doesn't work.&#x20;

***

#### USB Key is Broken

[Contact support](https://optitrack.com/support/) to purchase a new key. Once received, contact support to complete the transfer of the license to the new key.

***

### License Activated but Motive Doesn't Open

* Check the license folder to verify the license has been downloaded.&#x20;
* Verify that the version of Motive installed is the correct version for the license. Install the correct version if necessary. Previous versions of Motive can be found under "Previous Releases" on the Download page.
* Ensure the computer meets the [minimum hardware requirement](../quick-start-guides/quick-start-guide-getting-started.md#host-pc-requirements) to run Motive; upgrade as necessary.
* Disable any firewall or antivirus software and launch Motive with administrative privileges.&#x20;
* Contact support if the issue persists after completing these troubleshooting steps.

***

### License won't Activate with the Online License Tool

The online License Tool is available on the [OptiTrack Support](https://optitrack.com/support/) page.&#x20;

<figure><img src="../.gitbook/assets/License Invalid error.png" alt=""><figcaption><p>Error while attempting to activate a license. </p></figcaption></figure>

* Check your data entry for typos.&#x20;
* Use the license tool from the Motive splash screen instead of the online license tool:

<figure><img src="../.gitbook/assets/License Tool link on Splash.png" alt=""><figcaption><p>Access the License Tool from the splash screen.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/License Activation Tool.png" alt=""><figcaption><p>The License Activation Tool from the Motive splash screen.</p></figcaption></figure>

* Only one license (initial or maintenance) can be activated at a time. Subsequent Maintenance licenses are activated when the prior maintenance period ends.&#x20;
* Two USB keys are plugged in. Only one USB key can be connected at a time.&#x20;

***

### Demo License

Support may authorize the use of a demo license at various times. Demo licenses are linked to a specific computer and require the computer's Machine ID to activate.&#x20;

Once permission is granted, send your First Name, Last Name, Email, and Machine ID to Support:

* Download and install the version of Motive that corresponds to the demo license.&#x20;
* Launch Motive. Click _About Motive_ window from the splash page.&#x20;
* The Machine ID is displayed at the bottom:

<figure><img src="../.gitbook/assets/About Motive ID Masked.png" alt=""><figcaption><p>the About Motive screen. </p></figcaption></figure>

* Support will send the license file via email. Check your spam filter and junk folder if it does not arrive on a timely basis.&#x20;
* Download and save the demo license (_.dat file_) attached to the email to the license folder: (C:\ProgramData\OptiTrack\License).
