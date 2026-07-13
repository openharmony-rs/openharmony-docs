# Decimal

任意精度的Decimal类型。

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## abs

```TypeScript
abs(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的绝对值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## abs

```TypeScript
static abs(n: Value): Decimal
```

返回一个新的Decimal对象，Decimal的值为参数n的绝对值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## acos

```TypeScript
acos(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的反余弦值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## acos

```TypeScript
static acos(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的反余弦值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## acosh

```TypeScript
acosh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的双曲余弦的倒数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## acosh

```TypeScript
static acosh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲余弦的倒数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## add

```TypeScript
add(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值加上n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## add

```TypeScript
static add(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x加y的和。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | Value | 是 | {double \| string \| Decimal} |
| y | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## asin

```TypeScript
asin(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的反正弦值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## asin

```TypeScript
static asin(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的反正弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## asinh

```TypeScript
asinh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的双曲正弦的倒数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## asinh

```TypeScript
static asinh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正弦的倒数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## atan

```TypeScript
atan(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的反正切值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## atan

```TypeScript
static atan(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的反正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## atan2

```TypeScript
static atan2(y: Value, x: Value): Decimal
```

返回一个新的Decimal对象，其值是-π到π（含边界）范围内y/x的反正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| y | Value | 是 | {double \| string \| Decimal} 除法的被除数。 |
| x | Value | 是 | {double \| string \| Decimal} 除法的除数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## atanh

```TypeScript
atanh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的双曲正切的倒数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## atanh

```TypeScript
static atanh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正切的倒数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## cbrt

```TypeScript
cbrt(): Decimal
```

返回一个新的Decimal对象，其值是当前Decimal对象的立方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## cbrt

```TypeScript
static cbrt(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的立方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## ceil

```TypeScript
ceil(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal向正无穷方向舍入得到的结果。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## ceil

```TypeScript
static ceil(n: Value): Decimal
```

返回一个新的Decimal对象，其值为使用ROUND_CEIL将n舍入为整数的结果。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## clamp

```TypeScript
clamp(min: Value, max: Value): Decimal
```

返回一个将Decimal值限制在min到max范围内的Decimal对象。如果值大于max，返回max；如果值小于min，返回min；否则，返回原值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| min | Value | 是 | {double \| string \| Decimal} |
| max | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `min` is out of range. |

## clamp

```TypeScript
static clamp(n: Value, min: Value, max: Value): Decimal
```

返回一个值为将n限制在min到max范围内的Decimal对象。当大于限制的最大值时返回max，小于限制的最小值时返回min，在范围内返回值不变。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |
| min | Value | 是 | {double \| string \| Decimal} |
| max | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `min` is out of range. |

## comparedTo

```TypeScript
comparedTo(n: Value): number
```

Decimal的比较方法。
1 如果此Decimal大于n的值，
-1 如果此Decimal小于n的值，
0 如果两者的值相等，
NaN 如果两者中任一Decimal的值为NaN。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | the number type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## constructor

```TypeScript
constructor(n: Value)
```

Decimal的构造函数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## cos

```TypeScript
cos(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的余弦值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## cos

```TypeScript
static cos(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的余弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## cosh

```TypeScript
cosh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的双曲余弦值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## cosh

```TypeScript
static cosh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲余弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## decimalPlaces

```TypeScript
decimalPlaces(): number
```

返回Decimal对象的小数位数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | the number type |

## div

```TypeScript
div(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值除以n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## div

```TypeScript
static div(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x除以y的商。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | Value | 是 | {double \| string \| Decimal} |
| y | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## dividedToIntegerBy

```TypeScript
dividedToIntegerBy(n: Value): Decimal
```

返回该Decimal除以n后获得的整数部分。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## equals

```TypeScript
equals(n: Value): boolean
```

返回此Decimal是否等于比较值n，相等返回true，否则返回false。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## exp

```TypeScript
exp(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的自然指数（即以e为底，此Decimal值为指数的幂）。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## exp

```TypeScript
static exp(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的自然指数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## floor

```TypeScript
floor(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal向负无穷方向舍入得到的结果。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## floor

```TypeScript
static floor(n: Value): Decimal
```

返回一个新的Decimal对象，其值为使用ROUND_FLOOR将n舍入为整数的结果。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## greaterThan

```TypeScript
greaterThan(n: Value): boolean
```

返回此Decimal是否大于比较值n，大于返回true，否则返回false。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(n: Value): boolean
```

返回此Decimal是否大于等于比较值n，大于等于返回true，否则返回false。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## hypot

```TypeScript
static hypot(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值是参数平方和的平方根。无入参时默认返回0。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value[] | 是 | {double \| string \| Decimal} Decimal |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## isFinite

```TypeScript
isFinite(): boolean
```

返回此Decimal是否为有限值，是有限值返回true，否则返回false。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

## isInteger

```TypeScript
isInteger(): boolean
```

返回此Decimal是否为整数，是整数返回true，否则返回false。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

## isNaN

```TypeScript
isNaN(): boolean
```

返回此Decimal是否为无效值（NaN），是NaN返回true，否则返回false。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

## isNegative

```TypeScript
isNegative(): boolean
```

返回此Decimal是否为负数（区分正负零），是负数返回true，否则返回false。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

## isPositive

```TypeScript
isPositive(): boolean
```

返回此Decimal是否为正数（区分正负零），是正数返回true，否则返回false。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

## isZero

```TypeScript
isZero(): boolean
```

返回此Decimal是否为0或是-0，是返回true，否则返回false。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

## lessThan

```TypeScript
lessThan(n: Value): boolean
```

返回此Decimal是否小于比较值n，小于返回true，否则返回false。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(n: Value): boolean
```

返回此Decimal是否小于等于比较值n，小于等于返回true，否则返回false。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## ln

```TypeScript
ln(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的自然对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## ln

```TypeScript
static ln(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的自然对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## log

```TypeScript
log(n: Value): Decimal
```

返回一个对数运算后的Decimal对象，其值是以n为底的对数值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## log

```TypeScript
static log(n: Value, base: Value): Decimal
```

返回一个新的Decimal对象，其值是以base为底n的对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |
| base | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## log10

```TypeScript
static log10(n: Value): Decimal
```

返回一个新的Decimal对象，其值是以10为底n的对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## log2

```TypeScript
static log2(n: Value): Decimal
```

返回一个新的Decimal对象，其值是以2为底n的对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## max

```TypeScript
static max(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值是所有参数中的最大值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value[] | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## min

```TypeScript
static min(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值是所有参数中的最小值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value[] | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## mod

```TypeScript
mod(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值除以n后的模。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## mod

```TypeScript
static mod(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值是x除以y的模。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | Value | 是 | {double \| string \| Decimal} |
| y | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## mul

```TypeScript
mul(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值乘以n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## mul

```TypeScript
static mul(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x乘以y的积。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | Value | 是 | {double \| string \| Decimal} |
| y | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## negate

```TypeScript
negate(): Decimal
```

返回一个新的Decimal对象，其值将此Decimal的值乘以-1。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## pow

```TypeScript
pow(n: Value): Decimal
```

返回一个新的Decimal对象，其值是这个Decimal值的n次幂。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## pow

```TypeScript
static pow(base: Value, exponent: Value): Decimal
```

返回一个新的Decimal对象，其值为base的exponent次幂。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| base | Value | 是 | {double \| string \| Decimal} 幂运算的底数的值。 |
| exponent | Value | 是 | {double \| string \| Decimal} 幂运算的幂的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## precision

```TypeScript
precision(): number
```

返回Decimal对象的有效数字位数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | the number type |

## precision

```TypeScript
precision(includeZeros: boolean | number): number
```

返回Decimal对象的有效数字位数，可通过includeZeros判断是否计算整数部分的尾随零。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| includeZeros | boolean \| number | 是 | 是否计算整数部分尾随零。true或1表示计算，false或0表示不计算。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | the number type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `includeZeros` is out of range. |

## random

```TypeScript
static random(): Decimal
```

返回一个新的Decimal对象，其值为大于等于0且小于1的随机值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200061](../errorcode-utils.md#10200061-加密方法不可用) | Crypto unavailable |

## random

```TypeScript
static random(significantDigits: number): Decimal
```

返回一个新的Decimal对象，其值为大于等于0且小于1的随机值，并保留significantDigits位有效数字（若产生尾随零则可能少于该位数）。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | {number} 随机值保留的有效数字。取值范围为[0, 1e9]的整数。[since 12 - 17] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200061](../errorcode-utils.md#10200061-加密方法不可用) | Crypto unavailable |

## round

```TypeScript
static round(n: Value): Decimal
```

返回一个新的Decimal对象，其值是使用rounding舍入模式将n舍入为整数的结果。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## set

```TypeScript
static set(config: DecimalConfig): void
```

用于设置Decimal的配置属性，通过set设置的属性是全局生效的。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | DecimalConfig | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `DecimalConfig.properties` is out of range. |
| [10200061](../errorcode-utils.md#10200061-加密方法不可用) | Crypto unavailable |

## sign

```TypeScript
static sign(n: Value): number
```

根据参数n的值返回对应的符号：
1 如果 n > 0，
-1 如果 n < 0，
0 如果 n 为 0，
-0 如果 n 为 -0，
NaN 其他情况

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type<br>**适用版本：** 12 - 17 |
| number | the Decimal type<br>**适用版本：** 18+ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sin

```TypeScript
sin(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的正弦值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## sin

```TypeScript
static sin(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的正弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sinh

```TypeScript
sinh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的双曲正弦值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## sinh

```TypeScript
static sinh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sqrt

```TypeScript
sqrt(): Decimal
```

返回一个新的Decimal对象，其值是当前Decimal的平方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## sqrt

```TypeScript
static sqrt(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的平方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sub

```TypeScript
sub(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值减去n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sub

```TypeScript
static sub(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x减y的差。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | Value | 是 | {double \| string \| Decimal} |
| y | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sum

```TypeScript
static sum(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值为参数的和。按照precision设置有效位数，按照rounding设置舍入模式。

仅对结果进行舍入，不对中间计算结果进行舍入。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value[] | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## tan

```TypeScript
tan(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的正切值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## tan

```TypeScript
static tan(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## tanh

```TypeScript
tanh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的双曲正切值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## tanh

```TypeScript
static tanh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## toBinary

```TypeScript
toBinary(): string
```

将Decimal转换为二进制表示的字符串。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toBinary

```TypeScript
toBinary(significantDigits: number): string
```

将Decimal转换为二进制表示的字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits` is out of range. |

## toBinary

```TypeScript
toBinary(significantDigits: number, rounding: Rounding): string
```

将Decimal转换为二进制表示的字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | Rounding | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits \| rounding` is out of range. |

## toDecimalPlaces

```TypeScript
toDecimalPlaces(): Decimal
```

返回一个保留小数点后指定位数的Decimal对象，不进行小数的取舍。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## toDecimalPlaces

```TypeScript
toDecimalPlaces(decimalPlaces: number): Decimal
```

返回一个保留小数点后指定位数的Decimal对象，可按照decimalPlaces设置小数位数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | number | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `decimalPlaces` is out of range. |

## toDecimalPlaces

```TypeScript
toDecimalPlaces(decimalPlaces: number, rounding: Rounding): Decimal
```

返回一个保留小数点后指定位数的Decimal对象，可按照decimalPlaces设置小数位数，可按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | number | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |
| rounding | Rounding | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `decimalPlaces \| rounding` is out of range. |

## toExponential

```TypeScript
toExponential(): string
```

将数值转换为指数表示法的字符串，不进行小数部分的舍入。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toExponential

```TypeScript
toExponential(decimalPlaces: number): string
```

将数值转换为指数表示法的字符串，可按照decimalPlaces设置小数位数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | number | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `decimalPlaces` is out of range. |

## toExponential

```TypeScript
toExponential(decimalPlaces: number, rounding: Rounding): string
```

将数值转换为指数表示法的字符串，可按照decimalPlaces设置小数位数，可按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | number | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |
| rounding | Rounding | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `decimalPlaces \| rounding` is out of range. |

## toFixed

```TypeScript
toFixed(): string
```

将数值转换为十进制定点模式表示的字符串，不进行小数的取舍。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toFixed

```TypeScript
toFixed(decimalPlaces: number): string
```

将数值转换为十进制定点模式表示的字符串，可按照decimalPlaces设置小数位数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本18+：SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | number | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `decimalPlaces` is out of range. |

## toFixed

```TypeScript
toFixed(decimalPlaces: number, rounding: Rounding): string
```

将数值转换为十进制定点模式表示的字符串，可按照decimalPlaces设置小数位数，可按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | number | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |
| rounding | Rounding | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `decimalPlaces \| rounding` is out of range. |

## toFraction

```TypeScript
toFraction(): Decimal[]
```

转换为分数表示的数。返回一个长度固定为2的Decimal数组，分别表示分子和分母。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal[] | the Decimal[] type |

## toFraction

```TypeScript
toFraction(maxDenominator: Value): Decimal[]
```

转换为分数表示的数，可以通过maxDenominator设置最大分母值。返回一个长度固定为2的Decimal数组，分别表示分子和分母。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxDenominator | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal[] | the Decimal[] type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## toHexadecimal

```TypeScript
toHexadecimal(): string
```

将Decimal转换为十六进制表示的字符串。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toHexadecimal

```TypeScript
toHexadecimal(significantDigits: number): string
```

将Decimal转换为十六进制表示的字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits` is out of range. |

## toHexadecimal

```TypeScript
toHexadecimal(significantDigits: number, rounding: Rounding): string
```

将Decimal转换为十六进制表示的字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | Rounding | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits \| rounding` is out of range. |

## toNearest

```TypeScript
toNearest(n: Value): Decimal
```

返回一个新的Decimal对象，此Decimal为指定值n乘以一个倍数后与原Decimal最接近的值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## toNearest

```TypeScript
toNearest(n: Value, rounding: Rounding): Decimal
```

返回一个新的Decimal对象，此Decimal为指定值n乘以一个倍数后与原Decimal最接近的值，可按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |
| rounding | Rounding | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `rounding` is out of range. |

## toNumber

```TypeScript
toNumber(): number
```

将值转换为number类型。零保留其符号。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | the number type |

## toOctal

```TypeScript
toOctal(): string
```

将Decimal转换为八进制表示的字符串。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toOctal

```TypeScript
toOctal(significantDigits: number): string
```

将Decimal转换为八进制表示的字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits` is out of range. |

## toOctal

```TypeScript
toOctal(significantDigits: number, rounding: Rounding): string
```

将Decimal转换为八进制表示的字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | {double \| string \| Decimal} |
| rounding | Rounding | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits \| rounding` is out of range. |

## toPrecision

```TypeScript
toPrecision(): string
```

将Decimal对象转换为字符串。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toPrecision

```TypeScript
toPrecision(significantDigits: number): string
```

将数值转换为字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits` is out of range. |

## toPrecision

```TypeScript
toPrecision(significantDigits: number, rounding: Rounding): string
```

将数值转换为字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | Rounding | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits \| rounding` is out of range. |

## toSignificantDigits

```TypeScript
toSignificantDigits(): Decimal
```

返回一个按照保留有效数字转换的Decimal对象。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## toSignificantDigits

```TypeScript
toSignificantDigits(significantDigits: number): Decimal
```

返回一个按照保留有效数字转换的Decimal对象，可按照significantDigits设置有效数字。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits` is out of range. |

## toSignificantDigits

```TypeScript
toSignificantDigits(significantDigits: number, rounding: Rounding): Decimal
```

返回一个按照保留有效数字转换的Decimal对象，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | Rounding | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits \| rounding` is out of range. |

## toString

```TypeScript
toString(): string
```

返回一个字符串，表示此 Decimal 的值。如果此 Decimal 的正指数等于或大于toExpPos，或负指数等于或小于toExpNeg，则将返回指数表示法。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## trunc

```TypeScript
trunc(): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal截断为整数部分。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

## trunc

```TypeScript
static trunc(n: Value): Decimal
```

返回一个新的Decimal对象，其值为将n截断为整数的结果。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | Value | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Decimal | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## valueOf

```TypeScript
valueOf(): string
```

返回一个字符串，表示此 Decimal 的值。与toString不同，负零将包含负号。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## EUCLIDEAN

```TypeScript
static readonly EUCLIDEAN : 9
```

非舍入模式，参见modulo

**类型：** 9

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ROUND_CEILING

```TypeScript
static readonly ROUND_CEILING : 2
```

向正无穷方向舍入

**类型：** 2

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ROUND_DOWN

```TypeScript
static readonly ROUND_DOWN : 1
```

向靠近零的方向舍入

**类型：** 1

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ROUND_FLOOR

```TypeScript
static readonly ROUND_FLOOR : 3
```

向负无穷方向舍入

**类型：** 3

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_CEILING

```TypeScript
static readonly ROUND_HALF_CEILING : 7
```

向最近的邻值舍入。如果距离相等，则向正无穷方向舍入

**类型：** 7

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_DOWN

```TypeScript
static readonly ROUND_HALF_DOWN : 5
```

向最近的邻值舍入。如果距离相等，则向靠近零的方向舍入

**类型：** 5

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_EVEN

```TypeScript
static readonly ROUND_HALF_EVEN : 6
```

向最近的邻值舍入。如果距离相等，则向偶数邻值舍入

**类型：** 6

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_FLOOR

```TypeScript
static readonly ROUND_HALF_FLOOR : 8
```

向最近的邻值舍入。如果距离相等，则向负无穷方向舍入

**类型：** 8

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_UP

```TypeScript
static readonly ROUND_HALF_UP : 4
```

向最近的邻值舍入。如果距离相等，则向远离零的方向舍入

**类型：** 4

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ROUND_UP

```TypeScript
static readonly ROUND_UP : 0
```

向远离零的方向舍入

**类型：** 0

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## d

```TypeScript
readonly d: number[]
```

digits：表示Decimal数整数部分和小数部分的数组。

**类型：** number[]

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## e

```TypeScript
get e(): number
```

exponent：表示Decimal数的十进制指数。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## s

```TypeScript
get s(): number
```

sign：表示Decimal数的符号位，0表示正数，1表示负数。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

