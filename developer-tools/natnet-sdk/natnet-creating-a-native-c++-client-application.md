# NatNet: Creating a Native (C++) Client Application

This guide covers essential points to developing a native client application using the NatNet SDK. The guideline uses sample codes in the SampleClient.cpp application in the `\NatNet SDK\Sample` folder, please refer to this project as an additional reference.

{% hint style="info" %}
**SDK/API Support Disclaimer**

We provide developer tools to enable OptiTrack customers across a broad set of applications to utilize their systems in the ways that best suit them. Our Motive API through the NatNet SDK and Camera SDK is designed to enable experienced software developers to integrate data transfer and/or system operation with their preferred systems and pipelines. Sample projects are provided alongside each tool, and we strongly recommend the users to reference or use the samples as reliable starting points. The following list specifies the range of support that will be provided for the SDK tools:

* Using the SDK tools requires background knowledge on software development; therefore, we do not provide support for basic project setup, compiling, and linking when using the SDK/API to create your own applications.
* Although we ensure the SDK tools and their libraries work as intended, we do not provide support for custom developed applications that have been programmed or modified by users using the SDK tools.
* Ticketed support will be provided for licensed Motive users using the Motive API and/or the NatNet SDK tools from the included libraries and sample source codes only.
* The Camera SDK is a free product, and therefore we do not provide free ticketed support for it.
* For other questions, please check out the [NaturalPoint forums](https://forums.naturalpoint.com/). Very often, similar development issues get reported and solved there.
{% endhint %}

### 1. Import Library

**a. Link the Library**

When developing a native NatNet client application, NatNetLib.dll file needs to be linked to the project and placed alongside its executable in order to utilize the library classes and functions.

**b. Include the Header Files**

After linking the library, include the header files within your application and import required library declarations. The header files are located in the `NatNet SDK/include` folder.

1. include "NatNetTypes.h"
2. include "NatNetClient.h"

[NatNet SDK](./)

### 2. Connect

#### a. Create a Client Object

Connection to a NatNet server application is accomplished through an instance of NatNetClient object. The client object is instantiated by calling the NatNetClient constructor with desired connection protocol (Multicast/Unicast) as its argument. Designate a desired connection protocol and instantiate the client object. In the SampleClient example, this step is done within the CreateClient function.

* ConnectionType\_Multicast = 0
* ConnectionType\_Unicast = 1

```
int CreateClient(ConnectionType connectionType) {
  // release previous server
   if(g_pClient)
   {
       g_pClient -> Disconnect();
       delete g_pClient;
   }
      // create NatNet client
   g_pClient = new NatNetClient(connectionType);
```

#### b. Discover Server Address

The NatNet SDK includes functions for discovering available tracking servers. While client applications can connect to a tracking server by simply inputting the matching IP address, the auto-detection feature provides easier use.The [NatNet\_BroadcastServerDiscovery](natnet-class-function-reference.md) function searches the network for a given amount of time and reports IP addresses of the available servers. The reported server information can be used to establish the connection. The [NatNet\_CreateAsyncServerDiscovery](natnet-class-function-reference.md) function continuously searches for available tracking servers by repeatedly calling a callback function. This is all demonstrated in the SampleClient application.

**\[C++] SampleClient.cpp : Server Discovery**

```
const unsigned int kDiscoveryWaitTimeMillisec = 5 * 1000; // Wait 5 seconds for responses.
const int kMaxDescriptions = 10; // Get info for, at most, the first 10 servers to respond. sNatNetDiscoveredServer servers[kMaxDescriptions]; 
 int actualNumDescriptions = kMaxDescriptions;
 NatNet_BroadcastServerDiscovery( servers, &actualNumDescriptions );
 if ( actualNumDescriptions < kMaxDescriptions ) {
    // If this happens, more servers responded than the array was able to store.
 }
```

#### c. Connect to Server

Now that you have instantiated a NatNetClient object, connect the client to the server application at the designated IP address by calling the [NatNetClient::Connect](natnet-class-function-reference.md#natnetclient-connect) method.The Connect method requires a sNatNetClientConnectParams struct for the communication information; including the local IP address that the client is running on and the server IP address that the tracking data is streamed to. It is important that the client connects to appropriate IP addresses; otherwise, the data will not be received.Once the connection is established, you can use methods within the NatNetClient object to send commands and query data.

```
 typedef struct sNatNetClientConnectParams {
 ConnectionType connectionType;
   uint16_t serverCommandPort;
   uint16_t serverDataPort;
   const char* serverAddress;
   const char* localAddress;
   const char* multicastAddress;
   if defined(__cplusplus) {
        sNatNetClientConnectParams()
       : connectionType( ConnectionType_Multicast )
       , serverCommandPort( 0 )
       , serverDataPort( 0 )
       , serverAddress( NULL )
       , localAddress( NULL )
       , multicastAddress( NULL )
   }
   endif {
    sNatNetClientConnectParams;
  }
}
```

**\[C++] SampleClient.cpp : Connect to the Server**

#### d. Confirm Connection

Now that the NatNetClient object is connected, let’s confirm the connection by querying the server for its descriptions. This can be obtained by calling the [NatNetClient::GetServerDescription](natnet-class-function-reference.md#natnetclient-getserverdescription) method and the information gets saved in the provided instance of sServerDescriptions. This is also demonstrated in the CreateClient function of the SampleClient project.

**\[C++] SampleClient.cpp : Request Server Description**

```
// print server info
 memset( &g_serverDescription, 0, sizeof( g_serverDescription ) );
 ret = g_pClient->GetServerDescription( &g_serverDescription );
 if ( ret != ErrorCode_OK || ! g_serverDescription.HostPresent )
 {
    printf("Unable to connect to server. Host not present. Exiting.");
    return 1;
 }
 printf("[SampleClient] Server application info:\n");

 printf("Application: %s (ver. %d.%d.%d.%d)\n", g_serverDescription.szHostApp, g_serverDescription.HostAppVersion[0],
         g_serverDescription.HostAppVersion[1],g_serverDescription.HostAppVersion[2],
         g_serverDescription.HostAppVersion[3]);

 printf("NatNet Version: %d.%d.%d.%d\n", g_serverDescription.NatNetVersion[0], g_serverDescription.NatNetVersion[1],
         g_serverDescription.NatNetVersion[2], g_serverDescription.NatNetVersion[3]);

 printf( "Client IP:%s\n", g_connectParams.localAddress );
 printf( "Server IP:%s\n", g_connectParams.serverAddress );
 printf("Server Name:%s\n\n", g_serverDescription.szHostComputerName);
```

You can also confirm connection by sending a NatNet remote command to the server. NatNet commands are sent by calling the [NatNetClient::SendMessageAndWait](natnet-class-function-reference.md#natnetclient-sendmessageandwait) method with supported [NatNet Command](natnet-class-function-reference.md) as one of its input arguments. The following sample sends a command for querying the number of analog sample for each of the mocap frames. If the client is successfully connected to the server, this method will save the data and return 0.

**\[C++] SampleClient.cpp : Send NatNet Commands**

```
// send/receive test request
printf("[SampleClient] Sending Test Request\n");
void* pResult;
int ret = 0;
int nBytes = 0;

// Querying configured system frame rate from the connected server
'''ret = g_pClient -> SendMessageAndWait("AnalogSamplesPerMocapFrame", &pResult, &nBytes);'''

if (ret == ErrorCode_OK)
{
 analogSamplesPerMocapFrame = *((int*)pResult);
 printf("Analog Samples Per Mocap Frame : %d", analogSamplesPerMocapFrame);
}
```

### 3. Get DataDescriptions

#### a. Fetching Data Description

Now that the client application is connected, [data descriptions](natnet-data-types.md#dataset-descriptions) for the streamed capture session can be obtained from the server. This can be done by calling the [NatNetClient::GetDataDescriptionList](natnet-class-function-reference.md#natnetclient-getdatadescriptionlist) method and saving the descriptions list into an instance of _sDataDescriptions_. From this instance, the client application can figure out how many assets are in the scene as well as their descriptions.This is done by the following line in the SampleClient project:Collapse

**\[C++] SampleClient.cpp : Get Data Descriptions**

```
// Retrieve Data Descriptions from server printf("\n\n[SampleClient] Requesting Data Descriptions..."); sDataDescriptions* pDataDefs = NULL; iResult = g_pClient->GetDataDescriptions(&pDataDefs);
if (iResult != ErrorCode_OK || pDataDefs == NULL){
printf("[SampleClient] Unable to retrieve Data Descriptions.");
}
```

#### b. Parsing Data Description

After an sDataDescriptions instance has been saved, data descriptions for each of the assets (marker, Rigid Body, Skeleton, and force plate from the server) can be accessed from it.Collapse

**\[C++] SampleClient.cpp : Parsing Data Descriptions**

```
// Retrieve Data Descriptions from server printf("\n\n[SampleClient] Requesting Data Descriptions..."); sDataDescriptions* pDataDefs = NULL; iResult = g_pClient->GetDataDescriptions(&pDataDefs);
if (iResult != ErrorCode_OK || pDataDefs == NULL) { Retrieve Data Descriptions from server printf("\n\n[SampleClient] Requesting Data Descriptions..."); sDataDescriptions* pDataDefs = NULL; 
iResult = g_pClient->GetDataDescriptions(&pDataDefs);
if (iResult != ErrorCode_OK || pDataDefs == NULL) {
    printf("[SampleClient] Unable to retrieve Data Descriptions.");
    } 
    else {
    printf("[SampleClient] Received %d Data Descriptions:\n", pDataDefs->nDataDescriptions );
   for(int i=0; i < pDataDefs->nDataDescriptions; i++)
   {
           printf("Data Description # %d (type=%d)\n", i, pDataDefs->arrDataDescriptions[i].type);
           if(pDataDefs->arrDataDescriptions[i].type == Descriptor_MarkerSet)
           {
                // Marker Set
                sMarkerSetDescription* pMS = pDataDefs->arrDataDescriptions[i].Data.MarkerSetDescription;
            }
            else if(pDataDefs->arrDataDescriptions[i].type == Descriptor_RigidBody)
            {
                // RigidBody
               sRigidBodyDescription* pRB = pDataDefs->arrDataDescriptions[i].Data.RigidBodyDescription;
            }
            else if(pDataDefs->arrDataDescriptions[i].type == Descriptor_Skeleton)
            {
                // Skeleton
               sSkeletonDescription* pSK = pDataDefs->arrDataDescriptions[i].Data.SkeletonDescription;
            }
            else if(pDataDefs->arrDataDescriptions[i].type == Descriptor_ForcePlate)
            {
                // Force Plate
               sForcePlateDescription* pFP = pDataDefs->arrDataDescriptions[i].Data.ForcePlateDescription;
            }
            else
            {
                printf("Unknown data type.");
                // Unknown
            }
   }      
```

#### C. Free Data Description

When you are finished using the data description structure, you should free the memory resources allocated by GetDataDescription using the NatNet helper routine [NatNet\_FreeDescriptions()](natnet-class-function-reference.md#natnet_freedescriptions).

```
    if ( pDataDefs ) {
    NatNet_FreeDescriptions( pDataDefs );
    pDataDefs = NULL; 
    }
```

### 4. Get FrameOfMocapData

#### a. Set Callback Functions

Now that we have data descriptions, let's fetch the corresponding frame-specific tracking data. To do this, a callback handler function needs to be set for processing the incoming frames. First, create a NatNetFrameReceivedCallback function that has the matching input arguments and the return values as described in the NatNetTypes.h file:`typedef void (NATNET_CALLCONV* NatNetFrameReceivedCallback)(sFrameOfMocapData* pFrameOfData, void* pUserData);`The SampleClient.cpp project sets _DataHandler_ function as the frame handler function.`void NATNET_CALLCONV DataHandler(sFrameOfMocapData* data, void* pUserData)`

The [NatNetClient::SetFrameReceivedCallback](natnet-class-function-reference.md#natnetclient-setframereceivedcallback) method creates a new thread and assigns the frame handler function. Call this method with the created function and the NatNetClient object as its arguments. In the SampleClient application, this is called within the CreateClient function:

```
//set the callback handlers 
//The DataHandler function will receive data from the server g_pClient -> SetFrameReceivedCallback( DataHandler, theClient ); 
```

#### b. Parsing/Handling Frame Data Handling

Once you call the SetDataCallback method to link a data handler callback function, this function will receive a packet of [sFrameOfMocapData](natnet-data-types.md) each time a frame is received. The sFrameOfMocapData contains a single frame data for all of the streamed assets. This allows prompt processing of the capture frames within the handler function.

```
// set the callback handlers
// The DataHandler function will receive data from the server
g_pClient->SetDataCallback( DataHandler, theClient );

void __cdecl DataHandler(sFrameOfMocapData* data, void* pUserData)
{
    NatNetClient* pClient = (NatNetClient*) pUserData;

    const double softwareLatencyMillisec = (softwareLatencyHostTicks * 1000) / static_cast<double>(g_serverDescription.HighResClockFrequency);

    if(fp)
    _WriteFrame(fp,data);

    int i=0;

    printf("FrameID : %d\n", data->iFrame);
    printf("Timestamp :  %3.2lf\n", data->fTimestamp);
    printf("Latency :  %3.2lf\n", data->softwareLatencyMillisec);

    // FrameOfMocapData params
    bool   bIsRecording = ((data->params & 0x01)!=0);
    bool   bTrackedModelsChanged = ((data->params & 0x02)!=0);

    if(bIsRecording)
    printf("RECORDING\n");

    if(bTrackedModelsChanged)
    printf("Models Changed.\n");

    // Printing Rigid Body Data…
    //…

    // Printing Skeleton Data…
    //…

    // Printing Rigid Body Data…
    //…

    // labeled markers…
    //…

     // force plates…
    //…
}
```

### 5. Disconnect

When exiting the program, call **Disconnect** method to disconnect the client application from the server.

```
if (g_pClient) {
   g_pClient->Disconnect();
   delete g_pClient;
   g_pClient = NULL;
   }
```
