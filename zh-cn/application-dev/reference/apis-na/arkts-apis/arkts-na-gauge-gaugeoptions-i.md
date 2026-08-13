# GaugeOptions

数据量规图表选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface GaugeOptions--><!--Device-unnamed-export interface GaugeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max?: double
```

当前数据段最大值。 默认值：100。 &lt;br&gt;**说明：** max小于min时使用默认值0和100。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GaugeOptions-max?: double--><!--Device-GaugeOptions-max?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: double
```

当前数据段最小值。 默认值：0。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GaugeOptions-min?: double--><!--Device-GaugeOptions-min?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: double | undefined
```

量规图的当前数据值，即图中指针指向位置。用于组件创建时量规图初始值的预置。 默认值：0 **说明：** value不在min和max范围内时使用min作为默认值。

**类型：** double \| undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GaugeOptions-value: double | undefined--><!--Device-GaugeOptions-value: double | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

