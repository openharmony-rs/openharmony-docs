# StackLayoutAlgorithm

堆叠布局算法类。 > **说明：** > > StackLayoutAlgorithm类对象可以作为 > [DynamicLayout](../../../reference/apis-arkui/arkui-ts/ts-container-dynamiclayout.md)组件的入参指定布局算法。

**继承/实现关系：** StackLayoutAlgorithm implements [LayoutAlgorithm](arkts-na-layoutalgorithm-i.md#LayoutAlgorithm)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-export declare class StackLayoutAlgorithm--><!--Device-unnamed-export declare class StackLayoutAlgorithm-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(option?: StackLayoutAlgorithmOptions)
```

堆叠布局算法类的构造函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-StackLayoutAlgorithm-constructor(option?: StackLayoutAlgorithmOptions)--><!--Device-StackLayoutAlgorithm-constructor(option?: StackLayoutAlgorithmOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [StackLayoutAlgorithmOptions](arkts-na-layoutalgorithm-stacklayoutalgorithmoptions-i.md) | 否 | 堆叠布局算法的构造入参，设置九宫格对齐格式。 |

## alignContent

```TypeScript
@Trace public alignContent?: LocalizedAlignment
```

设置子组件在堆叠布局算法中对齐格式。 非法值：按默认值处理。

**类型：** [LocalizedAlignment](arkts-na-enums-localizedalignment-e.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-StackLayoutAlgorithm-@Trace public alignContent?: LocalizedAlignment--><!--Device-StackLayoutAlgorithm-@Trace public alignContent?: LocalizedAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

