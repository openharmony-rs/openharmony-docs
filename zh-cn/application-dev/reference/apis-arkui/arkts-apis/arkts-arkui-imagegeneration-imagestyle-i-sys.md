# ImageStyle（系统接口）

```TypeScript
interface ImageStyle
```

AI图像生成模型支持的风格类型，如涂鸦、水彩画。

**起始版本：** 23

<!--Device-imageGeneration-interface ImageStyle--><!--Device-imageGeneration-interface ImageStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## icon

```TypeScript
icon: image.PixelMap | string | Resource
```

将在样式列表中显示的风格图标信息。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageStyle-icon: image.PixelMap | string | Resource--><!--Device-ImageStyle-icon: image.PixelMap | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: ResourceStr
```

将在样式列表中显示的样式名称信息。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageStyle-name: ResourceStr--><!--Device-ImageStyle-name: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
