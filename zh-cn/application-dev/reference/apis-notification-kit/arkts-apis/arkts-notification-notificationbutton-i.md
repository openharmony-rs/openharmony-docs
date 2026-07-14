# NotificationButton

描述通知按钮。

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## icons

```TypeScript
icons?: Array<image.PixelMap>
```

按钮图片（最多支持3个）。图标像素的总字节数不超过192KB图标像素的总字节数通过
[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md#getpixelbytesnumber-1)获取），建议图标像素长宽为128*128。实际显示效果依赖
于设备能力和通知中心UI样式。

**类型：** Array<image.PixelMap>

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## iconsResource

```TypeScript
iconsResource?: Array<Resource>
```

按钮资源（最多支持3个）。

**类型：** Array<Resource>

**起始版本：** 12

**系统能力：** SystemCapability.Notification.Notification

## names

```TypeScript
names?: Array<string>
```

按钮名称（最多支持3个）。

**类型：** Array<string>

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

