# Support

A system common event is an event that is published by a system service or system application and requires specific permissions to subscribe to. To publish or subscribe to this type of event, you must follow the event-specific definitions.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [Support](arkts-basicservices-commoneventmanager-support-e.md)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BOOT_COMPLETED

```TypeScript
COMMON_EVENT_BOOT_COMPLETED = 'usual.event.BOOT_COMPLETED'
```

Indicates that the boot is complete and the system is loaded.

To subscribe to this common event, your application must have the ohos.permission.RECEIVER_STARTUP_COMPLETED permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BOOT_COMPLETED](arkts-basicservices-commoneventmanager-support-e.md#common_event_boot_completed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCKED_BOOT_COMPLETED

```TypeScript
COMMON_EVENT_LOCKED_BOOT_COMPLETED = 'usual.event.LOCKED_BOOT_COMPLETED'
```

(reserved, not supported yet) Indicates that the guidance is complete and the system is loaded, but the screen is still locked.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_LOCKED_BOOT_COMPLETED](arkts-basicservices-commoneventmanager-support-e.md#common_event_locked_boot_completed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SHUTDOWN

```TypeScript
COMMON_EVENT_SHUTDOWN = 'usual.event.SHUTDOWN'
```

Indicates that the device is being shut down and will continue until it is finally shut down.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_SHUTDOWN](arkts-basicservices-commoneventmanager-support-e.md#common_event_shutdown)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_CHANGED

```TypeScript
COMMON_EVENT_BATTERY_CHANGED = 'usual.event.BATTERY_CHANGED'
```

Indicates that the battery charging status, battery level, and other information has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BATTERY_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_battery_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_LOW

```TypeScript
COMMON_EVENT_BATTERY_LOW = 'usual.event.BATTERY_LOW'
```

Indicates that the battery level is low.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BATTERY_LOW](arkts-basicservices-commoneventmanager-support-e.md#common_event_battery_low)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_OKAY

```TypeScript
COMMON_EVENT_BATTERY_OKAY = 'usual.event.BATTERY_OKAY'
```

Indicates that the battery level is normal.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BATTERY_OKAY](arkts-basicservices-commoneventmanager-support-e.md#common_event_battery_okay)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_CONNECTED

```TypeScript
COMMON_EVENT_POWER_CONNECTED = 'usual.event.POWER_CONNECTED'
```

Indicates that the device is connected to an external power supply.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_POWER_CONNECTED](arkts-basicservices-commoneventmanager-support-e.md#common_event_power_connected)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_DISCONNECTED

```TypeScript
COMMON_EVENT_POWER_DISCONNECTED = 'usual.event.POWER_DISCONNECTED'
```

Indicates that the device is disconnected from the external power supply.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_POWER_DISCONNECTED](arkts-basicservices-commoneventmanager-support-e.md#common_event_power_disconnected)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_OFF

```TypeScript
COMMON_EVENT_SCREEN_OFF = 'usual.event.SCREEN_OFF'
```

Indicates that the device screen is off and the device is in sleep mode.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_SCREEN_OFF](arkts-basicservices-commoneventmanager-support-e.md#common_event_screen_off)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_ON

```TypeScript
COMMON_EVENT_SCREEN_ON = 'usual.event.SCREEN_ON'
```

Indicates that the device screen is on and the device is in interactive state.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_SCREEN_ON](arkts-basicservices-commoneventmanager-support-e.md#common_event_screen_on)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_THERMAL_LEVEL_CHANGED

```TypeScript
COMMON_EVENT_THERMAL_LEVEL_CHANGED = 'usual.event.THERMAL_LEVEL_CHANGED'
```

Indicates that the device thermal level has changed.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_THERMAL_LEVEL_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_thermal_level_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_PRESENT

```TypeScript
COMMON_EVENT_USER_PRESENT = 'usual.event.USER_PRESENT'
```

(reserved, not supported yet) Indicates that the user unlocks the device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USER_PRESENT](arkts-basicservices-commoneventmanager-support-e.md#common_event_user_present)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIME_TICK

```TypeScript
COMMON_EVENT_TIME_TICK = 'usual.event.TIME_TICK'
```

Indicates that the system time has changed as time ticks by.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_TIME_TICK](arkts-basicservices-commoneventmanager-support-e.md#common_event_time_tick)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIME_CHANGED

```TypeScript
COMMON_EVENT_TIME_CHANGED = 'usual.event.TIME_CHANGED'
```

Indicates that the system time is set.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_TIME_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_time_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DATE_CHANGED

```TypeScript
COMMON_EVENT_DATE_CHANGED = 'usual.event.DATE_CHANGED'
```

(reserved, not supported yet) Indicates that the system date has been changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DATE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_date_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIMEZONE_CHANGED

```TypeScript
COMMON_EVENT_TIMEZONE_CHANGED = 'usual.event.TIMEZONE_CHANGED'
```

Indicates that the system time zone is changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_TIMEZONE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_timezone_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CLOSE_SYSTEM_DIALOGS

```TypeScript
COMMON_EVENT_CLOSE_SYSTEM_DIALOGS = 'usual.event.CLOSE_SYSTEM_DIALOGS'
```

(reserved, not supported yet) Indicates that the user closes a temporary system dialog box.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_CLOSE_SYSTEM_DIALOGS](arkts-basicservices-commoneventmanager-support-e.md#common_event_close_system_dialogs)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_ADDED

```TypeScript
COMMON_EVENT_PACKAGE_ADDED = 'usual.event.PACKAGE_ADDED'
```

Indicates that a new application package has been installed on the device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGE_ADDED](arkts-basicservices-commoneventmanager-support-e.md#common_event_package_added)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_REPLACED

```TypeScript
COMMON_EVENT_PACKAGE_REPLACED = 'usual.event.PACKAGE_REPLACED'
```

(reserved, not supported yet) Indicates that a later version of an installed application package has replaced the previous one on the device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGE_REPLACED](arkts-basicservices-commoneventmanager-support-e.md#common_event_package_replaced)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_REPLACED

```TypeScript
COMMON_EVENT_MY_PACKAGE_REPLACED = 'usual.event.MY_PACKAGE_REPLACED'
```

(reserved, not supported yet) Indicates that the new version of the application package has replaced the previous version.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_MY_PACKAGE_REPLACED](arkts-basicservices-commoneventmanager-support-e.md#common_event_my_package_replaced)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_REMOVED

```TypeScript
COMMON_EVENT_PACKAGE_REMOVED = 'usual.event.PACKAGE_REMOVED'
```

Indicates that an installed application has been uninstalled from the device with the application data retained.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGE_REMOVED](arkts-basicservices-commoneventmanager-support-e.md#common_event_package_removed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BUNDLE_REMOVED

```TypeScript
COMMON_EVENT_BUNDLE_REMOVED = 'usual.event.BUNDLE_REMOVED'
```

(reserved, not supported yet) Indicates that an installed bundle has been uninstalled from the device with the application data retained.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BUNDLE_REMOVED](arkts-basicservices-commoneventmanager-support-e.md#common_event_bundle_removed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_FULLY_REMOVED

```TypeScript
COMMON_EVENT_PACKAGE_FULLY_REMOVED = 'usual.event.PACKAGE_FULLY_REMOVED'
```

(reserved, not supported yet) Indicates that an installed application, including both the application data and code, has been completely uninstalled from the device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGE_FULLY_REMOVED](arkts-basicservices-commoneventmanager-support-e.md#common_event_package_fully_removed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_CHANGED

```TypeScript
COMMON_EVENT_PACKAGE_CHANGED = 'usual.event.PACKAGE_CHANGED'
```

Indicates that an application package has been changed (for example, an ability in the package has been enabled or disabled).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_package_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_RESTARTED

```TypeScript
COMMON_EVENT_PACKAGE_RESTARTED = 'usual.event.PACKAGE_RESTARTED'
```

Indicates that the user closed all processes of the application and restarted the application.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGE_RESTARTED](arkts-basicservices-commoneventmanager-support-e.md#common_event_package_restarted)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_DATA_CLEARED

```TypeScript
COMMON_EVENT_PACKAGE_DATA_CLEARED = 'usual.event.PACKAGE_DATA_CLEARED'
```

Indicates that the user cleared the application package data.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGE_DATA_CLEARED](arkts-basicservices-commoneventmanager-support-e.md#common_event_package_data_cleared)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGES_SUSPENDED

```TypeScript
COMMON_EVENT_PACKAGES_SUSPENDED = 'usual.event.PACKAGES_SUSPENDED'
```

(reserved, not supported yet) Indicates that application packages have been suspended.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGES_SUSPENDED](arkts-basicservices-commoneventmanager-support-e.md#common_event_packages_suspended)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGES_UNSUSPENDED

```TypeScript
COMMON_EVENT_PACKAGES_UNSUSPENDED = 'usual.event.PACKAGES_UNSUSPENDED'
```

(reserved, not supported yet) Indicates that the application HAP package is not suspended (resumed from the suspended state).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGES_UNSUSPENDED](arkts-basicservices-commoneventmanager-support-e.md#common_event_packages_unsuspended)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_SUSPENDED

```TypeScript
COMMON_EVENT_MY_PACKAGE_SUSPENDED = 'usual.event.MY_PACKAGE_SUSPENDED'
```

Indicates that the application HAP package is suspended.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_MY_PACKAGE_SUSPENDED](arkts-basicservices-commoneventmanager-support-e.md#common_event_my_package_suspended)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_UNSUSPENDED

```TypeScript
COMMON_EVENT_MY_PACKAGE_UNSUSPENDED = 'usual.event.MY_PACKAGE_UNSUSPENDED'
```

Indicates that the application package is not suspended.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_MY_PACKAGE_UNSUSPENDED](arkts-basicservices-commoneventmanager-support-e.md#common_event_my_package_unsuspended)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_UID_REMOVED

```TypeScript
COMMON_EVENT_UID_REMOVED = 'usual.event.UID_REMOVED'
```

(reserved, not supported yet) Indicates that a user ID has been removed from the system.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_UID_REMOVED](arkts-basicservices-commoneventmanager-support-e.md#common_event_uid_removed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_FIRST_LAUNCH

```TypeScript
COMMON_EVENT_PACKAGE_FIRST_LAUNCH = 'usual.event.PACKAGE_FIRST_LAUNCH'
```

(reserved, not supported yet) Indicates that an installed application is started for the first time.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGE_FIRST_LAUNCH](arkts-basicservices-commoneventmanager-support-e.md#common_event_package_first_launch)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION

```TypeScript
COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION = 'usual.event.PACKAGE_NEEDS_VERIFICATION'
```

(reserved, not supported yet) Indicates that an application requires system verification.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION](arkts-basicservices-commoneventmanager-support-e.md#common_event_package_needs_verification)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_VERIFIED

```TypeScript
COMMON_EVENT_PACKAGE_VERIFIED = 'usual.event.PACKAGE_VERIFIED'
```

(reserved, not supported yet) Indicates that an application has been verified by the system.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_PACKAGE_VERIFIED](arkts-basicservices-commoneventmanager-support-e.md#common_event_package_verified)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE

```TypeScript
COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_AVAILABLE'
```

(reserved, not supported yet) Indicates that applications installed on the external storage are available for the system.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE](arkts-basicservices-commoneventmanager-support-e.md#common_event_external_applications_available)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE

```TypeScript
COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE'
```

(reserved, not supported yet) Indicates that applications installed on the external storage are not available for the system.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE](arkts-basicservices-commoneventmanager-support-e.md#common_event_external_applications_unavailable)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CONFIGURATION_CHANGED

```TypeScript
COMMON_EVENT_CONFIGURATION_CHANGED = 'usual.event.CONFIGURATION_CHANGED'
```

(reserved, not supported yet) Indicates that the device state (for example, orientation and locale) has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_CONFIGURATION_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_configuration_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCALE_CHANGED

```TypeScript
COMMON_EVENT_LOCALE_CHANGED = 'usual.event.LOCALE_CHANGED'
```

(reserved, not supported yet) Indicates that the device locale has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_LOCALE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_locale_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MANAGE_PACKAGE_STORAGE

```TypeScript
COMMON_EVENT_MANAGE_PACKAGE_STORAGE = 'usual.event.MANAGE_PACKAGE_STORAGE'
```

(reserved, not supported yet) Indicates that the device storage is insufficient.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_MANAGE_PACKAGE_STORAGE](arkts-basicservices-commoneventmanager-support-e.md#common_event_manage_package_storage)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DRIVE_MODE

```TypeScript
COMMON_EVENT_DRIVE_MODE = 'common.event.DRIVE_MODE'
```

(reserved, not supported yet) Indicates that the system is in driving mode.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DRIVE_MODE](arkts-basicservices-commoneventmanager-support-e.md#common_event_drive_mode)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HOME_MODE

```TypeScript
COMMON_EVENT_HOME_MODE = 'common.event.HOME_MODE'
```

(reserved, not supported yet) Indicates that the system is in home mode.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_HOME_MODE](arkts-basicservices-commoneventmanager-support-e.md#common_event_home_mode)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_OFFICE_MODE

```TypeScript
COMMON_EVENT_OFFICE_MODE = 'common.event.OFFICE_MODE'
```

(reserved, not supported yet) Indicates that the system is in office mode.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_OFFICE_MODE](arkts-basicservices-commoneventmanager-support-e.md#common_event_office_mode)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STARTED

```TypeScript
COMMON_EVENT_USER_STARTED = 'usual.event.USER_STARTED'
```

(reserved, not supported yet) Indicates that the user has been started.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USER_STARTED](arkts-basicservices-commoneventmanager-support-e.md#common_event_user_started)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_BACKGROUND

```TypeScript
COMMON_EVENT_USER_BACKGROUND = 'usual.event.USER_BACKGROUND'
```

(reserved, not supported yet) Indicates that the user has been brought to the background.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USER_BACKGROUND](arkts-basicservices-commoneventmanager-support-e.md#common_event_user_background)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_FOREGROUND

```TypeScript
COMMON_EVENT_USER_FOREGROUND = 'usual.event.USER_FOREGROUND'
```

(reserved, not supported yet) Indicates that the user has been brought to the foreground.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USER_FOREGROUND](arkts-basicservices-commoneventmanager-support-e.md#common_event_user_foreground)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_SWITCHED

```TypeScript
COMMON_EVENT_USER_SWITCHED = 'usual.event.USER_SWITCHED'
```

Indicates that user switching is in progress.

To subscribe to this common event, your application must have the ohos.permission.MANAGE_LOCAL_ACCOUNTS permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USER_SWITCHED](arkts-basicservices-commoneventmanager-support-e.md#common_event_user_switched)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STARTING

```TypeScript
COMMON_EVENT_USER_STARTING = 'usual.event.USER_STARTING'
```

(reserved, not supported yet) Indicates that user starting is in progress. To subscribe to this common event, your application must have the ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USER_STARTING](arkts-basicservices-commoneventmanager-support-e.md#common_event_user_starting)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_UNLOCKED

```TypeScript
COMMON_EVENT_USER_UNLOCKED = 'usual.event.USER_UNLOCKED'
```

(reserved, not supported yet) Indicates that the credential encryption storage of the current user has been unlocked upon restart.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USER_UNLOCKED](arkts-basicservices-commoneventmanager-support-e.md#common_event_user_unlocked)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STOPPING

```TypeScript
COMMON_EVENT_USER_STOPPING = 'usual.event.USER_STOPPING'
```

(reserved, not supported yet) Indicates the user to be stopped.

To subscribe to this common event, your application must have the ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USER_STOPPING](arkts-basicservices-commoneventmanager-support-e.md#common_event_user_stopping)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STOPPED

```TypeScript
COMMON_EVENT_USER_STOPPED = 'usual.event.USER_STOPPED'
```

(reserved, not supported yet) Indicates that the user has been stopped.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USER_STOPPED](arkts-basicservices-commoneventmanager-support-e.md#common_event_user_stopped)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HWID_LOGIN

```TypeScript
COMMON_EVENT_HWID_LOGIN = 'common.event.HWID_LOGIN'
```

HW id login successfully.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN](arkts-basicservices-commoneventmanager-support-e.md#common_event_distributed_account_login)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HWID_LOGOUT

```TypeScript
COMMON_EVENT_HWID_LOGOUT = 'common.event.HWID_LOGOUT'
```

HW id logout successfully.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT](arkts-basicservices-commoneventmanager-support-e.md#common_event_distributed_account_logout)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HWID_TOKEN_INVALID

```TypeScript
COMMON_EVENT_HWID_TOKEN_INVALID = 'common.event.HWID_TOKEN_INVALID'
```

HW id is invalid.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID](arkts-basicservices-commoneventmanager-support-e.md#common_event_distributed_account_token_invalid)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HWID_LOGOFF

```TypeScript
COMMON_EVENT_HWID_LOGOFF = 'common.event.HWID_LOGOFF'
```

HW id logs off.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF](arkts-basicservices-commoneventmanager-support-e.md#common_event_distributed_account_logoff)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_POWER_STATE

```TypeScript
COMMON_EVENT_WIFI_POWER_STATE = 'usual.event.wifi.POWER_STATE'
```

Indicates a change in the Wi-Fi state (enabled or disabled).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_POWER_STATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_power_state)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_SCAN_FINISHED

