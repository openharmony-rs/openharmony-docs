# PiPLiveActionEvent

```TypeScript
type PiPLiveActionEvent = 'playbackStateChanged' | 'voiceStateChanged'
```

直播控制事件类型。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PiPWindow-type PiPLiveActionEvent = 'playbackStateChanged' | 'voiceStateChanged'--><!--Device-PiPWindow-type PiPLiveActionEvent = 'playbackStateChanged' | 'voiceStateChanged'-End-->

**系统能力：** SystemCapability.Window.SessionManager

| 类型 | 说明 |
| --- | --- |
| 'playbackStateChanged' | 播放或暂停直播。 |
| 'voiceStateChanged' | 静音或解除静音。 [since 12] |

