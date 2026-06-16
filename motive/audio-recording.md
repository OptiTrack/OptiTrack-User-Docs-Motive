---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/GaZwzcsVav6zPBRZpapU/motive/audio-recording
---

# Audio Recording

{% hint style="danger" %}
It is heavily recommended that you use another audio capture software with timecode to capture and synchronize audio data. Audio capture in Motive is for **reference only** and is not intended to perfectly align to video or motion capture data.&#x20;
{% endhint %}

{% hint style="info" %}
Take scrubbing is not supported to align with audio recorded within Motive. If you would like the audio to be closely in reference to video and motion capture data, you must play the take from the beginning.&#x20;
{% endhint %}

Recorded “Take” files with audio data will play back sound and may be exported into WAV audio files. This page details audio capture recommendations and instructions for recording and playing back audio in Motive.

{% hint style="info" %}
**Confirmed Devices**

For the users who needs to use this feature, it's recommended to use one of the below devices that has been confirmed to work:

* AT2020 USB microphone
* mixPre-3
{% endhint %}

## Audio Recording and Playback

### Audio Recording Steps

1. In Motive, open the Audio tab of the [Settings](../motive-ui-panes/settings/settings-audio.md) window, then enable the “Capture” property.
2. Select the audio input device that you would like to use.
3. Make noise to confirm the microphone is working with the level visual.
4. Make sure the “Device Format” of the recording device matches the “Device Format” that will be used for playback (speakers and headsets).
5. Start capturing data.

### Audio Playback Steps

1. In Motive, open a _Take_ that includes audio data.
2. Open the Audio tab of the [Settings](../motive-ui-panes/settings/settings-audio.md) window, then enable the “Playback” property.
3. Select the audio output device that you will be using.
4. Make sure the configurations in _Device Format_ closely matches the _Take Format_.
5. Play the _Take_.

![](<../.gitbook/assets/image (1415).png>)

## Device Format

In order to playback audio recordings in Motive, the audio format of recorded data **MUST** closely match the audio format used by the output device. Specifically, the number of channels and frequency (Hz) of the audio must match. Otherwise, recorded sound will not be played back.

The recorded audio format is determined when a take is first recorded. The recorded data format and the playback format may not always agree by default. In this case, the windows audio settings will need to be adjusted to match the take.&#x20;

{% hint style="warning" %}
Audio capture within Motive, does not natively synchronize to video or motion capture data and is intended for **reference audio only**. If you require synchronization, please use an external device and software with timecode. See below for suggestions for [External Audio Capture](audio-recording.md#external-audio-capture).
{% endhint %}

A device's audio format can be configured under the Sound settings found in the Control Panel. To do this select the recording device, click on Properties, then the default format can be changed under the Advanced Tab as shown in the image below.

![Accessing microphone properties from the Sound settings.](<../.gitbook/assets/image (308).png>) ![Configuring microphone device format.](<../.gitbook/assets/image (1403).png>)

## Audio Export

Recorded audio files can be exported into WAV format. To export, right-click on a _Take_ from the [Data pane](../motive-ui-panes/data-pane.md) and select Export Audio option in the context menu.

![Exporting recorded audio in Motive.](<../.gitbook/assets/image (1389).png>)

## External Audio Capture

There are a variety of different programs and hardware that specialize in audio capture. A not very exhaustive list of examples can be seen below.

* Tentacle Sync TRACK E
* Adobe Premiere
* Avid Media Composer
* Etc...

In order to capture audio using a different program, you will need to connect both the motion capture system (through the eSync) and the audio capture device to timecode data (and possibly genlock data). You can then use the timecode information to synchronize the two sources of data for your end product.

For more information on synchronizing external devices, read through the [Synchronization](../synchronization/synchronization-setup.md) page.

## Suggested Capture Devices

The following devices are internally tested and should work for most use cases for **reference audio only**:

* AT2020 USB
* MixPre-3 II Digital USB Preamp
