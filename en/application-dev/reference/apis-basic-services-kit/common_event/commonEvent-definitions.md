# System Common Events (To Be Deprecated Soon)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @peixu-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

This document provides indexes for predefined system common events.

Common event types are defined in [Support enumeration of the ohos.commonEvent module](../js-apis-commonEvent.md#support).

**System capability**: SystemCapability.Notification.CommonEvent

* **COMMON_EVENT_BOOT_COMPLETED<sup>(deprecated)</sup>** indicates that the boot is complete and the system is loaded.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use **COMMON_EVENT_BOOT_COMPLETED** instead.

  - Value: **usual.event.BOOT_COMPLETED**
  - Required permissions: **ohos.permission.RECEIVER_STARTUP_COMPLETED** (for system applications only)

* **COMMON_EVENT_LOCKED_BOOT_COMPLETED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the guidance is complete and the system is loaded, but the screen is still locked.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9.

  - Value: **usual.event.LOCKED_BOOT_COMPLETED**
  - Required permissions: **ohos.permission.RECEIVER_STARTUP_COMPLETED** (for system applications only)

* **COMMON_EVENT_SHUTDOWN<sup>(deprecated)</sup>** indicates that the device is being shut down and will continue until it is finally shut down.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_SHUTDOWN](commonEventManager-definitions.md#common_event_shutdown) instead.

  - Value: **usual.event.SHUTDOWN**
  - Required permissions: none

* **COMMON_EVENT_BATTERY_CHANGED<sup>(deprecated)</sup>** indicates that the battery charging status, battery level, and other information has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BATTERY_CHANGED](commonEventManager-definitions.md#common_event_battery_changed) instead.

  - Value: **usual.event.BATTERY_CHANGED**
  - Required permissions: none

* **COMMON_EVENT_BATTERY_LOW<sup>(deprecated)</sup>** indicates that the battery level is low.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BATTERY_LOW](commonEventManager-definitions.md#common_event_battery_low) instead.

  - Value: **usual.event.BATTERY_LOW**
  - Required permissions: none

* **COMMON_EVENT_BATTERY_OKAY<sup>(deprecated)</sup>** indicates that the battery level is normal.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BATTERY_OKAY](commonEventManager-definitions.md#common_event_battery_okay) instead.

  - Value: **usual.event.BATTERY_OKAY**
  - Required permissions: none

* **COMMON_EVENT_POWER_CONNECTED<sup>(deprecated)</sup>** indicates that the device is connected to an external power supply.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_POWER_CONNECTED](commonEventManager-definitions.md#common_event_power_connected) instead.

  - Value: **usual.event.POWER_CONNECTED**
  - Required permissions: none


* **COMMON_EVENT_POWER_DISCONNECTED<sup>(deprecated)</sup>** indicates that the device is disconnected from the external power supply.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_POWER_DISCONNECTED](commonEventManager-definitions.md#common_event_power_disconnected) instead.

  - Value: **usual.event.POWER_DISCONNECTED**
  - Required permissions: none


* **COMMON_EVENT_SCREEN_OFF<sup>(deprecated)</sup>** indicates that the device screen is off and the device is in sleep mode.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_SCREEN_OFF](commonEventManager-definitions.md#common_event_screen_off) instead.

  - Value: **usual.event.SCREEN_OFF**
  - Required permissions: none


* **COMMON_EVENT_SCREEN_ON<sup>(deprecated)</sup>** indicates that the device screen is on and the device is in interactive state.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_SCREEN_ON](commonEventManager-definitions.md#common_event_screen_on) instead.

  - Value: **usual.event.SCREEN_ON**
  - Required permissions: none


* **COMMON_EVENT_THERMAL_LEVEL_CHANGED<sup>(deprecated)</sup>** indicates that the device thermal level has changed.

  > **NOTE**
  >
  > This type is supported since API version 8 and deprecated since API version 9. You are advised to use [COMMON_EVENT_THERMAL_LEVEL_CHANGED](commonEventManager-definitions.md#common_event_thermal_level_changed) instead.

  - Value: **usual.event.THERMAL_LEVEL_CHANGED**
  - Required permissions: none


* **COMMON_EVENT_USER_PRESENT<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the user unlocks the device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USER_PRESENT](commonEventManager-definitions.md#common_event_user_presentdeprecated) instead.

  - Value: **usual.event.USER_PRESENT**
  - Required permissions: none


* **COMMON_EVENT_TIME_TICK<sup>(deprecated)</sup>** indicates that the system time has changed as time ticks by.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_TIME_TICK](commonEventManager-definitions.md#common_event_time_tick) instead.

  - Value: **usual.event.TIME_TICK**
  - Required permissions: none


* **COMMON_EVENT_TIME_CHANGED<sup>(deprecated)</sup>** indicates that the system time is set.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_TIME_CHANGED](commonEventManager-definitions.md#common_event_time_changed) instead.

  - Value: **usual.event.TIME_CHANGED**
  - Required permissions: none


* **COMMON_EVENT_DATE_CHANGED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the system date has been changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_DATE_CHANGED](commonEventManager-definitions.md#common_event_date_changed) instead.

  - Value: **usual.event.DATE_CHANGED**
  - Required permissions: none


* **COMMON_EVENT_TIMEZONE_CHANGED<sup>(deprecated)</sup>** indicates that the system time zone is changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_TIMEZONE_CHANGED](commonEventManager-definitions.md#common_event_timezone_changed) instead.

  - Value: **usual.event.TIMEZONE_CHANGED**
  - Required permissions: none


* **COMMON_EVENT_CLOSE_SYSTEM_DIALOGS<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the user closes a temporary system dialog box.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_CLOSE_SYSTEM_DIALOGS](commonEventManager-definitions.md#common_event_close_system_dialogs) instead.

  - Value: **usual.event.CLOSE_SYSTEM_DIALOGS**
  - Required permissions: none


* **COMMON_EVENT_PACKAGE_ADDED<sup>(deprecated)</sup>** indicates that a new application package has been installed on the device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGE_ADDED](commonEventManager-definitions.md#common_event_package_added) instead.

  - Value: **usual.event.PACKAGE_ADDED**
  - Required permissions: none

* **COMMON_EVENT_PACKAGE_REPLACED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that a later version of an installed application package has replaced the previous one on the device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGE_REPLACED](commonEventManager-definitions.md#common_event_package_replaced) instead.

  - Value: **usual.event.PACKAGE_REPLACED**
  - Required permissions: none


* **COMMON_EVENT_MY_PACKAGE_REPLACED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the new version of the application package has replaced the previous version.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_MY_PACKAGE_REPLACED](commonEventManager-definitions.md#common_event_my_package_replaced) instead.

  - Value: **usual.event.MY_PACKAGE_REPLACED**
  - Required permissions: none

* **COMMON_EVENT_PACKAGE_REMOVED<sup>(deprecated)</sup>** indicates that an installed application has been uninstalled from the device with the application data retained.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGE_REMOVED](commonEventManager-definitions.md#common_event_package_removed) instead.

  - Value: **usual.event.PACKAGE_REMOVED**
  - Required permissions: none


* **COMMON_EVENT_BUNDLE_REMOVED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an installed bundle has been uninstalled from the device with the application data retained. 

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BUNDLE_REMOVED](commonEventManager-definitions.md#common_event_bundle_removed) instead.

  - Value: **usual.event.BUNDLE_REMOVED**
  - Required permissions: none


* **COMMON_EVENT_PACKAGE_FULLY_REMOVED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an installed application, including both the application data and code, has been completely uninstalled from the device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGE_FULLY_REMOVED](commonEventManager-definitions.md#common_event_package_fully_removed) instead.

  - Value: **usual.event.PACKAGE_FULLY_REMOVED**
  - Required permissions: none


* **COMMON_EVENT_PACKAGE_CHANGED<sup>(deprecated)</sup>** indicates that an application package has been changed (for example, an ability in the package has been enabled or disabled).

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGE_CHANGED](commonEventManager-definitions.md#common_event_package_changed) instead.

  - Value: **usual.event.PACKAGE_CHANGED**
  - Required permissions: none


* **COMMON_EVENT_PACKAGE_RESTARTED<sup>(deprecated)</sup>** indicates that the user closed all processes of the application and restarted the application.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGE_RESTARTED](commonEventManager-definitions.md#common_event_package_restarted) instead.

  - Value: **usual.event.PACKAGE_RESTARTED**
  - Required permissions: none


* **COMMON_EVENT_PACKAGE_DATA_CLEARED<sup>(deprecated)</sup>** indicates that the user cleared the application package data.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGE_DATA_CLEARED](commonEventManager-definitions.md#common_event_package_data_cleared) instead.

  - Value: **usual.event.PACKAGE_DATA_CLEARED**
  - Required permissions: none


* **COMMON_EVENT_PACKAGES_SUSPENDED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that application packages have been suspended.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGES_SUSPENDED](commonEventManager-definitions.md#common_event_packages_suspended) instead.

  - Value: **usual.event.PACKAGES_SUSPENDED**
  - Required permissions: none


* **COMMON_EVENT_PACKAGES_UNSUSPENDED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the application HAP package is not suspended (resumed from the suspended state).

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGES_UNSUSPENDED](commonEventManager-definitions.md#common_event_packages_unsuspended) instead.

  - Value: **usual.event.PACKAGES_UNSUSPENDED**
  - Required permissions: none


* **COMMON_EVENT_MY_PACKAGE_SUSPENDED<sup>(deprecated)</sup>** indicates that the application HAP package is suspended.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_MY_PACKAGE_SUSPENDED](commonEventManager-definitions.md#common_event_my_package_suspended) instead.

  - Value: **usual.event.MY_PACKAGE_SUSPENDED**
  - Required permissions: none


* **COMMON_EVENT_MY_PACKAGE_UNSUSPENDED<sup>(deprecated)</sup>** indicates that the application package is not suspended.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_MY_PACKAGE_UNSUSPENDED](commonEventManager-definitions.md#common_event_my_package_unsuspended) instead.

  - Value: **usual.event.MY_PACKAGE_UNSUSPENDED**
  - Required permissions: none


* **COMMON_EVENT_UID_REMOVED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that a user ID has been removed from the system.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_UID_REMOVED](commonEventManager-definitions.md#common_event_uid_removed) instead.

  - Value: **usual.event.UID_REMOVED**
  - Required permissions: none


* **COMMON_EVENT_PACKAGE_FIRST_LAUNCH<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an installed application is started for the first time.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGE_FIRST_LAUNCH](commonEventManager-definitions.md#common_event_package_first_launch) instead.

  - Value: **usual.event.PACKAGE_FIRST_LAUNCH**
  - Required permissions: none


* **COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an application requires system verification.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION](commonEventManager-definitions.md#common_event_package_needs_verification) instead.

  - Value: **usual.event.PACKAGE_NEEDS_VERIFICATION**
  - Required permissions: none


* **COMMON_EVENT_PACKAGE_VERIFIED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an application has been verified by the system.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_PACKAGE_VERIFIED](commonEventManager-definitions.md#common_event_package_verified) instead.

  - Value: **usual.event.PACKAGE_VERIFIED**
  - Required permissions: none


* **COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that applications installed on the external storage are available for the system.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE](commonEventManager-definitions.md#common_event_external_applications_available) instead.

  - Value: **usual.event.EXTERNAL_APPLICATIONS_AVAILABLE**
  - Required permissions: none


* **COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that applications installed on the external storage are not available for the system.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE](commonEventManager-definitions.md#common_event_external_applications_unavailable) instead.

  - Value: **usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE**
  - Required permissions: none


* **COMMON_EVENT_CONFIGURATION_CHANGED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the device state (for example, orientation and locale) has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_CONFIGURATION_CHANGED](commonEventManager-definitions.md#common_event_configuration_changed) instead.

  - Value: **usual.event.CONFIGURATION_CHANGED**
  - Required permissions: none


* **COMMON_EVENT_LOCALE_CHANGED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the device locale has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_LOCALE_CHANGED](commonEventManager-definitions.md#common_event_locale_changed) instead.

  - Value: **usual.event.LOCALE_CHANGED**
  - Required permissions: none


* **COMMON_EVENT_MANAGE_PACKAGE_STORAGE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the device storage is insufficient.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_MANAGE_PACKAGE_STORAGE](commonEventManager-definitions.md#common_event_manage_package_storage) instead.

  - Value: **usual.event.MANAGE_PACKAGE_STORAGE**
  - Required permissions: none


* **COMMON_EVENT_DRIVE_MODE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the system is in driving mode.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_DRIVE_MODE](commonEventManager-definitions.md#common_event_drive_mode) instead.

  - Value: **common.event.DRIVE_MODE**
  - Required permissions: none


* **COMMON_EVENT_HOME_MODE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the system is in home mode.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_HOME_MODE](commonEventManager-definitions.md#common_event_home_mode) instead.

  - Value: **common.event.HOME_MODE**
  - Required permissions: none


* **COMMON_EVENT_OFFICE_MODE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the system is in office mode.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_OFFICE_MODE](commonEventManager-definitions.md#common_event_office_mode) instead.

  - Value: **common.event.OFFICE_MODE**
  - Required permissions: none


* **COMMON_EVENT_USER_STARTED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the user has been started.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USER_STARTED](commonEventManager-definitions.md#common_event_user_started) instead.

  - Value: **usual.event.USER_STARTED**
  - Required permissions: none


* **COMMON_EVENT_USER_BACKGROUND<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the user has been brought to the background.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USER_BACKGROUND](commonEventManager-definitions.md#common_event_user_background) instead.

  - Value: **usual.event.USER_BACKGROUND**
  - Required permissions: none


* **COMMON_EVENT_USER_FOREGROUND<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the user has been brought to the foreground.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USER_FOREGROUND](commonEventManager-definitions.md#common_event_user_foreground) instead.

  - Value: **usual.event.USER_FOREGROUND**
  - Required permissions: none


* **COMMON_EVENT_USER_SWITCHED<sup>(deprecated)</sup>** indicates that user switching is in progress.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use **COMMON_EVENT_USER_SWITCHED** instead.

  - Value: **usual.event.USER_SWITCHED**
  - Required permissions: **ohos.permission.MANAGE_LOCAL_ACCOUNTS** (for system applications only)


* **COMMON_EVENT_USER_STARTING<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that user starting is in progress.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USER_STARTING](commonEventManager-definitions.md#common_event_user_starting) instead.

  - Value: **usual.event.USER_STARTING**
  - Required permissions: **ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS** (for system applications only)


* **COMMON_EVENT_USER_UNLOCKED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the credential encryption storage of the current user has been unlocked upon restart.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USER_UNLOCKED](commonEventManager-definitions.md#common_event_user_unlocked) instead.

  - Value: **usual.event.USER_UNLOCKED**
  - Required permissions: none


* **COMMON_EVENT_USER_STOPPING<sup>(deprecated)</sup>** (reserved, not supported yet) indicates the user to be stopped.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USER_STOPPING](commonEventManager-definitions.md#common_event_user_stopping) instead.

  - Value: **usual.event.USER_STOPPING**
  - Required permissions: **ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS** (for system applications only)


* **COMMON_EVENT_USER_STOPPED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the user has been stopped.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USER_STOPPED](commonEventManager-definitions.md#common_event_user_stopped) instead.

  - Value: **usual.event.USER_STOPPED**
  - Required permissions: none


* **COMMON_EVENT_WIFI_POWER_STATE<sup>(deprecated)</sup>** indicates a change in the Wi-Fi state (enabled or disabled).

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_POWER_STATE](commonEventManager-definitions.md#common_event_wifi_power_state) instead.

  - Value: **usual.event.wifi.POWER_STATE**
  - Required permissions: none


* **COMMON_EVENT_WIFI_SCAN_FINISHED<sup>(deprecated)</sup>** indicates that the Wi-Fi access point has been scanned and proved available.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_SCAN_FINISHED](commonEventManager-definitions.md#common_event_wifi_scan_finished) instead.

  - Value: **usual.event.wifi.SCAN_FINISHED**
  - Required permissions: **ohos.permission.LOCATION**


* **COMMON_EVENT_WIFI_RSSI_VALUE<sup>(deprecated)</sup>** indicates that the Wi-Fi signal strength (RSSI) has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_RSSI_VALUE](commonEventManager-definitions.md#common_event_wifi_rssi_value) instead.

  - Value: **usual.event.wifi.RSSI_VALUE**
  - Required permissions: **ohos.permission.GET_WIFI_INFO**


* **COMMON_EVENT_WIFI_CONN_STATE<sup>(deprecated)</sup>** indicates that the Wi-Fi connection state has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_CONN_STATE](commonEventManager-definitions.md#common_event_wifi_conn_state) instead.

  - Value: **usual.event.wifi.CONN_STATE**
  - Required permissions: none


* **COMMON_EVENT_WIFI_HOTSPOT_STATE<sup>(deprecated)</sup>** indicates a change in the Wi-Fi hotspot state (enabled or disabled).

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_HOTSPOT_STATE](commonEventManager-definitions.md#common_event_wifi_hotspot_state) instead.

  - Value: **usual.event.wifi.HOTSPOT_STATE**
  - Required permissions: none


* **COMMON_EVENT_WIFI_AP_STA_JOIN<sup>(deprecated)</sup>** indicates that a client has joined the Wi-Fi hotspot of the current device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_AP_STA_JOIN](commonEventManager-definitions.md#common_event_wifi_ap_sta_join) instead.

  - Value: **usual.event.wifi.WIFI_HS_STA_JOIN**
  - Required permissions: **ohos.permission.GET_WIFI_INFO**


* **COMMON_EVENT_WIFI_AP_STA_LEAVE<sup>(deprecated)</sup>** indicates that the client is disconnected from the Wi-Fi hotspot of the current device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_AP_STA_LEAVE](commonEventManager-definitions.md#common_event_wifi_ap_sta_leave) instead.

  - Value: **usual.event.wifi.WIFI_HS_STA_LEAVE**
  - Required permissions: **ohos.permission.GET_WIFI_INFO**


* **COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE<sup>(deprecated)</sup>** (not supported yet) indicates that the state of MPLINK (an enhanced Wi-Fi feature) has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE](commonEventManager-definitions.md#common_event_wifi_mplink_state_change) instead.

  - Value: **usual.event.wifi.mplink.STATE_CHANGE**
  - Required permissions: none


* **COMMON_EVENT_WIFI_P2P_CONN_STATE<sup>(deprecated)</sup>** indicates that the Wi-Fi P2P connection state has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_P2P_CONN_STATE](commonEventManager-definitions.md#common_event_wifi_p2p_conn_state) instead.

  - Value: **usual.event.wifi.p2p.CONN_STATE_CHANGE**
  - Required permissions: **ohos.permission.GET_WIFI_INFO** and **ohos.permission.LOCATION**


* **COMMON_EVENT_WIFI_P2P_STATE_CHANGED<sup>(deprecated)</sup>** indicates a change in the Wi-Fi P2P state (enabled or disabled).

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_P2P_STATE_CHANGED](commonEventManager-definitions.md#common_event_wifi_p2p_state_changed) instead.

  - Value: **usual.event.wifi.p2p.STATE_CHANGE**
  - Required permissions: **ohos.permission.GET_WIFI_INFO**


* **COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED<sup>(deprecated)</sup>** indicates that the state of the Wi-Fi P2P peer device has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED](commonEventManager-definitions.md#common_event_wifi_p2p_peers_state_changed) instead.

  - Value: **usual.event.wifi.p2p.DEVICES_CHANGE**
  - Required permissions: **ohos.permission.GET_WIFI_INFO**


* **COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED<sup>(deprecated)</sup>** indicates that the Wi-Fi P2P discovery state has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED](commonEventManager-definitions.md#common_event_wifi_p2p_peers_discovery_state_changed) instead.

  - Value: **usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE**
  - Required permissions: **ohos.permission.GET_WIFI_INFO**


* **COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED<sup>(deprecated)</sup>** indicates that the state of the Wi-Fi P2P local device has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED](commonEventManager-definitions.md#common_event_wifi_p2p_current_device_state_changed) instead.

  - Value: **usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE**
  - Required permissions: **ohos.permission.GET_WIFI_INFO**


* **COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED<sup>(deprecated)</sup>** indicates that the Wi-Fi P2P group information has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED](commonEventManager-definitions.md#common_event_wifi_p2p_group_state_changed) instead.

  - Value: **usual.event.wifi.p2p.GROUP_STATE_CHANGED**
  - Required permissions: **ohos.permission.GET_WIFI_INFO**


* **COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates the connection state of Bluetooth handsfree communication.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_handsfree_ag_connect_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the device connected to the Bluetooth handsfree function is active.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_handsfree_ag_current_device_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the connection state of Bluetooth A2DP has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_handsfree_ag_audio_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates the connection state of Bluetooth A2DP.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_a2dpsource_connect_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the device connected using Bluetooth A2DP is active.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_a2dpsource_current_device_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the playing state of Bluetooth A2DP has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_a2dpsource_playing_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the AVRCP connection state of Bluetooth A2DP has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_a2dpsource_avrcp_connect_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the audio codec state of Bluetooth A2DP has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_a2dpsource_codec_value_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that a remote Bluetooth device is discovered.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_discovereddeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.DISCOVERED**
  - Required permissions: ohos.permission.LOCATION and ohos.permission.USE_BLUETOOTH


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the Bluetooth class of a remote Bluetooth device has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_class_value_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that a low-level (ACL) connection has been established with the remote Bluetooth device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_acl_connecteddeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.ACL_CONNECTED**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the low-level (ACL) connection has been disconnected from the remote Bluetooth device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_acl_disconnecteddeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.ACL_DISCONNECTED**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the friendly name of a remote Bluetooth device is retrieved for the first time or has changed since the last retrieval.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_name_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.NAME_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates the connection state with a remote Bluetooth device is changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_pair_statedeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.PAIR_STATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the battery level of a remote Bluetooth device is retrieved for the first time or has changed since the last retrieval.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_battery_value_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT<sup>(deprecated)</sup>** (reserved, not supported yet) indicates the SDP state of a remote Bluetooth device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_sdp_resultdeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.SDP_RESULT**
  - Required permissions: none


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates the UUID connection state with a remote Bluetooth device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_uuid_valuedeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.UUID_VALUE**
  - Required permissions: **ohos.permission.DISCOVER_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ<sup>(deprecated)</sup>** (reserved, not supported yet) indicates the pairing request from a remote Bluetooth device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_pairing_reqdeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.PAIRING_REQ**
  - Required permissions: **ohos.permission.DISCOVER_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that Bluetooth pairing has been canceled.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_pairing_canceldeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.PAIRING_CANCEL**
  - Required permissions: none


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ<sup>(deprecated)</sup>** (reserved, not supported yet) indicates the connection request from a remote Bluetooth device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_connect_reqdeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.CONNECT_REQ**
  - Required permissions: none


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY<sup>(deprecated)</sup>** (reserved, not supported yet) indicates the response to the connection request from a remote Bluetooth device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_connect_replydeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.CONNECT_REPLY**
  - Required permissions: none


* **COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the connection to a remote Bluetooth device has been canceled.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL](commonEventManager-definitions.md#common_event_bluetooth_remotedevice_connect_canceldeprecated) instead.

  - Value: **usual.event.bluetooth.remotedevice.CONNECT_CANCEL**
  - Required permissions: none


* **COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the connection state with a Bluetooth handsfree has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_handsfreeunit_connect_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE**
  - Required permissions: none


* **COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the audio state of a Bluetooth handsfree has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_handsfreeunit_audio_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE**
  - Required permissions: none


* **COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the audio gateway state of a Bluetooth handsfree has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT](commonEventManager-definitions.md#common_event_bluetooth_handsfreeunit_ag_common_eventdeprecated) instead.

  - Value: **usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT**
  - Required permissions: none


* **COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the calling state of a Bluetooth handsfree has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_handsfreeunit_ag_call_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE**
  - Required permissions: none


* **COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates a change in the Bluetooth adapter state (enabled or disabled).

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_host_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.host.STATE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that Bluetooth is discoverable.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE](commonEventManager-definitions.md#common_event_bluetooth_host_req_discoverabledeprecated) instead.

  - Value: **usual.event.bluetooth.host.REQ_DISCOVERABLE**
  - Required permissions: none


* **COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that Bluetooth is enabled.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE](commonEventManager-definitions.md#common_event_bluetooth_host_req_enabledeprecated) instead.

  - Value: **usual.event.bluetooth.host.REQ_ENABLE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that Bluetooth is disabled.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE](commonEventManager-definitions.md#common_event_bluetooth_host_req_disabledeprecated) instead.

  - Value: **usual.event.bluetooth.host.REQ_DISABLE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the Bluetooth scan mode of the device is changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_host_scan_mode_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.host.SCAN_MODE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that Bluetooth discovery is started on the device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED](commonEventManager-definitions.md#common_event_bluetooth_host_discovery_starteddeprecated) instead.

  - Value: **usual.event.bluetooth.host.DISCOVERY_STARTED**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that Bluetooth discovery is finished on the device.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED](commonEventManager-definitions.md#common_event_bluetooth_host_discovery_finisheddeprecated) instead.

  - Value: **usual.event.bluetooth.host.DISCOVERY_FINISHED**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the name of the device Bluetooth adapter has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_host_name_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.host.NAME_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the connection state of Bluetooth A2DP Sink has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_a2dpsink_connect_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the playing state of Bluetooth A2DP Sink has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_a2dpsink_playing_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the audio state of Bluetooth A2DP Sink has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE](commonEventManager-definitions.md#common_event_bluetooth_a2dpsink_audio_state_updatedeprecated) instead.

  - Value: **usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE**
  - Required permissions: **ohos.permission.USE_BLUETOOTH**


* **COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the state of the device NFC adapter has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED](commonEventManager-definitions.md#common_event_nfc_action_adapter_state_changed) instead.

  - Value: **usual.event.nfc.action.ADAPTER_STATE_CHANGED**
  - Required permissions: none


* **COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the NFC RF field is detected to be in the enabled state.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED](commonEventManager-definitions.md#common_event_nfc_action_rf_field_on_detected) instead.

  - Value: **usual.event.nfc.action.RF_FIELD_ON_DETECTED**
  - Required permissions: **ohos.permission.MANAGE_SECURE_SETTINGS** (for system applications only)


* **COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the NFC RF field is detected to be in the disabled state.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED](commonEventManager-definitions.md#common_event_nfc_action_rf_field_off_detected) instead.

  - Value: **usual.event.nfc.action.RF_FIELD_OFF_DETECTED**
  - Required permissions: **ohos.permission.MANAGE_SECURE_SETTINGS** (for system applications only)


* **COMMON_EVENT_DISCHARGING<sup>(deprecated)</sup>** indicates that the system stops charging the battery.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_DISCHARGING](commonEventManager-definitions.md#common_event_discharging) instead.

  - Value: **usual.event.DISCHARGING**
  - Required permissions: none


* **COMMON_EVENT_CHARGING<sup>(deprecated)</sup>** indicates that the system starts charging the battery.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_CHARGING](commonEventManager-definitions.md#common_event_charging) instead.

  - Value: **usual.event.CHARGING**
  - Required permissions: none


* **COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the system idle mode has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED](commonEventManager-definitions.md#common_event_device_idle_mode_changed) instead.

  - Value: **usual.event.DEVICE_IDLE_MODE_CHANGED**
  - Required permissions: none


* **COMMON_EVENT_POWER_SAVE_MODE_CHANGED<sup>(deprecated)</sup>** indicates that the system power-saving mode has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_POWER_SAVE_MODE_CHANGED](commonEventManager-definitions.md#common_event_power_save_mode_changed) instead.

  - Value: **usual.event.POWER_SAVE_MODE_CHANGED**
  - Required permissions: none


* **COMMON_EVENT_USER_ADDED<sup>(deprecated)</sup>** indicates that a user has been added to the system.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use **COMMON_EVENT_USER_ADDED** instead.

  - Value: **usual.event.USER_ADDED**
  - Required permissions: **ohos.permission.MANAGE_LOCAL_ACCOUNTS** (for system applications only)


* **COMMON_EVENT_USER_REMOVED<sup>(deprecated)</sup>** indicates that a user has been removed from the system.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use **COMMON_EVENT_USER_REMOVED** instead.

  - Value: **usual.event.USER_REMOVED**
  - Required permissions: **ohos.permission.MANAGE_LOCAL_ACCOUNTS** (for system applications only)


* **COMMON_EVENT_ABILITY_ADDED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an ability has been added.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_ABILITY_ADDED](commonEventManager-definitions.md#common_event_ability_added) instead.

  - Value: **usual.event.ABILITY_ADDED**
  - Required permissions: **ohos.permission.LISTEN_BUNDLE_CHANGE**


* **COMMON_EVENT_ABILITY_REMOVED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an ability has been removed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_ABILITY_REMOVED](commonEventManager-definitions.md#common_event_ability_removed) instead.

  - Value: **usual.event.ABILITY_REMOVED**
  - Required permissions: **ohos.permission.LISTEN_BUNDLE_CHANGE**


* **COMMON_EVENT_ABILITY_UPDATED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an ability has been updated.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_ABILITY_UPDATED](commonEventManager-definitions.md#common_event_ability_updated) instead.

  - Value: **usual.event.ABILITY_UPDATED**
  - Required permissions: **ohos.permission.LISTEN_BUNDLE_CHANGE**


* **COMMON_EVENT_LOCATION_MODE_STATE_CHANGED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the location mode of the system has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_LOCATION_MODE_STATE_CHANGED](commonEventManager-definitions.md#common_event_location_mode_state_changed) instead.

  - Value: **usual.event.location.MODE_STATE_CHANGED**
  - Required permissions: none


* **COMMON_EVENT_IVI_SLEEP<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the in-vehicle infotainment (IVI) system of the vehicle is sleeping.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_IVI_SLEEP](commonEventManager-definitions.md#common_event_ivi_sleep) instead.

  - Value: **common.event.IVI_SLEEP**
  - Required permissions: none


* **COMMON_EVENT_IVI_PAUSE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the IVI system of the vehicle is in sleep mode and notifies the application to stop playing.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_IVI_PAUSE](commonEventManager-definitions.md#common_event_ivi_pause) instead.

  - Value: **common.event.IVI_PAUSE**
  - Required permissions: none


* **COMMON_EVENT_IVI_STANDBY<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that a third-party application in the IVI system of a vehicle is suspended.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_IVI_STANDBY](commonEventManager-definitions.md#common_event_ivi_standby) instead.

  - Value: **common.event.IVI_STANDBY**
  - Required permissions: none


* **COMMON_EVENT_IVI_LASTMODE_SAVE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the third-party application in the IVI system of the vehicle saves the last mode.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_IVI_LASTMODE_SAVE](commonEventManager-definitions.md#common_event_ivi_lastmode_save) instead.

  - Value: **common.event.IVI_LASTMODE_SAVE**
  - Required permissions: none


* **COMMON_EVENT_IVI_VOLTAGE_ABNORMAL<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the voltage of the vehicle's power system is abnormal.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_IVI_VOLTAGE_ABNORMAL](commonEventManager-definitions.md#common_event_ivi_voltage_abnormal) instead.

  - Value: **common.event.IVI_VOLTAGE_ABNORMAL**
  - Required permissions: none


* **COMMON_EVENT_IVI_HIGH_TEMPERATURE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the temperature of the IVI system of the vehicle is too high.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_IVI_HIGH_TEMPERATURE](commonEventManager-definitions.md#common_event_ivi_high_temperature) instead.

  - Value: **common.event.IVI_HIGH_TEMPERATURE**
  - Required permissions: none


* **COMMON_EVENT_IVI_EXTREME_TEMPERATURE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the temperature of the IVI system of the vehicle is extremely high.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_IVI_EXTREME_TEMPERATURE](commonEventManager-definitions.md#common_event_ivi_extreme_temperature) instead.

  - Value: **common.event.IVI_EXTREME_TEMPERATURE**
  - Required permissions: none


* **COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the IVI system of the vehicle has an extreme temperature.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL](commonEventManager-definitions.md#common_event_ivi_temperature_abnormal) instead.

  - Value: **common.event.IVI_TEMPERATURE_ABNORMAL**
  - Required permissions: none


* **COMMON_EVENT_IVI_VOLTAGE_RECOVERY<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the voltage of the vehicle's power system is restored to normal.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_IVI_VOLTAGE_RECOVERY](commonEventManager-definitions.md#common_event_ivi_voltage_recovery) instead.

  - Value: **common.event.IVI_VOLTAGE_RECOVERY**
  - Required permissions: none


* **COMMON_EVENT_IVI_TEMPERATURE_RECOVERY<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the temperature of the IVI system is restored to normal.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_IVI_TEMPERATURE_RECOVERY](commonEventManager-definitions.md#common_event_ivi_temperature_recovery) instead.

  - Value: **common.event.IVI_TEMPERATURE_RECOVERY**
  - Required permissions: none


* **COMMON_EVENT_IVI_ACTIVE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the battery service of the vehicle-mounted system is active.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_IVI_ACTIVE](commonEventManager-definitions.md#common_event_ivi_active) instead.

  - Value: **common.event.IVI_ACTIVE**
  - Required permissions: none

* **COMMON_EVENT_USB_DEVICE_ATTACHED<sup>(deprecated)</sup>** indicates that a USB device has been attached to the device functioning as a USB host.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USB_DEVICE_ATTACHED](commonEventManager-definitions.md#common_event_usb_device_attached) instead.

  - Value: **usual.event.hardware.usb.action.USB_DEVICE_ATTACHED**
  - Required permissions: none


* **COMMON_EVENT_USB_DEVICE_DETACHED<sup>(deprecated)</sup>** indicates that a USB device has been detached from the device functioning as a USB host.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USB_DEVICE_DETACHED](commonEventManager-definitions.md#common_event_usb_device_detached) instead.

  - Value: **usual.event.hardware.usb.action.USB_DEVICE_DETACHED**
  - Required permissions: none


* **COMMON_EVENT_USB_ACCESSORY_ATTACHED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that a USB accessory was attached.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USB_ACCESSORY_ATTACHED](commonEventManager-definitions.md#common_event_usb_accessory_attached) instead.

  - Value: **usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED**
  - Required permissions: none


* **COMMON_EVENT_USB_ACCESSORY_DETACHED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the USB attachment is uninstalled.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_USB_ACCESSORY_DETACHED](commonEventManager-definitions.md#common_event_usb_accessory_detached) instead.

  - Value: **usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED**
  - Required permissions: none


* **COMMON_EVENT_DISK_REMOVED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an external storage device was removed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_DISK_REMOVED](commonEventManager-definitions.md#common_event_disk_removed) instead.

  - Value: **usual.event.data.DISK_REMOVED**
  - Required permissions: **ohos.permission.STORAGE_MANAGER** (for system applications only)


* **COMMON_EVENT_DISK_UNMOUNTED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an external storage device was unmounted.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_DISK_UNMOUNTED](commonEventManager-definitions.md#common_event_disk_unmounted) instead.

  - Value: **usual.event.data.DISK_UNMOUNTED**
  - Required permissions: **ohos.permission.STORAGE_MANAGER** (for system applications only)


* **COMMON_EVENT_DISK_MOUNTED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an external storage device was mounted.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_DISK_MOUNTED](commonEventManager-definitions.md#common_event_disk_mounted) instead.

  - Value: **usual.event.data.DISK_MOUNTED**
  - Required permissions: **ohos.permission.STORAGE_MANAGER** (for system applications only)


* **COMMON_EVENT_DISK_BAD_REMOVAL<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an external storage device was removed without being unmounted.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_DISK_BAD_REMOVAL](commonEventManager-definitions.md#common_event_disk_bad_removal) instead.

  - Value: **usual.event.data.DISK_BAD_REMOVAL**
  - Required permissions: **ohos.permission.STORAGE_MANAGER** (for system applications only)


* **COMMON_EVENT_DISK_UNMOUNTABLE<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the external storage device cannot be mounted when a card is inserted.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_DISK_UNMOUNTABLE](commonEventManager-definitions.md#common_event_disk_unmountable) instead.

  - Value: **usual.event.data.DISK_UNMOUNTABLE**
  - Required permissions: **ohos.permission.STORAGE_MANAGER** (for system applications only)


* **COMMON_EVENT_DISK_EJECT<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the external storage medium has been ejected (interactive operation at the system software layer, not directly ejected physically).

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_DISK_EJECT](commonEventManager-definitions.md#common_event_disk_eject) instead.

  - Value: **usual.event.data.DISK_EJECT**
  - Required permissions: **ohos.permission.STORAGE_MANAGER** (for system applications only)


* **COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the account visibility changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED](commonEventManager-definitions.md#common_event_visible_accounts_updated) instead.

  - Value: **usual.event.data.VISIBLE_ACCOUNTS_UPDATED**
  - Required permissions: **ohos.permission.GET_APP_ACCOUNTS** (for system applications only)


* **COMMON_EVENT_ACCOUNT_DELETED<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that an account was deleted.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_ACCOUNT_DELETED](commonEventManager-definitions.md#common_event_account_deleted) instead.

  - Value: **usual.event.data.ACCOUNT_DELETED**
  - Required permissions: **ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS** (for system applications only)


* **COMMON_EVENT_FOUNDATION_READY<sup>(deprecated)</sup>** (reserved, not supported yet) indicates that the foundation is ready.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_FOUNDATION_READY](commonEventManager-definitions.md#common_event_foundation_ready) instead.

  - Value: **usual.event.data.FOUNDATION_READY**
  - Required permissions: **ohos.permission.RECEIVER_STARTUP_COMPLETED** (for system applications only)


* **COMMON_EVENT_AIRPLANE_MODE_CHANGED<sup>(deprecated)</sup>** indicates that the airplane mode of the device has changed.

  > **NOTE**
  >
  > This type is supported since API version 7 and deprecated since API version 9. You are advised to use [COMMON_EVENT_AIRPLANE_MODE_CHANGED](commonEventManager-definitions.md#common_event_airplane_mode_changed10) instead.

  - Value: **usual.event.AIRPLANE_MODE**
  - Required permissions: none

* **COMMON_EVENT_SPLIT_SCREEN<sup>(deprecated)</sup>** indicates that the screen has been split.

  > **NOTE**
  >
  > This type is supported since API version 8 and deprecated since API version 9. You are advised to use [COMMON_EVENT_SPLIT_SCREEN](commonEventManager-definitions.md#common_event_split_screen) instead.
