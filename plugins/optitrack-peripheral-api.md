# OptiTrack Peripheral API

The OptiTrack Peripheral API is an open C++ API that can be used to create 'plugin' devices. Custom built plugin DLL's will allow you to initialize and synchronize external devices with the OptiTrack motion capture system in Motive. After building a custom plugin device using the API, the library must be placed in the `\device` folder within the Motive install directory in order to initialize and integrate desired peripheral devices. For integrating [AMTI](../movement-sciences/movement-sciences-hardware/amti-force-plate-setup.md) and [Bertec](../movement-sciences/movement-sciences-hardware/bertec-force-plate-setup.md) force plates and [NI-DAQ](../movement-sciences/movement-sciences-hardware/ni-daq-setup.md) devices, the existing BiomechDevicePlugin.dll that installs with the peripheral module can be utilized.&#x20;

The following features are supported by the Peripheral API:

* Real-time synchronized data collection from peripheral hardware device and the OptiTrack motion capture system into Motive _Take_ (TAK) files and the open standard C3D file format.
* Motive UI access to device properties and event settings under the [Devices pane](../motive-ui-panes/devices-pane.md), allowing the users to configure the device in Motive.
* Real-time display of live device data in Motive's scope view in the [Graph View pane](../motive-ui-panes/graph-view-pane.md).
* Captured data review in Motive's 2D Graphing windows in the [Graph View pane](../motive-ui-panes/graph-view-pane.md).

## Contents <a href="#contents" id="contents"></a>

The **Peripheral API** folder is installed with the Motive software. It can be found in the Motive install directory, which is located in `C:\Program Files\OptiTrack\Motive\PeripheralAPI` by default.

| Folder       | Contents                                                                           |
| ------------ | ---------------------------------------------------------------------------------- |
| \example     | Visual Studio Example Device project and source code showing Peripheral API usage. |
| \include     | API headers (include in your project)                                              |
| \lib         | Peripheral API / Motive import library (link to your project)                      |
| ClassDiagram | Class relationship diagram of Plugin Devices to Motive Plugin Library.             |
| Readme.txt   | Peripheral API release notes.                                                      |

## Requirements <a href="#requirements" id="requirements"></a>

The following components are required for using the OptiTrack Peripheral API.

* Microsoft Windows 10 or higher.
* Microsoft Visual Studio 2019 or higher.

If you plan to use a newer version of Microsoft Visual Studio, you may need to download Windows SDK 8.1 and the VC++ 2015.3v140 toolset (x86,x64).

## Peripheral API Setup <a href="#retarget-solution" id="retarget-solution"></a>

### Retarget Solution <a href="#retarget-solution" id="retarget-solution"></a>

**Downloads/Installs**

* You can download the Windows SDK 8.1 from this [link. ](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive/)​

<figure><img src="https://4243847686-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FTSFWA3dBvgCMGQlNWsHE%2Fuploads%2FURByOODWGrMPh2iXcB9k%2Fimage.png?alt=media&#x26;token=6309f1c9-f642-4fed-ae1e-aaa8a4e0021d" alt=""><figcaption></figcaption></figure>

* To download the v140 Toolset, you can modify your existing install of VS, or upon first downloading add the toolset from the Individual Components tab.

<figure><img src="https://4243847686-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FTSFWA3dBvgCMGQlNWsHE%2Fuploads%2FdZcZ0MHw6yhQSsVBboBl%2Fimage.png?alt=media&#x26;token=3a4803e5-0c95-47e2-b98b-f06036967e8d" alt=""><figcaption></figcaption></figure>

* Once you have the Windows SDK 8.1 and v140 Toolset downloaded, you'll need to retarget the OptiTrackPeripheralExample solution.

<figure><img src="https://4243847686-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FTSFWA3dBvgCMGQlNWsHE%2Fuploads%2FbYSWqytzN3iZEb5FAKIJ%2Fimage.png?alt=media&#x26;token=0a613382-26f5-46d7-b057-0fb571f687e6" alt=""><figcaption></figcaption></figure>

**Retargeting Steps**

1. In Visual Studio, right click Solution 'OptiTrackPeripheralExample', or whatever you named the copy as.
2. Select 'Retarget Solution'​
3. For the Windows SDK Version dropdown, select 8.1.
4.  For the Platform Toolset dropdown, select v140 or No Upgrade (if VS has already loaded v140 as the default).

    <figure><img src="https://4243847686-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FTSFWA3dBvgCMGQlNWsHE%2Fuploads%2F5mxflTlxIGp5rRUWn5Sf%2Fimage.png?alt=media&#x26;token=f9d9a56f-102d-4158-83bb-490f130cac9c" alt=""><figcaption></figcaption></figure>
5. Click OK
6. This should now be ready to build without errors.

## Usage <a href="#usage" id="usage"></a>

The following guideline can be used to create and apply custom device plugin DLLs in Motive:

1.  Copy the OptiTrackPeripheralExample project and modify the code in the lines where indicated in the sample.Edit the 'REQUIRED' and 'OPTIONAL' sections.​ Changes made in the .cpp files are reflected in the Devices and Properties panes.

    <figure><img src="../.gitbook/assets/image (457).png" alt=""><figcaption><p>Edit the 'REQUIRED' and 'OPTIONAL' sections. Click image to enlarge.</p></figcaption></figure>

    <figure><img src="../.gitbook/assets/image (464).png" alt=""><figcaption><p>Changes made in the .cpp files are reflected in the Devices and Properties panes.</p></figcaption></figure>
2. Build the sample, which produces a plugin DLL. Copy this DLL to the `<Motive install folder>\devices` subfolder.
3. If your plugin has external dependencies (e.g. driver / SDK dlls), make sure these are on your system path, or in the Motive install directory.
4. Launch Motive. Your device should appear in the [Devices pane](../motive-ui-panes/devices-pane.md) in Motive. If it does not, check the Motive [Log pane](../motive-ui-panes/log-pane.md) for error notifications.
5. When a peripheral device is detected in Motive, real-time collected data can be monitored from the real-time plotting of the [Graph View pane](../motive-ui-panes/graph-view-pane.md) in the Live mode.

<figure><img src="https://4243847686-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FTSFWA3dBvgCMGQlNWsHE%2Fuploads%2FpkLIbQcK2ebhADppeiwt%2Fimage.png?alt=media&#x26;token=9a658877-32d2-473d-983d-a86d5f412b62" alt=""><figcaption></figcaption></figure>

## Class Diagram <a href="#class-diagram" id="class-diagram"></a>

<figure><img src="https://4243847686-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FTSFWA3dBvgCMGQlNWsHE%2Fuploads%2FZVjvIcOp8WUjfno3gjGn%2Fimage.png?alt=media&#x26;token=e4ed3697-2d34-4b28-b679-909145106947" alt=""><figcaption><p>Click image to enlarge</p></figcaption></figure>
