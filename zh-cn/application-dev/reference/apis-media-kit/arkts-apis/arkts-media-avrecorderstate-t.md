# AVRecorderState

```TypeScript
type AVRecorderState = 'idle' | 'prepared' | 'started' | 'paused' | 'stopped' | 'released' | 'error'
```

音视频录制的状态机。可通过state属性获取当前状态。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

| 类型 | 说明 |
| --- | --- |
| 'idle' | The AVRecorder enters this state after it is just created or the[AVRecorder.reset()]{ |
| 'prepared' | The AVRecorder enters this state when the parameters are set. In this state, you cancall [AVRecorder.start()]{ |
| 'started' | The AVRecorder enters this state when the recording starts. In this state, you can call[AVRecorder.pause()]{ |
| 'paused' | The AVRecorder enters this state when the recording is paused. In this state, you cancall [AVRecorder.resume()]{ |
| 'stopped' | The AVRecorder enters this state when the recording stops. In this state, you can call[AVRecorder.prepare()]{ |
| 'released' | The AVRecorder enters this state when the recording resources are released. In thisstate, no operation can be performed. In any other state, you can call[AVRecorder.release()]{ |
| 'error' | The AVRecorder enters this state when an irreversible error occurs in the AVRecorderinstance. In this state, the[AVRecorder.on('error') event]{ |

