# CustomGeometry

定义自定义几何形状的顶点数组及其数据.

**继承/实现关系：** CustomGeometry extends [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md)

**起始版本：** 18

<!--Device-unnamed-export declare class CustomGeometry extends GeometryDefinition--><!--Device-unnamed-export declare class CustomGeometry extends GeometryDefinition-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## colors

```TypeScript
colors?: Color[]
```

顶点颜色. 如果colors不为null，则colors[N]对应vertices[N].

**类型：** Color[]

**起始版本：** 18

<!--Device-CustomGeometry-colors?: Color[]--><!--Device-CustomGeometry-colors?: Color[]-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## indices

```TypeScript
indices?: number[]
```

构成三角形的顶点索引. PrimitiveTopology应用于索引定义的序列.

给定vertices = [a, b, c, d]，创建相同的一对三角形的示例:topology = PrimitiveTopology.TRIANGLE_LIST indices = [0, 1, 2, 2, 1, 3]生成的三角形：abc、cbd

topology = PrimitiveTopology.TRIANGLE_STRIP indices = [0, 1, 2, 3]生成的三角形：abc、cbd (b和c在cbd中被反转，以匹配第一个三角形的面方向)

**类型：** number[]

**默认值：** indices: [0, 1 ,2,..., vertices.size() - 1]

**起始版本：** 18

<!--Device-CustomGeometry-indices?: int[]--><!--Device-CustomGeometry-indices?: int[]-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## normals

```TypeScript
normals?: Vec3[]
```

顶点法线。如果normals不为null，则normals[N]对应vertices[N]，且generateNormals参数会被忽略。

**类型：** Vec3[]

**起始版本：** 18

<!--Device-CustomGeometry-normals?: Vec3[]--><!--Device-CustomGeometry-normals?: Vec3[]-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## topology

```TypeScript
topology?: PrimitiveTopology
```

如何从索引顶点形成网格三角形.

**类型：** PrimitiveTopology

**默认值：** PrimitiveTopology.TRIANGLE_LIST 三角形列表拓扑

**起始版本：** 18

<!--Device-CustomGeometry-topology?: PrimitiveTopology--><!--Device-CustomGeometry-topology?: PrimitiveTopology-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## uvs

```TypeScript
uvs?: Vec2[]
```

顶点纹理映射UV坐标. 如果uvs不为null，则uvs[N]对应vertices[N]

**类型：** Vec2[]

**起始版本：** 18

<!--Device-CustomGeometry-uvs?: Vec2[]--><!--Device-CustomGeometry-uvs?: Vec2[]-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## vertices

```TypeScript
set vertices(value: Vec3[])
```

顶点数组.

**类型：** Vec3[]

**起始版本：** 18

<!--Device-CustomGeometry-set vertices(value: Vec3[])--><!--Device-CustomGeometry-set vertices(value: Vec3[])-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

