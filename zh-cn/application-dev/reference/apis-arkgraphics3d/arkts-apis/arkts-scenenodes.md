# SceneNodes

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [Camera](arkts-arkgraphics3d-scenenodes-camera-i.md) | 定义相机. |
| [Container](arkts-arkgraphics3d-scenenodes-container-i.md) | 定义场景对象的容器。容器提供了一种将场景对象分组到层次结构中的方法。 |
| [DirectionalLight](arkts-arkgraphics3d-scenenodes-directionallight-i.md) | 定义平行光. |
| [Geometry](arkts-arkgraphics3d-scenenodes-geometry-i.md) | 定义Geometry接口. |
| [LayerMask](arkts-arkgraphics3d-scenenodes-layermask-i.md) | 定义节点的图层掩码. |
| [Light](arkts-arkgraphics3d-scenenodes-light-i.md) | 定义Light接口. |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 定义Node接口. |
| [SpotLight](arkts-arkgraphics3d-scenenodes-spotlight-i.md) | 聚光灯类型，继承自[Light](arkts-arkgraphics3d-scenenodes-light-i.md#Light)。 聚光灯会朝某个方向发出锥形光，强度随着圆锥角度的衰减由innerAngle和outerAngle两个参数定义。 另外与点光源类似，强度也会随着距离光源位置的增加而衰减。 > > **注意：** > > 用户需要保证设置的innerAngle与outerAngle值是合理的。当outerAngle设置的值大于PI/2时，内部会强制其等于PI/2。 > 当outerAngle设置的值小于innerAngle时，内部会强制其等于innerAngle。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LightType](arkts-arkgraphics3d-scenenodes-lighttype-e.md) | 光源类型枚举. |
| [NodeType](arkts-arkgraphics3d-scenenodes-nodetype-e.md) | 节点类型枚举. |

