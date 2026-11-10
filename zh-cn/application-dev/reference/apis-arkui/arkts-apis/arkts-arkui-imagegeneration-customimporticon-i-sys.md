# CustomImportIcon（系统接口）

```TypeScript
interface CustomImportIcon
```

自定义导入图标，用于从应用端添加图片和文字。

**起始版本：** 26.0.0

<!--Device-imageGeneration-interface CustomImportIcon--><!--Device-imageGeneration-interface CustomImportIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## callback

```TypeScript
callback: CustomImportCallback
```

导入操作的异步回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomImportIcon-callback: CustomImportCallback--><!--Device-CustomImportIcon-callback: CustomImportCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## image

```TypeScript
image: image.PixelMap | ResourceStr
```

图标图片信息。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) &#124; [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomImportIcon-image: image.PixelMap | ResourceStr--><!--Device-CustomImportIcon-image: image.PixelMap | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## text

```TypeScript
text: ResourceStr
```

图标文字描述。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomImportIcon-text: ResourceStr--><!--Device-CustomImportIcon-text: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
