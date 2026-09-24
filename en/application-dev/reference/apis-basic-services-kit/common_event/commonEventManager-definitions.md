# System Common Events
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=f1df35e744e8be0a80ac7cb20765106cc0424535 translatedAt=2026-09-23T02:10:22.948Z pushedAt=2026-09-23T10:54:49.442Z -->

This document provides a list of system-defined common events.
Common event types are defined in [Support enumeration of the ohos.commonEventManager module](../js-apis-commonEventManager.md#support).

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Ability Kit

### COMMON_EVENT_PACKAGE_RESTARTED

Indicates that the user restarts an application package and terminates all its processes.

When a specified user restarts an application package and terminates all its processes on a device, the event notification service is triggered to publish this [system common event](../../../basic-services/common-event/common-event-glossary.md#system-common-event).

> **NOTE** 
> 
> <!--Del-->A system application can listen to the restart events of its own application and other applications.<!--DelEnd-->
> 
> A third-party application can only listen to the restart event of its own application.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PACKAGE_RESTARTED"


### COMMON_EVENT_PACKAGE_DATA_CLEARED

Indicates that the user clears application package data.

When a specified user clears application package data on the device, this will trigger the event notification service to publish this system common event.

> **NOTE** 
> 
> <!--Del-->A system application can listen to the data clearing events of its own application and other applications.<!--DelEnd-->
> 
> A third-party application can only listen to the data clearing event of its own application.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PACKAGE_DATA_CLEARED"


### COMMON_EVENT_QUICK_FIX_APPLY_RESULT

Indicates that a quick fix is applied to an application.

When a quick fix is applied to an application by a specified user on the device, the common event service is triggered to publish this event.

> **NOTE** 
> 
> <!--Del-->A system application can listen to the quick fix events of its own application and other applications.<!--DelEnd-->
> 
> A third-party application can only listen to the quick fix events of its own application.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.QUICK_FIX_APPLY_RESULT"


### COMMON_EVENT_QUICK_FIX_REVOKE_RESULT<sup>10+</sup>

Indicates the revocation of a quick fix.

When a quick fix is revoked on the device, the common event service is triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.QUICK_FIX_REVOKE_RESULT"


### COMMON_EVENT_PACKAGE_ADDED

Indicates the action of the common event that a new application package has been installed on the device.

When a new application is installed by a specified user on the device, the common event service is triggered to publish this system common event.

> **NOTE** 
> 
> <!--Del-->A system application can listen to the installation events of its own application and other applications.<!--DelEnd-->
> 
> A third-party application, by default, can only listen to the installation event of its own application. If a third-party application needs to listen to the installation event of an InHouse application, the InHouse application that needs to be listened to must configure this application's [appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier) in [allowListenBundleChangedEvent](../../../quick-start/app-configuration-file.md) in app.json5.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value**: usual.event.PACKAGE_ADDED


### COMMON_EVENT_PACKAGE_REMOVED

Indicates the operation of the common event that an installed application has been uninstalled from the device but its application data is retained.

When a specified application package is uninstalled by a specified user on the device, it will trigger the common event service to publish this system common event.

> **NOTE** 
> 
> <!--Del-->A system application can listen to the uninstall events of its own application and other applications.<!--DelEnd-->
> 
> A third-party application, by default, can only listen to the uninstall event of its own application. If a third-party application needs to listen to the uninstall event of an InHouse application, the InHouse application to be listened to needs to configure its [appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier) in [allowListenBundleChangedEvent](../../../quick-start/app-configuration-file.md) in app.json5.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value**: usual.event.PACKAGE_REMOVED


### COMMON_EVENT_BUNDLE_REMOVED

(Reserved event, not yet supported) Indicates the event that an existing application package is removed from the device.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value**: "usual.event.BUNDLE_REMOVED"


### COMMON_EVENT_PACKAGE_FULLY_REMOVED

Indicates the event that an existing application program is completely removed from the device.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PACKAGE_FULLY_REMOVED"


### COMMON_EVENT_PACKAGE_CHANGED

Indicates the action of the common event that an application package has changed (for example, a component in the package has been enabled or disabled).

When an installed application program package on the device is updated or a component in the package is enabled or disabled, the event notification service publishing will be triggered to publish this system common event.

> **NOTE** 
> 
> <!--Del-->A system application can listen to change events of its own application and other applications.<!--DelEnd-->
> 
> By default, a third-party application can only listen to change events of its own application. If a third-party application needs to listen to update events of an InHouse application, the InHouse application that needs to be listened to must configure the [appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier) of this application in [allowListenBundleChangedEvent](../../../quick-start/app-configuration-file.md) in app.json5.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PACKAGE_CHANGED"


### COMMON_EVENT_PACKAGE_CACHE_CLEARED

Indicates the action of the common event for a user to clear the cache data of an application package.

When the cache of an application package installed on the device is cleared, the event notification service will be triggered to publish this system common event.

> **NOTE** 
> 
> <!--Del-->A system application can listen to the cache clearing events of its own application and other applications.<!--DelEnd-->
> 
> A third-party application, by default, can only listen to the cache clearing events of its own application. If a third-party application needs to listen to the cache clearing events of an InHouse application, the InHouse application that needs to be listened to must configure its [appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier) in [allowListenBundleChangedEvent](../../../quick-start/app-configuration-file.md) in app.json5.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PACKAGE_CACHE_CLEARED"


### COMMON_EVENT_PACKAGES_SUSPENDED

(Reserved event, not yet supported) Indicates that the package has been suspended.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PACKAGES_SUSPENDED"


### COMMON_EVENT_MY_PACKAGE_SUSPENDED

(Reserved event, not yet supported) Sent to a package that has been suspended by the system.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.MY_PACKAGE_SUSPENDED"


### COMMON_EVENT_MY_PACKAGE_UNSUSPENDED

(Reserved event, not yet supported) Sent to a package that has been unsuspended by the system.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.MY_PACKAGE_UNSUSPENDED"


### COMMON_EVENT_MANAGE_PACKAGE_STORAGE

Notifies the user of the low memory status and that package management should be started.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.MANAGE_PACKAGE_STORAGE"

### COMMON_EVENT_SKILL_CHANGED

Indicates a common event that the skill of an application on the device changes.

When an application program containing a skill is installed, updated, or uninstalled for a specified user on the device, the event notification service publishing will trigger this system common event.

> **NOTE** 
> 
> By default, an application can only receive the skill change event of its own application.
> 
> After applying for the ohos.permission.MANAGE_SKILL_PRIVILEGE permission, an application can receive the skill change events of its own application and other applications.

**Since**: 26.0.0

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.SKILL_CHANGED"

## Account Kit

### COMMON_EVENT_MINORSMODE_ON<sup>12+</sup>

Indicates that the user enables minor mode.

When the youth mode is enabled on a device, the event notification service is triggered to publish this [system common event](../../../basic-services/common-event/common-event-glossary.md#system-common-event).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Atomic service API**: This API can be used in atomic services since API version 12.

**Value:** "usual.event.MINORSMODE_ON"



### COMMON_EVENT_MINORSMODE_OFF<sup>12+</sup>

Indicates that the user turns off minor mode.

When minor mode is turned off on the device, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Atomic service API**: This API can be used in atomic services since API version 12.

**Value:** "usual.event.MINORSMODE_OFF"


## ArkData


### COMMON_EVENT_DATA_SHARE_READY<sup>12+</sup>

Indicates that the datashare service is available.

After the DataShare service is started, the event notification service is triggered to publish this [system common event](../../../basic-services/common-event/common-event-glossary.md#system-common-event).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Atomic service API**: This API can be used in atomic services since API version 12.

**Value:** "usual.event.DATA_SHARE_READY"


## ArkUI

### COMMON_EVENT_SPLIT_SCREEN

A common event that indicates split-screen behavior.

When any of the following actions is performed, the event notification service is triggered to publish this [system common event](../../../basic-services/common-event/common-event-glossary.md#system-common-event).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Atomic service API**: This API can be used in atomic services since API version 11.

**Value:** "common.event.SPLIT_SCREEN"



## Notification Kit

### COMMON_EVENT_SLOT_CHANGE

Indicates that the [notification slot](../../../notification/notification-glossary.md#notification-slot) or notification switch settings have changed.

  When the [notification slot settings](../../../notification/notification-glossary.md#notification-setting) (including the switch) change or the notification feature is enabled or disabled, the notification service is triggered to publish this [system common event](../../../basic-services/common-event/common-event-glossary.md#system-common-event).

**System capability**: SystemCapability.Notification.CommonEvent

**Subscriber permission:** ohos.permission.NOTIFICATION_CONTROLLER

**Value:** "usual.event.SLOT_CHANGE"


## Background Tasks Kit


### COMMON_EVENT_DEVICE_IDLE_MODE_CHANGED
Indicates that the device standby state changes, which triggers the action of publishing a common event.

If the user has not used the device for a period of time and the screen is turned off, the system delays the CPU and network access by background applications, and the [common event service](../../../basic-services/common-event/common-event-glossary.md#common-event-service-ces) will be triggered to publish this [system common event](../../../basic-services/common-event/common-event-glossary.md#system-common-event).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.DEVICE_IDLE_MODE_CHANGED"


## Basic Services Kit

### COMMON_EVENT_USB_STATE

Indicates that the USB device status changes.

When a USB device is connected to or disconnected from the device, the event notification service is triggered to publish this [system common event](../../../basic-services/common-event/common-event-glossary.md#system-common-event).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.hardware.usb.action.USB_STATE"


### COMMON_EVENT_USB_PORT_CHANGED

Prompts the user that the USB port status of the device has changed.

When the USB port status changes, the event notification service publishing will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.hardware.usb.action.USB_PORT_CHANGED"


### COMMON_EVENT_USB_DEVICE_ATTACHED

Indicates that a USB device has been attached when the user device acts as a USB host.

When the USB connection state changes, this will trigger the event notification service publishing this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.hardware.usb.action.USB_DEVICE_ATTACHED"


### COMMON_EVENT_USB_DEVICE_DETACHED

Indicates that a USB device is detached when the user device acts as a USB host.

When the USB connection is disconnected and the state changes, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.hardware.usb.action.USB_DEVICE_DETACHED"


### COMMON_EVENT_TIME_CHANGED

Action of the common event for setting the system time.

When the system time is set, this will trigger the event notification service publishing this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.TIME_CHANGED"


### COMMON_EVENT_TIME_TICK

Action of the common event that indicates the system time changes.

When the system time changes in units of a whole minute, the event notification service publishing will trigger this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.TIME_TICK"


### COMMON_EVENT_TIMEZONE_CHANGED

Indicates the action of the common event for a system time zone change.

When the system time zone changes, the common event service is triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.TIMEZONE_CHANGED"





### COMMON_EVENT_USER_INFO_UPDATED

Indicates that the user information has been updated.

A change in the distributed account information, a change in the system account profile photo, or a change in the system account name will trigger the event notification service to publish this system common event. The event carries the system account ID.

APIs related to this event: **setOsAccountName**, **setOsAccountProfilePhoto**, and **setOsAccountDistributedInfo**. The first two are system APIs, and the last is a public API. For details, see [@ohos.account.osAccount (OS Account Management)](../js-apis-osAccount.md) and [@ohos.account.distributedAccount (Distributed Account Management)](../js-apis-distributed-account.md).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.USER_INFO_UPDATED"


### COMMON_EVENT_USER_UNLOCKED

Indicates the action of the common event that the credential-encrypted storage of the current user has been unlocked when the device is unlocked after restart.

Switching to a user with a lock screen password and unlocking for the first time will trigger the event notification service publishing this system common event. The event carries the system account ID that identifies the user.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value**: usual.event.USER_UNLOCKED


### COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGIN

Indicates the action of a successful distributed account login.

When a distributed account login succeeds, the event notification service publishing will trigger this system common event, and the event carries the system account ID and sub-identity ID.

APIs associated with this common event: setOsAccountDistributedInfo and updateOsAccountDistributedInfo (deprecated), which are public APIs, and setOsAccountDistributedInfoByLocalId, which is a system API. For details, see [Distributed Account API Reference](../js-apis-distributed-account.md).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Atomic service API**: This API can be used in atomic services since API version 12.

**Value:** "common.event.DISTRIBUTED_ACCOUNT_LOGIN"


### COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOUT

Indicates the action of a successful distributed account logout.

When a distributed account logs out, the event notification service publishing will trigger this system common event. The event carries the system account ID and the sub-identity ID.

APIs associated with this common event: setOsAccountDistributedInfo and updateOsAccountDistributedInfo (deprecated), which are public APIs, and setOsAccountDistributedInfoByLocalId, which is a system API. For details, see [Distributed Account API Reference](../js-apis-distributed-account.md).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Atomic service API**: This API can be used in atomic services since API version 12.

**Value:** "common.event.DISTRIBUTED_ACCOUNT_LOGOUT"


### COMMON_EVENT_DISTRIBUTED_ACCOUNT_TOKEN_INVALID

Indicates the action that the distributed account token is invalid.

When the token of a distributed account is invalid, the event notification service will trigger the publishing of this system common event. The event carries the system account ID and the sub-identity ID.

APIs associated with this common event: setOsAccountDistributedInfo and updateOsAccountDistributedInfo (deprecated), which are public APIs, and setOsAccountDistributedInfoByLocalId, which is a system API. For details, see [Distributed Account API Reference](../js-apis-distributed-account.md).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Atomic service API**: This API can be used in atomic services since API version 12.

**Value:** "common.event.DISTRIBUTED_ACCOUNT_TOKEN_INVALID"



### COMMON_EVENT_DISTRIBUTED_ACCOUNT_LOGOFF

Indicates the action of logging off a distributed account.

A successful distributed account logoff will trigger the event notification service publishing of this system common event. The event carries the system account ID and the sub-identity ID.

APIs associated with this common event: setOsAccountDistributedInfo and updateOsAccountDistributedInfo (deprecated), which are public APIs, and setOsAccountDistributedInfoByLocalId, which is a system API. For details, see [Distributed Account API Reference](../js-apis-distributed-account.md).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Atomic service API**: This API can be used in atomic services since API version 12.

**Value:** "common.event.DISTRIBUTED_ACCOUNT_LOGOFF"



### COMMON_EVENT_SCREEN_LOCKED

Indicates the common event of screen locking.
When the screen is locked, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Atomic service API**: This API can be used in atomic services since API version 11.

**Value:** usual.event.SCREEN_LOCKED



### COMMON_EVENT_SCREEN_UNLOCKED

Indicates the common event of screen unlocking.
When the lock screen is unlocked, this will trigger the event notification service publishing of this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Atomic service API**: This API can be used in atomic services since API version 11.

**Value:** usual.event.SCREEN_UNLOCKED


### COMMON_EVENT_USER_PRESENT<sup>(deprecated)</sup>
Action of the common event indicating that the user unlocks the device.

  > **NOTE**
  >
  > This event is supported since API version 9 and deprecated since API version 10. You are advised to use [COMMON_EVENT_SCREEN_UNLOCKED](#common_event_screen_unlocked) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.USER_PRESENT"


### COMMON_EVENT_BATTERY_CHANGED

Indicates the action of the common event that the battery charging status, level, and other information have changed.

When the battery level, battery temperature, battery health status, type of charger connected to the device, maximum current of the charger, maximum voltage of the charger, battery charging status, number of charging cycles, total battery capacity, remaining battery capacity, battery technical model, or battery charging type changes, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.BATTERY_CHANGED"


### COMMON_EVENT_BATTERY_LOW

Indicates the action of the common event for low battery level.

When the battery level falls below the low battery percentage configured on the device, the event notification service will be triggered to publish this system common event.<!--Del-->For details about the low battery percentage configured on the device, see [*Battery Level Customization Development Guide*](../../../../device-dev/subsystems/subsys-power-battery-level-customization.md).<!--DelEnd-->

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.BATTERY_LOW"


### COMMON_EVENT_BATTERY_OKAY

Indicates the action of the common event that the battery exits the low battery state.

When the battery level rises from the low battery level to above the low battery level, it will trigger the event notification service to publish this system common event.


**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.BATTERY_OKAY"


### COMMON_EVENT_POWER_CONNECTED

Indicates the action of the common event that the device is connected to an external power source.

When the device is connected to an external recognizable charger type for charging, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.POWER_CONNECTED"


### COMMON_EVENT_POWER_DISCONNECTED

Indicates the action of the common event that the device is disconnected from the external power supply.

When the device is disconnected from the external power supply, the event notification service publishing will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.POWER_DISCONNECTED"


### COMMON_EVENT_DISCHARGING

Indicates the action of the common event that the system stops charging the battery.

When the system stops charging the battery, this will trigger the event notification service to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.DISCHARGING"


### COMMON_EVENT_CHARGING

Indicates the action of the common event that the system starts charging the battery.

When the system starts charging the battery, it will trigger the event notification service to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.CHARGING"



### COMMON_EVENT_CHARGE_IDLE_MODE_CHANGED<sup>10+</sup>

Indicates the action of the common event that the device enters the charging idle mode.

When the device is in a state of being idle, charging, and with an acceptable temperature rise, the event notification service publishing will trigger this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value**: usual.event.CHARGE_IDLE_MODE_CHANGED


### COMMON_EVENT_SHUTDOWN

Indicates the action of the common event that the device is being shut down and will continue to shut down completely.

When the device is being shut down and will continue to shut down completely, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.SHUTDOWN"


### COMMON_EVENT_SCREEN_OFF

Indicates the action of the common event that the device screen-off initiated by the power service is complete.

When the device screen-off initiated by the power service is complete, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** usual.event.SCREEN_OFF


### COMMON_EVENT_SCREEN_ON

Indicates the action of the common event that the screen is turned on by the power service.

When the screen is turned on by the power service, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** usual.event.SCREEN_ON


### COMMON_EVENT_POWER_SAVE_MODE_CHANGED

Indicates the action of the common event that the system power save mode changes.

When the system power save mode changes, the common event service is triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.POWER_SAVE_MODE_CHANGED"


### COMMON_EVENT_THERMAL_LEVEL_CHANGED

Action of the common event that indicates the thermal status of the device.

When the thermal level of the device changes, this system common event will be triggered and published by the event notification service. <!--Del-->For details about the thermal level configuration, see [Thermal Level Customization Development Guide](../../../../device-dev/subsystems/subsys-thermal_level.md). <!--DelEnd-->

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.THERMAL_LEVEL_CHANGED"


### COMMON_EVENT_ENTER_FORCE_SLEEP<sup>12+</sup>

Indicates the action of the common event that the device is about to enter the forced sleep mode.

When the device is about to enter the forced sleep mode, the event notification service publishing will trigger this system common event. All subscribers must process this event within 1 second.


**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.ENTER_FORCE_SLEEP"

### COMMON_EVENT_EXIT_FORCE_SLEEP<sup>12+</sup>

Indicates the action of the common event that the device exits the forced sleep mode.

When the device exits the forced sleep mode, it will trigger the event notification service to publish this system common event.


**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.EXIT_FORCE_SLEEP"

### COMMON_EVENT_ENTER_HIBERNATE<sup>15+</sup>

Indicates the action of the common event that the device is about to enter hibernation mode.

When the device is about to enter hibernation mode, the event notification service will trigger the publishing of this system common event. All subscribers must process this event within 1 second.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.ENTER_HIBERNATE"

### COMMON_EVENT_EXIT_HIBERNATE<sup>15+</sup>

Indicates the action of the common event that the device exits hibernate mode.

When the device exits hibernate mode, the event notification service will trigger the publishing of this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.EXIT_HIBERNATE"

### COMMON_EVENT_VOLUME_DECRYPTED

Indicates that a specific volume on the device has been decrypted.

When a specific volume on the device is decrypted, the event notification service will be triggered to publish this system common event.

**Since**: 26.0.0

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.VOLUME_DECRYPTED"

### COMMON_EVENT_VOLUME_ENCRYPTED

Indicates that a specific volume on the device has been encrypted.

When a specific volume on the device is encrypted, the event notification service publishing will be triggered to publish this system common event.

**Since**: 26.0.0

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.VOLUME_ENCRYPTED"

### COMMON_EVENT_VOLUME_ENCRYPTION_POLICY_SET

Indicates that the encryption policy has been set for a specific volume on the device.

When the encryption policy is set for a specific volume on the device, the event notification service publishing will be triggered to publish this system common event.

**Since**: 26.0.0

**System capability**: SystemCapability.Notification.CommonEvent

**Subscriber permission:** ohos.permission.QUERY_VOLUME_ENCRYPTION_STATUS

**Value:** "usual.event.VOLUME_ENCRYPTION_POLICY_SET"


## Connectivity Kit

### COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_CHANGE<sup>20+</sup>

Indicates the operation of the common event for the Bluetooth HFP AG connection state change.

When the Bluetooth HFP AG connection state changes, the event notification service is triggered to publish this [system common event](../../../basic-services/common-event/common-event-glossary.md#system-common-event).

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions for subscribers:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.handsfree.ag.CONNECT_STATE_CHANGE"


### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_CHANGE<sup>20+</sup>

Indicates the operation of the common event for the Bluetooth A2DP Source connection state change.

When the Bluetooth A2DP Source connection state changes, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions for subscribers:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.a2dpsource.CONNECT_STATE_CHANGE"


### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_CHANGE<sup>20+</sup>

Indicates the operation of the common event for a Bluetooth AVRCP connection state change.

When the Bluetooth AVRCP connection state changes, the event notification service publishing will trigger this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_CHANGE"


### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_CHANGE<sup>20+</sup>

Indicates the operation of the common event for a change in the Bluetooth media codec.

When the Bluetooth media codec changes, this will trigger the event notification service to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions for subscribers:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.a2dpsource.CODEC_VALUE_CHANGE"


### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAY_STATE_CHANGE<sup>24+</sup>

Indicates the action of the common event for the Bluetooth media A2DP playback state change.

When the Bluetooth media A2DP playback state changes, the event notification service publishing will trigger this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Value**: "usual.event.bluetooth.a2dpsource.PLAY_STATE_CHANGE"


### COMMON_EVENT_BLUETOOTH_SCO_CONNECT_STATE_CHANGE<sup>24+</sup>

Indicates the operation of the common event for Bluetooth SCO state changes.

When the Bluetooth SCO state changes, this will trigger the event notification service to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Value**: "usual.event.bluetooth.SCO_CONNECT_STATE_CHANGE"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE<sup>20+</sup>

Indicates the action of the common event for the ACL connection state change of a Bluetooth remote device.

When the ACL connection state of a Bluetooth remote device changes, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.remotedevice.ACL_STATE_CHANGE"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE_CHANGE<sup>20+</sup>

Indicates the operation of the common event for Bluetooth pairing state changes.

When the Bluetooth pairing state changes, this will trigger the event notification service publishing this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.remotedevice.PAIR_STATE_CHANGE"


### COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_CHANGE<sup>23+</sup>

Indicates the action of the event that the Bluetooth scan mode changes.

When the Bluetooth scan mode changes, the event notification service publishing will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.host.SCAN_MODE_CHANGE"


### COMMON_EVENT_NFC_ACTION_ADAPTER_STATE_CHANGED

Indicates the action of the common event that the device NFC state has changed.

Indicates that when the device NFC state changes, the event notification service publishing will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.nfc.action.ADAPTER_STATE_CHANGED"


### COMMON_EVENT_NFC_ACTION_RF_FIELD_ON_DETECTED

Common event indicating that an NFC RF field is detected.

When an NFC RF field is detected, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.nfc.action.RF_FIELD_ON_DETECTED"


### COMMON_EVENT_NFC_ACTION_RF_FIELD_OFF_DETECTED

Common event indicating that the NFC field is detected to have left.

When the NFC field is detected to have left, the event notification service publishing will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.nfc.action.RF_FIELD_OFF_DETECTED"


### COMMON_EVENT_WIFI_POWER_STATE

Indicates the Wi-Fi state changes.

When the Wi-Fi state changes (for example, Wi-Fi is enabled or disabled), the event notification service publishing will be triggered to publish this system common event.

Status values: 0: WLAN is being disabled, 1: WLAN is disabled, 2: WLAN is being enabled, 3: WLAN is enabled.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.wifi.POWER_STATE"


### COMMON_EVENT_WIFI_SCAN_FINISHED

Indicates the action that a Wi-Fi access point has been scanned and proven available.

When a Wi-Fi access point has been scanned and proven available, the event notification service publishing will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.LOCATION

**Value:** "usual.event.wifi.SCAN_FINISHED"


### COMMON_EVENT_WIFI_RSSI_VALUE

  Indicates that the Wi-Fi signal strength (RSSI) changes.

  When the Wi-Fi signal strength (RSSI) changes, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions for subscribers:** ohos.permission.GET_WIFI_INFO

**Value:** "usual.event.wifi.RSSI_VALUE"



### COMMON_EVENT_WIFI_CONN_STATE

  The Wi-Fi connection state changes.

  When the Wi-Fi connection state changes, the event notification service publishing will be triggered to publish this system common event.


**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.wifi.CONN_STATE"


### COMMON_EVENT_WIFI_HOTSPOT_STATE

Indicates the Wi-Fi hotspot state changes.

When the Wi-Fi hotspot state changes, the event notification service will be triggered to publish this system common event.

Status values: 2: AP is being enabled, 3: AP has been enabled, 4: AP is being disabled, 5: AP has been disabled.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.wifi.HOTSPOT_STATE"


### COMMON_EVENT_WIFI_AP_STA_JOIN

Indicates that a client joins the Wi-Fi hotspot of the current device.

When a client joins the Wi-Fi hotspot of the current device, it will trigger the event notification service to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.GET_WIFI_INFO

**Value:** "usual.event.wifi.WIFI_HS_STA_JOIN"


### COMMON_EVENT_WIFI_AP_STA_LEAVE

Indicates that a client has disconnected from the Wi-Fi hotspot of the current device.

When a client has disconnected from the Wi-Fi hotspot of the current device, the event notification service will be triggered to publish this system common event.


**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.GET_WIFI_INFO

**Value:** "usual.event.wifi.WIFI_HS_STA_LEAVE"


### COMMON_EVENT_WIFI_MPLINK_STATE_CHANGE

Indicates that the MPLink (enhanced Wi-Fi) state has changed.

When the MPLink (enhanced Wi-Fi) state changes, the event notification service publishing will be triggered to publish this system common event (not yet supported).


**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.wifi.mplink.STATE_CHANGE"


### COMMON_EVENT_WIFI_P2P_CONN_STATE

Indicates that the Wi-Fi P2P connection state changes.

When the Wi-Fi P2P connection state changes, the event notification service publishing will trigger this system common event.


**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**Value:** "usual.event.wifi.p2p.CONN_STATE_CHANGE"


### COMMON_EVENT_WIFI_P2P_STATE_CHANGED

Indicates the Wi-Fi P2P state change.

When the Wi-Fi P2P state changes, the event notification service publishing will trigger this system common event.

State values: 2: P2P is being enabled, 3: P2P is enabled, 4: P2P is being disabled, 5: P2P is disabled.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.GET_WIFI_INFO

**Value:** "usual.event.wifi.p2p.STATE_CHANGE"


### COMMON_EVENT_WIFI_P2P_PEERS_STATE_CHANGED

Indicates that the Wi-Fi P2P peer state changes.

When the Wi-Fi P2P peer state changes, the event notification service publishing will trigger this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions for subscribers**: ohos.permission.GET_WIFI_INFO

**Value:** "usual.event.wifi.p2p.DEVICES_CHANGE"


### COMMON_EVENT_WIFI_P2P_PEERS_DISCOVERY_STATE_CHANGED

Indicates the Wi-Fi P2P discovery state change.

When the Wi-Fi P2P discovery state changes, the event notification service publishing will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.GET_WIFI_INFO

**Value:** "usual.event.wifi.p2p.PEER_DISCOVERY_STATE_CHANGE"


### COMMON_EVENT_WIFI_P2P_CURRENT_DEVICE_STATE_CHANGED

Indicates the change of the current device state of Wi-Fi P2P.

When the current device state of Wi-Fi P2P changes, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.GET_WIFI_INFO

**Value:** "usual.event.wifi.p2p.CURRENT_DEVICE_CHANGE"


### COMMON_EVENT_WIFI_P2P_GROUP_STATE_CHANGED

Indicates that the Wi-Fi P2P group information has changed.

When the Wi-Fi P2P group information changes, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions for subscribers**: ohos.permission.GET_WIFI_INFO

**Value:** "usual.event.wifi.p2p.GROUP_STATE_CHANGED"

## Core File Kit

### COMMON_EVENT_VOLUME_REMOVED

Indicates that an external storage device was removed.

This common event is triggered when an external storage device is removed.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.STORAGE_MANAGER (for system applications only)

**Value**: usual.event.data.VOLUME_REMOVED

### COMMON_EVENT_VOLUME_UNMOUNTED

Indicates that an external storage device was unmounted.

This common event is triggered when an external storage device is successfully unmounted by calling the **unmount** API or by removing the device.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.STORAGE_MANAGER (for system applications only)

**Value**: usual.event.data.VOLUME_UNMOUNTED

### COMMON_EVENT_VOLUME_MOUNTED

Indicates that an external storage device was mounted.

This common event is triggered when an external storage device is successfully mounted by calling the **mount** API or by inserting the device.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.STORAGE_MANAGER (for system applications only)

**Value**: usual.event.data.VOLUME_MOUNTED

### COMMON_EVENT_VOLUME_BAD_REMOVAL

Indicates that an external storage device was removed without being unmounted.

This common event is triggered when an external storage device is directly removed without being unmounted.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.STORAGE_MANAGER (for system applications only)

**Value**: usual.event.data.VOLUME_BAD_REMOVAL

### COMMON_EVENT_VOLUME_EJECT

Indicates that an external storage device is about to be ejected.

This common event is triggered when the user calls the **unmount** API on a mounted external storage device or removes the device.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** **ohos.permission.STORAGE_MANAGER** (for system applications only)

**Value**: usual.event.data.VOLUME_EJECT

## MDM Kit

### COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED

Indicates that the browser managed policy has changed.

When the browser hosting policy changes, the event notification service is triggered to publish this [system common event](../../../basic-services/common-event/common-event-glossary.md#system-common-event).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.MANAGED_BROWSER_POLICY_CHANGED"


## Localization Kit

### COMMON_EVENT_LOCALE_CHANGED

Indicates that the system language is set.
When the system language is set, the event notification service is triggered to publish this [system common event](../../../basic-services/common-event/common-event-glossary.md#system-common-event).

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.LOCALE_CHANGED"


## Network Kit

### COMMON_EVENT_CONNECTIVITY_CHANGE<sup>10+</sup>

Indicates that the network connection status changes.

When the (Ethernet, Wi-Fi, or cellular) network connection state changes (disconnected, connecting, or connected), the event notification service is triggered to publish this [system common event](../../../basic-services/common-event/common-event-glossary.md#system-common-event).
The following table lists the enum values and their corresponding connection status.

| Enumeration Value | Connection Status |
| ------ | ---------- |
|    2   |   Connecting   |
|    3   |   Connected   |
|    4   |   Disconnecting |
|    5   |   Disconnected   |

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Atomic service API**: This API can be used in atomic services since API version 11.

**Value:** "usual.event.CONNECTIVITY_CHANGE"


### COMMON_EVENT_AIRPLANE_MODE_CHANGED<sup>10+</sup>

Indicates that the airplane mode state changes.

After the system airplane mode is enabled or disabled, this will trigger the event notification service to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.AIRPLANE_MODE"


### COMMON_EVENT_HTTP_PROXY_CHANGE<sup>10+</sup>

Indicates that the network HTTP proxy configuration information is updated.

When the HTTP proxy configuration information of the system global proxy or various networks (Ethernet, Wi-Fi, cellular, etc.) changes, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.HTTP_PROXY_CHANGE"


## Telephony Kit

This topic lists the [system common events](../../../basic-services/common-event/common-event-glossary.md#system-common-event) provided by the telephony subsystem to applications.

### COMMON_EVENT_SIM_STATE_CHANGED<sup>10+</sup>

Indicates that the SIM card state is updated.

When the SIM card state on the device changes, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.SIM_STATE_CHANGED"


### COMMON_EVENT_CALL_STATE_CHANGED<sup>10+</sup>

Indicates a call state update.

When the call state of the device is updated, the common event service is triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions**: ohos.permission.GET_TELEPHONY_STATE (for system applications only)

**Value:** "usual.event.CALL_STATE_CHANGED"


### COMMON_EVENT_NETWORK_STATE_CHANGED<sup>10+</sup>

Indicates that the network state is updated.

When the network state of the device is updated, the common event service is triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** usual.event.NETWORK_STATE_CHANGED


### COMMON_EVENT_SIGNAL_INFO_CHANGED<sup>10+</sup>

Indicates that the signal information is updated.

When the signal information of the device is updated, the common event service is triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.SIGNAL_INFO_CHANGED"


## AppGallery Kit
This topic lists the [system common events](../../../basic-services/common-event/common-event-glossary.md#system-common-event) provided by the AppGallery Kit to applications.

### COMMON_EVENT_PRIVACY_STATE_CHANGED<sup>11+</sup>

Common event that indicates the privacy signing result.

In a privacy dialog box scenario, when the user taps Agree, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PRIVACY_STATE_CHANGED"

## Multimodalinput Kit
This topic lists the [system common events](../../../basic-services/common-event/common-event-glossary.md#system-common-event) provided by the Multimodalinput Kit to applications.

### COMMON_EVENT_TABLET_MODE_CHANGED<sup>23+</sup>

Indicates a device that can sense the opening and closing of its stand, for example, a tablet with a stand. When the stand open/close state changes, the event notification service will be triggered to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Value:** "usual.event.TABLET_MODE_CHANGED"

### COMMON_EVENT_LID_STATE_CHANGED<sup>23+</sup>

Indicates a device that can sense the opening and closing of its lid, for example, a laptop with an openable and closable lid. When the lid state changes, it will trigger the event notification service to publish this system common event.

**System capability**: SystemCapability.Notification.CommonEvent

**Value:** usual.event.LID_STATE_CHANGED

## Reserved Common Event

Below are reserved common events that are not supported yet.

### COMMON_EVENT_LOCKED_BOOT_COMPLETED

(Reserved event, not yet supported) Indicates that the user has completed boot, the system has been loaded, but the screen is still locked.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.LOCKED_BOOT_COMPLETED"


### COMMON_EVENT_PACKAGE_FIRST_LAUNCH

(Reserved event, not yet supported) The application program is launched for the first time after installation.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PACKAGE_FIRST_LAUNCH"


### COMMON_EVENT_PACKAGE_NEEDS_VERIFICATION

(Reserved event, not yet supported) Sent by the system package verifier when a package needs to be verified.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PACKAGE_NEEDS_VERIFICATION"


### COMMON_EVENT_PACKAGE_VERIFIED

(Reserved event, not yet supported) Sent by the system package verifier when a package is verified.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PACKAGE_VERIFIED"

### COMMON_EVENT_PACKAGE_REPLACED

(Reserved event, not yet supported) Indicates the action of installing a new version of an application package on the device and replacing the old version. The data contains the package name.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PACKAGE_REPLACED"


### COMMON_EVENT_MY_PACKAGE_REPLACED

(Reserved event, not yet supported) Indicates the action of installing a new version of an application package on the device and replacing the old version. It does not contain extra data and is sent only to the replaced application.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.MY_PACKAGE_REPLACED"


### COMMON_EVENT_PACKAGES_UNSUSPENDED

(Reserved event, not yet supported) Indicates that the package has been unsuspended.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.PACKAGES_UNSUSPENDED"


### COMMON_EVENT_CLOSE_SYSTEM_DIALOGS

(Reserved event, not yet supported) Indicates the action of the common event that a user closes a temporary system dialog box.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.CLOSE_SYSTEM_DIALOGS"



### COMMON_EVENT_UID_REMOVED

(Reserved event, not yet supported) Indicates the action of the common event that the user ID has been removed from the system.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value**: usual.event.UID_REMOVED


### COMMON_EVENT_EXTERNAL_APPLICATIONS_AVAILABLE

(Reserved event, not yet supported) Indicates the operation of the common event that makes applications installed on external storage available to the system.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.EXTERNAL_APPLICATIONS_AVAILABLE"


### COMMON_EVENT_EXTERNAL_APPLICATIONS_UNAVAILABLE

(Reserved event, not yet supported) Indicates the operation of the common event that application programs installed on external storage are unavailable to the system.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.EXTERNAL_APPLICATIONS_UNAVAILABLE"


### COMMON_EVENT_CONFIGURATION_CHANGED

(Reserved event, not yet supported) Indicates the action of the common event that the device status (for example, orientation and locale) has changed.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.CONFIGURATION_CHANGED"



### COMMON_EVENT_DRIVE_MODE
(Reserved event, not yet supported) Indicates the action of the common event that the system is in drive mode.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.DRIVE_MODE"



### COMMON_EVENT_HOME_MODE
(Reserved event, not yet supported) Indicates the action of the common event that the system is in HOME mode.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.HOME_MODE"



### COMMON_EVENT_OFFICE_MODE
(Reserved event, not yet supported) Indicates the action of the common event indicating that the system is in office mode.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.OFFICE_MODE"



### COMMON_EVENT_USER_STARTED

(Reserved event, not yet supported) Indicates the action of the common event that the user has started.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value**: usual.event.USER_STARTED


### COMMON_EVENT_USER_BACKGROUND

(Reserved event, not yet supported) Indicates the action of the common event that the user has been brought to the background.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value**: usual.event.USER_BACKGROUND


### COMMON_EVENT_USER_STARTING
(Reserved event, not yet supported) Indicates the action of the common event for starting a user.

**System capability**: SystemCapability.Notification.CommonEvent

Required permissions: **ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS** (for system applications only)

**Value**: usual.event.USER_STARTING



### COMMON_EVENT_USER_STOPPING
(Reserved event, not yet supported) Indicates the action of the common event for stopping a user.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS (for system applications only)

**Value**: usual.event.USER_STOPPING


### COMMON_EVENT_USER_STOPPED
(Reserved event, not yet supported) Indicates the action of the common event that the user has stopped.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value**: usual.event.USER_STOPPED


### COMMON_EVENT_DISK_REMOVED

(Reserved event, not yet supported) Sent when the external storage device status changes to removed.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.STORAGE_MANAGER (for system applications only)

**Value**: usual.event.data.DISK_REMOVED


### COMMON_EVENT_DISK_UNMOUNTED

(Reserved event, not yet supported) This common event is sent when the status of an external storage device changes to unmounted.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.STORAGE_MANAGER (for system applications only)

**Value:** "usual.event.data.DISK_UNMOUNTED"


### COMMON_EVENT_DISK_MOUNTED

(Reserved event, not yet supported) This common event is sent when the status of an external storage device changes to mounted.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** **ohos.permission.STORAGE_MANAGER** (for system applications only)

**Value:** usual.event.data.DISK_MOUNTED



### COMMON_EVENT_DISK_BAD_REMOVAL

(Reserved event, not yet supported) This common event is published when the external storage device is removed while in the mounted state.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.STORAGE_MANAGER (for system applications only)

**Value**: usual.event.data.DISK_BAD_REMOVAL


### COMMON_EVENT_DISK_UNMOUNTABLE

(Reserved event, not yet supported) This common event is sent when the external storage device status changes to a state where it cannot be mounted while a card is inserted.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.STORAGE_MANAGER (for system applications only)

**Value:** "usual.event.data.DISK_UNMOUNTABLE"


### COMMON_EVENT_DISK_EJECT

(Reserved event, not yet supported) This common event is sent when the user has indicated the desire to remove the external storage medium.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** **ohos.permission.STORAGE_MANAGER** (for system applications only)

**Value**: usual.event.data.DISK_EJECT


### COMMON_EVENT_DATE_CHANGED

(Reserved event, not yet supported) Indicates the action of the common event that the system date has changed.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.DATE_CHANGED"

### COMMON_EVENT_USB_ACCESSORY_ATTACHED

Indicates the action of the common event that a USB accessory is attached.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.hardware.usb.action.USB_ACCESSORY_ATTACHED"


### COMMON_EVENT_USB_ACCESSORY_DETACHED

Indicates the action of the common event that a USB accessory is detached.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.hardware.usb.action.USB_ACCESSORY_DETACHED"

### COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Action of the common event for the Bluetooth hands-free communication connection state.

  > **NOTE**
  >
  > This event is supported since API version 9 and deprecated since API version 20. You are advised to use [COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CONNECT_STATE_CHANGE](#common_event_bluetooth_handsfree_ag_connect_state_change20) instead.

**System capability**: SystemCapability.Notification.CommonEvent

Required permissions: **ohos.permission.USE_BLUETOOTH**

Value: **"usual.event.bluetooth.handsfree.ag.CONNECT_STATE_UPDATE"**



### COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_CURRENT_DEVICE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that a device connected to the Bluetooth handsfree is in the active state.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** **ohos.permission.USE_BLUETOOTH**

**Value:** **"usual.event.bluetooth.handsfree.ag.CURRENT_DEVICE_UPDATE"**


### COMMON_EVENT_BLUETOOTH_HANDSFREE_AG_AUDIO_STATE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that the Bluetooth A2DP connection state has changed.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.handsfree.ag.AUDIO_STATE_UPDATE"




### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Action of the Bluetooth A2DP connection state common event.

  > **NOTE**
  >
  > This interface supports since API version 9 and is deprecated since API version 20. You are advised to use [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CONNECT_STATE_CHANGE](#common_event_bluetooth_a2dpsource_connect_state_change20) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** **ohos.permission.USE_BLUETOOTH**

**Value:** **"usual.event.bluetooth.a2dpsource.CONNECT_STATE_UPDATE"**




### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CURRENT_DEVICE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that a device connected via Bluetooth A2DP is in the active state.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.a2dpsource.CURRENT_DEVICE_UPDATE"



### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that the AVRCP connection state of Bluetooth A2DP has changed.

  > **NOTE**
  >
  > This interface is supported since API version 9 and deprecated since API version 20. You are advised to use [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_AVRCP_CONNECT_STATE_CHANGE](#common_event_bluetooth_a2dpsource_avrcp_connect_state_change20) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.a2dpsource.AVRCP_CONNECT_STATE_UPDATE"



### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_PLAYING_STATE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Action of the common event indicating that the Bluetooth A2DP playing state changes.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.a2dpsource.PLAYING_STATE_UPDATE"



### COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event for Bluetooth A2DP audio codec state changes.

  > **NOTE**
  >
  > This event is supported since API version 9 and deprecated since API version 20. You are advised to use [COMMON_EVENT_BLUETOOTH_A2DPSOURCE_CODEC_VALUE_CHANGE](#common_event_bluetooth_a2dpsource_codec_value_change20) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.a2dpsource.CODEC_VALUE_UPDATE"




### COMMON_EVENT_USER_FOREGROUND

(Reserved event, not yet supported) Action of the common event indicating that the user has been brought to the foreground.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value**: usual.event.USER_FOREGROUND




### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_DISCOVERED<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event for discovering a remote Bluetooth device.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.LOCATION and ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.remotedevice.DISCOVERED"




### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CLASS_VALUE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that the Bluetooth class of a remote Bluetooth device has changed.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.remotedevice.CLASS_VALUE_UPDATE"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_CONNECTED<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that a low-level (ACL) connection has been established with a remote Bluetooth device.

  > **NOTE**
  >
  > This interface is supported since API version 9 and deprecated since API version 20. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE](#common_event_bluetooth_remotedevice_acl_state_change20) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.remotedevice.ACL_CONNECTED"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_DISCONNECTED<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that the low-level (ACL) connection has been disconnected from the remote Bluetooth device.

  > **NOTE**
  >
  > This event is supported since API version 9 and deprecated since API version 20. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_ACL_STATE_CHANGE](#common_event_bluetooth_remotedevice_acl_state_change20) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** **ohos.permission.USE_BLUETOOTH**

**Value:** **"usual.event.bluetooth.remotedevice.ACL_DISCONNECTED"**


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_NAME_UPDATE<sup>(deprecated)</sup>

(Reserved event, not yet supported) Indicates the operation of the common event that the friendly name of a remote Bluetooth device is retrieved for the first time or has been changed since the last retrieval.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.remotedevice.NAME_UPDATE"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Action of the common event indicating that the connection state of a remote Bluetooth device changes.

  > **NOTE**
  >
  > This event is supported since API version 9 and deprecated since API version 20. You are advised to use [COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIR_STATE_CHANGE](#common_event_bluetooth_remotedevice_pair_state_change20) instead.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.remotedevice.PAIR_STATE"



### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_BATTERY_VALUE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that the battery level of a remote Bluetooth device is retrieved for the first time or has changed since the last retrieval.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

Required permissions: **ohos.permission.USE_BLUETOOTH**

Value: **usual.event.bluetooth.remotedevice.BATTERY_VALUE_UPDATE**


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_SDP_RESULT<sup>(deprecated)</sup>
(Reserved event, not yet supported) Action of the common event for the SDP status of a remote Bluetooth device.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.remotedevice.SDP_RESULT"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_UUID_VALUE<sup>(deprecated)</sup>
Action of the common event for the UUID connection status of a remote Bluetooth device.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.remotedevice.UUID_VALUE"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_REQ<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event for a remote Bluetooth device pairing request.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.DISCOVER_BLUETOOTH

**Value:** "usual.event.bluetooth.remotedevice.PAIRING_REQ"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_PAIRING_CANCEL<sup>(deprecated)</sup>
(Reserved event, not yet supported) Action of the common event for canceling Bluetooth pairing.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.remotedevice.PAIRING_CANCEL"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REQ<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event for a remote Bluetooth device connection request.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.remotedevice.CONNECT_REQ"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_REPLY<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event for the remote Bluetooth device connection request response.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.remotedevice.CONNECT_REPLY"


### COMMON_EVENT_BLUETOOTH_REMOTEDEVICE_CONNECT_CANCEL<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event for canceling the connection to a remote Bluetooth device.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.remotedevice.CONNECT_CANCEL"


### COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_CONNECT_STATE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that the Bluetooth hands-free unit connection state has changed.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.handsfreeunit.CONNECT_STATE_UPDATE"


### COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AUDIO_STATE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that the Bluetooth hands-free audio state has changed.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.handsfreeunit.AUDIO_STATE_UPDATE"


### COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_COMMON_EVENT<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that the Bluetooth handsfree audio gateway state has changed.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.handsfreeunit.AG_COMMON_EVENT"


### COMMON_EVENT_BLUETOOTH_HANDSFREEUNIT_AG_CALL_STATE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that the Bluetooth hands-free call state has changed.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.handsfreeunit.AG_CALL_STATE_UPDATE"


### COMMON_EVENT_BLUETOOTH_HOST_STATE_UPDATE<sup>(deprecated)</sup>
Indicates the action of the common event that the Bluetooth adapter state has changed, for example, Bluetooth is turned on or off.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.host.STATE_UPDATE"


### COMMON_EVENT_BLUETOOTH_HOST_REQ_DISCOVERABLE<sup>(deprecated)</sup>

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

(Reserved event, not yet supported) Indicates the action of the common event that a user allows a Bluetooth scan request.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.bluetooth.host.REQ_DISCOVERABLE"


### COMMON_EVENT_BLUETOOTH_HOST_REQ_ENABLE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event for a user request to enable Bluetooth.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

Required permissions: **ohos.permission.USE_BLUETOOTH**

Value: **"usual.event.bluetooth.host.REQ_ENABLE"**



### COMMON_EVENT_BLUETOOTH_HOST_REQ_DISABLE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event for a user request to disable Bluetooth.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.host.REQ_DISABLE"


### COMMON_EVENT_BLUETOOTH_HOST_SCAN_MODE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Action of the common event indicating that the device Bluetooth scan mode changes.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.host.SCAN_MODE_UPDATE"




### COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_STARTED<sup>(deprecated)</sup>
Action of the common event indicating that Bluetooth scanning has started on the device.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.host.DISCOVERY_STARTED"


### COMMON_EVENT_BLUETOOTH_HOST_DISCOVERY_FINISHED<sup>(deprecated)</sup>
Action of the common event indicating that Bluetooth scanning is finished on the device.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.host.DISCOVERY_FINISHED"


### COMMON_EVENT_BLUETOOTH_HOST_NAME_UPDATE<sup>(deprecated)</sup>
Indicates the operation of the common event that the name of the device Bluetooth adapter has changed.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Value:** "usual.event.bluetooth.host.NAME_UPDATE"


### COMMON_EVENT_BLUETOOTH_A2DPSINK_CONNECT_STATE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that the Bluetooth A2DP connection state changes.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.a2dpsink.CONNECT_STATE_UPDATE"



### COMMON_EVENT_BLUETOOTH_A2DPSINK_PLAYING_STATE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Action of the common event for Bluetooth A2DP playback state changes.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.a2dpsink.PLAYING_STATE_UPDATE"


### COMMON_EVENT_BLUETOOTH_A2DPSINK_AUDIO_STATE_UPDATE<sup>(deprecated)</sup>
(Reserved event, not yet supported) Indicates the action of the common event that the audio state of the Bluetooth A2DP sink has changed.

  > **NOTE**
  >
  > This API is supported since API version 9 and deprecated since API version 20.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.USE_BLUETOOTH

**Value:** "usual.event.bluetooth.a2dpsink.AUDIO_STATE_UPDATE"


### COMMON_EVENT_ABILITY_ADDED
(Reserved event, not yet supported) Indicates the action of the common event for an added ability.

**System capability**: SystemCapability.Notification.CommonEvent

Required permissions: **ohos.permission.LISTEN_BUNDLE_CHANGE**

**Value**: usual.event.ABILITY_ADDED


### COMMON_EVENT_ABILITY_REMOVED
(Reserved event, not yet supported) Indicates the action of the common event for a removed ability.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.LISTEN_BUNDLE_CHANGE

**Value**: usual.event.ABILITY_REMOVED



### COMMON_EVENT_ABILITY_UPDATED
(Reserved event, not yet supported) Indicates the action of the common event that the ability has been updated.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** ohos.permission.LISTEN_BUNDLE_CHANGE

**Value:** "usual.event.ABILITY_UPDATED"


### COMMON_EVENT_LOCATION_MODE_STATE_CHANGED
(Reserved event, not yet supported) Action of the common event indicating that the system location mode has changed.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.location.MODE_STATE_CHANGED"


### COMMON_EVENT_IVI_SLEEP
(Reserved event, not yet supported) Indicates the action of the common event that the in-vehicle infotainment (IVI) system of the vehicle is sleeping.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.IVI_SLEEP"


### COMMON_EVENT_IVI_PAUSE
(Reserved event, not yet supported) Indicates that the IVI has entered sleep mode and notifies the application program to stop playing.


**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.IVI_PAUSE"



### COMMON_EVENT_IVI_STANDBY
(Reserved event, not yet supported) Indicates the action of the common event that a third-party application pauses the current work.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.IVI_STANDBY"


### COMMON_EVENT_IVI_LASTMODE_SAVE
(Reserved event, not yet supported) Indicates the action of the common event for a third-party application to save its last mode.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.IVI_LASTMODE_SAVE"


### COMMON_EVENT_IVI_VOLTAGE_ABNORMAL
(Reserved event, not yet supported) Indicates the action of the common event that the vehicle power system voltage is abnormal.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.IVI_VOLTAGE_ABNORMAL"


### COMMON_EVENT_IVI_HIGH_TEMPERATURE

(Reserved event, not yet supported) Indicates that the IVI temperature is too high.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.IVI_HIGH_TEMPERATURE"


### COMMON_EVENT_IVI_EXTREME_TEMPERATURE
(Reserved event, not yet supported) Indicates that the IVI temperature is extremely high.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.IVI_EXTREME_TEMPERATURE"



### COMMON_EVENT_IVI_TEMPERATURE_ABNORMAL
(Reserved event, not yet supported) Indicates the action of the common event that the in-vehicle system has an extreme temperature.


**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.IVI_TEMPERATURE_ABNORMAL"


### COMMON_EVENT_IVI_VOLTAGE_RECOVERY
(Reserved event, not yet supported) Indicates the action of the common event that the voltage of the vehicle power system recovers to normal.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.IVI_VOLTAGE_RECOVERY"


### COMMON_EVENT_IVI_TEMPERATURE_RECOVERY
(Reserved event, not yet supported) Indicates the action of the common event that the in-vehicle system temperature returns to normal.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.IVI_TEMPERATURE_RECOVERY"


### COMMON_EVENT_IVI_ACTIVE
(Reserved event, not yet supported) Indicates the action of the common event that the battery service is in the active state.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "common.event.IVI_ACTIVE"



### COMMON_EVENT_VISIBLE_ACCOUNTS_UPDATED
(Reserved event, not yet supported) Indicates the action of the common event for visible account changes.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions**: ohos.permission.GET_APP_ACCOUNTS (for system applications only)

**Value:** "usual.event.data.VISIBLE_ACCOUNTS_UPDATED"


### COMMON_EVENT_ACCOUNT_DELETED
(Reserved event, not yet supported) Action of the common event for deleting an account.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions:** **ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS** (for system applications only)

**Value:** **usual.event.data.ACCOUNT_DELETED**



### COMMON_EVENT_FOUNDATION_READY
(Reserved event, not yet supported) Indicates the action of the common event that the foundation is ready.

**System capability**: SystemCapability.Notification.CommonEvent

**Required permissions**: ohos.permission.RECEIVER_STARTUP_COMPLETED (for system applications only)

**Value:** "usual.event.data.FOUNDATION_READY"



### COMMON_EVENT_SPN_INFO_CHANGED
Indicates the action of the common event that the SPN display information has been updated.

**System capability**: SystemCapability.Notification.CommonEvent

**Required Permissions:** none

**Value:** "usual.event.SPN_INFO_CHANGED"
<!--no_check-->
