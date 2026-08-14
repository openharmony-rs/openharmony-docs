# TextDecoder

The TextDecoder represents a text decoder that accepts a string as input, decodes it in UTF-8 format, and outputs UTF-8 byte stream.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-util-class TextDecoder--><!--Device-util-class TextDecoder-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor()
```

The textDecoder constructor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-TextDecoder-constructor()--><!--Device-TextDecoder-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

## create

```TypeScript
static create(encoding?: string, options?: TextDecoderOptions): TextDecoder
```

Replaces the original constructor to process arguments and return a textDecoder object.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-TextDecoder-static create(encoding?: string, options?: TextDecoderOptions): TextDecoder--><!--Device-TextDecoder-static create(encoding?: string, options?: TextDecoderOptions): TextDecoder-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | Decoding format |
| options | [TextDecoderOptions](../../apis-arkts/arkts-apis/arkts-arkts-util-textdecoderoptions-i.md) | 否 | Options |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextDecoder](../../apis-arkts/arkts-apis/arkts-arkts-util-textdecoder-c.md) |  |

## decodeToString

```TypeScript
decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string
```

The input is decoded and a string is returned. If options.stream is set to true, any incomplete byte sequences found at the end of the input are internally buffered and will be emitted after the next call to textDecoder.decodeToString(). If textDecoder.fatal is set to true, any decoding errors that occur will result in a TypeError being thrown.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-TextDecoder-decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string--><!--Device-TextDecoder-decodeToString(input: Uint8Array, options?: DecodeToStringOptions): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| input | Uint8Array | 是 | Decoded numbers in accordance with the format. |
| options | [DecodeToStringOptions](../../apis-arkts/arkts-apis/arkts-arkts-util-decodetostringoptions-i.md) | 否 | The default option is set to false. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Return decoded text |

