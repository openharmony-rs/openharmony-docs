# MaterialType

Enumerates the material types in a scene. The material type defines how materials in a scene are rendered.

@enum { int }

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## SHADER

```TypeScript
SHADER = 1
```

Shader-defined.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## METALLIC_ROUGHNESS

```TypeScript
METALLIC_ROUGHNESS = 2
```

Metallic-Roughness model based on Physically Based Rendering (PBR), simulating realistic material lighting effects through metallicity and roughness parameters.

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## UNLIT

```TypeScript
UNLIT = 3
```

Material that is not affected by lighting.

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

## OCCLUSION

```TypeScript
OCCLUSION = 4
```

Occlusion material: occludes other objects in the scene but does not occlude the environment.

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D
