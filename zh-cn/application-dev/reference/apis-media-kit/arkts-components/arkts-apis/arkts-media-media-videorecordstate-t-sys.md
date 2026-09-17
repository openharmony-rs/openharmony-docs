# VideoRecordState（系统接口）

```TypeScript
type VideoRecordState = 'idle' | 'prepared' | 'playing' | 'paused' | 'stopped' | 'error'
```

视频录制的状态机。可通过state属性获取当前状态。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| 'idle' | 视频录制空闲。 |
| 'prepared' | 视频录制参数设置完成。 |
| 'playing' | 视频正在录制。 |
| 'paused' | 视频暂停录制。 |
| 'stopped' | 视频录制停止。 |
| 'error' | 错误状态。 |
