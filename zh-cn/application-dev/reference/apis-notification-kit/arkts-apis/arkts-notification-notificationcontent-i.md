# NotificationContent

通知内容。

**起始版本：** 7

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

**替代接口：** [notificationContentType](arkts-notification-notificationcontent-i.md#notificationcontenttype)

**系统能力：** SystemCapability.Notification.Notification

## longText

```TypeScript
longText?: NotificationLongTextContent
```

长文本类型通知内容。

**类型：** NotificationLongTextContent

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## multiLine

```TypeScript
multiLine?: NotificationMultiLineContent
```

多行类型通知内容。

**类型：** NotificationMultiLineContent

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## normal

```TypeScript
normal?: NotificationBasicContent
```

基本类型通知内容。

**类型：** NotificationBasicContent

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## notificationContentType

```TypeScript
notificationContentType?: notificationManager.ContentType
```

通知内容类型。

**类型：** notificationManager.ContentType

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## picture

```TypeScript
picture?: NotificationPictureContent
```

图片类型通知内容。

**类型：** NotificationPictureContent

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## systemLiveView

```TypeScript
systemLiveView?: NotificationSystemLiveViewContent
```

系统实况窗类型通知内容。不支持三方应用直接创建该类型通知，可以由系统代理创建系统实况窗类型通知后，三方应用发布同ID的通知来更新指定内容。

**类型：** NotificationSystemLiveViewContent

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

