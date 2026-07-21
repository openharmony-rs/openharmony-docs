# NotificationContent

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=50e734d278c25dbb71273705da516c218b3754a1 translatedAt=2026-06-29T02:36:56.240Z pushedAt=2026-06-30T10:57:37.007Z -->

The **NotificationContent** defines the content structure of a notification and provides content description API of multiple notification types. When an application needs to publish a notification, it can select the corresponding content type API to construct the notification content based on the display requirements (such as plain text, long text, multi-line text, picture, or live view).

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationContent

Describes the notification contents.

**System capability**: SystemCapability.Notification.Notification

| Name          | Type                                                                       | Read-Only| Optional| Description              |
| -----------   | --------------------------------------------------------------------------- | ---- | --- | ------------------ |
| notificationContentType<sup>11+</sup>    | [notificationManager.ContentType](./js-apis-notificationManager.md#contenttype)                | No  | Yes  | Notification content type, used to specify the content layout type of the notification, which determines the display style of the notification in the notification center. It must be used together with the corresponding notification content object. For example, when this parameter is set to **NOTIFICATION_CONTENT_BASIC_TEXT**, the **normal** field must be specified at the same time.       |
| normal         | [NotificationBasicContent](#notificationbasiccontent)                      | No  | Yes  | Basic notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_BASIC_TEXT**. The notification displays the title and body in a plain text style.   |
| longText       | [NotificationLongTextContent](#notificationlongtextcontent)                | No  | Yes  | Long text notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_LONG_TEXT**. The complete long text content can be displayed after the notification is expanded. |
| multiLine      | [NotificationMultiLineContent](#notificationmultilinecontent)              | No  | Yes  | Multi-line notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_MULTILINE**. The notification is displayed in a multi-line list style after expansion.   |
| picture        | [NotificationPictureContent](#notificationpicturecontent)                  | No  | Yes  | Picture notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_PICTURE**. The picture can be displayed after the notification is expanded.   |
| systemLiveView<sup>11+</sup> | [NotificationSystemLiveViewContent](#notificationsystemliveviewcontent)    | No  | Yes  | System live view notification content. Third-party applications are not supported to directly create this type of notification. After a system agent creates a system live view notification, a third-party application can publish a notification with the same ID to update the specified content.|
| contentType<sup>(deprecated)</sup> | [notification.ContentType](./js-apis-notification.md#contenttype)  | No | Yes | Notification content type.<br>This attribute is supported since API version 7 and deprecated since API version 11. You are advised to use **notificationContentType** instead.      |

## NotificationBasicContent

Describes the basic text notification, which is used to display the title and body content. It serves as the basic content structure for other notification types. Other notification types (such as long text, multi-line text, picture, and live view) inherit this API and extend their own specific fields on this basis.

**System capability**: SystemCapability.Notification.Notification

| Name          | Type   | Read-Only| Optional| Description                              |
| -------------- | ------ | ---- |-----| ---------------------------------- |
| title          | string | No  | No  | Notification title, displayed at the top of the notification.<br>It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated.         |
| text           | string | No  | No  | Notification body content, displayed below the title.<br>It cannot be an empty string. The size does not exceed 3072 bytes, and the excess part will be truncated.         |
| additionalText | string | No  | Yes  | Additional notification content, which supplements the notification content and is not displayed in the notification center.<br>It defaults to empty. The size does not exceed 3072 bytes, and the excess part will be truncated.   |
| lockscreenPicture<sup>12+</sup> | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) |  No |  Yes | Picture displayed on the lock screen. This parameter is left empty by default. Currently, only the live view notification is supported. The total number of the icon pixel bytes cannot exceed 192 KB (which is obtained through [getPixelBytesNumber](../apis-image-kit/arkts-apis-image-PixelMap.md#getpixelbytesnumber7)). The recommended icon size is 128 × 128 pixels. The display effect depends on the device capability and notification center UI style.  |

## NotificationLongTextContent

Describes the long text notification. This API is inherited from [NotificationBasicContent](#notificationbasiccontent).

> **NOTE**
>
> - When this notification type forms a group notification with other notifications, its display effect defaults to the collapsed state, and the displayed title and body are the **title** and **text** inherited from [NotificationBasicContent](#notificationbasiccontent).<br>When this notification type is displayed alone and does not form a group notification with other notifications, its display effect defaults to the expanded state, where the displayed title is the expanded title **expandedTitle**, and the displayed body content is the long text **longText**.
>
> - When a user taps a group notification to view the notification details, the display effect of this notification changes to the expanded state.
>
> - The actual display effect depends on the device capabilities and the notification center UI style.

**System capability**: SystemCapability.Notification.Notification

| Name          | Type   | Read-Only| Optional| Description                            |
| -------------- | ------ | ---- | --- | -------------------------------- |
| expandedTitle  | string | No | No | Title when the notification is expanded.<br>It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated. |
| longText       | string | No | No | Full long text content displayed after the notification is expanded.<br>It cannot be an empty string. The size does not exceed 3072 bytes, and the excess part will be truncated. |
| briefText      | string | No | No | Notification summary content, which is a summary of the notification content and is not displayed in the notification center.<br>It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated. |

## NotificationMultiLineContent

Describes the multi-line text notification. This API is inherited from [NotificationBasicContent](#notificationbasiccontent).

> **NOTE**
>
> - When this notification type forms a group notification with other notifications, its display effect defaults to the collapsed state, and the displayed title and body are the **title** and **text** inherited from [NotificationBasicContent](#notificationbasiccontent).<br>When this notification type is displayed alone and does not form a group notification with other notifications, its display effect defaults to the expanded state, where the displayed title is the expanded title **longTitle**, and the multi-line text content **lines** is displayed as the body.
>
> - When a user taps a group notification to view the notification details, the display effect of this notification changes to the expanded state.
>
> - The actual display effect depends on the device capabilities and the notification center UI style.

**System capability**: SystemCapability.Notification.Notification

| Name          | Type           | Read-Only| Optional| Description                            |
| -------------- | --------------- | --- | --- | -------------------------------- |
| longTitle      | string          | No  | No  | Title when the notification is expanded.<br>It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated.|
| lines          | Array\<string\> | No  | No  | List of multi-line text displayed after the notification is expanded. Each line is displayed as an independent entry and supports up to three lines.<br>Each line size does not exceed 1024 bytes, excess part will be truncated.  |
| briefText      | string          | No  | No  | Notification summary content, which is a summary of the notification content and is not displayed in the notification center.<br>It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated. |

## NotificationPictureContent

Describes the picture-attached notification. This API is inherited from [NotificationBasicContent](#notificationbasiccontent).

> **NOTE**
>
> - When this notification type forms a group notification with other notifications, its display effect defaults to the collapsed state, and the displayed title and body are the **title** and **text** inherited from [NotificationBasicContent](#notificationbasiccontent).<br>When this notification type is displayed alone and does not form a group notification with other notifications, its display effect defaults to the expanded state, where the displayed title is the expanded title **expandedTitle**, and the displayed body is the **text** inherited from **NotificationBasicContent** and the picture content **picture** of this type.
>
> - When a user taps a group notification to view the notification details, the display effect of this notification changes to the expanded state.
>
> - The actual display effect depends on the device capabilities and the notification center UI style.

**System capability**: SystemCapability.Notification.Notification

| Name          | Type                                         | Read-Only| Optional| Description                              |
| -------------- | -------------------------------------------- | ---- | --- |------------------------------------|
| expandedTitle  | string                                       | No  | No  | Title when the notification is expanded.<br>It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated.    |
| picture        | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No  | No  | Picture content displayed after the notification is expanded.<br>The total bytes of the image pixels cannot exceed 2 MB.|
| briefText      | string                                       | No  | No  | Notification summary content, which is a summary of the notification content and is not displayed in the notification center.<br>It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated. |

## NotificationSystemLiveViewContent

Describes the system live view notification content, which is used to display real-time status information in the live view. Third-party applications are not supported to directly create this notification type. After the system proxy creates a system live view notification, a third-party application can publish a notification with the same ID to update the specified content. This API is inherited from [NotificationBasicContent](#notificationbasiccontent).

> **NOTE**
>
> The actual display effect depends on the device capabilities and the notification center UI style.

**System capability**: SystemCapability.Notification.Notification

| Name                        | Type                                            | Read-Only| Optional| Description                              |
| ---------------------------- | ----------------------------------------------- | --- | --- | -----------------------------------|
| typeCode<sup>11+</sup>       | number                                          | No  | No  | Type identifier for marking the caller's service type, which is used to distinguish different live view service scenarios.       |
| capsule<sup>11+</sup>        | [NotificationCapsule](#notificationcapsule11)   | No | Yes | Capsule of the notification. This parameter is left empty by default.           |
| button<sup>11+</sup>         | [NotificationButton](#notificationbutton11)     | No | Yes | Button of the notification. This parameter is left empty by default.           |
| time<sup>11+</sup>           | [NotificationTime](#notificationtime11)         | No | Yes | Time of the notification. This parameter is left empty by default.           |
| progress<sup>11+</sup>       | [NotificationProgress](#notificationprogress11) | No | Yes | Progress of the notification. This parameter is left empty by default.           |

## NotificationCapsule<sup>11+</sup>

Describes the notification capsule, which is used to display the capsule form in the live view.

> **NOTE**
>
> The actual display effect depends on the device capabilities and the notification center UI style.

**System capability**: SystemCapability.Notification.Notification

| Name           | Type                                         | Read-Only| Optional| Description                           |
| --------------- | -------------------------------------------- | --- | --- | -------------------------------- |
| title           | string                                       | No  | Yes  | Capsule title.<br>The size does not exceed 202 bytes, and the excess part will be truncated. The value defaults to empty.  |
| icon            | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | No  | Yes  | Capsule icon.<br>The total bytes of the icon pixel does not exceed 192 KB (the total bytes of the icon pixel is obtained through [getPixelBytesNumber](../apis-image-kit/arkts-apis-image-PixelMap.md#getpixelbytesnumber7)). It is recommended that the icon pixel dimensions be 128 × 128.                        |
| backgroundColor | string                                       | No  | Yes  | Capsule background color. Colors in rgb, rgba, or argb format are supported.<br>Example of rgb format color: **#ffffff**, **rgb(255, 100, 255)**.<br>Example of rgba format color: **rgba(255, 100, 255, 0.5)**.<br>Example of argb format color: **#ff000000**.<br>The size does not exceed 202 bytes, and the excess part will be truncated. The value defaults to empty.                        |

## NotificationButton<sup>11+</sup>

Describes the notification button, which is used to display an interactive button in the live view.

> **NOTE**
>
> The actual display effect depends on the device capabilities and the notification center UI style.

**System capability**: SystemCapability.Notification.Notification

| Name | Type                                                  | Read-Only| Optional| Description            |
| ----- | ----------------------------------------------------- | --- | --- | ----------------- |
| names | Array\<string\> | No | Yes | List of button names. Each name corresponds to the text displayed on a notification button. A maximum of 3 buttons is supported.<br>The size of each name does not exceed 202 bytes, and the excess part will be truncated. The value defaults to empty. |
| icons | Array\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)\> | No | Yes | List of button icons, corresponding one-to-one with **names**, with each icon displayed on its corresponding button. A maximum of 3 icons is supported. The total bytes of icon pixels does not exceed 192 KB (the total bytes of icon pixels is obtained through [getPixelBytesNumber](../apis-image-kit/arkts-apis-image-PixelMap.md#getpixelbytesnumber7)). It is recommended that the icon pixel dimensions be 128 × 128. The value defaults to empty. This parameter is mutually exclusive with **iconsResource**; only one of them can be used. |
| iconsResource<sup>12+</sup> | Array\<[Resource](../apis-arkui/arkui-ts/ts-types.md#resource)\> | No | Yes | List of button icon resources, corresponding one-to-one with **names** via Resource references. A maximum of 3 resources is supported. The value defaults to empty. This parameter is mutually exclusive with **icons**; only one of them can be used. |

## NotificationTime<sup>11+</sup>

Describes the notification timing information.

> **NOTE**
>
> The actual display effect depends on the device capabilities and the notification center UI style.

**System capability**: SystemCapability.Notification.Notification

| Name          | Type             | Read-Only| Optional| Description                            |
| -------------- | ---------------- | --- | --- | -------------------------------- |
| initialTime    | number           | No  | Yes  | Initial time for the timer, used to set the starting point of the timer in the Live View.<br>The value range is all non-negative integers. The default value is **0**.<br>Unit: millisecond.  |
| isCountDown    | boolean          | No  | Yes  | Whether it is countdown mode. The default value is **false**.<br> - **true**: The time is displayed decreasing from initialTime.<br> - **false**: The time is displayed increasing from initialTime. |
| isPaused       | boolean          | No  | Yes  | Whether the timer is paused. The default value is **false**.<br> - **true**: The timer is paused at the current value.<br> - **false**: The timer runs normally.   |
| isInTitle      | boolean          | No  | Yes  | Whether the time information is displayed in the notification title. The default value is **false**.<br> - **true**: The timer information will be embedded in the title area.<br> - **false**: The timer information is displayed in a separate area.|

**Example**:

<!--code_no_check-->

```ts
// The notification counts down from three seconds and the time is displayed in the title.
time: {
    initialTime: 3000,
    isCountDown: true,
    isPaused: false,
    isInTitle: true,
}
```

## NotificationProgress<sup>11+</sup>

Describes the notification progress, which is used to display progress bar information in the live view.

> **NOTE**
>
> The actual display effect depends on the device capabilities and the notification center UI style.

**System capability**: SystemCapability.Notification.Notification

| Name          | Type           | Read-Only| Optional| Description                            |
| -------------- | --------------- | --- | --- | -------------------------------- |
| maxValue        | number         | No  | Yes  | Maximum value of the progress.<br>The value range is all non-negative integers.                       |
| currentValue    | number         | No  | Yes  | Current value of the progress.<br>The value range is all non-negative integers.                       |
| isPercentage    | boolean        | No  | Yes  | Whether to display the progress as a percentage. The value defaults to **false**.<br> - **true**: The progress is displayed as a percentage.<br> - **false**: The progress is displayed as an absolute value.|