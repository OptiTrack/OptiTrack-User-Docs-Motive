---
description: >-
  This document provides general guidelines to create a device plugin for
  external glove devices in Motive.
---

# Peripheral API:  Glove Devices

Starting with Motive 3.1, an example project, GloveDeviceExample, is included along with the peripheral API library. This guide will reference that example and provide basic information on how to use the peripheralimport library (LIB) to create glove device plugins and identify required configuration settings.

This guide assumes that you have access to Motive 3.1 or above. Additional descriptions are commented throughout the source and header files also.

### Overview

Mocap systems often incorporate external measurement systems in order to accomplish more complex analysis. Commonly integrated devices include force plates, data acquisition boards, and EMG sensors.

There are a few different ways to combine data with external systems:  recorded data sets can be analyzed in post-capture; data can be streamed real-time into a client application and then combined downstream; or data can be combined live in Motive using the plugin interface. With finger-tracking devices, the workflow is much simpler if the motion capture data of the two systems gets joined together in Motive.

In this article, we will show how to integrate glove devices using the plugin interface provided by the [peripheral API](../plugins/optitrack-peripheral-api.md) (peripheralimport.lib), which is used to create and manage plugin devices in Motive.&#x20;

### Glove device data

Glove devices update the local quaternion rotation of the finger bones. The hand skeleton in Motive is made up of 15 bone joints, three bones per finger. Each bone will require 4 float values to represent the quaternion rotation. In total, 60 float analog channels will be created for the glove device.

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption><p>Float values per glove.</p></figcaption></figure>

The hand orientation in Motive respects the right-handed coordinate system. For the left hand, the local coordinate is +X pointing towards the fingertips when in T-pose, and for the right hand, +X points towards the wrist/body when in T-pose.&#x20;

<div><figure><img src="../.gitbook/assets/Right Hand Glove Axis.png" alt=""><figcaption><p>Right hand:  X axis points to wrist.</p></figcaption></figure> <figure><img src="../.gitbook/assets/Left Hand Glove Axis.png" alt=""><figcaption><p>Left hand: X axis points to fingertips.</p></figcaption></figure></div>

### Glove Device Example

The glove device example is a guide for integrating glove devices into Motive. This project is located in:

&#x20;_\[Motive Installation Directory]\PeripheralAPI\example\GloveDeviceExample_

Parts of the GloveDeviceExample code can be replaced with calls to the SDK in order to initialize, connect, receive, and map the glove data into Motive. These are annotated with placeholder comments throughout the source files. The glove device example project includes some of the base classes that can be inherited:

* **GloveDeviceFactoryBase** class, which handles instantiation and initialization of glove device in Motive.
* **GloveDeviceBase** class, which extends the **cPluginDevice** class of the peripheral API, and abstracts out the required configurations for glove devices.
* **ExampleGloveDevice** and **ExampleGloveAdapterSingleton** are sample implementations of a glove plugin by inheriting the above base classes.
* **HardwareSimulator** class is a dummy device to simulate callbacks for the device connection and device data update.

To create a glove SDK, this example can be used as a template and the callbacks can be replaced with the SDK functions that will connect and report glove devices and their data. The following table describes the source code in more detail.

| Name                                                                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| -------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| _dllmain.cpp_                                                              | <p>This is the main entry point for the plugin interface. At startup, Motive looks for plugin DLLs located in the devices folder (C:\Program Files\OptiTrack\Motive\devices) and attempts to load them.</p><p>Once loaded, Motive calls the DLLEnumerateDeviceFactories function to enumerate device factories that will be used to instantiate the devices in Motive. Upon program exit, Motive will call the PluginDLLUnload function, where the plugin cleans itself up and unloads the SDK.</p> |
| <p><em>GloveDeviceBase.h</em></p><p><em>GloveDeviceBase.cpp</em></p>       | <p>This file contains GloveDeviceBase class and the GloveDeviceFactory class.</p><p> </p><p>GloveDeviceBase class extends the cPluginDevice and abstracts out the configurations required for a glove device.</p><p> </p><p>GloveDeviceFactory class extends the cPluginDeviceFactory class and abstracts out device factory configurations required for a glove device. In Peripheral API, an instance of factory class is needed for each instance of a device.</p>                               |
| <p><em>HardwareSimulator.h</em></p><p><em>HardwareSimulator.cpp</em></p>   | HardwareSimulator is included to simulate a glove device. It updates the data callbacks by reading from the pre-recorded glove data in a CSV file as an example. It also includes data formats and structure types for device information and data.                                                                                                                                                                                                                                                 |
| <p><em>ExampleGloveDevice.h</em></p><p><em>ExampleGloveDevice.cpp</em></p> | <p>ExampleGloveDevice inherits from GloveDeviceBase class to create a glove device. This class represents the actual glove device class that will be integrated.</p><p> </p><p>This class mainly handles the <em>DoCollectionThread</em>, a separate thread used to obtain the data from the glove SDK and populate it in the analog data channels.</p>                                                                                                                                             |
| _ExampleGloveAdapterSingleton.cpp_                                         | <p>The ExampleGloveAdapterSingleton class is both an adapter to manage interaction with the device SDK and an aggregator that stores the glove data in its buffer.</p><p> </p><p>This adapter class runs a detection thread, <em>DoDetectionThread</em>, that periodically checks if a new glove has been detected.</p>                                                                                                                                                                             |

