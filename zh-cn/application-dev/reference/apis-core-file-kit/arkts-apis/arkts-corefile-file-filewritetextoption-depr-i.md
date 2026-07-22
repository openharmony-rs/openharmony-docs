# FileWriteTextOption

可选项类型，支持writeText接口使用。

**起始版本：** 3

**废弃版本：** 10

<!--Device-unnamed-export interface FileWriteTextOption--><!--Device-unnamed-export interface FileWriteTextOption-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## append

```TypeScript
append?: boolean
```

是否追加模式，默认为false。true为追加，false为不追加。

**类型：** boolean

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteTextOption-append?: boolean--><!--Device-FileWriteTextOption-append?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteTextOption-complete?: () => void--><!--Device-FileWriteTextOption-complete?: () => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## encoding

```TypeScript
encoding?: string
```

编码格式，默认为UTF-8。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteTextOption-encoding?: string--><!--Device-FileWriteTextOption-encoding?: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteTextOption-fail?: (data: string, code: number) => void--><!--Device-FileWriteTextOption-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## success

```TypeScript
success?: () => void
```

接口调用成功的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteTextOption-success?: () => void--><!--Device-FileWriteTextOption-success?: () => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## text

```TypeScript
text: string
```

写入的字符串。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteTextOption-text: string--><!--Device-FileWriteTextOption-text: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## uri

```TypeScript
uri: string
```

本地文件URI，如果文件不存在会创建文件。由于轻量级穿戴设备底层文件系统的限制，该值必须满足以下要求：1. URI 中不得包含以下特殊字符：\"*+,:;&lt;=&gt;?[]|\x7F等。2. 最大允许字符长度为128个字符。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteTextOption-uri: string--><!--Device-FileWriteTextOption-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

