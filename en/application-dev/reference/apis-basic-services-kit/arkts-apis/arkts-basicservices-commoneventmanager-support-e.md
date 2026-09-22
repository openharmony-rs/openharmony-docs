# Support

```TypeScript
export enum Support
```

System common events are events published by system services or system apps. Subscribing to these common events requires specific permissions and event values.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BOOT_COMPLETED

```TypeScript
COMMON_EVENT_BOOT_COMPLETED = 'usual.event.BOOT_COMPLETED'
```

Indicates that the boot is complete and the system is loaded.

When the specified user finishes the boot process on the device, the common event service is triggered to publish this event.

To subscribe to this common event, your application must have the ohos.permission.RECEIVER_STARTUP_COMPLETED permission.(This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCKED_BOOT_COMPLETED

```TypeScript
COMMON_EVENT_LOCKED_BOOT_COMPLETED = 'usual.event.LOCKED_BOOT_COMPLETED'
```

(Reserved, not supported yet) Indicates that the guidance is complete and the system is loaded, but the screen is still locked.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SHUTDOWN

```TypeScript
COMMON_EVENT_SHUTDOWN = 'usual.event.SHUTDOWN'
```

Indicates that the device is being shut down and the final shutdown will proceed.

When the device is being shut down until it is powered off, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_CHANGED

```TypeScript
COMMON_EVENT_BATTERY_CHANGED = 'usual.event.BATTERY_CHANGED'
```

Indicates that the charging state, level, and other information about the battery have changed.

When any of the following information changes, the event notification service is triggered to publish this event: battery level, battery temperature, battery health status, type of the charger connected to the device, maximum current of the charger, maximum voltage of the charger, battery charging status, number of charging times, total battery capacity, remaining battery capacity, battery model, and battery charging type.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_LOW

```TypeScript
COMMON_EVENT_BATTERY_LOW = 'usual.event.BATTERY_LOW'
```

Indicates that the battery level is low.

When the battery level drops to lower than the low battery level set for the device, the event notification service is triggered to publish this event. <!--Del-->For details about how to set the low battery level percentage, see [Battery Level Customization](https://gitee.com/openharmony/docs/blob/master/en/device-dev/subsystems/subsys-power-battery-level-customization.md).<!--DelEnd-->

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BATTERY_OKAY

```TypeScript
COMMON_EVENT_BATTERY_OKAY = 'usual.event.BATTERY_OKAY'
```

Indicates that the battery level is normal.

When the battery level increases from a low level to a level higher than the low level, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_CONNECTED

```TypeScript
COMMON_EVENT_POWER_CONNECTED = 'usual.event.POWER_CONNECTED'
```

Indicates that the device is connected to an external power supply.

When the device connects to an external charger, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_DISCONNECTED

```TypeScript
COMMON_EVENT_POWER_DISCONNECTED = 'usual.event.POWER_DISCONNECTED'
```

Indicates that the device is disconnected from the external power supply.

When the device is disconnected from the external power supply, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_OFF

```TypeScript
COMMON_EVENT_SCREEN_OFF = 'usual.event.SCREEN_OFF'
```

Indicates that a device screen-off initiated by the power service is complete.

When the device screen-off initiated by the power service is complete, the event notification service is triggered to release this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_ON

```TypeScript
COMMON_EVENT_SCREEN_ON = 'usual.event.SCREEN_ON'
```

Indicates that a device screen-on initiated by the power service is complete.

When the device screen-on initiated by the power service is complete, the event notification service is triggered to release this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_THERMAL_LEVEL_CHANGED

```TypeScript
COMMON_EVENT_THERMAL_LEVEL_CHANGED = 'usual.event.THERMAL_LEVEL_CHANGED'
```

Indicates that the device's thermal level has changed.

When the device's thermal level changes, the event notification service is triggered to publish this event. <!-- Del-->For details about how to configure the device thermal level, see [Thermal Level Customization](https://gitee.com/openharmony/docs/blob/master/en/device-dev/subsystems/subsys-thermal_level.md).<!--DelEnd-->

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ENTER_FORCE_SLEEP

```TypeScript
COMMON_EVENT_ENTER_FORCE_SLEEP = 'usual.event.ENTER_FORCE_SLEEP'
```

Indicates that the device is about to enter the forced sleep mode.

When the device is about to enter the forced sleep mode, the event notification service is triggered to publish this event. This event should be processed within one second.

**Since:** 12

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXIT_FORCE_SLEEP

```TypeScript
COMMON_EVENT_EXIT_FORCE_SLEEP = 'usual.event.EXIT_FORCE_SLEEP'
```

Indicates that the device exits the forced sleep mode.

When the device exits the forced sleep mode, the event notification service is triggered to publish this event.

**Since:** 12

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ENTER_HIBERNATE

```TypeScript
COMMON_EVENT_ENTER_HIBERNATE = 'usual.event.ENTER_HIBERNATE'
```

Indicates that the device is about to enter the hibernation mode.

When the device is about to enter the hibernation mode, the event notification service is triggered to publish this event. This event should be processed within one second.

**Since:** 15

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXIT_HIBERNATE

```TypeScript
COMMON_EVENT_EXIT_HIBERNATE = 'usual.event.EXIT_HIBERNATE'
```

Indicates that the device exits the hibernation mode.

When the device exits the hibernation mode, the event notification service is triggered to publish this event.

**Since:** 15

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_PRESENT

```TypeScript
COMMON_EVENT_USER_PRESENT = 'usual.event.USER_PRESENT'
```

Indicates the action of a common event that the user unlocks the device.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [COMMON_EVENT_SCREEN_UNLOCKED](#common_event_screen_unlocked)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIME_TICK

```TypeScript
COMMON_EVENT_TIME_TICK = 'usual.event.TIME_TICK'
```

Indicates that the system time has changed.

When the system time in the unit of minute changes, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIME_CHANGED

```TypeScript
COMMON_EVENT_TIME_CHANGED = 'usual.event.TIME_CHANGED'
```

Indicates that the system time is set.

When the system time is set, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DATE_CHANGED

```TypeScript
COMMON_EVENT_DATE_CHANGED = 'usual.event.DATE_CHANGED'
```

(Reserved, not supported yet) Indicates that the system time has changed.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TIMEZONE_CHANGED

```TypeScript
COMMON_EVENT_TIMEZONE_CHANGED = 'usual.event.TIMEZONE_CHANGED'
```

Indicates that the system time zone has changed.

When the system time zone changes, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CLOSE_SYSTEM_DIALOGS

```TypeScript
COMMON_EVENT_CLOSE_SYSTEM_DIALOGS = 'usual.event.CLOSE_SYSTEM_DIALOGS'
```

(Reserved, not supported yet) Indicates that a user closes a temporary system dialog box.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_ADDED

```TypeScript
COMMON_EVENT_PACKAGE_ADDED = 'usual.event.PACKAGE_ADDED'
```

Indicates that a new application package has been installed on the device.

When a new application is installed by a specified user on the device, the event notification service is triggered to publish this event.

> **NOTE:** 
> 
> Third-party applications can only listen for the installation event of themselves.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_REPLACED

```TypeScript
COMMON_EVENT_PACKAGE_REPLACED = 'usual.event.PACKAGE_REPLACED'
```

(Reserved, not supported yet) Indicates the action of a common event that a new version of an installed application package has replaced the previous one on the device. Data contains the name of the package.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_REPLACED

```TypeScript
COMMON_EVENT_MY_PACKAGE_REPLACED = 'usual.event.MY_PACKAGE_REPLACED'
```

(Reserved, not supported yet) Indicates the action of a common event that a new version of an installed application package has replaced the previous one on the device. This event does not contain additional data and is sent only to the replaced application.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_REMOVED

```TypeScript
COMMON_EVENT_PACKAGE_REMOVED = 'usual.event.PACKAGE_REMOVED'
```

Indicates that an installed bundle has been uninstalled from the device.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BUNDLE_REMOVED

```TypeScript
COMMON_EVENT_BUNDLE_REMOVED = 'usual.event.BUNDLE_REMOVED'
```

(Reserved, not supported yet) Indicates that an installed bundle has been uninstalled from the device.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_FULLY_REMOVED

```TypeScript
COMMON_EVENT_PACKAGE_FULLY_REMOVED = 'usual.event.PACKAGE_FULLY_REMOVED'
```

Indicates that an installed application has been completely uninstalled from the device.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_CHANGED

```TypeScript
COMMON_EVENT_PACKAGE_CHANGED = 'usual.event.PACKAGE_CHANGED'
```

Indicates that an application package has been changed (for example, an ability in the package has been enabled or disabled).

When an application package installed on the device is updated or an ability in the package is enabled or disabled, the event notification service is triggered to publish this event.

> **NOTE:** 
> 
> Third-party applications can only listen for the change event of themselves.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_RESTARTED

```TypeScript
COMMON_EVENT_PACKAGE_RESTARTED = 'usual.event.PACKAGE_RESTARTED'
```

Indicates that the user has restarted the application package and killed all its processes.

When the specified user restarts the application and kills all its processes, the event notification service is triggered to publish this event.

> **NOTE:** 
> 
> Third-party applications can only listen for the restart event of themselves.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_DATA_CLEARED

```TypeScript
COMMON_EVENT_PACKAGE_DATA_CLEARED = 'usual.event.PACKAGE_DATA_CLEARED'
```

Indicates that the user has cleared the application package data.

When the specified user clears the application package data on the device, the event notification service is triggered to publish this event.

> **NOTE:** 
> 
> Third-party applications can only listen for the data clearance event of themselves.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_CACHE_CLEARED

```TypeScript
COMMON_EVENT_PACKAGE_CACHE_CLEARED = 'usual.event.PACKAGE_CACHE_CLEARED'
```

Indicates that the user cleared the application package cache.

When the cache of an application package installed on the device is cleared, the event notification service is triggered to publish this event.

> **NOTE:** 
> 
> Third-party applications can only listen for the cache clearance event of themselves.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGES_SUSPENDED

```TypeScript
COMMON_EVENT_PACKAGES_SUSPENDED = 'usual.event.PACKAGES_SUSPENDED'
```

(Reserved, not supported yet) Indicates that the package has been suspended.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGES_UNSUSPENDED

```TypeScript
COMMON_EVENT_PACKAGES_UNSUSPENDED = 'usual.event.PACKAGES_UNSUSPENDED'
```

(Reserved, not supported yet) Indicates that the package has been unsuspended.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_SUSPENDED

```TypeScript
COMMON_EVENT_MY_PACKAGE_SUSPENDED = 'usual.event.MY_PACKAGE_SUSPENDED'
```

(Reserved, not supported yet) Indicates that application packages have been suspended by the system.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MY_PACKAGE_UNSUSPENDED

```TypeScript
COMMON_EVENT_MY_PACKAGE_UNSUSPENDED = 'usual.event.MY_PACKAGE_UNSUSPENDED'
```

(Reserved, not supported yet) Indicates that application packages have been unsuspended by the system.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_UID_REMOVED

```TypeScript
COMMON_EVENT_UID_REMOVED = 'usual.event.UID_REMOVED'
```

(Reserved, not supported yet) Indicates that a user ID has been removed from the system.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_FIRST_LAUNCH

```TypeScript
COMMON_EVENT_PACKAGE_FIRST_LAUNCH = 'usual.event.PACKAGE_FIRST_LAUNCH'
```

(Reserved, not supported yet) Indicates an initial start of an application after installation.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION

```TypeScript
COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION = 'usual.event.PACKAGE_NEEDS_VERIFICATION'
```

(Reserved, not supported yet) Indicates that a package is sent by the system verifier when the package needs verification.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_PACKAGE_VERIFIED

```TypeScript
COMMON_EVENT_PACKAGE_VERIFIED = 'usual.event.PACKAGE_VERIFIED'
```

(Reserved, not supported yet) Indicates that a package is sent by the system verifier when the package is verified.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE

```TypeScript
COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_AVAILABLE'
```

(Reserved, not supported yet) Indicates that applications installed on the external storage become available for the system.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE

```TypeScript
COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE = 'usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE'
```

(Reserved, not supported yet) Indicates that applications installed on the external storage become unavailable for the system.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CONFIGURATION_CHANGED

```TypeScript
COMMON_EVENT_CONFIGURATION_CHANGED = 'usual.event.CONFIGURATION_CHANGED'
```

(Reserved, not supported yet) Indicates that the device state (for example, orientation and locale) has changed.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCALE_CHANGED

```TypeScript
COMMON_EVENT_LOCALE_CHANGED = 'usual.event.LOCALE_CHANGED'
```

Indicates that the system language is set.

When the system language is set, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MANAGE_PACKAGE_STORAGE

```TypeScript
COMMON_EVENT_MANAGE_PACKAGE_STORAGE = 'usual.event.MANAGE_PACKAGE_STORAGE'
```

Notifies the low memory state and package management should be started.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DRIVE_MODE

```TypeScript
COMMON_EVENT_DRIVE_MODE = 'common.event.DRIVE_MODE'
```

(Reserved, not supported yet) Indicates that the system is in driving mode.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HOME_MODE

```TypeScript
COMMON_EVENT_HOME_MODE = 'common.event.HOME_MODE'
```

(Reserved, not supported yet) Indicates that the system is in home mode.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_OFFICE_MODE

```TypeScript
COMMON_EVENT_OFFICE_MODE = 'common.event.OFFICE_MODE'
```

(Reserved, not supported yet) Indicates that the system is in office mode.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STARTED

```TypeScript
COMMON_EVENT_USER_STARTED = 'usual.event.USER_STARTED'
```

(Reserved, not supported yet) Indicates that the user has been started.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_BACKGROUND

```TypeScript
COMMON_EVENT_USER_BACKGROUND = 'usual.event.USER_BACKGROUND'
```

(Reserved, not supported yet) Indicates that the user has been brought to the background.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_FOREGROUND

```TypeScript
COMMON_EVENT_USER_FOREGROUND = 'usual.event.USER_FOREGROUND'
```

(Reserved, not supported yet) Indicates that the user has been brought to the foreground.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_SWITCHED

```TypeScript
COMMON_EVENT_USER_SWITCHED = 'usual.event.USER_SWITCHED'
```

Indicates that a user switchover is complete.

When a system account is switched, the common event service is triggered to publish this event carrying the system account ID.

The system API related to this common event is **activateOsAccount**. For details, see [@ohos.account.osAccount (System Account Management)](../../../reference/js-apis-osAccount.md).

To subscribe to this common event, your application must have the ohos.permission.MANAGE_LOCAL_ACCOUNTS permission (before API version 21); ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission (since API version 21).

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STARTING

```TypeScript
COMMON_EVENT_USER_STARTING = 'usual.event.USER_STARTING'
```

(Reserved, not supported yet) Indicates that the user is going to be started.

To subscribe to this common event, your application must have the **ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS** permission.(This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_UNLOCKED

```TypeScript
COMMON_EVENT_USER_UNLOCKED = 'usual.event.USER_UNLOCKED'
```

Indicates that the credential-encrypted storage has been unlocked for the current user after the device is restarted.

When the device is unlocked with the lock screen password the first time after user switching, the event notification service is triggered to publish this event carrying the system account ID that identifies the user.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STOPPING

```TypeScript
COMMON_EVENT_USER_STOPPING = 'usual.event.USER_STOPPING'
```

(Reserved, not supported yet) Indicates that the user is going to be stopped.

To subscribe to this common event, your application must have the **ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS** permission.(This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_STOPPED

```TypeScript
COMMON_EVENT_USER_STOPPED = 'usual.event.USER_STOPPED'
```

(Reserved, not supported yet) Indicates that the user has been stopped.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN = 'common.event.DISTRIBUTED_ACCOUNT_LOGIN'
```

Indicates a successful login from a distributed account.

When a distributed account is successfully logged in, the event notification service is triggered to publish this event carrying the OS account ID and the sub-profile ID.

APIs related to this event: **setOsAccountDistributedInfo** and **updateOsAccountDistributedInfo** (discarded), and **setOsAccountDistributedInfoByLocalId**. The first two are public APIs, and the last one is a system API. For details, see [@ohos.account.distributedAccount (Distributed Account Management)](../../../reference/js-apis-distributed-account.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT = 'common.event.DISTRIBUTED_ACCOUNT_LOGOUT'
```

Indicates a successful logout from a distributed account.

When a distributed account is successfully logged out, the event notification service is triggered to publish this event carrying the OS account ID and the sub-profile ID.

APIs related to this event: **setOsAccountDistributedInfo** and **updateOsAccountDistributedInfo** (discarded), and **setOsAccountDistributedInfoByLocalId**. The first two are public APIs, and the last one is a system API. For details, see [@ohos.account.distributedAccount (Distributed Account Management)](../../../reference/js-apis-distributed-account.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID = 'common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID'
```

Indicates that the token of a distributed account is invalid.

When the token of a distributed account is invalid, the event notification service is triggered to publish this event carrying the OS account ID and the sub-profile ID.

APIs related to this event: **setOsAccountDistributedInfo** and **updateOsAccountDistributedInfo** (discarded), and **setOsAccountDistributedInfoByLocalId**. The first two are public APIs, and the last one is a system API. For details, see [@ohos.account.distributedAccount (Distributed Account Management)](../../../reference/js-apis-distributed-account.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF = 'common.event.DISTRIBUTED_ACCOUNT_LOGOFF'
```

Indicates that a distributed account is deregistered.

When a distributed account is deregistered, the event notification service is triggered to publish this event carrying the OS account ID and the sub-profile ID.

APIs related to this event: **setOsAccountDistributedInfo** and **updateOsAccountDistributedInfo** (discarded), and **setOsAccountDistributedInfoByLocalId**. The first two are public APIs, and the last one is a system API. For details, see [@ohos.account.distributedAccount (Distributed Account Management)](../../../reference/js-apis-distributed-account.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_POWER_STATE

```TypeScript
COMMON_EVENT_WIFI_POWER_STATE = 'usual.event.wifi.POWER_STATE'
```

Indicates that the Wi-Fi state changes.

When the Wi-Fi state changes (such as enabled or disabled), the event notification service is triggered to release the system public event.

State values: **0** indicates that the Wi-Fi is being disabling; **1** indicates that the Wi-Fi has been disabled; **2** indicates that the Wi-Fi is being enabled; **3** indicates that the Wi-Fi has been enabled.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_SCAN_FINISHED

```TypeScript
COMMON_EVENT_WIFI_SCAN_FINISHED = 'usual.event.wifi.SCAN_FINISHED'
```

Indicates that a Wi-Fi access point is detected and proven to be available.

When a Wi-Fi access point is detected and proven to be available, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.LOCATION** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_RSSI_VALUE

```TypeScript
COMMON_EVENT_WIFI_RSSI_VALUE = 'usual.event.wifi.RSSI_VALUE'
```

Indicates that the Wi-Fi signal strength (RSSI) has changed.

When the Wi-Fi signal strength (RSSI) changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.GET_WIFI_INFO** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_CONN_STATE

```TypeScript
COMMON_EVENT_WIFI_CONN_STATE = 'usual.event.wifi.CONN_STATE'
```

Indicates that the Wi-Fi connection state has changed.

When the Wi-Fi connection state changes, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_HOTSPOT_STATE

```TypeScript
COMMON_EVENT_WIFI_HOTSPOT_STATE = 'usual.event.wifi.HOTSPOT_STATE'
```

Indicates that the Wi-Fi hotspot state has changed.

When the Wi-Fi hotspot state changes, the event notification service is triggered to publish this event.

State values: **2** indicates that the AP is being enabled, **3** indicates that the AP has been enabled; **4** indicates that the AP is being disabled; **5** indicates that the AP has been disabled.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_AP_STA_JOIN

```TypeScript
COMMON_EVENT_WIFI_AP_STA_JOIN = 'usual.event.wifi.WIFI_HS_STA_JOIN'
```

Indicates that a client has joined the Wi-Fi hotspot of the current device.

When a client joins the Wi-Fi hotspot of the current device, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.GET_WIFI_INFO** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_AP_STA_LEAVE

```TypeScript
COMMON_EVENT_WIFI_AP_STA_LEAVE = 'usual.event.wifi.WIFI_HS_STA_LEAVE'
```

Indicates that the client is disconnected from the Wi-Fi hotspot of the current device.

When a client is disconnected from the Wi-Fi hotspot of the current device, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.GET_WIFI_INFO** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE

```TypeScript
COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE = 'usual.event.wifi.mplink.STATE_CHANGE'
```

Indicates that the state of MPLINK (an enhanced Wi-Fi feature) has changed.

When the state of MPLINK changes, the event notification service is triggered to publish this event (not supported yet).

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_CONN_STATE

```TypeScript
COMMON_EVENT_WIFI_P2P_CONN_STATE = 'usual.event.wifi.p2p.CONN_STATE_CHANGE'
```

Indicates that the Wi-Fi P2P connection state has changed.

When the Wi-Fi P2P connection state changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.GET_WIFI_INFO** and **ohos.permission.LOCATION** permissions.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_STATE_CHANGED = 'usual.event.wifi.p2p.STATE_CHANGE'
```

Indicates that the Wi-Fi P2P state has changed.

When the Wi-Fi P2P state changes, the event notification service is triggered to publish this event.

State values: **2** indicates that the P2P is being enabled, **3** indicates that the P2P has been enabled; **4** indicates that the P2P is being disabled; **5** indicates that the P2P has been disabled.

To subscribe to this common event, your application must have the **ohos.permission.GET_WIFI_INFO** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED = 'usual.event.wifi.p2p.DEVICES_CHANGE'
```

Indicates that the state of the Wi-Fi P2P peer device has changed.

When the state of the Wi-Fi P2P peer device changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.GET_WIFI_INFO** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED = 'usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE'
```

Indicates that the Wi-Fi P2P discovery state has changed.

When the Wi-Fi P2P discovery state changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.GET_WIFI_INFO** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED = 'usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE'
```

Indicates that the state of the Wi-Fi P2P local device has changed.

When the state of the Wi-Fi P2P local device changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.GET_WIFI_INFO** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED

```TypeScript
COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED = 'usual.event.wifi.p2p.GROUP_STATE_CHANGED'
```

Indicates that the Wi-Fi P2P group information has changed.

When the Wi-Fi P2P group information changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.GET_WIFI_INFO** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE'
```

(Reserved, not supported yet) Indicates the common event about the connection state of Bluetooth handsfree communication.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_CHANGE](#common_event_bluetooth_handsfree_ag_connect_state_change)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE'
```

(Reserved, not supported yet) Indicates that the device connected to the Bluetooth handsfree is active.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE'
```

(Reserved, not supported yet) Indicates that the connection state of Bluetooth A2DP has changed.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE'
```

(Reserved, not supported yet) Indicates the common event about the connection state of Bluetooth A2DP.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_CHANGE](#common_event_bluetooth_a2dpsource_connect_state_change)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE'
```

(Reserved, not supported yet) Indicates that the device connected using Bluetooth A2DP is active.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE'
```

(Reserved, not supported yet) Indicates that the playing state of Bluetooth A2DP has changed.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE'
```

(Reserved, not supported yet) Indicates that the AVRCP connection state of Bluetooth A2DP has changed.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_CHANGE](#common_event_bluetooth_a2dpsource_avrcp_connect_state_change)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE =
        'usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE'
```

(Reserved, not supported yet) Indicates that the audio codec state of Bluetooth A2DP has changed.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_CHANGE](#common_event_bluetooth_a2dpsource_codec_value_change)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED =
        'usual.event.bluetooth.remotedevice.DISCOVERED'
```

(Reserved, not supported yet) Indicates that a remote Bluetooth device is discovered.

To subscribe to this common event, your application must have the **ohos.permission.LOCATION** and **ohos.permission.USE_BLUETOOTH** permissions.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE =
        'usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE'
```

(Reserved, not supported yet) Indicates that the Bluetooth class of a remote Bluetooth device has changed.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED =
        'usual.event.bluetooth.remotedevice.ACL_CONNECTED'
```

(Reserved, not supported yet) Indicates that a low-ACL connection has been established with a remote Bluetooth device.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE](#common_event_bluetooth_remotedevice_acl_state_change)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED =
        'usual.event.bluetooth.remotedevice.ACL_DISCONNECTED'
```

(Reserved, not supported yet) Indicates that a low-ACL connection has been disconnected from a remote Bluetooth device.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE](#common_event_bluetooth_remotedevice_acl_state_change)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE =
        'usual.event.bluetooth.remotedevice.NAME_UPDATE'
```

(Reserved, not supported yet) Indicates that the friendly name of a remote Bluetooth device is retrieved for the first time or has changed since the last retrieval.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE =
        'usual.event.bluetooth.remotedevice.PAIR_STATE'
```

(Reserved, not supported yet) Indicates that the connection state of a remote Bluetooth device has changed.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE_CHANGE](#common_event_bluetooth_remotedevice_pair_state_change)

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE =
        'usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE'
```

(Reserved, not supported yet) Indicates that the battery level of a remote Bluetooth device is retrieved for the first time or has changed since the last retrieval.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT =
        'usual.event.bluetooth.remotedevice.SDP_RESULT'
```

(Reserved, not supported yet) Indicates the common event about the SDP state of a remote Bluetooth device.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE =
        'usual.event.bluetooth.remotedevice.UUID_VALUE'
```

Indicates the action of a common event about the UUID connection state of a remote Bluetooth device.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ =
        'usual.event.bluetooth.remotedevice.PAIRING_REQ'
```

(Reserved, not supported yet) Indicates the common event about the pairing request from a remote Bluetooth device.

To subscribe to this common event, your application must have the **ohos.permission.DISCOVER_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL =
        'usual.event.bluetooth.remotedevice.PAIRING_CANCEL'
```

(Reserved, not supported yet) Indicates that Bluetooth pairing is canceled.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ =
        'usual.event.bluetooth.remotedevice.CONNECT_REQ'
```

(Reserved, not supported yet) Indicates the common event about the connection request from a remote Bluetooth device.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY =
        'usual.event.bluetooth.remotedevice.CONNECT_REPLY'
```

(Reserved, not supported yet) Indicates the common event about the response to the connection request from a remote Bluetooth device.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL =
        'usual.event.bluetooth.remotedevice.CONNECT_CANCEL'
```

(Reserved, not supported yet) Indicates that the connection to a remote Bluetooth device has been canceled.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE'
```

(Reserved, not supported yet) Indicates that the connection state of a Bluetooth handsfree has changed.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE'
```

(Reserved, not supported yet) Indicates that the audio state of a Bluetooth handsfree has changed.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT =
        'usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT'
```

(Reserved, not supported yet) Indicates that the audio gateway state of a Bluetooth handsfree has changed.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE =
        'usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE'
```

(Reserved, not supported yet) Indicates that the calling state of a Bluetooth handsfree has changed.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE =
        'usual.event.bluetooth.host.STATE_UPDATE'
```

Indicates that the state of a Bluetooth adapter has been changed, for example, Bluetooth has been enabled or disabled.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE =
        'usual.event.bluetooth.host.REQ_DISCOVERABLE'
```

(Reserved, not supported yet) Indicates the common event about the request for the user to allow Bluetooth device scanning.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE = 'usual.event.bluetooth.host.REQ_ENABLE'
```

(Reserved, not supported yet) Indicates the common event about the request for the user to enable Bluetooth.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE =
        'usual.event.bluetooth.host.REQ_DISABLE'
```

(Reserved, not supported yet) Indicates the common event about the request for the user to disable Bluetooth.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE =
        'usual.event.bluetooth.host.SCAN_MODE_UPDATE'
```

(Reserved, not supported yet) Indicates that the Bluetooth scanning mode of a device has changed.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_CHANGE =
        'usual.event.bluetooth.host.SCAN_MODE_CHANGE'
```

Indicates that the Bluetooth scanning mode changes.

When the Bluetooth scanning mode changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 23

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED =
        'usual.event.bluetooth.host.DISCOVERY_STARTED'
```

Indicates that the Bluetooth scanning has been started on the device.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED =
        'usual.event.bluetooth.host.DISCOVERY_FINISHED'
```

Indicates that the Bluetooth scanning is finished on the device.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE =
        'usual.event.bluetooth.host.NAME_UPDATE'
```

Indicates that the Bluetooth adapter name of the device has changed.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE'
```

(Reserved, not supported yet) Indicates that the connection state of Bluetooth A2DP has changed.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE'
```

(Reserved, not supported yet) Indicates that the playing state of Bluetooth A2DP has changed.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE =
        'usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE'
```

(Reserved, not supported yet) Indicates that the audio state of Bluetooth A2DP Sink has changed.

To subscribe to this common event, your application must have the **ohos.permission.USE_BLUETOOTH** permission.

**Since:** 9

**Deprecated since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED

```TypeScript
COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED = 'usual.event.nfc.action.ADAPTER_STATE_CHANGED'
```

Indicates that the state of the device NFC adapter has changed.

When the state of the device NFC adapter changes, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED

```TypeScript
COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED = 'usual.event.nfc.action.RF_FIELD_ON_DETECTED'
```

Indicates that the NFC RF field is on.

When the NFC RF field becomes available, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED

```TypeScript
COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED = 'usual.event.nfc.action.RF_FIELD_OFF_DETECTED'
```

Indicates that the NFC RF field is off.

When the NFC RF field becomes unavailable, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISCHARGING

```TypeScript
COMMON_EVENT_DISCHARGING = 'usual.event.DISCHARGING'
```

Indicates that the system stops charging the battery.

When the system stops charging the battery, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CHARGING

```TypeScript
COMMON_EVENT_CHARGING = 'usual.event.CHARGING'
```

Indicates that the system starts charging the battery.

When the system starts charging the battery, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED

```TypeScript
COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED = 'usual.event.DEVICE_IDLE_MODE_CHANGED'
```

Indicates that the system idle mode has changed.

When the user does not use the device for the specified period of time and the screen is turned off, the system delays the CPU and network access by background applications, and the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED

```TypeScript
COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED = 'usual.event.CHARGE_IDLE_MODE_CHANGED'
```

Indicates that the device enters the charging idle mode.

When the device starts charging in idle mode, and the temperature rise is acceptable, the event notification service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_POWER_SAVE_MODE_CHANGED

```TypeScript
COMMON_EVENT_POWER_SAVE_MODE_CHANGED = 'usual.event.POWER_SAVE_MODE_CHANGED'
```

Indicates that the system power-saving mode has changed.

When the system power saving mode changes, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_ADDED

```TypeScript
COMMON_EVENT_USER_ADDED = 'usual.event.USER_ADDED'
```

Indicates that a user has been added to the system.

When a system account is created, the common event service is triggered to publish this event carrying the system account ID.

The system APIs related to this common event are **createOsAccount** and **createOsAccountForDomain**. For details, see [@ohos.account.osAccount (System Account Management)](../../../reference/js-apis-osAccount.md).

To subscribe to this common event, your application must have the ohos.permission.MANAGE_LOCAL_ACCOUNTS permission.(This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_REMOVED

```TypeScript
COMMON_EVENT_USER_REMOVED = 'usual.event.USER_REMOVED'
```

Indicates that a user has been removed from the system.

When a system account is removed, the common event service is triggered to publish this event carrying the system account ID.

The system API related to this common event is **removeOsAccount**. For details, see [@ohos.account.osAccount (System Account Management)](../../../reference/js-apis-osAccount.md).

To subscribe to this common event, your application must have the ohos.permission.MANAGE_LOCAL_ACCOUNTS permission.(This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_ADDED

```TypeScript
COMMON_EVENT_ABILITY_ADDED = 'common.event.ABILITY_ADDED'
```

(Reserved, not supported yet) Indicates that an ability has been added.

To subscribe to this common event, your application must have the **ohos.permission.LISTEN_BUNDLE_CHANGE** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_REMOVED

```TypeScript
COMMON_EVENT_ABILITY_REMOVED = 'common.event.ABILITY_REMOVED'
```

(Reserved, not supported yet) Indicates that an ability has been removed.

To subscribe to this common event, your application must have the **ohos.permission.LISTEN_BUNDLE_CHANGE** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ABILITY_UPDATED

```TypeScript
COMMON_EVENT_ABILITY_UPDATED = 'common.event.ABILITY_UPDATED'
```

(Reserved, not supported yet) Indicates that an ability has been updated.

To subscribe to this common event, your application must have the **ohos.permission.LISTEN_BUNDLE_CHANGE** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LOCATION_MODE_STATE_CHANGED

```TypeScript
COMMON_EVENT_LOCATION_MODE_STATE_CHANGED = 'usual.event.location.MODE_STATE_CHANGED'
```

(Reserved, not supported yet) Indicates that the location mode of the system has changed.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_SLEEP

```TypeScript
COMMON_EVENT_IVI_SLEEP = 'common.event.IVI_SLEEP'
```

(Reserved, not supported yet) Indicates that the in-vehicle infotainment (IVI) system of a vehicle is sleeping.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_PAUSE

```TypeScript
COMMON_EVENT_IVI_PAUSE = 'common.event.IVI_PAUSE'
```

(Reserved, not supported yet) Indicates that the IVI system of a vehicle has entered sleep mode and the playing application is instructed to stop playback.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_STANDBY

```TypeScript
COMMON_EVENT_IVI_STANDBY = 'common.event.IVI_STANDBY'
```

(Reserved, not supported yet) Indicates that a third-party application is instructed to pause the current work.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_LASTMODE_SAVE

```TypeScript
COMMON_EVENT_IVI_LASTMODE_SAVE = 'common.event.IVI_LASTMODE_SAVE'
```

(Reserved, not supported yet) Indicates that a third-party application is instructed to save its last mode.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_VOLTAGE_ABNORMAL

```TypeScript
COMMON_EVENT_IVI_VOLTAGE_ABNORMAL = 'common.event.IVI_VOLTAGE_ABNORMAL'
```

(Reserved, not supported yet) Indicates that the voltage of the vehicle's power system is abnormal.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_HIGH_TEMPERATURE

```TypeScript
COMMON_EVENT_IVI_HIGH_TEMPERATURE = 'common.event.IVI_HIGH_TEMPERATURE'
```

(Reserved, not supported yet) Indicates that the temperature of the IVI system is high.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_EXTREME_TEMPERATURE

```TypeScript
COMMON_EVENT_IVI_EXTREME_TEMPERATURE = 'common.event.IVI_EXTREME_TEMPERATURE'
```

(Reserved, not supported yet) Indicates that the temperature of the IVI system is extremely high.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL

```TypeScript
COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL = 'common.event.IVI_TEMPERATURE_ABNORMAL'
```

(Reserved, not supported yet) Indicates that the IVI system has an extreme temperature.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_VOLTAGE_RECOVERY

```TypeScript
COMMON_EVENT_IVI_VOLTAGE_RECOVERY = 'common.event.IVI_VOLTAGE_RECOVERY'
```

(Reserved, not supported yet) Indicates that the voltage of the vehicle's power system is restored to normal.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_TEMPERATURE_RECOVERY

```TypeScript
COMMON_EVENT_IVI_TEMPERATURE_RECOVERY = 'common.event.IVI_TEMPERATURE_RECOVERY'
```

(Reserved, not supported yet) Indicates that the temperature of the IVI system is restored to normal.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_IVI_ACTIVE

```TypeScript
COMMON_EVENT_IVI_ACTIVE = 'common.event.IVI_ACTIVE'
```

(Reserved, not supported yet) Indicates that the battery service is active.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_STATE

```TypeScript
COMMON_EVENT_USB_STATE = 'usual.event.hardware.usb.action.USB_STATE'
```

Indicates that the USB device state has changed.

When a USB device is connected to or disconnected from the device, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_PORT_CHANGED

```TypeScript
COMMON_EVENT_USB_PORT_CHANGED = 'usual.event.hardware.usb.action.USB_PORT_CHANGED'
```

Indicates that the USB port state of the device has changed.

When the USB port state changes, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_DEVICE_ATTACHED

```TypeScript
COMMON_EVENT_USB_DEVICE_ATTACHED = 'usual.event.hardware.usb.action.USB_DEVICE_ATTACHED'
```

Indicates that a USB device has been attached to the device functioning as a USB host.

When a USB device is attached, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_DEVICE_DETACHED

```TypeScript
COMMON_EVENT_USB_DEVICE_DETACHED = 'usual.event.hardware.usb.action.USB_DEVICE_DETACHED'
```

Indicates that a USB device has been detached from the device functioning as a USB host.

When a USB device is detached, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_ACCESSORY_ATTACHED

```TypeScript
COMMON_EVENT_USB_ACCESSORY_ATTACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED'
```

Indicates that a USB accessory has been attached.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USB_ACCESSORY_DETACHED

```TypeScript
COMMON_EVENT_USB_ACCESSORY_DETACHED = 'usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED'
```

Indicates that a USB accessory has been detached.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_REMOVED

```TypeScript
COMMON_EVENT_DISK_REMOVED = 'usual.event.data.DISK_REMOVED'
```

(Reserved, not supported yet) Indicates that an external storage device was removed.

To subscribe to this common event, your application must have the **ohos.permission.STORAGE_MANAGER** permission. (This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_UNMOUNTED

```TypeScript
COMMON_EVENT_DISK_UNMOUNTED = 'usual.event.data.DISK_UNMOUNTED'
```

(Reserved, not supported yet) Indicates that an external storage device was unmounted.

To subscribe to this common event, your application must have the **ohos.permission.STORAGE_MANAGER** permission. (This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_MOUNTED

```TypeScript
COMMON_EVENT_DISK_MOUNTED = 'usual.event.data.DISK_MOUNTED'
```

(Reserved, not supported yet) Indicates that an external storage device was mounted.

To subscribe to this common event, your application must have the **ohos.permission.STORAGE_MANAGER** permission. (This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_BAD_REMOVAL

```TypeScript
COMMON_EVENT_DISK_BAD_REMOVAL = 'usual.event.data.DISK_BAD_REMOVAL'
```

(Reserved, not supported yet) Indicates that an external storage device was removed without being unmounted.

To subscribe to this common event, your application must have the **ohos.permission.STORAGE_MANAGER** permission. (This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_UNMOUNTABLE

```TypeScript
COMMON_EVENT_DISK_UNMOUNTABLE = 'usual.event.data.DISK_UNMOUNTABLE'
```

(Reserved, not supported yet) Indicates that an external storage device becomes unmountable.

To subscribe to this common event, your application must have the **ohos.permission.STORAGE_MANAGER** permission. (This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DISK_EJECT

```TypeScript
COMMON_EVENT_DISK_EJECT = 'usual.event.data.DISK_EJECT'
```

(Reserved, not supported yet) Indicates that an external storage device was ejected.

To subscribe to this common event, your application must have the **ohos.permission.STORAGE_MANAGER** permission. (This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_REMOVED

```TypeScript
COMMON_EVENT_VOLUME_REMOVED = 'usual.event.data.VOLUME_REMOVED'
```

Indicates that an external storage device was removed.

This common event is triggered when an external storage device is removed.

To subscribe to this common event, your application must have the ohos.permission.STORAGE_MANAGER permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_UNMOUNTED

```TypeScript
COMMON_EVENT_VOLUME_UNMOUNTED = 'usual.event.data.VOLUME_UNMOUNTED'
```

Indicates that an external storage device was unmounted.

This common event is triggered when an external storage device is successfully unmounted by calling the **unmount** API or by removing the device.

To subscribe to this common event, your application must have the ohos.permission.STORAGE_MANAGER permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_MOUNTED

```TypeScript
COMMON_EVENT_VOLUME_MOUNTED = 'usual.event.data.VOLUME_MOUNTED'
```

Indicates that an external storage device was mounted.

This common event is triggered when an external storage device is successfully mounted by calling the **mount** API or by inserting the device.

To subscribe to this common event, your application must have the ohos.permission.STORAGE_MANAGER permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_BAD_REMOVAL

```TypeScript
COMMON_EVENT_VOLUME_BAD_REMOVAL = 'usual.event.data.VOLUME_BAD_REMOVAL'
```

Indicates that an external storage device was removed without being unmounted.

This common event is triggered when an external storage device is directly removed without being unmounted.

To subscribe to this common event, your application must have the ohos.permission.STORAGE_MANAGER permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_EJECT

```TypeScript
COMMON_EVENT_VOLUME_EJECT = 'usual.event.data.VOLUME_EJECT'
```

Indicates that an external storage device is about to be ejected.

This common event is triggered when the user calls the **unmount** API on a mounted external storage device or removes the device.

To subscribe to this common event, your application must have the ohos.permission.STORAGE_MANAGER permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED

```TypeScript
COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED = 'usual.event.data.VISIBLE_ACCOUNTS_UPDATED'
```

(Reserved, not supported yet) Indicates that the account visibility changed.

To subscribe to this common event, your application must have the **ohos.permission.GET_APP_ACCOUNTS** permission.(This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_ACCOUNT_DELETED

```TypeScript
COMMON_EVENT_ACCOUNT_DELETED = 'usual.event.data.ACCOUNT_DELETED'
```

(Reserved, not supported yet) Indicates that the account was deleted.

To subscribe to this common event, your application must have the **ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS** permission.(This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_FOUNDATION_READY

```TypeScript
COMMON_EVENT_FOUNDATION_READY = 'common.event.FOUNDATION_READY'
```

(Reserved, not supported yet) Indicates that the foundation is ready.

To subscribe to this common event, your application must have the **ohos.permission.RECEIVER_STARTUP_COMPLETED** permission.(This permission is available only for system applications.)

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_AIRPLANE_MODE_CHANGED

```TypeScript
COMMON_EVENT_AIRPLANE_MODE_CHANGED = 'usual.event.AIRPLANE_MODE'
```

Indicates that the airplane mode state has changed.

When the airplane mode is enabled or disabled, the event notification service is triggered to publish this event.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SPLIT_SCREEN

```TypeScript
COMMON_EVENT_SPLIT_SCREEN = 'common.event.SPLIT_SCREEN'
```

Indicates a screen splitting action.

When any of the following actions is performed, the event notification service is triggered to publish this event: accessing the recent tasks screen, creating a split-screen bar, and destroying a split-screen bar.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SLOT_CHANGE

```TypeScript
COMMON_EVENT_SLOT_CHANGE = 'usual.event.SLOT_CHANGE'
```

Indicates that the notification slot or notification switch settings have changed.

When the notification slot settings (including the switch) change or the notification feature is enabled or disabled, the notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.NOTIFICATION_CONTROLLER** permission.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SPN_INFO_CHANGED

```TypeScript
COMMON_EVENT_SPN_INFO_CHANGED = 'usual.event.SPN_INFO_CHANGED'
```

Indicates that the SPN information had changed.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_QUICK_FIX_APPLY_RESULT

```TypeScript
COMMON_EVENT_QUICK_FIX_APPLY_RESULT = 'usual.event.QUICK_FIX_APPLY_RESULT'
```

Indicates the result of applying a quick fix to the application.

When the specified user applies a quick fix to the application on the device, the event notification service is triggered to publish this event.

> **NOTE:** 
> 
> Third-party applications can only listen for the quick fix event of themselves.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_QUICK_FIX_REVOKE_RESULT

```TypeScript
COMMON_EVENT_QUICK_FIX_REVOKE_RESULT = 'usual.event.QUICK_FIX_REVOKE_RESULT'
```

Indicates the result of revoking a quick fix to the application.

When a quick fix to the application is revoked on the device, the event notification service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_INFO_UPDATED

```TypeScript
COMMON_EVENT_USER_INFO_UPDATED = 'usual.event.USER_INFO_UPDATED'
```

Indicates that the user information has been updated.

When the distributed account information, system account profile picture, or system account name is changed, the event notification service is triggered to publish this event carrying the system account ID.

APIs related to this event: **setOsAccountName**, **setOsAccountProfilePhoto**, and **setOsAccountDistributedInfo**. The first two are system APIs, and the last is a public API. For details, see [@ohos.account.osAccount (System Account Management)](../../../reference/js-apis-osAccount.md) and [@ohos.account.distributedAccount (Distributed Account Management)](../../../reference/js-apis-distributed-account.md).

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_HTTP_PROXY_CHANGE

```TypeScript
COMMON_EVENT_HTTP_PROXY_CHANGE = 'usual.event.HTTP_PROXY_CHANGE'
```

Indicates that the HTTP proxy configuration has changed.

When the configuration information of the system global proxy or HTTP proxy on various networks (such as Ethernet, Wi-Fi, and cellular networks) changes, the event notification service is triggered to release the system common event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SIM_STATE_CHANGED

```TypeScript
COMMON_EVENT_SIM_STATE_CHANGED = 'usual.event.SIM_STATE_CHANGED'
```

Indicates that the SIM card status has changed.

When there is a change in the SIM card status of the device, the event notification service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CALL_STATE_CHANGED

```TypeScript
COMMON_EVENT_CALL_STATE_CHANGED = 'usual.event.CALL_STATE_CHANGED'
```

Indicates that the call state has been updated.

When the call state of the device is updated, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.GET_TELEPHONY_STATE** permission.(This permission is available only for system applications.)

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_NETWORK_STATE_CHANGED

```TypeScript
COMMON_EVENT_NETWORK_STATE_CHANGED = 'usual.event.NETWORK_STATE_CHANGED'
```

Indicates that the network state has been updated.

When the network state of the device is updated, the event notification service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SIGNAL_INFO_CHANGED

```TypeScript
COMMON_EVENT_SIGNAL_INFO_CHANGED = 'usual.event.SIGNAL_INFO_CHANGED'
```

Indicates that the signal information has been updated.

When the signal information of the device is updated, the event notification service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_UNLOCKED

```TypeScript
COMMON_EVENT_SCREEN_UNLOCKED = 'usual.event.SCREEN_UNLOCKED'
```

Indicates that the screen has been unlocked.

When the screen is unlocked, the event notification service is triggered to publish this event.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SCREEN_LOCKED

```TypeScript
COMMON_EVENT_SCREEN_LOCKED = 'usual.event.SCREEN_LOCKED'
```

Indicates that the screen has been locked.

When the screen is locked, the event notification service is triggered to publish this event.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_CONNECTIVITY_CHANGE

```TypeScript
COMMON_EVENT_CONNECTIVITY_CHANGE = 'usual.event.CONNECTIVITY_CHANGE'
```

Indicates that the network connection state has changed.

When the (Ethernet, Wi-Fi, or cellular) network connection state changes (disconnected, connecting, or connected), the event notification service is triggered to publish this event.

The following table lists the enum values and their corresponding connection status.

> **NOTE:** 
> The following table lists the enum values and their corresponding connection status
> 
> | Value | Connection State |
> | ------ | ---------- |
> | 2 | Connecting. |
> | 3 | Connected. |
> | 4 | Disconnecting.|
> | 5 | Disconnected. |.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.handsfree.ag.CONNECT_STATE_CHANGE'
```

Indicates that the Bluetooth HFP AG connection state changes.

When the Bluetooth HFP AG connection state changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MINORSMODE_ON

```TypeScript
COMMON_EVENT_MINORSMODE_ON = 'usual.event.MINORSMODE_ON'
```

Indicates that the minor mode is enabled.

When the minor mode is enabled on the device, the event notification service is triggered to publish this event.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MINORSMODE_OFF

```TypeScript
COMMON_EVENT_MINORSMODE_OFF = 'usual.event.MINORSMODE_OFF'
```

Indicates that the minor mode is disabled.

When the minor mode is disabled on the device, the event notification service is triggered to publish this event.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_DATA_SHARE_READY

```TypeScript
COMMON_EVENT_DATA_SHARE_READY = 'usual.event.DATA_SHARE_READY'
```

Indicates that the DataShare service is available.

After the DataShare service is started, the event notification service is triggered to publish this event.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.CONNECT_STATE_CHANGE'
```

Indicates that the Bluetooth A2DP source connection state changes.

When the Bluetooth A2DP source connection state changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_CHANGE'
```

Indicates that the Bluetooth AVRCP connection state changes.

When the Bluetooth AVRCP connection state changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_CHANGE =
        'usual.event.bluetooth.a2dpsource.CODEC_VALUE_CHANGE'
```

Indicates that the Bluetooth media codec changes.

When the Bluetooth media codec changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAY_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAY_STATE_CHANGE =
        'usual.event.bluetooth.a2dpsource.PLAY_STATE_CHANGE'
```

Indicates that the Bluetooth A2DP playback state changes.

When the Bluetooth A2DP playback state changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_SCO_CONNECT_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_SCO_CONNECT_STATE_CHANGE = 
        'usual.event.bluetooth.SCO_CONNECT_STATE_CHANGE'
```

Indicates that the Bluetooth SCO state changes.

When the Bluetooth SCO state changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE = 
        'usual.event.bluetooth.remotedevice.ACL_STATE_CHANGE'
```

Indicates that the Bluetooth ACL connection state changes.

When the Bluetooth ACL connection state changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE_CHANGE

```TypeScript
COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE_CHANGE =
        'usual.event.bluetooth.remotedevice.PAIR_STATE_CHANGE'
```

Indicates that the Bluetooth pairing state changes.

When the Bluetooth pairing state changes, the event notification service is triggered to publish this event.

To subscribe to this common event, your application must have the **ohos.permission.ACCESS_BLUETOOTH** permission.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED

```TypeScript
COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED = 'usual.event.MANAGED_BROWSER_POLICY_CHANGED'
```

Indicates that the browser hosting policy has been changed.

When the browser hosting policy changes, the event notification service is triggered to publish this system common event.

**Since:** 15

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_KIOSK_MODE_ON

```TypeScript
COMMON_EVENT_KIOSK_MODE_ON = 'usual.event.KIOSK_MODE_ON'
```

Indicates that the kiosk mode is enabled. When this mode is on, the common event service is triggered to publish this system common event.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_KIOSK_MODE_OFF

```TypeScript
COMMON_EVENT_KIOSK_MODE_OFF = 'usual.event.KIOSK_MODE_OFF'
```

Indicates that the kiosk mode is disabled. When this mode is off, the common event service is triggered to publish this system common event.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_TABLET_MODE_CHANGED

```TypeScript
COMMON_EVENT_TABLET_MODE_CHANGED = 'usual.event.TABLET_MODE_CHANGED'
```

Indicates that the tablet mode of a device (such as a tablet with bracket) has been changed.

When the tablet mode of a device has been changed, the event notification service is triggered to publish this event.

**Since:** 23

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_DECRYPTED

```TypeScript
COMMON_EVENT_VOLUME_DECRYPTED = 'usual.event.VOLUME_DECRYPTED'
```

This common event indicates that specific volumes on the device have been decrypted.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_ENCRYPTED

```TypeScript
COMMON_EVENT_VOLUME_ENCRYPTED = 'usual.event.VOLUME_ENCRYPTED'
```

This common event indicates that specific volumes on the device have been encrypted.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_VOLUME_ENCRYPTION_POLICY_SET

```TypeScript
COMMON_EVENT_VOLUME_ENCRYPTION_POLICY_SET = 'usual.event.VOLUME_ENCRYPTION_POLICY_SET'
```

This common event indicates that specific volumes on the device have had their encryption policy set.

To subscribe to this common event, your application must have the ohos.permission.QUERY_VOLUME_ENCRYPTION_STATUS permission.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_SKILL_CHANGED

```TypeScript
COMMON_EVENT_SKILL_CHANGED = 'usual.event.SKILL_CHANGED'
```

This common event indicates that the skill information of an application has been changed.

To receive this common event, your application must have the ohos.permission.MANAGE_SKILL_PRIVILEGE permission.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_LID_STATE_CHANGED

```TypeScript
COMMON_EVENT_LID_STATE_CHANGED = 'usual.event.LID_STATE_CHANGED'
```

Indicates that the lid state of a device (such as a laptop) has been changed.

When the lid state of a device has been changed, the event notification service is triggered to publish this event.

**Since:** 23

**System capability:** SystemCapability.Notification.CommonEvent
