# CounterV2InlineStyleOptions

CounterV2InlineStyleOptions定义了数值内联型CounterV2的属性和事件。

继承于[CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md)。

**继承/实现关系：** CounterV2InlineStyleOptions extends [CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md)

**起始版本：** 26.0.0

<!--Device-unnamed-declare class CounterV2InlineStyleOptions extends CounterV2CommonOptions--><!--Device-unnamed-declare class CounterV2InlineStyleOptions extends CounterV2CommonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2Type, CounterV2DateData } from '@kit.ArkUI';
```

## max

```TypeScript
max?: number
```

设置CounterV2的最大值。

默认值：999

取值范围：(-∞, +∞)

值为undefined时，按默认值处理。

**类型：** number

**默认值：** 999

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2InlineStyleOptions-max?: int--><!--Device-CounterV2InlineStyleOptions-max?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: number
```

设置CounterV2的最小值。

默认值：0

取值范围：(-∞, +∞)

值为undefined时，按默认值处理。

**类型：** number

**默认值：** 0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2InlineStyleOptions-min?: int--><!--Device-CounterV2InlineStyleOptions-min?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: OnInlineCounterV2Change
```

数值改变时，返回当前值。

默认值：数值改变时，不返回值。

值为undefined时，按默认值处理。

**类型：** OnInlineCounterV2Change

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2InlineStyleOptions-onChange?: OnInlineCounterV2Change--><!--Device-CounterV2InlineStyleOptions-onChange?: OnInlineCounterV2Change-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textWidth

```TypeScript
textWidth?: number
```

设置数值文本的宽度。

默认值：undefined

取值范围：[0, +∞)

单位：vp

不设置该属性或者设置为undefined时，文本宽度由内容自适应撑开。小于0时，按0处理。

**类型：** number

**默认值：** undefined

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2InlineStyleOptions-textWidth?: double--><!--Device-CounterV2InlineStyleOptions-textWidth?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: number
```

设置CounterV2的初始值。

默认值：0

取值范围：[min, max]，其中min和max分别对应下述CounterV2的最小值和最大值。

超出取值范围时，如果值为undefined，按默认值处理，否则按最大值处理。

**类型：** number

**默认值：** 0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2InlineStyleOptions-value?: int--><!--Device-CounterV2InlineStyleOptions-value?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

