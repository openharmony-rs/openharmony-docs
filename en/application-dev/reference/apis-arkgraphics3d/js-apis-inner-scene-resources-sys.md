# SceneResource (System API)
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @zzhao0-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->

The module provides basic resource types in 3D graphics.

> **NOTE**
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [SceneResources](js-apis-inner-scene-resources.md).

## Modules to Import
```ts
import { MaterialType, UnlitShadowAlphaMaterial } from '@kit.ArkGraphics3D';
```

## MaterialType
Enumerates the material types in a scene. The material type defines how materials in a scene are rendered.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Value| Description|
| ---- | ---- | ---- |
| UNLIT_SHADOW_ALPHA<sup>23+</sup> | 100 | Draws only shadows. When the [Blend](js-apis-inner-scene-resources.md#blend20) property of the material is enabled, the material is blended with the background to simulate a transparent material effect.<br>**System API**: This is a system API.<br>**Model restriction**: This API can be used only in the stage model.|

## UnlitShadowAlphaMaterial<sup>23+</sup>

This material inherits from [Material](js-apis-inner-scene-resources.md#material) and draws only the surface shadows. When the [Blend](js-apis-inner-scene-resources.md#blend20) property is enabled, the material can be blended with the background to simulate transparency.

**System capability**: SystemCapability.ArkUi.Graphics3D

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| baseColor | [MaterialProperty](js-apis-inner-scene-resources.md#materialproperty20) | No| No| Color information of the shadow on the surface of a transparent material.|
