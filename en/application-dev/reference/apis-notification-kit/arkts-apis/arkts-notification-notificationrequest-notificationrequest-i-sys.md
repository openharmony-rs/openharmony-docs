# NotificationRequest

Defines the data structure of a notification request, which is used to describe all information about a notification, including the notification content, identifier, display style, and interaction behavior.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## agentBundle

```TypeScript
readonly agentBundle?: BundleOption
```

Information about the agent bundle for creating notifications. This parameter is left empty by default.

**Type:** [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md)

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## appInstanceKey

```TypeScript
readonly appInstanceKey?: string
```

Application instance key. This parameter is left empty by default.

**Type:** string

**Since:** 15

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## classification

```TypeScript
classification?: string
```

Notification classification. Not supported currently.

**Type:** string

**Since:** 7

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

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## deviceId

```TypeScript
readonly deviceId?: string
```

Device ID of the notification source. Not supported currently.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## extendInfo

```TypeScript
extendInfo?: Record<string, Object>
```

Extended parameters customized for the system applications to publish notifications. This parameter is left empty by default.

**Type:** Record&lt;string, Object&gt;

**Since:** 20

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## forceDistributed

```TypeScript
forceDistributed?: boolean
```

Whether notifications are forcibly displayed in all scenario across devices. The default value is **false**. **NOTE:** This field takes effect only when the application is in the cross-device collaborative management list and **notDistributed** is set to **false**. Check whether the **collaborationFilter** field in the **notification_config.json** file contains the UID or bundle name of the application. For details about the file configuration path, see the **NOTIFICATION_CONFIG_FILE** property in [notification_config_parse.h](https://gitcode.com/openharmony/notification_distributed_notification_service/blob/master/services/ans/include/notification_config_parse.h). If yes, the application is on the cross-device collaborative management list.
- **true**: Notifications are displayed on all collaboration devices.
- **false**: Notifications are displayed on the applications that are on the collaborative management list.

**Type:** boolean

**Default:** false

**Since:** 18

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## groupInfo

```TypeScript
groupInfo?: GroupInfo
```

Custom group notification information. This parameter is left empty by default.

**Type:** [GroupInfo](arkts-notification-notificationrequest-groupinfo-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

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

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## notDistributed

```TypeScript
notDistributed?: boolean
```

Whether notifications are not displayed in all scenarios across devices. The default value is **false**. **NOTE:** This field is mutually exclusive with the **forceDistributed** field. When both fields are set to **true**, only the **notDistributed** field takes effect.
- **true**: Notifications are displayed only on the local device.
- **false**: Notifications are displayed on all collaboration devices.

**Type:** boolean

**Default:** false

**Since:** 18

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## notificationControlFlags

```TypeScript
notificationControlFlags?: number
```

Notification mode control. The default value is **0**. This API can be used to reduce the notification modes of the current notification. This parameter is obtained by performing the bitwise OR operation with the enumeration of NotificationControlFlagStatus.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## representativeBundle

```TypeScript
representativeBundle?: BundleOption
```

Information about the proxied bundle. This parameter is left empty by default.

**Type:** [BundleOption](arkts-notification-notificationcommondef-bundleoption-i.md)

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## source

```TypeScript
readonly source?: number
```

Notification source. Not supported currently.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## trigger

```TypeScript
trigger?:Trigger
```

Condition object. This parameter is left empty by default.

**Type:** [Trigger](arkts-notification-notificationrequest-trigger-i-sys.md)

**Since:** 23

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## unifiedGroupInfo

```TypeScript
unifiedGroupInfo?: UnifiedGroupInfo
```

Intelligent notification unification information. This parameter is left empty by default.

**Type:** [UnifiedGroupInfo](arkts-notification-notificationrequest-unifiedgroupinfo-i-sys.md)

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
