# BoidsSimWorld（系统接口）

群组模拟世界对象，用于管理群组模拟的生命周期及组件。

> **说明：**
> 使用以下接口前，需先通过[BoidsSimPlugin.getDefaultBoidsSimWorld](arkts-arkgraphics3d-sceneboidssim-boidssimplugin-c-sys.md#getdefaultboidssimworld)获取群组模拟世界实例。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## addBoidsSimComponent

```TypeScript
addBoidsSimComponent(node: Node, param: BoidsSimParameters): void
```

在指定节点上添加群组行为组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |
| param | [BoidsSimParameters](arkts-arkgraphics3d-sceneboidssim-boidssimparameters-i-sys.md) | 是 | 群组行为参数。 |

**示例**

```TypeScript
import { BoidsSimParameters, BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function manageBoidsSimComponent(world: BoidsSimWorld, node: Node): void {
  // 添加群组行为组件
  let boidsParams: BoidsSimParameters = {
    boundaryMinPos: { x: -10.0, y: -10.0, z: -10.0 },
    boundaryMaxPos: { x: 10.0, y: 10.0, z: 10.0 },
    separationWeight: 4.0,
    separationDistance: 0.5,
  };
  world.addBoidsSimComponent(node, boidsParams);

  // 更新群组行为组件
  world.setBoidsSimComponent(node, boidsParams);

  // 获取群组行为参数
  let params: BoidsSimParameters | null = world.getBoidsSimComponent(node);

  // 移除群组行为组件
  world.removeBoidsSimComponent(node);
}
```

## addBoidsSimGravityComponent

```TypeScript
addBoidsSimGravityComponent(node: Node, param: BoidsSimGravityParameters): void
```

在指定节点上添加引力场组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |
| param | [BoidsSimGravityParameters](arkts-arkgraphics3d-sceneboidssim-boidssimgravityparameters-i-sys.md) | 是 | 引力场参数。 |

**示例**

```TypeScript
import { BoidsSimGravityParameters, BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function manageBoidsSimGravityComponent(world: BoidsSimWorld, fieldNode: Node): void {
  // 添加引力场组件
  let gravityParams: BoidsSimGravityParameters = { accelerationMag: 4.0, radius: 10.0 };
  world.addBoidsSimGravityComponent(fieldNode, gravityParams);

  // 更新引力场组件
  world.setBoidsSimGravityComponent(fieldNode, gravityParams);

  // 获取引力场参数
  let grav: BoidsSimGravityParameters | null = world.getBoidsSimGravityComponent(fieldNode);

  // 移除引力场组件
  world.removeBoidsSimGravityComponent(fieldNode);
}
```

## addBoidsSimRepulsionComponent

```TypeScript
addBoidsSimRepulsionComponent(node: Node, param: BoidsSimRepulsionParameters): void
```

在指定节点上添加斥力场组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |
| param | [BoidsSimRepulsionParameters](arkts-arkgraphics3d-sceneboidssim-boidssimrepulsionparameters-i-sys.md) | 是 | 斥力场参数。 |

**示例**

```TypeScript
import { BoidsSimRepulsionParameters, BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function manageBoidsSimRepulsionComponent(world: BoidsSimWorld, fieldNode: Node): void {
  // 添加斥力场组件
  let repulsionParams: BoidsSimRepulsionParameters = { accelerationMag: 4.0, radius: 10.0 };
  world.addBoidsSimRepulsionComponent(fieldNode, repulsionParams);

  // 更新斥力场组件
  world.setBoidsSimRepulsionComponent(fieldNode, repulsionParams);

  // 获取斥力场参数
  let repl: BoidsSimRepulsionParameters | null = world.getBoidsSimRepulsionComponent(fieldNode);

  // 移除斥力场组件
  world.removeBoidsSimRepulsionComponent(fieldNode);
}
```

## getBoidsSimComponent

```TypeScript
getBoidsSimComponent(node: Node): BoidsSimParameters | null
```

获取指定节点上的群组行为参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BoidsSimParameters](arkts-arkgraphics3d-sceneboidssim-boidssimparameters-i-sys.md) \| null | 返回群组行为参数，若节点未挂载该组件则返回null。 |

**示例**

```TypeScript
import { BoidsSimParameters, BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function queryBoidsSimComponent(world: BoidsSimWorld, node: Node): void {
  let params: BoidsSimParameters | null = world.getBoidsSimComponent(node);
  if (params) {
    let maxVel: number = params.maxVelocityMag;
  }
}
```

## getBoidsSimGravityComponent

```TypeScript
getBoidsSimGravityComponent(node: Node): BoidsSimGravityParameters | null
```

获取指定节点上的引力场参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BoidsSimGravityParameters](arkts-arkgraphics3d-sceneboidssim-boidssimgravityparameters-i-sys.md) \| null | 返回引力场参数，若节点未挂载该组件则返回null。 |

**示例**

```TypeScript
import { BoidsSimGravityParameters, BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function queryBoidsSimGravityComponent(world: BoidsSimWorld, node: Node): void {
  let params: BoidsSimGravityParameters | null = world.getBoidsSimGravityComponent(node);
  if (params) {
    let accel: number = params.accelerationMag;
  }
}
```

## getBoidsSimRepulsionComponent

```TypeScript
getBoidsSimRepulsionComponent(node: Node): BoidsSimRepulsionParameters | null
```

获取指定节点上的斥力场参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BoidsSimRepulsionParameters](arkts-arkgraphics3d-sceneboidssim-boidssimrepulsionparameters-i-sys.md) \| null | 返回斥力场参数，若节点未挂载该组件则返回null。 |

**示例**

```TypeScript
import { BoidsSimRepulsionParameters, BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function queryBoidsSimRepulsionComponent(world: BoidsSimWorld, node: Node): void {
  let params: BoidsSimRepulsionParameters | null = world.getBoidsSimRepulsionComponent(node);
  if (params) {
    let accel: number = params.accelerationMag;
  }
}
```

## pause

```TypeScript
pause(): void
```

暂停群组模拟。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { BoidsSimWorld } from '@kit.ArkGraphics3D';

function pauseBoidsSim(world: BoidsSimWorld): void {
  world.pause();
}
```

## play

```TypeScript
play(): void
```

开始或恢复群组模拟。当群组模拟处于停止状态时，调用此方法可以开始群组模拟；当群组模拟处于暂停状态时，调用此方法可以恢复群组模拟。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { BoidsSimWorld } from '@kit.ArkGraphics3D';

function controlBoidsSimLifecycle(world: BoidsSimWorld): void {
  world.play();
}
```

## removeBoidsSimComponent

```TypeScript
removeBoidsSimComponent(node: Node): void
```

移除指定节点上的群组行为组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |

**示例**

```TypeScript
import { BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function removeBoidsSimComponent(world: BoidsSimWorld, node: Node): void {
  world.removeBoidsSimComponent(node);
}
```

## removeBoidsSimGravityComponent

```TypeScript
removeBoidsSimGravityComponent(node: Node): void
```

移除指定节点上的引力场组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |

**示例**

```TypeScript
import { BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function removeBoidsSimGravityComponent(world: BoidsSimWorld, node: Node): void {
  world.removeBoidsSimGravityComponent(node);
}
```

## removeBoidsSimRepulsionComponent

```TypeScript
removeBoidsSimRepulsionComponent(node: Node): void
```

移除指定节点上的斥力场组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |

**示例**

```TypeScript
import { BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function removeBoidsSimRepulsionComponent(world: BoidsSimWorld, node: Node): void {
  world.removeBoidsSimRepulsionComponent(node);
}
```

## setBoidsSimComponent

```TypeScript
setBoidsSimComponent(node: Node, param: BoidsSimParameters): void
```

更新指定节点上的群组行为组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |
| param | [BoidsSimParameters](arkts-arkgraphics3d-sceneboidssim-boidssimparameters-i-sys.md) | 是 | 群组行为参数。 |

**示例**

```TypeScript
import { BoidsSimParameters, BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function updateBoidsSimComponent(world: BoidsSimWorld, node: Node): void {
  let newParams: BoidsSimParameters = {
    boundaryMinPos: { x: -20.0, y: -20.0, z: -20.0 },
    boundaryMaxPos: { x: 20.0, y: 20.0, z: 20.0 },
    separationWeight: 5.0,
    separationDistance: 1.0,
  };
  world.setBoidsSimComponent(node, newParams);
}
```

## setBoidsSimGravityComponent

```TypeScript
setBoidsSimGravityComponent(node: Node, param: BoidsSimGravityParameters): void
```

更新指定节点上的引力场组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |
| param | [BoidsSimGravityParameters](arkts-arkgraphics3d-sceneboidssim-boidssimgravityparameters-i-sys.md) | 是 | 引力场参数。 |

**示例**

```TypeScript
import { BoidsSimGravityParameters, BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function updateBoidsSimGravityComponent(world: BoidsSimWorld, node: Node): void {
  let newParams: BoidsSimGravityParameters = { accelerationMag: 8.0, radius: 15.0 };
  world.setBoidsSimGravityComponent(node, newParams);
}
```

## setBoidsSimRepulsionComponent

```TypeScript
setBoidsSimRepulsionComponent(node: Node, param: BoidsSimRepulsionParameters): void
```

更新指定节点上的斥力场组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 目标场景的节点。 |
| param | [BoidsSimRepulsionParameters](arkts-arkgraphics3d-sceneboidssim-boidssimrepulsionparameters-i-sys.md) | 是 | 斥力场参数。 |

**示例**

```TypeScript
import { BoidsSimRepulsionParameters, BoidsSimWorld, Node } from '@kit.ArkGraphics3D';

function updateBoidsSimRepulsionComponent(world: BoidsSimWorld, node: Node): void {
  let newParams: BoidsSimRepulsionParameters = { accelerationMag: 8.0, radius: 15.0 };
  world.setBoidsSimRepulsionComponent(node, newParams);
}
```

## stop

```TypeScript
stop(): void
```

停止群组模拟并重置状态。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { BoidsSimWorld } from '@kit.ArkGraphics3D';

function stopBoidsSim(world: BoidsSimWorld): void {
  world.stop();
}
```

## isPlaying

```TypeScript
get isPlaying(): boolean
```

当前模拟是否正在播放。true表示正在播放，false表示已经暂停。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。
