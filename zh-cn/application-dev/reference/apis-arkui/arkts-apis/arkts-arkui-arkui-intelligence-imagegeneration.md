# @ohos.arkui.intelligence.imageGeneration

使用UI组件的AI生成图像模块

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace imageGeneration--><!--Device-unnamed-declare namespace imageGeneration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [closeGeneratorDialog](arkts-arkui-imagegeneration-closegeneratordialog-f-sys.md#closegeneratordialog-1) | 关闭AI图像生成任务弹窗。 |
| [closeGeneratorNodeGraph](arkts-arkui-imagegeneration-closegeneratornodegraph-f-sys.md#closegeneratornodegraph-1) | 关闭AI节点图Sheet页。 |
| [hideGeneratorDialog](arkts-arkui-imagegeneration-hidegeneratordialog-f-sys.md#hidegeneratordialog-1) | 隐藏AI图像生成任务弹窗。 |
| [hideGeneratorNodeGraph](arkts-arkui-imagegeneration-hidegeneratornodegraph-f-sys.md#hidegeneratornodegraph-1) | 隐藏AI节点图Sheet页。 |
| [openGeneratorNodeGraph](arkts-arkui-imagegeneration-opengeneratornodegraph-f-sys.md#opengeneratornodegraph-1) | 打开AI节点图Sheet页。 |
| [restoreGeneratorDialog](arkts-arkui-imagegeneration-restoregeneratordialog-f-sys.md#restoregeneratordialog-1) | 恢复AI图像生成任务弹窗。 |
| [restoreGeneratorNodeGraph](arkts-arkui-imagegeneration-restoregeneratornodegraph-f-sys.md#restoregeneratornodegraph-1) | 恢复AI节点图Sheet页。 |
| [showGeneratorDialog](arkts-arkui-imagegeneration-showgeneratordialog-f-sys.md#showgeneratordialog-1) | 打开AI图像生成任务弹窗并执行AI图像生成操作。 |
| [startSmartCanvasService](arkts-arkui-imagegeneration-startsmartcanvasservice-f-sys.md#startsmartcanvasservice-1) | 启动智能画布服务。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CustomImportIcon](arkts-arkui-imagegeneration-customimporticon-i-sys.md) | 自定义导入图标，用于从应用端添加图片和文字。 |
| [CustomImportResult](arkts-arkui-imagegeneration-customimportresult-i-sys.md) | 自定义导入图标的导入结果。 |
| [GenerateImageTaskParams](arkts-arkui-imagegeneration-generateimagetaskparams-i-sys.md) | AI生成图像任务的配置参数选项。 |
| [GenerateImageTaskPartialResult](arkts-arkui-imagegeneration-generateimagetaskpartialresult-i-sys.md) | AI生成图像任务的配置流结果。 |
| [GenerateImageTaskResult](arkts-arkui-imagegeneration-generateimagetaskresult-i-sys.md) | AI生成图像任务的配置结果。 |
| [GenerateTextTaskPartialResult](arkts-arkui-imagegeneration-generatetexttaskpartialresult-i-sys.md) | AI生成文本任务的配置流结果。 |
| [GenerateTextTaskResult](arkts-arkui-imagegeneration-generatetexttaskresult-i-sys.md) | AI生成文本任务的配置结果。 |
| [GeneratorDialogOptions](arkts-arkui-imagegeneration-generatordialogoptions-i-sys.md) | 用于打开ImageGeneratorDialog的参数。 |
| [GeneratorNodeGraphOptions](arkts-arkui-imagegeneration-generatornodegraphoptions-i-sys.md) | 打开NodeGraphComponent的参数。 |
| [GeneratorResult](arkts-arkui-imagegeneration-generatorresult-i-sys.md) | AI生成图像的结果 |
| [GeneratorResultPageIcon](arkts-arkui-imagegeneration-generatorresultpageicon-i-sys.md) | ImageGeneratorDialog生成结果页面中的自定义图标对象。 |
| [ImageGenerationModel](arkts-arkui-imagegeneration-imagegenerationmodel-i-sys.md) | AI图像模型抽象接口。 |
| [ImageItem](arkts-arkui-imagegeneration-imageitem-i-sys.md) | AI生成图像的图像信息。 |
| [ImageStyle](arkts-arkui-imagegeneration-imagestyle-i-sys.md) | AI图像生成模型支持的风格类型，如涂鸦、水彩画。 |
| [LiveViewInfo](arkts-arkui-imagegeneration-liveviewinfo-i-sys.md) | AI图像生成中实况窗的选项。 |
| [TaskStatistic](arkts-arkui-imagegeneration-taskstatistic-i-sys.md) | 与AI图像生成任务相关的统计数据。 |
| [TextGenerationModel](arkts-arkui-imagegeneration-textgenerationmodel-i-sys.md) | AI文本模型抽象接口。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CustomImportCallback](arkts-arkui-imagegeneration-customimportcallback-t-sys.md) | 自定义导入操作的异步回调类型。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PartialResultType](arkts-arkui-imagegeneration-partialresulttype-e-sys.md) | 提供流输出结果类型的定义。 |
<!--DelEnd-->
