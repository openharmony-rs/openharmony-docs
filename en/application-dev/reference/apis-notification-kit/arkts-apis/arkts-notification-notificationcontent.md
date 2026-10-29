# notificationContent(NotificationContent)

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md) | Describes the basic text notification, which is used to display the title and body content. It serves as basic content structure for other notification types. Other notification types (such as long text, multi-line text, picture, and live view) inherit this API and extend their own specific fields on this basis. |
| [NotificationButton](arkts-notification-notificationcontent-notificationbutton-i.md) | Describes the [notification button](../../../notification/notification-glossary.md#notification-button), which is used to display an interactive button in the live view. |
| [NotificationCapsule](arkts-notification-notificationcontent-notificationcapsule-i.md) | Describes the [notification capsule](../../../notification/notification-glossary.md#notification-capsule), which is used to display the capsule form in the live view. |
| [NotificationContent](arkts-notification-notificationcontent-i.md) | NotificationContent defines the content structure of a notification and provides interfaces for describing multiple notification content types. When an application needs to publish a notification, it can select the corresponding content type interface to construct the [notification content](../../../notification/notification-glossary.md#notification-content) based on the display requirements of the notification (such as basic text, long text, multi-line text, picture, and live view). |
| [NotificationLongTextContent](arkts-notification-notificationcontent-notificationlongtextcontent-i.md) | Describes the long text notification. This API is inherited from [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md). |
| [NotificationMultiLineContent](arkts-notification-notificationcontent-notificationmultilinecontent-i.md) | Describes the multi-line text notification. This API is inherited from [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md). |
| [NotificationPictureContent](arkts-notification-notificationcontent-notificationpicturecontent-i.md) | Describes the picture-attached notification. This API is inherited from [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md). |
| [NotificationProgress](arkts-notification-notificationcontent-notificationprogress-i.md) | Describes the [notification progress](../../../notification/notification-glossary.md#notification-progress), which is used to display progress bar information in the live view. |
| [NotificationSystemLiveViewContent](arkts-notification-notificationcontent-notificationsystemliveviewcontent-i.md) | Describes the [system live view](../../../notification/notification-glossary.md#system-live-view) [notification content](../../../notification/notification-glossary.md#notification-content), which is used to display real-time status information in the live view. Third-party applications are not supported to directly create this type of notification. After the system agent creates a system live view type notification, a third-party application can publish a notification with the same ID to update the specified content. This API is inherited from [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md). |
| [NotificationTime](arkts-notification-notificationcontent-notificationtime-i.md) | Describes the notification timing information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i-sys.md) | Describes the basic text notification, which is used to display the title and body content. It serves as basic content structure for other notification types. Other notification types (such as long text, multi-line text, picture, and live view) inherit this API and extend their own specific fields on this basis. |
| [NotificationCapsule](arkts-notification-notificationcontent-notificationcapsule-i-sys.md) | Describes the [notification capsule](../../../notification/notification-glossary.md#notification-capsule), which is used to display the capsule form in the live view. |
| [NotificationContent](arkts-notification-notificationcontent-i-sys.md) | NotificationContent defines the content structure of a notification and provides interfaces for describing multiple notification content types. When an application needs to publish a notification, it can select the corresponding content type interface to construct the [notification content](../../../notification/notification-glossary.md#notification-content) based on the display requirements of the notification (such as basic text, long text, multi-line text, picture, and live view). |
| [NotificationIconButton](arkts-notification-notificationcontent-notificationiconbutton-i-sys.md) | Describes the system [notification button](../../../notification/notification-glossary.md#notification-button). |
| [NotificationLiveViewContent](arkts-notification-notificationcontent-notificationliveviewcontent-i-sys.md) | Describes the [normal live view notification](../../../notification/notification-glossary.md#normal-live-view). This API is inherited from [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md). |
| [NotificationMultiLineContent](arkts-notification-notificationcontent-notificationmultilinecontent-i-sys.md) | Describes the multi-line text notification. This API is inherited from [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md). |
| [NotificationSystemLiveViewContent](arkts-notification-notificationcontent-notificationsystemliveviewcontent-i-sys.md) | Describes the [system live view](../../../notification/notification-glossary.md#system-live-view) [notification content](../../../notification/notification-glossary.md#notification-content), which is used to display real-time status information in the live view. Third-party applications are not supported to directly create this type of notification. After the system agent creates a system live view type notification, a third-party application can publish a notification with the same ID to update the specified content. This API is inherited from [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md). |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [IconType](arkts-notification-icontype-t-sys.md) | Describes the icon types. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [LiveViewStatus](arkts-notification-notificationcontent-liveviewstatus-e-sys.md) | Describes the status of the [normal live view notification](../../../notification/notification-glossary.md#normal-live-view). |
| [LiveViewTypes](arkts-notification-notificationcontent-liveviewtypes-e-sys.md) | Describes the type of the [live view notification](../../../notification/notification-glossary.md#live-view-notification). |
<!--DelEnd-->
