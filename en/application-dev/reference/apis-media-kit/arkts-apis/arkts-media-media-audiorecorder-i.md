# AudioRecorder

AudioRecorder is a class for audio recording management. It provides APIs to record audio. Before calling any API in AudioRecorder, you must use [createAudioRecorder()](arkts-media-media-createaudiorecorder-f.md) to create an AudioRecorder instance.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [media](arkts-media-multimedia-media.md)

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

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'prepare' &#124; 'start' &#124; 'pause' &#124; 'resume' &#124; 'stop' &#124; 'release' &#124; 'reset' | Yes | Event type. The following events are supported: 'prepare'&#124;'start'&#124; 'pause' &#124; 'resume' &#124;'stop'&#124;'release'&#124;'reset'<br>- 'prepare': triggered when the **prepare()** API is called and the audio recording parameters are set.<br>- 'start': triggered when the **start()** API is called and audio recording starts.<br>- 'pause': triggered when the **pause()** API is called and audio recording is paused.<br>- 'resume': triggered when the **resume()** API is called and audio recording is resumed.<br>- 'stop': triggered when the **stop()** API is called and audio recording stops.<br>- 'release': triggered when the **release()** API is called and the recording resources are released.<br>- 'reset': triggered when the **reset()** API is called and audio recording is reset. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

Subscribes to the audio recording events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'prepare' &#124; 'start' &#124; 'pause' &#124; 'resume' &#124; 'stop' &#124; 'release' &#124; 'reset' | Yes | Event type. The following events are supported: 'prepare'&#124;'start'&#124; 'pause' &#124; 'resume' &#124;'stop'&#124;'release'&#124;'reset'<br>- 'prepare': triggered when the **prepare()** API is called and the audio recording parameters are set.<br>- 'start': triggered when the **start()** API is called and audio recording starts.<br>- 'pause': triggered when the **pause()** API is called and audio recording is paused.<br>- 'resume': triggered when the **resume()** API is called and audio recording is resumed.<br>- 'stop': triggered when the **stop()** API is called and audio recording stops.<br>- 'release': triggered when the **release()** API is called and the recording resources are released.<br>- 'reset': triggered when the **reset()** API is called and audio recording is reset. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

Subscribes to the audio recording events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'prepare' &#124; 'start' &#124; 'pause' &#124; 'resume' &#124; 'stop' &#124; 'release' &#124; 'reset' | Yes | Event type. The following events are supported: 'prepare'&#124;'start'&#124; 'pause' &#124; 'resume' &#124;'stop'&#124;'release'&#124;'reset'<br>- 'prepare': triggered when the **prepare()** API is called and the audio recording parameters are set.<br>- 'start': triggered when the **start()** API is called and audio recording starts.<br>- 'pause': triggered when the **pause()** API is called and audio recording is paused.<br>- 'resume': triggered when the **resume()** API is called and audio recording is resumed.<br>- 'stop': triggered when the **stop()** API is called and audio recording stops.<br>- 'release': triggered when the **release()** API is called and the recording resources are released.<br>- 'reset': triggered when the **reset()** API is called and audio recording is reset. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

Subscribes to the audio recording events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'prepare' &#124; 'start' &#124; 'pause' &#124; 'resume' &#124; 'stop' &#124; 'release' &#124; 'reset' | Yes | Event type. The following events are supported: 'prepare'&#124;'start'&#124; 'pause' &#124; 'resume' &#124;'stop'&#124;'release'&#124;'reset'<br>- 'prepare': triggered when the **prepare()** API is called and the audio recording parameters are set.<br>- 'start': triggered when the **start()** API is called and audio recording starts.<br>- 'pause': triggered when the **pause()** API is called and audio recording is paused.<br>- 'resume': triggered when the **resume()** API is called and audio recording is resumed.<br>- 'stop': triggered when the **stop()** API is called and audio recording stops.<br>- 'release': triggered when the **release()** API is called and the recording resources are released.<br>- 'reset': triggered when the **reset()** API is called and audio recording is reset. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

