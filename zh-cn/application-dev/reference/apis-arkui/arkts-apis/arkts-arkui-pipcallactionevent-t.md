# PiPCallActionEvent

```TypeScript
type PiPCallActionEvent = 'hangUp' | 'micStateChanged' | 'videoStateChanged' | 'voiceStateChanged'
```

视频通话控制事件类型。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

| 类型 | 说明 |
| --- | --- |
| 'hangUp' | 挂断视频通话。 |
| 'micStateChanged' | 打开或关闭麦克风。 |
| 'videoStateChanged' | 打开或关闭摄像头。 |
| 'voiceStateChanged' | 静音或解除静音。 [since 12] |

