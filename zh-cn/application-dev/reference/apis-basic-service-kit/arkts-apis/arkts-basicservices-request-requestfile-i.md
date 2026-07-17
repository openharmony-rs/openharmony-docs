# RequestFile

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [File](arkts-basicservices-request-file-i.md)

<!--Device-unnamed-export interface RequestFile--><!--Device-unnamed-export interface RequestFile-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## 导入模块

```TypeScript
import { UploadResponse, RequestData, DownloadRequestOptions, DownloadResponse, RequestFile, OnDownloadCompleteOptions, OnDownloadCompleteResponse, UploadRequestOptions } from '@kit.BasicServicesKit';
```

## filename

```TypeScript
filename?: string
```

multipart 提交时，请求头中的文件名。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** filename

<!--Device-RequestFile-filename?: string--><!--Device-RequestFile-filename?: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## name

```TypeScript
name?: string
```

multipart 提交时，表单项目的名称，缺省为file。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** name

<!--Device-RequestFile-name?: string--><!--Device-RequestFile-name?: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## type

```TypeScript
type?: string
```

文件的内容类型，默认根据文件名或路径的后缀获取。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** contentType

<!--Device-RequestFile-type?: string--><!--Device-RequestFile-type?: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## uri

```TypeScript
uri: string
```

文件的本地存储路径。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**替代接口：** path

<!--Device-RequestFile-uri: string--><!--Device-RequestFile-uri: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

