# Audio Playback Development
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## Selecting an Audio Playback Development Mode

The system provides a variety of APIs for you to develop audio playback applications. You can select them based on the audio data formats, audio sources, audio usage scenarios, and even the programming language you use. Selecting a suitable class helps you reduce development workload and your application deliver a better effect.

- [AudioRenderer](using-audiorenderer-for-playback.md): provides ArkTS and JS APIs to implement audio output. It supports only the PCM format and requires applications to continuously write audio data. The applications can perform data preprocessing, for example, setting the sampling rate and bit width of audio files, before audio input. This class can be used to develop more professional and diverse playback applications. To use this class, you must have basic audio processing knowledge.

- [AudioHaptic](using-audiohaptic-for-playback.md): provides ArkTS and JS APIs for audio playback with audio-haptic effect. It applies to scenarios where haptic feedback needs to be initiated synchronously during audio playback, for example, when there are incoming calls or messages or users are typing.

- [OpenSL ES](using-opensl-es-for-playback.md): provides a set of standard, cross-platform native audio APIs. It supports audio output in PCM format and is suitable for playback applications that are ported from other embedded platforms or that implement audio output at the native layer.

- [Using OHAudio for Audio Playback](using-ohaudio-for-playback.md): provides a set of native APIs for audio output. These APIs are normalized in design and support both common and low-latency audio channels. They support the PCM format only. They are suitable for playback applications that implement audio output at the native layer.<!--Del-->

- [TonePlayer](using-toneplayer-for-playback-sys.md): provides ArkTS and JS APIs to implement the playback of dialing tones and ringback tones. It can be used to play the content selected from a fixed type range, without requiring the input of media assets or audio data. This class is applicable to specific scenarios where dialing tones and ringback tones are played. It is available only to system applications.<!--DelEnd-->

In addition to the preceding classes, you can also use **AVPlayer** and **SoundPool** in Media Kit to implement audio playback.

- [AVPlayer](../media/using-avplayer-for-playback.md): provides ArkTS and JS APIs to implement audio playback. It also supports parsing streaming media and local assets, decapsulating media assets, decoding audio, and outputting audio. It can play audio files in MP3 and M4A formats, but not in PCM format.

- [SoundPool](../media/using-soundpool-for-playback.md): provides ArkTS and JS APIs to implement short sound playback in low latency mode. It can be used to play short sound effects, such as camera shutter sound effect, key press sound effect, and game shooting sound effect.

## Development Precautions for Background Playback

If you want the application to continue playing in the background, you must develop the audio playback functionality and choose either [accessing AVSession](../avsession/avsession-access-scene.md) or [requesting a continuous task](../../task-management/continuous-task.md) based on your service scenario. The specific rules are as follows:

- When an application needs to play media types (stream types **STREAM_USAGE_MUSIC**, **STREAM_USAGE_MOVIE**, and **STREAM_USAGE_AUDIOBOOK**) and game types (stream type **STREAM_USAGE_GAME**) in the background, it must access AVSession and request continuous tasks.

- In addition to the aforementioned playback types, when an application needs to run other user-perceptible tasks in the background for a long time, it must request continuous tasks of the [AUDIO_PLAYBACK](./../../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundmode) type.

If an application does not meet the above access standards, playback in the background will be muted and frozen by the system, preventing normal background playback. Playback will only resume and unmute when the application is brought back to the foreground.

For details, see [Background Playback](../avsession/avsession-background-scene.md).
