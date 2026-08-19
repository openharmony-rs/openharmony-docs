# BadgeEnabledChangedCallback（系统接口）

```TypeScript
export type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) => void
```

type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) => void 注册应用角标使能状态变化的回调函数类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) => void--><!--Device-unnamed-export type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [EnabledNotificationCallbackData](arkts-notification-notificationsubscriber-enablednotificationcallbackdata-i-sys.md) | 是 | 回调返回监听到的角标使能状态信息。 |

