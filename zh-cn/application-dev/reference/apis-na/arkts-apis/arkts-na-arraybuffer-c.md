# ArrayBuffer

与JS ArrayBuffer API兼容的类。 用于表示通用的、固定长度的原始二进制数据缓冲区。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export class ArrayBuffer--><!--Device-unnamed-export class ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## at

```TypeScript
public at(pos: int): byte
```

返回指定索引处的字节。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public at(pos: int): byte--><!--Device-ArrayBuffer-public at(pos: int): byte-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | int | 是 | 在缓冲区中的位置。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| byte | 字节值。 |

## atomicAddI16

```TypeScript
public atomicAddI16(index: int, byteOffset: int, value: short): long
```

以原子方式将一个值加到指定索引处的元素上。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAddI16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicAddI16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 要相加的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAddI32

```TypeScript
public atomicAddI32(index: int, byteOffset: int, value: int): long
```

以原子方式将一个值加到指定索引处的元素上。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAddI32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicAddI32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 要相加的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAddI64

```TypeScript
public atomicAddI64(index: int, byteOffset: int, value: long): long
```

以原子方式将一个值加到指定索引处的元素上。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAddI64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicAddI64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 要相加的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAddI8

```TypeScript
public atomicAddI8(index: int, byteOffset: int, value: byte): long
```

以原子方式将一个值加到指定索引处的元素上。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAddI8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicAddI8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 要相加的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAddU16

```TypeScript
public atomicAddU16(index: int, byteOffset: int, value: short): long
```

以原子方式将一个值加到指定索引处的元素上。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAddU16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicAddU16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 要相加的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAddU32

```TypeScript
public atomicAddU32(index: int, byteOffset: int, value: int): long
```

以原子方式将一个值加到指定索引处的元素上。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAddU32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicAddU32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 要相加的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAddU64

```TypeScript
public atomicAddU64(index: int, byteOffset: int, value: long): long
```

以原子方式将一个值加到指定索引处的元素上。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAddU64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicAddU64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 要相加的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAddU8

```TypeScript
public atomicAddU8(index: int, byteOffset: int, value: byte): long
```

以原子方式将一个值加到指定索引处的元素上。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAddU8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicAddU8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 要相加的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAndI16

```TypeScript
public atomicAndI16(index: int, byteOffset: int, value: short): long
```

以原子方式对指定索引处的元素执行按位与运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAndI16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicAndI16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 参与按位与运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAndI32

```TypeScript
public atomicAndI32(index: int, byteOffset: int, value: int): long
```

以原子方式对指定索引处的元素执行按位与运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAndI32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicAndI32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 参与按位与运算的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAndI64

```TypeScript
public atomicAndI64(index: int, byteOffset: int, value: long): long
```

以原子方式对指定索引处的元素执行按位与运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAndI64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicAndI64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 参与按位与运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAndI8

```TypeScript
public atomicAndI8(index: int, byteOffset: int, value: byte): long
```

以原子方式对指定索引处的元素执行按位与运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAndI8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicAndI8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 参与按位与运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAndU16

```TypeScript
public atomicAndU16(index: int, byteOffset: int, value: short): long
```

以原子方式对指定索引处的元素执行按位与运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAndU16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicAndU16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 参与按位与运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAndU32

```TypeScript
public atomicAndU32(index: int, byteOffset: int, value: int): long
```

以原子方式对指定索引处的元素执行按位与运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAndU32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicAndU32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 参与按位与运算的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAndU64

```TypeScript
public atomicAndU64(index: int, byteOffset: int, value: long): long
```

以原子方式对指定索引处的元素执行按位与运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAndU64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicAndU64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 参与按位与运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicAndU8

```TypeScript
public atomicAndU8(index: int, byteOffset: int, value: byte): long
```

以原子方式对指定索引处的元素执行按位与运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicAndU8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicAndU8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 参与按位与运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicCompareExchangeI16

