# OnAVRecorderStateChangeHandler

```TypeScript
type OnAVRecorderStateChangeHandler = (state: AVRecorderState, reason: StateChangeReason) => void
```

录制状态机切换事件回调方法。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type OnAVRecorderStateChangeHandler = (state: AVRecorderState, reason: StateChangeReason) => void--><!--Device-unnamed-type OnAVRecorderStateChangeHandler = (state: AVRecorderState, reason: StateChangeReason) => void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [AVRecorderState](arkts-media-avrecorderstate-t.md) | 是 | 当前录制状态。  |
| reason | [StateChangeReason](arkts-media-media-statechangereason-e.md) | 是 | 当前录制状态的切换原因。  |

