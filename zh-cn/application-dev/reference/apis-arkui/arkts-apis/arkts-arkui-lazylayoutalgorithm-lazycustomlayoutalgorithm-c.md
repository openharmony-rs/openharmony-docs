# LazyCustomLayoutAlgorithm

自定义懒加载布局算法类。

> **说明：**  
>  
> LazyCustomLayoutAlgorithm类对象可以作为  
> [LazyDynamicLayout](docroot://reference/apis-arkui/arkui-ts/ts-container-lazydynamiclayout.md)组件的入参指定布局算法。

**继承/实现关系：** LazyCustomLayoutAlgorithm implements [LazyLayoutAlgorithm](arkts-arkui-lazylayoutalgorithm-i.md)

**起始版本：** 26.0.0

<!--Device-unnamed-export class LazyCustomLayoutAlgorithm implements LazyLayoutAlgorithm--><!--Device-unnamed-export class LazyCustomLayoutAlgorithm implements LazyLayoutAlgorithm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(option?: LazyCustomLayoutAlgorithmOptions)
```

自定义懒加载布局算法类的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyCustomLayoutAlgorithm-constructor(option?: LazyCustomLayoutAlgorithmOptions)--><!--Device-LazyCustomLayoutAlgorithm-constructor(option?: LazyCustomLayoutAlgorithmOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [LazyCustomLayoutAlgorithmOptions](arkts-arkui-lazylayoutalgorithm-lazycustomlayoutalgorithmoptions-i.md) | 否 | 自定义懒加载布局算法的构造入参，设置布局算法的轴向。 |

<a id="onlayout"></a>
## onLayout

```TypeScript
onLayout(self: FrameNode, position: Position): void
```

通过重写此函数，开发者可以自定义排列子组件的位置。ArkUI框架会在懒加载动态布局组件确定位置时，将该组件对应的FrameNode和布局位置通过onLayout传递给开发者。不允许在onLayout函数中改变状态变量。

> **说明：**  
>  
> - 在此函数中，开发者可以调用[FrameNode](arkts-arkui-framenode-c.md)的  
> [getChild()](arkts-arkui-framenode-c.md#getchild-1)方法获取子组件FrameNode，调用  
> [FrameNode](arkts-arkui-framenode-c.md)的[layout()](arkts-arkui-framenode-c.md#layout-1)方法设置子组件位置，参考  
> LazyDynamicLayout组件  
> [示例1（实现懒加载自定义布局）](docroot://reference/apis-arkui/arkui-ts/ts-container-lazydynamiclayout.md#示例1实现懒加载自定义布局)。  
>  
> - 在此函数中调用[getChild()](arkts-arkui-framenode-c.md#getchild-1)方法获取子组件时，必须传入  
> [ExpandMode.LAZY_NOT_EXPAND](arkts-arkui-framenode-expandmode-e.md)，避免全量加载子组件导致懒加载失效。调用  
> [getChildrenCount()](arkts-arkui-framenode-c.md#getchildrencount-1)方法获取子组件总数时，必须传入  
> [ChildrenCountMode.ALL_NOT_EXPAND](arkts-arkui-framenode-childrencountmode-e.md)，避免获取子组件总数时全量加载子组件导致懒加载失效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyCustomLayoutAlgorithm-onLayout(self: FrameNode, position: Position): void--><!--Device-LazyCustomLayoutAlgorithm-onLayout(self: FrameNode, position: Position): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| self | [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | 是 | 懒加载动态布局组件在组件树上的实体节点。 |
| position | [Position](arkts-arkui-position-i.md) | 是 | 懒加载动态布局组件进行布局时使用的位置信息。 |

<a id="onmeasure"></a>
## onMeasure

```TypeScript
onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void
```

通过重写此函数，开发者可以自定义测量子组件的大小。ArkUI框架会在懒加载动态布局组件确定尺寸时，将该组件对应的FrameNode、布局约束和懒加载辅助对象通过onMeasure传递给开发者。不允许在onMeasure函数中改变状态变量。

> **说明：**  
>  
> - 在此函数中，开发者可以调用[FrameNode](arkts-arkui-framenode-c.md)的  
> [getChild()](arkts-arkui-framenode-c.md#getchild-1)方法获取子组件FrameNode，调用  
> [FrameNode](arkts-arkui-framenode-c.md)的[measure()](arkts-arkui-framenode-c.md#measure-1)方法测量子组件大小，参考  
> LazyDynamicLayout组件  
> [示例1（实现懒加载自定义布局）](docroot://reference/apis-arkui/arkui-ts/ts-container-lazydynamiclayout.md#示例1实现懒加载自定义布局)。  
>  
> - 在此函数中调用[getChild()](arkts-arkui-framenode-c.md#getchild-1)方法获取子组件时，必须传入  
> [ExpandMode.LAZY_NOT_EXPAND](arkts-arkui-framenode-expandmode-e.md)，避免全量加载子组件导致懒加载失效。调用  
> [getChildrenCount()](arkts-arkui-framenode-c.md#getchildrencount-1)方法获取子组件总数时，必须传入  
> [ChildrenCountMode.ALL_NOT_EXPAND](arkts-arkui-framenode-childrencountmode-e.md)，避免获取子组件总数时全量加载子组件导致懒加载失效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyCustomLayoutAlgorithm-onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void--><!--Device-LazyCustomLayoutAlgorithm-onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| self | [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | 是 | 懒加载动态布局组件在组件树上的实体节点。 |
| constraint | [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | 是 | 懒加载动态布局组件进行测量时使用的布局约束。 |
| helper | [LazyLayoutHelper](arkts-arkui-lazylayoutalgorithm-lazylayouthelper-c.md) | 否 | 懒加载布局辅助对象，提供布局方向和可视区域位置信息。为undefined时表示不支持懒加载。helper为undefined的场景如下：<br>1. 在[WaterFlow](../../apis-arkui/arkts-components/arkts-arkui-water_flow-i)组件多列模式或分段模式的多列分段下使用时不支持懒加载。<br>2. 在[List](../../apis-arkui/arkts-components/arkts-arkui-list-i)组件下使用，当List设置了[lanes](ListAttribute#lanes(value: number \| LengthConstrain, gutter?: Dimension))、[chainAnimation](ListAttribute#chainAnimation)、[scrollSnapAlign](ListAttribute#scrollSnapAlign)属性中的任意一个时不支持懒加载。 |