```TypeScript
COMMON_EVENT_WIFI_SCAN_FINISHED = 'usual.event.wifi.SCAN_FINISHED'
```

Indicates that the Wi-Fi access point has been scanned and proved available.

To subscribe to this common event, your application must have the ohos.permission.LOCATION permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_SCAN_FINISHED](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_scan_finished)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_RSSI_VALUE

```TypeScript
COMMON_EVENT_WIFI_RSSI_VALUE = 'usual.event.wifi.RSSI_VALUE'
```

Indicates that the Wi-Fi signal strength (RSSI) has changed.

To subscribe to this common event, your application must have the ohos.permission.GET_WIFI_INFO permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_RSSI_VALUE](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_rssi_value)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_CONN_STATE

```TypeScript
COMMON_EVENT_WIFI_CONN_STATE = 'usual.event.wifi.CONN_STATE'
```

Indicates that the Wi-Fi connection state has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_CONN_STATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_conn_state)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_HOTSPOT_STATE

```TypeScript
COMMON_EVENT_WIFI_HOTSPOT_STATE = 'usual.event.wifi.HOTSPOT_STATE'
```

Indicates a change in the Wi-Fi hotspot state (enabled or disabled).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_HOTSPOT_STATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_hotspot_state)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_AP_STA_JOIN

