# CustomLayoutAlgorithm

自定义布局算法类。

> **说明：**  
>  
> CustomLayoutAlgorithm类对象可以赋值给LayoutAlgorithm类型变量，作为[DynamicLayout](arkts-arkui-components-arkdynamiclayout.md)组件  
> 的入参指定布局算法。

**继承/实现关系：** CustomLayoutAlgorithm implements [LayoutAlgorithm](arkts-arkui-layoutalgorithm-i.md)

**起始版本：** 24

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export class CustomLayoutAlgorithm implements LayoutAlgorithm--><!--Device-unnamed-export class CustomLayoutAlgorithm implements LayoutAlgorithm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="onlayout"></a>
## onLayout

```TypeScript
onLayout(self: FrameNode, position: Position): void
```

通过重写此函数，开发者可以自定义排列子组件的位置。ArkUI框架会在动态布局组件确定位置时，将该组件对应的FrameNode和布局位置通过onLayout传递给开发者。不允许在onLayout函数中改变状态变量。

> **说明：**  
>  
> 在此函数中，开发者可以调用[FrameNode](arkts-arkui-framenode-c.md)的  
> [getChild()](arkts-arkui-framenode-c.md#getchild-1)方法获取子组件FrameNode，调用  
> [FrameNode](arkts-arkui-framenode-c.md)的[layout()](arkts-arkui-framenode-c.md#layout-1)方法设置子组件位置，参考DynamicLayout组件  
> [示例1（自定义布局算法实现瀑布流布局）](docroot://reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md#示例1自定义布局算法实现瀑布流布局)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-CustomLayoutAlgorithm-onLayout(self: FrameNode, position: Position): void--><!--Device-CustomLayoutAlgorithm-onLayout(self: FrameNode, position: Position): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| self | [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | 是 | 动态布局组件在组件树上的实体节点。 |
| position | [Position](arkts-arkui-position-i.md) | 是 | 动态布局组件进行布局时使用的位置信息。 |

<a id="onmeasure"></a>
## onMeasure

```TypeScript
onMeasure(self: FrameNode, constraint: LayoutConstraint): void
```

通过重写此函数，开发者可以自定义测量子组件的大小。ArkUI框架会在动态布局组件确定尺寸时，将该组件对应的FrameNode和布局约束通过onMeasure传递给开发者。不允许在onMeasure函数中改变状态变量。

> **说明：**  
>  
> 在此函数中，开发者可以调用[FrameNode](arkts-arkui-framenode-c.md)的  
> [getChild()](arkts-arkui-framenode-c.md#getchild-1)方法获取子组件FrameNode，调用  
> [FrameNode](arkts-arkui-framenode-c.md)的[measure()](arkts-arkui-framenode-c.md#measure-1)方法测量子组件大小，参考DynamicLayout组  
> 件  
> [示例1（自定义布局算法实现瀑布流布局）](docroot://reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md#示例1自定义布局算法实现瀑布流布局)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-CustomLayoutAlgorithm-onMeasure(self: FrameNode, constraint: LayoutConstraint): void--><!--Device-CustomLayoutAlgorithm-onMeasure(self: FrameNode, constraint: LayoutConstraint): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| self | [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | 是 | 动态布局组件在组件树上的实体节点。 |
| constraint | [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | 是 | 动态布局组件进行测量时使用的布局约束。 |

