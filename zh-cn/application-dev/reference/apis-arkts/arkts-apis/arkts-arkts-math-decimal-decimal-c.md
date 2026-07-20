# Decimal

任意精度的Decimal类型。

**起始版本：** 12

<!--Device-unnamed-declare class Decimal--><!--Device-unnamed-declare class Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { Decimal } from '@kit.ArkTS';
```

<a id="abs"></a>
## abs

```TypeScript
abs(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的绝对值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-abs(): Decimal--><!--Device-Decimal-abs(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="abs-1"></a>
## abs

```TypeScript
static abs(n: Value): Decimal
```

返回一个新的Decimal对象，Decimal的值为参数n的绝对值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static abs(n: Value): Decimal--><!--Device-Decimal-static abs(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="acos"></a>
## acos

```TypeScript
acos(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的反余弦值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-acos(): Decimal--><!--Device-Decimal-acos(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="acos-1"></a>
## acos

```TypeScript
static acos(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的反余弦值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static acos(n: Value): Decimal--><!--Device-Decimal-static acos(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="acosh"></a>
## acosh

```TypeScript
acosh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的双曲余弦的倒数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-acosh(): Decimal--><!--Device-Decimal-acosh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="acosh-1"></a>
## acosh

```TypeScript
static acosh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲余弦的倒数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static acosh(n: Value): Decimal--><!--Device-Decimal-static acosh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="add"></a>
## add

```TypeScript
add(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值加上n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-add(n: Value): Decimal--><!--Device-Decimal-add(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="add-1"></a>
## add

```TypeScript
static add(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x加y的和。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static add(x: Value, y: Value): Decimal--><!--Device-Decimal-static add(x: Value, y: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |
| y | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="asin"></a>
## asin

```TypeScript
asin(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的反正弦值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-asin(): Decimal--><!--Device-Decimal-asin(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="asin-1"></a>
## asin

```TypeScript
static asin(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的反正弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static asin(n: Value): Decimal--><!--Device-Decimal-static asin(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="asinh"></a>
## asinh

```TypeScript
asinh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的双曲正弦的倒数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-asinh(): Decimal--><!--Device-Decimal-asinh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="asinh-1"></a>
## asinh

```TypeScript
static asinh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正弦的倒数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static asinh(n: Value): Decimal--><!--Device-Decimal-static asinh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="atan"></a>
## atan

```TypeScript
atan(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的反正切值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-atan(): Decimal--><!--Device-Decimal-atan(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="atan-1"></a>
## atan

```TypeScript
static atan(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的反正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static atan(n: Value): Decimal--><!--Device-Decimal-static atan(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="atan2"></a>
## atan2

```TypeScript
static atan2(y: Value, x: Value): Decimal
```

返回一个新的Decimal对象，其值是-π到π（含边界）范围内y/x的反正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static atan2(y: Value, x: Value): Decimal--><!--Device-Decimal-static atan2(y: Value, x: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| y | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} 除法的被除数。 |
| x | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} 除法的除数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="atanh"></a>
## atanh

```TypeScript
atanh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的双曲正切的倒数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-atanh(): Decimal--><!--Device-Decimal-atanh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="atanh-1"></a>
## atanh

```TypeScript
static atanh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正切的倒数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static atanh(n: Value): Decimal--><!--Device-Decimal-static atanh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="cbrt"></a>
## cbrt

```TypeScript
cbrt(): Decimal
```

返回一个新的Decimal对象，其值是当前Decimal对象的立方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-cbrt(): Decimal--><!--Device-Decimal-cbrt(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="cbrt-1"></a>
## cbrt

```TypeScript
static cbrt(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的立方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static cbrt(n: Value): Decimal--><!--Device-Decimal-static cbrt(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="ceil"></a>
## ceil

```TypeScript
ceil(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal向正无穷方向舍入得到的结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-ceil(): Decimal--><!--Device-Decimal-ceil(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="ceil-1"></a>
## ceil

```TypeScript
static ceil(n: Value): Decimal
```

返回一个新的Decimal对象，其值为使用ROUND_CEIL将n舍入为整数的结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static ceil(n: Value): Decimal--><!--Device-Decimal-static ceil(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="clamp"></a>
## clamp

```TypeScript
clamp(min: Value, max: Value): Decimal
```

返回一个将Decimal值限制在min到max范围内的Decimal对象。如果值大于max，返回max；如果值小于min，返回min；否则，返回原值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-clamp(min: Value, max: Value): Decimal--><!--Device-Decimal-clamp(min: Value, max: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| min | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |
| max | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `min` is out of range. |

<a id="clamp-1"></a>
## clamp

```TypeScript
static clamp(n: Value, min: Value, max: Value): Decimal
```

返回一个值为将n限制在min到max范围内的Decimal对象。当大于限制的最大值时返回max，小于限制的最小值时返回min，在范围内返回值不变。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static clamp(n: Value, min: Value, max: Value): Decimal--><!--Device-Decimal-static clamp(n: Value, min: Value, max: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |
| min | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |
| max | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `min` is out of range. |

<a id="comparedto"></a>
## comparedTo

```TypeScript
comparedTo(n: Value): number
```

Decimal的比较方法。1 如果此Decimal大于n的值，  
-1 如果此Decimal小于n的值，0 如果两者的值相等，NaN 如果两者中任一Decimal的值为NaN。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-comparedTo(n: Value): double--><!--Device-Decimal-comparedTo(n: Value): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | the number type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="constructor"></a>
## constructor

```TypeScript
constructor(n: Value)
```

Decimal的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-constructor(n: Value)--><!--Device-Decimal-constructor(n: Value)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="cos"></a>
## cos

```TypeScript
cos(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的余弦值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-cos(): Decimal--><!--Device-Decimal-cos(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="cos-1"></a>
## cos

```TypeScript
static cos(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的余弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static cos(n: Value): Decimal--><!--Device-Decimal-static cos(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="cosh"></a>
## cosh

```TypeScript
cosh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的双曲余弦值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-cosh(): Decimal--><!--Device-Decimal-cosh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="cosh-1"></a>
## cosh

```TypeScript
static cosh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲余弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static cosh(n: Value): Decimal--><!--Device-Decimal-static cosh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="decimalplaces"></a>
## decimalPlaces

```TypeScript
decimalPlaces(): number
```

返回Decimal对象的小数位数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-decimalPlaces(): double--><!--Device-Decimal-decimalPlaces(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | the number type |

<a id="div"></a>
## div

```TypeScript
div(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值除以n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-div(n: Value): Decimal--><!--Device-Decimal-div(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="div-1"></a>
## div

```TypeScript
static div(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x除以y的商。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static div(x: Value, y: Value): Decimal--><!--Device-Decimal-static div(x: Value, y: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |
| y | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="dividedtointegerby"></a>
## dividedToIntegerBy

```TypeScript
dividedToIntegerBy(n: Value): Decimal
```

返回该Decimal除以n后获得的整数部分。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-dividedToIntegerBy(n: Value): Decimal--><!--Device-Decimal-dividedToIntegerBy(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="equals"></a>
## equals

```TypeScript
equals(n: Value): boolean
```

返回此Decimal是否等于比较值n，相等返回true，否则返回false。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-equals(n: Value): boolean--><!--Device-Decimal-equals(n: Value): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="exp"></a>
## exp

```TypeScript
exp(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的自然指数（即以e为底，此Decimal值为指数的幂）。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-exp(): Decimal--><!--Device-Decimal-exp(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="exp-1"></a>
## exp

```TypeScript
static exp(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的自然指数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static exp(n: Value): Decimal--><!--Device-Decimal-static exp(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="floor"></a>
## floor

```TypeScript
floor(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal向负无穷方向舍入得到的结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-floor(): Decimal--><!--Device-Decimal-floor(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="floor-1"></a>
## floor

```TypeScript
static floor(n: Value): Decimal
```

返回一个新的Decimal对象，其值为使用ROUND_FLOOR将n舍入为整数的结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static floor(n: Value): Decimal--><!--Device-Decimal-static floor(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="greaterthan"></a>
## greaterThan

```TypeScript
greaterThan(n: Value): boolean
```

返回此Decimal是否大于比较值n，大于返回true，否则返回false。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-greaterThan(n: Value): boolean--><!--Device-Decimal-greaterThan(n: Value): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="greaterthanorequalto"></a>
## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(n: Value): boolean
```

返回此Decimal是否大于等于比较值n，大于等于返回true，否则返回false。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-greaterThanOrEqualTo(n: Value): boolean--><!--Device-Decimal-greaterThanOrEqualTo(n: Value): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="hypot"></a>
## hypot

```TypeScript
static hypot(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值是参数平方和的平方根。无入参时默认返回0。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static hypot(...n: Value[]): Decimal--><!--Device-Decimal-static hypot(...n: Value[]): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md)[] | 是 | {double \| string \| Decimal} Decimal |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="isfinite"></a>
## isFinite

```TypeScript
isFinite(): boolean
```

返回此Decimal是否为有限值，是有限值返回true，否则返回false。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isFinite(): boolean--><!--Device-Decimal-isFinite(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

<a id="isinteger"></a>
## isInteger

```TypeScript
isInteger(): boolean
```

返回此Decimal是否为整数，是整数返回true，否则返回false。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isInteger(): boolean--><!--Device-Decimal-isInteger(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

<a id="isnan"></a>
## isNaN

```TypeScript
isNaN(): boolean
```

返回此Decimal是否为无效值（NaN），是NaN返回true，否则返回false。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isNaN(): boolean--><!--Device-Decimal-isNaN(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

<a id="isnegative"></a>
## isNegative

```TypeScript
isNegative(): boolean
```

返回此Decimal是否为负数（区分正负零），是负数返回true，否则返回false。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isNegative(): boolean--><!--Device-Decimal-isNegative(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

<a id="ispositive"></a>
## isPositive

```TypeScript
isPositive(): boolean
```

返回此Decimal是否为正数（区分正负零），是正数返回true，否则返回false。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isPositive(): boolean--><!--Device-Decimal-isPositive(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

<a id="iszero"></a>
## isZero

```TypeScript
isZero(): boolean
```

返回此Decimal是否为0或是-0，是返回true，否则返回false。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isZero(): boolean--><!--Device-Decimal-isZero(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

<a id="lessthan"></a>
## lessThan

```TypeScript
lessThan(n: Value): boolean
```

返回此Decimal是否小于比较值n，小于返回true，否则返回false。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-lessThan(n: Value): boolean--><!--Device-Decimal-lessThan(n: Value): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="lessthanorequalto"></a>
## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(n: Value): boolean
```

返回此Decimal是否小于等于比较值n，小于等于返回true，否则返回false。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-lessThanOrEqualTo(n: Value): boolean--><!--Device-Decimal-lessThanOrEqualTo(n: Value): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="ln"></a>
## ln

```TypeScript
ln(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的自然对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-ln(): Decimal--><!--Device-Decimal-ln(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="ln-1"></a>
## ln

```TypeScript
static ln(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的自然对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static ln(n: Value): Decimal--><!--Device-Decimal-static ln(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="log"></a>
## log

```TypeScript
log(n: Value): Decimal
```

返回一个对数运算后的Decimal对象，其值是以n为底的对数值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-log(n: Value): Decimal--><!--Device-Decimal-log(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="log-1"></a>
## log

```TypeScript
static log(n: Value, base: Value): Decimal
```

返回一个新的Decimal对象，其值是以base为底n的对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static log(n: Value, base: Value): Decimal--><!--Device-Decimal-static log(n: Value, base: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |
| base | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="log10"></a>
## log10

```TypeScript
static log10(n: Value): Decimal
```

返回一个新的Decimal对象，其值是以10为底n的对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static log10(n: Value): Decimal--><!--Device-Decimal-static log10(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="log2"></a>
## log2

```TypeScript
static log2(n: Value): Decimal
```

返回一个新的Decimal对象，其值是以2为底n的对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static log2(n: Value): Decimal--><!--Device-Decimal-static log2(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="max"></a>
## max

```TypeScript
static max(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值是所有参数中的最大值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static max(...n: Value[]): Decimal--><!--Device-Decimal-static max(...n: Value[]): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md)[] | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="min"></a>
## min

```TypeScript
static min(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值是所有参数中的最小值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static min(...n: Value[]): Decimal--><!--Device-Decimal-static min(...n: Value[]): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md)[] | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="mod"></a>
## mod

```TypeScript
mod(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值除以n后的模。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-mod(n: Value): Decimal--><!--Device-Decimal-mod(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="mod-1"></a>
## mod

```TypeScript
static mod(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值是x除以y的模。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static mod(x: Value, y: Value): Decimal--><!--Device-Decimal-static mod(x: Value, y: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |
| y | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="mul"></a>
## mul

```TypeScript
mul(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值乘以n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-mul(n: Value): Decimal--><!--Device-Decimal-mul(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="mul-1"></a>
## mul

```TypeScript
static mul(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x乘以y的积。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static mul(x: Value, y: Value): Decimal--><!--Device-Decimal-static mul(x: Value, y: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |
| y | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="negate"></a>
## negate

```TypeScript
negate(): Decimal
```

返回一个新的Decimal对象，其值将此Decimal的值乘以-1。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-negate(): Decimal--><!--Device-Decimal-negate(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="pow"></a>
## pow

```TypeScript
pow(n: Value): Decimal
```

返回一个新的Decimal对象，其值是这个Decimal值的n次幂。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-pow(n: Value): Decimal--><!--Device-Decimal-pow(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="pow-1"></a>
## pow

```TypeScript
static pow(base: Value, exponent: Value): Decimal
```

返回一个新的Decimal对象，其值为base的exponent次幂。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static pow(base: Value, exponent: Value): Decimal--><!--Device-Decimal-static pow(base: Value, exponent: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| base | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} 幂运算的底数的值。 |
| exponent | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} 幂运算的幂的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

<a id="precision"></a>
## precision

```TypeScript
precision(): number
```

返回Decimal对象的有效数字位数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-precision(): double--><!--Device-Decimal-precision(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | the number type |

<a id="precision-1"></a>
## precision

```TypeScript
precision(includeZeros: boolean | number): number
```

返回Decimal对象的有效数字位数，可通过includeZeros判断是否计算整数部分的尾随零。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-precision(includeZeros: boolean | int): double--><!--Device-Decimal-precision(includeZeros: boolean | int): double-End-->

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

<a id="random"></a>
## random

```TypeScript
static random(): Decimal
```

返回一个新的Decimal对象，其值为大于等于0且小于1的随机值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static random(): Decimal--><!--Device-Decimal-static random(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200061](../errorcode-utils.md#10200061-加密方法不可用) | Crypto unavailable |

<a id="random-1"></a>
## random

```TypeScript
static random(significantDigits: number): Decimal
```

返回一个新的Decimal对象，其值为大于等于0且小于1的随机值，并保留significantDigits位有效数字（若产生尾随零则可能少于该位数）。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static random(significantDigits: double): Decimal--><!--Device-Decimal-static random(significantDigits: double): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | {number} 随机值保留的有效数字。取值范围为[0, 1e9]的整数。[since 12 - 17] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200061](../errorcode-utils.md#10200061-加密方法不可用) | Crypto unavailable |

<a id="round"></a>
## round

```TypeScript
static round(n: Value): Decimal
```

返回一个新的Decimal对象，其值是使用rounding舍入模式将n舍入为整数的结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static round(n: Value): Decimal--><!--Device-Decimal-static round(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="set"></a>
## set

```TypeScript
static set(config: DecimalConfig): void
```

用于设置Decimal的配置属性，通过set设置的属性是全局生效的。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static set(config: DecimalConfig): void--><!--Device-Decimal-static set(config: DecimalConfig): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [DecimalConfig](arkts-arkts-math-decimal-decimalconfig-i.md) | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `DecimalConfig.properties` is out of range. |
| [10200061](../errorcode-utils.md#10200061-加密方法不可用) | Crypto unavailable |

<a id="sign"></a>
## sign

```TypeScript
static sign(n: Value): number
```

根据参数n的值返回对应的符号：1 如果 n > 0，  
-1 如果 n < 0，0 如果 n 为 0，  
-0 如果 n 为 -0，NaN 其他情况

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sign(n: Value): double--><!--Device-Decimal-static sign(n: Value): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type<br>**适用版本：** 12 - 17 |
| number | the Decimal type<br>**适用版本：** 18+ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="sin"></a>
## sin

```TypeScript
sin(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的正弦值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-sin(): Decimal--><!--Device-Decimal-sin(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="sin-1"></a>
## sin

```TypeScript
static sin(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的正弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sin(n: Value): Decimal--><!--Device-Decimal-static sin(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="sinh"></a>
## sinh

```TypeScript
sinh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的双曲正弦值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-sinh(): Decimal--><!--Device-Decimal-sinh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="sinh-1"></a>
## sinh

```TypeScript
static sinh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sinh(n: Value): Decimal--><!--Device-Decimal-static sinh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="sqrt"></a>
## sqrt

```TypeScript
sqrt(): Decimal
```

返回一个新的Decimal对象，其值是当前Decimal的平方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-sqrt(): Decimal--><!--Device-Decimal-sqrt(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="sqrt-1"></a>
## sqrt

```TypeScript
static sqrt(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的平方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sqrt(n: Value): Decimal--><!--Device-Decimal-static sqrt(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="sub"></a>
## sub

```TypeScript
sub(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值减去n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-sub(n: Value): Decimal--><!--Device-Decimal-sub(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="sub-1"></a>
## sub

```TypeScript
static sub(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x减y的差。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sub(x: Value, y: Value): Decimal--><!--Device-Decimal-static sub(x: Value, y: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |
| y | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="sum"></a>
## sum

```TypeScript
static sum(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值为参数的和。按照precision设置有效位数，按照rounding设置舍入模式。

仅对结果进行舍入，不对中间计算结果进行舍入。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sum(...n: Value[]): Decimal--><!--Device-Decimal-static sum(...n: Value[]): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md)[] | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="tan"></a>
## tan

```TypeScript
tan(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的正切值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-tan(): Decimal--><!--Device-Decimal-tan(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="tan-1"></a>
## tan

```TypeScript
static tan(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static tan(n: Value): Decimal--><!--Device-Decimal-static tan(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="tanh"></a>
## tanh

```TypeScript
tanh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的双曲正切值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-tanh(): Decimal--><!--Device-Decimal-tanh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="tanh-1"></a>
## tanh

```TypeScript
static tanh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static tanh(n: Value): Decimal--><!--Device-Decimal-static tanh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="tobinary"></a>
## toBinary

```TypeScript
toBinary(): string
```

将Decimal转换为二进制表示的字符串。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toBinary(): string--><!--Device-Decimal-toBinary(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

<a id="tobinary-1"></a>
## toBinary

```TypeScript
toBinary(significantDigits: number): string
```

将Decimal转换为二进制表示的字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toBinary(significantDigits: double): string--><!--Device-Decimal-toBinary(significantDigits: double): string-End-->

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

<a id="tobinary-2"></a>
## toBinary

```TypeScript
toBinary(significantDigits: number, rounding: Rounding): string
```

将Decimal转换为二进制表示的字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toBinary(significantDigits: double, rounding: Rounding): string--><!--Device-Decimal-toBinary(significantDigits: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits \| rounding` is out of range. |

<a id="todecimalplaces"></a>
## toDecimalPlaces

```TypeScript
toDecimalPlaces(): Decimal
```

返回一个保留小数点后指定位数的Decimal对象，不进行小数的取舍。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toDecimalPlaces(): Decimal--><!--Device-Decimal-toDecimalPlaces(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="todecimalplaces-1"></a>
## toDecimalPlaces

```TypeScript
toDecimalPlaces(decimalPlaces: number): Decimal
```

返回一个保留小数点后指定位数的Decimal对象，可按照decimalPlaces设置小数位数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toDecimalPlaces(decimalPlaces: double): Decimal--><!--Device-Decimal-toDecimalPlaces(decimalPlaces: double): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | number | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `decimalPlaces` is out of range. |

<a id="todecimalplaces-2"></a>
## toDecimalPlaces

```TypeScript
toDecimalPlaces(decimalPlaces: number, rounding: Rounding): Decimal
```

返回一个保留小数点后指定位数的Decimal对象，可按照decimalPlaces设置小数位数，可按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toDecimalPlaces(decimalPlaces: double, rounding: Rounding): Decimal--><!--Device-Decimal-toDecimalPlaces(decimalPlaces: double, rounding: Rounding): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | number | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `decimalPlaces \| rounding` is out of range. |

<a id="toexponential"></a>
## toExponential

```TypeScript
toExponential(): string
```

将数值转换为指数表示法的字符串，不进行小数部分的舍入。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toExponential(): string--><!--Device-Decimal-toExponential(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

<a id="toexponential-1"></a>
## toExponential

```TypeScript
toExponential(decimalPlaces: number): string
```

将数值转换为指数表示法的字符串，可按照decimalPlaces设置小数位数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toExponential(decimalPlaces: double): string--><!--Device-Decimal-toExponential(decimalPlaces: double): string-End-->

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

<a id="toexponential-2"></a>
## toExponential

```TypeScript
toExponential(decimalPlaces: number, rounding: Rounding): string
```

将数值转换为指数表示法的字符串，可按照decimalPlaces设置小数位数，可按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toExponential(decimalPlaces: double, rounding: Rounding): string--><!--Device-Decimal-toExponential(decimalPlaces: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | number | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `decimalPlaces \| rounding` is out of range. |

<a id="tofixed"></a>
## toFixed

```TypeScript
toFixed(): string
```

将数值转换为十进制定点模式表示的字符串，不进行小数的取舍。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toFixed(): string--><!--Device-Decimal-toFixed(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

<a id="tofixed-1"></a>
## toFixed

```TypeScript
toFixed(decimalPlaces: number): string
```

将数值转换为十进制定点模式表示的字符串，可按照decimalPlaces设置小数位数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toFixed(decimalPlaces: double): string--><!--Device-Decimal-toFixed(decimalPlaces: double): string-End-->

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

<a id="tofixed-2"></a>
## toFixed

```TypeScript
toFixed(decimalPlaces: number, rounding: Rounding): string
```

将数值转换为十进制定点模式表示的字符串，可按照decimalPlaces设置小数位数，可按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toFixed(decimalPlaces: double, rounding: Rounding): string--><!--Device-Decimal-toFixed(decimalPlaces: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | number | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `decimalPlaces \| rounding` is out of range. |

<a id="tofraction"></a>
## toFraction

```TypeScript
toFraction(): Decimal[]
```

转换为分数表示的数。返回一个长度固定为2的Decimal数组，分别表示分子和分母。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toFraction(): Decimal[]--><!--Device-Decimal-toFraction(): Decimal[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md)[] | the Decimal[] type |

<a id="tofraction-1"></a>
## toFraction

```TypeScript
toFraction(maxDenominator: Value): Decimal[]
```

转换为分数表示的数，可以通过maxDenominator设置最大分母值。返回一个长度固定为2的Decimal数组，分别表示分子和分母。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toFraction(maxDenominator: Value): Decimal[]--><!--Device-Decimal-toFraction(maxDenominator: Value): Decimal[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxDenominator | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md)[] | the Decimal[] type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="tohexadecimal"></a>
## toHexadecimal

```TypeScript
toHexadecimal(): string
```

将Decimal转换为十六进制表示的字符串。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toHexadecimal(): string--><!--Device-Decimal-toHexadecimal(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

<a id="tohexadecimal-1"></a>
## toHexadecimal

```TypeScript
toHexadecimal(significantDigits: number): string
```

将Decimal转换为十六进制表示的字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toHexadecimal(significantDigits: double): string--><!--Device-Decimal-toHexadecimal(significantDigits: double): string-End-->

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

<a id="tohexadecimal-2"></a>
## toHexadecimal

```TypeScript
toHexadecimal(significantDigits: number, rounding: Rounding): string
```

将Decimal转换为十六进制表示的字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toHexadecimal(significantDigits: double, rounding: Rounding): string--><!--Device-Decimal-toHexadecimal(significantDigits: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits \| rounding` is out of range. |

<a id="tonearest"></a>
## toNearest

```TypeScript
toNearest(n: Value): Decimal
```

返回一个新的Decimal对象，此Decimal为指定值n乘以一个倍数后与原Decimal最接近的值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toNearest(n: Value): Decimal--><!--Device-Decimal-toNearest(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="tonearest-1"></a>
## toNearest

```TypeScript
toNearest(n: Value, rounding: Rounding): Decimal
```

返回一个新的Decimal对象，此Decimal为指定值n乘以一个倍数后与原Decimal最接近的值，可按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toNearest(n: Value, rounding: Rounding): Decimal--><!--Device-Decimal-toNearest(n: Value, rounding: Rounding): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `rounding` is out of range. |

<a id="tonumber"></a>
## toNumber

```TypeScript
toNumber(): number
```

将值转换为number类型。零保留其符号。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toNumber(): double--><!--Device-Decimal-toNumber(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | the number type |

<a id="tooctal"></a>
## toOctal

```TypeScript
toOctal(): string
```

将Decimal转换为八进制表示的字符串。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toOctal(): string--><!--Device-Decimal-toOctal(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

<a id="tooctal-1"></a>
## toOctal

```TypeScript
toOctal(significantDigits: number): string
```

将Decimal转换为八进制表示的字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toOctal(significantDigits: double): string--><!--Device-Decimal-toOctal(significantDigits: double): string-End-->

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

<a id="tooctal-2"></a>
## toOctal

```TypeScript
toOctal(significantDigits: number, rounding: Rounding): string
```

将Decimal转换为八进制表示的字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toOctal(significantDigits: double, rounding: Rounding): string--><!--Device-Decimal-toOctal(significantDigits: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | {double \| string \| Decimal} |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits \| rounding` is out of range. |

<a id="toprecision"></a>
## toPrecision

```TypeScript
toPrecision(): string
```

将Decimal对象转换为字符串。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toPrecision(): string--><!--Device-Decimal-toPrecision(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

<a id="toprecision-1"></a>
## toPrecision

```TypeScript
toPrecision(significantDigits: number): string
```

将数值转换为字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toPrecision(significantDigits: double): string--><!--Device-Decimal-toPrecision(significantDigits: double): string-End-->

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

<a id="toprecision-2"></a>
## toPrecision

```TypeScript
toPrecision(significantDigits: number, rounding: Rounding): string
```

将数值转换为字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toPrecision(significantDigits: double, rounding: Rounding): string--><!--Device-Decimal-toPrecision(significantDigits: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits \| rounding` is out of range. |

<a id="tosignificantdigits"></a>
## toSignificantDigits

```TypeScript
toSignificantDigits(): Decimal
```

返回一个按照保留有效数字转换的Decimal对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toSignificantDigits(): Decimal--><!--Device-Decimal-toSignificantDigits(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="tosignificantdigits-1"></a>
## toSignificantDigits

```TypeScript
toSignificantDigits(significantDigits: number): Decimal
```

返回一个按照保留有效数字转换的Decimal对象，可按照significantDigits设置有效数字。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toSignificantDigits(significantDigits: double): Decimal--><!--Device-Decimal-toSignificantDigits(significantDigits: double): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits` is out of range. |

<a id="tosignificantdigits-2"></a>
## toSignificantDigits

```TypeScript
toSignificantDigits(significantDigits: number, rounding: Rounding): Decimal
```

返回一个按照保留有效数字转换的Decimal对象，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toSignificantDigits(significantDigits: double, rounding: Rounding): Decimal--><!--Device-Decimal-toSignificantDigits(significantDigits: double, rounding: Rounding): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | number | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | [Rounding](arkts-arkts-rounding-t.md) | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../errorcode-utils.md#10200001-参数范围越界错误) | The value of `significantDigits \| rounding` is out of range. |

<a id="tostring"></a>
## toString

```TypeScript
toString(): string
```

返回一个字符串，表示此 Decimal 的值。如果此 Decimal 的正指数等于或大于toExpPos，或负指数等于或小于toExpNeg，则将返回指数表示法。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toString(): string--><!--Device-Decimal-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

<a id="trunc"></a>
## trunc

```TypeScript
trunc(): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal截断为整数部分。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-trunc(): Decimal--><!--Device-Decimal-trunc(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

<a id="trunc-1"></a>
## trunc

```TypeScript
static trunc(n: Value): Decimal
```

返回一个新的Decimal对象，其值为将n截断为整数的结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static trunc(n: Value): Decimal--><!--Device-Decimal-static trunc(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | [Value](../../apis-asset-store-kit/arkts-apis/arkts-assetstore-asset-value-t.md) | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Decimal](arkts-arkts-math-decimal-decimal-c.md) | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

<a id="valueof"></a>
## valueOf

```TypeScript
valueOf(): string
```

返回一个字符串，表示此 Decimal 的值。与toString不同，负零将包含负号。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-valueOf(): string--><!--Device-Decimal-valueOf(): string-End-->

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly EUCLIDEAN : 9--><!--Device-Decimal-static readonly EUCLIDEAN : 9-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_CEILING

```TypeScript
static readonly ROUND_CEILING : 2
```

向正无穷方向舍入

**类型：** 2

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_CEILING : 2--><!--Device-Decimal-static readonly ROUND_CEILING : 2-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_DOWN

```TypeScript
static readonly ROUND_DOWN : 1
```

向靠近零的方向舍入

**类型：** 1

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_DOWN : 1--><!--Device-Decimal-static readonly ROUND_DOWN : 1-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_FLOOR

```TypeScript
static readonly ROUND_FLOOR : 3
```

向负无穷方向舍入

**类型：** 3

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_FLOOR : 3--><!--Device-Decimal-static readonly ROUND_FLOOR : 3-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_CEILING

```TypeScript
static readonly ROUND_HALF_CEILING : 7
```

向最近的邻值舍入。如果距离相等，则向正无穷方向舍入

**类型：** 7

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_HALF_CEILING : 7--><!--Device-Decimal-static readonly ROUND_HALF_CEILING : 7-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_DOWN

```TypeScript
static readonly ROUND_HALF_DOWN : 5
```

向最近的邻值舍入。如果距离相等，则向靠近零的方向舍入

**类型：** 5

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_HALF_DOWN : 5--><!--Device-Decimal-static readonly ROUND_HALF_DOWN : 5-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_EVEN

```TypeScript
static readonly ROUND_HALF_EVEN : 6
```

向最近的邻值舍入。如果距离相等，则向偶数邻值舍入

**类型：** 6

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_HALF_EVEN : 6--><!--Device-Decimal-static readonly ROUND_HALF_EVEN : 6-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_FLOOR

```TypeScript
static readonly ROUND_HALF_FLOOR : 8
```

向最近的邻值舍入。如果距离相等，则向负无穷方向舍入

**类型：** 8

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_HALF_FLOOR : 8--><!--Device-Decimal-static readonly ROUND_HALF_FLOOR : 8-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_UP

```TypeScript
static readonly ROUND_HALF_UP : 4
```

向最近的邻值舍入。如果距离相等，则向远离零的方向舍入

**类型：** 4

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_HALF_UP : 4--><!--Device-Decimal-static readonly ROUND_HALF_UP : 4-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_UP

```TypeScript
static readonly ROUND_UP : 0
```

向远离零的方向舍入

**类型：** 0

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_UP : 0--><!--Device-Decimal-static readonly ROUND_UP : 0-End-->

**系统能力：** SystemCapability.Utils.Lang

## d

```TypeScript
readonly d: number[]
```

digits：表示Decimal数整数部分和小数部分的数组。

**类型：** number[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-readonly d: number[]--><!--Device-Decimal-readonly d: number[]-End-->

**系统能力：** SystemCapability.Utils.Lang

## e

```TypeScript
get e(): number
```

exponent：表示Decimal数的十进制指数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-get e(): double--><!--Device-Decimal-get e(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

## s

```TypeScript
get s(): number
```

sign：表示Decimal数的符号位，0表示正数，1表示负数。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-get s(): double--><!--Device-Decimal-get s(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

