# CustomGeometry

A custom geometry type that inherits from GeometryDefinition.

@extends GeometryDefinition

**Inheritance/Implementation:** CustomGeometry extends [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md)

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## colors

```TypeScript
colors?: Color[]
```

Array of colors for the vertices. The default value is undefined.

**Type:** [Color](arkts-arkgraphics3d-scenetypes-color-i.md)[]

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## indices

```TypeScript
indices?: number[]
```

Array of indices for the vertices, with values starting at 0. The default value is undefined.

**Type:** number[]

**Default:** undefined

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## normals

```TypeScript
normals?: Vec3[]
```

Array of normals corresponding to the vertices. The default value is undefined.

**Type:** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)[]

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## topology

```TypeScript
topology?: PrimitiveTopology
```

Parsing mode of triangle primitives. The default value is TRIANGLE_LIST.

**Type:** [PrimitiveTopology](arkts-arkgraphics3d-scenetypes-primitivetopology-e.md)

**Default:** PrimitiveTopology.TRIANGLE_LIST

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## uvs

```TypeScript
uvs?: Vec2[]
```

Array of UV coordinates for the vertices. The default value is undefined.

**Type:** [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md)[]

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## vertices

```TypeScript
get vertices(): Vec3[]
```

Array of vertices that make up the model.

**Type:** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)[]

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

```TypeScript
set vertices(value: Vec3[])
```

Array of vertices that make up the model.

**Type:** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)[]

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D
