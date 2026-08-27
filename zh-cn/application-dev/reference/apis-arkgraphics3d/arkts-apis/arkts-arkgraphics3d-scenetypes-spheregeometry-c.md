# SphereGeometry

球体几何类型，继承自GeometryDefinition。@extends GeometryDefinition

**继承/实现关系：** SphereGeometry extends [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D

## radius

```TypeScript
set radius(value: number)
```

球体半径，单位为世界坐标系下的场景单位（比如cm、m、km等），取值范围大于0。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D

## segmentCount

```TypeScript
set segmentCount(value: number)
```

在球体上以经纬度分割的段数，取值范围是大于等于3的正整数。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D
