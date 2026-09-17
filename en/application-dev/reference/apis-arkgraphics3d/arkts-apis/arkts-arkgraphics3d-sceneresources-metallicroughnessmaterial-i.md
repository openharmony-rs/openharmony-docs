# MetallicRoughnessMaterial

Material resource for creating realistic appearances, using the Metallic-Roughness model based on PBR. It simulates the surface lighting and reflection effects of different materials like metal and plastic by adjusting metallicity and roughness parameters. It inherits from Material.

@extends Material @interface MetallicRoughnessMaterial

**Inheritance/Implementation:** MetallicRoughnessMaterial extends [Material](arkts-arkgraphics3d-sceneresources-material-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## ambientOcclusion

```TypeScript
ambientOcclusion: MaterialProperty
```

Ambient occlusion map, which is used to simulate the occlusion of ambient light in recesses or detailed parts of an object to enhance local shadows and improve detail realism.

**Type:** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## baseColor

```TypeScript
baseColor: MaterialProperty
```

Base color map, which is used to represent the material's color in the absence of lighting.

**Type:** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## clearCoat

```TypeScript
clearCoat: MaterialProperty
```

Clear coat, similar to car paint, carbon fiber, or a wet surface, which requires an additional transparent layer with reflective properties.

**Type:** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## clearCoatNormal

```TypeScript
clearCoatNormal: MaterialProperty
```

Normal map of the clear coat.

**Type:** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## clearCoatRoughness

```TypeScript
clearCoatRoughness: MaterialProperty
```

Roughness of the clear coat.

**Type:** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## emissive

```TypeScript
emissive: MaterialProperty
```

Emissive color, which is the color of the material as a light source.

**Type:** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## material

```TypeScript
material: MaterialProperty
```

Metal material parameters. Roughness: strength of reflection caused by the fine surface structure details of the material. Metallic: metallic properties of the material. Reflectance: reflectivity of the material.

**Type:** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## normal

```TypeScript
normal: MaterialProperty
```

Normal map, which is used to represent the surface structure details of an object to enhance lighting realism without altering the geometric structure.

**Type:** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## sheen

```TypeScript
sheen: MaterialProperty
```

Gentle, widespread shine of microfiber materials, ideal for representing fabrics and textiles.

**Type:** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## specular

```TypeScript
specular: MaterialProperty
```

Specular reflection of non-metallic materials, showing the intensity of traditional mirror-like reflections.

**Type:** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D
