# SlotLevel

Enumerates the notification level.

This API is used to define the notification reminder behavior level of NotificationSlot, affecting how the notification is displayed in the status bar, whether to show banners and alert sounds, etc.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

## LEVEL_NONE

```TypeScript
LEVEL_NONE = 0
```

Notification is disabled.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

## LEVEL_MIN

```TypeScript
LEVEL_MIN = 1
```

Notification is enabled, but the notification icon is not displayed in the status bar, with no alert tone and banner.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

## LEVEL_LOW

```TypeScript
LEVEL_LOW = 2
```

Notification is enabled, and the notification icon is displayed in the status bar, with no alert tone and banner.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

## LEVEL_DEFAULT

```TypeScript
LEVEL_DEFAULT = 3
```

Notification is enabled, and the notification icon is displayed in the status bar, with an alert tone but no banner.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

## LEVEL_HIGH

```TypeScript
LEVEL_HIGH = 4
```

Notification is enabled, and the notification icon is displayed in the status bar, with an alert tone and banner.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification
