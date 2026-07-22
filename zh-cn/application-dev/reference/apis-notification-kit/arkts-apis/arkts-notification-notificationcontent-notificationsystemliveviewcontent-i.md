# NotificationSystemLiveViewContent

描述系统实况窗通知内容，用于在实况窗中展示实时状态信息。不支持三方应用直接创建该类型通知，可以由系统代理创建系统实况窗类型通知后，三方应用发布同ID的通知来更新指定内容。继承自[NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)。
> **说明：**  
>  
> 实际显示效果依赖于设备能力和通知中心UI样式。

**继承/实现关系：** NotificationSystemLiveViewContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**起始版本：** 11

<!--Device-unnamed-export interface NotificationSystemLiveViewContent extends NotificationBasicContent--><!--Device-unnamed-export interface NotificationSystemLiveViewContent extends NotificationBasicContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## button

```TypeScript
button?: NotificationButton
```

实况通知的按钮。默认为空。

**类型：** NotificationButton

**起始版本：** 11

<!--Device-NotificationSystemLiveViewContent-button?: NotificationButton--><!--Device-NotificationSystemLiveViewContent-button?: NotificationButton-End-->

**系统能力：** SystemCapability.Notification.Notification

## capsule

```TypeScript
capsule?: NotificationCapsule
```

实况通知的胶囊。默认为空。

**类型：** NotificationCapsule

**起始版本：** 11

<!--Device-NotificationSystemLiveViewContent-capsule?: NotificationCapsule--><!--Device-NotificationSystemLiveViewContent-capsule?: NotificationCapsule-End-->

**系统能力：** SystemCapability.Notification.Notification

## progress

```TypeScript
progress?: NotificationProgress
```

实况内容的进度。默认为空。

**类型：** NotificationProgress

**起始版本：** 11

<!--Device-NotificationSystemLiveViewContent-progress?: NotificationProgress--><!--Device-NotificationSystemLiveViewContent-progress?: NotificationProgress-End-->

**系统能力：** SystemCapability.Notification.Notification

## time

```TypeScript
time?: NotificationTime
```

实况通知的时间。默认为空。

**类型：** NotificationTime

**起始版本：** 11

<!--Device-NotificationSystemLiveViewContent-time?: NotificationTime--><!--Device-NotificationSystemLiveViewContent-time?: NotificationTime-End-->

**系统能力：** SystemCapability.Notification.Notification

## typeCode

```TypeScript
typeCode: number
```

类型标识符，标记调用方业务类型，用于区分不同实况窗业务场景。

**类型：** number

**起始版本：** 11

<!--Device-NotificationSystemLiveViewContent-typeCode: int--><!--Device-NotificationSystemLiveViewContent-typeCode: int-End-->

**系统能力：** SystemCapability.Notification.Notification

