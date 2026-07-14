# EnabledPriorityNotificationByBundleCallbackData（系统接口）

应用通知优先级开关状态

**起始版本：** 23

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## bundle

```TypeScript
readonly bundle: string
```

应用的包名。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## enableStatus

```TypeScript
readonly enableStatus: notificationManager.PriorityEnableStatus
```

应用通知的优先使能状态。
- DISABLE：不允许设置为优先通知。
- ENABLE_BY_INTELLIGENT：允许经智能识别、用户关键词匹配、应用规则匹配等方式设置为优先通知。
- ENABLE：应用通知均设置为优先通知。

**类型：** notificationManager.PriorityEnableStatus

**起始版本：** 23

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
readonly uid: number
```

应用的uid。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

