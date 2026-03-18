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

<table><thead><tr><th>Command (string)</th><th>Description</th><th>Parameters (String)</th><th>Returns</th></tr></thead><tbody><tr><td>UnitsToMillimeters</td><td><p>Sending this command requests current system’s measurement units, in terms of millimeters.</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "UnitsToMillimeters";
</code></pre></td><td>none</td><td>float</td></tr><tr><td>FrameRate</td><td><p>Queries for the tracking framerate of the system. Returns a float value representing the system framerate.</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "FrameRate";
</code></pre></td><td>none</td><td>float</td></tr><tr><td>CurrentMode</td><td><p>Requests current mode that Motive is in. Returns 0 if Motive is in Live mode. Returns 1 if Motive is in Edit mode.</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "CurrentMode";
</code></pre></td><td>none</td><td>int</td></tr><tr><td>StartRecording</td><td><p>This command initiates recording in Motive</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "StartRecording";
</code></pre></td><td>none</td><td>none</td></tr><tr><td>StopRecording</td><td><p>This command stops recording in Motive</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "StopRecording";
</code></pre></td><td>none</td><td>none</td></tr><tr><td>LiveMode</td><td><p>This command switches Motive to Live mode</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "LiveMode";
</code></pre></td><td>none</td><td>none</td></tr><tr><td>EditMode</td><td><p>This command switches Motive to Edit mode.</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "EditMode";
</code></pre></td><td>none</td><td>None</td></tr><tr><td>TimelinePlay</td><td><p>Starts playback of a <em>Take</em> that is loaded in Motive</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "TimelinePlay";
</code></pre></td><td>none</td><td>none</td></tr><tr><td>TimelineStop</td><td><p>Stops playback of the loaded <em>Take</em></p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "TimelineStop";
</code></pre></td><td>none</td><td>none</td></tr><tr><td>SetPlaybackTakeName</td><td><p>Set playback take</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "SetPlaybackTakeName," + stringTakeName;
</code></pre></td><td>Take name</td><td>None</td></tr><tr><td>SetRecordTakeName</td><td><p>Set a take name to record.</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "SetRecordTakeName," + stringTakeName;
</code></pre></td><td>Take name</td><td>None</td></tr><tr><td>SetCurrentSession</td><td><p>Set current session. If the session name already exists, Motive switches to that session. If the session does not exist, Motive will create a new session. You can use absolute paths to define folder locations.</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "SetCurrentSession," + stringSessionName;&#x3C;/source>&#x3C;source>string command = "SetCurrentSession," + "c:/folder"
</code></pre></td><td>Session name</td><td>None</td></tr><tr><td>CurrentSessionPath</td><td><p>Gets the unix-style path to the current session folder as a string value, including trailing delimiter.</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string folder = "CurrentSessionPath";
</code></pre></td><td>none</td><td>string</td></tr><tr><td>SetPlaybackStartFrame</td><td><p>Set start frame</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "SetPlaybackStartFrame," + stringFrameNumber;
</code></pre></td><td>Frame number</td><td>None</td></tr><tr><td>SetPlaybackStopFrame</td><td><p>Sets stop frame.</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "SetPlaybackStopFrame," + stringFrameNumber;
</code></pre></td><td>Frame number</td><td>None</td></tr><tr><td>SetPlaybackCurrentFrame</td><td><p>Set current frame</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "SetPlaybackCurrentFrame," + stringFrameNumber;
</code></pre></td><td>Frame number</td><td>none</td></tr><tr><td>SetPlaybackLooping</td><td><p>Enable or disable looping in the playback. To disable, zero must be sent along with the command.</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string enablelooping = "SetPlaybackLooping"; 

