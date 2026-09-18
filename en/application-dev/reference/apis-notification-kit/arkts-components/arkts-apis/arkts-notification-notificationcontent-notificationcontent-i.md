# NotificationContent

Describes the notification contents.

**Since:** 7

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

**System capability:** SystemCapability.Notification.Notification

## longText

```TypeScript
longText?: NotificationLongTextContent
```

Long text notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_LONG_TEXT**. The complete long text content can be displayed after the notification is expanded.

**Type:** [NotificationLongTextContent](arkts-notification-notificationcontent-notificationlongtextcontent-i.md)

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## multiLine

```TypeScript
multiLine?: NotificationMultiLineContent
```

Multi-line notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_MULTILINE**. The notification is displayed in a multi-line list style after expansion.

**Type:** [NotificationMultiLineContent](arkts-notification-notificationcontent-notificationmultilinecontent-i.md)

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## normal

```TypeScript
normal?: NotificationBasicContent
```

Basic notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_BASIC_TEXT**. The notification displays the title and body in a plain text style.

**Type:** [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## notificationContentType

```TypeScript
notificationContentType?: notificationManager.ContentType
```

Notification content type, used to specify the content layout type of the notification, which determines the display style of the notification in the notification center. It must be used together with the corresponding notification content object. For example, when this parameter is set to **NOTIFICATION_CONTENT_BASIC_TEXT**, the **normal** field must be specified at the same time.

**Type:** [notificationManager.ContentType](arkts-notification-notificationmanager-contenttype-e.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## picture

```TypeScript
picture?: NotificationPictureContent
```

Picture notification content. This parameter is used when **notificationContentType** is **NOTIFICATION_CONTENT_PICTURE**. The picture can be displayed after the notification is expanded.

**Type:** [NotificationPictureContent](arkts-notification-notificationcontent-notificationpicturecontent-i.md)

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## systemLiveView

```TypeScript
systemLiveView?: NotificationSystemLiveViewContent
```

System live view notification content. Third-party applications are not supported to directly create this type of notification. After a system agent creates a system live view notification, a third-party application can publish a notification with the same ID to update the specified content.

**Type:** [NotificationSystemLiveViewContent](arkts-notification-notificationcontent-notificationsystemliveviewcontent-i.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification
