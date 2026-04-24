# BoidsSim (系统接口)
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @zzhao0-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->

本模块提供3D图形中群组模拟动画的类型及操作方法。

> **说明：** 
> - 本模块首批接口从API version 26开始支持，后续版本的新增接口，采用上角标标记接口的起始版本。

## 导入模块

```ts
import { BoidsSimPlugin, BoidsSimWorld, BoidsSimParameters,
  BoidsSimGravityParameters, BoidsSimRepulsionParameters } from '@kit.ArkGraphics3D';
```

## BoidsSimParameters

群组模拟参数，用于配置每个个体的行为属性。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| initialVelocity | [Vec3](js-apis-inner-scene-types.md#vec3) | 否 | 是 | 每个个体的初始速度向量。默认值为(0, 0, 0)。 |
| initialPosition | [Vec3](js-apis-inner-scene-types.md#vec3) | 否 | 是 | 每个个体的初始位置。未设置时保留当前实体位置。默认值为(NaN, NaN, NaN)。 |
| initialRotation | [Quaternion](js-apis-inner-scene-types.md#quaternion) | 否 | 是 | 每个个体的初始旋转。未设置时保留当前实体旋转。默认值为(NaN, NaN, NaN, NaN)。 |
| boundaryMinPos | [Vec3](js-apis-inner-scene-types.md#vec3) | 否 | 是 | 约束个体运动范围的轴对齐包围盒最小角点。当boundaryMinPos的任一分量大于或等于boundaryMaxPos对应分量时，该个体视为无边界约束。默认值为(0, 0, 0)。 |
| boundaryMaxPos | [Vec3](js-apis-inner-scene-types.md#vec3) | 否 | 是 | 约束个体运动范围的轴对齐包围盒最大角点。默认值为(0, 0, 0)。 |
| maxVelocityMag | number | 否 | 是 | 个体每模拟帧可达到的最大速度。取值 >= 0。 |
| maxAccelerationMag | number | 否 | 是 | 个体每模拟帧可达到的最大加速度。取值 >= 0。 |
| maxTurnRate | [Vec3](js-apis-inner-scene-types.md#vec3) | 否 | 是 | 每模拟帧每轴最大转向速率（弧度）。每个分量取值 >= 0。 |
| separationWeight | number | 否 | 是 | 分离规则权重。个体在separationDistance范围内受邻近个体排斥的强度。取值 >= 0。 |
| separationDistance | number | 否 | 是 | 分离规则的感知半径。仅严格在该距离内的邻近个体对分离力有贡献（边界处力为零）。取值 >= 0。 |
| alignmentWeight | number | 否 | 是 | 对齐规则权重。个体在alignmentDistance范围内朝向邻近个体平均航向的强度。取值 >= 0。 |
| alignmentDistance | number | 否 | 是 | 对齐规则的感知半径。在该距离内（含边界）的邻近个体对对齐力有贡献。取值 >= 0。 |
| cohesionWeight | number | 否 | 是 | 凝聚规则权重。个体在cohesionDistance范围内朝向邻近个体平均位置吸引的强度。取值 >= 0。 |
| cohesionDistance | number | 否 | 是 | 凝聚规则的感知半径。在该距离内（含边界）的邻近个体对凝聚力有贡献。取值 >= 0。 |
| boundaryWeight | number | 否 | 是 | 边界约束力权重。个体在boundaryDistance范围内被边界墙推回的强度。取值 >= 0。 |
| boundaryDistance | number | 否 | 是 | 边界约束力生效距离。个体距边界墙面在该距离内时受到排斥力。取值 >= 0。 |
| gravityWeight | number | 否 | 是 | 引力场对该个体的吸引强度。取值 >= 0。 |
| repulsionWeight | number | 否 | 是 | 斥力场对该个体的排斥强度。取值 >= 0。 |

## BoidsSimGravityParameters

引力场参数，用于配置场景中的引力场。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| radius | number | 否 | 是 | 引力场的作用半径。仅严格在该距离内的个体受到吸引（边界处力为零）。取值 >= 0。 |
| accelerationMag | number | 否 | 是 | 施加于个体、方向指向引力场实体的吸引加速度大小。取值 >= 0。 |

## BoidsSimRepulsionParameters

斥力场参数，用于配置场景中的斥力场。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| radius | number | 否 | 是 | 斥力场的作用半径。仅严格在该距离内的个体受到排斥（边界处力为零）。取值 >= 0。 |
| accelerationMag | number | 否 | 是 | 施加于个体、方向远离斥力场实体的排斥加速度大小。取值 >= 0。 |

## BoidsSimWorld

群组模拟世界对象，用于管理群组模拟的生命周期及组件。

### 属性

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| isPlaying | boolean | 是 | 否 | 当前模拟是否正在播放。 |

### play

play(): void

开始或恢复群组模拟。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

### pause

pause(): void

暂停群组模拟。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

### stop

stop(): void

停止群组模拟并重置状态。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

### addBoidsSimComponent

addBoidsSimComponent(node: [Node](js-apis-inner-scene-nodes.md#node), param: [BoidsSimParameters](#boidssimparameters)): void

在指定结点上添加群组行为组件。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |
| param | [BoidsSimParameters](#boidssimparameters) | 是 | 群组行为参数。 |

### setBoidsSimComponent

setBoidsSimComponent(node: [Node](js-apis-inner-scene-nodes.md#node), param: [BoidsSimParameters](#boidssimparameters)): void

更新指定结点上的群组行为组件。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |
| param | [BoidsSimParameters](#boidssimparameters) | 是 | 群组行为参数。 |

### addBoidsSimGravityComponent

addBoidsSimGravityComponent(node: [Node](js-apis-inner-scene-nodes.md#node), param: [BoidsSimGravityParameters](#boidssimgravityparameters)): void

在指定结点上添加引力场组件。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |
| param | [BoidsSimGravityParameters](#boidssimgravityparameters) | 是 | 引力场参数。 |

### setBoidsSimGravityComponent

setBoidsSimGravityComponent(node: [Node](js-apis-inner-scene-nodes.md#node), param: [BoidsSimGravityParameters](#boidssimgravityparameters)): void

更新指定结点上的引力场组件。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |
| param | [BoidsSimGravityParameters](#boidssimgravityparameters) | 是 | 引力场参数。 |

### addBoidsSimRepulsionComponent

addBoidsSimRepulsionComponent(node: [Node](js-apis-inner-scene-nodes.md#node), param: [BoidsSimRepulsionParameters](#boidssimrepulsionparameters)): void

在指定结点上添加斥力场组件。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |
| param | [BoidsSimRepulsionParameters](#boidssimrepulsionparameters) | 是 | 斥力场参数。 |

### setBoidsSimRepulsionComponent

setBoidsSimRepulsionComponent(node: [Node](js-apis-inner-scene-nodes.md#node), param: [BoidsSimRepulsionParameters](#boidssimrepulsionparameters)): void

更新指定结点上的斥力场组件。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |
| param | [BoidsSimRepulsionParameters](#boidssimrepulsionparameters) | 是 | 斥力场参数。 |

### getBoidsSimComponent

getBoidsSimComponent(node: [Node](js-apis-inner-scene-nodes.md#node)): [BoidsSimParameters](#boidssimparameters) \| null

获取指定结点上的群组行为参数。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |

**返回值：**
| 类型 | 说明 |
| ---- | ---- |
| [BoidsSimParameters](#boidssimparameters) \| null | 返回群组行为参数，若结点未挂载该组件则返回null。 |

### getBoidsSimGravityComponent

getBoidsSimGravityComponent(node: [Node](js-apis-inner-scene-nodes.md#node)): [BoidsSimGravityParameters](#boidssimgravityparameters) \| null

获取指定结点上的引力场参数。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |

**返回值：**
| 类型 | 说明 |
| ---- | ---- |
| [BoidsSimGravityParameters](#boidssimgravityparameters) \| null | 返回引力场参数，若结点未挂载该组件则返回null。 |

### getBoidsSimRepulsionComponent

getBoidsSimRepulsionComponent(node: [Node](js-apis-inner-scene-nodes.md#node)): [BoidsSimRepulsionParameters](#boidssimrepulsionparameters) \| null

获取指定结点上的斥力场参数。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |

**返回值：**
| 类型 | 说明 |
| ---- | ---- |
| [BoidsSimRepulsionParameters](#boidssimrepulsionparameters) \| null | 返回斥力场参数，若结点未挂载该组件则返回null。 |

### removeBoidsSimComponent

removeBoidsSimComponent(node: [Node](js-apis-inner-scene-nodes.md#node)): void

移除指定结点上的群组行为组件。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |

### removeBoidsSimGravityComponent

removeBoidsSimGravityComponent(node: [Node](js-apis-inner-scene-nodes.md#node)): void

移除指定结点上的引力场组件。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |

### removeBoidsSimRepulsionComponent

removeBoidsSimRepulsionComponent(node: [Node](js-apis-inner-scene-nodes.md#node)): void

移除指定结点上的斥力场组件。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| node | [Node](js-apis-inner-scene-nodes.md#node) | 是 | 目标场景结点。 |

## BoidsSimPlugin

群组模拟插件，提供静态方法用于获取群组模拟世界。

### getDefaultBoidsSimWorld

static getDefaultBoidsSimWorld(scene: [Scene](js-apis-inner-scene.md)): [BoidsSimWorld](#boidssimworld) \| null

获取与指定场景关联的群组模拟世界实例。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**起始版本：** 26.0.0

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| scene | [Scene](js-apis-inner-scene.md) | 是 | 目标场景对象。 |

**返回值：**
| 类型 | 说明 |
| ---- | ---- |
| [BoidsSimWorld](#boidssimworld) \| null | 返回群组模拟世界实例，若不存在则返回null。 |

**示例：**
```ts
import { BoidsSimPlugin, BoidsSimWorld, BoidsSimParameters, Scene, Node } from '@kit.ArkGraphics3D';

async function boidsSimExample(): Promise<void> {
  const boidsPluginId = "a1b2c3d4-e5f6-4a5b-8c9d-0e1f2a3b4c5d";
  const boidsPluginLoaded = await Scene.getDefaultRenderContext()?.loadPlugin(boidsPluginId);
  if (!boidsPluginLoaded) {
    console.error('Failed to load BoidsSimPlugin');
    return;
  }

  let scene: Scene | null = await Scene.load($rawfile("***.glb"));
  if (!scene) {
    console.error('Scene load failed');
    return;
  }

  let world: BoidsSimWorld | null = BoidsSimPlugin.getDefaultBoidsSimWorld(scene);
  if (!world) {
    console.error('Failed to get BoidsSimWorld');
    return;
  }

  let param: BoidsSimParameters = {
    boundaryMinPos: { x: -10.0, y: -10.0, z: -10.0 },
    boundaryMaxPos: { x: 10.0, y: 10.0, z: 10.0 },
    separationWeight: 4.0,
    separationDistance: 0.5,
    alignmentWeight: 4.0,
    alignmentDistance: 3.0,
    cohesionWeight: 1.0,
    cohesionDistance: 3.0,
    boundaryWeight: 8.0,
  };

  let node1: Node | null = scene.root?.getNodeByPath("<node 1 path>");
  let node2: Node | null = scene.root?.getNodeByPath("<node 2 path>");
  if (node1) {
    world.addBoidsSimComponent(node1, param);
  }
  if (node2) {
    world.addBoidsSimComponent(node2, param);
  }

  world.play();
}
```
