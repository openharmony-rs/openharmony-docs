# Support

系统公共事件是指由系统服务或系统应用发布的事件，订阅这些系统公共事件需要特定的权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [Support](arkts-basicservices-support-e.md)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BOOT_COMPLETED

```TypeScript
COMMON_EVENT_BOOT_COMPLETED = 'usual.event.BOOT_COMPLETED'
```

提示用户已完成引导并加载系统。

要订阅此事件，您的应用必须具备ohos.permission.RECEIVER_STARTUP_COMPLETED权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BOOT_COMPLETED](arkts-basicservices-support-e.md#common_event_boot_completed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCKED_BOOT_COMPLETED

```TypeScript
COMMON_EVENT_LOCKED_BOOT_COMPLETED = 'usual.event.LOCKED_BOOT_COMPLETED'
```

（预留事件，暂未支持）提示用户已完成引导，系统已加载，但屏幕仍锁定。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_LOCKED_BOOT_COMPLETED](arkts-basicservices-support-e.md#common_event_locked_boot_completed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SHUTDOWN

```TypeScript
COMMON_EVENT_SHUTDOWN = 'usual.event.SHUTDOWN'
```

提示设备正在关闭并将继续直至最终关闭。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_SHUTDOWN](arkts-basicservices-support-e.md#common_event_shutdown)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_CHANGED

```TypeScript
COMMON_EVENT_BATTERY_CHANGED = 'usual.event.BATTERY_CHANGED'
```

提示电池充电状态、电量和其他信息发生变化。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BATTERY_CHANGED](arkts-basicservices-support-e.md#common_event_battery_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_LOW

```TypeScript
COMMON_EVENT_BATTERY_LOW = 'usual.event.BATTERY_LOW'
```

提示电池电量低。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BATTERY_LOW](arkts-basicservices-support-e.md#common_event_battery_low)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_OKAY

```TypeScript
COMMON_EVENT_BATTERY_OKAY = 'usual.event.BATTERY_OKAY'
```

提示电池退出低电量状态。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BATTERY_OKAY](arkts-basicservices-support-e.md#common_event_battery_okay)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_CONNECTED

```TypeScript
COMMON_EVENT_POWER_CONNECTED = 'usual.event.POWER_CONNECTED'
```

提示设备连接到外部电源。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_POWER_CONNECTED](arkts-basicservices-support-e.md#common_event_power_connected)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_DISCONNECTED

```TypeScript
COMMON_EVENT_POWER_DISCONNECTED = 'usual.event.POWER_DISCONNECTED'
```

提示设备与外部电源断开。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_POWER_DISCONNECTED](arkts-basicservices-support-e.md#common_event_power_disconnected)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_OFF

```TypeScript
COMMON_EVENT_SCREEN_OFF = 'usual.event.SCREEN_OFF'
```

提示设备屏幕关闭且设备处于睡眠状态。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_SCREEN_OFF](arkts-basicservices-support-e.md#common_event_screen_off)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_ON

```TypeScript
COMMON_EVENT_SCREEN_ON = 'usual.event.SCREEN_ON'
```

提示设备屏幕打开且设备处于交互状态。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_SCREEN_ON](arkts-basicservices-support-e.md#common_event_screen_on)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_THERMAL_LEVEL_CHANGED

```TypeScript
COMMON_EVENT_THERMAL_LEVEL_CHANGED = 'usual.event.THERMAL_LEVEL_CHANGED'
```

提示设备热状态（温度等级）发生变化。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_THERMAL_LEVEL_CHANGED](arkts-basicservices-support-e.md#common_event_thermal_level_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_PRESENT

```TypeScript
COMMON_EVENT_USER_PRESENT = 'usual.event.USER_PRESENT'
```

（预留事件，暂未支持）提示用户解锁了设备。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USER_PRESENT](arkts-basicservices-support-e.md#common_event_user_present)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIME_TICK

```TypeScript
COMMON_EVENT_TIME_TICK = 'usual.event.TIME_TICK'
```

提示系统时间发生更改（指时间正常流逝）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_TIME_TICK](arkts-basicservices-support-e.md#common_event_time_tick)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIME_CHANGED

```TypeScript
COMMON_EVENT_TIME_CHANGED = 'usual.event.TIME_CHANGED'
```

提示系统时间被重新设置。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_TIME_CHANGED](arkts-basicservices-support-e.md#common_event_time_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DATE_CHANGED

```TypeScript
COMMON_EVENT_DATE_CHANGED = 'usual.event.DATE_CHANGED'
```

（预留事件，暂未支持）提示系统日期已更改。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DATE_CHANGED](arkts-basicservices-support-e.md#common_event_date_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIMEZONE_CHANGED

```TypeScript
COMMON_EVENT_TIMEZONE_CHANGED = 'usual.event.TIMEZONE_CHANGED'
```

提示系统时区发生变更。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_TIMEZONE_CHANGED](arkts-basicservices-support-e.md#common_event_timezone_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CLOSE_SYSTEM_DIALOGS

```TypeScript
COMMON_EVENT_CLOSE_SYSTEM_DIALOGS = 'usual.event.CLOSE_SYSTEM_DIALOGS'
```

（预留事件，暂未支持）提示用户关闭临时系统对话框。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_CLOSE_SYSTEM_DIALOGS](arkts-basicservices-support-e.md#common_event_close_system_dialogs)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_ADDED

```TypeScript
COMMON_EVENT_PACKAGE_ADDED = 'usual.event.PACKAGE_ADDED'
```

提示设备上已安装新应用程序包。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGE_ADDED](arkts-basicservices-support-e.md#common_event_package_added)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_REPLACED

```TypeScript
COMMON_EVENT_PACKAGE_REPLACED = 'usual.event.PACKAGE_REPLACED'
```

（预留事件，暂未支持）提示设备上已安装的旧版本应用程序已被新版本所替换。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGE_REPLACED](arkts-basicservices-support-e.md#common_event_package_replaced)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_REPLACED

```TypeScript
COMMON_EVENT_MY_PACKAGE_REPLACED = 'usual.event.MY_PACKAGE_REPLACED'
```

（预留事件，暂未支持）提示应用程序包的新版本已取代前一个版本。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_MY_PACKAGE_REPLACED](arkts-basicservices-support-e.md#common_event_my_package_replaced)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_REMOVED

```TypeScript
COMMON_EVENT_PACKAGE_REMOVED = 'usual.event.PACKAGE_REMOVED'
```

提示已安装的应用程序已从设备卸载，但应用程序数据得到保留的。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGE_REMOVED](arkts-basicservices-support-e.md#common_event_package_removed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BUNDLE_REMOVED

```TypeScript
COMMON_EVENT_BUNDLE_REMOVED = 'usual.event.BUNDLE_REMOVED'
```

（预留事件，暂未支持）提示已从设备中卸载已安装应用程序的附加包，但应用程序数据得到保留。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BUNDLE_REMOVED](arkts-basicservices-support-e.md#common_event_bundle_removed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_FULLY_REMOVED

```TypeScript
COMMON_EVENT_PACKAGE_FULLY_REMOVED = 'usual.event.PACKAGE_FULLY_REMOVED'
```

（预留事件，暂未支持）提示已从设备中完全卸载已安装的应用程序（包括应用程序数据和代码）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGE_FULLY_REMOVED](arkts-basicservices-support-e.md#common_event_package_fully_removed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_CHANGED

```TypeScript
COMMON_EVENT_PACKAGE_CHANGED = 'usual.event.PACKAGE_CHANGED'
```

提示应用程序包已发生更改（例如，包中的组件已启用或禁用）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGE_CHANGED](arkts-basicservices-support-e.md#common_event_package_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_RESTARTED

```TypeScript
COMMON_EVENT_PACKAGE_RESTARTED = 'usual.event.PACKAGE_RESTARTED'
```

提示用户终止了应用程序的所有进程并重启应用程序。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGE_RESTARTED](arkts-basicservices-support-e.md#common_event_package_restarted)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_DATA_CLEARED

```TypeScript
COMMON_EVENT_PACKAGE_DATA_CLEARED = 'usual.event.PACKAGE_DATA_CLEARED'
```

提示用户清除了应用包数据。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGE_DATA_CLEARED](arkts-basicservices-support-e.md#common_event_package_data_cleared)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGES_SUSPENDED

```TypeScript
COMMON_EVENT_PACKAGES_SUSPENDED = 'usual.event.PACKAGES_SUSPENDED'
```

（预留事件，暂未支持）提示应用程序已挂起。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGES_SUSPENDED](arkts-basicservices-support-e.md#common_event_packages_suspended)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGES_UNSUSPENDED

```TypeScript
COMMON_EVENT_PACKAGES_UNSUSPENDED = 'usual.event.PACKAGES_UNSUSPENDED'
```

（预留事件，暂未支持）提示应用HAP包未挂起（从挂起状态恢复）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGES_UNSUSPENDED](arkts-basicservices-support-e.md#common_event_packages_unsuspended)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_SUSPENDED

```TypeScript
COMMON_EVENT_MY_PACKAGE_SUSPENDED = 'usual.event.MY_PACKAGE_SUSPENDED'
```

提示应用HAP包被挂起的。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_MY_PACKAGE_SUSPENDED](arkts-basicservices-support-e.md#common_event_my_package_suspended)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_UNSUSPENDED

```TypeScript
COMMON_EVENT_MY_PACKAGE_UNSUSPENDED = 'usual.event.MY_PACKAGE_UNSUSPENDED'
```

提示应用包未挂起。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_MY_PACKAGE_UNSUSPENDED](arkts-basicservices-support-e.md#common_event_my_package_unsuspended)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_UID_REMOVED

```TypeScript
COMMON_EVENT_UID_REMOVED = 'usual.event.UID_REMOVED'
```

（预留事件，暂未支持）提示用户ID已从系统中删除。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_UID_REMOVED](arkts-basicservices-support-e.md#common_event_uid_removed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_FIRST_LAUNCH

```TypeScript
COMMON_EVENT_PACKAGE_FIRST_LAUNCH = 'usual.event.PACKAGE_FIRST_LAUNCH'
```

（预留事件，暂未支持）提示首次启动已安装的应用程序。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGE_FIRST_LAUNCH](arkts-basicservices-support-e.md#common_event_package_first_launch)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION

```TypeScript
COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION = 'usual.event.PACKAGE_NEEDS_VERIFICATION'
```

（预留事件，暂未支持）提示应用需要系统校验。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION](arkts-basicservices-support-e.md#common_event_package_needs_verification)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_VERIFIED

```TypeScript
COMMON_EVENT_PACKAGE_VERIFIED = 'usual.event.PACKAGE_VERIFIED'
```

（预留事件，暂未支持）提示应用已被系统校验。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_PACKAGE_VERIFIED](arkts-basicservices-support-e.md#common_event_package_verified)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE

```TypeScript
COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_AVAILABLE'
```

（预留事件，暂未支持）提示安装在外部存储上的应用程序对系统可用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE](arkts-basicservices-support-e.md#common_event_external_applications_available)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE

```TypeScript
COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE'
```

（预留事件，暂未支持）提示安装在外部存储上的应用程序对系统不可用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CONFIGURATION_CHANGED

```TypeScript
COMMON_EVENT_CONFIGURATION_CHANGED = 'usual.event.CONFIGURATION_CHANGED'
```

（预留事件，暂未支持）提示设备状态（例如，方向、区域设置等）已更改。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_CONFIGURATION_CHANGED](arkts-basicservices-support-e.md#common_event_configuration_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCALE_CHANGED

```TypeScript
COMMON_EVENT_LOCALE_CHANGED = 'usual.event.LOCALE_CHANGED'
```

（预留事件，暂未支持）提示设备区域设置已更改。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_LOCALE_CHANGED](arkts-basicservices-support-e.md#common_event_locale_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MANAGE_PACKAGE_STORAGE

```TypeScript
COMMON_EVENT_MANAGE_PACKAGE_STORAGE = 'usual.event.MANAGE_PACKAGE_STORAGE'
```

（预留事件，暂未支持）提示设备存储空间不足。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_MANAGE_PACKAGE_STORAGE](arkts-basicservices-support-e.md#common_event_manage_package_storage)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DRIVE_MODE

```TypeScript
COMMON_EVENT_DRIVE_MODE = 'common.event.DRIVE_MODE'
```

（预留事件，暂未支持）提示系统处于驾驶模式。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DRIVE_MODE](arkts-basicservices-support-e.md#common_event_drive_mode)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HOME_MODE

```TypeScript
COMMON_EVENT_HOME_MODE = 'common.event.HOME_MODE'
```

（预留事件，暂未支持）提示系统处于HOME模式。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_HOME_MODE](arkts-basicservices-support-e.md#common_event_home_mode)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_OFFICE_MODE

```TypeScript
COMMON_EVENT_OFFICE_MODE = 'common.event.OFFICE_MODE'
```

（预留事件，暂未支持）提示系统处于办公模式。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_OFFICE_MODE](arkts-basicservices-support-e.md#common_event_office_mode)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STARTED

```TypeScript
COMMON_EVENT_USER_STARTED = 'usual.event.USER_STARTED'
```

（预留事件，暂未支持）提示用户已启动。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USER_STARTED](arkts-basicservices-support-e.md#common_event_user_started)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_BACKGROUND

```TypeScript
COMMON_EVENT_USER_BACKGROUND = 'usual.event.USER_BACKGROUND'
```

（预留事件，暂未支持）提示用户已被带到后台。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USER_BACKGROUND](arkts-basicservices-support-e.md#common_event_user_background)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_FOREGROUND

```TypeScript
COMMON_EVENT_USER_FOREGROUND = 'usual.event.USER_FOREGROUND'
```

（预留事件，暂未支持）提示用户已被带到前台。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USER_FOREGROUND](arkts-basicservices-support-e.md#common_event_user_foreground)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_SWITCHED

```TypeScript
COMMON_EVENT_USER_SWITCHED = 'usual.event.USER_SWITCHED'
```

提示用户正在切换。

要订阅此事件，您的应用必须具备ohos.permission.MANAGE_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USER_SWITCHED](arkts-basicservices-support-e.md#common_event_user_switched)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STARTING

```TypeScript
COMMON_EVENT_USER_STARTING = 'usual.event.USER_STARTING'
```

（预留事件，暂未支持）提示用户正在启动。

要订阅此事件，您的应用必须具备ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USER_STARTING](arkts-basicservices-support-e.md#common_event_user_starting)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_UNLOCKED

```TypeScript
COMMON_EVENT_USER_UNLOCKED = 'usual.event.USER_UNLOCKED'
```

（预留事件，暂未支持）在重启后解锁时，提示当前用户的凭据加密存储已解锁。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USER_UNLOCKED](arkts-basicservices-support-e.md#common_event_user_unlocked)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STOPPING

```TypeScript
COMMON_EVENT_USER_STOPPING = 'usual.event.USER_STOPPING'
```

（预留事件，暂未支持）提示要停止用户。

要订阅此事件，您的应用必须具备ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USER_STOPPING](arkts-basicservices-support-e.md#common_event_user_stopping)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STOPPED

```TypeScript
COMMON_EVENT_USER_STOPPED = 'usual.event.USER_STOPPED'
```

（预留事件，暂未支持）提示用户已停止。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USER_STOPPED](arkts-basicservices-support-e.md#common_event_user_stopped)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HWID_LOGIN

```TypeScript
COMMON_EVENT_HWID_LOGIN = 'common.event.HWID_LOGIN'
```

表示分布式账号登录成功的动作。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN](arkts-basicservices-support-e.md#common_event_distributed_account_login)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HWID_LOGOUT

```TypeScript
COMMON_EVENT_HWID_LOGOUT = 'common.event.HWID_LOGOUT'
```

表示分布式账号登出成功的动作。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT](arkts-basicservices-support-e.md#common_event_distributed_account_logout)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HWID_TOKEN_INVALID

```TypeScript
COMMON_EVENT_HWID_TOKEN_INVALID = 'common.event.HWID_TOKEN_INVALID'
```

表示分布式账号token令牌无效的动作。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID](arkts-basicservices-support-e.md#common_event_distributed_account_token_invalid)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HWID_LOGOFF

```TypeScript
COMMON_EVENT_HWID_LOGOFF = 'common.event.HWID_LOGOFF'
```

表示分布式账号注销的动作。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF](arkts-basicservices-support-e.md#common_event_distributed_account_logoff)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_POWER_STATE

```TypeScript
COMMON_EVENT_WIFI_POWER_STATE = 'usual.event.wifi.POWER_STATE'
```

提示Wi-Fi功能状态的变更，如启用或禁用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_POWER_STATE](arkts-basicservices-support-e.md#common_event_wifi_power_state)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_SCAN_FINISHED

```TypeScript
COMMON_EVENT_WIFI_SCAN_FINISHED = 'usual.event.wifi.SCAN_FINISHED'
```

提示Wi-Fi接入点已被扫描并证明可用。

要订阅此事件，您的应用必须具备ohos.permission.LOCATION权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_SCAN_FINISHED](arkts-basicservices-support-e.md#common_event_wifi_scan_finished)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_RSSI_VALUE

```TypeScript
COMMON_EVENT_WIFI_RSSI_VALUE = 'usual.event.wifi.RSSI_VALUE'
```

提示Wi-Fi信号强度（RSSI）改变。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_RSSI_VALUE](arkts-basicservices-support-e.md#common_event_wifi_rssi_value)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_CONN_STATE

```TypeScript
COMMON_EVENT_WIFI_CONN_STATE = 'usual.event.wifi.CONN_STATE'
```

提示Wi-Fi连接状态发生改变。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_CONN_STATE](arkts-basicservices-support-e.md#common_event_wifi_conn_state)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_HOTSPOT_STATE

```TypeScript
COMMON_EVENT_WIFI_HOTSPOT_STATE = 'usual.event.wifi.HOTSPOT_STATE'
```

提示Wi-Fi热点功能状态的变更，如启用或禁用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_HOTSPOT_STATE](arkts-basicservices-support-e.md#common_event_wifi_hotspot_state)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_AP_STA_JOIN

```TypeScript
COMMON_EVENT_WIFI_AP_STA_JOIN = 'usual.event.wifi.WIFI_HS_STA_JOIN'
```

提示有客户端加入当前设备Wi-Fi热点。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_AP_STA_JOIN](arkts-basicservices-support-e.md#common_event_wifi_ap_sta_join)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_AP_STA_LEAVE

```TypeScript
COMMON_EVENT_WIFI_AP_STA_LEAVE = 'usual.event.wifi.WIFI_HS_STA_LEAVE'
```

提示客户端已断开与当前设备Wi-Fi热点的连接。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_AP_STA_LEAVE](arkts-basicservices-support-e.md#common_event_wifi_ap_sta_leave)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE

```TypeScript
COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE = 'usual.event.wifi.mplink.STATE_CHANGE'
```

提示MPLink（增强Wi-Fi功能）状态已更改（暂不支持）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE](arkts-basicservices-support-e.md#common_event_wifi_mplink_state_change)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_CONN_STATE

```TypeScript
COMMON_EVENT_WIFI_P2P_CONN_STATE = 'usual.event.wifi.p2p.CONN_STATE_CHANGE'
```

提示Wi-Fi P2P连接状态改变。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO和ohos.permission.LOCATION权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_P2P_CONN_STATE](arkts-basicservices-support-e.md#common_event_wifi_p2p_conn_state)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_STATE_CHANGED = 'usual.event.wifi.p2p.STATE_CHANGE'
```

提示Wi-Fi P2P状态发生变更，如启用和禁用。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_P2P_STATE_CHANGED](arkts-basicservices-support-e.md#common_event_wifi_p2p_state_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED = 'usual.event.wifi.p2p.DEVICES_CHANGE'
```

提示Wi-Fi P2P对等体状态变化。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED](arkts-basicservices-support-e.md#common_event_wifi_p2p_peers_state_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED = 'usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE'
```

提示Wi-Fi P2P发现状态变化。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED](arkts-basicservices-support-e.md#common_event_wifi_p2p_peers_discovery_state_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED = 'usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE'
```

提示Wi-Fi P2P当前设备状态变化。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED](arkts-basicservices-support-e.md#common_event_wifi_p2p_current_device_state_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED = 'usual.event.wifi.p2p.GROUP_STATE_CHANGED'
```

提示Wi-Fi P2P群组信息已更改。

要订阅此事件，您的应用必须具备ohos.permission.GET_WIFI_INFO权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED](arkts-basicservices-support-e.md#common_event_wifi_p2p_group_state_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙免提通信连接状态。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_handsfree_ag_connect_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE'
```

（预留事件，暂未支持）提示连接到具有蓝牙免提功能的设备处于活动状态。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_handsfree_ag_current_device_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙A2DP连接状态已更改。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_handsfree_ag_audio_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙A2DP连接状态。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_a2dpsource_connect_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE'
```

（预留事件，暂未支持）提示使用蓝牙A2DP连接的设备处于活动状态。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_a2dpsource_current_device_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙A2DP播放状态发生改变。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_a2dpsource_playing_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙A2DP的AVRCP连接状态已更改。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_a2dpsource_avrcp_connect_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE = 'usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙A2DP音频编解码状态更改。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_a2dpsource_codec_value_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED = 'usual.event.bluetooth.remotedevice.DISCOVERED'
```

（预留事件，暂未支持）提示发现远程蓝牙设备。

要订阅此事件，您的应用必须具备ohos.permission.LOCATION和ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_discovered)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE'
```

（预留事件，暂未支持）提示远程蓝牙设备的蓝牙类别已更改。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_class_value_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED = 'usual.event.bluetooth.remotedevice.ACL_CONNECTED'
```

