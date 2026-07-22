# FileCopyOption

可选项类型，支持copy接口使用。

**起始版本：** 3

**废弃版本：** 10

<!--Device-unnamed-export interface FileCopyOption--><!--Device-unnamed-export interface FileCopyOption-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileCopyOption-complete?: () => void--><!--Device-FileCopyOption-complete?: () => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## dstUri

```TypeScript
dstUri: string
```

文件要拷贝到的位置的URI。不支持用应用资源路径或tmp类型的URI。由于轻量级穿戴设备底层文件系统的限制，该值必须满足以下要求：1. URI 中不得包含以下特殊字符：\"*+,:;&lt;=&gt;?[]|\x7F等。2. 最大允许字符长度为128个字符。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileCopyOption-dstUri: string--><!--Device-FileCopyOption-dstUri: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileCopyOption-fail?: (data: string, code: number) => void--><!--Device-FileCopyOption-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## srcUri

```TypeScript
srcUri: string
```

要拷贝的文件的URI。由于轻量级穿戴设备底层文件系统的限制，该值必须满足以下要求：1. URI 中不得包含以下特殊字符：\"*+,:;&lt;=&gt;?[]|\x7F等。2. 最大允许字符长度为128个字符。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileCopyOption-srcUri: string--><!--Device-FileCopyOption-srcUri: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## success

```TypeScript
success?: (uri: string) => void
```

接口调用成功的回调函数，返回文件要移动到的位置的URI。

**类型：** (uri: string) =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileCopyOption-success?: (uri: string) => void--><!--Device-FileCopyOption-success?: (uri: string) => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

