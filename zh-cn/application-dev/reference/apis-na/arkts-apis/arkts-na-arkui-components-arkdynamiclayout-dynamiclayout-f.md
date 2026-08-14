# DynamicLayout

## DynamicLayout

```TypeScript
@ComponentBuilder
export declare function DynamicLayout (
    algorithm: LayoutAlgorithm,
    content_: CustomBuilder,
): DynamicLayoutAttribute
```

动态布局容器。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function DynamicLayout (    algorithm: LayoutAlgorithm,    content_: CustomBuilder,): DynamicLayoutAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function DynamicLayout (    algorithm: LayoutAlgorithm,    content_: CustomBuilder,): DynamicLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algorithm | [LayoutAlgorithm](arkts-na-layoutalgorithm-i.md) | 是 | 指定动态布局组件的布局算法。 取非法值时，按照堆叠布局算法StackLayoutAlgorithm布局子组件，子组件堆叠排列。 |
| content_ | CustomBuilder | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DynamicLayoutAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-arkdynamiclayout-dynamiclayoutattribute-c.md) |  |

