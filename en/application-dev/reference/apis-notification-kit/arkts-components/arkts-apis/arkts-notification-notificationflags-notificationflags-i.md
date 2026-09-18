# NotificationFlags

Defines the notification flags.

**Since:** 8

**System capability:** SystemCapability.Notification.Notification

## bannerEnabled

```TypeScript
bannerEnabled?: NotificationFlagStatus
```

Settings of banner for the notification. The default value is **TYPE_NONE**. Only TYPE_CLOSE takes effect.

**Type:** [NotificationFlagStatus](arkts-notification-notificationflags-notificationflagstatus-e.md)

**Since:** 23

**System capability:** SystemCapability.Notification.Notification

## lockScreenEnabled

```TypeScript
lockScreenEnabled?: NotificationFlagStatus
```

Settings of screen lock for the notification. The default value is **TYPE_NONE**. Only TYPE_CLOSE takes effect.

**Type:** [NotificationFlagStatus](arkts-notification-notificationflags-notificationflagstatus-e.md)

**Since:** 23

**System capability:** SystemCapability.Notification.Notification

## soundEnabled

```TypeScript
soundEnabled?: NotificationFlagStatus
```

Settings of sound for the notification. The default value is **TYPE_NONE**. This parameter becomes writable starting from API version 23. Only TYPE_CLOSE takes effect.

@readonly [since 8 - 22]

**Type:** [NotificationFlagStatus](arkts-notification-notificationflags-notificationflagstatus-e.md)

**Since:** 8

**System capability:** SystemCapability.Notification.Notification

## vibrationEnabled

```TypeScript
vibrationEnabled?: NotificationFlagStatus
```

Settings of vibration for the notification. The default value is **TYPE_NONE**. This parameter becomes writable starting from API version 23. Only TYPE_CLOSE takes effect.

@readonly [since 8 - 22]

**Type:** [NotificationFlagStatus](arkts-notification-notificationflags-notificationflagstatus-e.md)

**Since:** 8

**System capability:** SystemCapability.Notification.Notification
