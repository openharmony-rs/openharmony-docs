# CounterV2DateStyleOptions

CounterV2DateStyleOptions定义日期内联型CounterV2的属性和事件。

继承于[CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md)。

**继承/实现关系：** CounterV2DateStyleOptions extends [CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md)

**起始版本：** 26.0.0

<!--Device-unnamed-declare class CounterV2DateStyleOptions extends CounterV2CommonOptions--><!--Device-unnamed-declare class CounterV2DateStyleOptions extends CounterV2CommonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2Type, CounterV2DateData } from '@kit.ArkUI';
```

## day

```TypeScript
day?: number
```

设置日期内联型初始日。

默认值：1

取值范围：[1, 31]

必须为合法日期，如month为2月时，day传入30将视为异常值，按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateStyleOptions-day?: int--><!--Device-CounterV2DateStyleOptions-day?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: number
```

设置日期内联型初始月份。

默认值：1

取值范围：[1, 12]

超出取值范围按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateStyleOptions-month?: int--><!--Device-CounterV2DateStyleOptions-month?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDateChange

```TypeScript
onDateChange?: OnDateCounterV2ChangeCallback
```

当日期改变时，返回当前日期。

值为undefined时，不显示当前的日期值。

**类型：** OnDateCounterV2ChangeCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateStyleOptions-onDateChange?: OnDateCounterV2ChangeCallback--><!--Device-CounterV2DateStyleOptions-onDateChange?: OnDateCounterV2ChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: number
```

设置日期内联型初始年份。

默认值：1

取值范围：[1, 5000]

超出取值范围按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateStyleOptions-year?: int--><!--Device-CounterV2DateStyleOptions-year?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

