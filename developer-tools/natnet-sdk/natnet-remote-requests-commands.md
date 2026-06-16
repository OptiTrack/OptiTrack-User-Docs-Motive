---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/developer-tools/natnet-sdk/natnet-remote-requests-commands
---

# NatNet: Remote Requests/Commands

## Remote Requests/Commands

The NatNet SDK features sending remote commands/requests from a client application over to a connected server application (i.e. Motive).

The _SendMessageAndWait_ method under NatNetClient class is the core method for sending remote commands. This function takes in a string value of the command and sends it over to the connected Motive server each time it's called, and once the server receives the remote command, corresponding actions will be performed. Please note that only a selected set of commands can be understood by the server, which are listed under the [remote commands](natnet-remote-requests-commands.md#remote-commands) chart below.

NatNet commands are sent via the UDP connection, 1510 port by default.

{% hint style="info" %}
For a sample use of NatNet commands, refer to the provided [WinFormSample](natnet-sample-projects.md).
{% endhint %}

### NatNetClient::SendMessageAndWait

```
ErrorCode	SendMessageAndWait( const char* szRequest,
				    void** ppServerResponse, 
					int* pResponseSize );
```

```
ErrorCode	SendMessageAndWait( const char* szRequest,
				    int tries, int timeout, 
				    void** ppServerResponse,
				    int* pResponseSize );
```

**Description**

Sends a NatNet command to the NatNet server and waits for a response.

**Input Parameters:**

