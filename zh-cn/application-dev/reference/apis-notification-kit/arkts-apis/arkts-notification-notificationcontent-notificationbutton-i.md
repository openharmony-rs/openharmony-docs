# NotificationButton

描述通知按钮，用于在实况窗中展示可交互的按钮。

> **说明：**  
>  
> 实际显示效果依赖于设备能力和通知中心UI样式。

**起始版本：** 11

<!--Device-unnamed-export interface NotificationButton--><!--Device-unnamed-export interface NotificationButton-End-->

**系统能力：** SystemCapability.Notification.Notification

## icons

```TypeScript
icons?: Array<image.PixelMap>
```

按钮图标列表，与names一一对应，每个图标显示在对应按钮上。最多支持3个。图标像素的总字节数不超过192KB（图标像素的总字节数通过[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber-1)获取），建议图标像素长宽为128*128。默认为空。该属性与iconsResource互斥，只使用其中一个即可。

**类型：** Array&lt;image.PixelMap&gt;

**起始版本：** 11

<!--Device-NotificationButton-icons?: Array<image.PixelMap>--><!--Device-NotificationButton-icons?: Array<image.PixelMap>-End-->

**系统能力：** SystemCapability.Notification.Notification

## iconsResource

```TypeScript
iconsResource?: Array<Resource>
```

按钮图标资源列表，与names一一对应，使用Resource资源引用图标。最多支持3个。默认为空。与icons互斥，只使用其中一个即可。

**类型：** Array&lt;Resource&gt;

**起始版本：** 12

<!--Device-NotificationButton-iconsResource?: Array<Resource>--><!--Device-NotificationButton-iconsResource?: Array<Resource>-End-->

**系统能力：** SystemCapability.Notification.Notification

## names

```TypeScript
names?: Array<string>
```

按钮名称列表，每个名称对应一个通知按钮的文本显示。最多支持3个按钮。每个名称的大小不超过202字节，超出部分会被截断。默认为空。

**类型：** Array&lt;string&gt;

**起始版本：** 11

<!--Device-NotificationButton-names?: Array<string>--><!--Device-NotificationButton-names?: Array<string>-End-->

**系统能力：** SystemCapability.Notification.Notification

