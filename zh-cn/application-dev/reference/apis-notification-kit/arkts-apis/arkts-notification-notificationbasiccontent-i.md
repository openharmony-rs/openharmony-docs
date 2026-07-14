# NotificationBasicContent

描述普通文本通知。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## additionalText

```TypeScript
additionalText?: string
```

通知附加内容，默认为空，是对通知内容的补充（大小不超过3072字节，超出部分会被截断）。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## lockscreenPicture

```TypeScript
lockscreenPicture?: image.PixelMap
```

通知在锁屏界面显示的图片，默认为空。当前仅支持实况窗类型通知。图标像素的总字节数不超过192KB（图标像素的总字节数通过
[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md#getpixelbytesnumber-1)获取），建议图标像素长宽为128*128。实际显示效果依赖
于设备能力和通知中心UI样式。

**类型：** image.PixelMap

**起始版本：** 12

**系统能力：** SystemCapability.Notification.Notification

## text

```TypeScript
text: string
```

通知内容（不可为空字符串，大小不超过3072字节，超出部分会被截断）。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## title

```TypeScript
title: string
```

通知标题（不可为空字符串，大小不超过1024字节，超出部分会被截断）。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