```TypeScript
COMMON_EVENT_WIFI_AP_STA_JOIN = 'usual.event.wifi.WIFI_HS_STA_JOIN'
```

Indicates that a client has joined the Wi-Fi hotspot of the current device.

To subscribe to this common event, your application must have the ohos.permission.GET_WIFI_INFO permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_AP_STA_JOIN](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_ap_sta_join)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_AP_STA_LEAVE

```TypeScript
COMMON_EVENT_WIFI_AP_STA_LEAVE = 'usual.event.wifi.WIFI_HS_STA_LEAVE'
```

Indicates that the client is disconnected from the Wi-Fi hotspot of the current device.

To subscribe to this common event, your application must have the ohos.permission.GET_WIFI_INFO permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_AP_STA_LEAVE](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_ap_sta_leave)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE

```TypeScript
COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE = 'usual.event.wifi.mplink.STATE_CHANGE'
```

(not supported yet) Indicates that the state of MPLINK (an enhanced Wi-Fi feature) has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_mplink_state_change)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_CONN_STATE

```TypeScript
COMMON_EVENT_WIFI_P2P_CONN_STATE = 'usual.event.wifi.p2p.CONN_STATE_CHANGE'
```

Indicates that the Wi-Fi P2P connection state has changed.

To subscribe to this common event, your application must have the ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION permissions.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_P2P_CONN_STATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_p2p_conn_state)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_STATE_CHANGED = 'usual.event.wifi.p2p.STATE_CHANGE'
```

Indicates a change in the Wi-Fi P2P state (enabled or disabled).

To subscribe to this common event, your application must have the ohos.permission.GET_WIFI_INFO permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_P2P_STATE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_p2p_state_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED = 'usual.event.wifi.p2p.DEVICES_CHANGE'
```

