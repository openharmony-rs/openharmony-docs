# CounterV2DateData

CounterV2DateData定义了日期通用属性和方法，包括年、月、日。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-declare class CounterV2DateData--><!--Device-unnamed-declare class CounterV2DateData-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(year: int, month: int, day: int)
```

CounterV2DateData的构造函数用于初始化日期对象。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateData-constructor(year: int, month: int, day: int)--><!--Device-CounterV2DateData-constructor(year: int, month: int, day: int)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| year | int | 是 | 日期内联型的年份。取值范围：[1, 5000]。超出取值范围按默认值处理。 |
| month | int | 是 | 日期内联型的月份。取值范围：[1, 12]。超出取值范围按默认值处理。 |
| day | int | 是 | 日期内联型的日。取值范围：[1, 31]。必须为合法日期，如month为2月时，day传入30将视为异常值，按默认值处理。超出取值范围按默认值处理。 |

## toString

```TypeScript
toString(): string
```

以字符串格式返回当前日期值。格式为"YYYY-MM-DD"。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateData-toString(): string--><!--Device-CounterV2DateData-toString(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式为“YYYY-MM-DD”的日期字符串，例如“2024-01-15”。 |

## day

```TypeScript
day: int
```

表示日期内联型的日。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateData-day: int--><!--Device-CounterV2DateData-day: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month: int
```

表示日期内联型的月份。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateData-month: int--><!--Device-CounterV2DateData-month: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year: int
```

表示日期内联型的年份。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2DateData-year: int--><!--Device-CounterV2DateData-year: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

