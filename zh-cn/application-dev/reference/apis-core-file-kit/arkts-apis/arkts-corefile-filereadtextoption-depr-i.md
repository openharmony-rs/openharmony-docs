# FileReadTextOption

可选项类型，支持readText接口使用。

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () => void

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## encoding

```TypeScript
encoding?: string
```

编码格式，默认为UTF-8。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。

**类型：** (data: string, code: number) => void

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## length

```TypeScript
length?: number
```

读取的长度，单位为Byte，默认值为4096。

**类型：** number

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## position

```TypeScript
position?: number
```

读取的起始位置，单位为Byte，默认为文件的起始位置。

**类型：** number

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## success

```TypeScript
success?: (data: FileReadTextResponse) => void
```

接口调用成功的回调函数。返回[FileReadTextResponse](arkts-corefile-filereadtextresponse-depr-i.md)。

**类型：** (data: FileReadTextResponse) => void

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## uri

```TypeScript
uri: string
```

本地文件URI。由于轻量级穿戴设备底层文件系统的限制，该值必须满足以下要求：
1. URI 中不得包含以下特殊字符：\"*+,:;<=>?[]|\x7F等。
2. 最大允许字符长度为128个字符。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

