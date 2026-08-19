# CustomLayoutAlgorithm

自定义布局算法类。 > **说明：** > > CustomLayoutAlgorithm类对象可以作为 > [DynamicLayout](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md)组件的入参指定布局算法。

**继承/实现关系：** CustomLayoutAlgorithm implements [LayoutAlgorithm](../../apis-arkui/arkts-apis/arkts-arkui-layoutalgorithm-i.md)

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export declare class CustomLayoutAlgorithm--><!--Device-unnamed-export declare class CustomLayoutAlgorithm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onLayout

```TypeScript
onLayout(self: FrameNode, position: NodePosition): void
```

通过重写此函数，开发者可以自定义排列子组件的位置。 ArkUI框架会在动态布局组件确定位置时，将该组件对应的FrameNode和布局位置通过onLayout传递给开发者。 不允许在onLayout函数中改变状态变量。 > **说明：** > > 在此函数中，开发者可以调用 > FrameNode的 > getChild()方法获取子组件FrameNode， > 调用FrameNode的 > layout()方法设置子组件位置， > 参考DynamicLayout组件 > [示例1（自定义布局算法实现瀑布流布局）](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md#示例1自定义布局算法实现瀑布流布局)。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

<!--Device-CustomLayoutAlgorithm-onLayout(self: FrameNode, position: NodePosition): void--><!--Device-CustomLayoutAlgorithm-onLayout(self: FrameNode, position: NodePosition): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| self | [FrameNode](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md) | 是 | 动态布局组件在组件树上的实体节点。 |
| position | [NodePosition](arkts-na-nodeposition-t.md) | 是 | 动态布局组件进行布局时使用的位置信息。 |

## onMeasure

```TypeScript
onMeasure(self: FrameNode, constraint: LayoutConstraint): void
```

通过重写此函数，开发者可以自定义测量子组件的大小。 ArkUI框架会在动态布局组件确定尺寸时，将该组件对应的FrameNode和布局约束通过onMeasure传递给开发者。 不允许在onMeasure函数中改变状态变量。 > **说明：** > > 在此函数中，开发者可以调用 > FrameNode的 > getChild()方法获取子组件FrameNode， > 调用FrameNode的 > measure()方法测量子组件大小， > 参考DynamicLayout组件 > [示例1（自定义布局算法实现瀑布流布局）](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md#示例1自定义布局算法实现瀑布流布局)。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

<!--Device-CustomLayoutAlgorithm-onMeasure(self: FrameNode, constraint: LayoutConstraint): void--><!--Device-CustomLayoutAlgorithm-onMeasure(self: FrameNode, constraint: LayoutConstraint): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| self | [FrameNode](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md) | 是 | 动态布局组件在组件树上的实体节点。 |
| constraint | [LayoutConstraint](../../apis-arkui/arkts-apis/arkts-arkui-framenode-layoutconstraint-i.md) | 是 | 动态布局组件进行测量时使用的布局约束。 |

