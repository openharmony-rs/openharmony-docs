# BoidsSimWorld（系统接口）

群组模拟世界接口. 提供群组模拟的播放控制和组件管理.

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class BoidsSimWorld--><!--Device-unnamed-export declare class BoidsSimWorld-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

<a id="addboidssimcomponent"></a>
## addBoidsSimComponent

```TypeScript
addBoidsSimComponent(node: Node, param: BoidsSimParameters): void
```

在指定节点上添加群组模拟组件.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-addBoidsSimComponent(node: Node, param: BoidsSimParameters): void--><!--Device-BoidsSimWorld-addBoidsSimComponent(node: Node, param: BoidsSimParameters): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要添加组件的节点 |
| param | [BoidsSimParameters](arkts-arkgraphics3d-sceneboidssim-boidssimparameters-i-sys.md) | 是 | 群组模拟参数 |

<a id="addboidssimgravitycomponent"></a>
## addBoidsSimGravityComponent

```TypeScript
addBoidsSimGravityComponent(node: Node, param: BoidsSimGravityParameters): void
```

在指定节点上添加引力场组件.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-addBoidsSimGravityComponent(node: Node, param: BoidsSimGravityParameters): void--><!--Device-BoidsSimWorld-addBoidsSimGravityComponent(node: Node, param: BoidsSimGravityParameters): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要添加组件的节点 |
| param | [BoidsSimGravityParameters](arkts-arkgraphics3d-sceneboidssim-boidssimgravityparameters-i-sys.md) | 是 | 引力场参数 |

<a id="addboidssimrepulsioncomponent"></a>
## addBoidsSimRepulsionComponent

```TypeScript
addBoidsSimRepulsionComponent(node: Node, param: BoidsSimRepulsionParameters): void
```

在指定节点上添加斥力场组件.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-addBoidsSimRepulsionComponent(node: Node, param: BoidsSimRepulsionParameters): void--><!--Device-BoidsSimWorld-addBoidsSimRepulsionComponent(node: Node, param: BoidsSimRepulsionParameters): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要添加组件的节点 |
| param | [BoidsSimRepulsionParameters](arkts-arkgraphics3d-sceneboidssim-boidssimrepulsionparameters-i-sys.md) | 是 | 斥力场参数 |

<a id="getboidssimcomponent"></a>
## getBoidsSimComponent

```TypeScript
getBoidsSimComponent(node: Node): BoidsSimParameters | null
```

获取指定节点上的群组模拟组件参数.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-getBoidsSimComponent(node: Node): BoidsSimParameters | null--><!--Device-BoidsSimWorld-getBoidsSimComponent(node: Node): BoidsSimParameters | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要查询的节点 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BoidsSimParameters](arkts-arkgraphics3d-sceneboidssim-boidssimparameters-i-sys.md) | 群组模拟参数，如果未找到则返回null |

<a id="getboidssimgravitycomponent"></a>
## getBoidsSimGravityComponent

```TypeScript
getBoidsSimGravityComponent(node: Node): BoidsSimGravityParameters | null
```

获取指定节点上的引力场组件参数.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-getBoidsSimGravityComponent(node: Node): BoidsSimGravityParameters | null--><!--Device-BoidsSimWorld-getBoidsSimGravityComponent(node: Node): BoidsSimGravityParameters | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要查询的节点 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BoidsSimGravityParameters](arkts-arkgraphics3d-sceneboidssim-boidssimgravityparameters-i-sys.md) | 引力场参数，如果未找到则返回null |

<a id="getboidssimrepulsioncomponent"></a>
## getBoidsSimRepulsionComponent

```TypeScript
getBoidsSimRepulsionComponent(node: Node): BoidsSimRepulsionParameters | null
```

获取指定节点上的斥力场组件参数.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-getBoidsSimRepulsionComponent(node: Node): BoidsSimRepulsionParameters | null--><!--Device-BoidsSimWorld-getBoidsSimRepulsionComponent(node: Node): BoidsSimRepulsionParameters | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要查询的节点 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BoidsSimRepulsionParameters](arkts-arkgraphics3d-sceneboidssim-boidssimrepulsionparameters-i-sys.md) | 斥力场参数，如果未找到则返回null |

