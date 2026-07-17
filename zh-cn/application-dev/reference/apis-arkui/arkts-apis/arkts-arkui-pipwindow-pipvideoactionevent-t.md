# PiPVideoActionEvent

```TypeScript
type PiPVideoActionEvent = 'playbackStateChanged' | 'nextVideo' | 'previousVideo' | 'fastForward' | 'fastBackward'
```

视频播放控制事件类型。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PiPWindow-type PiPVideoActionEvent = 'playbackStateChanged' | 'nextVideo' | 'previousVideo' | 'fastForward' | 'fastBackward'--><!--Device-PiPWindow-type PiPVideoActionEvent = 'playbackStateChanged' | 'nextVideo' | 'previousVideo' | 'fastForward' | 'fastBackward'-End-->

**系统能力：** SystemCapability.Window.SessionManager

| 类型 | 说明 |
| --- | --- |
| 'playbackStateChanged' | 播放状态发生了变化。 |
| 'nextVideo' | 播放下一个视频。 |
| 'previousVideo' | 播放上一个视频。 |
| 'fastForward' | 视频进度快进。从API version 12 开始支持。 [since 12] |
| 'fastBackward' | 视频进度后退。从API version 12 开始支持。 [since 12] |