### Class Diagram

<figure><img src="../.gitbook/assets/Glove API flow chart.png" alt=""><figcaption><p>Glove Device Example Diagram. Click to enlarge. </p></figcaption></figure>

### Glove SDK

There are a few requirements from the glove SDK side:

* Data callback that reports data from all connected gloves.
* Reports device Information, including number of connected devices, serial numbers, battery levels, and signal strengths.
* Remote host connection.
* Proper error handling for the SDK calls.

### Glove device Plugin breakdown

#### Connecting to Host

The plugin starts at DLLEnumerateDeviceFactories method in **dllmain.cpp**. This entry method calls ExampleGlove\_EnumerateDeviceFactories static method to instantiate the ExampleGloveAdapter class, which starts the _DoDetectionThread_, which periodically attempts to connect to the glove host. Once it’s connected, it registers the SDK callbacks.

```clike
 * Motive calls the following method on application start up. This register device factories with Motive 
 * so that the device can be instantiated when it's ready (1 factory per device)
 */
OPTITRACKPERIPHERALEXAMPLE_API int DLLEnumerateDeviceFactories(IDeviceManager* pDeviceManager)
{
   
	list<unique_ptr<IDeviceFactory>> availDFs;

	ExampleDevice::ExampleGlove_EnumerateDeviceFactories(pDeviceManager, availDFs);
	for (list<unique_ptr<IDeviceFactory>>::iterator iter = availDFs.begin(); iter != availDFs.end(); iter++) {
		// transfers ownership of device factory to host
		pDeviceManager->AddDevice(std::move(*iter));
	}

	return (int)availDFs.size();
}
```

The detection thread in the file **ExampleGloveAdapterSingleton.cpp** includes a loop that attempts to connect to the host at the given IP address defined under General Settings -> Advanced -> Glove Server Address. The SDK instance can be instantiated either at the constructor of the adapter class or before the while loop. Within the while loop, attempts to connect to the host by calling the ConnectToHost function below.

```clike
///////////////////////////////////////////////////////////////////////////////
// 
// Glove Host Detection Thread
//
void OptiTrackPluginDevices::ExampleDevice::ExampleGloveAdapterSingleton::DoDetectionThread()
{
	while (!bIsConnected && bIsDetecting)
	{
		// Try reconnecting
		if (s_Instance->mConnectionAttemptCount < s_Instance->kMaxConnectionAttempt) {
			bIsConnected = ConnectToHost();
			s_Instance->mConnectionAttemptCount++;
		}
		else {
			bIsDetecting = false;
			NotifyConnectionFail();
		}
		std::this_thread::sleep_for(std::chrono::milliseconds(20000));
	}
}

```

When the ConnectToHost call successfully connects to the glove server, required callbacks can be registered:

```clike
///////////////////////////////////////////////////////////////////////////////
// 
// SDK Helper Functions
//
bool OptiTrackPluginDevices::ExampleDevice::ExampleGloveAdapterSingleton::ConnectToHost()
{
	// Check if glove server address is defined in Motive's settings.
	if ((mServerAddress.empty())) {
		char* szServerAddress = new char[MAX_PATH];
		if (mDeviceManager->GetProperty("Glove Server Address", &szServerAddress))
		{
			std::string str(szServerAddress);
			mServerAddress = str;
		}
		delete[] szServerAddress;
	}

	/*
	* [Glove SDK Placeholder]
	*	SDK call to connect to the host at 'mServerAddress'.
	*/
	bIsConnected = true;

	
	StartSimulatedHardware(1);
	RegisterSDKCallbacks();

    return true;
}

```

