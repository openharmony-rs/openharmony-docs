# CylinderGeometry

圆柱体几何类型，继承自GeometryDefinition。

> **说明：**
> 
> 开发者需保证参数radius，height，segmentCount设置正确，否则无法创建圆柱体并可能引发不可预期的行为。
@extends GeometryDefinition

**继承/实现关系：** CylinderGeometry extends [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md)

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D

## height

```TypeScript
set height(value: number)
```

圆柱体的高度，单位为世界坐标系下的场景单位（比如cm、m、km等），取值范围大于0。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D

## radius

```TypeScript
set radius(value: number)
```

圆柱体的底面半径，单位为世界坐标系下的场景单位（比如cm、m、km等），取值范围大于0。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D

## segmentCount

```TypeScript
set segmentCount(value: number)
```

圆柱体圆周方向的分段面数量，取值范围是大于等于3的正整数，若设为浮点数将自动向下取整。 该数值直接影响圆柱体侧面的光滑度：数值越大，侧面包含的面片数量越多，视觉上越接近光滑曲面；数值越小，侧面会呈现明显的多边形轮廓。 注意数值过大会延长几何创建耗时，还可能导致线程阻塞。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D
