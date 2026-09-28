# NotificationContent (System API)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4bb0b56d7d67b2ab3ff0955bce487aba3399fade translatedAt=2026-09-22T02:07:44.168Z pushedAt=2026-09-22T08:29:58.358Z -->

NotificationContent defines the content structure of a notification and provides interfaces for describing multiple notification content types. When an application needs to publish a notification, it can select the corresponding content type interface to construct the [notification content](../../notification/notification-glossary.md#notification-content) based on the display requirements of the notification (such as plain text, long text, multiline text, picture, and live view).

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [NotificationContent](./js-apis-inner-notification-notificationContent.md).

## NotificationContent

**System capability**: SystemCapability.Notification.Notification

| Name          | Type                                                                       | Read-Only| Optional| Description              |
| -----------   | --------------------------------------------------------------------------- | ---- | --- | ------------------ |
| liveView<sup>11+</sup>       | [NotificationLiveViewContent](#notificationliveviewcontent11)              | No  | Yes  | Normal live view type [notification content](../../notification/notification-glossary.md#notification-content-notification-content).<br>**System API**: This API is a system API. |

## NotificationBasicContent

Describes the normal text notification.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name          | Type                                                                       | Read-Only| Optional| Description              |
| -----------   | --------------------------------------------------------------------------- | ---- | --- | ------------------ |
| structuredText<sup>21+</sup> | Map<string, string> |  No  |  Yes  | Structured field of the notification. Currently, only service reminder SMS messages are supported for structured display in the [notification center](../../notification/notification-glossary.md#notification-center). Empty by default. (The size of each key/value must not exceed 512 bytes; the excess part is truncated. A maximum of 3 pairs of structured data is supported, and the excess part is ignored.)   |

## NotificationLiveViewContent<sup>11+</sup>

Describes the [normal live view notification](../../notification/notification-glossary.md#normal-live-view). This API is inherited from [NotificationBasicContent](#notificationbasiccontent).

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name          | Type                                                               | Read-Only| Optional| Description                                                 |
| -------------- | ------------------------------------------------------------------ | --- | --- | ------------------------------------------------------|
| status         | [LiveViewStatus](#liveviewstatus11)                                | No | No | Notification status.                 |
| version        | number                                                             | No | Yes | Notification version number. If the version number stored in the database is **0xffffffff**, the version number is not verified when the live view is updated or ended; otherwise, the current version number must be greater than the version number stored in the database. If this parameter is left empty, the default value is **0xffffffff**. |
| extraInfo      | Record<string, Object\>                                               | No  | Yes  | Additional content of the [live view notification](../../notification/notification-glossary.md#live-view-notification). Empty by default.           |
| pictureInfo    | Record<string, Array<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)\>\> | No | Yes | Extra image information of the live view. This parameter is left empty by default.|
| isLocalUpdateOnly<sup>12+</sup> | boolean                                           | No | Yes | Whether the live view is updated only locally. The default value is **false**.<br> - **true**: Yes.<br> - **false**: No.    |
| extensionWantAgent<sup>20+</sup> | [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md)    |  No |  Yes | Redirection by tapping in the auxiliary area. This parameter is left empty by default.     |


## NotificationSystemLiveViewContent<sup>18+</sup>

Describes the [system live view](../../notification/notification-glossary.md#system-live-view) [notification content](../../notification/notification-glossary.md#notification-content), which is used to display real-time status information in the live view. Third-party applications cannot create this type of notification. After the system agent creates a system live view type notification, a third-party application can publish a notification with the same ID to update the specified content. This API is inherited from [NotificationBasicContent](#notificationbasiccontent).

> **NOTE**
>
> The actual display effect depends on the device capability and the [notification center](../../notification/notification-glossary.md#notification-center) UI style.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name                        | Type                                            | Read-Only| Optional| Description                              |
| ---------------------------- | ----------------------------------------------- | --- | --- | -----------------------------------|
| liveViewType | [LiveViewTypes](#liveviewtypes18)  | No| Yes | Live view types. The default value is **LIVE_VIEW_ACTIVITY**. |
| cardButtons | Array\<[NotificationIconButton](#notificationiconbutton18)\>    |  No |  Yes | Live view buttons (a maximum of three buttons are supported). This parameter is left empty by default.     |

## NotificationCapsule<sup>11+</sup>

Describes the [notification capsule](../../notification/notification-glossary.md#notification-capsule), which is used to display the capsule form in the live view.

> **NOTE**
>
> The actual display effect depends on the device capability and the [notification center](../../notification/notification-glossary.md#notification-center) UI style.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name                 |  Type                        | Read-Only| Optional| Description                             |
| --------------------- | ---------------------------- | ---- | ---- | -------------------------------- |
| content<sup>12+</sup> | string                       |  No |  Yes | Extended text of the capsule. This parameter is left empty by default.                  |
| time<sup>18+</sup> | number                       |  No  |  Yes  | Display duration of the notification capsule of an instant task. The default value is **0**.<br>Unit: second.   |
| capsuleButtons<sup>18+</sup> | Array\<[NotificationIconButton](#notificationiconbutton18)\>    |  No |  Yes | Buttons of the notification capsule of an instant task. A maximum of two buttons are supported. This parameter is left empty by default.     |

## LiveViewStatus<sup>11+</sup>

Describes the status of the [normal live view notification](../../notification/notification-glossary.md#normal-live-view).

**System capability**: SystemCapability.Security.AccessToken

**System API**: This is a system API.

| Name                        | Value|   Description  |
| ---------------------------- |----|----------|
| LIVE_VIEW_CREATE             | 0  | The live view is created.    |
| LIVE_VIEW_INCREMENTAL_UPDATE | 1  | The live view is updated in incremental mode.|
| LIVE_VIEW_END                | 2  | The live view is ended.    |
| LIVE_VIEW_FULL_UPDATE        | 3  | The live view is updated in full mode.|
| LIVE_VIEW_PENDING_CREATE<sup>23+</sup>     | 4  | The live view is created by condition.<br>**Model restriction**: This API can be used only in the stage model.|
| LIVE_VIEW_PENDING_END<sup>23+</sup>        | 6  | The live view is terminated by condition.<br>**Model restriction**: This API can be used only in the stage model.|

## NotificationIconButton<sup>18+</sup>

Describes the system [notification button](../../notification/notification-glossary.md#notification-button).

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name         | Type                   | Read-Only| Optional| Description                                     |
| ------------ | ----------------------- | ---- | ---- | ---------------------------------------- |
| name         | string                  | No   |  No  | Button identifier, used to distinguish multiple different buttons for the same notification. The string length cannot exceed 202 bytes, and the exceeding part will be truncated. It cannot be an empty string.   |
| iconResource | [IconType](#icontype18) | No  |  No | Background image of a button.                            |
| text         | string                  | No   |  Yes  | Text displayed on the button, which defaults to empty. The string length cannot exceed 202 bytes, and the exceeding part will be truncated.             |
| hidePanel    | boolean                 | No   |  Yes  | Whether to hide the [notification center](../../notification/notification-glossary.md#notification-center) when the button is clicked. The default value is false.<br> - true: yes.<br> - false: no.   |

## IconType<sup>18+</sup>

type IconType = Resource | image.PixelMap

Describes the icon types.

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Type                                                            | Description                             |
| ---------------------------------------------------------------- | -------------------------------- |
| [Resource](../apis-arkui/arkui-ts/ts-types.md#resource)          | Image resource.            |
| [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | Image.                |

## LiveViewTypes<sup>18+</sup>

Describes the type of the [live view notification](../../notification/notification-glossary.md#live-view-notification).

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name                        | Value|   Description  |
| ---------------------------- |----|----------|
| LIVE_VIEW_ACTIVITY           | 0  | Real-time activity (progress).|
| LIVE_VIEW_INSTANT            | 1  | Instant task.|
| LIVE_VIEW_LONG_TERM          | 2  | Long-term task.|

## NotificationMultiLineContent

Describes the multi-line text notification content. This API inherits from [NotificationBasicContent](#notificationbasiccontent).

> **NOTE**
>
> - When this type of notification forms a [group notification](../../notification/notification-glossary.md#group-notification) with other notifications, the notification is displayed in the collapsed state by default, and the title and body displayed are the `title` and `text` in the [normal text](#notificationbasiccontent) inherited by this type.<br>When this type of notification is displayed alone and does not form a group notification with other notifications, the notification is displayed in the expanded state by default, with the expanded title `longTitle` displayed as the title and the multi-line text content `lines` displayed as the body in multiple lines.
>
> - When the user taps a notification displayed in a group to view the details of each notification, the notification changes to the expanded state.
>
> - The actual display effect depends on the device capability and the [notification center](../../notification/notification-glossary.md#notification-center) UI style.

**System capability**: SystemCapability.Notification.Notification

| Name          | Type   | Read-Only| Optional| Description                            |
| -------------- | ------ | ---- | --- | -------------------------------- |
| lineWantAgents<sup>20+</sup>       | Array<[WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md)> |  No | Yes | **wantAgent**s triggered when a line of text in the multi-line text is tapped. The text in different lines corresponds to different **wantAgent**s. The maximum number of lines configured for this field is equal to the value of [lines](./js-apis-inner-notification-notificationContent.md#notificationmultilinecontent). This parameter is left empty by default.<br>**System API**: This is a system API.<br>**Required permissions**: ohos.permission.NOTIFICATION_AGENT_CONTROLLER|
<!--no_check-->