```TypeScript
public atomicCompareExchangeI16(index: int, byteOffset: int, expectedValue: short, replacementValue: short): long
```

以原子方式比较并交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicCompareExchangeI16(index: int, byteOffset: int, expectedValue: short, replacementValue: short): long--><!--Device-ArrayBuffer-public atomicCompareExchangeI16(index: int, byteOffset: int, expectedValue: short, replacementValue: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| expectedValue | short | 是 | 期望值。 |
| replacementValue | short | 是 | 替换值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicCompareExchangeI32

```TypeScript
public atomicCompareExchangeI32(index: int, byteOffset: int, expectedValue: int, replacementValue: int): long
```

以原子方式比较并交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicCompareExchangeI32(index: int, byteOffset: int, expectedValue: int, replacementValue: int): long--><!--Device-ArrayBuffer-public atomicCompareExchangeI32(index: int, byteOffset: int, expectedValue: int, replacementValue: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| expectedValue | int | 是 | 期望值。 <br>取值约束：应为整数。 |
| replacementValue | int | 是 | 替换值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicCompareExchangeI64

```TypeScript
public atomicCompareExchangeI64(index: int, byteOffset: int, expectedValue: long, replacementValue: long): long
```

以原子方式比较并交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicCompareExchangeI64(index: int, byteOffset: int, expectedValue: long, replacementValue: long): long--><!--Device-ArrayBuffer-public atomicCompareExchangeI64(index: int, byteOffset: int, expectedValue: long, replacementValue: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| expectedValue | long | 是 | 期望值。 |
| replacementValue | long | 是 | 替换值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicCompareExchangeI8

```TypeScript
public atomicCompareExchangeI8(index: int, byteOffset: int, expectedValue: byte, replacementValue: byte): long
```

以原子方式比较并交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicCompareExchangeI8(index: int, byteOffset: int, expectedValue: byte, replacementValue: byte): long--><!--Device-ArrayBuffer-public atomicCompareExchangeI8(index: int, byteOffset: int, expectedValue: byte, replacementValue: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| expectedValue | byte | 是 | 期望值。 |
| replacementValue | byte | 是 | 替换值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicCompareExchangeU16

```TypeScript
public atomicCompareExchangeU16(index: int, byteOffset: int, expectedValue: short, replacementValue: short): long
```

以原子方式比较并交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicCompareExchangeU16(index: int, byteOffset: int, expectedValue: short, replacementValue: short): long--><!--Device-ArrayBuffer-public atomicCompareExchangeU16(index: int, byteOffset: int, expectedValue: short, replacementValue: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| expectedValue | short | 是 | 期望值。 |
| replacementValue | short | 是 | 替换值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicCompareExchangeU32

```TypeScript
public atomicCompareExchangeU32(index: int, byteOffset: int, expectedValue: int, replacementValue: int): long
```

以原子方式比较并交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicCompareExchangeU32(index: int, byteOffset: int, expectedValue: int, replacementValue: int): long--><!--Device-ArrayBuffer-public atomicCompareExchangeU32(index: int, byteOffset: int, expectedValue: int, replacementValue: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| expectedValue | int | 是 | 期望值。 <br>取值约束：应为整数。 |
| replacementValue | int | 是 | 替换值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicCompareExchangeU64

```TypeScript
public atomicCompareExchangeU64(index: int, byteOffset: int, expectedValue: long, replacementValue: long): long
```

以原子方式比较并交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicCompareExchangeU64(index: int, byteOffset: int, expectedValue: long, replacementValue: long): long--><!--Device-ArrayBuffer-public atomicCompareExchangeU64(index: int, byteOffset: int, expectedValue: long, replacementValue: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| expectedValue | long | 是 | 期望值。 |
| replacementValue | long | 是 | 替换值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicCompareExchangeU8

```TypeScript
public atomicCompareExchangeU8(index: int, byteOffset: int, expectedValue: byte, replacementValue: byte): long
```

以原子方式比较并交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicCompareExchangeU8(index: int, byteOffset: int, expectedValue: byte, replacementValue: byte): long--><!--Device-ArrayBuffer-public atomicCompareExchangeU8(index: int, byteOffset: int, expectedValue: byte, replacementValue: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| expectedValue | byte | 是 | 期望值。 |
| replacementValue | byte | 是 | 替换值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicExchangeI16

```TypeScript
public atomicExchangeI16(index: int, byteOffset: int, value: short): long
```

以原子方式交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicExchangeI16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicExchangeI16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 要交换的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicExchangeI32

```TypeScript
public atomicExchangeI32(index: int, byteOffset: int, value: int): long
```

以原子方式交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicExchangeI32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicExchangeI32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 要交换的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicExchangeI64

```TypeScript
public atomicExchangeI64(index: int, byteOffset: int, value: long): long
```

以原子方式交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicExchangeI64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicExchangeI64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 要交换的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicExchangeI8

```TypeScript
public atomicExchangeI8(index: int, byteOffset: int, value: byte): long
```

以原子方式交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicExchangeI8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicExchangeI8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 要交换的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicExchangeU16

```TypeScript
public atomicExchangeU16(index: int, byteOffset: int, value: short): long
```

以原子方式交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicExchangeU16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicExchangeU16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 要交换的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicExchangeU32

```TypeScript
public atomicExchangeU32(index: int, byteOffset: int, value: int): long
```

以原子方式交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicExchangeU32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicExchangeU32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 要交换的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicExchangeU64

```TypeScript
public atomicExchangeU64(index: int, byteOffset: int, value: long): long
```

以原子方式交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicExchangeU64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicExchangeU64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 要交换的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicExchangeU8

```TypeScript
public atomicExchangeU8(index: int, byteOffset: int, value: byte): long
```

以原子方式交换指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicExchangeU8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicExchangeU8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 要交换的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicLoadI16

```TypeScript
public atomicLoadI16(index: int, byteOffset: int): long
```

以原子方式加载指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicLoadI16(index: int, byteOffset: int): long--><!--Device-ArrayBuffer-public atomicLoadI16(index: int, byteOffset: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicLoadI32

```TypeScript
public atomicLoadI32(index: int, byteOffset: int): long
```

以原子方式加载指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicLoadI32(index: int, byteOffset: int): long--><!--Device-ArrayBuffer-public atomicLoadI32(index: int, byteOffset: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicLoadI64

```TypeScript
public atomicLoadI64(index: int, byteOffset: int): long
```

以原子方式加载指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicLoadI64(index: int, byteOffset: int): long--><!--Device-ArrayBuffer-public atomicLoadI64(index: int, byteOffset: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicLoadI8

```TypeScript
public atomicLoadI8(index: int, byteOffset: int): long
```

以原子方式加载指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicLoadI8(index: int, byteOffset: int): long--><!--Device-ArrayBuffer-public atomicLoadI8(index: int, byteOffset: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicLoadU16

```TypeScript
public atomicLoadU16(index: int, byteOffset: int): long
```

以原子方式加载指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicLoadU16(index: int, byteOffset: int): long--><!--Device-ArrayBuffer-public atomicLoadU16(index: int, byteOffset: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicLoadU32

```TypeScript
public atomicLoadU32(index: int, byteOffset: int): long
```

以原子方式加载指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicLoadU32(index: int, byteOffset: int): long--><!--Device-ArrayBuffer-public atomicLoadU32(index: int, byteOffset: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicLoadU64

```TypeScript
public atomicLoadU64(index: int, byteOffset: int): long
```

以原子方式加载指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicLoadU64(index: int, byteOffset: int): long--><!--Device-ArrayBuffer-public atomicLoadU64(index: int, byteOffset: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicLoadU8

```TypeScript
public atomicLoadU8(index: int, byteOffset: int): long
```

以原子方式加载指定索引处的值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicLoadU8(index: int, byteOffset: int): long--><!--Device-ArrayBuffer-public atomicLoadU8(index: int, byteOffset: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicOrI16

```TypeScript
public atomicOrI16(index: int, byteOffset: int, value: short): long
```

以原子方式对指定索引处的元素执行按位或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicOrI16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicOrI16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 参与按位或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicOrI32

```TypeScript
public atomicOrI32(index: int, byteOffset: int, value: int): long
```

以原子方式对指定索引处的元素执行按位或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicOrI32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicOrI32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 参与按位或运算的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicOrI64

```TypeScript
public atomicOrI64(index: int, byteOffset: int, value: long): long
```

以原子方式对指定索引处的元素执行按位或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicOrI64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicOrI64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 参与按位或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicOrI8

```TypeScript
public atomicOrI8(index: int, byteOffset: int, value: byte): long
```

以原子方式对指定索引处的元素执行按位或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicOrI8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicOrI8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 参与按位或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicOrU16

```TypeScript
public atomicOrU16(index: int, byteOffset: int, value: short): long
```

以原子方式对指定索引处的元素执行按位或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicOrU16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicOrU16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 参与按位或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicOrU32

```TypeScript
public atomicOrU32(index: int, byteOffset: int, value: int): long
```

以原子方式对指定索引处的元素执行按位或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicOrU32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicOrU32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 参与按位或运算的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicOrU64

```TypeScript
public atomicOrU64(index: int, byteOffset: int, value: long): long
```

以原子方式对指定索引处的元素执行按位或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicOrU64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicOrU64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 参与按位或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicOrU8

```TypeScript
public atomicOrU8(index: int, byteOffset: int, value: byte): long
```

以原子方式对指定索引处的元素执行按位或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicOrU8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicOrU8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 参与按位或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicStoreI16

```TypeScript
public atomicStoreI16(index: int, byteOffset: int, value: short): long
```

以原子方式在指定索引处存储一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicStoreI16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicStoreI16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 要存储的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 已存储的值。 |

## atomicStoreI32

```TypeScript
public atomicStoreI32(index: int, byteOffset: int, value: int): long
```

以原子方式在指定索引处存储一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicStoreI32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicStoreI32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 要存储的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 已存储的值。 |

## atomicStoreI64

```TypeScript
public atomicStoreI64(index: int, byteOffset: int, value: long): long
```

以原子方式在指定索引处存储一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicStoreI64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicStoreI64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 要存储的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 已存储的值。 |

## atomicStoreI8

```TypeScript
public atomicStoreI8(index: int, byteOffset: int, value: byte): long
```

以原子方式在指定索引处存储一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicStoreI8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicStoreI8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 要存储的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 已存储的值。 |

## atomicStoreU16

```TypeScript
public atomicStoreU16(index: int, byteOffset: int, value: short): long
```

以原子方式在指定索引处存储一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicStoreU16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicStoreU16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 要存储的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 已存储的值。 |

## atomicStoreU32

```TypeScript
public atomicStoreU32(index: int, byteOffset: int, value: int): long
```

以原子方式在指定索引处存储一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicStoreU32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicStoreU32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 要存储的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 已存储的值。 |

## atomicStoreU64

```TypeScript
public atomicStoreU64(index: int, byteOffset: int, value: long): long
```

以原子方式在指定索引处存储一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicStoreU64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicStoreU64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 要存储的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 已存储的值。 |

## atomicStoreU8

```TypeScript
public atomicStoreU8(index: int, byteOffset: int, value: byte): long
```

以原子方式在指定索引处存储一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicStoreU8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicStoreU8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 要存储的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 已存储的值。 |

## atomicSubI16

```TypeScript
public atomicSubI16(index: int, byteOffset: int, value: short): long
```

以原子方式从指定索引处的元素中减去一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicSubI16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicSubI16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 要相减的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicSubI32

```TypeScript
public atomicSubI32(index: int, byteOffset: int, value: int): long
```

以原子方式从指定索引处的元素中减去一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicSubI32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicSubI32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 要相减的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicSubI64

```TypeScript
public atomicSubI64(index: int, byteOffset: int, value: long): long
```

以原子方式从指定索引处的元素中减去一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicSubI64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicSubI64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 要相减的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicSubI8

```TypeScript
public atomicSubI8(index: int, byteOffset: int, value: byte): long
```

以原子方式从指定索引处的元素中减去一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicSubI8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicSubI8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 要相减的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicSubU16

```TypeScript
public atomicSubU16(index: int, byteOffset: int, value: short): long
```

以原子方式从指定索引处的元素中减去一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicSubU16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicSubU16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 要相减的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicSubU32

```TypeScript
public atomicSubU32(index: int, byteOffset: int, value: int): long
```

以原子方式从指定索引处的元素中减去一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicSubU32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicSubU32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 要相减的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicSubU64

```TypeScript
public atomicSubU64(index: int, byteOffset: int, value: long): long
```

以原子方式从指定索引处的元素中减去一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicSubU64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicSubU64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 要相减的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicSubU8

```TypeScript
public atomicSubU8(index: int, byteOffset: int, value: byte): long
```

以原子方式从指定索引处的元素中减去一个值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicSubU8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicSubU8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 要相减的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicXorI16

```TypeScript
public atomicXorI16(index: int, byteOffset: int, value: short): long
```

以原子方式对指定索引处的元素执行按位异或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicXorI16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicXorI16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 参与按位异或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicXorI32

```TypeScript
public atomicXorI32(index: int, byteOffset: int, value: int): long
```

以原子方式对指定索引处的元素执行按位异或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicXorI32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicXorI32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 参与按位异或运算的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicXorI64

```TypeScript
public atomicXorI64(index: int, byteOffset: int, value: long): long
```

以原子方式对指定索引处的元素执行按位异或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicXorI64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicXorI64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 参与按位异或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicXorI8

```TypeScript
public atomicXorI8(index: int, byteOffset: int, value: byte): long
```

以原子方式对指定索引处的元素执行按位异或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicXorI8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicXorI8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 参与按位异或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicXorU16

```TypeScript
public atomicXorU16(index: int, byteOffset: int, value: short): long
```

以原子方式对指定索引处的元素执行按位异或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicXorU16(index: int, byteOffset: int, value: short): long--><!--Device-ArrayBuffer-public atomicXorU16(index: int, byteOffset: int, value: short): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | short | 是 | 参与按位异或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicXorU32

```TypeScript
public atomicXorU32(index: int, byteOffset: int, value: int): long
```

以原子方式对指定索引处的元素执行按位异或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicXorU32(index: int, byteOffset: int, value: int): long--><!--Device-ArrayBuffer-public atomicXorU32(index: int, byteOffset: int, value: int): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | int | 是 | 参与按位异或运算的值。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicXorU64

```TypeScript
public atomicXorU64(index: int, byteOffset: int, value: long): long
```

以原子方式对指定索引处的元素执行按位异或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicXorU64(index: int, byteOffset: int, value: long): long--><!--Device-ArrayBuffer-public atomicXorU64(index: int, byteOffset: int, value: long): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | long | 是 | 参与按位异或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## atomicXorU8

```TypeScript
public atomicXorU8(index: int, byteOffset: int, value: byte): long
```

以原子方式对指定索引处的元素执行按位异或运算。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public atomicXorU8(index: int, byteOffset: int, value: byte): long--><!--Device-ArrayBuffer-public atomicXorU8(index: int, byteOffset: int, value: byte): long-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待访问的索引。 <br>取值约束：必须为大于或等于0的整数。 |
| byteOffset | int | 是 | 在ArrayBuffer中的字节偏移量，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| value | byte | 是 | 参与按位异或运算的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 操作后的值。 |

## bytesLength

```TypeScript
public static bytesLength(text: string, encoding: string): int
```

返回字符串在给定编码下的字节长度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public static bytesLength(text: string, encoding: string): int--><!--Device-ArrayBuffer-public static bytesLength(text: string, encoding: string): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 源字符串。 |
| encoding | string | 是 | 编码类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 计算得到的字节长度。 |

## constructor

```TypeScript
constructor(length: int, maxByteLength?: int)
```

创建一个大小等于length参数的ArrayBuffer。

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-constructor(length: int, maxByteLength?: int)--><!--Device-ArrayBuffer-constructor(length: int, maxByteLength?: int)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | int | 是 | ArrayBuffer的大小，单位为字节。 <br>取值约束：必须为大于或等于0的整数。 |
| maxByteLength | int | 否 | 可选参数，ArrayBuffer可调整到的最大大小。 <br>取值约束：必须为大于或等于0的整数。 |

## constructor

```TypeScript
public constructor(length: double, maxByteLength?: double)
```

创建一个大小等于length参数的ArrayBuffer。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public constructor(length: double, maxByteLength?: double)--><!--Device-ArrayBuffer-public constructor(length: double, maxByteLength?: double)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | double | 是 | ArrayBuffer的大小，单位为字节。 <br>取值约束：必须大于或等于0。 |
| maxByteLength | double | 否 | 可选参数，ArrayBuffer可调整到的最大大小。 <br>取值约束：必须大于或等于0。 |

## from

```TypeScript
public static from(arr: FixedArray<byte>): ArrayBuffer
```

根据字节数组创建一个新的ArrayBuffer。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public static from(arr: FixedArray<byte>): ArrayBuffer--><!--Device-ArrayBuffer-public static from(arr: FixedArray<byte>): ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arr | FixedArray&lt;byte&gt; | 是 | 源字节数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 新的ArrayBuffer。 |

## from

```TypeScript
public static from(u8arr: Uint8Array): ArrayBuffer
```

根据Uint8Array创建一个新的ArrayBuffer。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public static from(u8arr: Uint8Array): ArrayBuffer--><!--Device-ArrayBuffer-public static from(u8arr: Uint8Array): ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| u8arr | Uint8Array | 是 | 源类型化数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 新的ArrayBuffer。 |

## from

```TypeScript
public static from(array: double[]): ArrayBuffer
```

根据数字数组创建一个新的ArrayBuffer。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public static from(array: double[]): ArrayBuffer--><!--Device-ArrayBuffer-public static from(array: double[]): ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| array | double[] | 是 | 源数字数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 新的ArrayBuffer。 |

## from

```TypeScript
public static from(str: string, encoding: string): ArrayBuffer
```

根据指定编码的字符串创建一个新的ArrayBuffer。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public static from(str: string, encoding: string): ArrayBuffer--><!--Device-ArrayBuffer-public static from(str: string, encoding: string): ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| str | string | 是 | 源字符串。 |
| encoding | string | 是 | 字符串编码，例如"utf8"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 新的ArrayBuffer。 |

## from

```TypeScript
public static from(buff: ArrayBuffer, byteOffset: int, length: int): ArrayBuffer
```

根据已有ArrayBuffer的一个片段创建一个新的ArrayBuffer。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public static from(buff: ArrayBuffer, byteOffset: int, length: int): ArrayBuffer--><!--Device-ArrayBuffer-public static from(buff: ArrayBuffer, byteOffset: int, length: int): ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buff | ArrayBuffer | 是 | 源缓冲区。 |
| byteOffset | int | 是 | 源中的起始偏移量。 <br>取值约束：应为整数。 |
| length | int | 是 | 要拷贝的字节数。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 新的ArrayBuffer。 |

## from

```TypeScript
public static from(buffer: ArrayBuffer, byteOffset?: double, length?: double): ArrayBuffer
```

使用数字参数，根据已有ArrayBuffer的一个片段创建一个新的ArrayBuffer。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public static from(buffer: ArrayBuffer, byteOffset?: double, length?: double): ArrayBuffer--><!--Device-ArrayBuffer-public static from(buffer: ArrayBuffer, byteOffset?: double, length?: double): ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 源缓冲区。 |
| byteOffset | double | 否 | 起始偏移量。 |
| length | double | 否 | 字节长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 新的ArrayBuffer。 |

## fromObject

```TypeScript
public static fromObject(obj: Object, byteOffsetOrEncoding: int | string, length: int): ArrayBuffer
```

根据对象创建一个新的ArrayBuffer。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public static fromObject(obj: Object, byteOffsetOrEncoding: int | string, length: int): ArrayBuffer--><!--Device-ArrayBuffer-public static fromObject(obj: Object, byteOffsetOrEncoding: int | string, length: int): ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object | 是 | 源对象，为字符串或ArrayBuffer。 |
| byteOffsetOrEncoding | int \| string | 是 | 字节偏移量或编码字符串。 |
| length | int | 是 | 要拷贝的长度。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 新的ArrayBuffer。 |

## getByteLength

```TypeScript
public getByteLength(): int
```

返回该ArrayBuffer的字节长度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public getByteLength(): int--><!--Device-ArrayBuffer-public getByteLength(): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 字节长度。 |

## isView

```TypeScript
public static isView(obj: Object): boolean
```

检查传入的对象是否为ArrayBuffer视图之一。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public static isView(obj: Object): boolean--><!--Device-ArrayBuffer-public static isView(obj: Object): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | Object | 是 | 待检查的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果该对象为视图则返回true，否则返回false。 |

## resize

```TypeScript
public resize(newLen : int): void
```

将该ArrayBuffer调整为指定长度。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public resize(newLen : int): void--><!--Device-ArrayBuffer-public resize(newLen : int): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newLen | int | 是 | 新的字节长度。 <br>取值约束：必须为大于或等于0的整数。 |

## set

```TypeScript
public set(pos: int, val: byte): void
```

设置指定索引处的字节值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public set(pos: int, val: byte): void--><!--Device-ArrayBuffer-public set(pos: int, val: byte): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | int | 是 | 在缓冲区中的位置。 <br>取值约束：应为整数。 |
| val | byte | 是 | 要设置的字节值。 |

## slice

```TypeScript
public slice(begin: int, end?: int): ArrayBuffer
```

创建一个新的ArrayBuffer，包含[begin, end)范围内字节的副本。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public slice(begin: int, end?: int): ArrayBuffer--><!--Device-ArrayBuffer-public slice(begin: int, end?: int): ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | int | 是 | 开始拷贝的起始索引（包含）。 <br>取值约束：应为整数。 |
| end | int | 否 | 停止拷贝的结束索引（不包含）。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 新的ArrayBuffer。 |

## slice

```TypeScript
public slice(begin: double, end?: double): ArrayBuffer
```

创建一个新的ArrayBuffer，包含[begin, end)范围内字节的副本。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public slice(begin: double, end?: double): ArrayBuffer--><!--Device-ArrayBuffer-public slice(begin: double, end?: double): ArrayBuffer-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | double | 是 | 开始拷贝的起始索引（包含）。 |
| end | double | 否 | 停止拷贝的结束索引（不包含）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | 新的ArrayBuffer。 |

## stringify

```TypeScript
public static stringify(buffer: ArrayBuffer, encoding: string, start: int, end: int): string
```

将ArrayBuffer的一个片段转换为字符串。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public static stringify(buffer: ArrayBuffer, encoding: string, start: int, end: int): string--><!--Device-ArrayBuffer-public static stringify(buffer: ArrayBuffer, encoding: string, start: int, end: int): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | 是 | 源缓冲区。 |
| encoding | string | 是 | 使用的编码。 |
| start | int | 是 | 起始索引。 <br>取值约束：应为整数。 |
| end | int | 是 | 结束索引。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 解码后的字符串。 |

## toString

```TypeScript
public toString(): string
```

返回该ArrayBuffer的字符串表示。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayBuffer-public toString(): string--><!--Device-ArrayBuffer-public toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 该ArrayBuffer的字符串表示。 |

