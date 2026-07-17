# SphereGeometry

定义球体.

**继承/实现关系：** SphereGeometry extends [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md)

**起始版本：** 18

<!--Device-unnamed-export declare class SphereGeometry extends GeometryDefinition--><!--Device-unnamed-export declare class SphereGeometry extends GeometryDefinition-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## radius

```TypeScript
set radius(value: number)
```

球体的半径, 单位为世界坐标系下的场景单位（例如cm、m、km等）.

**类型：** number

**起始版本：** 18

<!--Device-SphereGeometry-set radius(value: double)--><!--Device-SphereGeometry-set radius(value: double)-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## segmentCount

```TypeScript
set segmentCount(value: number)
```

将球体按经纬度分割成若干圈和段.

**类型：** number

**起始版本：** 18

<!--Device-SphereGeometry-set segmentCount(value: int)--><!--Device-SphereGeometry-set segmentCount(value: int)-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