* szRequest: NatNet command string, which is one of the commands listed on the below [remote commands](natnet-remote-requests-commands.md#remote-commands) chart. If the command requires input parameters, corresponding parameters should be included in the command with comma delimiters. (e.g. string strCommand = "SetPlaybackTakeName," + TakeName;).
* tries: Number of attempts to send the command. Default: 10.
* timeout: Number of milliseconds to wait for a response from the server before the call times out. Default: 20.
* ppServerResponse: Server response for the remote command. The response format depends on which command is sent out.
* pResponseSize: Number of bytes in response

**Returns:**

ErrorCode, On success, it returns 0 or ErrorCode\_OK.

### Remote Commands

Motive Supported NatNet Commands/Requests

```
string command = "LiveMode";
```

<details>

<summary>UnitsToMillimeters</summary>

Sending this command requests current system’s measurement units, in terms of millimeters.

**Parameters (String):** None

**Returns:** Float

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "UnitsToMillimeters";
```
{% endcode %}

</details>

<details>

<summary>FrameRate</summary>

Queries for the tracking framerate of the system. Returns a float value representing the system framerate.

**Parameters (String):** None

**Returns:** Float

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "FrameRate";
```
{% endcode %}

</details>

<details>

<summary>CurrentMode</summary>

Requests current mode that Motive is in. Returns 0 if Motive is in Live mode. Returns 1 if Motive is in Edit mode.

**Parameters (String):** None

**Returns:** Int

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "CurrentMode";
```
{% endcode %}

</details>

<details>

<summary>StartRecording</summary>

This command initiates recording in Motive.

**Parameters (String):** None

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "StartRecording";
```
{% endcode %}

</details>

<details>

<summary>StopRecording</summary>

This command stops recording in Motive.

**Parameters (String):** None

**Returns:** None

_Sample command string:_

```
string command = "StopRecording";
```

</details>

<details>

<summary>LiveMode</summary>

This command switches Motive to Live mode.

**Parameters (String):** None

**Returns:** None

_Sample command string_

{% code overflow="wrap" %}
```
string command = "LiveMode";
```
{% endcode %}

</details>

<details>

<summary>EditMode</summary>

This command switches Motive to Edit mode.

**Parameters (String):** None

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "EditMode";
```
{% endcode %}

</details>

<details>

<summary>TimelinePlay</summary>

Starts playback of a _Take_ that is loaded in Motive.

**Parameters (String):** None

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "TimelinePlay";
```
{% endcode %}

</details>

<details>

<summary>TimelineStop</summary>

Stops playback of the loaded _Take._

**Parameters (String):** None

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "TimelineStop";
```
{% endcode %}

</details>

<details>

<summary>SetPlaybackTakeName</summary>

Set playback take.

**Parameters (String):** Take name

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "SetPlaybackTakeName," + stringTakeName;
```
{% endcode %}

</details>

<details>

<summary>SetRecordTakeName</summary>

Set a take name to record.

**Parameters (String):** Take name

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "SetRecordTakeName," + stringTakeName;
```
{% endcode %}

</details>

<details>

<summary>SetCurrentSession</summary>

Set current session. If the session name already exists, Motive switches to that session. If the session does not exist, Motive will create a new session. You can use absolute paths to define folder locations.

**Parameters (String):** Session name

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "SetCurrentSession," + stringSessionName;</source><source>string command = "SetCurrentSession," + "c:/folder"
```
{% endcode %}

</details>

<details>

<summary>CurrentSessionPath</summary>

Gets the unix-style path to the current session folder as a string value, including trailing delimiter.

**Parameters (String):** none

**Returns:** string

_Sample command string:_

{% code overflow="wrap" %}
```
string folder = "CurrentSessionPath";
```
{% endcode %}

</details>

<details>

<summary>SetPlaybackStartFrame</summary>

Set start frame.

**Parameters (String):** Frame Number

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "SetPlaybackStartFrame," + stringFrameNumber;
```
{% endcode %}

</details>

<details>

<summary>SetPlaybackStopFrame</summary>

Sets stop frame.

**Parameters (String):** Frame Number

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "SetPlaybackStopFrame," + stringFrameNumber;
```
{% endcode %}

</details>

<details>

<summary>SetPlaybackCurrentFrame</summary>

Set current frame.

**Parameters (String):** Frame Number

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "SetPlaybackCurrentFrame," + stringFrameNumber;
```
{% endcode %}

</details>

<details>

<summary>SetPlaybackLooping</summary>

Enable or disable looping in the playback. To disable, zero must be sent along with the command.

**Parameters (String):** None

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string enablelooping = "SetPlaybackLooping"; 

string disablelooping = "SetPlaybackLooping, 0";
```
{% endcode %}

</details>

<details>

<summary>EnableAsset</summary>

Enables tracking of corresponding asset (rigid body / skeleton) from Motive.

**Parameters (String):** Asset name

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "EnableAsset," + stringNodeName;
```
{% endcode %}

</details>

<details>

<summary>DisableAsset </summary>

Disables tracking of a corresponding asset (rigid body / skeleton) from Motive.

**Parameters (String):** Asset name

**Returns:** None

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "DisableAsset," + stringNodeName;
```
{% endcode %}

</details>

<details>

<summary>GetProperty </summary>

Queries the server for configured value of a property in Motive. The property name must exactly match the displayed name. This request string must have the following inputs along with the command, each of them separated by a comma.

* Node name
* Property name

**Parameters (String):**&#x20;

* Node name (if applicable)
* Property name

**Returns:** Int

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "GetProperty," + stringNodeName + "," + stringPropertyName;
```
{% endcode %}

For rigid body assets, Streaming ID of rigid bodies can be used in place of the stringNodeName. For example, string command for getting name of a rigid body with streaming ID of 3 would be:

{% code overflow="wrap" %}
```
string command = "GetProperty," + "3"+ "," + "Name";
```
{% endcode %}

_**eSync:2:**_

Beginning with Motive 3.1, accessing the eSync 2 no longer requires the inclusion of the device's serial number. For example:

```
GetProperty, eSync 2, SyncOutput1Enabled
```

</details>

<details>

<summary>SetProperty</summary>

Requests Motive to configure specified properties. The property name must exactly match the respective name of setting displayed in Motive. Please refer to the [Properties pane](../../motive-ui-panes/properties-pane/) page for the list of properties. _Master Rate_ can be used for controlling the frame rate of the camera system. For configuring camera settings remotely, use the "model #\[serial]" string format.

**Parameters (String):**&#x20;

* Node name (Leave empty if not applicable)
* Property name
* Desired value

**Returns:** Int

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "SetProperty," + stringNodeName + "," + stringPropertyName + "," + stringPropertyValue;
//Sets the frame rate of the camera system to 180FPS.
string command = "SetProperty,Master Rate,180";
// Sets the gain on camera #13003 to 2.
"SetProperty," + "Prime 13 #13003", + "," + "Gain" + "," + "2";
```
{% endcode %}

For rigid body assets, Streaming ID of rigid bodies can be used in place of the stringNodeName. For example, string command for enabling rigid body with streaming ID of 3 would be:

{% code overflow="wrap" %}
```
string command = "SetProperty," + "3"+ "," + "Enable" + "," + "True";
```
{% endcode %}

_**eSync:2:**_

Beginning with Motive 3.1, accessing the eSync 2 no longer requires the inclusion of the device's serial number.

</details>

<details>

<summary>GetTakeProperty </summary>

Request property of a Take. You can query property of a specific Take by entering the name, or enter empty string to query the currently loaded take. Most of the properties available in the [Properties: Take](../../motive-ui-panes/properties-pane/properties-pane-take.md) can be queried through this command.

**Parameters (String):**&#x20;

* Take Name. Leave empty for currently loaded take.
* Name of the property. See [Properties: Take](../../motive-ui-panes/properties-pane/properties-pane-take.md).

**Returns:** Depends on the property type.

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "GetTakeProperty," + takeName + "," + propertyName;
//Querying for EndFrame number on the currently loaded take. string command = "GetTakeProperty,,End Frame";
```
{% endcode %}

</details>

<details>

<summary>CurrentTakeLength </summary>

Request length of current take.

**Parameters (String):** None

**Returns:** Int

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "CurrentTakeLength";
```
{% endcode %}

</details>

<details>

<summary>RecalibrateAsset </summary>

Recalibrates the asset. Returns integer indicating if command was successful. Zero if successful.

**Parameters (String):** Asset Name

**Returns:** Int

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "RecalibrateAsset";
```
{% endcode %}

</details>

<details>

<summary>ResetAssetOrientation</summary>

Reorients the asset. Returns integer indicating if command was successful. Zero if successful.

**Parameters (String):** Asset Name

**Returns:** Int

_Sample command string:_

{% code overflow="wrap" %}
```
string command = "ResetAssetOrientation";
```
{% endcode %}

</details>

### Subscription Commands

_Supported for Motive 3.0 or above._

Subscription commands work with Unicast streaming protocol only. When needed, unicast clients can send subscription commands to receive only specific data types through the data stream. This allows users to minimize the size of streaming packets. For more information, read through the [NatNet: Unicast Data Subscription Commands](natnet-unicast-data-subscription-commands.md) page.

Following is a general format used for the subscription command strings:

* SubscribeToData,\[DataType],\[All or specific asset]
* SubscribeByID,\[DataType],\[ID]

## Sample Use

Below is a sample use of the NatNet commands from the [WinFormsSample](https://v30.wiki.optitrack.com/index.php?title=NatNet:_Sample_Projects) application.

**Start Recording**

{% code overflow="wrap" %}
```
private void RecordButton_Click(object sender, EventArgs e)
{
	string command = "StartRecording";

	int nBytes = 0;
	byte[] response = new byte[10000];
	int rc = m_NatNet.SendMessageAndWait(command, 3, 100, out response, out nBytes);
	if (rc != 0)
	{
		OutputMessage(command + " not handled by server");
	}
	else
	{
		int opResult = System.BitConverter.ToInt32(response, 0);
		if (opResult == 0)
			OutputMessage(command + " handled and succeeded.");
		else
			OutputMessage(command + " handled but failed.");
	}
}
```
{% endcode %}

**Framerate Query**

{% code overflow="wrap" %}
```
// [NatNet] [optional] Query mocap server for the current camera framerate
int nBytes = 0;
byte[] response = new byte[10000];
int rc;
rc = m_NatNet.SendMessageAndWait("FrameRate", out response, out nBytes);

if (rc == 0)
{
    try
    {
        m_ServerFramerate = BitConverter.ToSingle(response, 0);
        OutputMessage(String.Format("   Camera Framerate: {0}", m_ServerFramerate));
    }
    catch (System.Exception ex)
    {
        OutputMessage(ex.Message);
    }
}
```
{% endcode %}

**Setting name of the recorded Take**

{% code overflow="wrap" %}
```
private void SetRecordingTakeButton_Click(object sender, EventArgs e)
{
    int nBytes = 0;
    byte[] response = new byte[10000];
    String strCommand = "SetRecordTakeName," + RecordingTakeNameText.Text;
    int rc = m_NatNet.SendMessageAndWait(strCommand, out response, out nBytes);
}
```
{% endcode %}

**Setting Motive Properties**

{% code overflow="wrap" %}
```
private void SetPropertyButton_Click(object sender, EventArgs e)
{
    int nBytes = 0;
    byte[] response = new byte[10000];
    string command = "SetProperty," + NodeNameText.Text + "," + PropertyNameText.Text + "," + PropertyValueText.Text;
    int rc = m_NatNet.SendMessageAndWait(command, out response, out nBytes);
    if (rc != 0)
    {
         OutputMessage(command + " not handled by server");
     }
    else
    {
        int opResult = System.BitConverter.ToInt32(response, 0);
        if (opResult == 0)
            OutputMessage(command + " handled and succeeded.");
        else
            OutputMessage(command + " handled but failed.");
    }
}
```
{% endcode %}
