# EnabledSilentReminderChangedCallback（系统接口）

```TypeScript
export type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) => void
```

注册应用通知静默提醒使能状态变化的回调函数类型。type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) => void

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) => void--><!--Device-unnamed-export type EnabledSilentReminderChangedCallback = (callbackData: EnabledSilentReminderCallbackData) => void-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackData | EnabledSilentReminderCallbackData | 是 | 回调返回监听到的静默提醒使能状态信息。 |

