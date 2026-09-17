# FileListOption

可选项类型，支持list接口使用。

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## 导入模块

```TypeScript
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success?: (data: FileListResponse) => void
```

接口调用成功的回调函数。返回[FileListResponse](arkts-corefile-system-file-filelistresponse-depr-i.md#filelistresponse)。

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [FileListResponse](arkts-corefile-system-file-filelistresponse-depr-i.md) | 是 |  |

## uri

```TypeScript
uri: string
```

目录URI。由于轻量级穿戴设备底层文件系统的限制，该值必须满足以下要求：
1. URI 中不得包含以下特殊字符：\"*+,:;&lt;=&gt;?[]|\x7F等。
2. 最大允许字符长度为128个字符。

**类型：** string

**起始版本：** 3

**废弃版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite
