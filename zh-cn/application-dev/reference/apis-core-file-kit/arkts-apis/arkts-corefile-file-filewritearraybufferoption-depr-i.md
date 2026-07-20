# FileWriteArrayBufferOption

可选项类型，支持writeArrayBuffer接口使用。

**起始版本：** 3

**废弃版本：** 10

<!--Device-unnamed-export interface FileWriteArrayBufferOption--><!--Device-unnamed-export interface FileWriteArrayBufferOption-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## append

```TypeScript
append?: boolean
```

是否追加模式，默认为false。当设置为true时，position参数无效。true为追加，false为不追加。

**类型：** boolean

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteArrayBufferOption-append?: boolean--><!--Device-FileWriteArrayBufferOption-append?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## buffer

```TypeScript
buffer: Uint8Array
```

写入的Buffer。

**类型：** Uint8Array

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteArrayBufferOption-buffer: Uint8Array--><!--Device-FileWriteArrayBufferOption-buffer: Uint8Array-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteArrayBufferOption-complete?: () => void--><!--Device-FileWriteArrayBufferOption-complete?: () => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteArrayBufferOption-fail?: (data: string, code: number) => void--><!--Device-FileWriteArrayBufferOption-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## position

```TypeScript
position?: number
```

文件写入的起始偏移位置，单位为Byte，默认为0。

**类型：** number

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteArrayBufferOption-position?: number--><!--Device-FileWriteArrayBufferOption-position?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## success

```TypeScript
success?: () => void
```

接口调用成功的回调函数。

**类型：** () =&gt; void

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteArrayBufferOption-success?: () => void--><!--Device-FileWriteArrayBufferOption-success?: () => void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## uri

```TypeScript
uri: string
```

本地文件URI，如果文件不存在会创建文件。由于轻量级穿戴设备底层文件系统的限制，该值必须满足以下要求：1. URI 中不得包含以下特殊字符：\"*+,:;<=>?[]|\x7F等。2. 最大允许字符长度为128个字符。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileWriteArrayBufferOption-uri: string--><!--Device-FileWriteArrayBufferOption-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