（预留事件，暂未支持）提示已与远程蓝牙设备建立低级别（ACL）连接。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_acl_connected)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED = 'usual.event.bluetooth.remotedevice.ACL_DISCONNECTED'
```

（预留事件，暂未支持）提示低级别（ACL）连接已从远程蓝牙设备断开。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_acl_disconnected)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE = 'usual.event.bluetooth.remotedevice.NAME_UPDATE'
```

（预留事件，暂未支持）提示远程蓝牙设备的友好名称首次被检索或自上次检索以来被更改。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_name_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE = 'usual.event.bluetooth.remotedevice.PAIR_STATE'
```

（预留事件，暂未支持）提示远程蓝牙设备连接状态更改。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_pair_state)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE'
```

（预留事件，暂未支持）提示远程蓝牙设备的电池电量首次被检索或自上次检索以来被更改。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_battery_value_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT = 'usual.event.bluetooth.remotedevice.SDP_RESULT'
```

（预留事件，暂未支持）提示远程蓝牙设备SDP状态。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_sdp_result)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE = 'usual.event.bluetooth.remotedevice.UUID_VALUE'
```

（预留事件，暂未支持）提示远程蓝牙设备UUID连接状态。

要订阅此事件，您的应用必须具备ohos.permission.DISCOVER_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_uuid_value)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ = 'usual.event.bluetooth.remotedevice.PAIRING_REQ'
```

（预留事件，暂未支持）提示远程蓝牙设备配对请求。

要订阅此事件，您的应用必须具备ohos.permission.DISCOVER_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_pairing_req)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL = 'usual.event.bluetooth.remotedevice.PAIRING_CANCEL'
```

