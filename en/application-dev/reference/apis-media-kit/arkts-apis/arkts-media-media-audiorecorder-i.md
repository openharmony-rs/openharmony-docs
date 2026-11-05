# AudioRecorder

```TypeScript
interface AudioRecorder
```

**AudioRecorder** is a class for audio recording management. It provides APIs to record audio. It supports operations such as preparing, starting, pausing, resuming, stopping, releasing, and resetting audio recording. The APIs of this class are applicable to scenarios where audio needs to be recorded, such as voice notes, call recording, and music recording. Before calling any API in **AudioRecorder**, you must use [createAudioRecorder()](arkts-media-media-createaudiorecorder-f.md) to create an **AudioRecorder** instance.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [media](arkts-media-multimedia-media.md)

<!--Device-media-interface AudioRecorder--><!--Device-media-interface AudioRecorder-End-->

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

Subscribes to the audio recording events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

<!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void--><!--Device-AudioRecorder-on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void-End-->

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'prepare' &#124; 'start' &#124; 'pause' &#124; 'resume' &#124; 'stop' &#124; 'release' &#124; 'reset' | Yes | Event type. The following events are supported: 'prepare', 'start', 'pause', 'resume', 'stop', 'release', and 'reset'.<br> -&nbsp;'prepare'&nbsp;: triggered when the **prepare()** API is called and the audio recording parameters are set.<br>-&nbsp;'start'&nbsp;: triggered when the **start()** API is called and audio recording starts.<br> -&nbsp;'pause'&nbsp;: triggered when the **pause()** API is called and audio recording is paused.<br> -&nbsp;'resume'&nbsp;: triggered when the **resume()** API is called and audio recording is resumed.<br> -&nbsp;'stop'&nbsp;: triggered when the **stop()** API is called and audio recording stops.<br> -&nbsp;'release'&nbsp;: triggered when the **release()** API is called and the recording resources are released.<br>-&nbsp;'reset'&nbsp;: triggered when the **reset()** API is called and audio recording is reset. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to the audio recording error event. After an error event is received, you must handle the error, release resources, and exit the current recording.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avrecorder-i.md#onerror)(type: 'error', callback: ErrorCallback)

<!--Device-AudioRecorder-on(type: 'error', callback: ErrorCallback): void--><!--Device-AudioRecorder-on(type: 'error', callback: ErrorCallback): void-End-->

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type, which is **'error'** in this case.<br>This event is triggered when an error occurs during audio recording. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback invoked when the event is triggered. |

## pause

```TypeScript
pause(): void
```

Pauses recording. This API can be called only after the **start()** API is called.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [pause](arkts-media-media-avrecorder-i.md#pause-1)(callback: AsyncCallback&lt;void&gt;)

<!--Device-AudioRecorder-pause(): void--><!--Device-AudioRecorder-pause(): void-End-->

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## prepare

```TypeScript
prepare(config: AudioRecorderConfig): void
```

Prepares for recording. This method can be used to initialize recording resources (including the encoder, sampling rate, and number of audio channels) based on the input configuration parameters.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [prepare](arkts-media-media-avrecorder-i.md#prepare-1)(config: AVRecorderConfig, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.MICROPHONE

<!--Device-AudioRecorder-prepare(config: AudioRecorderConfig): void--><!--Device-AudioRecorder-prepare(config: AudioRecorderConfig): void-End-->

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [AudioRecorderConfig](arkts-media-media-audiorecorderconfig-i.md) | Yes | Audio recording parameters, including the audio output URI, encoding format, sample rate, audio channel count, and output format. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | permission denied.<br>**Applicable version:** 12 and later |

## release

```TypeScript
release(): void
```

Releases recording resources. After the resources are released, other recording methods cannot be called.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [release](arkts-media-media-avrecorder-i.md#release-1)(callback: AsyncCallback&lt;void&gt;)

<!--Device-AudioRecorder-release(): void--><!--Device-AudioRecorder-release(): void-End-->

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## reset

```TypeScript
reset(): void
```

Resets recording.

Before resetting audio recording, you must call **stop()** to stop recording. After audio recording is reset, you must call **prepare()** to set the recording configurations for another recording.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [reset](arkts-media-media-avrecorder-i.md#reset-1)(callback: AsyncCallback&lt;void&gt;)

<!--Device-AudioRecorder-reset(): void--><!--Device-AudioRecorder-reset(): void-End-->

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## resume

```TypeScript
resume(): void
```

Resumes recording. This API can be called only after the **pause()** API is called.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [resume](arkts-media-media-avrecorder-i.md#resume-1)(callback: AsyncCallback&lt;void&gt;)

<!--Device-AudioRecorder-resume(): void--><!--Device-AudioRecorder-resume(): void-End-->

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## start

```TypeScript
start(): void
```

Starts recording. This API can be called only after the **prepare()** API is called.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [start](arkts-media-media-avrecorder-i.md#start-1)(callback: AsyncCallback&lt;void&gt;)

<!--Device-AudioRecorder-start(): void--><!--Device-AudioRecorder-start(): void-End-->

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## stop

```TypeScript
stop(): void
```

Stops recording and saves the recorded audio data to a file. This API can be called only after the **start()** API is called.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [stop](arkts-media-media-avrecorder-i.md#stop-1)(callback: AsyncCallback&lt;void&gt;)

<!--Device-AudioRecorder-stop(): void--><!--Device-AudioRecorder-stop(): void-End-->

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder
