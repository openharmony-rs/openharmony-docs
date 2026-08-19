# SceneNodes

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [Camera](arkts-arkgraphics3d-scenenodes-camera-i.md) | 相机类型，Camera继承自Node。 |
| [Container](arkts-arkgraphics3d-scenenodes-container-i.md) | 定义场景对象的容器。容器提供了一种将场景对象分组到层次结构中的方法。 |
| [DirectionalLight](arkts-arkgraphics3d-scenenodes-directionallight-i.md) | 平行光类型，继承自Light。 |
| [Geometry](arkts-arkgraphics3d-scenenodes-geometry-i.md) | 几何节点类型，用于承载可渲染的网格数据，并支持可选的形变功能，继承自Node。 |
| [LayerMask](arkts-arkgraphics3d-scenenodes-layermask-i.md) | 用于定义节点的图层掩码。 |
| [Light](arkts-arkgraphics3d-scenenodes-light-i.md) | 光源，继承自Node。 |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 3D场景由树状层次结构的节点组成，其中每个节点都实现了Node接口。继承自SceneResource。 |
| [SpotLight](arkts-arkgraphics3d-scenenodes-spotlight-i.md) | 聚光灯类型，继承自Light。 聚光灯会朝某个方向发出锥形光，强度随着圆锥角度的衰减由innerAngle和outerAngle两个参数定义。另外与点光源类似，强度也会随着距离光源位置的增加而衰减。 > **注意：** > > 用户需要保证设置的innerAngle与outerAngle值是合理的。 > 当outerAngle设置的值大于PI/2时，内部会强制其等于PI/2。 > 当outerAngle设置的值小于innerAngle时，内部会强制其等于innerAngle。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LightType](arkts-arkgraphics3d-scenenodes-lighttype-e.md) | 光源类型枚举。 |
| [NodeType](arkts-arkgraphics3d-scenenodes-nodetype-e.md) | 节点类型枚举。 |

