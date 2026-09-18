# SphereGeometry

A sphere geometry type that inherits from GeometryDefinition.

@extends GeometryDefinition

**Inheritance/Implementation:** SphereGeometry extends [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md)

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## radius

```TypeScript
get radius(): number
```

Radius of the sphere, measured in the world coordinate system's units (for example, cm, m, or km). The value must be greater than 0.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

```TypeScript
set radius(value: number)
```

Radius of the sphere, measured in the world coordinate system's units (for example, cm, m, or km). The value must be greater than 0.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## segmentCount

```TypeScript
get segmentCount(): number
```

Number of segments divided by longitude and latitude on the sphere. The value range is a positive integer greater than or equal to 3.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

```TypeScript
set segmentCount(value: number)
```

Number of segments divided by longitude and latitude on the sphere. The value range is a positive integer greater than or equal to 3.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D