Indicates that the state of the Wi-Fi P2P peer device has changed.

To subscribe to this common event, your application must have the ohos.permission.GET_WIFI_INFO permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_p2p_peers_state_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED = 'usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE'
```

Indicates that the Wi-Fi P2P discovery state has changed.

To subscribe to this common event, your application must have the ohos.permission.GET_WIFI_INFO permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_p2p_peers_discovery_state_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED = 'usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE'
```

Indicates that the state of the Wi-Fi P2P local device has changed.

To subscribe to this common event, your application must have the ohos.permission.GET_WIFI_INFO permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_p2p_current_device_state_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED = 'usual.event.wifi.p2p.GROUP_STATE_CHANGED'
```

Indicates that the Wi-Fi P2P group information has changed.

To subscribe to this common event, your application must have the ohos.permission.GET_WIFI_INFO permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_wifi_p2p_group_state_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE'
```

(reserved, not supported yet) Indicates the connection state of Bluetooth handsfree communication.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_handsfree_ag_connect_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE'
```

(reserved, not supported yet) Indicates that the device connected to the Bluetooth handsfree function is active.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_handsfree_ag_current_device_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE'
```

(reserved, not supported yet) Indicates that the connection state of Bluetooth A2DP has changed.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_handsfree_ag_audio_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE'
```

(reserved, not supported yet) Indicates the connection state of Bluetooth A2DP.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_a2dpsource_connect_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE = 'usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE'
```

