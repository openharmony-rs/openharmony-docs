# TextEncoder

The TextEncoder interface represents a text encoder. The encoder takes the byte stream as the input and outputs the String string.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-util-class TextEncoder--><!--Device-util-class TextEncoder-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(encoding?: string)
```

The textEncoder constructor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextEncoder-constructor(encoding?: string)--><!--Device-TextEncoder-constructor(encoding?: string)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | The string for encoding format. |

## create

```TypeScript
static create(encoding?: string): TextEncoder
```

Create a TextEncoder object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextEncoder-static create(encoding?: string): TextEncoder--><!--Device-TextEncoder-static create(encoding?: string): TextEncoder-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | The string for encoding format. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

## encodeInto

```TypeScript
encodeInto(input?: string): Uint8Array
```

UTF-8 encodes the input string and returns a Uint8Array containing the encoded bytes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextEncoder-encodeInto(input?: string): Uint8Array--><!--Device-TextEncoder-encodeInto(input?: string): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | string | 否 | The string to be encoded. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | Returns the encoded text. |

## encodeIntoUint8Array

```TypeScript
encodeIntoUint8Array(input: string, dest: Uint8Array): EncodeIntoUint8ArrayInfo
```

Encode string, write the result to dest array.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextEncoder-encodeIntoUint8Array(input: string, dest: Uint8Array): EncodeIntoUint8ArrayInfo--><!--Device-TextEncoder-encodeIntoUint8Array(input: string, dest: Uint8Array): EncodeIntoUint8ArrayInfo-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | string | 是 | The string to be encoded. |
| dest | Uint8Array | 是 | Encoded numbers in accordance with the format |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Return the object, where read represents |

## encoding

```TypeScript
get encoding(): string
```

Encoding format.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextEncoder-get encoding(): string--><!--Device-TextEncoder-get encoding(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

