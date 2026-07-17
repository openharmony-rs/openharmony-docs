# FileListResponse

文件列表返回，包含文件列表信息。

**起始版本：** 3

**废弃版本：** 10

<!--Device-unnamed-export interface FileListResponse--><!--Device-unnamed-export interface FileListResponse-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## fileList

```TypeScript
fileList: Array<FileResponse>
```

获取的文件列表，其中每个文件的信息的格式为：{uri:'file1',lastModifiedTime:1589965924479,length:10240,type:?'file'}

**类型：** Array<FileResponse>

**起始版本：** 3

**废弃版本：** 10

<!--Device-FileListResponse-fileList: Array<FileResponse>--><!--Device-FileListResponse-fileList: Array<FileResponse>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

