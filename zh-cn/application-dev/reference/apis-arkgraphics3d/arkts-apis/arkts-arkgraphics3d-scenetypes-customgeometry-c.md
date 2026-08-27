# CustomGeometry

自定义几何类型，继承自GeometryDefinition。@extends GeometryDefinition

**继承/实现关系：** CustomGeometry extends [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D

## colors

```TypeScript
colors?: Color[]
```

顶点数组对应的颜色数组，默认值为undefined。

**类型：** [Color](arkts-arkgraphics3d-scenetypes-color-i.md)[]

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D

## indices

```TypeScript
indices?: number[]
```

顶点索引数组，数组中元素的取值范围大于等于0，默认值为undefined。

**类型：** number[]

**默认值：** undefined

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D

## normals

```TypeScript
normals?: Vec3[]
```

顶点数组对应的法向量数组，默认值为undefined。

**类型：** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)[]

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D

## topology

```TypeScript
topology?: PrimitiveTopology
```

三角形图元的解析方式，默认值为TRIANGLE_LIST。

**类型：** [PrimitiveTopology](arkts-arkgraphics3d-scenetypes-primitivetopology-e.md)

**默认值：** PrimitiveTopology.TRIANGLE_LIST

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D

## uvs

```TypeScript
uvs?: Vec2[]
```

顶点数组对应的UV坐标数组，默认值为undefined。

**类型：** [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md)[]

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D

## vertices

```TypeScript
set vertices(value: Vec3[])
```

模型的顶点数组。

**类型：** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)[]

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D
