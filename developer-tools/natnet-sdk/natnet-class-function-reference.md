---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/developer-tools/natnet-sdk/natnet-class-function-reference
---

# NatNet: Class/Function Reference

This page provides function and class references of the NatNet SDK library.

The [NatNetClient](natnet-class-function-reference.md#natnetclient-class) class (or NatNetClientML from the managed assembly) is the key object of the SDK. An instance of this client class allows an application to connect to a server application and query data. [API helper functions](natnet-class-function-reference.md#natnet-c++-api-functions) are provided with the C++ library for a more convenient use of the SDK tools. For additional information, refer to the provided headers files (native) or reference the NatNatML.dll file (managed).

{% hint style="info" %}
**Note:**

* NatNet SDK is backwards compatible.
* Deprecated methods from previous SDK versions are not documented on this page, and their use in new applications is discouraged. They are subject to removal in a future version of the SDK. Refer to the header files for complete descriptions.
* The NatNetServer class has been deprecated for versions 3.0 and above.
* Note that some parts of the managed .NET assembly may be slightly different from the native library reference provided here. Refer to the NatNetML.dll file using an object browser for detailed information.
{% endhint %}

## ErrorCode

Most of the NatNet SDK functions return their operation results in an integer type representation named ErrorType, which is just an enumerator that describes operation results as the following:

| Error Name                  | Integer | Description                                                                                          |
| --------------------------- | ------- | ---------------------------------------------------------------------------------------------------- |
| ErrorCode\_OK               | 0       | Operation successful                                                                                 |
| ErrorCode\_Internal         | 1       | Suspect internal errors. Contact support.                                                            |
| ErrorCode\_External         | 2       | External errors. Make sure correct parameters are used for input arguments when calling the methods. |
| ErrorCode\_Network          | 3       | The error occurred on the network side.                                                              |
| ErrorCode\_Other            | 4       | Unlisted error is conflicting the method call.                                                       |
| ErrorCode\_InvalidArgument  | 5       | Invalid input arguments have been inputted.                                                          |
| ErrorCode\_InvalidOperation | 6       | Invalid operation.                                                                                   |

## NatNetClient Class

The **NatNetClient** class is the main component of the NatNet SDK. Using an instance of the NatNetClient class, you can establish a network connection with a server application (e.g. Motive) and query data descriptions, tracking data, and send/receive remote commands. For detailed declarations, refer to the [NatNetClient.h](natnet-4.5.md) header file included in the SDK.

### Constructor and Destructor

**NatNetClient::NatNetClient()**

**Constructor:** Creates a new instance of a NatNetClient class. Defaults to multicast connection if no input is given.

**NatNetClient::NatNetClient(iConnectionType)**

**Constructor:** Creates a new instance of a NatNet Client using the specified connection protocol; either unicast or multicast.

**Input:** iConnectionType: (0 = Multicast, 1 = Unicast).

{% hint style="info" %}
This approach is being deprecated. The NatNetClient class now determines the connection type through sNatNetClientConnectParams input when calling the **NatNetClient::Connect** method.
{% endhint %}

**NatNetClient::\~NatNetClient()**

**Destructor:** Destructor

### Member Methods

#### NatNetClient::Connect

```
ErrorCode        Connect( const sNatNetClientConnectParams& connectParams );
```

**Description**

This method connects an instantiated NatNetClient object to a server application (e.g. Motive) at the inputted IP address.

**Input Parameters:**

* Connection parameters object.

**Returns:**

[ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

{% hint style="info" %}
**sNatNetClientConenectParams:**

* Declared under the _NatNetTypes.h_ file.
* Local address. IP address of the localhost where the client application is running.
* Server address. IP address where the server application is streaming to.
* (Optional) Command port. Defaults to 1510.
* (Optional) Data port. Defaults to 1511.
* (Optional) Multicast IP address. Defaults to 239.255.42.99:1511.

```
typedef struct sNatNetClientConnectParams
{
    ConnectionType connectionType;
    uint16_t serverCommandPort;
    uint16_t serverDataPort;
    const char* serverAddress;
    const char* localAddress;
    const char* multicastAddress;

#if defined(__cplusplus)
    sNatNetClientConnectParams()
        : connectionType( ConnectionType_Multicast )
        , serverCommandPort( 0 )
        , serverDataPort( 0 )
        , serverAddress( NULL )
        , localAddress( NULL )
        , multicastAddress( NULL )
    {
    }
#endif
} sNatNetClientConnectParams;
```
{% endhint %}

#### NatNetClient::Disconnect

```
ErrorCode        Disconnect();
```

**Description**

Calling this method disconnects the client from the Motive server application.

**Input Parameters:**

* None

**Returns:**

[ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

#### NatNetClient::SetFrameReceivedCallback

{% code overflow="wrap" %}
```
ErrorCode        SetFrameReceivedCallback( NatNetFrameReceivedCallback pfnDataCallback, void* pUserContext = 0 );
```
{% endcode %}

**Description**

This method sets a frame handler function and creates a new thread for receiving and processing each frame of capture data.

* Managed Assembly: Use _OnFrameReady_ event type to add a function delegate.

**Input Parameters:**

* pfnDataCallback: A NatNetFrameReceivedCallback function. NatNetFrameReceivedCallback is a type of a pointer to a frame handler function which processes each incoming frame of tracking data. Format of the inputted function must agree with the following type definition:

`typedef void (NATNET_CALLCONV* NatNetFrameReceivedCallback)(sFrameOfMocapData* pFrameOfData, void* pUserData);`

* User definable data: the Client object.

**Returns:**

[ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

#### NatNetClient::SendMessageAndWait

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

Sends a NatNet command to the NatNet server and waits for a response. See [NatNet: Remote Requests/Commands](natnet-remote-requests-commands.md) for more details.

**Input Parameters:**

* szRequest: NatNet command.
* tries: Number of attempts to send the command. Default: 10.
* timeout: Number of milliseconds to wait for a response from the server before the call times out. Default: 20.
* ppServerResponse: Application defined response.
* pResponseSize: Number of bytes in response

**Returns:**

[ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

#### NatNetClient::GetServerDescription

```
ErrorCode        GetServerDescription( sServerDescription* pServerDescription );
```

**Description**

Requests a description of the current NatNet server that a client object is connected to and saves it into an instance of sServerDescription. This call is blocked until the request is responded or times out.

**Input Parameters:**

* Declared sServerDescription object.

**Returns:**

[ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

#### NatNetClient::GetDataDescriptionList

{% code overflow="wrap" %}
```
ErrorCode GetDataDescriptionList( sDataDescriptions** ppDataDescriptions, uint32_t descriptionTypesMask = 0xFFFFFFFF );
```
{% endcode %}

**Description**

Requests a list of [dataset descriptions](natnet-data-types.md#dataset-descriptions) of the capture session and saves onto the declared instance of sDataDescriptions.

**Input Parameters:**

* Pointer to an sDataDescriptions pointer which receives the address of the client's internal sDataDescriptions object. This pointer is valid until the client is destroyed or until the next call to GetDataDescriptions.
* Specifies which data types to retrieve data descriptions for. The default option includes all types, however for performance and size reasons you may select a subset using the _descriptionTypesMask_ bitmask. The Bitmask is defined as follows:
  * Bit 0 : Markersets
  * Bit 1 : Rigid Bodies
  * Bit 2 : Skeletons
  * Bit 3 : Force Plates
  * Bit 4 : Peripheral Devices
  * Bit 5 : Cameras
  * Bit 6 : Trained Markersets

**Returns:**

[ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

#### NatNetClient::SecondsSinceHostTimestamp

```
double    SecondsSinceHostTimestamp( uint64_t hostTimestamp ) const;
```

**Description**

This method calculates and returns the time difference between a specific event in the processing pipeline and when the NatNet client application receives the tracking data. For example, if sFrameOfMocapData::CameraMideExposureTimestamp is inputted, it will return the latency from the camera exposure to when the tracking data is received. For more information on how it is used, read through the [Latency Measurements](latency-measurements.md) page.

**Input Parameters:**

* (uint64\_t) A timestamp value from a sFrameOfMocapData struct.

**Returns:**

(double) The time, in seconds, past since the provided timestamp.

## NatNet C++ API Functions

Once the NatNetSDK library has been imported into a client application, the following helper functions can be used.

{% hint style="info" %}
These functions are available ONLY for C++ applications.
{% endhint %}

### Function list

#### NatNet\_GetVersion

```
 NATNET_API void	NATNET_CALLCONV NatNet_GetVersion( unsigned char outVersion[4] );
```

**Description**

This function gets the version (#.#.#.#) of the NatNet SDK and saves it into an array.

**Input Parameters:**

* Unsigned char array with a array length of 4.

**Returns:**

* Void

#### NatNet\_SetLogCallback

```
 NATNET_API void	NATNET_CALLCONV NatNet_SetLogCallback( NatNetLogCallback pfnLogCallback );
```

**Description**

This function assignes a callback handler function for receiving and reporting error/debug messages.

**Input Parameters:**

* pfnLogCallback: NatNetLogCallback function. NatNetLogCallback is a type of a pointer to a callback function that is used to handle the log messages sent from the server application. Format of the linked function must agree with the following type definition:

`typedef void (NATNET_CALLCONV* NatNetLogCallback)(Verbosity level, const char* message);`

**Returns:**

* Void

#### NatNet\_DecodeID

```
 NATNET_API void	NATNET_CALLCONV NatNet_DecodeID( int compositeId,
           						int* pOutEntityId,
         						int* pOutMemberId );
```

**Description**

Takes an ID of a data set (a marker, a Rigid Body, a Skeleton, or a force plate), and decodes its model ID and member ID into the provided integer variables. For example, ID of a Skeleton bone segment will be decoded into its model ID (Skeleton) and Rigid Body ID (bone). See [NatNet: Data Types](natnet-data-types.md).

**Input Parameters:**

* An ID value for a respective data set (sRigidBodyData, sSkeletonData, sMarker, or sFrocePLateData) from a sFrameOfMocapData packet.
* Pointer to declared integer value for saving the entity ID and the member ID (e.g. Skeleton ID and its bone Rigid Body ID).

**Returns:**

* Void

#### NatNet\_DecodeTimecode

```
NATNET_API ErrorCode	NATNET_CALLCONV	NatNet_DecodeTimecode( 	unsigned int timecode,
           						unsigned int timecodeSubframe,
              						int* pOutHour, int* pOutMinute,
              						int* pOutSecond, int* pOutFrame,
             						int* pOutSubframe );
```

**Description**

Helper function to decode OptiTrack timecode data into individual components.

**Input Parameters:**

* Timecode integer from a packet of sFrameOfMocapData. (timecode)
* TimecodeSubframe integer from a packet of sFrameOfMocapData. (timecodeSubframe)
* Pointers to declared integer variables for saving the hours (pOutHour), minutes (pOutMinute), seconds (pOutSecond), frames (pOutFrame), and subframes (pOutSubframe) values.

**Returns:**

* [ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

#### NatNet\_TimecodeStringify

```
NATNET_API ErrorCode	NATNET_CALLCONV NatNet_TimecodeStringify( unsigned int timecode, 
              							unsigned int timecodeSubframe,
              							char* outBuffer,
              							int outBufferSize );
```

**Description**

Helper function to parse OptiTrack timecode into a user friendly string in the form **hh:mm:ss:ff:yy**

**Input Parameters:**

* timecode: Timecode integer from a packet of sFrameOfMocapData. (timecode)
* timecodeSubframe: TimecodeSubframe integer from a packet of sFrameOfMocapData. (timecodeSubframe)
* outBuffer: Declared char for saving the output.
* outBufferSize: size of the character array buffer (outBuffer).

**Returns:**

* [ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

#### NatNet\_CopyFrame

```
NATNET_API ErrorCode	NATNET_CALLCONV NatNet_CopyFrame( sFrameOfMocapData* pSrc,
              						sFrameOfMocapData* pDst );
```

**Description**

This helper function performs a deep copy of frame data from pSrc into pDst. Some members of pDst will be dynamically allocated; use NatNet\_FreeFrame( pDst ) to clean them up.

**Input Parameters:**

* Pointer to two sFrameOfMocapData variables to copy from (pSrc) and copy to (pDst).

**Returns:**

* [ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

#### NatNet\_FreeFrame

```
NATNET_API ErrorCode	NATNET_CALLCONV NatNet_FreeFrame( sFrameOfMocapData* pFrame );
```

**Description**

Frees the dynamically allocated members of a frame copy created using _NatNet\_CopyFrame_ function. Note that the object pointed to by _pFrame_ itself is NOT de-allocated, but only its nested members which were dynamically allocated are freed.

**Input Parameters:**

* sFrameOfMocapData that has been copied using the NatNet\_CopyFrame function.

**Returns:**

* [ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

{% hint style="danger" %}
Do not call this on any _pFrame_ data that was not the destination of a call to _NatNet\_CopyFrame_.
{% endhint %}

#### NatNet\_FreeDescriptions

```
NATNET_API ErrorCode	NATNET_CALLCONV NatNet_FreeDescriptions( sDataDescriptions* pFrame );
```

**Description**

Deallocates data descriptions _pDesc_ and all of its members; after this call, this object is no longer valid.

**Input Parameters:**

* Data descriptions (sDataDescriptions).

**Returns:**

* [ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

#### NatNet\_BroadcastServerDiscovery

```
NATNET_API ErrorCode	NATNET_CALLCONV NatNet_BroadcastServerDiscovery( sNatNetDiscoveredServer* outServers, int* pInOutNumServers, unsigned int timeoutMillisec = 1000 );
```

**Description**

Sends broadcast messages to discover active NatNet servers and blocks for a specified time to gather responses.

**Input Parameters:**

* **outServers:** An array of length equal to the input value of _pInOutNumServers_. This array will receive the details of all servers discovered by the broadcast.
* **pInOutNumServers:** A pointer to an integer containing the length of the array. After this function returns, the integer is modified to contain the total number of servers that responded to the broadcast inquiry. If the modified number is larger than the original number passed to the function, there was insufficient space for those additional servers.
* **timeoutMillisec:** Amount of time, in milliseconds, to wait for server responses to the broadcast before returning.

**Returns:**

* [ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

#### NatNet\_CreateAsyncServerDiscovery

```
NATNET_API ErrorCode	NATNET_CALLCONV NatNet_CreateAsyncServerDiscovery( NatNetDiscoveryHandle* pOutDiscovery, NatNetServerDiscoveryCallback pfnCallback, void* pUserContext = NULL );
```

**Description**

Begin sending periodic broadcast messages to discover active NatNet servers in the background.

**Input Parameters:**

* **pOutDiscovery:** Out pointer that will receive a handle representing the asynchronous discovery process. **The handle returned should be passed to NatNet\_FreeAsyncServerDiscovery method later for clean up.**
* **pfnCallback:** A NatNetServerDiscoveryCallback function pointer that will be invoked once for every new server that's discovered by the asynchronous search. The callback will also be passed onto the provided _pUserContext_ argument.
* **pUserContext:** User-specified context data to be passed to the provided _pfnCallback_ when invoked.

**Returns:**

* [ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.

#### NatNet\_FreeAsyncServerDiscovery

```
NATNET_API ErrorCode	NATNET_CALLCONV NatNet_CreateAsyncServerDiscovery( NatNetDiscoveryHandle* pOutDiscovery, NatNetServerDiscoveryCallback pfnCallback, void* pUserContext = NULL );
```

**Description**

Begin sending periodic broadcast messages to continuously search and discover active NatNet servers in the background.

**Input Parameters:**

* **pOutDiscovery:** Out pointer that will receive a handle representing the asynchronous discovery process. The handle returned should be passed to NatNet\_FreeAsyncServerDiscovery method later for clean up.
* **pfnCallback:** A NatNetServerDiscoveryCallback function pointer that will be invoked once for every new server that's discovered by the asynchronous search. The callback will also be passed onto the provided _pUserContext_ argument.
* **pUserContext:** User-specified context data to be passed to the provided _pfnCallback_ when invoked.

**Returns:**

* [ErrorCode](natnet-class-function-reference.md#errorcode), On success, it returns 0 or ErrorCode\_OK.
