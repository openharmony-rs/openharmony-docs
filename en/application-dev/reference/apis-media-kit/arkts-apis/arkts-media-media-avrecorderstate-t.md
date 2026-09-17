# AVRecorderState

```TypeScript
type AVRecorderState = 'idle' | 'prepared' | 'started' | 'paused' | 'stopped' | 'released' | 'error'
```

Enumerates the AVRecorder states. You can obtain the state through the **state** property.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

| Type | Description |
| --- | --- |
| 'idle' | The AVRecorder enters this state after it is just created or the [AVRecorder.reset()](arkts-media-media-avrecorder-i.md#reset) API is called when the AVRecorder is in any state except released. In this state, you can call [AVRecorder.prepare()](arkts-media-media-avrecorder-i.md#prepare) to set recording parameters. |
| 'prepared' | The AVRecorder enters this state when the parameters are set. In this state, you can call [AVRecorder.start()](arkts-media-media-avrecorder-i.md#start) to start recording. |
| 'started' | The AVRecorder enters this state when the recording starts. In this state, you can call [AVRecorder.pause()](arkts-media-media-avrecorder-i.md#pause) to pause recording or call [AVRecorder.stop()](arkts-media-media-avrecorder-i.md#stop) to stop recording. |
| 'paused' | The AVRecorder enters this state when the recording is paused. In this state, you can call [AVRecorder.resume()](arkts-media-media-avrecorder-i.md#resume) to continue recording or call [AVRecorder.stop()](arkts-media-media-avrecorder-i.md#stop) to stop recording. |
| 'stopped' | The AVRecorder enters this state when the recording stops. In this state, you can call [AVRecorder.prepare()](arkts-media-media-avrecorder-i.md#prepare) to set recording parameters so that the AVRecorder enters the prepared state again. |
| 'released' | The AVRecorder enters this state when the recording resources are released. In this state, no operation can be performed. In any other state, you can call [AVRecorder.release()](arkts-media-media-avrecorder-i.md#release) to enter the released state. |
| 'error' | The AVRecorder enters this state when an irreversible error occurs in the AVRecorder instance. In this state, the [AVRecorder.on('error') event](arkts-media-media-avrecorder-i.md#onerror) is reported, with the detailed error cause. In the error state, you must call [AVRecorder.reset()](arkts-media-media-avrecorder-i.md#reset) to reset the AVRecorder instance or call [AVRecorder.release()](arkts-media-media-avrecorder-i.md#release) to release the resources. |
