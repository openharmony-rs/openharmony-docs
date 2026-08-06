# Scene

定义3D场景.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export declare class Scene--><!--Device-unnamed-export declare class Scene-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## cloneNode

```TypeScript
cloneNode(node: Node, parent: Node, name: string): Node | null
```

克隆以输入节点为根节点的节点或子树

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-Scene-cloneNode(node: Node, parent: Node, name: string): Node | null--><!--Device-Scene-cloneNode(node: Node, parent: Node, name: string): Node | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要克隆的输入节点 |
| parent | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 克隆节点将被设置为其子节点的父节点 |
| name | string | 是 | 克隆节点的名称 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 克隆结果，如果克隆失败则返回null. |

## createComponent

```TypeScript
createComponent(node: Node, name: string): Promise<SceneComponent>
```

创建新组件.

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-Scene-createComponent(node: Node, name: string): Promise<SceneComponent>--><!--Device-Scene-createComponent(node: Node, name: string): Promise<SceneComponent>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 组件附加到的节点 |
| name | string | 是 | 要加载的组件名称. 有效名称由各插件定义. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | - 新添加的组件. |

## destroy

```TypeScript
destroy(): void
```

释放所有原生场景资源. 所有TS引用将变为undefined.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Scene-destroy(): void--><!--Device-Scene-destroy(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getComponent

```TypeScript
getComponent(node: Node, name: string): SceneComponent | null
```

通过名称获取组件.

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-Scene-getComponent(node: Node, name: string): SceneComponent | null--><!--Device-Scene-getComponent(node: Node, name: string): SceneComponent | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 组件附加到的节点. |
| name | string | 是 | 组件名称 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

## getDefaultRenderContext

```TypeScript
static getDefaultRenderContext(): RenderContext | null
```

获取默认渲染上下文

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-Scene-static getDefaultRenderContext(): RenderContext | null--><!--Device-Scene-static getDefaultRenderContext(): RenderContext | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | -- 默认RenderContext实例 |

## getNodeByPath

```TypeScript
getNodeByPath(path: string, type?: NodeType): Node | null
```

通过路径获取节点.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Scene-getNodeByPath(path: string, type?: NodeType): Node | null--><!--Device-Scene-getNodeByPath(path: string, type?: NodeType): Node | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 节点路径 |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 验证节点类型，如果不匹配则返回null |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 如果通过路径找到节点 |

## getResourceFactory

```TypeScript
getResourceFactory(): SceneResourceFactory
```

获取资源工厂.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Scene-getResourceFactory(): SceneResourceFactory--><!--Device-Scene-getResourceFactory(): SceneResourceFactory-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 如果通过路径找到节点 |

## importNode

```TypeScript
importNode(name: string, node: Node, parent: Node | null): Node
```

将节点导入场景. 原始节点可能来自另一个场景. 节点将被克隆，导入后对旧节点的修改将不可见.

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-Scene-importNode(name: string, node: Node, parent: Node | null): Node--><!--Device-Scene-importNode(name: string, node: Node, parent: Node | null): Node-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 新创建节点的名称. |
| node | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要导入的节点. |
| parent | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 是 | 父节点，根节点为null |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 新创建的节点. |

## importScene

```TypeScript
importScene(name: string, scene: Scene, parent: Node | null): Node
```

将场景作为节点导入场景. 节点层级将出现在父节点下. 场景中的所有动画将被复制.

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-Scene-importScene(name: string, scene: Scene, parent: Node | null): Node--><!--Device-Scene-importScene(name: string, scene: Scene, parent: Node | null): Node-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 新创建节点的名称 |
| scene | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The scene to be imported. |
| parent | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 是 | 父节点，根节点为null |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 新创建的节点. |

## load

```TypeScript
static load(uri? : ResourceStr): Promise<Scene>
```

从ResourceStr创建新场景. 如果未提供uri，将返回空场景.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Scene-static load(uri? : ResourceStr): Promise<Scene>--><!--Device-Scene-static load(uri? : ResourceStr): Promise<Scene>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 创建场景的资源 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | 返回创建的场景 |

## renderFrame

```TypeScript
renderFrame(params?: RenderParameters): boolean
```

为所有活动相机渲染新帧.

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-Scene-renderFrame(params?: RenderParameters): boolean--><!--Device-Scene-renderFrame(params?: RenderParameters): boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 渲染参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果渲染被调度则返回true，否则返回false |

## animations

```TypeScript
get animations(): Animation[]
```

场景的动画.

**类型：** Animation[]

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Scene-get animations(): Animation[]--><!--Device-Scene-get animations(): Animation[]-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## environment

```TypeScript
set environment(value: Environment)
```

场景的环境.

**类型：** Environment

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Scene-set environment(value: Environment)--><!--Device-Scene-set environment(value: Environment)-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderConfiguration

```TypeScript
get renderConfiguration(): RenderConfiguration
```

渲染配置设置

**类型：** RenderConfiguration

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-Scene-get renderConfiguration(): RenderConfiguration--><!--Device-Scene-get renderConfiguration(): RenderConfiguration-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## root

```TypeScript
get root(): Node | null
```

场景的根节点.

**类型：** Node

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Scene-get root(): Node | null--><!--Device-Scene-get root(): Node | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

