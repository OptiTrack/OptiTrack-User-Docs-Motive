# Status Panel

The status panel lists out the system parameters for monitoring the live status of system operations. Click on the displayed status at the bottom right corner of Motive, and the Status Panel will pop up. You can drag and place the Status Panel anywhere.

## Status Panel

![Status Panel in Motive.](<../.gitbook/assets/image (1026).png>)

#### **Residual**

Average of [residual](../motive/reconstruction-and-2d-mode.md) values of all live-reconstructed 3D points. This is available only in the [Live mode](../motive/data-recording/#live-mode-and-edit-mode) or in the [2D Mode](../motive/reconstruction-and-2d-mode.md#2d-mode).

#### **Data**

Current incoming data transfer rate (KB/s) for all attached cameras.

#### **Point Cloud**

Measured latency of the point cloud reconstruction engine.

#### **Assets**

Measured latency of the Rigid Body solver and the Skeleton solver combined.

#### **Software**

Measured software latency. It represents the amount of time it takes Motive to process each frame of captured data. This includes the time taken for reconstructing the 2D data into 3D data, labeling and modeling the trackable assets, displaying in the viewport, and other processes configured in Motive.

#### **System**

**Available only on Ethernet Camera systems (Prime series and Slim13E).** Measured total system latency. This is the time measured from the middle of the camera exposures to when Motive has fully solved all of the tracking data.

#### **Streaming**

The data rate at which the tracking data is streamed to connected client applications.

#### **Final Rate**

Final data acquisition rate of the system.

#### **Cameras**

**Available only on Ethernet Camera systems (Prime series or Slim 13E).** Average temperature, in Celsius, on the imager boards of the cameras in the system.

## Status Panel: Latency

When there is an increased latency on any of the processing pipeline that needs an attention, it will be highlighted in purple. Increase processing latency may result in dropped frames when real-time processing the data in live-captures or in 2D Mode. Increased latency usually occurs due to the CPU not being fast enough to process the data in real-time. If you perform post-processing reconstructions, you will be accessing the recorded 3D data or solved data (rigid bodies), and there will be no processing required for the corresponding pipeline and they will be indicated as _inactive_.

![Increased Point Cloud latency and skeleton solver latency. Increase in skeleton solve latency is due to the Point Cloud engine slowing down.](<../.gitbook/assets/image (984).png>) ![Point cloud is inactive when accessing already reconstructed 3D data.](<../.gitbook/assets/image (1005).png>)

#### **Real-time Point Cloud Latency**

With large camera systems, the Point Cloud engine may experience increased latency due to the amount of data it needs to handle in real-time. If the increased latency is causing frame drops or affecting the tracking quality, you can exclude selected cameras from contributing to the real-time reconstruction. In the [Devices pane](devices-pane.md), reveal the _Reconstruction_ setting from the header context menu, and disable this setting for the cameras that you wish to process later. 2D frames captured by these cameras will be recorded in the TAK but they will not contribute to real-time reconstruction. This will reduce the amount of data to be processed in real-time, and you will still be able to utilize the 2D frames using post-processing reconstruction pipeline.

![](<../.gitbook/assets/image (969).png>)
