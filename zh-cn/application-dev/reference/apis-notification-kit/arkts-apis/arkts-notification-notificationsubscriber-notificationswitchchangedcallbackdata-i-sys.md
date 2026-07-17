# NotificationSwitchChangedCallbackData（系统接口）

通知开关状态变化的回调函数类型。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface NotificationSwitchChangedCallbackData--><!--Device-unnamed-export interface NotificationSwitchChangedCallbackData-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## enableStatus

```TypeScript
readonly enableStatus: notificationManager.SwitchState
```

通知开关状态。

**类型：** notificationManager.SwitchState

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSwitchChangedCallbackData-readonly enableStatus: notificationManager.SwitchState--><!--Device-NotificationSwitchChangedCallbackData-readonly enableStatus: notificationManager.SwitchState-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## switchName

```TypeScript
readonly switchName: string
```

通知开关名称。取值为：DEAL（交易类通知聚合开关）、LOGISTICS（物流类通知聚合开关）。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSwitchChangedCallbackData-readonly switchName: string--><!--Device-NotificationSwitchChangedCallbackData-readonly switchName: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
readonly userId: number
```

用户ID。取值为所有整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSwitchChangedCallbackData-readonly userId: int--><!--Device-NotificationSwitchChangedCallbackData-readonly userId: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

