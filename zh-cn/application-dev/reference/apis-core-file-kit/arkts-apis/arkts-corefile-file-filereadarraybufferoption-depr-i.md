# FileReadArrayBufferOption

可选项类型，支持readArrayBuffer接口使用。

**起始版本：** 3

**废弃版本：** 10

<!--Device-unnamed-export interface FileReadArrayBufferOption--><!--Device-unnamed-export interface FileReadArrayBufferOption-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileReadArrayBufferOption-complete?: () => void--><!--Device-FileReadArrayBufferOption-complete?: () => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileReadArrayBufferOption-fail?: (data: string, code: number) => void--><!--Device-FileReadArrayBufferOption-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## length

```TypeScript
length?: number
```

需要读取的长度，单位为Byte，缺省则读取到文件结尾。

**类型：** number

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileReadArrayBufferOption-length?: number--><!--Device-FileReadArrayBufferOption-length?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## position

```TypeScript
position?: number
```

读取的起始位置，单位为Byte，缺省为文件的起始位置。

**类型：** number

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileReadArrayBufferOption-position?: number--><!--Device-FileReadArrayBufferOption-position?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## success

```TypeScript
success?: (data: FileReadArrayBufferResponse) => void
```

接口调用成功的回调函数。返回[FileReadArrayBufferResponse](arkts-corefile-file-filereadarraybufferresponse-depr-i.md)。

**类型：** (data: FileReadArrayBufferResponse) =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileReadArrayBufferOption-success?: (data: FileReadArrayBufferResponse) => void--><!--Device-FileReadArrayBufferOption-success?: (data: FileReadArrayBufferResponse) => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## uri

```TypeScript
uri: string
```

本地文件URI。由于轻量级穿戴设备底层文件系统的限制，该值必须满足以下要求：1. URI 中不得包含以下特殊字符：\"*+,:;<=>?[]|\x7F等。2. 最大允许字符长度为128个字符。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileReadArrayBufferOption-uri: string--><!--Device-FileReadArrayBufferOption-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

