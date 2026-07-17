# NotificationContent

通知内容。

**起始版本：** 7

<!--Device-unnamed-export interface NotificationContent--><!--Device-unnamed-export interface NotificationContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## contentType

```TypeScript
contentType?: notification.ContentType
```

通知内容类型。

从API version 7开始支持，从API version 11开始废弃，建议使用notificationContentType替代。

**类型：** notification.ContentType

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [notificationContentType](arkts-notification-notificationcontent-notificationcontent-i.md#notificationcontenttype)

<!--Device-NotificationContent-contentType?: notification.ContentType--><!--Device-NotificationContent-contentType?: notification.ContentType-End-->

**系统能力：** SystemCapability.Notification.Notification

## longText

```TypeScript
longText?: NotificationLongTextContent
```

长文本类型通知内容。当notificationContentType为NOTIFICATION_CONTENT_LONG_TEXT时使用，通知展开后可展示完整长文本内容。

**类型：** NotificationLongTextContent

**起始版本：** 7

<!--Device-NotificationContent-longText?: NotificationLongTextContent--><!--Device-NotificationContent-longText?: NotificationLongTextContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## multiLine

```TypeScript
multiLine?: NotificationMultiLineContent
```

多行类型通知内容。当notificationContentType为NOTIFICATION_CONTENT_MULTILINE时使用，通知展开后以多行列表样式展示。

**类型：** NotificationMultiLineContent

**起始版本：** 7

<!--Device-NotificationContent-multiLine?: NotificationMultiLineContent--><!--Device-NotificationContent-multiLine?: NotificationMultiLineContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## normal

```TypeScript
normal?: NotificationBasicContent
```

基本类型通知内容。当notificationContentType为NOTIFICATION_CONTENT_BASIC_TEXT时使用，通知以普通文本样式展示标题和正文。

**类型：** NotificationBasicContent

**起始版本：** 7

<!--Device-NotificationContent-normal?: NotificationBasicContent--><!--Device-NotificationContent-normal?: NotificationBasicContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## notificationContentType

```TypeScript
notificationContentType?: notificationManager.ContentType
```

通知内容类型，用于指定通知的内容布局类型，决定了通知在通知中心中的展示样式。需与对应类型的通知内容对象配合使用，例如设置为NOTIFICATION_CONTENT_BASIC_TEXT时需同时填充normal字段。

**类型：** notificationManager.ContentType

**起始版本：** 11

<!--Device-NotificationContent-notificationContentType?: notificationManager.ContentType--><!--Device-NotificationContent-notificationContentType?: notificationManager.ContentType-End-->

**系统能力：** SystemCapability.Notification.Notification

## picture

```TypeScript
picture?: NotificationPictureContent
```

图片类型通知内容。当notificationContentType为NOTIFICATION_CONTENT_PICTURE时使用。通知展开后可展示图片。

**类型：** NotificationPictureContent

**起始版本：** 7

<!--Device-NotificationContent-picture?: NotificationPictureContent--><!--Device-NotificationContent-picture?: NotificationPictureContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## systemLiveView

```TypeScript
systemLiveView?: NotificationSystemLiveViewContent
```

系统实况窗类型通知内容。不支持三方应用直接创建该类型通知，可以由系统代理创建系统实况窗类型通知后，三方应用发布同ID的通知来更新指定内容。

**类型：** NotificationSystemLiveViewContent

**起始版本：** 11

<!--Device-NotificationContent-systemLiveView?: NotificationSystemLiveViewContent--><!--Device-NotificationContent-systemLiveView?: NotificationSystemLiveViewContent-End-->

**系统能力：** SystemCapability.Notification.Notification

