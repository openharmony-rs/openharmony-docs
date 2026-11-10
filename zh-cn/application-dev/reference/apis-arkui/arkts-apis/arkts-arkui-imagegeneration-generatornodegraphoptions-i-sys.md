# GeneratorNodeGraphOptions（系统接口）

```TypeScript
interface GeneratorNodeGraphOptions
```

打开NodeGraphComponent的参数。

**起始版本：** 23

<!--Device-imageGeneration-interface GeneratorNodeGraphOptions--><!--Device-imageGeneration-interface GeneratorNodeGraphOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## customIcons

```TypeScript
customIcons?: Array<GeneratorResultPageIcon>
```

AI生成图像结果页面上使用的自定义图标。

**类型：** Array&lt;[GeneratorResultPageIcon](arkts-arkui-imagegeneration-generatorresultpageicon-i-sys.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorNodeGraphOptions-customIcons?: Array<GeneratorResultPageIcon>--><!--Device-GeneratorNodeGraphOptions-customIcons?: Array<GeneratorResultPageIcon>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## customImportIcon

```TypeScript
customImportIcon?: CustomImportIcon
```

以下配置参数用于自定义导入的图标。

**类型：** [CustomImportIcon](arkts-arkui-imagegeneration-customimporticon-i-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorNodeGraphOptions-customImportIcon?: CustomImportIcon--><!--Device-GeneratorNodeGraphOptions-customImportIcon?: CustomImportIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## imageGenerationModel

```TypeScript
imageGenerationModel?: ImageGenerationModel
```

用于AI生成图像任务的模型。

**类型：** [ImageGenerationModel](arkts-arkui-imagegeneration-imagegenerationmodel-i-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorNodeGraphOptions-imageGenerationModel?: ImageGenerationModel--><!--Device-GeneratorNodeGraphOptions-imageGenerationModel?: ImageGenerationModel-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## liveViewInfo

```TypeScript
liveViewInfo?: LiveViewInfo
```

AI图像生成过程中的实况窗的信息。

**类型：** [LiveViewInfo](arkts-arkui-imagegeneration-liveviewinfo-i-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorNodeGraphOptions-liveViewInfo?: LiveViewInfo--><!--Device-GeneratorNodeGraphOptions-liveViewInfo?: LiveViewInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## textGenerationModel

```TypeScript
textGenerationModel?: TextGenerationModel
```

用于AI生成图像任务中的文本润色模型。

**类型：** [TextGenerationModel](arkts-arkui-imagegeneration-textgenerationmodel-i-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorNodeGraphOptions-textGenerationModel?: TextGenerationModel--><!--Device-GeneratorNodeGraphOptions-textGenerationModel?: TextGenerationModel-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
