# BadgeEnabledChangedCallback

注册应用角标使能状态变化的回调函数类型。type BadgeEnabledChangedCallback = (data: EnabledNotificationCallbackData) => void

**起始版本：** 12

<!--Device-unnamed-export interface BadgeEnabledChangedCallback--><!--Device-unnamed-export interface BadgeEnabledChangedCallback-End-->

**系统能力：** SystemCapability.Notification.Notification

<a id="constructor"></a>
## constructor

```TypeScript
(data: EnabledNotificationCallbackData): void
```

回调返回监听到的角标使能状态信息。

**起始版本：** 12

<!--Device-BadgeEnabledChangedCallback-(data: EnabledNotificationCallbackData): void--><!--Device-BadgeEnabledChangedCallback-(data: EnabledNotificationCallbackData): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [EnabledNotificationCallbackData](arkts-notification-notificationsubscriber-enablednotificationcallbackdata-i-sys.md) | 是 |  |

