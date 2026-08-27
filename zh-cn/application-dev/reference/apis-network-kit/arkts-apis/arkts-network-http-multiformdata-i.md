# MultiFormData

多部分表单数据的类型。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
```

## contentType

```TypeScript
contentType: string
```

数据类型，如'text/plain'，'image/png', 'image/jpeg', 'audio/mpeg', 'video/mp4'等。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

## data

```TypeScript
data?: string | Object | ArrayBuffer
```

表单数据内容。

**类型：** string \| Object \| ArrayBuffer

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

## filePath

```TypeScript
filePath?: string
```

此参数将文件路径指向的文件内容设置为表单数据，如果未指定data内容，则必须设置filePath。  
**说明：**需传入文件管理模块支持的格式，可以通过文件管理的[access](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-access-f.md)接口，验证文件是否存在且可访问。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

## name

```TypeScript
name: string
```

数据名称。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

## remoteFileName

```TypeScript
remoteFileName?: string
```

上传到服务器保存为文件的名称。  
**说明：**指定该字段后，请求头中会添加filename字段，表示上传到服务器文件的名称。（1）当上传数据为文件时，若通过data字段指定文件内容，通常需要设置remoteFileName字段，用以指定上传到服务器文件的名称（实际结果与服务器具体行为有关）；若通过filePath字段指定文件路径，请求头中会自动添加 filename字段，其默认值为filePath中的文件名称，如需特殊指定，也可通过本字段对filename重新设置。（2）当上传数据为二进制格式时，则必须设置remoteFileName字段。（3）当使用filePath上传文件时，设置remoteFileName字段会影响文件传输方式。若设置了remoteFileName，系统会先尝试将文件完整读入内存后再发送；若未设置remoteFileName，系统会使用流式 传输方式直接从文件读取并发送数据。对于大文件（如超过100MB）的上传场景，建议不设置remoteFileName，使用系统默认的流式传输方式，避免内存占用过高。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack
