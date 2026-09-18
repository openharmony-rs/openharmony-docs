# NotificationSorting (System API)

The **NotificationSorting** module provides APIs for defining the sorting information of active notifications.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## hashCode

```TypeScript
readonly hashCode: string
```

Unique ID of the notification.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## ranking

```TypeScript
readonly ranking: number
```

Notification level. If this parameter is not set, the default value is used based on the notification slot type.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## slot

```TypeScript
readonly slot: NotificationSlot
```

Notification slot type.

**Type:** [NotificationSlot](arkts-notification-notificationslot-notificationslot-i.md)

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
