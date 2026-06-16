---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/movement-sciences/prime-color-camera-setup/prime-color-camera-setup-faq-troubleshooting
---

# Prime Color Camera Setup: FAQ / Troubleshooting

<details>

<summary><strong>Q: Can custom camera lenses be used?</strong></summary>

A: The Prime Color camera uses the standard C mount for the lens, and lenses from other vendors can be mounted onto the color camera; however, there will be no guarantee for the lens and image quality. For this reason, we suggest using lenses that we provide.

</details>

<details>

<summary><strong>Q: Slow memory write out</strong></summary>

A: If the disk drive on the host PC is not fast enough to write the data, the RAM usage will gradually creep up to its maximum memory when recording a capture. In which case, the recorded TAK file may be corrupted or incomplete. If you are seeing this issue, you will have to lower down the [bit-rate](prime-color-camera-setup-camera-settings.md#bit-rate) to reduce the amount of data or use a faster disk drive.



</details>

<figure><img src="../../.gitbook/assets/image (833).png" alt=""><figcaption></figcaption></figure>

<details>

<summary><strong>Q: There are frame drops even when there is enough bandwidth available</strong></summary>

A: Dropped 2D frames with Prime Color in the system can be introduced due to the following issue:

* **Low PC Specifications or improper settings:** If you're seeing a significant amount of frame drops your PC specifications or settings may need to be upgraded and fine tuned. For the latest PC specifications and settings, please see our [Quick Start Guide: Prime Color Camera Setup](../../quick-start-guides/quick-start-guide-prime-color-camera-setup.md) page.
* **Network Bandwidth:** Insufficient network bandwidth will cause frame drops. You will have to make sure the network setup, including the network switches, Ethernet cables, and the network adapter on the host PC, is capable of transmitting and receiving data fast enough. See:[ Data Bandwidth](prime-color-setup-hardware-setup.md#data-bandwidth)
* **Audio playing in background (MMCSS):** When playing audio using applications (e.g. Chrome, VLC) that registers to Multimedia Class Scheduler Service (MMCSS), it will interfere with how the CPU resource is used in Motive. This service will prioritize time-sensitive multimedia applications to utilize the CPU resources as much as possible, which may cause increased latency which may lead to dropped frames. We recommend exiting out from such applications if there are any latency and frame drop issues. It is best to [remove any unnecessary apps and bloatware](../../quick-start-guides/quick-start-guide-prime-color-camera-setup.md#debloat-windows) to limit the competition of resources for Motive.&#x20;

</details>

