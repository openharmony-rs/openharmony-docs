# Decimal

任意精度的Decimal类型。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare class Decimal--><!--Device-unnamed-declare class Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

## abs

```TypeScript
abs(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的绝对值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-abs(): Decimal--><!--Device-Decimal-abs(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## abs

```TypeScript
static abs(n: Value): Decimal
```

返回一个新的Decimal对象，Decimal的值为参数n的绝对值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static abs(n: Value): Decimal--><!--Device-Decimal-static abs(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## acos

```TypeScript
acos(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的反余弦值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-acos(): Decimal--><!--Device-Decimal-acos(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## acos

```TypeScript
static acos(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的反余弦值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static acos(n: Value): Decimal--><!--Device-Decimal-static acos(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## acosh

```TypeScript
acosh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的双曲余弦的倒数。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-acosh(): Decimal--><!--Device-Decimal-acosh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## acosh

```TypeScript
static acosh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲余弦的倒数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static acosh(n: Value): Decimal--><!--Device-Decimal-static acosh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## add

```TypeScript
add(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值加上n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-add(n: Value): Decimal--><!--Device-Decimal-add(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## add

```TypeScript
static add(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x加y的和。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static add(x: Value, y: Value): Decimal--><!--Device-Decimal-static add(x: Value, y: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |
| y | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## asin

```TypeScript
asin(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的反正弦值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-asin(): Decimal--><!--Device-Decimal-asin(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## asin

```TypeScript
static asin(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的反正弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static asin(n: Value): Decimal--><!--Device-Decimal-static asin(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## asinh

```TypeScript
asinh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的双曲正弦的倒数。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-asinh(): Decimal--><!--Device-Decimal-asinh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## asinh

```TypeScript
static asinh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正弦的倒数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static asinh(n: Value): Decimal--><!--Device-Decimal-static asinh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## atan

```TypeScript
atan(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的反正切值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-atan(): Decimal--><!--Device-Decimal-atan(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## atan

```TypeScript
static atan(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的反正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static atan(n: Value): Decimal--><!--Device-Decimal-static atan(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## atan2

```TypeScript
static atan2(y: Value, x: Value): Decimal
```

返回一个新的Decimal对象，其值是-π到π（含边界）范围内y/x的反正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static atan2(y: Value, x: Value): Decimal--><!--Device-Decimal-static atan2(y: Value, x: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| y | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} 除法的被除数。 |
| x | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} 除法的除数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## atanh

```TypeScript
atanh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的双曲正切的倒数。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-atanh(): Decimal--><!--Device-Decimal-atanh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## atanh

```TypeScript
static atanh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正切的倒数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static atanh(n: Value): Decimal--><!--Device-Decimal-static atanh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## cbrt

```TypeScript
cbrt(): Decimal
```

返回一个新的Decimal对象，其值是当前Decimal对象的立方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-cbrt(): Decimal--><!--Device-Decimal-cbrt(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## cbrt

```TypeScript
static cbrt(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的立方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static cbrt(n: Value): Decimal--><!--Device-Decimal-static cbrt(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## ceil

```TypeScript
ceil(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal向正无穷方向舍入得到的结果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-ceil(): Decimal--><!--Device-Decimal-ceil(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## ceil

```TypeScript
static ceil(n: Value): Decimal
```

返回一个新的Decimal对象，其值为使用ROUND\_CEIL将n舍入为整数的结果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static ceil(n: Value): Decimal--><!--Device-Decimal-static ceil(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## clamp

```TypeScript
clamp(min: Value, max: Value): Decimal
```

返回一个将Decimal值限制在min到max范围内的Decimal对象。如果值大于max，返回max；如果值小于min，返回min；否则，返回原值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-clamp(min: Value, max: Value): Decimal--><!--Device-Decimal-clamp(min: Value, max: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| min | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |
| max | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## clamp

```TypeScript
static clamp(n: Value, min: Value, max: Value): Decimal
```

返回一个值为将n限制在min到max范围内的Decimal对象。当大于限制的最大值时返回max，小于限制的最小值时返回min，在范围内返回值不变。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static clamp(n: Value, min: Value, max: Value): Decimal--><!--Device-Decimal-static clamp(n: Value, min: Value, max: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |
| min | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |
| max | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## comparedTo

ArkTS-Dyn:
```TypeScript
comparedTo(n: Value): number
```

ArkTS-Sta:
```TypeScript
comparedTo(n: Value): double
```

Decimal的比较方法。 1 如果此Decimal大于n的值， -1 如果此Decimal小于n的值， 0 如果两者的值相等， NaN 如果两者中任一Decimal的值为NaN。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-comparedTo(n: Value): double--><!--Device-Decimal-comparedTo(n: Value): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | the number type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## constructor

```TypeScript
constructor(n: Value)
```

Decimal的构造函数。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-constructor(n: Value)--><!--Device-Decimal-constructor(n: Value)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## cos

```TypeScript
cos(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的余弦值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-cos(): Decimal--><!--Device-Decimal-cos(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## cos

```TypeScript
static cos(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的余弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static cos(n: Value): Decimal--><!--Device-Decimal-static cos(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## cosh

```TypeScript
cosh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的双曲余弦值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-cosh(): Decimal--><!--Device-Decimal-cosh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## cosh

```TypeScript
static cosh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲余弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static cosh(n: Value): Decimal--><!--Device-Decimal-static cosh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## decimalPlaces

ArkTS-Dyn:
```TypeScript
decimalPlaces(): number
```

ArkTS-Sta:
```TypeScript
decimalPlaces(): double
```

返回Decimal对象的小数位数。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-decimalPlaces(): double--><!--Device-Decimal-decimalPlaces(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | the number type |

## div

```TypeScript
div(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值除以n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-div(n: Value): Decimal--><!--Device-Decimal-div(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## div

```TypeScript
static div(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x除以y的商。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static div(x: Value, y: Value): Decimal--><!--Device-Decimal-static div(x: Value, y: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |
| y | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## dividedToIntegerBy

```TypeScript
dividedToIntegerBy(n: Value): Decimal
```

返回该Decimal除以n后获得的整数部分。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-dividedToIntegerBy(n: Value): Decimal--><!--Device-Decimal-dividedToIntegerBy(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## equals

```TypeScript
equals(n: Value): boolean
```

返回此Decimal是否等于比较值n，相等返回true，否则返回false。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-equals(n: Value): boolean--><!--Device-Decimal-equals(n: Value): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## exp

```TypeScript
exp(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的自然指数（即以e为底，此Decimal值为指数的幂）。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-exp(): Decimal--><!--Device-Decimal-exp(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## exp

```TypeScript
static exp(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的自然指数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static exp(n: Value): Decimal--><!--Device-Decimal-static exp(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## floor

```TypeScript
floor(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal向负无穷方向舍入得到的结果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-floor(): Decimal--><!--Device-Decimal-floor(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## floor

```TypeScript
static floor(n: Value): Decimal
```

返回一个新的Decimal对象，其值为使用ROUND\_FLOOR将n舍入为整数的结果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static floor(n: Value): Decimal--><!--Device-Decimal-static floor(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## greaterThan

```TypeScript
greaterThan(n: Value): boolean
```

返回此Decimal是否大于比较值n，大于返回true，否则返回false。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-greaterThan(n: Value): boolean--><!--Device-Decimal-greaterThan(n: Value): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(n: Value): boolean
```

返回此Decimal是否大于等于比较值n，大于等于返回true，否则返回false。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-greaterThanOrEqualTo(n: Value): boolean--><!--Device-Decimal-greaterThanOrEqualTo(n: Value): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## hypot

```TypeScript
static hypot(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值是参数平方和的平方根。无入参时默认返回0。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static hypot(...n: Value[]): Decimal--><!--Device-Decimal-static hypot(...n: Value[]): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_[] | 是 | {double \| string \| Decimal} Decimal |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## isFinite

```TypeScript
isFinite(): boolean
```

返回此Decimal是否为有限值，是有限值返回true，否则返回false。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isFinite(): boolean--><!--Device-Decimal-isFinite(): boolean-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isInteger(): boolean--><!--Device-Decimal-isInteger(): boolean-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isNaN(): boolean--><!--Device-Decimal-isNaN(): boolean-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isNegative(): boolean--><!--Device-Decimal-isNegative(): boolean-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isPositive(): boolean--><!--Device-Decimal-isPositive(): boolean-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-isZero(): boolean--><!--Device-Decimal-isZero(): boolean-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-lessThan(n: Value): boolean--><!--Device-Decimal-lessThan(n: Value): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(n: Value): boolean
```

返回此Decimal是否小于等于比较值n，小于等于返回true，否则返回false。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-lessThanOrEqualTo(n: Value): boolean--><!--Device-Decimal-lessThanOrEqualTo(n: Value): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the boolean type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## ln

```TypeScript
ln(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal值的自然对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-ln(): Decimal--><!--Device-Decimal-ln(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## ln

```TypeScript
static ln(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的自然对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static ln(n: Value): Decimal--><!--Device-Decimal-static ln(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## log

```TypeScript
log(n: Value): Decimal
```

返回一个对数运算后的Decimal对象，其值是以n为底的对数值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-log(n: Value): Decimal--><!--Device-Decimal-log(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## log

```TypeScript
static log(n: Value, base: Value): Decimal
```

返回一个新的Decimal对象，其值是以base为底n的对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static log(n: Value, base: Value): Decimal--><!--Device-Decimal-static log(n: Value, base: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |
| base | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## log10

```TypeScript
static log10(n: Value): Decimal
```

返回一个新的Decimal对象，其值是以10为底n的对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static log10(n: Value): Decimal--><!--Device-Decimal-static log10(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## log2

```TypeScript
static log2(n: Value): Decimal
```

返回一个新的Decimal对象，其值是以2为底n的对数。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static log2(n: Value): Decimal--><!--Device-Decimal-static log2(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## max

```TypeScript
static max(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值是所有参数中的最大值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static max(...n: Value[]): Decimal--><!--Device-Decimal-static max(...n: Value[]): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_[] | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## min

```TypeScript
static min(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值是所有参数中的最小值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static min(...n: Value[]): Decimal--><!--Device-Decimal-static min(...n: Value[]): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_[] | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## mod

```TypeScript
mod(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值除以n后的模。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-mod(n: Value): Decimal--><!--Device-Decimal-mod(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## mod

```TypeScript
static mod(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值是x除以y的模。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static mod(x: Value, y: Value): Decimal--><!--Device-Decimal-static mod(x: Value, y: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |
| y | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## mul

```TypeScript
mul(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值乘以n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-mul(n: Value): Decimal--><!--Device-Decimal-mul(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## mul

```TypeScript
static mul(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x乘以y的积。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static mul(x: Value, y: Value): Decimal--><!--Device-Decimal-static mul(x: Value, y: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |
| y | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## negate

```TypeScript
negate(): Decimal
```

返回一个新的Decimal对象，其值将此Decimal的值乘以-1。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-negate(): Decimal--><!--Device-Decimal-negate(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## pow

```TypeScript
pow(n: Value): Decimal
```

返回一个新的Decimal对象，其值是这个Decimal值的n次幂。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-pow(n: Value): Decimal--><!--Device-Decimal-pow(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## pow

```TypeScript
static pow(base: Value, exponent: Value): Decimal
```

返回一个新的Decimal对象，其值为base的exponent次幂。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static pow(base: Value, exponent: Value): Decimal--><!--Device-Decimal-static pow(base: Value, exponent: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| base | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} 幂运算的底数的值。 |
| exponent | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} 幂运算的幂的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200060](../../errorcode-utils.md#10200060-超出精度限制) | Precision limit exceeded. |

## precision

ArkTS-Dyn:
```TypeScript
precision(): number
```

ArkTS-Sta:
```TypeScript
precision(): double
```

返回Decimal对象的有效数字位数。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-precision(): double--><!--Device-Decimal-precision(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | the number type |

## precision

ArkTS-Dyn:
```TypeScript
precision(includeZeros: boolean | number): number
```

ArkTS-Sta:
```TypeScript
precision(includeZeros: boolean | int): double
```

返回Decimal对象的有效数字位数，可通过includeZeros判断是否计算整数部分的尾随零。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-precision(includeZeros: boolean | int): double--><!--Device-Decimal-precision(includeZeros: boolean | int): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| includeZeros | ArkTS-Dyn: boolean \| number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：boolean \| int | 是 | 是否计算整数部分尾随零。true或1表示计算，false或0表示不计算。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | the number type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## random

```TypeScript
static random(): Decimal
```

返回一个新的Decimal对象，其值为大于等于0且小于1的随机值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static random(): Decimal--><!--Device-Decimal-static random(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200061](../../errorcode-utils.md#10200061-加密方法不可用) | Crypto unavailable |

## random

ArkTS-Dyn:
```TypeScript
static random(significantDigits: number): Decimal
```

ArkTS-Sta:
```TypeScript
static random(significantDigits: double): Decimal
```

返回一个新的Decimal对象，其值为大于等于0且小于1的随机值，并保留significantDigits位有效数字（若产生尾随零则可能少于该位数）。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static random(significantDigits: double): Decimal--><!--Device-Decimal-static random(significantDigits: double): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | {number} 随机值保留的有效数字。取值范围为[0, 1e9]的整数。[since 12 - 17] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200061](../../errorcode-utils.md#10200061-加密方法不可用) | Crypto unavailable |

## round

```TypeScript
static round(n: Value): Decimal
```

返回一个新的Decimal对象，其值是使用rounding舍入模式将n舍入为整数的结果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static round(n: Value): Decimal--><!--Device-Decimal-static round(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## set

```TypeScript
static set(config: DecimalConfig): void
```

用于设置Decimal的配置属性，通过set设置的属性是全局生效的。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static set(config: DecimalConfig): void--><!--Device-Decimal-static set(config: DecimalConfig): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |
| [10200061](../../errorcode-utils.md#10200061-加密方法不可用) | Crypto unavailable |

## sign

ArkTS-Dyn:
```TypeScript
static sign(n: Value): number
```

ArkTS-Sta:
```TypeScript
static sign(n: Value): double
```

根据参数n的值返回对应的符号： 1 如果 n > 0， -1 如果 n < 0， 0 如果 n 为 0， -0 如果 n 为 -0， NaN 其他情况

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sign(n: Value): double--><!--Device-Decimal-static sign(n: Value): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 17 |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | the Decimal type\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 18+ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sin

```TypeScript
sin(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的正弦值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-sin(): Decimal--><!--Device-Decimal-sin(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## sin

```TypeScript
static sin(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的正弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sin(n: Value): Decimal--><!--Device-Decimal-static sin(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sinh

```TypeScript
sinh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的双曲正弦值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-sinh(): Decimal--><!--Device-Decimal-sinh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## sinh

```TypeScript
static sinh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正弦值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sinh(n: Value): Decimal--><!--Device-Decimal-static sinh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sqrt

```TypeScript
sqrt(): Decimal
```

返回一个新的Decimal对象，其值是当前Decimal的平方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-sqrt(): Decimal--><!--Device-Decimal-sqrt(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## sqrt

```TypeScript
static sqrt(n: Value): Decimal
```

返回一个新的Decimal对象，其值为n的平方根。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sqrt(n: Value): Decimal--><!--Device-Decimal-static sqrt(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sub

```TypeScript
sub(n: Value): Decimal
```

返回一个新的Decimal对象，其值是将此Decimal的值减去n。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-sub(n: Value): Decimal--><!--Device-Decimal-sub(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sub

```TypeScript
static sub(x: Value, y: Value): Decimal
```

返回一个新的Decimal对象，其值为x减y的差。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sub(x: Value, y: Value): Decimal--><!--Device-Decimal-static sub(x: Value, y: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |
| y | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## sum

```TypeScript
static sum(...n: Value[]): Decimal
```

返回一个新的Decimal对象，其值为参数的和。按照precision设置有效位数，按照rounding设置舍入模式。 仅对结果进行舍入，不对中间计算结果进行舍入。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static sum(...n: Value[]): Decimal--><!--Device-Decimal-static sum(...n: Value[]): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_[] | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## tan

```TypeScript
tan(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的正切值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-tan(): Decimal--><!--Device-Decimal-tan(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## tan

```TypeScript
static tan(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static tan(n: Value): Decimal--><!--Device-Decimal-static tan(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## tanh

```TypeScript
tanh(): Decimal
```

返回一个新的Decimal对象，其值是此Decimal的双曲正切值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-tanh(): Decimal--><!--Device-Decimal-tanh(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## tanh

```TypeScript
static tanh(n: Value): Decimal
```

返回一个新的Decimal对象，其值是n的双曲正切值。按照precision设置有效位数，按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static tanh(n: Value): Decimal--><!--Device-Decimal-static tanh(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} 以弧度为单位的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## toBinary

```TypeScript
toBinary(): string
```

将Decimal转换为二进制表示的字符串。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toBinary(): string--><!--Device-Decimal-toBinary(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toBinary

ArkTS-Dyn:
```TypeScript
toBinary(significantDigits: number): string
```

ArkTS-Sta:
```TypeScript
toBinary(significantDigits: double): string
```

将Decimal转换为二进制表示的字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toBinary(significantDigits: double): string--><!--Device-Decimal-toBinary(significantDigits: double): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toBinary

ArkTS-Dyn:
```TypeScript
toBinary(significantDigits: number, rounding: Rounding): string
```

ArkTS-Sta:
```TypeScript
toBinary(significantDigits: double, rounding: Rounding): string
```

将Decimal转换为二进制表示的字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toBinary(significantDigits: double, rounding: Rounding): string--><!--Device-Decimal-toBinary(significantDigits: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toDecimalPlaces

```TypeScript
toDecimalPlaces(): Decimal
```

返回一个保留小数点后指定位数的Decimal对象，不进行小数的取舍。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toDecimalPlaces(): Decimal--><!--Device-Decimal-toDecimalPlaces(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## toDecimalPlaces

ArkTS-Dyn:
```TypeScript
toDecimalPlaces(decimalPlaces: number): Decimal
```

ArkTS-Sta:
```TypeScript
toDecimalPlaces(decimalPlaces: double): Decimal
```

返回一个保留小数点后指定位数的Decimal对象，可按照decimalPlaces设置小数位数。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toDecimalPlaces(decimalPlaces: double): Decimal--><!--Device-Decimal-toDecimalPlaces(decimalPlaces: double): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toDecimalPlaces

ArkTS-Dyn:
```TypeScript
toDecimalPlaces(decimalPlaces: number, rounding: Rounding): Decimal
```

ArkTS-Sta:
```TypeScript
toDecimalPlaces(decimalPlaces: double, rounding: Rounding): Decimal
```

返回一个保留小数点后指定位数的Decimal对象，可按照decimalPlaces设置小数位数，可按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toDecimalPlaces(decimalPlaces: double, rounding: Rounding): Decimal--><!--Device-Decimal-toDecimalPlaces(decimalPlaces: double, rounding: Rounding): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |
| rounding | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toExponential

```TypeScript
toExponential(): string
```

将数值转换为指数表示法的字符串，不进行小数部分的舍入。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toExponential(): string--><!--Device-Decimal-toExponential(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toExponential

ArkTS-Dyn:
```TypeScript
toExponential(decimalPlaces: number): string
```

ArkTS-Sta:
```TypeScript
toExponential(decimalPlaces: double): string
```

将数值转换为指数表示法的字符串，可按照decimalPlaces设置小数位数。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toExponential(decimalPlaces: double): string--><!--Device-Decimal-toExponential(decimalPlaces: double): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toExponential

ArkTS-Dyn:
```TypeScript
toExponential(decimalPlaces: number, rounding: Rounding): string
```

ArkTS-Sta:
```TypeScript
toExponential(decimalPlaces: double, rounding: Rounding): string
```

将数值转换为指数表示法的字符串，可按照decimalPlaces设置小数位数，可按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toExponential(decimalPlaces: double, rounding: Rounding): string--><!--Device-Decimal-toExponential(decimalPlaces: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |
| rounding | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toFixed

```TypeScript
toFixed(): string
```

将数值转换为十进制定点模式表示的字符串，不进行小数的取舍。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toFixed(): string--><!--Device-Decimal-toFixed(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toFixed

ArkTS-Dyn:
```TypeScript
toFixed(decimalPlaces: number): string
```

ArkTS-Sta:
```TypeScript
toFixed(decimalPlaces: double): string
```

将数值转换为十进制定点模式表示的字符串，可按照decimalPlaces设置小数位数。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toFixed(decimalPlaces: double): string--><!--Device-Decimal-toFixed(decimalPlaces: double): string-End-->

**系统能力：** 
- API版本18+：SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toFixed

ArkTS-Dyn:
```TypeScript
toFixed(decimalPlaces: number, rounding: Rounding): string
```

ArkTS-Sta:
```TypeScript
toFixed(decimalPlaces: double, rounding: Rounding): string
```

将数值转换为十进制定点模式表示的字符串，可按照decimalPlaces设置小数位数，可按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toFixed(decimalPlaces: double, rounding: Rounding): string--><!--Device-Decimal-toFixed(decimalPlaces: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decimalPlaces | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的小数点后有效位数。取值范围为[0, 1e9]的整数。 |
| rounding | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toFraction

```TypeScript
toFraction(): Decimal[]
```

转换为分数表示的数。返回一个长度固定为2的Decimal数组，分别表示分子和分母。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toFraction(): Decimal[]--><!--Device-Decimal-toFraction(): Decimal[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_[] | the Decimal[] type |

## toFraction

```TypeScript
toFraction(maxDenominator: Value): Decimal[]
```

转换为分数表示的数，可以通过maxDenominator设置最大分母值。返回一个长度固定为2的Decimal数组，分别表示分子和分母。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toFraction(maxDenominator: Value): Decimal[]--><!--Device-Decimal-toFraction(maxDenominator: Value): Decimal[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxDenominator | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_[] | the Decimal[] type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## toHexadecimal

```TypeScript
toHexadecimal(): string
```

将Decimal转换为十六进制表示的字符串。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toHexadecimal(): string--><!--Device-Decimal-toHexadecimal(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toHexadecimal

ArkTS-Dyn:
```TypeScript
toHexadecimal(significantDigits: number): string
```

ArkTS-Sta:
```TypeScript
toHexadecimal(significantDigits: double): string
```

将Decimal转换为十六进制表示的字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toHexadecimal(significantDigits: double): string--><!--Device-Decimal-toHexadecimal(significantDigits: double): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toHexadecimal

ArkTS-Dyn:
```TypeScript
toHexadecimal(significantDigits: number, rounding: Rounding): string
```

ArkTS-Sta:
```TypeScript
toHexadecimal(significantDigits: double, rounding: Rounding): string
```

将Decimal转换为十六进制表示的字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toHexadecimal(significantDigits: double, rounding: Rounding): string--><!--Device-Decimal-toHexadecimal(significantDigits: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toNearest

```TypeScript
toNearest(n: Value): Decimal
```

返回一个新的Decimal对象，此Decimal为指定值n乘以一个倍数后与原Decimal最接近的值。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toNearest(n: Value): Decimal--><!--Device-Decimal-toNearest(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## toNearest

```TypeScript
toNearest(n: Value, rounding: Rounding): Decimal
```

返回一个新的Decimal对象，此Decimal为指定值n乘以一个倍数后与原Decimal最接近的值，可按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toNearest(n: Value, rounding: Rounding): Decimal--><!--Device-Decimal-toNearest(n: Value, rounding: Rounding): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |
| rounding | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toNumber

ArkTS-Dyn:
```TypeScript
toNumber(): number
```

ArkTS-Sta:
```TypeScript
toNumber(): double
```

将值转换为number类型。零保留其符号。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toNumber(): double--><!--Device-Decimal-toNumber(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | the number type |

## toOctal

```TypeScript
toOctal(): string
```

将Decimal转换为八进制表示的字符串。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toOctal(): string--><!--Device-Decimal-toOctal(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toOctal

ArkTS-Dyn:
```TypeScript
toOctal(significantDigits: number): string
```

ArkTS-Sta:
```TypeScript
toOctal(significantDigits: double): string
```

将Decimal转换为八进制表示的字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toOctal(significantDigits: double): string--><!--Device-Decimal-toOctal(significantDigits: double): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toOctal

ArkTS-Dyn:
```TypeScript
toOctal(significantDigits: number, rounding: Rounding): string
```

ArkTS-Sta:
```TypeScript
toOctal(significantDigits: double, rounding: Rounding): string
```

将Decimal转换为八进制表示的字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toOctal(significantDigits: double, rounding: Rounding): string--><!--Device-Decimal-toOctal(significantDigits: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | {double \| string \| Decimal} |
| rounding | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toPrecision

```TypeScript
toPrecision(): string
```

将Decimal对象转换为字符串。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toPrecision(): string--><!--Device-Decimal-toPrecision(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

## toPrecision

ArkTS-Dyn:
```TypeScript
toPrecision(significantDigits: number): string
```

ArkTS-Sta:
```TypeScript
toPrecision(significantDigits: double): string
```

将数值转换为字符串，可按照significantDigits设置有效数字。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toPrecision(significantDigits: double): string--><!--Device-Decimal-toPrecision(significantDigits: double): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toPrecision

ArkTS-Dyn:
```TypeScript
toPrecision(significantDigits: number, rounding: Rounding): string
```

ArkTS-Sta:
```TypeScript
toPrecision(significantDigits: double, rounding: Rounding): string
```

将数值转换为字符串，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toPrecision(significantDigits: double, rounding: Rounding): string--><!--Device-Decimal-toPrecision(significantDigits: double, rounding: Rounding): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | the string type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toSignificantDigits

```TypeScript
toSignificantDigits(): Decimal
```

返回一个按照保留有效数字转换的Decimal对象。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toSignificantDigits(): Decimal--><!--Device-Decimal-toSignificantDigits(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## toSignificantDigits

ArkTS-Dyn:
```TypeScript
toSignificantDigits(significantDigits: number): Decimal
```

ArkTS-Sta:
```TypeScript
toSignificantDigits(significantDigits: double): Decimal
```

返回一个按照保留有效数字转换的Decimal对象，可按照significantDigits设置有效数字。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toSignificantDigits(significantDigits: double): Decimal--><!--Device-Decimal-toSignificantDigits(significantDigits: double): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toSignificantDigits

ArkTS-Dyn:
```TypeScript
toSignificantDigits(significantDigits: number, rounding: Rounding): Decimal
```

ArkTS-Sta:
```TypeScript
toSignificantDigits(significantDigits: double, rounding: Rounding): Decimal
```

返回一个按照保留有效数字转换的Decimal对象，可按照significantDigits设置有效数字，可按照rounding设置舍入模式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toSignificantDigits(significantDigits: double, rounding: Rounding): Decimal--><!--Device-Decimal-toSignificantDigits(significantDigits: double, rounding: Rounding): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| significantDigits | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 转换时保留的有效数字。取值范围为[1, 1e9]的整数。 |
| rounding | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 转换时使用的舍入模式。取值范围为0到8的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200001](../../errorcode-utils.md#10200001-参数范围越界错误) | The value of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ is out of range. |

## toString

```TypeScript
toString(): string
```

返回一个字符串，表示此 Decimal 的值。如果此 Decimal 的正指数等于或大于toExpPos，或负指数等于或小于toExpNeg，则将返回指数表示法。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-toString(): string--><!--Device-Decimal-toString(): string-End-->

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

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-trunc(): Decimal--><!--Device-Decimal-trunc(): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

## trunc

```TypeScript
static trunc(n: Value): Decimal
```

返回一个新的Decimal对象，其值为将n截断为整数的结果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static trunc(n: Value): Decimal--><!--Device-Decimal-static trunc(n: Value): Decimal-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| n | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | {double \| string \| Decimal} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | the Decimal type |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types;2. Parameter verification failed. |

## valueOf

```TypeScript
valueOf(): string
```

返回一个字符串，表示此 Decimal 的值。与toString不同，负零将包含负号。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

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

模运算下，余数始终为正。使用欧几里得除法：q = sign(x) * floor(a / abs(x))。

**类型：** 9

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly EUCLIDEAN : 9--><!--Device-Decimal-static readonly EUCLIDEAN : 9-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_CEILING

```TypeScript
static readonly ROUND_CEILING : 2
```

向正无穷方向舍入。

**类型：** 2

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_CEILING : 2--><!--Device-Decimal-static readonly ROUND_CEILING : 2-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_DOWN

```TypeScript
static readonly ROUND_DOWN : 1
```

向靠近零的方向舍入。模运算下，余数与被除数的符号相同，使用截断除法。

**类型：** 1

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_DOWN : 1--><!--Device-Decimal-static readonly ROUND_DOWN : 1-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_FLOOR

```TypeScript
static readonly ROUND_FLOOR : 3
```

向负无穷方向舍入。模运算下，余数与除数的符号相同。

**类型：** 3

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_FLOOR : 3--><!--Device-Decimal-static readonly ROUND_FLOOR : 3-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_CEILING

```TypeScript
static readonly ROUND_HALF_CEILING : 7
```

向最近的邻值舍入。如果距离相等，则向正无穷方向舍入。

**类型：** 7

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_HALF_CEILING : 7--><!--Device-Decimal-static readonly ROUND_HALF_CEILING : 7-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_DOWN

```TypeScript
static readonly ROUND_HALF_DOWN : 5
```

向最近的邻值舍入。如果距离相等，则向靠近零方向舍入。

**类型：** 5

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_HALF_DOWN : 5--><!--Device-Decimal-static readonly ROUND_HALF_DOWN : 5-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_EVEN

```TypeScript
static readonly ROUND_HALF_EVEN : 6
```

向最近的邻值舍入。如果距离相等，则向偶数邻值舍入。模运算下，IEEE 754 求余函数。

**类型：** 6

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_HALF_EVEN : 6--><!--Device-Decimal-static readonly ROUND_HALF_EVEN : 6-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_FLOOR

```TypeScript
static readonly ROUND_HALF_FLOOR : 8
```

向最近的邻值舍入。如果距离相等，则向负无穷方向舍入。

**类型：** 8

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_HALF_FLOOR : 8--><!--Device-Decimal-static readonly ROUND_HALF_FLOOR : 8-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_HALF_UP

```TypeScript
static readonly ROUND_HALF_UP : 4
```

向最近的邻值舍入。如果距离相等，则向远离零的方向舍入。

**类型：** 4

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-static readonly ROUND_HALF_UP : 4--><!--Device-Decimal-static readonly ROUND_HALF_UP : 4-End-->

**系统能力：** SystemCapability.Utils.Lang

## ROUND_UP

```TypeScript
static readonly ROUND_UP : 0
```

向远离零的方向舍入。模运算下，如果被除数为负，则余数为正，否则为负。

**类型：** 0

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

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

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-readonly d: number[]--><!--Device-Decimal-readonly d: number[]-End-->

**系统能力：** SystemCapability.Utils.Lang

## e

```TypeScript
get e(): double
```

exponent：表示Decimal数的十进制指数。

**类型：** double

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-get e(): double--><!--Device-Decimal-get e(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

## s

```TypeScript
get s(): double
```

sign：表示Decimal数的符号位，0表示正数，1表示负数。

**类型：** double

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Decimal-get s(): double--><!--Device-Decimal-get s(): double-End-->

**系统能力：** SystemCapability.Utils.Lang