<a id="pause"></a>
## pause

```TypeScript
pause(): void
```

暂停模拟.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-pause(): void--><!--Device-BoidsSimWorld-pause(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

<a id="play"></a>
## play

```TypeScript
play(): void
```

开始或恢复模拟.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-play(): void--><!--Device-BoidsSimWorld-play(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

<a id="removeboidssimcomponent"></a>
## removeBoidsSimComponent

```TypeScript
removeBoidsSimComponent(node: Node): void
```

从指定节点移除群组模拟组件.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-removeBoidsSimComponent(node: Node): void--><!--Device-BoidsSimWorld-removeBoidsSimComponent(node: Node): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要移除组件的节点 |

<a id="removeboidssimgravitycomponent"></a>
## removeBoidsSimGravityComponent

```TypeScript
removeBoidsSimGravityComponent(node: Node): void
```

从指定节点移除引力场组件.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-removeBoidsSimGravityComponent(node: Node): void--><!--Device-BoidsSimWorld-removeBoidsSimGravityComponent(node: Node): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要移除组件的节点 |

<a id="removeboidssimrepulsioncomponent"></a>
## removeBoidsSimRepulsionComponent

```TypeScript
removeBoidsSimRepulsionComponent(node: Node): void
```

从指定节点移除斥力场组件.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-removeBoidsSimRepulsionComponent(node: Node): void--><!--Device-BoidsSimWorld-removeBoidsSimRepulsionComponent(node: Node): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要移除组件的节点 |

<a id="setboidssimcomponent"></a>
## setBoidsSimComponent

```TypeScript
setBoidsSimComponent(node: Node, param: BoidsSimParameters): void
```

更新指定节点上的群组模拟组件参数.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-setBoidsSimComponent(node: Node, param: BoidsSimParameters): void--><!--Device-BoidsSimWorld-setBoidsSimComponent(node: Node, param: BoidsSimParameters): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要更新的节点 |
| param | [BoidsSimParameters](arkts-arkgraphics3d-sceneboidssim-boidssimparameters-i-sys.md) | 是 | 群组模拟参数 |

<a id="setboidssimgravitycomponent"></a>
## setBoidsSimGravityComponent

```TypeScript
setBoidsSimGravityComponent(node: Node, param: BoidsSimGravityParameters): void
```

更新指定节点上的引力场组件参数.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-setBoidsSimGravityComponent(node: Node, param: BoidsSimGravityParameters): void--><!--Device-BoidsSimWorld-setBoidsSimGravityComponent(node: Node, param: BoidsSimGravityParameters): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要更新的节点 |
| param | [BoidsSimGravityParameters](arkts-arkgraphics3d-sceneboidssim-boidssimgravityparameters-i-sys.md) | 是 | 引力场参数 |

<a id="setboidssimrepulsioncomponent"></a>
## setBoidsSimRepulsionComponent

```TypeScript
setBoidsSimRepulsionComponent(node: Node, param: BoidsSimRepulsionParameters): void
```

更新指定节点上的斥力场组件参数.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-setBoidsSimRepulsionComponent(node: Node, param: BoidsSimRepulsionParameters): void--><!--Device-BoidsSimWorld-setBoidsSimRepulsionComponent(node: Node, param: BoidsSimRepulsionParameters): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要更新的节点 |
| param | [BoidsSimRepulsionParameters](arkts-arkgraphics3d-sceneboidssim-boidssimrepulsionparameters-i-sys.md) | 是 | 斥力场参数 |

<a id="stop"></a>
## stop

```TypeScript
stop(): void
```

停止模拟并重置所有boid到初始状态.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-stop(): void--><!--Device-BoidsSimWorld-stop(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## isPlaying

```TypeScript
get isPlaying(): boolean
```

模拟是否正在播放.

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimWorld-get isPlaying(): boolean--><!--Device-BoidsSimWorld-get isPlaying(): boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

