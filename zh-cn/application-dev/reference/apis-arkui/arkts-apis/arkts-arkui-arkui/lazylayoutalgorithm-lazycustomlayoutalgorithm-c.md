# LazyCustomLayoutAlgorithm

定义懒式自定义布局算法。

**继承/实现关系：** LazyCustomLayoutAlgorithm implements [LazyLayoutAlgorithm](lazylayoutalgorithm-lazylayoutalgorithm-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class LazyCustomLayoutAlgorithm implements LazyLayoutAlgorithm--><!--Device-unnamed-export declare class LazyCustomLayoutAlgorithm implements LazyLayoutAlgorithm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: LazyCustomLayoutAlgorithmOptions)
```

构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyCustomLayoutAlgorithm-constructor(option?: LazyCustomLayoutAlgorithmOptions)--><!--Device-LazyCustomLayoutAlgorithm-constructor(option?: LazyCustomLayoutAlgorithmOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 设置懒加载自定义布局算法的属性。 |

## onLayout

```TypeScript
onLayout(self: FrameNode, position: NodePosition): void
```

方法为DynamicLayout的FrameNode及其每个子节点分配一个位置。 它可以用于指定DynamicLayoutdFrameNode及其子节点的布局位置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyCustomLayoutAlgorithm-onLayout(self: FrameNode, position: NodePosition): void--><!--Device-LazyCustomLayoutAlgorithm-onLayout(self: FrameNode, position: NodePosition): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| self | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | DynamicLayout组件的FrameNode。 |
| position | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 节点的位置，将在执行布局方法时使用。 |

## onMeasure

```TypeScript
onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void
```

测量DynamicLayout FrameNode及其内容，以确定测量的大小的方法。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyCustomLayoutAlgorithm-onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void--><!--Device-LazyCustomLayoutAlgorithm-onMeasure(self: FrameNode, constraint: LayoutConstraint, helper?: LazyLayoutHelper): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| self | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | DynamicLayout组件的FrameNode。 |
| constraint | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 节点的布局约束，将在测量过程中使用。 |
| helper | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 懒布局算法的助手对象，提供布局方向和视图位置信息。如果未定义，则表示当前组件未在可滚动组件下使用，不支持懒布局。 |

