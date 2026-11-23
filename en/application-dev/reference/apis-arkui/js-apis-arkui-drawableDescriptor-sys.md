# @ohos.arkui.drawableDescriptor (DrawableDescriptor) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-11-18T09:32:52.873Z pushedAt=2026-11-20T07:45:41.182Z nl=1 -->

The **DrawableDescriptor** module provides APIs for obtaining **pixelMap** objects, including the foreground, background, mask, and layered icons.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> You can preview how this component looks on a real device, but not in DevEco Studio Previewer.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.arkui.drawableDescriptor (DrawableDescriptor)](js-apis-arkui-drawableDescriptor.md).

## Modules to Import

```ts
import { DrawableDescriptor, LayeredDrawableDescriptor } from '@kit.ArkUI';
```

## DrawableDescriptor

### constructor

constructor()

Creates a **DrawableDescriptor** or **LayeredDrawableDescriptor** object. The [getDrawableDescriptor](../apis-localization-kit/js-apis-resource-manager.md#getdrawabledescriptor10) or [getDrawableDescriptorByName](../apis-localization-kit/js-apis-resource-manager.md#getdrawabledescriptorbyname10) API is required for object construction.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### setSVGResourceLimitLevel

setSVGResourceLimitLevel(limit: image.SVGResourceLimitLevel): void

Sets the resource limit level for SVG decoding. If this API is not called, the default value is image.[SVGResourceLimitLevel](../apis-image-kit/js-apis-image-sys.md#svgresourcelimitlevel).NONE.

**Since**: 26.0.1

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| --------- | ---------------- | ---- | ------------------------------------------ |
| limit | image.[SVGResourceLimitLevel](../apis-image-kit/js-apis-image-sys.md#svgresourcelimitlevel) | Yes | Resource limit level for SVG decoding. |