（预留事件，暂未支持）提示取消蓝牙配对。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_pairing_cancel)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ = 'usual.event.bluetooth.remotedevice.CONNECT_REQ'
```

（预留事件，暂未支持）提示远程蓝牙设备连接请求。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_connect_req)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY = 'usual.event.bluetooth.remotedevice.CONNECT_REPLY'
```

（预留事件，暂未支持）提示远程蓝牙设备连接请求响应。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_connect_reply)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL = 'usual.event.bluetooth.remotedevice.CONNECT_CANCEL'
```

（预留事件，暂未支持）提示取消与远程蓝牙设备的连接。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL](arkts-basicservices-support-e.md#common_event_bluetooth_remotedevice_connect_cancel)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙免提连接状态已更改。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_handsfreeunit_connect_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙免提音频状态已更改。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_handsfreeunit_audio_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT = 'usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT'
```

（预留事件，暂未支持）提示蓝牙免提音频网关状态已更改。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT](arkts-basicservices-support-e.md#common_event_bluetooth_handsfreeunit_ag_common_event)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙免提呼叫状态已更改。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_handsfreeunit_ag_call_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE = 'usual.event.bluetooth.host.STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙适配器状态已更改，例如蓝牙已打开或关闭。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_host_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE = 'usual.event.bluetooth.host.REQ_DISCOVERABLE'
```

（预留事件，暂未支持）提示用户允许扫描蓝牙请求。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE](arkts-basicservices-support-e.md#common_event_bluetooth_host_req_discoverable)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE = 'usual.event.bluetooth.host.REQ_ENABLE'
```

（预留事件，暂未支持）提示用户打开蓝牙请求。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE](arkts-basicservices-support-e.md#common_event_bluetooth_host_req_enable)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE = 'usual.event.bluetooth.host.REQ_DISABLE'
```

（预留事件，暂未支持）提示用户关闭蓝牙请求。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE](arkts-basicservices-support-e.md#common_event_bluetooth_host_req_disable)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE = 'usual.event.bluetooth.host.SCAN_MODE_UPDATE'
```

（预留事件，暂未支持）提示设备蓝牙扫描模式更改。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_host_scan_mode_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED = 'usual.event.bluetooth.host.DISCOVERY_STARTED'
```

（预留事件，暂未支持）提示设备上已启动蓝牙扫描。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED](arkts-basicservices-support-e.md#common_event_bluetooth_host_discovery_started)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED = 'usual.event.bluetooth.host.DISCOVERY_FINISHED'
```

（预留事件，暂未支持）提示设备上蓝牙扫描完成。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED](arkts-basicservices-support-e.md#common_event_bluetooth_host_discovery_finished)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE = 'usual.event.bluetooth.host.NAME_UPDATE'
```

（预留事件，暂未支持）提示设备蓝牙适配器名称已更改。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_host_name_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙A2DP宿的连接状态已更改。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_a2dpsink_connect_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙A2DP宿的播放状态发生改变。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_a2dpsink_playing_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE'
```

（预留事件，暂未支持）提示蓝牙A2DP宿的音频状态已更改。

要订阅此事件，您的应用必须具备ohos.permission.USE_BLUETOOTH权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE](arkts-basicservices-support-e.md#common_event_bluetooth_a2dpsink_audio_state_update)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED

```TypeScript
COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED = 'usual.event.nfc.action.ADAPTER_STATE_CHANGED'
```

（预留事件，暂未支持）提示设备NFC适配器状态已更改。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED](arkts-basicservices-support-e.md#common_event_nfc_action_adapter_state_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED

```TypeScript
COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED = 'usual.event.nfc.action.RF_FIELD_ON_DETECTED'
```

（预留事件，暂未支持）提示检测到NFC设备RF字段处于使能状态。

要订阅此事件，您的应用必须具备ohos.permission.MANAGE_SECURE_SETTINGS权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED](arkts-basicservices-support-e.md#common_event_nfc_action_rf_field_on_detected)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED

```TypeScript
COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED = 'usual.event.nfc.action.RF_FIELD_OFF_DETECTED'
```

（预留事件，暂未支持）提示检测到NFC设备RF字段处于关闭状态。

要订阅此事件，您的应用必须具备ohos.permission.MANAGE_SECURE_SETTINGS权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED](arkts-basicservices-support-e.md#common_event_nfc_action_rf_field_off_detected)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISCHARGING

```TypeScript
COMMON_EVENT_DISCHARGING = 'usual.event.DISCHARGING'
```

提示系统停止为电池充电。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DISCHARGING](arkts-basicservices-support-e.md#common_event_discharging)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CHARGING

```TypeScript
COMMON_EVENT_CHARGING = 'usual.event.CHARGING'
```

提示系统开始为电池充电。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_CHARGING](arkts-basicservices-support-e.md#common_event_charging)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED

```TypeScript
COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED = 'usual.event.DEVICE_IDLE_MODE_CHANGED'
```

（预留事件，暂未支持）提示系统空闲模式已更改。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED](arkts-basicservices-support-e.md#common_event_device_idle_mode_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_SAVE_MODE_CHANGED

```TypeScript
COMMON_EVENT_POWER_SAVE_MODE_CHANGED = 'usual.event.POWER_SAVE_MODE_CHANGED'
```

提示系统节能模式更改。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_POWER_SAVE_MODE_CHANGED](arkts-basicservices-support-e.md#common_event_power_save_mode_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_ADDED

```TypeScript
COMMON_EVENT_USER_ADDED = 'usual.event.USER_ADDED'
```

提示用户已添加到系统中。

要订阅此事件，您的应用必须具备ohos.permission.MANAGE_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USER_ADDED](arkts-basicservices-support-e.md#common_event_user_added)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_REMOVED

```TypeScript
COMMON_EVENT_USER_REMOVED = 'usual.event.USER_REMOVED'
```

提示用户已从系统中删除。

要订阅此事件，您的应用必须具备ohos.permission.MANAGE_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USER_REMOVED](arkts-basicservices-support-e.md#common_event_user_removed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_ADDED

```TypeScript
COMMON_EVENT_ABILITY_ADDED = 'common.event.ABILITY_ADDED'
```

（预留事件，暂未支持）提示有某个能力已被添加。

要订阅此事件，您的应用必须具备ohos.permission.LISTEN_BUNDLE_CHANGE权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_ABILITY_ADDED](arkts-basicservices-support-e.md#common_event_ability_added)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_REMOVED

```TypeScript
COMMON_EVENT_ABILITY_REMOVED = 'common.event.ABILITY_REMOVED'
```

（预留事件，暂未支持）提示已删除某个能力。

要订阅此事件，您的应用必须具备ohos.permission.LISTEN_BUNDLE_CHANGE权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_ABILITY_REMOVED](arkts-basicservices-support-e.md#common_event_ability_removed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_UPDATED

```TypeScript
COMMON_EVENT_ABILITY_UPDATED = 'common.event.ABILITY_UPDATED'
```

（预留事件，暂未支持）提示能力已更新。

要订阅此事件，您的应用必须具备ohos.permission.LISTEN_BUNDLE_CHANGE权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_ABILITY_UPDATED](arkts-basicservices-support-e.md#common_event_ability_updated)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCATION_MODE_STATE_CHANGED

```TypeScript
COMMON_EVENT_LOCATION_MODE_STATE_CHANGED = 'usual.event.location.MODE_STATE_CHANGED'
```

（预留事件，暂未支持）提示系统定位模式已更改。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_LOCATION_MODE_STATE_CHANGED](arkts-basicservices-support-e.md#common_event_location_mode_state_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_SLEEP

```TypeScript
COMMON_EVENT_IVI_SLEEP = 'common.event.IVI_SLEEP'
```

（预留事件，暂未支持）提示车辆的车载信息娱乐（IVI）系统正在休眠。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_IVI_SLEEP](arkts-basicservices-support-e.md#common_event_ivi_sleep)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_PAUSE

```TypeScript
COMMON_EVENT_IVI_PAUSE = 'common.event.IVI_PAUSE'
```

（预留事件，暂未支持）提示车辆的车载信息娱乐（IVI）系统已休眠，并通知应用程序停止播放。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_IVI_PAUSE](arkts-basicservices-support-e.md#common_event_ivi_pause)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_STANDBY

```TypeScript
COMMON_EVENT_IVI_STANDBY = 'common.event.IVI_STANDBY'
```

（预留事件，暂未支持）提示车辆的车载信息娱乐（IVI）系统中的第三方应用暂停当前工作。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_IVI_STANDBY](arkts-basicservices-support-e.md#common_event_ivi_standby)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_LASTMODE_SAVE

```TypeScript
COMMON_EVENT_IVI_LASTMODE_SAVE = 'common.event.IVI_LASTMODE_SAVE'
```

（预留事件，暂未支持）提示车辆的车载信息娱乐（IVI）系统中的第三方应用保存其最后一个模式。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_IVI_LASTMODE_SAVE](arkts-basicservices-support-e.md#common_event_ivi_lastmode_save)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_VOLTAGE_ABNORMAL

```TypeScript
COMMON_EVENT_IVI_VOLTAGE_ABNORMAL = 'common.event.IVI_VOLTAGE_ABNORMAL'
```

（预留事件，暂未支持）提示车辆电源系统电压异常。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_IVI_VOLTAGE_ABNORMAL](arkts-basicservices-support-e.md#common_event_ivi_voltage_abnormal)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_HIGH_TEMPERATURE

```TypeScript
COMMON_EVENT_IVI_HIGH_TEMPERATURE = 'common.event.IVI_HIGH_TEMPERATURE'
```

（预留事件，暂未支持）提示车辆的车载信息娱乐（IVI）系统温度过高。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_IVI_HIGH_TEMPERATURE](arkts-basicservices-support-e.md#common_event_ivi_high_temperature)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_EXTREME_TEMPERATURE

```TypeScript
COMMON_EVENT_IVI_EXTREME_TEMPERATURE = 'common.event.IVI_EXTREME_TEMPERATURE'
```

（预留事件，暂未支持）提示车辆的车载信息娱乐（IVI）系统温度极高。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_IVI_EXTREME_TEMPERATURE](arkts-basicservices-support-e.md#common_event_ivi_extreme_temperature)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL

```TypeScript
COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL = 'common.event.IVI_TEMPERATURE_ABNORMAL'
```

（预留事件，暂未支持）提示车辆的车载信息娱乐（IVI）系统具有极端温度。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL](arkts-basicservices-support-e.md#common_event_ivi_temperature_abnormal)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_VOLTAGE_RECOVERY

```TypeScript
COMMON_EVENT_IVI_VOLTAGE_RECOVERY = 'common.event.IVI_VOLTAGE_RECOVERY'
```

（预留事件，暂未支持）提示车辆电源系统电压恢复正常。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_IVI_VOLTAGE_RECOVERY](arkts-basicservices-support-e.md#common_event_ivi_voltage_recovery)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_TEMPERATURE_RECOVERY

```TypeScript
COMMON_EVENT_IVI_TEMPERATURE_RECOVERY = 'common.event.IVI_TEMPERATURE_RECOVERY'
```

（预留事件，暂未支持）提示车载系统温度恢复正常。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_IVI_TEMPERATURE_RECOVERY](arkts-basicservices-support-e.md#common_event_ivi_temperature_recovery)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_ACTIVE

```TypeScript
COMMON_EVENT_IVI_ACTIVE = 'common.event.IVI_ACTIVE'
```

（预留事件，暂未支持）提示车载系统电池服务处于活动状态。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_IVI_ACTIVE](arkts-basicservices-support-e.md#common_event_ivi_active)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_DEVICE_ATTACHED

```TypeScript
COMMON_EVENT_USB_DEVICE_ATTACHED = 'usual.event.hardware.usb.action.USB_DEVICE_ATTACHED'
```

当用户设备作为USB主机时，提示USB设备已挂载。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USB_DEVICE_ATTACHED](arkts-basicservices-support-e.md#common_event_usb_device_attached)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_DEVICE_DETACHED

```TypeScript
COMMON_EVENT_USB_DEVICE_DETACHED = 'usual.event.hardware.usb.action.USB_DEVICE_DETACHED'
```

当用户设备作为USB主机时，提示USB设备被卸载。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USB_DEVICE_DETACHED](arkts-basicservices-support-e.md#common_event_usb_device_detached)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_ACCESSORY_ATTACHED

```TypeScript
COMMON_EVENT_USB_ACCESSORY_ATTACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED'
```

（预留事件，暂未支持）提示已连接USB附件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USB_ACCESSORY_ATTACHED](arkts-basicservices-support-e.md#common_event_usb_accessory_attached)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_ACCESSORY_DETACHED

```TypeScript
COMMON_EVENT_USB_ACCESSORY_DETACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED'
```

（预留事件，暂未支持）提示USB附件被卸载。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_USB_ACCESSORY_DETACHED](arkts-basicservices-support-e.md#common_event_usb_accessory_detached)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_REMOVED

```TypeScript
COMMON_EVENT_DISK_REMOVED = 'usual.event.data.DISK_REMOVED'
```

（预留事件，暂未支持）提示外部存储设备状态变更为移除。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DISK_REMOVED](arkts-basicservices-support-e.md#common_event_disk_removed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_UNMOUNTED

```TypeScript
COMMON_EVENT_DISK_UNMOUNTED = 'usual.event.data.DISK_UNMOUNTED'
```

（预留事件，暂未支持）提示外部存储设备状态变更为卸载。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DISK_UNMOUNTED](arkts-basicservices-support-e.md#common_event_disk_unmounted)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_MOUNTED

```TypeScript
COMMON_EVENT_DISK_MOUNTED = 'usual.event.data.DISK_MOUNTED'
```

（预留事件，暂未支持）提示外部存储设备状态变更为挂载。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DISK_MOUNTED](arkts-basicservices-support-e.md#common_event_disk_mounted)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_BAD_REMOVAL

```TypeScript
COMMON_EVENT_DISK_BAD_REMOVAL = 'usual.event.data.DISK_BAD_REMOVAL'
```

（预留事件，暂未支持）提示外部存储设备在挂载状态下被移除。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DISK_BAD_REMOVAL](arkts-basicservices-support-e.md#common_event_disk_bad_removal)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_UNMOUNTABLE

```TypeScript
COMMON_EVENT_DISK_UNMOUNTABLE = 'usual.event.data.DISK_UNMOUNTABLE'
```

（预留事件，暂未支持）提示外部存储设备在插卡情况下无法挂载。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DISK_UNMOUNTABLE](arkts-basicservices-support-e.md#common_event_disk_unmountable)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_EJECT

```TypeScript
COMMON_EVENT_DISK_EJECT = 'usual.event.data.DISK_EJECT'
```

（预留事件，暂未支持）提示用户已作出弹出外部存储介质的操作（系统软件层面的交互操作，非直接物理弹出）。

要订阅此事件，您的应用必须具备ohos.permission.STORAGE_MANAGER权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_DISK_EJECT](arkts-basicservices-support-e.md#common_event_disk_eject)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED

```TypeScript
COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED = 'usual.event.data.VISIBLE_ACCOUNTS_UPDATED'
```

（预留事件，暂未支持）提示账户发生可见性的更改。

要订阅此事件，您的应用必须具备ohos.permission.GET_APP_ACCOUNTS权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED](arkts-basicservices-support-e.md#common_event_visible_accounts_updated)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ACCOUNT_DELETED

```TypeScript
COMMON_EVENT_ACCOUNT_DELETED = 'usual.event.data.ACCOUNT_DELETED'
```

（预留事件，暂未支持）提示有账户被删除。

要订阅此事件，您的应用必须具备ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_ACCOUNT_DELETED](arkts-basicservices-support-e.md#common_event_account_deleted)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_FOUNDATION_READY

```TypeScript
COMMON_EVENT_FOUNDATION_READY = 'common.event.FOUNDATION_READY'
```

（预留事件，暂未支持）提示foundation已准备好。

要订阅此事件，您的应用必须具备ohos.permission.RECEIVER_STARTUP_COMPLETED权限（该权限仅系统应用可申请）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_FOUNDATION_READY](arkts-basicservices-support-e.md#common_event_foundation_ready)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_AIRPLANE_MODE_CHANGED

```TypeScript
COMMON_EVENT_AIRPLANE_MODE_CHANGED = 'usual.event.AIRPLANE_MODE'
```

提示设备飞行模式发生了切换。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_AIRPLANE_MODE_CHANGED](arkts-basicservices-support-e.md#common_event_airplane_mode_changed)

**系统能力：** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SPLIT_SCREEN

```TypeScript
COMMON_EVENT_SPLIT_SCREEN = 'common.event.SPLIT_SCREEN'
```

提示分屏。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [COMMON_EVENT_SPLIT_SCREEN](arkts-basicservices-support-e.md#common_event_split_screen)

**系统能力：** SystemCapability.Notification.CommonEvent

