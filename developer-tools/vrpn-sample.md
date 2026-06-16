---
description: >-
  Use the VRPN Sample to verify that OptiTrack data is streaming through the
  VRPN protocol.
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/developer-tools/vrpn-sample
---

# VRPN Sample

## Overview

Mocap data can be livestreamed through the Virtual Reality Peripheral Network (VRPN). To confirm that live OptiTrack data is streaming through this protocol, download and run the VRPN Sample available on our [downloads page](https://optitrack.com/support/downloads?cat=plugin).&#x20;

## VRPN Sample Contents

Once downloaded, the VRPN Sample provides the following content:

* **SimpleVRPNTest** folder, which includes all the files needed to run the VRPN test.
* **thirdparty** folder, which includes files needed to stream VRPN to third-party applications, such as Python or Java.&#x20;
* **License** file for VRPN.

## Streaming Settings

Click the Streaming Settings button in the lower left corner of the Control Deck to open the [Streaming tab](../motive-ui-panes/settings/settings-streaming.md) of the [Application Settings](../motive-ui-panes/settings/) panel.&#x20;

{% hint style="info" %}
The Streaming Settings button is gray <img src="../.gitbook/assets/Control Deck - Streaming Off SMALL (6).png" alt="" data-size="line"> when streaming is disabled and white ![](<../.gitbook/assets/Control Deck - Streaming On SMALL (2).png>) when streaming is enabled.&#x20;
{% endhint %}

<figure><img src="../.gitbook/assets/Settings Streaming for VRPN Sample.png" alt="" width="491"><figcaption><p>Streaming Settings for VRPN</p></figcaption></figure>

#### NatNet Settings

Enable NatNet streaming to access the Local Interface setting. If streaming mocap data to the same computer as Motive, select Loopback. Otherwise, select the IP address for the network that the data should stream to.&#x20;

#### VRPN Settings

Enable VRPN and ensure the correct Broadcast Port is selected.&#x20;

## Run the Simple VRPN Test

* Open the SimpleVRPNTest folder and browse to _x64 > release._&#x20;
* Run **SimpleVRPNTest.exe.** The script will request the required input. Press Enter at any prompt to select the default value, noted in parentheses.&#x20;
  * **Motive IP:** enter the IP address for the Motive computer. This is the same address used in the NatNet settings in Motive.&#x20;
  * **Local IP:** enter the IP address of the computer that the data is streaming to. Use localhost if the data is streaming to the same computer.&#x20;
  * **Port Number:** enter the VRPN port number used in the VRPN settings.&#x20;
  * &#x20;**Object Name:** enter the name of an asset in the mocap volume to track for the test. Make sure to precisely match the case and spacing in Motive when entering the name, or the VRPN test will fail.&#x20;
* Once the requested parameters are entered, the script creates 3 [output files](vrpn-sample.md#output-files) and reports on the status of the test. A successful test will note the number of Tracker Dropped Frames, Duplicate Frames, and Received Frames collected.&#x20;

<figure><img src="../.gitbook/assets/VRPN Test Success 1st run (1).png" alt=""><figcaption><p>A successful VRPN test.</p></figcaption></figure>

### Run Again

Once a connection has been successfully made between the local PC and the Motive server, the sample allows three (3) options for running the test again.&#x20;

{% hint style="warning" %}
The _Run Again_ options are not available if the local PC does not successfully connect to the Motive server. See the [troubleshooting ](vrpn-sample.md#troubleshooting)section below for more information.
{% endhint %}

#### Repeat with the Same Values (r)

Use the R key to re-run the test using the same values. Data will append to the existing [output files](vrpn-sample.md#output-files).&#x20;

#### Prompt to Change Values (P)

The P key allows you to input new data for the Motive IP, Port Number, and Object Name, but does not allow you to change the local IP. This maintains the connection once established rather than dropping and re-connected each time new data is selected to stream.&#x20;

Data is appended to the existing [output files](vrpn-sample.md#output-files) when this option is selected.&#x20;

<figure><img src="../.gitbook/assets/VRPN test - P to prompt new values ANNOTATED.png" alt=""><figcaption></figcaption></figure>

#### Clear for New Input (C)

The C key clears all of the entered data, including the Local IP address with an existing connection. This option overwrites the existing[ output files](vrpn-sample.md#output-files) in the default directory.&#x20;

### Output Files

The Simple VRPN Test creates three output files in the same folder where the sample is located, overwriting any existing files with the same name:

* **output\_analog.txt** includes the analog data of the selected asset, if applicable.&#x20;
* **output\_button.txt** includes the button data of the selected asset, if applicable.&#x20;
* **output\_tracker.txt** includes the tracking data of the selected asset.&#x20;

Analog and Button data are only available when the test tracks a VRPN asset that contains this type of data. For example, a Navigation Controller includes both analog and button data, whereas a puck, skeleton, or trained markerset will have neither.&#x20;

<figure><img src="../.gitbook/assets/VRPN Sample and logs.png" alt=""><figcaption><p>Output results from the VRPN Test are saved in the <em>Release</em> folder.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/VRPN Tracking data output.png" alt="" width="471"><figcaption><p>output_tracker.txt data</p></figcaption></figure>

## Troubleshooting

The VRPN test will fail if it is unable to establish a connection between the host pc and the Motive server, or if any of the input data does not match the data in Motive.&#x20;

The images below show the various errors that can occur.&#x20;

### Connection Issues

Connection issues arise when either the Motive IP or the Local IP information is entered incorrectly or when there is a problem with the network.&#x20;

* Ensure that the Motive IP address entered matches the _Local Interface_ address in Motive's NatNet settings.&#x20;
* If the _Local Interface_ address in Motive is set to _loopback_, use the default _localhost_ option for both the Motive IP and the Local IP.&#x20;
* If all entered values are correct, contact your IT department to ensure you have sufficient privileges to stream data on the selected network.

#### Wrong Motive IP Entered

<figure><img src="../.gitbook/assets/VRPN test failed - Motive IP.png" alt=""><figcaption><p>Connection failed - wrong Motive IP address entered.  </p></figcaption></figure>

#### Wrong Local IP Entered

Example 1 shows the error when an IP address is used:

<figure><img src="../.gitbook/assets/VRPN test failed - Local IP.png" alt=""><figcaption><p>Connection failed - wrong Local IP entered.</p></figcaption></figure>

Example 2 shows the error when an incorrect server name is entered rather than an IP address:

<figure><img src="../.gitbook/assets/VRPN test failed - Local IP typo.png" alt=""><figcaption><p>Connection failed - incomplete Local IP name entered.</p></figcaption></figure>

### No Response&#x20;

Once a connection is made, the VRPN test will attempt to connect to the Rigid Body in Motive using the port number entered. If the test is unsuccessful, the test will return VRPN warning messages stating there was no response from server.&#x20;

Once the issue is identified, use the [Run Again](vrpn-sample.md#run-again) commands to re-run the test with the appropriate inputs.&#x20;

#### Incorrect Port Number

* Ensure that the Port Number entered matches the VRPN Port Number in Motive and correct as necessary.
* Verify with your IT department that the selected port number is open and allows streaming data.

<figure><img src="../.gitbook/assets/VRPN test failed - wrong port.png" alt=""><figcaption><p>Test failed - incorrect Port Number entered.</p></figcaption></figure>

#### Rigid Body Not Found

If the asset selected is not found in the live capture volume (or if the name is misspelled), the VRPN Test will return errors during data collection.

* Ensure that the _Object Name_ entered in the test is an enabled Rigid Body currently being streamed from Motive.&#x20;

<figure><img src="../.gitbook/assets/VRPN test failed - 1st connection RB name ANNOTATED.png" alt=""><figcaption><p>VRPN Test - Selected asset is not found.</p></figcaption></figure>
