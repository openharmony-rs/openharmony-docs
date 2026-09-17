# UnlitShadowAlphaMaterial (System API)

This material inherits from Material and draws only the surface shadows. When the Blend property is enabled, the material can be blended with the background to simulate transparency.

@extends Material @interface UnlitShadowAlphaMaterial

**Inheritance/Implementation:** UnlitShadowAlphaMaterial extends [Material](arkts-arkgraphics3d-sceneresources-material-i.md)

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## baseColor

```TypeScript
baseColor: MaterialProperty
```

Color information of the shadow on the surface of a transparent material.

**Type:** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.
