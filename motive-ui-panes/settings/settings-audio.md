# Settings: Audio

In Motive, the Application Settings can be accessed under the [View tab](../toolbar-command-bar.md#view) or by clicking [![Toolbar AppSettings 20.png](https://v30.wiki.optitrack.com/images/8/8e/Toolbar_AppSettings_20.png)](https://v30.wiki.optitrack.com/index.php?title=File:Toolbar_AppSettings_20.png) icon on the main toolbar. Default Application Settings can be recovered by Reset Application Settings under the Edit Tools tab from the main [Toolbar](../toolbar-command-bar.md).

If you have an audio input device, you can record _synchronized_ audio along with motion capture data in Motive. Recorded audio files can be played back from a captured _Take_ or be exported into a WAV audio files. This page details how to record and playback audio in Motive. Before using an audio input device (microphone) in Motive, first make sure that the device is properly connected and configured in Windows.

## Audio Recording/Playback

### Audio Settings

In Motive, audio recording and playback settings can be accessed from [Application Settings](./).

![Audio settings in Motive.](<../../.gitbook/assets/image (372).png>)

### Audio Recording Steps

1. In Motive, open the Audio Settings, and check the box next to _Enable Capture_.
2. Select the audio input device that you want to use.
3. Press the Test button to confirm that the input device is properly working.
4. Make sure the device format of the recording device matches the device format that will be used in the playback devices (speakers and headsets).
5. Capture the _Take_.

### Audio Playback Steps

1. Enable the Audio device before loading the TAK file with audio recordings. Enabling after is currently not supported, as the audio engine gets initialized on TAK load
2. Open a _Take_ that includes audio recordings.
3. To playback recorded audio from a Take, check the box next to _Enable Playback_.
4. Select the audio output device that you will be using.
5. Make sure the configurations in _Device Format_ closely match the _Take Format_. This is elaborated further in the section below.
6. Play the _Take_.

## Device Format

In order to playback audio recordings in Motive, audio format of recorded sounds **MUST** match closely with the audio format used in the output device. Specifically, communication channels and frequency of the audio must match. Otherwise, recorded sound will not be played back.

The recorded audio format is determined by the format of a recording device that was used when capturing _Takes_. However, audio formats in the input and output devices may not always agree. In this case, you will need to adjust the input device properties to match them. Device's audio format can be configured under the Sound settings in Windows. In Sound settings (accessed from Control Panel), select the recording device, click on Properties, and the default format can be changed under the Advanced Tab, as shown in the image below.

![Accessing microphone properties from the Sound settings.](<../../.gitbook/assets/image (339).png>) ![Configuring microphone device format.](<../../.gitbook/assets/image (302) (1).png>)

## Audio Export

Recorded audio files can be exported into WAV format. To export, right-click on a _Take_ from the [Data pane](../data-pane.md) and select Export Audio option in the context menu.

![Exporting recorded audio in Motive.](<../../.gitbook/assets/image (358).png>)

## Other Options

If you want to use an external audio input system to record synchronized audio, you will need to connect the motion capture system into a Genlock signal or a Timecode device. This will allow you to precisely synchronize the recorded audio along with the capture data.

For more information on synchronizing external devices, read through the [Synchronization](../../synchronization/synchronization-setup.md) page.
