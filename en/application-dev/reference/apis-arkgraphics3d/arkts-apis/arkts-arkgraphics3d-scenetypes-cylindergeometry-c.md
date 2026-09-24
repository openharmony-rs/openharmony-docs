# CylinderGeometry

```TypeScript
export declare class CylinderGeometry extends GeometryDefinition
```

A cylinder geometry type that inherits from GeometryDefinition.

> **NOTE:** 
> 
> You must ensure that all three parameters are set correctly.
> Invalid values may prevent cylinder creation or cause undefined behavior.

@extends GeometryDefinition

**Inheritance/Implementation:** CylinderGeometry extends [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md)

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

## height

```TypeScript
get height(): number
```

Height of the cylinder, in scene units of the world coordinate system (such as cm, m, km, etc.). The value range is greater than 0.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

```TypeScript
set height(value: number)
```

Height of the cylinder, in scene units of the world coordinate system (such as cm, m, km, etc.). The value range is greater than 0.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

## radius

```TypeScript
get radius(): number
```

Bottom radius of the cylinder, in scene units of the world coordinate system (such as cm, m, km, etc.). The value range is greater than 0.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

```TypeScript
set radius(value: number)
```

Bottom radius of the cylinder, in scene units of the world coordinate system (such as cm, m, km, etc.). The value range is greater than 0.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

## segmentCount

```TypeScript
get segmentCount(): number
```

Use regular polygons to approximate the circular base of the cylinder, where segmentCount is the number of sides of the regular polygon used.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

```TypeScript
set segmentCount(value: number)
```

Use regular polygons to approximate the circular base of the cylinder, where segmentCount is the number of sides of the regular polygon used.

**Type:** number

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D