string disablelooping = "SetPlaybackLooping, 0";
</code></pre></td><td>none</td><td>none</td></tr><tr><td>EnableAsset</td><td><p>Enables tracking of corresponding asset (rigid body / skeleton) from Motive</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "EnableAsset," + stringNodeName;
</code></pre></td><td>Asset name </td><td>None </td></tr><tr><td>DisableAsset </td><td><p>Disables tracking of a corresponding asset (rigid body / skeleton) from Motive.</p><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "DisableAsset," + stringNodeName;
</code></pre></td><td>Asset name </td><td>None </td></tr><tr><td>GetProperty </td><td><p>Queries the server for configured value of a property in Motive. The property name must exactly match the displayed name. This request string must have the following inputs along with the command, each of them separated by a comma.</p><ul><li>Node name</li><li>Property name</li></ul><p><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "GetProperty," + stringNodeName + "," + stringPropertyName;
</code></pre><p>For rigid body assets, Streaming ID of rigid bodies can be used in place of the stringNodeName. For example, string command for getting name of a rigid body with streaming ID of 3 would be:</p><pre data-overflow="wrap"><code>string command = "GetProperty," + "3"+ "," + "Name";
</code></pre><p><em><strong>eSync:2:</strong></em></p><p>Accessing the eSync 2 requires '#' to be included at the beginning of the eSync 2's serial number. If the '#' is not present, it will make the eSync 2 inaccessible. ie. GetProperty, eSync 2 #ES002005, Source Value</p></td><td><ul><li>Node name (if applicable)</li><li>Property name</li></ul></td><td>int</td></tr><tr><td>SetProperty</td><td><p>Requests Motive to configure specified properties. The property name must exactly match the respective name of setting displayed in Motive. Please refer to the <a href="https://v30.wiki.optitrack.com/index.php?title=Properties_pane">Properties pane</a> page for the list of properties. <em>Master Rate</em> can be used for controlling the frame rate of the camera system. For configuring camera settings remotely, use the "model #[serial]" string format.</p><p><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "SetProperty," + stringNodeName + "," + stringPropertyName + "," + stringPropertyValue;
//Sets the frame rate of the camera system to 180FPS.
string command = "SetProperty,Master Rate,180";
// Sets the gain on camera #13003 to 2.
"SetProperty," + "Prime 13 #13003", + "," + "Gain" + "," + "2";
</code></pre><p>For rigid body assets, Streaming ID of rigid bodies can be used in place of the stringNodeName. For example, string command for enabling rigid body with streaming ID of 3 would be:</p><pre data-overflow="wrap"><code>string command = "SetProperty," + "3"+ "," + "Enable" + "," + "True";
</code></pre><p><em><strong>eSync:2:</strong></em></p><p>Accessing the eSync 2 requires '#' to be included at the beginning of the eSync 2's serial number. If the '#' is not present, it will make the eSync 2 inaccessible. ie. GetProperty, eSync 2 #ES002005, Source Value</p></td><td><ul><li>Node name. (Leave it empty if not applicable.)</li><li>Property name</li><li>Desired value</li></ul></td><td>int</td></tr><tr><td>GetTakeProperty </td><td><p>Request property of a Take. You can query property of a specific Take by entering the name, or enter empty string to query the currently loaded take. Most of the properties available in the <a href="https://v30.wiki.optitrack.com/index.php?title=Properties:_Take">Properties: Take</a> can be queried through this command.</p><p><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "GetTakeProperty," + takeName + "," + propertyName;
//Querying for EndFrame number on the currently loaded take. string command = "GetTakeProperty,,End Frame";
</code></pre></td><td><ul><li>Take Name. Leave empty for currently loaded take.</li><li>Name of the property. See <a href="https://v30.wiki.optitrack.com/index.php?title=Properties:_Take">Properties: Take</a>.</li></ul></td><td>Depends on the property type.</td></tr><tr><td>CurrentTakeLength </td><td><p>Request length of current take.</p><p><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "CurrentTakeLength";
</code></pre></td><td>None</td><td>int</td></tr><tr><td>RecalibrateAsset </td><td><p>Recalibrates the asset. Returns integer indicating if command was successful. Zero if successful.<br><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "RecalibrateAsset";
</code></pre></td><td>Asset Name</td><td>int</td></tr><tr><td>ResetAssetOrientation</td><td><p>Reorients the asset. Returns integer indicating if command was successful. Zero if successful.<br><br><em>Sample command string:</em></p><pre data-overflow="wrap"><code>string command = "ResetAssetOrientation";
</code></pre></td><td>Asset Name </td><td>int</td></tr></tbody></table>



### Subscription Commands

_Supported for Motive 3.0 or above._

Subscription commands work with Unicast streaming protocol only. When needed, unicast clients can send subscription commands to receive only specific data types through the data stream. This allows users to minimize the size of streaming packets. For more information, read through the [NatNet: Unicast Data Subscription Commands](natnet-unicast-data-subscription-commands.md) page.

Following is a general format used for the subscription command strings:

* SubscribeToData,\[DataType],\[All or specific asset]
* SubscribeByID,\[DataType],\[ID]

## Sample Use

Below is a sample use of the NatNet commands from the [WinFormsSample](https://v30.wiki.optitrack.com/index.php?title=NatNet:_Sample_Projects) application.

**Start Recording**

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

**Framerate Query**

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

**Setting name of the recorded Take**

```
private void SetRecordingTakeButton_Click(object sender, EventArgs e)
{
    int nBytes = 0;
    byte[] response = new byte[10000];
    String strCommand = "SetRecordTakeName," + RecordingTakeNameText.Text;
    int rc = m_NatNet.SendMessageAndWait(strCommand, out response, out nBytes);
}
```

**Setting Motive Properties**

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