(reserved, not supported yet) Indicates that the device connected using Bluetooth A2DP is active.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_a2dpsource_current_device_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE'
```

(reserved, not supported yet) Indicates that the playing state of Bluetooth A2DP has changed.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_a2dpsource_playing_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE'
```

(reserved, not supported yet) Indicates that the AVRCP connection state of Bluetooth A2DP has changed.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_a2dpsource_avrcp_connect_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE = 'usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE'
```

(reserved, not supported yet) Indicates that the audio codec state of Bluetooth A2DP has changed.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_a2dpsource_codec_value_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED = 'usual.event.bluetooth.remotedevice.DISCOVERED'
```

(reserved, not supported yet) Indicates that a remote Bluetooth device is discovered.

To subscribe to this common event, your application must have the ohos.permission.LOCATION and ohos.permission.USE_BLUETOOTH permissions.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_discovered)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE'
```

(reserved, not supported yet) Indicates that the Bluetooth class of a remote Bluetooth device has changed.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_class_value_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED = 'usual.event.bluetooth.remotedevice.ACL_CONNECTED'
```

(reserved, not supported yet) Indicates that a low-level (ACL) connection has been established with the remote Bluetooth device.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_acl_connected)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED = 'usual.event.bluetooth.remotedevice.ACL_DISCONNECTED'
```

(reserved, not supported yet) Indicates that the low-level (ACL) connection has been disconnected from the remote Bluetooth device.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_acl_disconnected)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE = 'usual.event.bluetooth.remotedevice.NAME_UPDATE'
```

(reserved, not supported yet) Indicates that the friendly name of a remote Bluetooth device is retrieved for the first time or has changed since the last retrieval.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_name_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE = 'usual.event.bluetooth.remotedevice.PAIR_STATE'
```

(reserved, not supported yet) Indicates the connection state with a remote Bluetooth device is changed.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_pair_state)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE = 'usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE'
```

(reserved, not supported yet) Indicates that the battery level of a remote Bluetooth device is retrieved for the first time or has changed since the last retrieval.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_battery_value_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT = 'usual.event.bluetooth.remotedevice.SDP_RESULT'
```

(reserved, not supported yet) Indicates the SDP state of a remote Bluetooth device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_sdp_result)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE = 'usual.event.bluetooth.remotedevice.UUID_VALUE'
```

(reserved, not supported yet) Indicates the UUID connection state with a remote Bluetooth device.

To subscribe to this common event, your application must have the ohos.permission.DISCOVER_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_uuid_value)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ = 'usual.event.bluetooth.remotedevice.PAIRING_REQ'
```

(reserved, not supported yet) Indicates the pairing request from a remote Bluetooth device.

To subscribe to this common event, your application must have the ohos.permission.DISCOVER_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_pairing_req)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL = 'usual.event.bluetooth.remotedevice.PAIRING_CANCEL'
```

(reserved, not supported yet) Indicates that Bluetooth pairing has been canceled.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_pairing_cancel)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ = 'usual.event.bluetooth.remotedevice.CONNECT_REQ'
```

(reserved, not supported yet) Indicates the connection request from a remote Bluetooth device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_connect_req)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY = 'usual.event.bluetooth.remotedevice.CONNECT_REPLY'
```

(reserved, not supported yet) Indicates the response to the connection request from a remote Bluetooth device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_connect_reply)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL = 'usual.event.bluetooth.remotedevice.CONNECT_CANCEL'
```

(reserved, not supported yet) Indicates that the connection to a remote Bluetooth device has been canceled.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_remotedevice_connect_cancel)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE'
```

(reserved, not supported yet) Indicates that the connection state with a Bluetooth handsfree has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_handsfreeunit_connect_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE'
```

(reserved, not supported yet) Indicates that the audio state of a Bluetooth handsfree has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_handsfreeunit_audio_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT = 'usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT'
```

(reserved, not supported yet) Indicates that the audio gateway state of a Bluetooth handsfree has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_handsfreeunit_ag_common_event)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE = 'usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE'
```

(reserved, not supported yet) Indicates that the calling state of a Bluetooth handsfree has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_handsfreeunit_ag_call_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE = 'usual.event.bluetooth.host.STATE_UPDATE'
```

(reserved, not supported yet) Indicates a change in the Bluetooth adapter state (enabled or disabled).

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_host_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE = 'usual.event.bluetooth.host.REQ_DISCOVERABLE'
```

(reserved, not supported yet) Indicates that Bluetooth is discoverable.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_host_req_discoverable)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE = 'usual.event.bluetooth.host.REQ_ENABLE'
```

(reserved, not supported yet) Indicates that Bluetooth is enabled.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_host_req_enable)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE = 'usual.event.bluetooth.host.REQ_DISABLE'
```

(reserved, not supported yet) Indicates that Bluetooth is disabled.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_host_req_disable)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE = 'usual.event.bluetooth.host.SCAN_MODE_UPDATE'
```

