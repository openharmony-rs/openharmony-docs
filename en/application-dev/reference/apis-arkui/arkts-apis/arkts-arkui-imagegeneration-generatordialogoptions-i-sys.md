# GeneratorDialogOptions (System API)

Parameters used to open the ImageGeneratorDialog.

@interface GeneratorDialogOptions

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## content

```TypeScript
content?: ResourceStr
```

Initial text information used for AI-generated image tasks.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## customIcons

```TypeScript
customIcons?: Array<GeneratorResultPageIcon>
```

Custom icons used on the AI generated image results page.

**Type:** Array&lt;[GeneratorResultPageIcon](arkts-arkui-imagegeneration-generatorresultpageicon-i-sys.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## customImportIcon

```TypeScript
customImportIcon?: CustomImportIcon
```

The following configuration parameters are used to customize the imported icon.

**Type:** [CustomImportIcon](arkts-arkui-imagegeneration-customimporticon-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## imageGenerationModel

```TypeScript
imageGenerationModel?: ImageGenerationModel
```

Model used for AI generate image tasks.

**Type:** [ImageGenerationModel](arkts-arkui-imagegeneration-imagegenerationmodel-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## images

```TypeScript
images?: Array<ImageItem>
```

Initial image parameters used for AI-generated image tasks.

**Type:** Array&lt;[ImageItem](arkts-arkui-imagegeneration-imageitem-i-sys.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## liveViewInfo

```TypeScript
liveViewInfo?: LiveViewInfo
```

Information for LiveView in AI image generation.

**Type:** [LiveViewInfo](arkts-arkui-imagegeneration-liveviewinfo-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## minimizeDuringGeneration

```TypeScript
minimizeDuringGeneration?: boolean
```

Indicates whether to enable minimize during image generation.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## onAreaDidChange

```TypeScript
onAreaDidChange?: Callback<common2D.Rect>
```

Callback triggered when the ImageGeneratorDialog changes in size or position.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[common2D.Rect](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-common2d-rect-i.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## recoverFromCache

```TypeScript
recoverFromCache?: boolean
```

Whether to recover from cache for AI image generation. The persistent cache file is used to store configuration parameters for AI image generation.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## textGenerationModel

```TypeScript
textGenerationModel?: TextGenerationModel
```

Text polishing model used in AI generate image tasks.

**Type:** [TextGenerationModel](arkts-arkui-imagegeneration-textgenerationmodel-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
