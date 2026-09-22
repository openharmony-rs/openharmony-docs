# NotificationSystemLiveViewContent

```TypeScript
export interface NotificationSystemLiveViewContent extends NotificationBasicContent
```

Describes the system live view notification content, which is used to display real-time status information in the live view. Third-party applications are not supported to directly create this notification type. After the system proxy creates a system live view notification, a third-party application can publish a notification with the same ID to update the specified content. This API is inherited from NotificationBasicContent.

> **NOTE:** 
> 
> The actual display effect depends on the device capabilities and the notification center UI style.

**Inheritance/Implementation:** NotificationSystemLiveViewContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## button

```TypeScript
button?: NotificationButton
```

Button of the notification. This parameter is left empty by default.

**Type:** [NotificationButton](arkts-notification-notificationcontent-notificationbutton-i.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## capsule

```TypeScript
capsule?: NotificationCapsule
```

Capsule of the notification. This parameter is left empty by default.

**Type:** [NotificationCapsule](arkts-notification-notificationcontent-notificationcapsule-i.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## progress

```TypeScript
progress?: NotificationProgress
```

Progress of the notification. This parameter is left empty by default.

**Type:** [NotificationProgress](arkts-notification-notificationcontent-notificationprogress-i.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## time

```TypeScript
time?: NotificationTime
```

Time of the notification. This parameter is left empty by default.

**Type:** [NotificationTime](arkts-notification-notificationcontent-notificationtime-i.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## typeCode

```TypeScript
typeCode: number
```

Type identifier for marking the caller's service type, which is used to distinguish different live view service scenarios.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Notification.Notification