(reserved, not supported yet) Indicates that the Bluetooth scan mode of the device is changed.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_host_scan_mode_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED = 'usual.event.bluetooth.host.DISCOVERY_STARTED'
```

(reserved, not supported yet) Indicates that Bluetooth discovery is started on the device.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_host_discovery_started)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED = 'usual.event.bluetooth.host.DISCOVERY_FINISHED'
```

(reserved, not supported yet) Indicates that Bluetooth discovery is finished on the device.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_host_discovery_finished)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE = 'usual.event.bluetooth.host.NAME_UPDATE'
```

(reserved, not supported yet) Indicates that the name of the device Bluetooth adapter has changed.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_host_name_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE'
```

(reserved, not supported yet) Indicates that the connection state of Bluetooth A2DP Sink has changed.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_a2dpsink_connect_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE'
```

(reserved, not supported yet) Indicates that the playing state of Bluetooth A2DP Sink has changed.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_a2dpsink_playing_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE = 'usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE'
```

(reserved, not supported yet) Indicates that the audio state of Bluetooth A2DP Sink has changed.

To subscribe to this common event, your application must have the ohos.permission.USE_BLUETOOTH permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE](arkts-basicservices-commoneventmanager-support-e.md#common_event_bluetooth_a2dpsink_audio_state_update)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED

```TypeScript
COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED = 'usual.event.nfc.action.ADAPTER_STATE_CHANGED'
```

(reserved, not supported yet) Indicates that the state of the device NFC adapter has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_nfc_action_adapter_state_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED

```TypeScript
COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED = 'usual.event.nfc.action.RF_FIELD_ON_DETECTED'
```

(reserved, not supported yet) Indicates that the NFC RF field is detected to be in the enabled state.

To subscribe to this common event, your application must have the ohos.permission.MANAGE_SECURE_SETTINGS permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED](arkts-basicservices-commoneventmanager-support-e.md#common_event_nfc_action_rf_field_on_detected)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED

```TypeScript
COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED = 'usual.event.nfc.action.RF_FIELD_OFF_DETECTED'
```

(reserved, not supported yet) Indicates that the NFC RF field is detected to be in the disabled state.

To subscribe to this common event, your application must have the ohos.permission.MANAGE_SECURE_SETTINGS permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED](arkts-basicservices-commoneventmanager-support-e.md#common_event_nfc_action_rf_field_off_detected)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISCHARGING

```TypeScript
COMMON_EVENT_DISCHARGING = 'usual.event.DISCHARGING'
```

Indicates that the system stops charging the battery.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DISCHARGING](arkts-basicservices-commoneventmanager-support-e.md#common_event_discharging)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CHARGING

```TypeScript
COMMON_EVENT_CHARGING = 'usual.event.CHARGING'
```

Indicates that the system starts charging the battery.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_CHARGING](arkts-basicservices-commoneventmanager-support-e.md#common_event_charging)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED

```TypeScript
COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED = 'usual.event.DEVICE_IDLE_MODE_CHANGED'
```

(reserved, not supported yet) Indicates that the system idle mode has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_device_idle_mode_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_SAVE_MODE_CHANGED

```TypeScript
COMMON_EVENT_POWER_SAVE_MODE_CHANGED = 'usual.event.POWER_SAVE_MODE_CHANGED'
```

Indicates that the system power-saving mode has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_POWER_SAVE_MODE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_power_save_mode_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_ADDED

```TypeScript
COMMON_EVENT_USER_ADDED = 'usual.event.USER_ADDED'
```

Indicates that a user has been added to the system.

To subscribe to this common event, your application must have the ohos.permission.MANAGE_LOCAL_ACCOUNTS permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USER_ADDED](arkts-basicservices-commoneventmanager-support-e.md#common_event_user_added)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_REMOVED

```TypeScript
COMMON_EVENT_USER_REMOVED = 'usual.event.USER_REMOVED'
```

Indicates that a user has been removed from the system.

To subscribe to this common event, your application must have the ohos.permission.MANAGE_LOCAL_ACCOUNTS permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USER_REMOVED](arkts-basicservices-commoneventmanager-support-e.md#common_event_user_removed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_ADDED

```TypeScript
COMMON_EVENT_ABILITY_ADDED = 'common.event.ABILITY_ADDED'
```

(reserved, not supported yet) Indicates that an ability has been added.

To subscribe to this common event, your application must have the ohos.permission.LISTEN_BUNDLE_CHANGE permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_ABILITY_ADDED](arkts-basicservices-commoneventmanager-support-e.md#common_event_ability_added)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_REMOVED

```TypeScript
COMMON_EVENT_ABILITY_REMOVED = 'common.event.ABILITY_REMOVED'
```

(reserved, not supported yet) Indicates that an ability has been removed.

To subscribe to this common event, your application must have the ohos.permission.LISTEN_BUNDLE_CHANGE permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_ABILITY_REMOVED](arkts-basicservices-commoneventmanager-support-e.md#common_event_ability_removed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_UPDATED

```TypeScript
COMMON_EVENT_ABILITY_UPDATED = 'common.event.ABILITY_UPDATED'
```

(reserved, not supported yet) Indicates that an ability has been updated.

To subscribe to this common event, your application must have the ohos.permission.LISTEN_BUNDLE_CHANGE permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_ABILITY_UPDATED](arkts-basicservices-commoneventmanager-support-e.md#common_event_ability_updated)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCATION_MODE_STATE_CHANGED

```TypeScript
COMMON_EVENT_LOCATION_MODE_STATE_CHANGED = 'usual.event.location.MODE_STATE_CHANGED'
```

(reserved, not supported yet) Indicates that the location mode of the system has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_LOCATION_MODE_STATE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_location_mode_state_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_SLEEP

```TypeScript
COMMON_EVENT_IVI_SLEEP = 'common.event.IVI_SLEEP'
```

(reserved, not supported yet) Indicates that the in-vehicle infotainment (IVI) system of the vehicle is sleeping.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_IVI_SLEEP](arkts-basicservices-commoneventmanager-support-e.md#common_event_ivi_sleep)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_PAUSE

```TypeScript
COMMON_EVENT_IVI_PAUSE = 'common.event.IVI_PAUSE'
```

(reserved, not supported yet) Indicates that the IVI system of the vehicle is in sleep mode and notifies the application to stop playing.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_IVI_PAUSE](arkts-basicservices-commoneventmanager-support-e.md#common_event_ivi_pause)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_STANDBY

```TypeScript
COMMON_EVENT_IVI_STANDBY = 'common.event.IVI_STANDBY'
```

(reserved, not supported yet) Indicates that a third-party application in the IVI system of a vehicle is suspended.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_IVI_STANDBY](arkts-basicservices-commoneventmanager-support-e.md#common_event_ivi_standby)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_LASTMODE_SAVE

```TypeScript
COMMON_EVENT_IVI_LASTMODE_SAVE = 'common.event.IVI_LASTMODE_SAVE'
```

(reserved, not supported yet) Indicates that the third-party application in the IVI system of the vehicle saves the last mode.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_IVI_LASTMODE_SAVE](arkts-basicservices-commoneventmanager-support-e.md#common_event_ivi_lastmode_save)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_VOLTAGE_ABNORMAL

```TypeScript
COMMON_EVENT_IVI_VOLTAGE_ABNORMAL = 'common.event.IVI_VOLTAGE_ABNORMAL'
```

(reserved, not supported yet) Indicates that the voltage of the vehicle's power system is abnormal.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_IVI_VOLTAGE_ABNORMAL](arkts-basicservices-commoneventmanager-support-e.md#common_event_ivi_voltage_abnormal)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_HIGH_TEMPERATURE

```TypeScript
COMMON_EVENT_IVI_HIGH_TEMPERATURE = 'common.event.IVI_HIGH_TEMPERATURE'
```

(reserved, not supported yet) Indicates that the temperature of the IVI system of the vehicle is too high.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_IVI_HIGH_TEMPERATURE](arkts-basicservices-commoneventmanager-support-e.md#common_event_ivi_high_temperature)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_EXTREME_TEMPERATURE

```TypeScript
COMMON_EVENT_IVI_EXTREME_TEMPERATURE = 'common.event.IVI_EXTREME_TEMPERATURE'
```

(reserved, not supported yet) Indicates that the temperature of the IVI system of the vehicle is extremely high.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_IVI_EXTREME_TEMPERATURE](arkts-basicservices-commoneventmanager-support-e.md#common_event_ivi_extreme_temperature)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL

```TypeScript
COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL = 'common.event.IVI_TEMPERATURE_ABNORMAL'
```

(reserved, not supported yet) Indicates that the IVI system of the vehicle has an extreme temperature.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL](arkts-basicservices-commoneventmanager-support-e.md#common_event_ivi_temperature_abnormal)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_VOLTAGE_RECOVERY

```TypeScript
COMMON_EVENT_IVI_VOLTAGE_RECOVERY = 'common.event.IVI_VOLTAGE_RECOVERY'
```

(reserved, not supported yet) Indicates that the voltage of the vehicle's power system is restored to normal.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_IVI_VOLTAGE_RECOVERY](arkts-basicservices-commoneventmanager-support-e.md#common_event_ivi_voltage_recovery)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_TEMPERATURE_RECOVERY

```TypeScript
COMMON_EVENT_IVI_TEMPERATURE_RECOVERY = 'common.event.IVI_TEMPERATURE_RECOVERY'
```

(reserved, not supported yet) Indicates that the temperature of the IVI system is restored to normal.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_IVI_TEMPERATURE_RECOVERY](arkts-basicservices-commoneventmanager-support-e.md#common_event_ivi_temperature_recovery)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_ACTIVE

```TypeScript
COMMON_EVENT_IVI_ACTIVE = 'common.event.IVI_ACTIVE'
```

(reserved, not supported yet) Indicates that the battery service of the vehicle-mounted system is active.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_IVI_ACTIVE](arkts-basicservices-commoneventmanager-support-e.md#common_event_ivi_active)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_DEVICE_ATTACHED

```TypeScript
COMMON_EVENT_USB_DEVICE_ATTACHED = 'usual.event.hardware.usb.action.USB_DEVICE_ATTACHED'
```

Indicates that a USB device has been attached to the device functioning as a USB host.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USB_DEVICE_ATTACHED](arkts-basicservices-commoneventmanager-support-e.md#common_event_usb_device_attached)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_DEVICE_DETACHED

```TypeScript
COMMON_EVENT_USB_DEVICE_DETACHED = 'usual.event.hardware.usb.action.USB_DEVICE_DETACHED'
```

Indicates that a USB device has been detached from the device functioning as a USB host.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USB_DEVICE_DETACHED](arkts-basicservices-commoneventmanager-support-e.md#common_event_usb_device_detached)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_ACCESSORY_ATTACHED

```TypeScript
COMMON_EVENT_USB_ACCESSORY_ATTACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED'
```

(reserved, not supported yet) Indicates that a USB accessory was attached.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USB_ACCESSORY_ATTACHED](arkts-basicservices-commoneventmanager-support-e.md#common_event_usb_accessory_attached)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_ACCESSORY_DETACHED

```TypeScript
COMMON_EVENT_USB_ACCESSORY_DETACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED'
```

(reserved, not supported yet) Indicates that the USB attachment is uninstalled.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_USB_ACCESSORY_DETACHED](arkts-basicservices-commoneventmanager-support-e.md#common_event_usb_accessory_detached)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_REMOVED

```TypeScript
COMMON_EVENT_DISK_REMOVED = 'usual.event.data.DISK_REMOVED'
```

(reserved, not supported yet) Indicates that an external storage device was removed.

To subscribe to this common event, your application must have the ohos.permission.STORAGE_MANAGER permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DISK_REMOVED](arkts-basicservices-commoneventmanager-support-e.md#common_event_disk_removed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_UNMOUNTED

```TypeScript
COMMON_EVENT_DISK_UNMOUNTED = 'usual.event.data.DISK_UNMOUNTED'
```

(reserved, not supported yet) Indicates that an external storage device was unmounted.

To subscribe to this common event, your application must have the ohos.permission.STORAGE_MANAGER permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DISK_UNMOUNTED](arkts-basicservices-commoneventmanager-support-e.md#common_event_disk_unmounted)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_MOUNTED

```TypeScript
COMMON_EVENT_DISK_MOUNTED = 'usual.event.data.DISK_MOUNTED'
```

(reserved, not supported yet) Indicates that an external storage device was mounted.

To subscribe to this common event, your application must have the ohos.permission.STORAGE_MANAGER permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DISK_MOUNTED](arkts-basicservices-commoneventmanager-support-e.md#common_event_disk_mounted)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_BAD_REMOVAL

```TypeScript
COMMON_EVENT_DISK_BAD_REMOVAL = 'usual.event.data.DISK_BAD_REMOVAL'
```

(reserved, not supported yet) Indicates that an external storage device was removed without being unmounted.

To subscribe to this common event, your application must have the ohos.permission.STORAGE_MANAGER permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DISK_BAD_REMOVAL](arkts-basicservices-commoneventmanager-support-e.md#common_event_disk_bad_removal)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_UNMOUNTABLE

```TypeScript
COMMON_EVENT_DISK_UNMOUNTABLE = 'usual.event.data.DISK_UNMOUNTABLE'
```

(reserved, not supported yet) Indicates that the external storage device cannot be mounted when a card is inserted.

To subscribe to this common event, your application must have the ohos.permission.STORAGE_MANAGER permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DISK_UNMOUNTABLE](arkts-basicservices-commoneventmanager-support-e.md#common_event_disk_unmountable)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_EJECT

```TypeScript
COMMON_EVENT_DISK_EJECT = 'usual.event.data.DISK_EJECT'
```

(reserved, not supported yet) Indicates that the external storage medium has been ejected (interactive operation at the system software layer, not directly ejected physically).

To subscribe to this common event, your application must have the ohos.permission.STORAGE_MANAGER permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_DISK_EJECT](arkts-basicservices-commoneventmanager-support-e.md#common_event_disk_eject)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED

```TypeScript
COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED = 'usual.event.data.VISIBLE_ACCOUNTS_UPDATED'
```

(reserved, not supported yet) Indicates that the account visibility changed.

To subscribe to this common event, your application must have the ohos.permission.GET_APP_ACCOUNTS permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED](arkts-basicservices-commoneventmanager-support-e.md#common_event_visible_accounts_updated)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ACCOUNT_DELETED

```TypeScript
COMMON_EVENT_ACCOUNT_DELETED = 'usual.event.data.ACCOUNT_DELETED'
```

(reserved, not supported yet) Indicates that an account was deleted.

To subscribe to this common event, your application must have the ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_ACCOUNT_DELETED](arkts-basicservices-commoneventmanager-support-e.md#common_event_account_deleted)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_FOUNDATION_READY

```TypeScript
COMMON_EVENT_FOUNDATION_READY = 'common.event.FOUNDATION_READY'
```

(reserved, not supported yet) Indicates that the foundation is ready.

To subscribe to this common event, your application must have the ohos.permission.RECEIVER_STARTUP_COMPLETED permission. (This permission is available only for system applications.)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_FOUNDATION_READY](arkts-basicservices-commoneventmanager-support-e.md#common_event_foundation_ready)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_AIRPLANE_MODE_CHANGED

```TypeScript
COMMON_EVENT_AIRPLANE_MODE_CHANGED = 'usual.event.AIRPLANE_MODE'
```

Indicates that the airplane mode of the device has changed.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_AIRPLANE_MODE_CHANGED](arkts-basicservices-commoneventmanager-support-e.md#common_event_airplane_mode_changed)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SPLIT_SCREEN

```TypeScript
COMMON_EVENT_SPLIT_SCREEN = 'common.event.SPLIT_SCREEN'
```

Indicates that the screen has been split.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [COMMON_EVENT_SPLIT_SCREEN](arkts-basicservices-commoneventmanager-support-e.md#common_event_split_screen)

**System capability:** SystemCapability.Notification.CommonEvent
