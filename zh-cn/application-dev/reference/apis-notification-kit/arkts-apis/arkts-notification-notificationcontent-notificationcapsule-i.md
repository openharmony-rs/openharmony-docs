# NotificationCapsule

描述通知胶囊，用于在实况窗中展示胶囊形态。
> **说明：**  
>  
> 实际显示效果依赖于设备能力和通知中心UI样式。

**起始版本：** 11

<!--Device-unnamed-export interface NotificationCapsule--><!--Device-unnamed-export interface NotificationCapsule-End-->

**系统能力：** SystemCapability.Notification.Notification

## backgroundColor

```TypeScript
backgroundColor?: string
```

胶囊背景颜色。支持rgb、rgba或者argb的格式颜色。rgb格式颜色示例：'#ffffff'、'rgb(255, 100, 255)'。rgba格式颜色示例：'rgba(255, 100, 255, 0.5)'。argb格式颜色示例：'#ff000000'。大小不超过202字节，超出部分会被截断。默认为空。

**类型：** string

**起始版本：** 11

<!--Device-NotificationCapsule-backgroundColor?: string--><!--Device-NotificationCapsule-backgroundColor?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## icon

```TypeScript
icon?: image.PixelMap
```

胶囊图标。图标像素的总字节数不超过192KB（图标像素的总字节数通过[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber)获取），建议图标像素长宽为128*128。

**类型：** image.PixelMap

**起始版本：** 11

<!--Device-NotificationCapsule-icon?: image.PixelMap--><!--Device-NotificationCapsule-icon?: image.PixelMap-End-->

**系统能力：** SystemCapability.Notification.Notification

## title

```TypeScript
title?: string
```

胶囊标题。大小不超过202字节，超出部分会被截断。默认为空。

**类型：** string

**起始版本：** 11

<!--Device-NotificationCapsule-title?: string--><!--Device-NotificationCapsule-title?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

