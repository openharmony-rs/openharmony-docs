# InlineStyleOptions

InlineStyleOptions定义了数值内联型Counter的属性和事件。

继承于[CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)。

**继承/实现关系：** InlineStyleOptions extends [CommonOptions](arkts-arkui-arkui-advanced-counter-commonoptions-c.md)

**起始版本：** 11

<!--Device-unnamed-declare class InlineStyleOptions extends CommonOptions--><!--Device-unnamed-declare class InlineStyleOptions extends CommonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterType, DateData, CounterComponent, CounterOptions } from '@kit.ArkUI';
```

## max

```TypeScript
max?: number
```

设置Counter的最大值。

默认值：999

取值范围：(-∞, +∞)

值为undefined时，按默认值处理。

**类型：** number

**默认值：** 999

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InlineStyleOptions-max?: number--><!--Device-InlineStyleOptions-max?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: number
```

设置Counter的最小值。

默认值：0

取值范围：(-∞, +∞)

值为undefined时，按默认值处理。

**类型：** number

**默认值：** 0

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InlineStyleOptions-min?: number--><!--Device-InlineStyleOptions-min?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: (value: number) => void
```

数值改变时，返回当前值。

value：当前显示的数值。

默认值：数值改变时，不返回值。

值为undefined时，按默认值处理。

**类型：** (value: number) =&gt; void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InlineStyleOptions-onChange?: (value: number) => void--><!--Device-InlineStyleOptions-onChange?: (value: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textWidth

```TypeScript
textWidth?: number
```

设置数值文本的宽度。

默认值：自适应文本宽度。

取值范围：[0, +∞)

单位：vp

超出取值范围时，如果值为undefined，按默认值处理，否则按最大值处理。

**类型：** number

**默认值：** 0

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InlineStyleOptions-textWidth?: number--><!--Device-InlineStyleOptions-textWidth?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: number
```

设置Counter的初始值。

默认值：0

取值范围：[min, max]，其中min和max分别对应下述Counter的最小值和最大值。

超出取值范围时，如果值为undefined，按默认值处理，否则按最大值处理。

**类型：** number

**默认值：** 0

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InlineStyleOptions-value?: number--><!--Device-InlineStyleOptions-value?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

