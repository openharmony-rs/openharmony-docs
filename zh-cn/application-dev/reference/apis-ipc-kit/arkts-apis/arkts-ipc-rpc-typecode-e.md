# TypeCode

从API version 12起，IPC新增[writeArrayBuffer](arkts-ipc-rpc-messagesequence-c.md#writearraybuffer)和 [readArrayBuffer](arkts-ipc-rpc-messagesequence-c.md#readarraybuffer)方法传递ArrayBuffer数据，传递数据时通过具体类型值来分辨业务是以哪一种TypedArray去进行数据 的读写。类型码对应数值及含义如下。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.IPC.Core

## INT8_ARRAY

```TypeScript
INT8_ARRAY = 0
```

TypedArray类型为INT8_ARRAY，数据将以8位有符号整数格式进行读写，每个元素占用1字节。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.IPC.Core

## UINT8_ARRAY

```TypeScript
UINT8_ARRAY = 1
```

TypedArray类型为UINT8_ARRAY，数据将以8位无符号整数格式进行读写，每个元素占用1字节。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.IPC.Core

## INT16_ARRAY

```TypeScript
INT16_ARRAY = 2
```

TypedArray类型为INT16_ARRAY，数据将以16位有符号整数格式进行读写，每个元素占用2字节。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.IPC.Core

## UINT16_ARRAY

```TypeScript
UINT16_ARRAY = 3
```

TypedArray类型为UINT16_ARRAY，数据将以16位无符号整数格式进行读写，每个元素占用2字节。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.IPC.Core

## INT32_ARRAY

```TypeScript
INT32_ARRAY = 4
```

TypedArray类型为INT32_ARRAY，数据将以32位有符号整数格式进行读写，每个元素占用4字节。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.IPC.Core

## UINT32_ARRAY

```TypeScript
UINT32_ARRAY = 5
```

TypedArray类型为UINT32_ARRAY，数据将以32位无符号整数格式进行读写，每个元素占用4字节。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.IPC.Core

## FLOAT32_ARRAY

```TypeScript
FLOAT32_ARRAY = 6
```

TypedArray类型为FLOAT32_ARRAY，数据将以32位单精度浮点数格式进行读写，每个元素占用4字节。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.IPC.Core

## FLOAT64_ARRAY

```TypeScript
FLOAT64_ARRAY = 7
```

TypedArray类型为FLOAT64_ARRAY，数据将以64位双精度浮点数格式进行读写，每个元素占用8字节。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.IPC.Core

## BIGINT64_ARRAY

```TypeScript
BIGINT64_ARRAY = 8
```

TypedArray类型为BIGINT64_ARRAY，数据将以64位大整数格式进行读写，每个元素占用8字节。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.IPC.Core

## BIGUINT64_ARRAY

```TypeScript
BIGUINT64_ARRAY = 9
```

TypedArray类型为BIGUINT64_ARRAY，数据将以64位无符号大整数格式进行读写，每个元素占用8字节。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.IPC.Core
