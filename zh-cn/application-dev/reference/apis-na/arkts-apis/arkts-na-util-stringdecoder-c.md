# StringDecoder

Provide the ability to decode binary streams into strings. The supported encoding types include: utf-8, iso-8859-2, koi8-r, macintosh, windows-1250, windows-1251, gbk, gb18030, big5, utf-16be, utf-16 le, etc.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-util-class StringDecoder--><!--Device-util-class StringDecoder-End-->

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(encoding?: string)
```

The StringDecoder constructor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-StringDecoder-constructor(encoding?: string)--><!--Device-StringDecoder-constructor(encoding?: string)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encoding | string | 否 | Encoding type of the input data.Default: utf8. |

## end

```TypeScript
end(chunk?: string | Uint8Array): string
```

Returns any remaining input stored in the internal buffer as a string. After end() is called, this object can be reused for new input.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-StringDecoder-end(chunk?: string | Uint8Array): string--><!--Device-StringDecoder-end(chunk?: string | Uint8Array): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 否 | The bytes to decode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns any remaining input stored in the internal buffer as a string. |

## write

```TypeScript
write(chunk: string | Uint8Array): string
```

Returns a decoded string, ensuring that any incomplete multiple byte characters at the end of the Uint8Array are omitted from the returned string and stored in an internal buffer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-StringDecoder-write(chunk: string | Uint8Array): string--><!--Device-StringDecoder-write(chunk: string | Uint8Array): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chunk | string \| Uint8Array | 是 | The bytes to decode. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns a decoded string. |

