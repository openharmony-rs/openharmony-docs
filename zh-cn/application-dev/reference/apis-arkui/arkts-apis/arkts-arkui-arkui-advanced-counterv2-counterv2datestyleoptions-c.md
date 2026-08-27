# CounterV2DateStyleOptions

CounterV2DateStyleOptions定义日期内联型CounterV2的属性和事件。继承于[CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md)，包含该接口所有属性。本节仅展示新增属性，继承属性请参见父接口。

**继承/实现关系：** CounterV2DateStyleOptions extends [CounterV2CommonOptions](arkts-arkui-arkui-advanced-counterv2-counterv2commonoptions-c.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## onDateChange

```TypeScript
onDateChange?: OnDateCounterV2ChangeCallback
```

当日期改变时，触发该回调。回调参数date表示当前显示的日期值。使用场景：当需要在日期变化时执行自定义操作（如更新关联数据、触发业务逻辑、记录日志等）时传入此回调。默认值：undefined，表示不触发该回调。值为undefined时，按默认值处理。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## day

```TypeScript
day?: number
```

设置日期内联型初始日。默认值：1取值范围：[1, 31]必须为合法日期，如month为2月时，day传入30将视为异常值，按默认值处理。超出取值范围按默认值处理。值为undefined时，按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: number
```

设置日期内联型初始月份。默认值：1取值范围：[1, 12]超出取值范围按默认值处理。值为undefined时，按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: number
```

设置日期内联型初始年份。默认值：1取值范围：[1, 5000]超出取值范围按默认值处理。值为undefined时，按默认值处理。

**类型：** number

**默认值：** 1

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
