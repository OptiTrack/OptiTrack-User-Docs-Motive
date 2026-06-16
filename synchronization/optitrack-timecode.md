---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/synchronization/optitrack-timecode
---

# OptiTrack Timecode

## Overview

This page covers the timecode representation in Motive and how it can be accessed through the [NatNet SDK](../developer-tools/natnet-sdk/) library tools.

## Timecode Integration

\
SMPTE Timecode signals can be integrated into OptiTrack motion capture systems through the eSync 2 synchronization hub. To do this, simply connect a timecode sync source to the _SMPTE Timecode Input_ of the eSync 2. Once the signal is detected, the corresponding timecode will be displayed at the top-right corner of the [Perspective View pane](../motive-ui-panes/viewport.md#perspective-view) in Motive. When you capture a _Take_ with timecode signal, the information saved into the corresponding _Take_ file.

**Note:** SMPTE Timecode integration requires the eSync 2 hub.

![Timecode display in Motive](<../.gitbook/assets/image (1127).png>) ![The eSync 2 synchronization hub. SMPTE Timecode signal connects to the input port E.](<../.gitbook/assets/image (857).png>)

## Timecode Representation

When SMPTE timecode signal is available within a system, each frame of data will contain an _OptiTrack timecode stamp_, which is an extended form of the typical studio SMPTE timecode stamp. Since the frame rate of an OptiTrack mocap system typically exceeds standard SMPTE timecode frame rates, an additional “subframe” value is added at the end of the timecode stamp. This “subframe” value is 0-based and indicates increments of captured mocap frames _in between_ every SMPTE timecode frames:

![OptiTrack Timecode Representation: 120 fps mocap data, 30-fps no-drop SMPTE timecode source.](<../.gitbook/assets/image (1331).png>)

In the above sample representation, a 120 FPS motion capture session is synchronized to a sync source with 30 FPS no-drop SMPTE timecode signal. In this case, there is a 4 : 1 ratio of number motion capture frames to a single frame of the sync source, and the extra motion capture frames are represented by the OptiTrack SubFrame field in the OptiTrack timecode.

{% hint style="info" %}
The generic form for OptiTrack timecode: **HH:MM:SS:FF.Y (hours:minutes:seconds:frames.subframe)**
{% endhint %}

## NatNet: Timecode

When using the [NatNet SDK 4.0](../developer-tools/natnet-sdk/natnet-4.5.md), the OptiTrack timecode is sent to NatNet clients in the form of two unsigned integers contained within the packet of [sFrameOfMocapData](../developer-tools/natnet-sdk/natnet-data-types.md):

* **OptiTrack encoded SMPTE timecode**: `Unsigned int Timecode`
* **OptiTrack encoded sub-frame data**: `Unsigned int TimecodeSubframe`

The `Unsigned int Timecode` parameter is interpreted differently when streaming from a live data (Live Mode) compared to when streaming from a recorded playback (Edit Mode). The differences are listed below:

* [**Live mode**](../motive-ui-panes/control-deck.md#live-and-edit-mode): When streaming in real-time, the _Timecode_ parameter is available only when SMPTE timecode signal is present in your mocap hardware setup; typically when using the eSync and a timecode generator. When present, the Timecode parameter will be a correctly formatted SMPTE timecode value.
* [**Edit Mode**](../motive-ui-panes/control-deck.md#live-and-edit-mode): When streaming from a recorded playback, the _Timecode_ parameter is the current frame number converted to SMPTE Timecode format.

### NatNet: Timecode Helper Functions

Timecode values should not be used directly, but decoded using the provided NatNet tools. Within the [NatNetClient](../developer-tools/natnet-sdk/natnet-class-function-reference.md#natnetclient-class) class, there are methods for decoding the Timecode parameter and the TimecodeSubframe parameter ([DecodeTimecode](../developer-tools/natnet-sdk/natnet-class-function-reference.md)) and converting them into a string-friendly format ([TimecodeStringify](../developer-tools/natnet-sdk/natnet-class-function-reference.md)).

The NatNet SDK provides [utility functions](../developer-tools/natnet-sdk/natnet-class-function-reference.md) for decoding the Timecode parameter and the TimecodeSubframe parameter ([NatNet\_DecodeTimecode](../developer-tools/natnet-sdk/natnet-class-function-reference.md)) and converting them into a string-friendly format ([NatNet\_TimecodeStringify](../developer-tools/natnet-sdk/natnet-class-function-reference.md)).

#### **NatNet\_DecodeTimecode**

Helper function to decode OptiTrack timecode data into individual timecode values bool NatNet\_DecodeTimecode(unsigned int inTimecode, unsigned int inTimecodeSubframe,

```
            int* hour, int* minute, int* second, 
            int* frame, int* subframe);
```

#### **NatNet\_TimecodeStringify**

Helper function to decode OptiTrack timecode into a user friendly string in the form “hh:mm:ss:ff:yy” bool NatNet\_TimecodeStringify(unsigned int inTimecode, unsigned int inTimecodeSubframe,

```
            char *Buffer, int BufferSize);
```

#### **C++ Sample: Using the utility functions for timecode parameters**

The following is an example of how to decode timecode using the NatNet helper functions (from the SampleClient.cpp example): // decode timecode to values int hour, minute, second, frame, subframe; bool bValid = pClient->DecodeTimecode(data->Timecode, data->TimecodeSubframe,

```
        &hour, &minute, &second, &frame, &subframe);
```

// decode timecode to friendly string char szTimecode\[128] = ""; pClient->TimecodeStringify(data->Timecode, data->TimecodeSubframe, szTimecode, 128); printf("Timecode : %s\n", szTimecode);
