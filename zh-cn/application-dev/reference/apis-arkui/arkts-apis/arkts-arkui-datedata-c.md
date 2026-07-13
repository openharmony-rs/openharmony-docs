# DateData

DateData定义了日期通用属性和方法，包括年、月、日。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(year: number, month: number, day: number)
```

DateData的构造函数用于初始化日期对象。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| year | number | 是 | 设置日期内联型初始年份。 |
| month | number | 是 | 设置日期内联型初始月份。 |
| day | number | 是 | 设置日期内联型初始日。 |

## toString

```TypeScript
toString(): string
```

以字符串格式返回当前日期值。格式为’YYYY-MM-DD'。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

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

超出取值范围按默认值处理。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

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

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

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

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

