# CustomImportResult（系统接口）

```TypeScript
interface CustomImportResult
```

自定义导入图标的导入结果。

**起始版本：** 26.0.0

<!--Device-imageGeneration-interface CustomImportResult--><!--Device-imageGeneration-interface CustomImportResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## content

```TypeScript
content?: ResourceStr
```

导入操作的文本内容。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomImportResult-content?: ResourceStr--><!--Device-CustomImportResult-content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## images

```TypeScript
images?: Array<ImageItem>
```

用于导入操作的图片相关的数组。

**类型：** Array&lt;[ImageItem](arkts-arkui-imagegeneration-imageitem-i-sys.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomImportResult-images?: Array<ImageItem>--><!--Device-CustomImportResult-images?: Array<ImageItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
