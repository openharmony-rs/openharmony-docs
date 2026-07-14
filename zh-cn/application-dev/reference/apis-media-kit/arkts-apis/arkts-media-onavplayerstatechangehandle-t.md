# OnAVPlayerStateChangeHandle

```TypeScript
type OnAVPlayerStateChangeHandle = (state: AVPlayerState, reason: StateChangeReason) => void
```

播放状态机切换事件回调方法。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | AVPlayerState | 是 | 当前播放状态。 |
| reason | StateChangeReason | 是 | 当前播放状态的切换原因。 |

