# FileReadArrayBufferResponse

文件读取返回，包含读取到的文件内容。

**起始版本：** 3

**废弃版本：** 10

<!--Device-unnamed-export interface FileReadArrayBufferResponse--><!--Device-unnamed-export interface FileReadArrayBufferResponse-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## buffer

```TypeScript
buffer: Uint8Array
```

获取的文件列表，其中每个文件的信息的格式为：{uri:'file1',lastModifiedTime:1589965924479,length:10240,type:?'file'}

**类型：** Uint8Array

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileReadArrayBufferResponse-buffer: Uint8Array--><!--Device-FileReadArrayBufferResponse-buffer: Uint8Array-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

