# NotificationControlFlagStatus (System API)

Each bit can control the notification mode. When the bitwise OR operation is performed on **notificationControlFlags** and the enumerated values in the following table, the notification mode is disabled.

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## NOTIFICATION_STATUS_CLOSE_SOUND

```TypeScript
NOTIFICATION_STATUS_CLOSE_SOUND = 1 << 0
```

Disables the sound notification function.

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## NOTIFICATION_STATUS_CLOSE_LOCKSCREEN

```TypeScript
NOTIFICATION_STATUS_CLOSE_LOCKSCREEN = 1 << 1
```

Disables the screen lock notification function.

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## NOTIFICATION_STATUS_CLOSE_BANNER

```TypeScript
NOTIFICATION_STATUS_CLOSE_BANNER = 1 << 2
```

Disables the banner notification function.

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## NOTIFICATION_STATUS_CLOSE_LIGHT_SCREEN

```TypeScript
NOTIFICATION_STATUS_CLOSE_LIGHT_SCREEN = 1 << 3
```

Disables the screen-on notification function.

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## NOTIFICATION_STATUS_CLOSE_VIBRATION

```TypeScript
NOTIFICATION_STATUS_CLOSE_VIBRATION = 1 << 4
```

Disables the vibration notification function.

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## NOTIFICATION_STATUS_CLOSE_STATUSBAR_ICON

```TypeScript
NOTIFICATION_STATUS_CLOSE_STATUSBAR_ICON = 1 << 5
```

Disables the icon notification function in the status bar.

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
