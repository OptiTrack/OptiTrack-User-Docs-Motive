# NatNet: Creating a Managed (C sharp) Client Application

The following guide references **SampleClientML.cs** client application that is provided with the SDK. This sample demonstrates the use of .NET NatNet assembly for connecting to a NatNet server, receiving a data stream, and parsing and printing out the received data.

{% hint style="info" %}
**SDK/API Support Disclaimer**

We provide developer tools to enable OptiTrack customers across a broad set of applications to utilize their systems in the ways that best suit them. Our Motive API through the NatNet SDK and Camera SDK is designed to enable experienced software developers to integrate data transfer and/or system operation with their preferred systems and pipelines. Sample projects are provided alongside each tool, and we strongly recommend the users to reference or use the samples as reliable starting points. The following list specifies the range of support that will be provided for the SDK tools:

* Using the SDK tools requires background knowledge on software development; therefore, we do not provide support for basic project setup, compiling, and linking when using the SDK/API to create your own applications.
* Although we ensure the SDK tools and their libraries work as intended, we do not provide support for custom developed applications that have been programmed or modified by users using the SDK tools.
* Ticketed support will be provided for licensed Motive users using the Motive API and/or the NatNet SDK tools from the included libraries and sample source codes only.
* The Camera SDK is a free product, and therefore we do not provide free ticketed support for it.
* For other questions, please check out the [NaturalPoint forums](https://forums.naturalpoint.com/). Very often, similar development issues get reported and solved there.
{% endhint %}

## 1. NatNet Library

When developing a managed client applications, you will need to link both native and managed DLL files(**NatNetLib.dll** and **NatNetML.dll**). The managed NatNet assembly is derived from the native library, so without the NatNetLib.dll, NatNetML.dll will not be imported properly. These library files can be found in the `NatNetSDK\lib` folder for 32-bit platform and in the `NatNetSDK\lib\x64` folder for 64-bit platform. Make sure these DLL files are properly linked and placed alongside the executables.

Also, when using the NatNetML assembly, place the NatNetML.xml file alongside imported DLL file. This allows XML documentation to be included as a reference. These library files can be found in the `NatNetSDK\lib` folder for 32-bit platform and in the `NatNetSDK\lib\x64` folder for 64-bit platform. Make sure these DLL files are properly linked and placed alongside the executables.

## 2. Connect

#### **a. Create a NatNetClientML object**

Tracking server and client network is established through an instance of NatNet client object (NatNetML.NatNetClientML). Also, this NatNetClientML object will be used for receiving tracking data and sending NatNet commands to and from the server application. When instantiating the NatNetClientML object, input an integer value for determining the desired type of UDP connection; whether it connects via multicast (0) or unicast (1).

#### **\[C#] SampleClientML.cs : Instantiating NatNetClientML**

```
/*  [NatNet] Network connection configuration    */
private static NatNetML.NatNetClientML m_NatNet;    // The client instance
private static string strLocalIP = "127.0.0.1";     // Local IP address (string)
private static string strServerIP = "127.0.0.1";    // Server IP address (string)
private static int iConnectionType = 0;             // Connection Type
```

```
static void connectToServer()
{
    /*  [NatNet] Instantiate the client object  */
    m_NatNet = new NatNetML.NatNetClientML(iConnectionType);

    /*  [NatNet] Checking verions of the NatNet SDK library  */
    int[] verNatNet = new int[4];           // Saving NatNet SDK version number
    verNatNet = m_NatNet.NatNetVersion();
    Console.WriteLine("NatNet SDK Version: {0}.{1}.{2}.{3}", verNatNet[0], verNatNet[1], verNatNet[2], verNatNet[3]);
 
    /*  [NatNet] Connecting to the Server    */
    Console.WriteLine("\nConnecting...\n\tLocal IP address: {0}\n\tServer IP Address: {1}\n\n", strLocalIP, strServerIP);
    m_NatNet.Initialize(strLocalIP, strServerIP);
}
```

#### **b. Connect to Server**

To connect to the server, use the **Initialize** method from the instantiated NatNetClientML object. When calling this method, input the proper Local IP address and the Server IP address. The local IP address must match the IP address of the host PC, and the server IP address must match the address that the server is streaming onto, which is defined in the [Data Streaming](../../motive/data-streaming.md) panel in Motive.

#### **\[C#] SampleClientML.cs : Connect to Server. Initialize**

```
/*  [NatNet] Network connection configuration    */
private static NatNetML.NatNetClientML m_NatNet;    // The client instance
private static string strLocalIP = "127.0.0.1";     // Local IP address (string)
private static string strServerIP = "127.0.0.1";    // Server IP address (string)
private static int iConnectionType = 0;             // Connection Type
```

```
static void connectToServer()
{
    /*  [NatNet] Instantiate the client object  */
    m_NatNet = new NatNetML.NatNetClientML(iConnectionType);

    /*  [NatNet] Checking verions of the NatNet SDK library  */
    int[] verNatNet = new int[4];           // Saving NatNet SDK version number
    verNatNet = m_NatNet.NatNetVersion();
    Console.WriteLine("NatNet SDK Version: {0}.{1}.{2}.{3}", verNatNet[0], verNatNet[1], verNatNet[2], verNatNet[3]);

    /*  [NatNet] Connecting to the Server    */
    Console.WriteLine("\nConnecting...\n\tLocal IP address: {0}\n\tServer IP Address: {1}\n\n", strLocalIP, strServerIP);
    m_NatNet.Initialize(strLocalIP, strServerIP);
}
```

{% hint style="info" %}
**Server Discovery**

You can also use the NatNetServerDiscover class to auto-detect available servers to connect to. This is demonstrated in the WinFromSamplesApp\*\*.\*\*
{% endhint %}

#### **c. Confirm connection**

To confirm whether the client has successfully connected to the server application, let's try querying for a [ServerDescriptor](natnet-data-types.md#dataset-descriptions) packet using the GetServerDescription method. If the server is connected, the corresponding server descriptions will be obtained. This method returns an [ErrorCode](natnet-class-function-reference.md#errorcode) value, and when successfully operated it will return a value of 0.

#### **\[C#] SampleClientML.cs : GetServerDescription**

```
static bool fetchServerDescriptor()
{
    NatNetML.ServerDescription m_ServerDescriptor = new NatNetML.ServerDescription();
    int errorCode = m_NatNet.GetServerDescription(m_ServerDescriptor);

    if (errorCode == 0)
    {
        Console.WriteLine("Success: Connected to the server\n");
        parseSeverDescriptor(m_ServerDescriptor);
        return true;
    }
    else
    {
        Console.WriteLine("Error: Failed to connect. Check the connection settings.");
        Console.WriteLine("Program terminated (Enter ESC to exit)");
        return false;
    }
}
```

## 3. Get DataDescriptions

As explained in the [NatNet: Data Types](natnet-data-types.md) page, there are two kinds of data formats included in streamed NatNet packets; one of which is Data Descriptions. In managed NatNet assembly, data descriptions for each of the assets (Marker Sets, Rigid Bodies, Skeletons, and force plates) included in the capture session is stored in a **DataDescriptor** class. A single capture take (or live streaming) may contain more than one assets, and respectively, there may be more than one data descriptions. For this reason, data descriptions are stored in a list format.

#### **a. GetDataDescription**

GetDataDescriptions method in the NatNetClientML class queries a list of _DataDescriptors_ from the connected server and saves it in a declared list of _NatNetML.DataDescriptions_. In the SampleClientML sample, the following lines are executed to accomplish this:

#### **\[C#] SampleClientML.cs : GetDataDescription**

```
/*  List for saving each of datadescriptors */
private static List<NatNetML.DataDescriptor> m_DataDescriptor = new List<NatNetML.DataDescriptor>();

static void fetchDataDescriptor()
{
    /*  [NatNet] Fetch Data Descriptions. Instantiate objects for saving data descriptions and frame data    */        
    bool result = m_NatNet.GetDataDescriptions(out m_DataDescriptor);

    if (result)
    {
        Console.WriteLine("Success: Data Descriptions obtained from the server.");
        parseDataDescriptor(m_DataDescriptor);
    }
    else
    {
        Console.WriteLine("Error: Could not get the Data Descriptions");
    }
        Console.WriteLine("\n");
}
```

#### **b. ParseDataDescription**

After obtaining a list of data descriptions, use the saved DataDescriptor objects to access and output data descriptions as needed. In many cases, it is better to re-organize and save the received descriptor objects into separate lists, or into hashtables, of corresponding data types, so that they can be referenced later in the program.

#### **\[C#] SampleClientML.cs : Parsing/Saving Data Descriptions**

```
static void parseDataDescriptor(List<NatNetML.DataDescriptor> description)
{
    //  [NatNet] Request a description of the Active Model List from the server. 
    //  This sample will list only names of the data sets, but you can access 
    int numDataSet = description.Count;
    Console.WriteLine("Total {0} data sets in the capture:", numDataSet);

    for (int i = 0; i < numDataSet; ++i)
    {
        int dataSetType = description[i].type;
        // Parse Data Descriptions for each data sets and save them in the delcared lists and hashtables for later uses.
        switch (dataSetType){
            case ((int) NatNetML.DataDescriptorType.eMarkerSetData):
                  NatNetML.MarkerSet mkset = (NatNetML.MarkerSet)description[i];
                  Console.WriteLine("\tMarkerSet ({0})", mkset.Name);
                  break;

            case ((int) NatNetML.DataDescriptorType.eRigidbodyData):
                  NatNetML.RigidBody rb = (NatNetML.RigidBody)description[i];
                  Console.WriteLine("\tRigidBody ({0})", rb.Name);

                  // Saving Rigid Body Descriptions
                  mRigidBodies.Add(rb);
                  break;

            case ((int) NatNetML.DataDescriptorType.eSkeletonData):
                  NatNetML.Skeleton skl = (NatNetML.Skeleton)description[i];
                  Console.WriteLine("\tSkeleton ({0}), Bones:", skl.Name);
 
                  //Saving Skeleton Descriptions
                  mSkeletons.Add(skl);
 
                  // Saving Individual Bone Descriptions
                  for (int j = 0; j < skl.nRigidBodies; j++)
                  {
                      Console.WriteLine("\t\t{0}. {1}", j + 1, skl.RigidBodies[j].Name);
                      int uniqueID = skl.ID * 1000 + skl.RigidBodies[j].ID;
                      int key = uniqueID.GetHashCode();
                      htSkelRBs.Add(key, skl.RigidBodies[j]); //Saving the bone segments onto the hashtable
                  }
                  break;

            case ((int) NatNetML.DataDescriptorType.eForcePlateData):
                    NatNetML.ForcePlate fp = (NatNetML.ForcePlate)description[i];
                    Console.WriteLine("\tForcePlate ({0})", fp.Serial);

                    // Saving Force Plate Channel Names
                    mForcePlates.Add(fp);
         
                    for (int j = 0; j < fp.ChannelCount; j++)
                    {
                          Console.WriteLine("\t\tChannel {0}: {1}", j + 1, fp.ChannelNames[j]);
                    }
                    break;

            default:
                  // When a Data Set does not match any of the descriptions provided by the SDK.
                  Console.WriteLine("\tError: Invalid Data Set");
                  break;
    }
  }
}
```

## 4. Get Frame Data

Now, let's obtain the tracking data from the connected server. Tracking data for a captured frame is stored in an instance of _NatNetML.FrameOfMocapData_. As explained in the [Data Types](natnet-data-types.md) page, every FrameOfMocapData contains tracking data of the corresponding frame. There are two approaches for obtaining frame data using the client object; by calling the GetLastFrameOfData method or by linking a callback handler function using the **OnFrameReady** method. In general, creating a callback function is recommended because this approach ensures that every frame of tracking data gets received.

#### **a. Callback Handler (OnFrameReady)**

The best way to receive tracking data without losing any of its frames is to create a callback handler function for processing the data. The **OnFrameReady** event type from the client object can be used to declare a callback event, and the linked function gets called each time a frame is received from the server. Setting up a frame handler function will ensure that every frame gets processed promptly. However, these handler functions should return as quickly as possible to prevent accumulation of frames due to processing latency within the handler.

```
m_NatNet.OnFrameReady += new NatNetML.FrameReadyEventHandler(frameHandlerFunction);
```

* OnFrameReady2: Alternate function signatured frame ready callback handler for .NET applications/hosts that don't support the _OnFrameReady_ event type defined above (e.g. MATLAB)

#### **\[C#] SampleClientML.cs : Frame Data Callback Handler**

```
Console.WriteLine("============================= FRAME OF DATA ===================================\n");
Console.WriteLine("Now Fetching the Frame Data\n");

/*  [NatNet] Assigning a event handler function for fetching frame data each time a frame is received   */
m_NatNet.OnFrameReady += new NatNetML.FrameReadyEventHandler(parseFrameData);

Console.WriteLine("Success: Data Port Connected \n");

/// [NatNet] parseFrameData will be called when a frame of Mocap data has is received from the server application
static void parseFrameData(NatNetML.FrameOfMocapData data, NatNetML.NatNetClientML client)
{

    /*  Exception handler for cases where assets are added or removed.
    Data description is re-obtained in the main function so that contents
    in the frame handler function is kept minimal. */

    if (( data.bTrackingModelsChanged == true || data.nRigidBodies != mRigidBodies.Count ||
      data.nSkeletons != mSkeletons.Count || data.nForcePlates != mForcePlates.Count))
    {
              assetChanged = true;
    }

    /*  Processing and outputting frame data every 200th frame.
    This conditional statement is included in order to simplify the program output */

    if(data.iFrame % 200 == 0)
    {
        if (data.bRecording == false)
        Console.WriteLine("Frame #{0} Received:", data.iFrame);
    
    else if (data.bRecording == true)
        Console.WriteLine("[Recording] Frame #{0} Received:", data.iFrame);
        processFrameData(data);
    }
}
```

#### **b. Single Frame (GetLastFrameOfData)**

Calling the GetLastFrameOfData method returns a FrameOfMocapData of the most recent frame that was streamed out from the connected server application. This approach is should only be used for .NET applications/hosts that do not support the OnFrameReady callback handler function.

```
FrameOfMocapData data = m_NatNet.GetLastFrameOfData();
```

{% hint style="info" %}
This function is supported in NatNetML only. Native implementations should always use the callback handlers.
{% endhint %}

## 5. Disconnect

When exiting the program, call **Uninitialize** method using the connected client object and disconnect the client application from the server.

#### **\[C#] SampleClientML.cs : Disconnect**

```
    /*  [NatNet] Disabling data handling function   */
    m_NatNet.OnFrameReady -= parseFrameData;

    /*  Clearing Saved Descriptions */
    mRigidBodies.Clear();
    mSkeletons.Clear();
    htSkelRBs.Clear();
    mForcePlates.Clear();

    /*  Disconnecting from the Server  */
    m_NatNet.Uninitialize();
} // End. Main()
```
