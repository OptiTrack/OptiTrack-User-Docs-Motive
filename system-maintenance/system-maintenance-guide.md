# System Maintenance Guide

Regular maintenance helps ensure consistent tracking quality, minimizes downtime, and extends the life of your motion capture system. Following a preventative maintenance schedule is typically far more effective than addressing issues after tracking quality deteriorates. We recommend going through a daily or per-use checklist, a brief monthly inspection, and a periodic calibration verification, which collectively can prevent most common system performance issues.

## Signs That Maintenance or Recalibration Might Be Required

* Increased marker swaps or labeling issues.
* Reduced tracking accuracy or coverage.
* Cameras that frequently disconnect.
* The need for increasingly aggressive tracking settings.
* Tracking blind spots that were not previously present.
* The average residual has increased considerably.

## Daily / Before-Use Checklist

* Verify that all cameras are connected and communicating with the software.
* Confirm that [synchronization devices](../synchronization/) and network hardware items are functioning normally.
* Perform a quick tracking test to ensure that markers are detected and reconstructed correctly.
* Check for any unexpected environmental changes that could affect tracking, such as moved equipment, new reflective surfaces, or lighting changes.
* Validate system calibration, especially if:
  * Cameras have been moved.
  * Truss structures or mounts have been adjusted.
  * Environmental conditions have changed.
  * Tracking quality appears reduced.
  * Average residual has increased significantly.
* Review calibration quality metrics and perform recalibration if necessary.

## Monthly Inspection

### Cameras and Optics

* Inspect camera lenses and protective windows for dust, fingerprints, or debris.
* Clean optical surfaces with an appropriate microfiber cloth when needed.
* Verify that [camera mounts](../hardware/) remain secure and have not shifted position.
* Confirm that [camera focus](../hardware/aiming-and-focusing.md#adjusting-focus) remains sharp throughout the capture volume.

### Cables and Network

* Inspect Ethernet and synchronization cables for wear, damage, or loose connections.
* Verify that all [switches, power supplies, and network infrastructure](../hardware/cabling-and-wiring/cabling-and-load-balancing.md) devices are operating correctly.
* Confirm that adequate ventilation exists around network equipment and workstations.

### Capture Volume Assessment

* Walk through the capture area and verify expected tracking coverage.
* Identify and remove new sources of occlusion where possible.
* Check for reflective objects that could create unwanted marker detections.
* Confirm that active and passive markers remain visible to multiple cameras throughout the working volume.

### Software and System Updates

* Keep computer operating systems, motion capture software, and supporting components up to date according to your organization's validation process.
* Test updates in a controlled environment before deployment on production systems when practical.
* Maintain backups of [calibration files](../motive/calibration/#calibration-files), asset definitions, and important project configurations.

### Marker and Asset Maintenance

* Inspect markers for damage, contamination, or wear.
* Replace worn markers that exhibit inconsistent performance.
* Verify that rigid body definitions and skeleton assets continue to solve correctly after significant workflow changes.

## Annual Preventive Review

Consider a comprehensive system review that includes:

* [Camera positioning](../hardware/camera-placement.md) and coverage analysis.
* Calibration validation.
* Network infrastructure inspection.
* Software review.
* Workflow and operator training refresh.
* Review of system expansion or optimization opportunities.
