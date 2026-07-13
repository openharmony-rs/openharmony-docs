# NotificationSystemLiveViewContent

描述系统实况窗通知内容。不支持三方应用直接创建该类型通知，可以由系统代理创建系统实况窗类型通知后，三方应用发布同ID的通知来更新指定内容。继承自
[NotificationBasicContent](arkts-notification-notificationbasiccontent-i.md)。

**继承/实现关系：** NotificationSystemLiveViewContent extends [NotificationBasicContent](arkts-notification-notificationbasiccontent-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## button

```TypeScript
button?: NotificationButton
```

实况通知的按钮。默认为空。

**类型：** NotificationButton

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## capsule

```TypeScript
capsule?: NotificationCapsule
```

实况通知的胶囊。默认为空。

**类型：** NotificationCapsule

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## progress

```TypeScript
progress?: NotificationProgress
```

实况内容的进度。默认为空。

**类型：** NotificationProgress

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## time

```TypeScript
time?: NotificationTime
```

实况通知的时间。默认为空。

**类型：** NotificationTime

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## typeCode

```TypeScript
typeCode: number
```

类型标识符，标记调用方业务类型。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

