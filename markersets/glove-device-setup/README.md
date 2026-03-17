# Glove Device Setup

### Motive Setup

#### **Step 1. Start Glove Software**

Before starting Motive, please make sure to launch your glove's software first.&#x20;

#### **Step 2. Start Motive**

Launch Motive. Connected gloves will be listed under the [Devices pane](../../motive-ui-panes/devices-pane.md).

![Manus VR Gloves listed in Motive.](<../../.gitbook/assets/image (1123).png>)

#### **Step 3. Create a Skeleton in Motive.**

Use the Builder pane to define a [Skeleton asset](https://github.com/OptiTrack/GitBook-Wiki/blob/main/motive/Skeleton-tracking.md) in Motive. You can use any Skeleton model that is not designed to track fingers using motion capture data. The recommended Skeletons models to use are the _Core 50_ or _Baseline 41_.

#### **Step 4. Pair Skeleton with the device**

After a Skeleton has been defined, pair the Skeleton to the glove device. Open the [Devices pane](../../motive-ui-panes/devices-pane.md), right-click on the listed glove device, and pair it to the Skeleton as shown in the screenshot below.

![Pairing Skeleton to a glove device](<../../.gitbook/assets/image (1144).png>)

![Gloves paired to Skeleton asset.](<../../.gitbook/assets/image (1106).png>)

#### **Step 5. Confirm the tracking**

Once the glove has been configured and paired with the created Skeleton, the fingers will be tracking in Motive.

<figure><img src="../../.gitbook/assets/image (829).png" alt=""><figcaption><p>Finger tracking from gloves integrated in Motive.</p></figcaption></figure>

## Export and streaming

Once Motive starts tracking the glove, the finger tracking data can be outputted for various applications. Real-time finger data can be streamed into any NatNet client, and recorded finger data can be exported into other file formats. For instructions on outputting tracking data from Motive, refer to the following pages:

* [Data Streaming](../../motive/data-streaming.md)
* [Data Export](../../motive/data-export/)
