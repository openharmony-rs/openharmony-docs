# CounterV2DateData

CounterV2DateData定义了日期通用属性和方法，包括年、月、日。

**起始版本：** 26.0.0

<!--Device-unnamed-declare class CounterV2DateData--><!--Device-unnamed-declare class CounterV2DateData-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2Type, CounterV2DateData } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(year: number, month: number, day: number)
```

CounterV2DateData的构造函数用于初始化日期对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateData-constructor(year: int, month: int, day: int)--><!--Device-CounterV2DateData-constructor(year: int, month: int, day: int)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| year | number | 是 | 设置日期内联型初始年份。<br/>取值范围：[1, 5000]<br/>超出取值范围按默认值处理。 |
| month | number | 是 | 设置日期内联型初始月份。<br/>取值范围：[1, 12]<br/>超出取值范围按默认值处理。 |
| day | number | 是 | 设置日期内联型初始日。<br/>取值范围：[1, 31]<br/>必须为合法日期，如month为2月时，day传入30将视为异常值，按默认值处理。 |

## toString

```TypeScript
toString(): string
```

以字符串格式返回当前日期值。格式为'YYYY-MM-DD'。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateData-toString(): string--><!--Device-CounterV2DateData-toString(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前日期值。 |

## day

```TypeScript
day: number
```

设置日期内联型初始日。

默认值：1

取值范围：[1, 31]

必须为合法日期，如month为2月时，day传入30将视为异常值，按默认值处理。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateData-day: int--><!--Device-CounterV2DateData-day: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month: number
```

设置日期内联型初始月份。

默认值：1

取值范围：[1, 12]

超出取值范围按默认值处理。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateData-month: int--><!--Device-CounterV2DateData-month: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year: number
```

设置日期内联型初始年份。

默认值：1

取值范围：[1, 5000]

超出取值范围按默认值处理。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateData-year: int--><!--Device-CounterV2DateData-year: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

