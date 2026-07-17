# AVRecorderState

```TypeScript
type AVRecorderState = 'idle' | 'prepared' | 'started' | 'paused' | 'stopped' | 'released' | 'error'
```

音视频录制的状态机。可通过state属性获取当前状态。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type AVRecorderState = 'idle' | 'prepared' | 'started' | 'paused' | 'stopped' | 'released' | 'error'--><!--Device-unnamed-type AVRecorderState = 'idle' | 'prepared' | 'started' | 'paused' | 'stopped' | 'released' | 'error'-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

| 类型 | 说明 |
| --- | --- |
| 'idle' | 闲置状态。此时可以调用[AVRecorder.prepare()]{ |
| 'prepared' | 参数设置完成。此时可以调用[AVRecorder.start()]{ |
| 'started' | 正在录制。此时可以调用[AVRecorder.pause()]{ |
| 'paused' | 录制暂停。此时可以调用[AVRecorder.resume()]{ |
| 'stopped' | 录制停止。此时可以调用[AVRecorder.prepare()]{ |
| 'released' | 录制资源释放。此时不能再进行任何操作。在任何其他状态下，均可以通过调用[AVRecorder.release()]{ |
| 'error' | 错误状态。当AVRecorder实例发生不可逆错误，会转换至当前状态。切换至error状态时会伴随[AVRecorder.on('error')事件]{ |

