# NotificationContent

```TypeScript
export interface NotificationContent
```

NotificationContent defines the content structure of a notification and provides interfaces for describing multiple notification content types. When an application needs to publish a notification, it can select the corresponding content type interface to construct the [notification content](../../../notification/notification-glossary.md#notification-content) based on the display requirements of the notification (such as basic text, long text, multi-line text, picture, and live view).

**Since:** 7

<!--Device-unnamed-export interface NotificationContent--><!--Device-unnamed-export interface NotificationContent-End-->

**System capability:** SystemCapability.Notification.Notification

## longText

```TypeScript
longText?: NotificationLongTextContent
```

Long text notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_LONG_TEXT**. The complete long text content can be displayed after the notification is expanded.

**Type:** [NotificationLongTextContent](arkts-notification-notificationcontent-notificationlongtextcontent-i.md)

**Since:** 7

<!--Device-NotificationContent-longText?: NotificationLongTextContent--><!--Device-NotificationContent-longText?: NotificationLongTextContent-End-->

**System capability:** SystemCapability.Notification.Notification

## multiLine

```TypeScript
multiLine?: NotificationMultiLineContent
```

Multi-line notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_MULTILINE**. The notification is displayed in a multi-line list style after expansion.

**Type:** [NotificationMultiLineContent](arkts-notification-notificationcontent-notificationmultilinecontent-i.md)

**Since:** 7

<!--Device-NotificationContent-multiLine?: NotificationMultiLineContent--><!--Device-NotificationContent-multiLine?: NotificationMultiLineContent-End-->

**System capability:** SystemCapability.Notification.Notification

## normal

```TypeScript
normal?: NotificationBasicContent
```

Basic notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_BASIC_TEXT**. The notification displays the title and body in a basic text style.

**Type:** [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**Since:** 7

<!--Device-NotificationContent-normal?: NotificationBasicContent--><!--Device-NotificationContent-normal?: NotificationBasicContent-End-->

**System capability:** SystemCapability.Notification.Notification

## notificationContentType

```TypeScript
notificationContentType?: notificationManager.ContentType
```

[Content type](../../../notification/notification-glossary.md#content-type) of the notification, which specifies the content layout type of the notification and determines the display style of the notification in the [notification center](../../../notification/notification-glossary.md#notification-center). It must be used together with the notification content object of the corresponding type. For example, when it is set to **NOTIFICATION_CONTENT_BASIC_TEXT**, the **normal** field must also be filled in.

**Type:** [notificationManager.ContentType](arkts-notification-notificationmanager-contenttype-e.md)

**Since:** 11

<!--Device-NotificationContent-notificationContentType?: notificationManager.ContentType--><!--Device-NotificationContent-notificationContentType?: notificationManager.ContentType-End-->

**System capability:** SystemCapability.Notification.Notification

## picture

```TypeScript
picture?: NotificationPictureContent
```

Picture notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_PICTURE**. The picture can be displayed after the notification is expanded.

**Type:** [NotificationPictureContent](arkts-notification-notificationcontent-notificationpicturecontent-i.md)

**Since:** 7

<!--Device-NotificationContent-picture?: NotificationPictureContent--><!--Device-NotificationContent-picture?: NotificationPictureContent-End-->

**System capability:** SystemCapability.Notification.Notification

## systemLiveView

```TypeScript
systemLiveView?: NotificationSystemLiveViewContent
```

[System live view](../../../notification/notification-glossary.md#system-live-view) type notification content. Third-party applications cannot directly create this type of notification. After the system agent creates a system live view type notification, a third-party application can publish a notification with the same ID to update the specified content.

**Type:** [NotificationSystemLiveViewContent](arkts-notification-notificationcontent-notificationsystemliveviewcontent-i.md)

**Since:** 11

<!--Device-NotificationContent-systemLiveView?: NotificationSystemLiveViewContent--><!--Device-NotificationContent-systemLiveView?: NotificationSystemLiveViewContent-End-->

**System capability:** SystemCapability.Notification.Notification

## contentType

```TypeScript
contentType?: notification.ContentType
```

Notification content type.

**Type:** [notification.ContentType](arkts-notification-notification-contenttype-depr-e.md)

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [notificationContentType](#notificationcontenttype)

<!--Device-NotificationContent-contentType?: notification.ContentType--><!--Device-NotificationContent-contentType?: notification.ContentType-End-->

**System capability:** SystemCapability.Notification.Notification
