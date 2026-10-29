# NotificationRequest (System API)

```TypeScript
export interface NotificationRequest
```

Defines the data structure of a [notification request](../../../notification/notification-glossary.md#notification-request), which is used to describe all information of a notification, including [notification content](../../../notification/notification-glossary.md#notification-content), identifier, display style, interaction behavior, and so on.

**Since:** 7

<!--Device-unnamed-export interface NotificationRequest--><!--Device-unnamed-export interface NotificationRequest-End-->

**System capability:** SystemCapability.Notification.Notification

## agentBundle

```TypeScript
readonly agentBundle?: BundleOption
```

Information about the agent bundle for creating notifications. This parameter is left empty by default.

**Type:** [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md)

**Since:** 12

<!--Device-NotificationRequest-readonly agentBundle?: BundleOption--><!--Device-NotificationRequest-readonly agentBundle?: BundleOption-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## appInstanceKey

```TypeScript
readonly appInstanceKey?: string
```

Application instance key. The default value is empty. Set this field when you need to distinguish between different instances of the same application.

**Type:** string

**Since:** 15

<!--Device-NotificationRequest-readonly appInstanceKey?: string--><!--Device-NotificationRequest-readonly appInstanceKey?: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## classification

```TypeScript
classification?: string
```

Notification classification.

Not supported currently.

**Type:** string

**Since:** 7

<!--Device-NotificationRequest-classification?: string--><!--Device-NotificationRequest-classification?: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## deviceId

```TypeScript
readonly deviceId?: string
```

Device ID of the notification source.

Not supported currently.

**Type:** string

**Since:** 8

<!--Device-NotificationRequest-readonly deviceId?: string--><!--Device-NotificationRequest-readonly deviceId?: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## extendInfo

```TypeScript
extendInfo?: Record<string, Object>
```

Extended parameters customized for the system applications to publish notifications. This parameter is left empty by default.

**Type:** Record&lt;string, Object&gt;

**Since:** 20

<!--Device-NotificationRequest-extendInfo?: Record<string, Object>--><!--Device-NotificationRequest-extendInfo?: Record<string, Object>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## forceDistributed

```TypeScript
forceDistributed?: boolean
```

Whether notifications are forcibly displayed through all-scenario cross-device collaboration. The default value is **false**.

**NOTE:** 

This field takes effect only when the application is in the cross-device collaboration management list and **notDistributed** is set to **false**. Check whether the **collaborationFilter** field in the **notification_config.json** file contains the UID or bundle name of the application. For details about the file configuration path, see the **NOTIFICATION_CONFIG_FILE** property in [notification_config_parse.h] (https://gitcode.com/openharmony/notification_distributed_notification_service/blob/master/services/ans/include/notification_config_parse.h). If yes, the application is on the cross-device collaboration management list.

- **true**: Notifications are displayed on all collaboration devices.  
- **false**: Notifications are displayed according to the collaborative management list.

**Type:** boolean

**Default:** false

**Since:** 18

<!--Device-NotificationRequest-forceDistributed?: boolean--><!--Device-NotificationRequest-forceDistributed?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## groupInfo

```TypeScript
groupInfo?: GroupInfo
```

Custom information of the [group notification](../../../notification/notification-glossary.md#group-notification). This parameter is left empty by default.

**Type:** [GroupInfo](arkts-notification-notificationrequest-groupinfo-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationRequest-groupInfo?: GroupInfo--><!--Device-NotificationRequest-groupInfo?: GroupInfo-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## isRemoveAllowed

```TypeScript
isRemoveAllowed?: boolean
```

Whether the notification can be removed. If a notification is not removable, it will not be deleted when the user touches the delete button below the notification, and it also cannot be deleted by swiping left on the notification and touching the delete button. The default value is **true**.

- **true**: The notification can be removed.  
- **false**: The notification cannot be removed.

**Type:** boolean

**Default:** true

**Since:** 8

**Required permissions:** 
- API version 11 and later: ohos.permission.SET_UNREMOVABLE_NOTIFICATION
- API versions 8 to 10: N/A

<!--Device-NotificationRequest-isRemoveAllowed?: boolean--><!--Device-NotificationRequest-isRemoveAllowed?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## notDistributed

```TypeScript
notDistributed?: boolean
```

Whether the notification is not displayed through all-scenario [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration). The default value is **false**.

**Note:** 

This field is mutually exclusive with the forceDistributed field. When both are set to **true**, only the notDistributed field takes effect.

- When set to **true**: the notification is displayed only on this device.

- When set to **false**: the notification is displayed on all collaboration devices.

**Type:** boolean

**Default:** false

**Since:** 18

<!--Device-NotificationRequest-notDistributed?: boolean--><!--Device-NotificationRequest-notDistributed?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## notificationControlFlags

```TypeScript
notificationControlFlags?: number
```

[Notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode) control. The default value is **0**.

This API can be used to reduce the reminder modes of the current notification. This parameter is obtained by performing a bitwise OR operation on the enums of [NotificationControlFlagStatus](arkts-notification-notificationmanager-notificationcontrolflagstatus-e-sys.md).

**Type:** number

**Since:** 12

<!--Device-NotificationRequest-notificationControlFlags?: long--><!--Device-NotificationRequest-notificationControlFlags?: long-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## representativeBundle

```TypeScript
representativeBundle?: BundleOption
```

Information about the proxied bundle. This parameter is left empty by default.

**Type:** [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md)

**Since:** 12

<!--Device-NotificationRequest-representativeBundle?: BundleOption--><!--Device-NotificationRequest-representativeBundle?: BundleOption-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## source

```TypeScript
readonly source?: number
```

Notification source.

Not supported currently.

**Type:** number

**Since:** 8

<!--Device-NotificationRequest-readonly source?: int--><!--Device-NotificationRequest-readonly source?: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## trigger

```TypeScript
trigger?:Trigger
```

Condition object. This parameter is left empty by default.

**Type:** [Trigger](arkts-notification-notificationrequest-trigger-i-sys.md)

**Since:** 23

<!--Device-NotificationRequest-trigger?:Trigger--><!--Device-NotificationRequest-trigger?:Trigger-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## unifiedGroupInfo

```TypeScript
unifiedGroupInfo?: UnifiedGroupInfo
```

Information field of message [smart aggregation](../../../notification/notification-glossary.md#notification-smart-aggregation). This parameter is left empty by default.

**Type:** [UnifiedGroupInfo](arkts-notification-notificationrequest-unifiedgroupinfo-i-sys.md)

**Since:** 12

<!--Device-NotificationRequest-unifiedGroupInfo?: UnifiedGroupInfo--><!--Device-NotificationRequest-unifiedGroupInfo?: UnifiedGroupInfo-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## creatorInstanceKey

```TypeScript
readonly creatorInstanceKey?: number
```

Creator instance key.

**Type:** number

**Since:** 12

**Deprecated since:** 15

**Substitutes:** [appInstanceKey](#appinstancekey)

<!--Device-NotificationRequest-readonly creatorInstanceKey?: number--><!--Device-NotificationRequest-readonly creatorInstanceKey?: number-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
