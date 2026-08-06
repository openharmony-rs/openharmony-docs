# CylinderGeometry

定义圆柱体.

**继承/实现关系：** CylinderGeometry extends [GeometryDefinition](scenetypes-geometrydefinition-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class CylinderGeometry extends GeometryDefinition--><!--Device-unnamed-export declare class CylinderGeometry extends GeometryDefinition-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## height

```TypeScript
set height(value: double)
```

圆柱体的高度, 单位为世界坐标系下的场景单位（例如cm、m、km等）.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-CylinderGeometry-set height(value: double)--><!--Device-CylinderGeometry-set height(value: double)-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## radius

```TypeScript
set radius(value: double)
```

圆柱体底面的半径, 单位为世界坐标系下的场景单位（例如cm、m、km等）.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-CylinderGeometry-set radius(value: double)--><!--Device-CylinderGeometry-set radius(value: double)-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## segmentCount

```TypeScript
set segmentCount(value: int)
```

使用正多边形近似圆柱体的圆形底面, 其中segmentCount是正多边形的边数.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-CylinderGeometry-set segmentCount(value: int)--><!--Device-CylinderGeometry-set segmentCount(value: int)-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

