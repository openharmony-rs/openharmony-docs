# GeneratorResultPageIcon (System API)

Custom icon object in the generation result page of ImageGeneratorDialog.

@interface GeneratorResultPageIcon

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## callback

```TypeScript
callback: Callback<GeneratorResult>
```

Icon click event callback.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GeneratorResult](arkts-arkui-imagegeneration-generatorresult-i-sys.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## image

```TypeScript
image: image.PixelMap | string | Resource
```

Icon image information.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## text

```TypeScript
text: ResourceStr
```

Icon text description.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
