# Adjusting Global Origin for Tracking Bars

{% hint style="danger" %}
USB Cameras are currently not supported in 3.x versions of Motive. The USB camera pages on this wiki are purely for reference only, at this time.
{% endhint %}

{% hint style="info" %}
The OptiTrack Duo/Trio tracking bars are factory calibrated and there is **no need to calibrate the cameras** to use the system. By default, the tracking volume is set at the center origin of the cameras and the axis are oriented so that Z-axis is forward, Y-axis is up, X-axis is left.
{% endhint %}

## Tracking Bar Coordinate System

If you wish to change the location and orientation of the global axis, you can use the ground plane tools from the [Calibration pane](https://v30.wiki.optitrack.com/index.php?title=Calibration) and use a Rigid Body or a calibration square to set the global origin.

![Default coordinate axis for the Trio tracking bar](<../../../../.gitbook/assets/image (878).png>) ![Default coordinate axis for the Duo tracking bar.](<../../../../.gitbook/assets/image (881).png>)

## Coordinate Systems Tool

When using the Duo/Trio tracking bars, you can set the coordinate origin at the desired location and orientation using either a Rigid Body or a [calibration square](../../../../motive/calibration/calibration-squares.md) as a reference point. Using a calibration square will allow you to set the origin more accurately. You can also use a custom calibration square to set this.

**Adjustig the Coordinate System Steps**

1. First set place the calibration square at the desired origin. If you are using a Rigid Body, its [pivot point](../../../../motive/rigid-body-tracking/) position and orientation will be used as the reference.
2. **\[Motive]** Open the [Calibration pane](../../../../motive/calibration/).
3. **\[Motive]** Open the _Ground Planes_ page.
4. **\[Motive]** Select the type of calibration square that will be used as a reference to set the global origin. Set it to Auto if you are using a calibration square from us. If you are using a Rigid Body, select the Rigid Body option from the drop-down menu. If you are using a [custom calibration square](../../../../motive/calibration/), you will need to set the vertical offset also.
5. **\[Motive]** Select the Calibration square markers or the Rigid Body markers from the [Perspective View pane](../../../../motive-ui-panes/viewport.md)
6. **\[Motive]** Click Set **Set Ground Plane** button, and the global origin will be adjusted.

![Ground plane page for adjusting global origin from the Calibration pane.](<../../../../.gitbook/assets/image (814).png>)

![Calibration square axis convention.](<../../../../.gitbook/assets/image (186).png>)
