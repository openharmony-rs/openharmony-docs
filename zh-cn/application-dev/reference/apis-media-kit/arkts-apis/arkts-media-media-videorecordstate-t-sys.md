# VideoRecordState（系统接口）

```TypeScript
type VideoRecordState = 'idle' | 'prepared' | 'playing' | 'paused' | 'stopped' | 'error'
```

从API version 9起停止维护，请使用AVRecorderState。 描述视频录制状态。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| 'idle' | 空闲状态。视频录制器已创建但未初始化。 |
| 'prepared' | 准备就绪状态。视频录制器已准备好录制。 |
| 'playing' | 播放状态。视频录制器正在录制。 |
| 'paused' | 暂停状态。视频录制器已暂停。 |
| 'stopped' | 停止状态。视频录制器已停止。 |
| 'error' | 错误状态。发生错误。 |
