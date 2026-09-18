# SlotType

Enumerates the notification slot types.

Different types correspond to different [SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md) values, determining the reminder behavior of the notification.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

## UNKNOWN_TYPE

```TypeScript
UNKNOWN_TYPE = 0
```

Unknown type. This type corresponds to the [SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md) of **LEVEL_MIN**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.Notification

## SOCIAL_COMMUNICATION

```TypeScript
SOCIAL_COMMUNICATION = 1
```

Social communication. This type corresponds to the [SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md) of **LEVEL_HIGH**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.Notification

## SERVICE_INFORMATION

```TypeScript
SERVICE_INFORMATION = 2
```

Service information. This type corresponds to the [SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md) of **LEVEL_HIGH**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.Notification

## CONTENT_INFORMATION

```TypeScript
CONTENT_INFORMATION = 3
```

Content information. This type corresponds to the [SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md) of **LEVEL_MIN**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.Notification

## LIVE_VIEW

```TypeScript
LIVE_VIEW = 4
```

Live view. A third-party application cannot directly create a notification of this type. Instead, after the system proxy creates a notification, the third-party application can release the notification with the same ID to update the specified content. This type corresponds to the [SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md) of **LEVEL_DEFAULT**.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.Notification

## CUSTOMER_SERVICE

```TypeScript
CUSTOMER_SERVICE = 5
```

Customer service message. This type is used for messages between users and customer service providers. The messages must be initiated by users. This type corresponds to the [SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md) of **LEVEL_DEFAULT**.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.Notification

## OTHER_TYPES

```TypeScript
OTHER_TYPES = 0xFFFF
```

Other types. This type corresponds to the [SlotLevel](arkts-notification-notificationmanager-slotlevel-e.md) of **LEVEL_MIN**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.Notification
