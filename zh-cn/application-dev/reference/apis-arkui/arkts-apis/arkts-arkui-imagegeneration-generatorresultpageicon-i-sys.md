# GeneratorResultPageIcon（系统接口）

```TypeScript
interface GeneratorResultPageIcon
```

ImageGeneratorDialog生成结果页面中的自定义图标对象。

**起始版本：** 23

<!--Device-imageGeneration-interface GeneratorResultPageIcon--><!--Device-imageGeneration-interface GeneratorResultPageIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## callback

```TypeScript
callback: Callback<GeneratorResult>
```

图标点击事件回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GeneratorResult](arkts-arkui-imagegeneration-generatorresult-i-sys.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorResultPageIcon-callback: Callback<GeneratorResult>--><!--Device-GeneratorResultPageIcon-callback: Callback<GeneratorResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## image

```TypeScript
image: image.PixelMap | string | Resource
```

图标图像信息。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorResultPageIcon-image: image.PixelMap | string | Resource--><!--Device-GeneratorResultPageIcon-image: image.PixelMap | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## text

```TypeScript
text: ResourceStr
```

图标文本描述。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorResultPageIcon-text: ResourceStr--><!--Device-GeneratorResultPageIcon-text: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
