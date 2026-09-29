# NotificationInfo

```TypeScript
export interface NotificationInfo
```

The **NotificationInfo** module describes the notification information delivered to the onReceiveMessage callback of ExtensionAbility for notification subscriptions.

**Since:** 22

<!--Device-unnamed-export interface NotificationInfo--><!--Device-unnamed-export interface NotificationInfo-End-->

**System capability:** SystemCapability.Notification.Notification

## appIndex

```TypeScript
readonly appIndex: number
```

Index of the application clone that creates the notification. It takes effect only for application clones.

**Type:** number

**Since:** 22

<!--Device-NotificationInfo-readonly appIndex: int--><!--Device-NotificationInfo-readonly appIndex: int-End-->

**System capability:** SystemCapability.Notification.Notification

## appName

```TypeScript
readonly appName?: string
```

Name of the application that creates the notification.

**Type:** string

**Since:** 22

<!--Device-NotificationInfo-readonly appName?: string--><!--Device-NotificationInfo-readonly appName?: string-End-->

**System capability:** SystemCapability.Notification.Notification

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name of the application that creates the notification.

**Type:** string

**Since:** 22

<!--Device-NotificationInfo-readonly bundleName: string--><!--Device-NotificationInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.Notification.Notification

## content

```TypeScript
readonly content: NotificationExtensionContent
```

Notification content, which includes the title and body of the notification.

**Type:** [NotificationExtensionContent](arkts-notification-notificationextensioncontent-i.md)

**Since:** 22

<!--Device-NotificationInfo-readonly content: NotificationExtensionContent--><!--Device-NotificationInfo-readonly content: NotificationExtensionContent-End-->

**System capability:** SystemCapability.Notification.Notification

## deliveryTime

```TypeScript
readonly deliveryTime?: number
```

Timestamp when the notification is published. Data format: timestamp. Unit: millisecond.

**Type:** number

**Since:** 22

<!--Device-NotificationInfo-readonly deliveryTime?: long--><!--Device-NotificationInfo-readonly deliveryTime?: long-End-->

**System capability:** SystemCapability.Notification.Notification

## groupName

```TypeScript
readonly groupName?: string
```

Name of the notification group.

**Type:** string

**Since:** 22

<!--Device-NotificationInfo-readonly groupName?: string--><!--Device-NotificationInfo-readonly groupName?: string-End-->

**System capability:** SystemCapability.Notification.Notification

## hashCode

```TypeScript
readonly hashCode: string
```

Unique identifier of the notification.

**Type:** string

**Since:** 22

<!--Device-NotificationInfo-readonly hashCode: string--><!--Device-NotificationInfo-readonly hashCode: string-End-->

**System capability:** SystemCapability.Notification.Notification

## notificationSlotType

```TypeScript
readonly notificationSlotType: notificationManager.SlotType
```

Notification slot type, which identifies the slot category of the notification (such as social communication and service reminder). Different slot types correspond to different reminder types.

**Type:** [notificationManager.SlotType](arkts-notification-notificationmanager-slottype-e.md)

**Since:** 22

<!--Device-NotificationInfo-readonly notificationSlotType: notificationManager.SlotType--><!--Device-NotificationInfo-readonly notificationSlotType: notificationManager.SlotType-End-->

**System capability:** SystemCapability.Notification.Notification
