# FileGetOption

可选项类型，支持get接口使用。

**起始版本：** 3

**废弃版本：** 10

<!--Device-unnamed-export interface FileGetOption--><!--Device-unnamed-export interface FileGetOption-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () => void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileGetOption-complete?: () => void--><!--Device-FileGetOption-complete?: () => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。

**类型：** (data: string, code: number) => void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileGetOption-fail?: (data: string, code: number) => void--><!--Device-FileGetOption-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## recursive

```TypeScript
recursive?: boolean
```

是否进行递归获取子目录文件列表，true为进行该操作，缺省为false。

**类型：** boolean

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileGetOption-recursive?: boolean--><!--Device-FileGetOption-recursive?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## success

```TypeScript
success?: (file: FileResponse) => void
```

接口调用成功的回调函数。 返回[FileResponse](arkts-corefile-file-fileresponse-depr-i.md)。

**类型：** (file: FileResponse) => void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileGetOption-success?: (file: FileResponse) => void--><!--Device-FileGetOption-success?: (file: FileResponse) => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## uri

```TypeScript
uri: string
```

文件的URI。由于轻量级穿戴设备底层文件系统的限制，该值必须满足以下要求：1. URI 中不得包含以下特殊字符：\"*+,:;<=>?[]|\x7F等。2. 最大允许字符长度为128个字符。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileGetOption-uri: string--><!--Device-FileGetOption-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