Subscribes to the audio recording events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'prepare' &#124; 'start' &#124; 'pause' &#124; 'resume' &#124; 'stop' &#124; 'release' &#124; 'reset' | Yes | Event type. The following events are supported: 'prepare'&#124;'start'&#124; 'pause' &#124; 'resume' &#124;'stop'&#124;'release'&#124;'reset'<br>- 'prepare': triggered when the **prepare()** API is called and the audio recording parameters are set.<br>- 'start': triggered when the **start()** API is called and audio recording starts.<br>- 'pause': triggered when the **pause()** API is called and audio recording is paused.<br>- 'resume': triggered when the **resume()** API is called and audio recording is resumed.<br>- 'stop': triggered when the **stop()** API is called and audio recording stops.<br>- 'release': triggered when the **release()** API is called and the recording resources are released.<br>- 'reset': triggered when the **reset()** API is called and audio recording is reset. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

Subscribes to the audio recording events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'prepare' &#124; 'start' &#124; 'pause' &#124; 'resume' &#124; 'stop' &#124; 'release' &#124; 'reset' | Yes | Event type. The following events are supported: 'prepare'&#124;'start'&#124; 'pause' &#124; 'resume' &#124;'stop'&#124;'release'&#124;'reset'<br>- 'prepare': triggered when the **prepare()** API is called and the audio recording parameters are set.<br>- 'start': triggered when the **start()** API is called and audio recording starts.<br>- 'pause': triggered when the **pause()** API is called and audio recording is paused.<br>- 'resume': triggered when the **resume()** API is called and audio recording is resumed.<br>- 'stop': triggered when the **stop()** API is called and audio recording stops.<br>- 'release': triggered when the **release()** API is called and the recording resources are released.<br>- 'reset': triggered when the **reset()** API is called and audio recording is reset. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset')

```TypeScript
on(type: 'prepare' | 'start' | 'pause' | 'resume' | 'stop' | 'release' | 'reset', callback: () => void): void
```

Subscribes to the audio recording events.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avrecorder-i.md#onstatechange)(type: 'stateChange', callback: OnAVRecorderStateChangeHandler)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'prepare' &#124; 'start' &#124; 'pause' &#124; 'resume' &#124; 'stop' &#124; 'release' &#124; 'reset' | Yes | Event type. The following events are supported: 'prepare'&#124;'start'&#124; 'pause' &#124; 'resume' &#124;'stop'&#124;'release'&#124;'reset'<br>- 'prepare': triggered when the **prepare()** API is called and the audio recording parameters are set.<br>- 'start': triggered when the **start()** API is called and audio recording starts.<br>- 'pause': triggered when the **pause()** API is called and audio recording is paused.<br>- 'resume': triggered when the **resume()** API is called and audio recording is resumed.<br>- 'stop': triggered when the **stop()** API is called and audio recording stops.<br>- 'release': triggered when the **release()** API is called and the recording resources are released.<br>- 'reset': triggered when the **reset()** API is called and audio recording is reset. |
| callback | () =&gt; void | Yes | Callback invoked when the event is triggered. |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to audio recording error events. After an error event is reported, you must handle the event and exit the recording.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [on](arkts-media-media-avrecorder-i.md#onerror)(type: 'error', callback: ErrorCallback)

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

Pauses audio recording. This API can be called only after the **'start'** event is triggered.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [pause](arkts-media-media-avrecorder-i.md#pause)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## prepare

```TypeScript
prepare(config: AudioRecorderConfig): void
```

Prepares for recording.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [prepare](arkts-media-media-avrecorder-i.md#prepare)(config: AVRecorderConfig, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.MICROPHONE

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

Releases the audio recording resources.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [release](arkts-media-media-avrecorder-i.md#release)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## reset

```TypeScript
reset(): void
```

Resets audio recording.

Before resetting audio recording, you must call **stop()** to stop recording. After audio recording is reset, you must call **prepare()** to set the recording configurations for another recording.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [reset](arkts-media-media-avrecorder-i.md#reset)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## resume

```TypeScript
resume(): void
```

Resumes audio recording. This API can be called only after the **'pause'** event is triggered.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [resume](arkts-media-media-avrecorder-i.md#resume)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## start

```TypeScript
start(): void
```

Starts audio recording. This API can be called only after the **'prepare'** event is triggered.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [start](arkts-media-media-avrecorder-i.md#start)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## stop

```TypeScript
stop(): void
```

Stops audio recording.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [stop](arkts-media-media-avrecorder-i.md#stop)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder
