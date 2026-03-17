# Camera Status Indicators

This page includes information on the status indicator lights on the OptiTrack Ethernet cameras.

## PrimeX Series

### Status Ring Light

The PrimeX Series cameras have a front mounted status ring light to indicate the state of the Motive software and firmware updates on the cameras. The following table lists the default ring light color associated with the state of Motive.

Status Ring Light Colors

<table><thead><tr><th width="131">Color</th><th width="131">Status</th><th width="225">Description</th><th width="119">Can Modify Color</th><th>Photo</th></tr></thead><tbody><tr><td>Off</td><td>Powered &#x26; Awaiting Connection</td><td>When camera is first plugged in the LED ring light will be off until it receives commands from Motive and has successfully authenticated via the security key. If it is not successful in connecting to the network, but receiving power it will remain off with a small flashing white dot light in the bottom left corner.</td><td>No</td><td><img src="../.gitbook/assets/image (786).png" alt=""></td></tr><tr><td>Slow Flashing Cyan, no IR</td><td>Idle</td><td>Powered and connected to network, but Motive is not running. Two dashes in the bottom left corner will be present in lieu of ID number.</td><td>No</td><td><img src="../.gitbook/assets/image (684).png" alt=""></td></tr><tr><td>Cyan</td><td>Live</td><td>Actively sending data and receiving commands when loaded into Motive.</td><td>Yes</td><td><img src="../.gitbook/assets/image (453).png" alt=""></td></tr><tr><td>White/Off</td><td>Masking</td><td>When a marker, or what a camera perceives as a marker, is visible to a camera when masking in the Calibration pane, the status light will turn white. When masks are applied and no erroneous marker data is seen, the LEDs turn off and the volume is ready to wand.</td><td>No</td><td><img src="../.gitbook/assets/image (520).png" alt=""></td></tr><tr><td>Solid Green</td><td>Recording</td><td>Camera is sending data to be written to memory or disk.</td><td>Yes</td><td><img src="../.gitbook/assets/image (808).png" alt=""></td></tr><tr><td>Variable Green</td><td>Sampling During Calibration</td><td><p>Camera starts out black, then green will appear on the ring light depending on where you have wanded relative to that camera.</p><p>When the camera starts to take samples, there will be a white light that follows the wand movement rotating around the LED.</p><p>This will fill in dark green and then light green when enough samples are taken.</p></td><td>No</td><td><img src="../.gitbook/assets/image (665).png" alt=""><img src="../.gitbook/assets/image (695).png" alt=""><img src="../.gitbook/assets/image (517).png" alt=""></td></tr><tr><td>Flashing White</td><td>Calibration</td><td>During calibration when cameras have collected sufficient data they will turn green. Once enough cameras have collected enough samples the left over cameras will flash white indicating they still need to collect more samples for a successful calibration.</td><td>No</td><td><img src="../.gitbook/assets/image (711).png" alt=""></td></tr><tr><td>None</td><td>Playback</td><td>Camera is operating but Motive is in Edit Mode.</td><td>Yes</td><td><img src="../.gitbook/assets/image (767).png" alt=""></td></tr><tr><td>Yellow</td><td>Selected</td><td>Camera is selected in Motive.</td><td>Yes</td><td><img src="../.gitbook/assets/image (1354).png" alt=""></td></tr><tr><td>Red</td><td>Reference</td><td>Camera is in reference mode. Instead of capturing the marker data, the camera is recording reference video, Greyscale and MJPEG</td><td>Yes</td><td><img src="../.gitbook/assets/image (676).png" alt=""></td></tr><tr><td>Cycle Red</td><td>Firmware Reset</td><td>On board flash memory is being reset.</td><td>No</td><td><img src="../.gitbook/assets/image (728).png" alt=""></td></tr><tr><td>Cycle Cyan</td><td>Firmware Update</td><td>For PrimeX cameras. Firmware is being written to flash. On completion, color turns off and camera reboots.</td><td>No</td><td><img src="../.gitbook/assets/image (481).png" alt=""></td></tr><tr><td>Cycle Yellow</td><td>Firmware Update</td><td>For Prime cameras. Firmware is being written to flash. On completion, color turns off and camera reboots.</td><td>No</td><td><img src="../.gitbook/assets/image (690).png" alt=""></td></tr></tbody></table>

### Bottom Left Display

On every PrimeX camera there is an additional display in the bottom left corner of the face of the camera.

Bottom Left Display Values

| Display Output  | Status                                                                                                                                                                                                                                                                                                 |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Cycling Numbers | Camera is in the process of updating the firmware. The numbers will start at 0 and increase to 100 indicating that the firmware has completed 100% of the update.                                                                                                                                      |
| Constant Number | This is the number of the camera as assigned by Motive. Every time Motive is closed and reopened or a camera is removed from the system, the number will update accordingly.                                                                                                                           |
| 'E'             | If an 'E' error code appears in the display this means that the camera has lost connection to the network. To troubleshoot this, start by unplugging the camera and plugging it back into the camera switch. Alternatively, you may also try restarting the entire switch to reset the entire network. |

### Changing Status Ring Light

If for any reason you need to change the status ring light you can do so by going into **Settings** and under **General** click on the color box next to the status you would like to change. This will bring up a color picker window where you can choose a solid color or choose mutli-color to oscillate between colors. You also have the ability to save a color to your color library to apply it to other statuses.

#### Turning off Aim Assist Button LED

In order to disable the aim assist button LED on the back of PrimeX cameras, you simply toggle them off in the General settings. You can find this under Aim Assist > Aiming Button LED.

![](<../.gitbook/assets/image (789).png>)

### Back Light

The PrimeX Series cameras also have a status indicator on the back panel and indicate the state of the camera only. When changing to a new version of Motive, the camera will need a firmware update in order to communicate to the new version. Firmware updates are automatic when starting Motives. If the camera's firmware updates to a new version of Motive, running an older version of Motive will cause the firmware to necessarily revert back to an older version of firmware. This process is automatic as well.

Back Ring Light Colors

| Color                 | Status             | Description                                                                                                                               |
| --------------------- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Green                 | Initialize Phase 1 | Camera is powered and boot loader is running. Preparing to run main firmware.                                                             |
| Yellow                | Initialize Phase 2 | Firmware is running and switch communication in progress.                                                                                 |
| Blinking Green (Slow) | Initialize Phase 3 | Switch communication established and awaiting an IP address.                                                                              |
| Cyan                  | Firmware Loading   | Host has initiated firmware upload process.                                                                                               |
| Blinking Yellow       | Initialize Phase 4 | Camera has fully initialized. In process of synchronizing with camera group or eSync.                                                     |
| Blinking Green (Fast) | Running            | Camera is fully operational and synchronized to the camera group. Ready for data capture.                                                 |
| Blue                  | Hibernating        | Camera is in a low power state and not sending data. Occurs after closing Motive but leaving the cameras connected to the switch.         |
| Alternating Red       | Firmware Reset     | On board flash memory is being reset.                                                                                                     |
| Alternating Yellow    | Firmware Update    | Firmware is being written to flash. Numeric display in front will show progress. On completion, the light turns green and camera reboots. |

### Updating Firmware

When changing versions of Motive, a firmware update is needed. This process is automatic when opening the software and the status ring light and back ring light show the state, as described in the table above, of the camera during this process. The camera should not be unplugged during a firmware reset or firmware update. Give the camera time to finish this process before turning off the software.

If a camera doesn't update its firmware with the rest of the cameras, it will not get loaded into Motive. Wait for all cameras that are updating to finish, then restart Motive. The cameras that failed to update will now update. This could be caused by miscommunication between the switch when loading in numerous cameras.

## Slim 13E

### Front LED

| Color                    | Info                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Blue                     | Actively sending data and receiving commands when loaded into Motive.                                                                                                                                                                                                                                                                                                                                                              |
| Green                    | Camera is sending data to be written to memory or disk.                                                                                                                                                                                                                                                                                                                                                                            |
| None                     | Camera is operating but Motive is in Edit Mode.                                                                                                                                                                                                                                                                                                                                                                                    |
| Yellow                   | Camera is selected in Motive.                                                                                                                                                                                                                                                                                                                                                                                                      |
| Orange                   | Camera is in reference mode. Instead of capturing the marker data, the camera is recording reference video, MJPEG                                                                                                                                                                                                                                                                                                                  |
| Blinking red on start up | <ul><li>Firmware update is in progress, which is normal. Firmware will be updated when a new version of Motive is installed on the computer.</li><li>If the LED blinks in red a few times about 15 seconds after the camera start-up, it means that the camera has failed to establish a connection with the PoE switch. When this happens, error sign, <em>E</em> or <em>E1</em>, will be shown on the numeric display.</li></ul> |
| Yellow on start up       | The camera is attempting to establish a link with the PoE switch.                                                                                                                                                                                                                                                                                                                                                                  |

### Back Light

Like PrimeX series cameras, SlimX 13 cameras also have a status indicator on the back panel and indicate the state of the camera.

Back Ring Light Colors

| Color                 | Status             | Description                                                                                                                               |
| --------------------- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Green                 | Initialize Phase 1 | Camera is powered and boot loader is running. Preparing to run main firmware.                                                             |
| Yellow                | Initialize Phase 2 | Firmware is running and switch communication in progress.                                                                                 |
| Blinking Green (Slow) | Initialize Phase 3 | Switch communication established and awaiting an IP address.                                                                              |
| Cyan                  | Firmware Loading   | Host has initiated firmware upload process.                                                                                               |
| Blinking Yellow       | Initialize Phase 4 | Camera has fully initialized. In process of synchronizing with camera group or eSync2.                                                    |
| Blinking Green (Fast) | Running            | Camera is fully operational and synchronized to the camera group. Ready for data capture.                                                 |
| Blue                  | Hibernating        | Camera is in a low power state and not sending data. Occurs after closing Motive but leaving the cameras connected to the switch.         |
| Alternating Red       | Firmware Reset     | On board flash memory is being reset.                                                                                                     |
| Alternating Yellow    | Firmware Update    | Firmware is being written to flash. Numeric display in front will show progress. On completion, the light turns green and camera reboots. |
