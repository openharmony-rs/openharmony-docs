# MaterialType

```TypeScript
export enum MaterialType
```

Enumerates the material types in a scene. The material type defines how materials in a scene are rendered.

@enum { int }

**Since:** 12

<!--Device-unnamed-export enum MaterialType--><!--Device-unnamed-export enum MaterialType-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## SHADER

```TypeScript
SHADER = 1
```

Shader-defined.

**Since:** 12

<!--Device-MaterialType-SHADER = 1--><!--Device-MaterialType-SHADER = 1-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## METALLIC_ROUGHNESS

```TypeScript
METALLIC_ROUGHNESS = 2
```

Metallic-Roughness model based on Physically Based Rendering (PBR), simulating realistic material lighting effects through metallicity and roughness parameters.

**Since:** 20

<!--Device-MaterialType-METALLIC_ROUGHNESS = 2--><!--Device-MaterialType-METALLIC_ROUGHNESS = 2-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## UNLIT

```TypeScript
UNLIT = 3
```

Material that is not affected by lighting.

**Since:** 23

<!--Device-MaterialType-UNLIT = 3--><!--Device-MaterialType-UNLIT = 3-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## OCCLUSION

```TypeScript
OCCLUSION = 4
```

Occlusion material: occludes other objects in the scene but does not occlude the environment.

**Since:** 23

<!--Device-MaterialType-OCCLUSION = 4--><!--Device-MaterialType-OCCLUSION = 4-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D
