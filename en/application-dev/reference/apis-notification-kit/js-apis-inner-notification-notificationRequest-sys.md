# NotificationRequest (System API)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @michael_woo888-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @huipeizi-->

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
| overlayIcon<sup>11+</sup>      | [image.PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7)             |   No | Yes | Notification overlay icon. The total number of bytes of image pixels cannot exceed 192 KB.<br>**System API**: This is a system API.                                                |
| classification                | string                                                   |   No | Yes | Notification category.<br>**System API**: This is a system API. Not supported currently.                              |
| isRemoveAllowed<sup>8+</sup>   | boolean                                                  |   No | Yes | Whether the notification can be removed. If a notification is not removable, it will not be deleted when the user touches the delete button below the notification, but it can still be deleted by swiping left on the notification and touching the delete button.<br> - **true**: Yes.<br> - **false** (default): No.<br>**System API**: This is a system API.<br>**Required permissions**: ohos.permission.SET_UNREMOVABLE_NOTIFICATION |
| source<sup>8+</sup>            | number                                                   |   Yes | Yes | Notification source.<br>**System API**: This is a system API. Not supported currently.                               |
| deviceId<sup>8+</sup>          | string                                                   |   Yes | Yes | Device ID of the notification source.<br>**System API**: This is a system API. Not supported currently.                      |
| representativeBundle<sup>12+</sup> | [BundleOption](js-apis-inner-notification-notificationCommonDef.md#bundleoption) | No| Yes| Information about the proxied bundle.<br>**System API**: This is a system API.|
| notificationControlFlags<sup>12+</sup>       | number                                                   |   No | Yes | Notification mode control.<br>This API can be used to reduce the notification modes of the current notification. This parameter is obtained by performing the bitwise OR operation with the enumeration of [NotificationControlFlagStatus](js-apis-notificationManager-sys.md#notificationcontrolflagstatus12).<br>**System API**: This is a system API.           |
| unifiedGroupInfo<sup>12+</sup>       | [UnifiedGroupInfo](#unifiedgroupinfo12) |   No | Yes |Intelligent notification unification information.<br>**System API**: This is a system API.|
| creatorInstanceKey<sup>(deprecated)</sup>      | number |   Yes | Yes | Creator instance key.<br>**System API**: This is a system API.|
| agentBundle<sup>12+</sup>       | [BundleOption](js-apis-inner-notification-notificationCommonDef.md#bundleoption) |   Yes | Yes | Information about the agent bundle for creating notifications.<br>**System API**: This is a system API.|
| appInstanceKey<sup>15+</sup>       | string |   Yes | Yes | Application instance key.<br>**System API**: This is a system API.|
| notDistributed<sup>18+</sup> | boolean | No| Yes| Whether notifications are not displayed in all scenarios across devices.<br>**NOTE**<br>This field is mutually exclusive with the **forceDistributed** field. When both fields are set, only the **notDistributed** field takes effect.<br>- **true**: Notifications are displayed only on the local device.<br>- **false** (default): Notifications are displayed on all collaboration devices.<br>**System API**: This is a system API.|
| forceDistributed<sup>18+</sup> | boolean | No| Yes| Whether notifications are forcibly displayed in all scenario across devices.<br>**NOTE**<br>This field takes effect only when the application is on the cross-device collaborative management list and the **notDistributed** field is not set. Check whether the **collaborationFilter** field in the **notification_config.json** file contains the UID or bundle name of the application. For details about the file configuration path, see the **NOTIFICATION_CONFIG_FILE** property in [notification_config_parse.h](https://gitee.com/openharmony/notification_distributed_notification_service/blob/master/services/ans/include/notification_config_parse.h). If yes, the application is on the cross-device collaborative management list.<br>- **true**: Notifications are displayed on all collaboration devices.<br>- **false** (default): Notifications are displayed on the applications that are on the collaborative management list.<br>**System API**: This is a system API. |

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
| sceneName          | string        | No| Yes  | Name of an unification scene.                  |
| extraInfo  | {[key: string]: any} | No|  Yes  | Other unification information.           |
