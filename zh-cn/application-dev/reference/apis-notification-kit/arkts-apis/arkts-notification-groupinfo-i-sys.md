# GroupInfo（系统接口）

组通知信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## groupTitle

```TypeScript
groupTitle?: string
```

通知成组后展示的组标题。当该通知是通知组中最新的一条通知时，该字段生效。默认为空。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## isGroupIcon

```TypeScript
isGroupIcon?: boolean
```

是否使用该通知[NotificationRequest](arkts-notification-notificationrequest-i.md)中的smallIcon字段作为通知成组后
展示的组图标。当该通知是通知组中最新的一条通知，且开发者传入smallIcon时，是否使用smallIcon作为组图标。默认值为false。

- true：使用smallIcon作为组通知的图标。
- false：不使用smallIcon作为组通知的图标。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

