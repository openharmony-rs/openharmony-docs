# notificationContent(Some notification types and content)

The **NotificationContent** defines the content structure of a notification and provides content description API
 of multiple notification types. When an application needs to publish a notification, it can select the
 corresponding content type API to construct the notification content based on the display requirements (such as
 plain text, long text, multi-line text, picture, or live view).



## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md) | Describes the basic text notification, which is used to display the title and body content. It serves as the basic content structure for other notification types. Other notification types (such as long text, multi-line text, picture, and live view) inherit this API and extend their own specific fields on this basis. |
| [NotificationButton](arkts-notification-notificationcontent-notificationbutton-i.md) | Describes the notification button, which is used to display an interactive button in the live view. |
| [NotificationCapsule](arkts-notification-notificationcontent-notificationcapsule-i.md) | Describes the notification capsule, which is used to display the capsule form in the live view. |
| [NotificationContent](arkts-notification-notificationcontent-notificationcontent-i.md) | Describes the notification contents. |
| [NotificationLongTextContent](arkts-notification-notificationcontent-notificationlongtextcontent-i.md) | Describes the long text notification. This API is inherited from NotificationBasicContent. |
| [NotificationMultiLineContent](arkts-notification-notificationcontent-notificationmultilinecontent-i.md) | Describes the multi-line text notification. This API is inherited from NotificationBasicContent. |
| [NotificationPictureContent](arkts-notification-notificationcontent-notificationpicturecontent-i.md) | Describes the picture-attached notification. This API is inherited from NotificationBasicContent. |
| [NotificationProgress](arkts-notification-notificationcontent-notificationprogress-i.md) | Describes the notification progress, which is used to display progress bar information in the live view. |
| [NotificationSystemLiveViewContent](arkts-notification-notificationcontent-notificationsystemliveviewcontent-i.md) | Describes the system live view notification content, which is used to display real-time status information in the live view. Third-party applications are not supported to directly create this notification type. After the system proxy creates a system live view notification, a third-party application can publish a notification with the same ID to update the specified content. This API is inherited from NotificationBasicContent. |
| [NotificationTime](arkts-notification-notificationcontent-notificationtime-i.md) | Describes the notification timing information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i-sys.md) | Describes the basic text notification, which is used to display the title and body content. It serves as the basic content structure for other notification types. Other notification types (such as long text, multi-line text, picture, and live view) inherit this API and extend their own specific fields on this basis. |
| [NotificationCapsule](arkts-notification-notificationcontent-notificationcapsule-i-sys.md) | Describes the notification capsule, which is used to display the capsule form in the live view. |
| [NotificationContent](arkts-notification-notificationcontent-notificationcontent-i-sys.md) | Describes the notification contents. |
| [NotificationIconButton](arkts-notification-notificationcontent-notificationiconbutton-i-sys.md) | Describes the system notification button. |
| [NotificationLiveViewContent](arkts-notification-notificationcontent-notificationliveviewcontent-i-sys.md) | Describes the normal live notification content. This API inherits from NotificationBasicContent. |
| [NotificationMultiLineContent](arkts-notification-notificationcontent-notificationmultilinecontent-i-sys.md) | Describes the multi-line text notification. This API is inherited from NotificationBasicContent. |
| [NotificationSystemLiveViewContent](arkts-notification-notificationcontent-notificationsystemliveviewcontent-i-sys.md) | Describes the system live view notification content, which is used to display real-time status information in the live view. Third-party applications are not supported to directly create this notification type. After the system proxy creates a system live view notification, a third-party application can publish a notification with the same ID to update the specified content. This API is inherited from NotificationBasicContent. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [LiveViewStatus](arkts-notification-notificationcontent-liveviewstatus-e-sys.md) | Enumerates the statuses of the common live view. |
| [LiveViewTypes](arkts-notification-notificationcontent-liveviewtypes-e-sys.md) | Enumerates live view types. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [IconType](arkts-notification-icontype-t-sys.md) | Describes the icon types. |
<!--DelEnd-->
