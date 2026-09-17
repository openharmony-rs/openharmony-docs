# Support

System common events are events published by system services or system apps. Subscribing to these common events requires specific permissions and event values.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

## COMMON_EVENT_USER_LOCKING

```TypeScript
COMMON_EVENT_USER_LOCKING = 'usual.event.USER_LOCKING'
```

Indicates that a user is about to be locked.

Before a user is locked, the common event service is triggered to publish this event carrying the system account ID.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_USER_LOCKED

```TypeScript
COMMON_EVENT_USER_LOCKED = 'usual.event.USER_LOCKED'
```

Indicates that a user is locked.

After a user is locked, the common event service is triggered to publish this event carrying the system account ID.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_CREATED

```TypeScript
COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_CREATED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_CREATED'
```

Indicates an OS account sub-profile is created.

After an OS account sub-profile is created, the common event service is triggered to publish this event carrying the OS account local ID and the sub-profile ID.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_DELETED

```TypeScript
COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_DELETED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_DELETED'
```

Indicates an OS account sub-profile is deleted.

After an OS account sub-profile is deleted, the common event service is triggered to publish this event carrying the OS account local ID and the sub-profile ID.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHING

```TypeScript
COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHING = 'usual.event.OS_ACCOUNT_SUB_PROFILE_SWITCHING'
```

Indicates an OS account sub-profile is switching.

After an OS account sub-profile is switching, the common event service is triggered to publish this event carrying the OS account local ID, the sub-profile ID switching to and the previous sub-profile ID switching from.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHED

```TypeScript
COMMON_EVENT_OS_ACCOUNT_SUB_PROFILE_SWITCHED = 'usual.event.OS_ACCOUNT_SUB_PROFILE_SWITCHED'
```

Indicates an OS account sub-profile is switched.

