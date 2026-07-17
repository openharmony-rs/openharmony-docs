# NotificationFlags

描述通知标志位。

**起始版本：** 8

<!--Device-unnamed-export interface NotificationFlags--><!--Device-unnamed-export interface NotificationFlags-End-->

**系统能力：** SystemCapability.Notification.Notification

## bannerEnabled

```TypeScript
bannerEnabled?: NotificationFlagStatus
```

是否启用横幅功能。默认值为TYPE_NONE。设置时仅[TYPE_CLOSE](arkts-notification-notificationflags-notificationflagstatus-e-sys.md)会生效。

**类型：** NotificationFlagStatus

**起始版本：** 23

<!--Device-NotificationFlags-bannerEnabled?: NotificationFlagStatus--><!--Device-NotificationFlags-bannerEnabled?: NotificationFlagStatus-End-->

**系统能力：** SystemCapability.Notification.Notification

## lockScreenEnabled

```TypeScript
lockScreenEnabled?: NotificationFlagStatus
```

是否启用锁屏功能。默认值为TYPE_NONE。设置时仅[TYPE_CLOSE](arkts-notification-notificationflags-notificationflagstatus-e-sys.md)会生效。

**类型：** NotificationFlagStatus

**起始版本：** 23

<!--Device-NotificationFlags-lockScreenEnabled?: NotificationFlagStatus--><!--Device-NotificationFlags-lockScreenEnabled?: NotificationFlagStatus-End-->

**系统能力：** SystemCapability.Notification.Notification

## soundEnabled

```TypeScript
soundEnabled?: NotificationFlagStatus
```

是否启用声音提示功能。默认值为TYPE_NONE。从API version 23开始成为可写参数，设置时仅[TYPE_CLOSE](arkts-notification-notificationflags-notificationflagstatus-e-sys.md)会生效。

**类型：** NotificationFlagStatus

**起始版本：** 8

<!--Device-NotificationFlags-soundEnabled?: NotificationFlagStatus--><!--Device-NotificationFlags-soundEnabled?: NotificationFlagStatus-End-->

**系统能力：** SystemCapability.Notification.Notification

## vibrationEnabled

```TypeScript
vibrationEnabled?: NotificationFlagStatus
```

是否启用振动提醒功能。默认值为TYPE_NONE。从API version 23开始成为可写参数，设置时仅[TYPE_CLOSE](arkts-notification-notificationflags-notificationflagstatus-e-sys.md)会生效。

**类型：** NotificationFlagStatus

**起始版本：** 8

<!--Device-NotificationFlags-vibrationEnabled?: NotificationFlagStatus--><!--Device-NotificationFlags-vibrationEnabled?: NotificationFlagStatus-End-->

**系统能力：** SystemCapability.Notification.Notification

