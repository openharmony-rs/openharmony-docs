# FileDeleteOption

可选项类型，支持delete接口使用。

**起始版本：** 3

**废弃版本：** 10

<!--Device-unnamed-export interface FileDeleteOption--><!--Device-unnamed-export interface FileDeleteOption-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileDeleteOption-complete?: () => void--><!--Device-FileDeleteOption-complete?: () => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileDeleteOption-fail?: (data: string, code: number) => void--><!--Device-FileDeleteOption-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## success

```TypeScript
success?: () => void
```

接口调用成功的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileDeleteOption-success?: () => void--><!--Device-FileDeleteOption-success?: () => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## uri

```TypeScript
uri: string
```

删除文件的URI，不能是应用资源路径。由于轻量级穿戴设备底层文件系统的限制，该值必须满足以下要求：1. URI 中不得包含以下特殊字符：\"*+,:;&lt;=&gt;?[]|\x7F等。2. 最大允许字符长度为128个字符。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileDeleteOption-uri: string--><!--Device-FileDeleteOption-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

