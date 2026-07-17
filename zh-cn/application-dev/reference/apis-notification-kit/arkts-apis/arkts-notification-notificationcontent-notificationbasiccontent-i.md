# NotificationBasicContent

描述普通文本通知，用于展示标题和正文内容，是其他通知类型的基础内容结构。其他通知类型（如长文本、多行文本、图片、实况窗）均继承本接口，在此基础上扩展各自特有字段。

**起始版本：** 7

<!--Device-unnamed-export interface NotificationBasicContent--><!--Device-unnamed-export interface NotificationBasicContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## additionalText

```TypeScript
additionalText?: string
```

通知附加内容，是对通知内容的补充，不在通知中心中显示。默认为空。大小不超过3072字节，超出部分会被截断。

**类型：** string

**起始版本：** 7

<!--Device-NotificationBasicContent-additionalText?: string--><!--Device-NotificationBasicContent-additionalText?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## lockscreenPicture

```TypeScript
lockscreenPicture?: image.PixelMap
```

通知在锁屏界面显示的图片，默认为空。当前仅支持实况窗类型通知。图标像素的总字节数不超过192KB（图标像素的总字节数通过[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber-1)获取），建议图标像素长宽为128*128。实际显示效果依赖于设备能力和通知中心UI样式。

**类型：** image.PixelMap

**起始版本：** 12

<!--Device-NotificationBasicContent-lockscreenPicture?: image.PixelMap--><!--Device-NotificationBasicContent-lockscreenPicture?: image.PixelMap-End-->

**系统能力：** SystemCapability.Notification.Notification

## text

```TypeScript
text: string
```

通知正文内容，显示在标题下方。不可为空字符串，大小不超过3072字节，超出部分会被截断。

**类型：** string

**起始版本：** 7

<!--Device-NotificationBasicContent-text: string--><!--Device-NotificationBasicContent-text: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## title

```TypeScript
title: string
```

通知标题，显示在通知顶部。不可为空字符串，大小不超过1024字节，超出部分会被截断。

**类型：** string

**起始版本：** 7

<!--Device-NotificationBasicContent-title: string--><!--Device-NotificationBasicContent-title: string-End-->

**系统能力：** SystemCapability.Notification.Notification

