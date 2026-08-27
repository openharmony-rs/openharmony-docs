# SceneTypes

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [CubeGeometry](arkts-arkgraphics3d-scenetypes-cubegeometry-c.md) | 立方体几何类型，继承自GeometryDefinition。@extends GeometryDefinition |
| [CustomGeometry](arkts-arkgraphics3d-scenetypes-customgeometry-c.md) | 自定义几何类型，继承自GeometryDefinition。@extends GeometryDefinition |
| [CylinderGeometry](arkts-arkgraphics3d-scenetypes-cylindergeometry-c.md) | 圆柱体几何类型，继承自GeometryDefinition。 |
| [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md) | 几何类型定义抽象类，用于解释特定几何类型的属性。 |
| [PlaneGeometry](arkts-arkgraphics3d-scenetypes-planegeometry-c.md) | 平面几何类型，继承自GeometryDefinition。@extends GeometryDefinition |
| [SphereGeometry](arkts-arkgraphics3d-scenetypes-spheregeometry-c.md) | 球体几何类型，继承自GeometryDefinition。@extends GeometryDefinition |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Aabb](arkts-arkgraphics3d-scenetypes-aabb-i.md) | 轴对齐边界盒，主要用于判断空间中的物体是否重叠。 |
| [Color](arkts-arkgraphics3d-scenetypes-color-i.md) | 用于表示RGBA格式的颜色，包含四个分量，依次为红色、绿色、蓝色和透明度。 |
| [Mat4x4](arkts-arkgraphics3d-scenetypes-mat4x4-i.md) | 4x4矩阵类型，可用于坐标变换。 |
| [Quaternion](arkts-arkgraphics3d-scenetypes-quaternion-i.md) | 用于表示3D空间中旋转的数学结构。与传统的欧拉角相比，四元数在数值稳定性和避免万向节锁方面具有优势。 |
| [Rect](arkts-arkgraphics3d-scenetypes-rect-i.md) | 用于表示平面中的矩形。 |
| [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md) | 二维向量，通常用于表示2D空间中的点或方向，由x和y两个分量组成。 |
| [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md) | 三维向量，通常用于表示3D空间中的点、方向或向量变换，由x、y和z三个分量组成。 |
| [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md) | 四维向量，通常用于表示4D空间中的点、方向或向量变换，由x、y、z和w四个分量组成。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GeometryType](arkts-arkgraphics3d-scenetypes-geometrytype-e.md) | 几何类型枚举，用于指定不同的几何类型。@enum { number } |
| [PrimitiveTopology](arkts-arkgraphics3d-scenetypes-primitivetopology-e.md) | 图元拓扑枚举，在顶点处理过程中，指定顶点的不同处理方式。@enum { number } |
| [RenderingPipelineType](arkts-arkgraphics3d-scenetypes-renderingpipelinetype-e.md) | 渲染管线类型枚举。@enum { number } |
| [ShadowAlgorithmType](arkts-arkgraphics3d-scenetypes-shadowalgorithmtype-e.md) | 阴影算法的枚举类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Position3](arkts-arkgraphics3d-position3-t.md) | 用于表示3维空间中物体的位置。 类型为三维向量，单位为世界坐标系下的场景单位（比如cm、m、km等），可取任意值。 |
| [Rotation3](arkts-arkgraphics3d-rotation3-t.md) | 用于表示3维空间中物体的旋转。 类型为三维向量，单位为弧度（rad），可取任意值。 |
| [Scale3](arkts-arkgraphics3d-scale3-t.md) | 用于表示3维空间中物体的缩放。 类型为三维向量，可取任意值。 |
