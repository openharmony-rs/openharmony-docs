# VideoRecordState（系统接口）

```TypeScript
type VideoRecordState = 'idle' | 'prepared' | 'playing' | 'paused' | 'stopped' | 'error'
```

The maintenance of this interface has been stopped since version api 9. Please use AVRecorderState.Describes video recorder states.

**起始版本：** 9

<!--Device-unnamed-type VideoRecordState = 'idle' | 'prepared' | 'playing' | 'paused' | 'stopped' | 'error'--><!--Device-unnamed-type VideoRecordState = 'idle' | 'prepared' | 'playing' | 'paused' | 'stopped' | 'error'-End-->

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| 'idle' | Idle state. The video recorder is created but not initialized. |
| 'prepared' | Prepared state. The video recorder is ready to record. |
| 'playing' | Playing state. The video recorder is recording. |
| 'paused' | Paused state. The video recorder is paused. |
| 'stopped' | Stopped state. The video recorder is stopped. |
| 'error' | Error state. An error occurred. |

