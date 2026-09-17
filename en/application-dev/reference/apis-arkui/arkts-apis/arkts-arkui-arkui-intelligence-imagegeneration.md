# @ohos.arkui.intelligence.imageGeneration

Module for AI-generated images using UI Component.

@namespace imageGeneration

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [closeGeneratorDialog](arkts-arkui-imagegeneration-closegeneratordialog-f-sys.md) | Close the AI image generation task popup. |
| [closeGeneratorNodeGraph](arkts-arkui-imagegeneration-closegeneratornodegraph-f-sys.md) | Close the AI node graph Sheet. |
| [hasRecoverCacheInGeneratorDialog](arkts-arkui-imagegeneration-hasrecovercacheingeneratordialog-f-sys.md) | Check whether cache files that can be restored exist in GeneratorDialog. The persistent cache file is used to store configuration parameters for AI image generation. |
| [hideGeneratorDialog](arkts-arkui-imagegeneration-hidegeneratordialog-f-sys.md) | Hide the AI image generation task popup. |
| [hideGeneratorNodeGraph](arkts-arkui-imagegeneration-hidegeneratornodegraph-f-sys.md) | Hide the AI node graph Sheet. |
| [openGeneratorNodeGraph](arkts-arkui-imagegeneration-opengeneratornodegraph-f-sys.md) | Open the AI node graph Sheet. |
| [restoreGeneratorDialog](arkts-arkui-imagegeneration-restoregeneratordialog-f-sys.md) | Restore the AI image generation task popup. |
| [restoreGeneratorNodeGraph](arkts-arkui-imagegeneration-restoregeneratornodegraph-f-sys.md) | Restore the AI node graph Sheet. |
| [showGeneratorDialog](arkts-arkui-imagegeneration-showgeneratordialog-f-sys.md) | Open the AI image generation task popup and perform AI image generation operations. |
| [startSmartCanvasService](arkts-arkui-imagegeneration-startsmartcanvasservice-f-sys.md) | Start the smart canvas service. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CustomImportIcon](arkts-arkui-imagegeneration-customimporticon-i-sys.md) | Customize the import icon, which is used to add images and text from the application side. |
| [CustomImportResult](arkts-arkui-imagegeneration-customimportresult-i-sys.md) | The result of import operation for custom import icon. |
| [GenerateImageTaskParams](arkts-arkui-imagegeneration-generateimagetaskparams-i-sys.md) | Configuration parameter options for AI-generated image tasks. |
| [GenerateImageTaskPartialResult](arkts-arkui-imagegeneration-generateimagetaskpartialresult-i-sys.md) | Configuration stream result for AI-generated image tasks. |
| [GenerateImageTaskResult](arkts-arkui-imagegeneration-generateimagetaskresult-i-sys.md) | Configuration result for AI-generated image tasks. |
| [GenerateTextTaskPartialResult](arkts-arkui-imagegeneration-generatetexttaskpartialresult-i-sys.md) | Configuration stream result for AI-generated text tasks. |
| [GenerateTextTaskResult](arkts-arkui-imagegeneration-generatetexttaskresult-i-sys.md) | Configuration result for AI-generated text tasks. |
| [GeneratorDialogOptions](arkts-arkui-imagegeneration-generatordialogoptions-i-sys.md) | Parameters used to open the ImageGeneratorDialog. |
| [GeneratorNodeGraphOptions](arkts-arkui-imagegeneration-generatornodegraphoptions-i-sys.md) | Parameters used to open the NodeGraphComponent. |
| [GeneratorResult](arkts-arkui-imagegeneration-generatorresult-i-sys.md) | The result of AI-generated images |
| [GeneratorResultPageIcon](arkts-arkui-imagegeneration-generatorresultpageicon-i-sys.md) | Custom icon object in the generation result page of ImageGeneratorDialog. |
| [ImageGenerationModel](arkts-arkui-imagegeneration-imagegenerationmodel-i-sys.md) | AI Image Model Abstract Interface. |
| [ImageItem](arkts-arkui-imagegeneration-imageitem-i-sys.md) | Image information for AI-generated images. |
| [ImageStyle](arkts-arkui-imagegeneration-imagestyle-i-sys.md) | Style types supported by AI image generation models, like Graffiti, Watercolor. |
| [LiveViewInfo](arkts-arkui-imagegeneration-liveviewinfo-i-sys.md) | Information for LiveView in AI image generation. |
| [TaskStatistic](arkts-arkui-imagegeneration-taskstatistic-i-sys.md) | Statistics Related to AI Image Generation Tasks. |
| [TextGenerationModel](arkts-arkui-imagegeneration-textgenerationmodel-i-sys.md) | AI Text Model Abstract Interface. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [PartialResultType](arkts-arkui-imagegeneration-partialresulttype-e-sys.md) | Provides stream output result type definition. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [CustomImportCallback](arkts-arkui-imagegeneration-customimportcallback-t-sys.md) | Async callback type for custom import operation. |
<!--DelEnd-->