### Creating a Glove Device

The process of creating a device involves two steps: &#x20;

1. Instantiate the device factory that owns the plugin device.
2. Transfer the ownership of the device factory to Motive to call the _Create_ method.&#x20;

In the **GloveDeviceExample** project, this occurs in **dllmain.cpp** and in **ExampleGloveAdapterSingleton.cpp** (ExampleGloveAdapterSingleton::CreateNewGloveDevice).

```clike
void OptiTrackPluginDevices::ExampleDevice::ExampleGloveAdapterSingleton::CreateNewGloveDevice(sGloveDeviceBaseInfo& deviceInfo)
{
	uint64_t gloveId = deviceInfo.gloveId;
	std::string deviceName = "ExampleGlove_" + std::to_string(deviceInfo.gloveId);

	// Create device factory using the name/id/serial/client.
	std::unique_ptr<ExampleGloveDeviceFactory> pDF =
		std::make_unique<ExampleGloveDeviceFactory>(deviceName, deviceInfo);
	pDF->mDeviceIndex = s_Instance->mCurrentDeviceIndex;
	s_Instance->mDeviceManager->AddDevice(std::move(pDF));
	s_Instance->mCurrentDeviceIndex++;

	return;
}

```

### Glove Device Factory

Once an instance of the device factory is transferred, Motive will call the _Create_ method when it’s ready to create the device. The following script is in the file **ExampleGloveDevice.cpp**:

```clike
///////////////////////////////////////////////////////////////////////////////
// 
// Example Glove Device Factory
//
const char* OptiTrackPluginDevices::ExampleDevice::ExampleGloveDeviceFactory::Name() const
{
	return "ExampleGloveDevice";
}

std::unique_ptr<AnalogSystem::IDevice> OptiTrackPluginDevices::ExampleDevice::ExampleGloveDeviceFactory::Create() const
{
	ExampleGloveDevice* pDevice = new ExampleGloveDevice(mDeviceSerial, mDeviceInfo);
	SetCommonGloveDeviceProperties(pDevice);
	SetQuaternionDataChannels(pDevice);

	// Transfer ownership to host
	std::unique_ptr<AnalogSystem::IDevice> ptrDevice(pDevice);
	return ptrDevice;
}

```

The _ExampleGloveDeviceFactory_ class overrides the _Create_ method, which is used to create the instance of glove device class (ExampleGloveDevice), and configures it, which includes setting common glove properties and the data channels that are required for that device. At last, it returns the pointer to the device back to Motive. These configurations are common to all glove devices, so these two methods are implemented at the glove device base (**GloveDeviceBase.h**).

```clike
* Sets up quaternion data channels for delivering local rotation of the finger nodes.
* Motive skeleton's hand consists of total 15 finger nodes, 3 per each finger.
* These data channels will get populated by the collection thread running on each device.
* Quaternion values are expected, resulting in total 60 float channels (15 finger nodes * 4 quat floats / node).
* Local rotation data is expected, and both hand data expects right-handed coordinate system with +x axis
* pointing towards the finger tip for left hand and towards the wrist/body for right hand.
*/
void SetQuaternionDataChannels(GloveDeviceBase* pDevice) const;

/**
* Set Common Glove device properties
*/
void SetCommonGloveDeviceProperties(GloveDeviceBase* pDevice) const;
```

**GloveDeviceBase.cpp:**

```clike
void OptiTrackPluginDevices::GloveDeviceFactoryBase::SetCommonGloveDeviceProperties(GloveDeviceBase* pDevice) const
{
	// REQUIRED: Set device name/model/serial
	pDevice->SetProperty(cPluginDeviceBase::kNamePropName, (char*)DeviceName());
	pDevice->SetProperty(cPluginDeviceBase::kDisplayNamePropName, (char*)DeviceName());
	pDevice->SetProperty(cPluginDeviceBase::kModelPropName, "Glove Model");	// model
	char mDeviceSerial[MAX_PATH];
	sprintf_s(mDeviceSerial, "%s-serial", DeviceName());
	pDevice->SetProperty(cPluginDeviceBase::kSerialPropName, mDeviceSerial);									// device serial (must be unique!)
		// device serial (must be unique!)
	pDevice->SetProperty(cPluginDeviceBase::kDeviceTypePropName, (long)DeviceType_Glove);					// set device type as glove
		// set device type as glove
	pDevice->SetProperty(cPluginDeviceBase::kRatePropName, 120.0);											// glove sampling rate
		// glove sampling rate
	pDevice->SetProperty(cPluginDeviceBase::kUseDriftCorrectionPropName, true);								// drift correction to fetch most recent data.
		// drift correction to fetch most recent data.
	pDevice->SetProperty(cPluginDeviceBase::kOrderPropName, (int) eGloveHandSide::Unknown);					// device order: (0 = uninitialized, 1=left, 2=right)
		// device order: (0 = uninitialized, 1 = left 2 = right)
}
```

