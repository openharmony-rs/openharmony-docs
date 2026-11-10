# GeneratorDialogOptions（系统接口）

```TypeScript
interface GeneratorDialogOptions
```

用于打开ImageGeneratorDialog的参数。

**起始版本：** 23

<!--Device-imageGeneration-interface GeneratorDialogOptions--><!--Device-imageGeneration-interface GeneratorDialogOptions-End-->

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

用于AI生成图像任务的初始文本信息。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorDialogOptions-content?: ResourceStr--><!--Device-GeneratorDialogOptions-content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## customIcons

```TypeScript
customIcons?: Array<GeneratorResultPageIcon>
```

AI生成图像结果页面上使用的自定义图标。

**类型：** Array&lt;[GeneratorResultPageIcon](arkts-arkui-imagegeneration-generatorresultpageicon-i-sys.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorDialogOptions-customIcons?: Array<GeneratorResultPageIcon>--><!--Device-GeneratorDialogOptions-customIcons?: Array<GeneratorResultPageIcon>-End-->

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

<!--Device-GeneratorDialogOptions-customImportIcon?: CustomImportIcon--><!--Device-GeneratorDialogOptions-customImportIcon?: CustomImportIcon-End-->

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

<!--Device-GeneratorDialogOptions-imageGenerationModel?: ImageGenerationModel--><!--Device-GeneratorDialogOptions-imageGenerationModel?: ImageGenerationModel-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## images

```TypeScript
images?: Array<ImageItem>
```

用于AI生成图像任务的初始图像参数。

**类型：** Array&lt;[ImageItem](arkts-arkui-imagegeneration-imageitem-i-sys.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorDialogOptions-images?: Array<ImageItem>--><!--Device-GeneratorDialogOptions-images?: Array<ImageItem>-End-->

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

<!--Device-GeneratorDialogOptions-liveViewInfo?: LiveViewInfo--><!--Device-GeneratorDialogOptions-liveViewInfo?: LiveViewInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## minimizeDuringGeneration

```TypeScript
minimizeDuringGeneration?: boolean
```

是否在生成图像过程中启用最小化。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorDialogOptions-minimizeDuringGeneration?: boolean--><!--Device-GeneratorDialogOptions-minimizeDuringGeneration?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## onAreaDidChange

```TypeScript
onAreaDidChange?: Callback<common2D.Rect>
```

当ImageGeneratorDialog的大小或位置发生变化时触发的回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[common2D.Rect](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-common2d-rect-i.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GeneratorDialogOptions-onAreaDidChange?: Callback<common2D.Rect>--><!--Device-GeneratorDialogOptions-onAreaDidChange?: Callback<common2D.Rect>-End-->

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

<!--Device-GeneratorDialogOptions-textGenerationModel?: TextGenerationModel--><!--Device-GeneratorDialogOptions-textGenerationModel?: TextGenerationModel-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