After an OS account sub-profile is switched, the common event service is triggered to publish this event carrying the OS account local ID, the sub-profile ID switched to and the previous sub-profile ID switched from.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_BOUND

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_BOUND = 'usual.event.DISTRIBUTED_ACCOUNT_BOUND'
```

Indicates a distributed account is bound.

After a distributed account is bound, the common event service is triggered to publish this event carrying the OS account local ID and the sub-profile ID.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_DISTRIBUTED_ACCOUNT_UNBOUND

```TypeScript
COMMON_EVENT_DISTRIBUTED_ACCOUNT_UNBOUND = 'usual.event.DISTRIBUTED_ACCOUNT_UNBOUND'
```

Indicates a distributed account is unbound.

After a distributed account is unbound, the common event service is triggered to publish this event carrying the OS account local ID and the sub-profile ID.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_CHARGE_TYPE_CHANGED

```TypeScript
COMMON_EVENT_CHARGE_TYPE_CHANGED = 'usual.event.CHARGE_TYPE_CHANGED'
```

Indicates that the system charging type has changed.

When the system charging type changes, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_DEVICE_IDLE_EXEMPTION_LIST_UPDATED

```TypeScript
COMMON_EVENT_DEVICE_IDLE_EXEMPTION_LIST_UPDATED = 'usual.event.DEVICE_IDLE_EXEMPTION_LIST_UPDATED'
```

Indicates that the exemption list for resource usage restrictions has been updated in idle mode.

When the exemption list for resource usage restrictions is updated, the common event service is triggered to publish this event.

Resources include application network access, Timer usage, and WorkScheduler task usage.

System applications can call JavaScript APIs to apply for removing resource usage restrictions.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_USB_CONTROL_DATA

```TypeScript
COMMON_EVENT_USB_CONTROL_DATA = 'usual.event.hardware.usb.action.USB_CONTROL_DATA'
```

Indicates that the local host receives a user-defined control transmission request from the USB host. This is a protected common event that can only be sent by system.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_DISK_VOLUME_STATE_CHANGE

```TypeScript
COMMON_EVENT_DISK_VOLUME_STATE_CHANGE = 'usual.event.data.DISK_VOLUME_STATE_CHANGE'
```

Indicates that the state of a system data disk volume has changed.

This common event is triggered when the state of a system data disk volume changes, such as during format or repair operations (started, succeeded, or failed).

To subscribe to this common event, your application must have the **ohos.permission.STORAGE_MANAGER** permission. (This permission is available only for system applications.)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_APP_FIRST_LAUNCH

```TypeScript
COMMON_EVENT_APP_FIRST_LAUNCH = 'usual.event.APP_FIRST_LAUNCH'
```

Indicates that when the application is launched for the first time after installation, the common event service is triggered to publish this system common event.

Model constraint: This API can be used only in the stage model.

To subscribe to this common event, your application must have the ohos.permission.INSTALL_BUNDLE permission.(This permission is available only for system applications.)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SMS_RECEIVE_COMPLETED

```TypeScript
COMMON_EVENT_SMS_RECEIVE_COMPLETED = 'usual.event.SMS_RECEIVE_COMPLETED'
```

Indicates that an SMS message is received.

When the device receives an SMS message, the common event service is triggered to publish this event.

To subscribe to this common event, your application must have the ohos.permission.RECEIVE_SMS permission.(This permission is available only for system applications.)

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SMS_EMERGENCY_CB_RECEIVE_COMPLETED

```TypeScript
COMMON_EVENT_SMS_EMERGENCY_CB_RECEIVE_COMPLETED = 'usual.event.SMS_EMERGENCY_CB_RECEIVE_COMPLETED'
```

Indicates that an emergency cell broadcast message is received.

When the device receives an emergency cell broadcast message, the common event service is triggered to publish this event.

To subscribe to this common event, your application must have the ohos.permission.RECEIVE_SMS permission.(This permission is available only for system applications.)

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SMS_CB_RECEIVE_COMPLETED

```TypeScript
COMMON_EVENT_SMS_CB_RECEIVE_COMPLETED = 'usual.event.SMS_CB_RECEIVE_COMPLETED'
```

Indicates that a cell broadcast message is received.

When the device receives a cell broadcast message, the common event service is triggered to publish this event.

To subscribe to this common event, your application must have the ohos.permission.RECEIVE_SMS permission.(This permission is available only for system applications.)

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_STK_COMMAND

```TypeScript
COMMON_EVENT_STK_COMMAND = 'usual.event.STK_COMMAND'
```

(Reserved, not supported yet) Indicates that an STK command is sent.

When an STK command is sent, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_STK_SESSION_END

```TypeScript
COMMON_EVENT_STK_SESSION_END = 'usual.event.STK_SESSION_END'
```

(Reserved, not supported yet) Indicates that an STK session has ended.

When an STK session ends, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_STK_CARD_STATE_CHANGED

```TypeScript
COMMON_EVENT_STK_CARD_STATE_CHANGED = 'usual.event.STK_CARD_STATE_CHANGED'
```

(Reserved, not supported yet) Indicates that the STK card state has been updated.

When the STK card state is updated, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_STK_ALPHA_IDENTIFIER

```TypeScript
COMMON_EVENT_STK_ALPHA_IDENTIFIER = 'usual.event.STK_ALPHA_IDENTIFIER'
```

(Reserved, not supported yet) Indicates that an STK Alpha identifier is sent.

When an STK Alpha identifier is sent, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SMS_WAPPUSH_RECEIVE_COMPLETED

```TypeScript
COMMON_EVENT_SMS_WAPPUSH_RECEIVE_COMPLETED = 'usual.event.SMS_WAPPUSH_RECEIVE_COMPLETED'
```

(Reserved, not supported yet) Indicates that a WAP push message is received.

When the device receives a WAP push message, the common event service is triggered to publish this event.

To subscribe to this common event, your application must have the ohos.permission.RECEIVE_SMS permission.(This permission is available only for system applications.)

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_OPERATOR_CONFIG_CHANGED

```TypeScript
COMMON_EVENT_OPERATOR_CONFIG_CHANGED = 'usual.event.OPERATOR_CONFIG_CHANGED'
```

Indicates that the carrier configuration has been updated.

When the carrier configuration of the device is updated, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SIM_CARD_DEFAULT_SMS_SUBSCRIPTION_CHANGED

```TypeScript
COMMON_EVENT_SIM_CARD_DEFAULT_SMS_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_SMS_SUBSCRIPTION_CHANGED'
```

Indicates that the default primary SIM card for the SMS service has been updated.

When the default primary SIM card for the SMS service is updated, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SIM_CARD_DEFAULT_DATA_SUBSCRIPTION_CHANGED

```TypeScript
COMMON_EVENT_SIM_CARD_DEFAULT_DATA_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_DATA_SUBSCRIPTION_CHANGED'
```

Indicates that the default primary SIM card for the data service has been updated.

When the default primary SIM card for the data service is updated, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SIM_CARD_DEFAULT_MAIN_SUBSCRIPTION_CHANGED

```TypeScript
COMMON_EVENT_SIM_CARD_DEFAULT_MAIN_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_MAIN_SUBSCRIPTION_CHANGED'
```

Indicates that the default primary SIM card of the device has been updated.

When the default primary SIM card of the device is updated, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SET_PRIMARY_SLOT_STATUS

```TypeScript
COMMON_EVENT_SET_PRIMARY_SLOT_STATUS = 'usual.event.SET_PRIMARY_SLOT_STATUS'
```

Indicates that the status of the action for setting the primary SIM card changes.

When the status of the action for setting the primary SIM card changes (for example, when the status is updated to executing or completed), the common event service is triggered to publish this event.

**Since:** 11

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_PRIMARY_SLOT_ROAMING

```TypeScript
COMMON_EVENT_PRIMARY_SLOT_ROAMING = 'usual.event.PRIMARY_SLOT_ROAMING'
```

Indicates that the roaming status of the default primary SIM card is updated.

When the roaming status of the default primary SIM card changes, the common event service is triggered to publish this event.

**Since:** 11

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SIM_CARD_DEFAULT_VOICE_SUBSCRIPTION_CHANGED

```TypeScript
COMMON_EVENT_SIM_CARD_DEFAULT_VOICE_SUBSCRIPTION_CHANGED = 'usual.event.SIM.DEFAULT_VOICE_SUBSCRIPTION_CHANGED'
```

Indicates that the default primary SIM card for the voice service has been updated.

When the default primary SIM card for the voice service is updated, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_CELLULAR_DATA_STATE_CHANGED

```TypeScript
COMMON_EVENT_CELLULAR_DATA_STATE_CHANGED = 'usual.event.CELLULAR_DATA_STATE_CHANGED'
```

Indicates that the cellular data state has been updated.

When the cellular data state of the device is updated, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_INCOMING_CALL_MISSED

```TypeScript
COMMON_EVENT_INCOMING_CALL_MISSED = 'usual.event.INCOMING_CALL_MISSED'
```

Indicates that an incoming call is missed.

When an incoming call is missed on the device, the common event service is triggered to publish this event.

To subscribe to this common event, your application must have the ohos.permission.GET_TELEPHONY_STATE permission. (This permission is available only for system applications.)

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_RADIO_STATE_CHANGE

```TypeScript
COMMON_EVENT_RADIO_STATE_CHANGE = 'usual.event.RADIO_STATE_CHANGE'
```

Indicates that the radio state of the device modem has changed.

When there is a change in the radio state of the device modem, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_DOMAIN_ACCOUNT_STATUS_CHANGED

```TypeScript
COMMON_EVENT_DOMAIN_ACCOUNT_STATUS_CHANGED = 'usual.event.DOMAIN_ACCOUNT_STATUS_CHANGED'
```

Indicates that domain account status changes.

When a domain user account is authenticated, deleted, or has the token updated, the common event service is triggered to publish this event carrying the system account ID, domain name, and account status.

The system APIs related to this common event are **removeOsAccount**, **DomainAccountManager.auth**, and **updateAccountToken**. For details, see [@ohos.account.osAccount (System Account Management)](../../../reference/js-apis-osAccount.md).

To subscribe to this common event, your application must have the ohos.permission.GET_LOCAL_ACCOUNTS permission.(This permission is available only for system applications.)

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SCREEN_LOCK_EXITING

```TypeScript
COMMON_EVENT_SCREEN_LOCK_EXITING = 'usual.event.SCREEN_LOCK_EXITING'
```

This commonEvent means when the screen lock is exiting.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SPECIAL_CODE

```TypeScript
COMMON_EVENT_SPECIAL_CODE = 'common.event.SPECIAL_CODE'
```

Indicates that a secret code is sent successfully.

When a secret code is successfully sent on the device, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_AUDIO_QUALITY_CHANGE

```TypeScript
COMMON_EVENT_AUDIO_QUALITY_CHANGE = 'usual.event.AUDIO_QUALITY_CHANGE'
```

Indicates that the audio quality has changed.

When there is a change in the audio quality of the device, the common event service is triggered to publish this event.

**Since:** 10

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_PRIVACY_STATE_CHANGED

```TypeScript
COMMON_EVENT_PRIVACY_STATE_CHANGED = 'usual.event.PRIVACY_STATE_CHANGED'
```

Indicates the privacy state has been changed.

When a user taps the agree button in the privacy statement dialog box, the event notification service is triggered to publish this event.

**Since:** 11

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_PACKAGE_INSTALLATION_STARTED

```TypeScript
COMMON_EVENT_PACKAGE_INSTALLATION_STARTED = 'usual.event.PACKAGE_INSTALLATION_STARTED'
```

Indicates that a package is sent by the system verifier when the package is verified.

When a new application starts to be installed by a specified user on the device, the common event service is triggered to publish this event.

**Since:** 12

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_DYNAMIC_ICON_CHANGED

```TypeScript
COMMON_EVENT_DYNAMIC_ICON_CHANGED = 'usual.event.DYNAMIC_ICON_CHANGED'
```

This common event means an application package enables or disables a dynamic icon. This is a protected common event that can only be sent by system.

**Since:** 12

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_BUNDLE_RESOURCES_CHANGED

```TypeScript
COMMON_EVENT_BUNDLE_RESOURCES_CHANGED = 'usual.event.BUNDLE_RESOURCES_CHANGED'
```

Indicates that the bundle management resource data has updated.

This common event is sent when the bundle management resource data is updated in scenarios such as language or theme switching.

To subscribe to this common event, your application must have the ohos.permission.GET_BUNDLE_RESOURCES permission.

**Since:** 15

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_VPN_CONNECTION_STATUS_CHANGED

```TypeScript
COMMON_EVENT_VPN_CONNECTION_STATUS_CHANGED = 'usual.event.VPN_CONNECTION_STATUS_CHANGED'
```

Indicates the common event that the VPN connection status has changed.

This common event is sent when a VPN connection is established or disconnected.

**Since:** 12

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_RESTORE_START

```TypeScript
COMMON_EVENT_RESTORE_START = 'usual.event.RESTORE_START'
```

Indicates that an application starts to be restored.

When a data migration application starts the backup and restore framework to perform a restoration task, the common event service is triggered to publish this event.

To subscribe to this common event, your application must have the ohos.permission.START_RESTORE_NOTIFICATION permission.

**Since:** 13

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_DEFAULT_APPLICATION_CHANGED

```TypeScript
COMMON_EVENT_DEFAULT_APPLICATION_CHANGED = 'usual.event.DEFAULT_APPLICATION_CHANGED'
```

Indicates that the default application for opening a file has changed.

This common event is sent when the default application for opening a file changes.

To subscribe to this common event, your application must have the ohos.permission.CHANGE_DEFAULT_APPLICATION permission.

**Since:** 19

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SHORTCUT_CHANGED

```TypeScript
COMMON_EVENT_SHORTCUT_CHANGED = 'usual.event.SHORTCUT_CHANGED'
```

Indicates that the application shortcut has changed.

This common event is sent when the shortcut is changed (for example, when [shortcutManager.setShortcutVisibleForSelf](../../../apis-ability-kit/js-apis-shortcutManager.md#shortcutmanagersetshortcutvisibleforself) of the shortcutManager module is successfully called).

To subscribe to this common event, your application must have the ohos.permission.MANAGE_SHORTCUTS permission.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_CUSTOM_CONFIG_POLICY_UPDATED

```TypeScript
COMMON_EVENT_CUSTOM_CONFIG_POLICY_UPDATED = 'usual.event.CUSTOM_CONFIG_POLICY_UPDATED'
```

Indicates that the configuration directory level and system parameters of a device are updated.

This common event is sent when the system updates the device configuration directory level and system parameters after identifying the home area and roaming area of the device.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_CUSTOM_ROAMING_REGION_UPDATED

```TypeScript
COMMON_EVENT_CUSTOM_ROAMING_REGION_UPDATED = 'usual.event.CUSTOM_ROAMING_REGION_UPDATED'
```

Indicates that the roaming area of a device is updated.

When the attributes such as network injection, persistent connection, and GPS location of a device change, the system identifies the roaming area and updates the parameters if the roaming area changes. After the update is complete, this common event is sent.

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SCREEN_SHARE

```TypeScript
COMMON_EVENT_SCREEN_SHARE = 'usual.event.SCREEN_SHARE'
```

Indicates that a screen sharing event has occurred in the system.

This is a protected common event and can be sent only by the system.

To subscribe to this common event, your application must have the ohos.permission.RECEIVE_SMS permission.(This permission is available only for system applications.)

**Since:** 20

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_RESTORE_END

```TypeScript
COMMON_EVENT_RESTORE_END = 'usual.event.RESTORE_END'
```

Represents the common event indicating the restore is complete for an application. When a data migration application starts the backup and restore framework to perform a restoration task, this common event is sent when the restore is complete.

To subscribe to this common event, your application must have the ohos.permission.RESTORE_END_NOTIFICATION permission.(This permission is available only for system applications.)

**Since:** 23

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_CLOUD_DISK_STATE_CHANGED

```TypeScript
COMMON_EVENT_CLOUD_DISK_STATE_CHANGED = 'usual.event.CLOUD_DISK_STATE_CHANGED'
```

Indicates that the sync root of the cloud disk has been updated.

When the sync root update is complete, the common event service is triggered to publish this event.

To subscribe to this common event, your application must have the ohos.permission.ACCESS_CLOUD_DISK_INFO permission.(This permission is available only for system applications.)

**Since:** 21

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_DATA_VOLUME_STATUS_REPORT

```TypeScript
COMMON_EVENT_DATA_VOLUME_STATUS_REPORT = 'usual.event.DATA_VOLUME_STATUS_REPORT'
```

This common event indicates whether a specific volume is available for use on a PC with an extended data disk. A broadcast is sent after the extended data disk is mounted during system startup or after the user logs in.

This event is supported only on PCs/2-in-1 devices.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SANDBOX_BUNDLE_ADDED

```TypeScript
COMMON_EVENT_SANDBOX_BUNDLE_ADDED = 'usual.event.SANDBOX_BUNDLE_ADDED'
```

Indicates that the sandbox application has been installed on the device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

## COMMON_EVENT_SANDBOX_BUNDLE_REMOVED

```TypeScript
COMMON_EVENT_SANDBOX_BUNDLE_REMOVED = 'usual.event.SANDBOX_BUNDLE_REMOVED'
```

Indicates that the sandbox application has been uninstalled on the device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.
