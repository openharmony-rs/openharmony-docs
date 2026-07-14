# NotificationCapsule

描述通知胶囊。

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## backgroundColor

```TypeScript
backgroundColor?: string
```

背景颜色。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## icon

```TypeScript
icon?: image.PixelMap
```

胶囊图片。图标像素的总字节数不超过192KB（图标像素的总字节数通过
[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md#getpixelbytesnumber-1)获取），
建议图标像素长宽为128*128。实际显示效果依赖于设备能力和通知中心UI样式。

**类型：** image.PixelMap

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## title

```TypeScript
title?: string
```

胶囊标题。大小不超过200字节，超出部分会被截断。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