Here, it’s important to define the common glove device properties at the device factory level. More specifically, the device type and device order must specify that this is a glove device because these properties will be referenced by Motive.

| Property Name                                  | Description                                                                                                                                                                                                                                 |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| cPluginDeviceBase::kNamePropName               | Default device name that will be defined for the device.                                                                                                                                                                                    |
| cPluginDeviceBase::kDisplayNamePropName        | Display name which will be shown in the Device pane, which the user can edit.                                                                                                                                                               |
| cPluginDeviceBase::kModelPropName              | Device model name.                                                                                                                                                                                                                          |
| cPluginDeviceBase::kSerialPropName             | A unique device serial number. It’s critical that each device has a unique serial number. Motive references the device serial number to determine whether a new device needs to be created.                                                 |
| cPluginDeviceBase::kDeviceTypePropName         | <p>Type of the device. This property must be specified as:  AnalogSystem::DeviceType_Glove </p><p>for all glove devices.</p>                                                                                                                |
| cPluginDeviceBase::kRatePropName               | Defines the sampling rate. In the GloveDeviceExample, the glove devices will attempt to poll from the data map within the adapter class at the rate defined here.                                                                           |
| cPluginDeviceBase::kUseDriftCorrectionPropName | This property sets whether Motive checks for frame alignment and tries to match the device frame. For glove devices, it’s best to get the latest data, so we set this to false.                                                             |
| cPluginDeviceBase::kOrderPropName              | Order of device. In glove devices, this property is used to specify whether the glove device is the Left or Right hand. This information is used when the glove device is paired with a skeleton to make sure the correct hand gets paired. |

#### Collection Thread & Data Map

The provided example uses data maps in the _ExampleGloveAdapter_ that the registered callbacks keep updated. More specifically, these maps contain device information and tracking data for all devices that the SDK reports. Ideally, the glove SDK should report all glove data at the same time in one packet. From **ExampleGloveAdapterSingleton.h:**&#x20;

```clike
/**
* [Glove SDK Placeholder]
* Example data map for storing aggregated device data.
*/ 
uint16_t mDeviceCount = 0;
std::vector<uint64_t> mDetectedDevices;
std::unordered_map<uint64_t, sGloveDeviceData> mLatestGloveData;
std::unordered_map<uint64_t, sGloveDeviceBaseInfo> mLatestDeviceInfo;

/** 
* [Glove SDK Placeholder]
* The following methods are sample callback functions as a demonstration of how this adapter could
* Communicate with plugin SDK. It receives aggregated frame data through the data callback.
*/
bool bIsSimulating;
void StartSimulatedHardware(int deviceCount);
static void RegisterSDKCallbacks();
static void OnDataCallback(std::vector<SimulatedPluginDevices::SimulatedGloveFrameData>& gloveFingerData);
static void OnDeviceInfoCallback(std::vector<SimulatedPluginDevices::SimulatedDeviceInfo>& newGloveInfo);
static sGloveDeviceBaseInfo ConvertDeviceInfoFormat(SimulatedPluginDevices::SimulatedDeviceInfo& glove);
static sGloveDeviceData ConvertDataFormat(const SimulatedPluginDevices::SimulatedGloveFrameData& glove);

```

Each glove device runs its own collection thread, _ExampleGloveDevice::DoCollectionThread()_, which updates the device information such as signal and battery levels, and also populates its analog channels for the tracking data.

## Use In Motive

This guide was intended for the development of the glove plugins. For instructions on setting up and using glove devices in Motive, please refer to the [Glove Device Setup](../markersets/glove-device-setup/) article.&#x20;

Please reach out to [OptiTrack support](https://optitrack.com/support/) for any questions or feedback on integrating glove devices.&#x20;
