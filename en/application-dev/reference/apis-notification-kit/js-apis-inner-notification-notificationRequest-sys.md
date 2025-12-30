# NotificationRequest (System API)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @michael_woo888-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

The **NotificationRequest** module provides APIs for defining the notification request.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [NotificationRequest](./js-apis-inner-notification-notificationRequest.md).

## NotificationRequest

**System capability**: SystemCapability.Notification.Notification

| Name                           | Type                                                   |  Read Only| Optional| Description                                                                   |
|-------------------------------| -------------------------------------------------------- | ----- | --- |-----------------------------------------------------------------------|
| trigger<sup>23+</sup>          | [Trigger](#trigger23) |   No | Yes | Condition object.<br>**System API**: This is a system API.|
| overlayIcon<sup>11+</sup>      | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)             |   No | Yes | Notification overlay icon. The total number of bytes of image pixels cannot exceed 192 KB.<br>**System API**: This is a system API.                                                |
| classification                | string                                                   |   No | Yes | Notification category.<br>**System API**: This is a system API. Not supported currently.                              |
| isRemoveAllowed<sup>8+</sup>   | boolean                                                  |   No | Yes | Whether the notification can be removed. If a notification is not removable, it will not be deleted when the user touches the delete button below the notification, and it also cannot be deleted by swiping left on the notification and touching the delete button. The default value is **true**.<br> - **true**: The notification can be removed.<br> - **false**: The notification cannot be removed.<br>**System API**: This is a system API.<br>**Required permissions**: ohos.permission.SET_UNREMOVABLE_NOTIFICATION|
| source<sup>8+</sup>            | number                                                   |   Yes | Yes | Notification source.<br>**System API**: This is a system API. Not supported currently.                               |
| deviceId<sup>8+</sup>          | string                                                   |   Yes | Yes | Device ID of the notification source.<br>**System API**: This is a system API. Not supported currently.                      |
| representativeBundle<sup>12+</sup> | [BundleOption](js-apis-inner-notification-notificationCommonDef.md#bundleoption) | No| Yes| Information about the proxied bundle.<br>**System API**: This is a system API.|
| notificationControlFlags<sup>12+</sup>       | number                                                   |   No | Yes | Notification mode control.<br>This API can be used to reduce the notification modes of the current notification. This parameter is obtained by performing the bitwise OR operation with the enumeration of [NotificationControlFlagStatus](js-apis-notificationManager-sys.md#notificationcontrolflagstatus12).<br>**System API**: This is a system API.           |
| unifiedGroupInfo<sup>12+</sup>       | [UnifiedGroupInfo](#unifiedgroupinfo12) |   No | Yes |Intelligent notification unification information.<br>**System API**: This is a system API.|
| creatorInstanceKey<sup>(deprecated)</sup>      | number |   Yes | Yes | Creator instance key.<br>This parameter is supported since API version 12 and deprecated since API version 15. You are advised to use **appInstanceKey** instead.<br>**System API**: This is a system API.|
| agentBundle<sup>12+</sup>       | [BundleOption](js-apis-inner-notification-notificationCommonDef.md#bundleoption) |   Yes | Yes | Information about the agent bundle for creating notifications.<br>**System API**: This is a system API.|
| appInstanceKey<sup>15+</sup>       | string |   Yes | Yes | Application instance key.<br>**System API**: This is a system API.|
| notDistributed<sup>18+</sup> | boolean | No| Yes| Whether notifications are not displayed in all scenarios across devices. The default value is **false**.<br>**NOTE**<br>This field is mutually exclusive with the **forceDistributed** field. When both fields are set to **true**, only the **notDistributed** field takes effect.<br>- **true**: Notifications are displayed only on the local device.<br>- **false**: Notifications are displayed on all collaboration devices.<br>**System API**: This is a system API.|
| forceDistributed<sup>18+</sup> | boolean | No| Yes| Whether notifications are forcibly displayed in all scenario across devices. The default value is **false**.<br>**NOTE**<br>This field takes effect only when the application is in the cross-device collaborative management list and **notDistributed** is set to **false**. Check whether the **collaborationFilter** field in the **notification_config.json** file contains the UID or bundle name of the application. For details about the file configuration path, see the **NOTIFICATION_CONFIG_FILE** property in [notification_config_parse.h](https://gitcode.com/openharmony/notification_distributed_notification_service/blob/master/services/ans/include/notification_config_parse.h). If yes, the application is on the cross-device collaborative management list.<br>- **true**: Notifications are displayed on all collaboration devices.<br>- **false**: Notifications are displayed on the applications that are on the collaborative management list.<br>**System API**: This is a system API.|
| extendInfo<sup>20+</sup> | Record<string, Object> | No| Yes| Extended parameters customized for the system applications to publish notifications.<br>**System API**: This is a system API.|

## DistributedOptions<sup>8+</sup>

Describes distributed notification options.

**System capability**: SystemCapability.Notification.Notification

| Name                   | Type          | Read Only| Optional| Description                              |
| ---------------------- | -------------- | ---- | ---- | ---------------------------------- |
| remindType             | number         |  Yes |  Yes  | Notification reminder type.<br>**System API**: This is a system API. |


## NotificationFilter<sup>11+</sup>

Describes the filter criteria for querying the live view.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name           | Type                                  | Read Only| Optional| Description                              |
| ----------------| ------------------------------------- | ---- | ---- | ---------------------------------- |
| bundle          | [BundleOption](js-apis-inner-notification-notificationCommonDef.md#bundleoption) | No| No  | Bundle information of the live view.|
| notificationKey | [notificationSubscribe.NotificationKey](js-apis-notificationSubscribe-sys.md#notificationkey) | No| No  | Notification information, including the notification ID and label.  |
| extraInfoKeys   | Array\<string>                        | No|   Yes  | List of extra keys. If this parameter is left empty, all extra information is included.|


## NotificationCheckRequest<sup>11+</sup>

Describes the notification authentication information.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name         | Type                                                      | Read Only| Optional| Description             |
| --------------| --------------------------------------------------------- | ---- | ---- | ----------------- |
| contentType   | [notificationManager.ContentType](js-apis-notificationManager.md#contenttype) | No| No  | Notification type.        |
| slotType      | [notificationManager.SlotType](js-apis-notificationManager.md#slottype)       | No| No  | Notification slot type.        |
| extraInfoKeys | Array\<string>                                            | No| No| Extra information about the live view.|

## UnifiedGroupInfo<sup>12+</sup>

Describes the fields of notification intelligent unification information.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name                  | Type           | Read Only| Optional| Description                              |
| ---------------------- | -------------- | ---- | ---- | ---------------------------------- |
| key          | string        | No| Yes  | Unified group ID.                  |
| title  | string | No| Yes  | Unified group title.           |
| content  | string | No| Yes  | Unified group summary.             |
| sceneName          | string        | No| Yes  | Name of a unification scene.                  |
| extraInfo  | {[key: string]: any} | No|  Yes  | Other unification information.           |

## MonitorEvent<sup>23+</sup>

Enumerates the event types of monitoring a geofence.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name          | Value | Description                              |
| -------------- | --- | --------------------------------- |
| MONITOR_TYPE_ENTRY | 1 | Entering a geofence.|
| MONITOR_TYPE_LEAVE | 2 | Exiting a geofence.|

## CoordinateSystemType<sup>23+</sup>

Enumerates the coordinate systems of a geofence.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name              | Value | Description            |
| ------------------ | --- | ---------------- |
| COORDINATE_TYPE_WGS84 | 1 | WGS84.|
| COORDINATE_TYPE_GCJ02 | 2 | GCJ02.|

## TriggerType<sup>23+</sup>

Enumerates the trigger types.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name        | Value | Description|
| ------------------ | ---------------- | ---- |
| TRIGGER_TYPE_GEOFENCE | 1 | Geofence.|

## Geofence<sup>23+</sup>

Defines the configuration of a geofence.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name     | Type                | Read Only| Optional| Description            |
| --------- | -------------------- | ---- | ---- | ---------------- |
| longitude | double | No| No| Longitude of the geofence center.|
| latitude | double | No| No| Latitude of the geofence center.|
| radius | double | No| No| Geofence radius, in meters.|
| delayTime | int | No| Yes| Delay time, in seconds. That is, the time to trigger a geofence after the user enters the geofence.|
| coordinateSystemType | [coordinatesystemtype](#coordinatesystemtype23) | No| No| Coordinate system type of the center point. |
| monitorEvent | [MonitorEvent](#monitorevent23) | No  | No| Event type for monitoring a geofence.|

## Trigger<sup>23+</sup>

Defines the details for triggering a geofence.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name                | Type                | Read Only| Optional| Description                                    |
| -------------------- | -------------------- | ---- | ---- | ---------------------------------------- |
| type | [TriggerType](#triggertype23) | No| No| Trigger type.|
| condition | [Geofence](#geofence23) | No| No| Details about a geofence.|
| displayTime | int | No| Yes| Display time of a live view, in seconds.|
