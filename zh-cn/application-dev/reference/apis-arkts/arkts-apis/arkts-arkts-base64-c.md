# Base64

将包含 Base64 数据的字符串或 Uint8Array 解码为重新分配的 Uint8Array。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [Base64Helper](arkts-arkts-base64helper-c.md)

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor()
```

用于创建 **Base64** 对象的构造函数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [constructor](arkts-arkts-base64helper-c.md#constructor-1)

**系统能力：** SystemCapability.Utils.Lang

## decode

```TypeScript
decode(src: Uint8Array | string): Promise<Uint8Array>
```

将输入内容解码为 Uint8Array 对象。该接口使用 promise 返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [decode](arkts-arkts-base64helper-c.md#decode-1)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array \| string | 是 | 要解码的 Uint8Array 对象或字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | 用于返回获取到的 Uint8Array 对象的 promise。 |

## decodeSync

```TypeScript
decodeSync(src: Uint8Array | string): Uint8Array
```

将输入内容解码为 Uint8Array 对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [decodeSync](arkts-arkts-base64helper-c.md#decodesync-1)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array \| string | 是 | 要解码的 Uint8Array 对象或字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 获取到的 Uint8Array 对象。 |

## encode

```TypeScript
encode(src: Uint8Array): Promise<Uint8Array>
```

将输入内容编码为 Uint8Array 对象。该接口使用 promise 返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [encode](arkts-arkts-base64helper-c.md#encode-1)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | 用于返回获取到的 Uint8Array 对象的 promise。 |

## encodeSync

```TypeScript
encodeSync(src: Uint8Array): Uint8Array
```

对输入的 Uint8Array 字节数组进行 Base64 编码，并返回编码后的 Uint8Array。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [encodeSync](arkts-arkts-base64helper-c.md#encodesync-1)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 获取到的 Uint8Array 对象。 |

## encodeToString

```TypeScript
encodeToString(src: Uint8Array): Promise<string>
```

将输入内容编码为字符串。该接口使用 promise 返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [encodeToString](arkts-arkts-base64helper-c.md#encodetostring-1)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 用于返回获取到的字符串的 promise。 |

## encodeToStringSync

```TypeScript
encodeToStringSync(src: Uint8Array): string
```

对输入的 Uint8Array 字节数组进行 Base64 编码，并返回编码后的字符串。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [encodeToStringSync](arkts-arkts-base64helper-c.md#encodetostringsync-1)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | 要编码的 Uint8Array 对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 获取到的字符串。 |

