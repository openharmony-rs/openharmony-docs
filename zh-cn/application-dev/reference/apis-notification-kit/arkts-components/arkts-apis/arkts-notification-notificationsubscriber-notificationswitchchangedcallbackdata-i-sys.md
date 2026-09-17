# NotificationSwitchChangedCallbackData（系统接口）

通知开关状态变化的回调函数类型。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## enableStatus

```TypeScript
readonly enableStatus: notificationManager.SwitchState
```

通知开关状态。

**类型：** [notificationManager.SwitchState](arkts-notification-notificationmanager-switchstate-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

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

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
readonly userId: number
```

用户ID。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。
