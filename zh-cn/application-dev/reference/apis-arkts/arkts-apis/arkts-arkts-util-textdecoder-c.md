# TextDecoder

The TextDecoder represents a text decoder that accepts a string as input, decodes it in UTF-8 format, and outputs UTF-8 byte stream.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-util-class TextDecoder--><!--Device-util-class TextDecoder-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor()
```

The textDecoder constructor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextDecoder-constructor()--><!--Device-TextDecoder-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## create

```TypeScript
static create(encoding?: string, options?: TextDecoderOptions): TextDecoder
```

Replaces the original constructor to process arguments and return a textDecoder object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextDecoder-static create(encoding?: string, options?: TextDecoderOptions): TextDecoder--><!--Device-TextDecoder-static create(encoding?: string, options?: TextDecoderOptions): TextDecoder-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | Decoding format |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Options |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

## decodeToString

```TypeScript
decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string
```

The input is decoded and a string is returned. If options.stream is set to true, any incomplete byte sequences found at the end of the input are internally buffered and will be emitted after the next call to textDecoder.decodeToString(). If textDecoder.fatal is set to true, any decoding errors that occur will result in a TypeError being thrown.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextDecoder-decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string--><!--Device-TextDecoder-decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | Uint8Array | 是 | Decoded numbers in accordance with the format. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | The default option is set to false. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return decoded text |

## encoding

```TypeScript
get encoding(): string
```

The source encoding's name, lowercased.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextDecoder-get encoding(): string--><!--Device-TextDecoder-get encoding(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

## fatal

```TypeScript
get fatal(): boolean
```

Returns \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_ if error mode is "fatal", and \_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_ otherwise.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextDecoder-get fatal(): boolean--><!--Device-TextDecoder-get fatal(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## ignoreBOM

```TypeScript
get ignoreBOM(): boolean
```

Returns \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_ if ignore BOM flag is set, and \_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_ otherwise.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-TextDecoder-get ignoreBOM(): boolean--><!--Device-TextDecoder-get ignoreBOM(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

