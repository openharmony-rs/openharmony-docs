# DrawableDescriptor

```TypeScript
export class DrawableDescriptor
```

Represents the base class providing overridable methods for [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) acquisition and image resource loading.

**Since:** 10

<!--Device-unnamed-export class DrawableDescriptor--><!--Device-unnamed-export class DrawableDescriptor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor()
```

Creates a new DrawableDescriptor.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-DrawableDescriptor-constructor()--><!--Device-DrawableDescriptor-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## setSVGResourceLimitLevel

```TypeScript
setSVGResourceLimitLevel(limit: image.SVGResourceLimitLevel): void
```

set svg resource limit level.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DrawableDescriptor-setSVGResourceLimitLevel(limit: image.SVGResourceLimitLevel): void--><!--Device-DrawableDescriptor-setSVGResourceLimitLevel(limit: image.SVGResourceLimitLevel): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| limit | [image.SVGResourceLimitLevel](../../apis-image-kit/arkts-apis/arkts-image-image-svgresourcelimitlevel-e-sys.md) | Yes | svg resource limit level. |
