# Base64Helper

使用Base64编码方案将Base64编码的字符串或输入的u8数组解码为新分配的u8数组。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-util-class Base64Helper--><!--Device-util-class Base64Helper-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor()
```

用于创建base64编码和解码的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Base64Helper-constructor()--><!--Device-Base64Helper-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## decode

```TypeScript
decode(src: Uint8Array | string, options?: Type): Promise<Uint8Array>
```

使用Base64编码方案将Base64编码的字符串或输入的u8数组异步解码为新分配的u8数组。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Base64Helper-decode(src: Uint8Array | string, options?: Type): Promise<Uint8Array>--><!--Device-Base64Helper-decode(src: Uint8Array | string, options?: Type): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array \| string | 是 | Uint8Array值或字符串值 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Type枚举之一 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | 返回异步解码的Uint8Array。 |

## decodeSync

```TypeScript
decodeSync(src: Uint8Array | string, options?: Type): Uint8Array
```

使用Base64编码方案将Base64编码的字符串或输入的u8数组解码为新分配的u8数组。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Base64Helper-decodeSync(src: Uint8Array | string, options?: Type): Uint8Array--><!--Device-Base64Helper-decodeSync(src: Uint8Array | string, options?: Type): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array \| string | 是 | Uint8Array值或字符串值 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Type枚举之一 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回解码后的Uint8Array。 |

## encode

```TypeScript
encode(src: Uint8Array, options?: Type): Promise<Uint8Array>
```

使用Base64编码方案将指定u8数组中的所有字节异步编码为新分配的u8数组。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Base64Helper-encode(src: Uint8Array, options?: Type): Promise<Uint8Array>--><!--Device-Base64Helper-encode(src: Uint8Array, options?: Type): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | Uint8Array值 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 枚举输入参数包含两种编码格式：BASIC和BASIC\_\_\_ESCAPED\_UNDERSCORE\_\_\_URL\_\_\_ESCAPED\_UNDERSCORE\_\_\_SAFE |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | 返回异步编码的新Uint8Array。 |

## encodeSync

```TypeScript
encodeSync(src: Uint8Array, options?: Type): Uint8Array
```

使用Base64编码方案将指定u8数组中的所有字节编码为新分配的u8数组。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Base64Helper-encodeSync(src: Uint8Array, options?: Type): Uint8Array--><!--Device-Base64Helper-encodeSync(src: Uint8Array, options?: Type): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | Uint8Array值 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 枚举输入参数包含两种编码格式：BASIC和BASIC\_\_\_ESCAPED\_UNDERSCORE\_\_\_URL\_\_\_ESCAPED\_UNDERSCORE\_\_\_SAFE |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回编码后的新Uint8Array。 |

## encodeToString

```TypeScript
encodeToString(src: Uint8Array, options?: Type): Promise<string>
```

使用Base64编码方案将指定的字节数组异步编码为字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Base64Helper-encodeToString(src: Uint8Array, options?: Type): Promise<string>--><!--Device-Base64Helper-encodeToString(src: Uint8Array, options?: Type): Promise<string>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | Uint8Array值 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Type枚举之一 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 返回异步编码的字符串。 |

## encodeToStringSync

```TypeScript
encodeToStringSync(src: Uint8Array, options?: Type): string
```

使用Base64编码方案将指定的字节数组编码为字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Base64Helper-encodeToStringSync(src: Uint8Array, options?: Type): string--><!--Device-Base64Helper-encodeToStringSync(src: Uint8Array, options?: Type): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Uint8Array | 是 | Uint8Array值 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Type枚举之一 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回编码后的字符串。 |

