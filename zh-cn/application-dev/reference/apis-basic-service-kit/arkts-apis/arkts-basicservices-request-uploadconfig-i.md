# UploadConfig

上传任务的配置信息。

**起始版本：** 6

<!--Device-request-interface UploadConfig--><!--Device-request-interface UploadConfig-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## begins

```TypeScript
begins?: number
```

上传任务开始时读取的文件起点，单位为字节（B）。默认值为0，取值范围为闭区间，表示从头开始传输。

**类型：** number

**起始版本：** 11

<!--Device-UploadConfig-begins?: long--><!--Device-UploadConfig-begins?: long-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## data

```TypeScript
data: Array<RequestData>
```

请求的表单数据。

**类型：** Array&lt;RequestData&gt;

**起始版本：** 6

<!--Device-UploadConfig-data: Array<RequestData>--><!--Device-UploadConfig-data: Array<RequestData>-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## ends

```TypeScript
ends?: number
```

上传任务结束时读取的文件终点，单位为字节（B）。默认值为-1，取值范围为闭区间，表示传输到整个文件末尾结束。

**类型：** number

**起始版本：** 11

<!--Device-UploadConfig-ends?: long--><!--Device-UploadConfig-ends?: long-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## files

```TypeScript
files: Array<File>
```

要上传的文件列表。文件以HTTP的multipart/form-data格式提交。

**类型：** Array&lt;File&gt;

**起始版本：** 6

<!--Device-UploadConfig-files: Array<File>--><!--Device-UploadConfig-files: Array<File>-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## header

```TypeScript
header: Object
```

添加要包含在上传请求中的HTTP或HTTPS标志头。

**类型：** Object

**起始版本：** 6

<!--Device-UploadConfig-header: Object--><!--Device-UploadConfig-header: Object-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## index

```TypeScript
index?: number
```

任务的路径索引，默认值为0。

**类型：** number

**起始版本：** 11

<!--Device-UploadConfig-index?: int--><!--Device-UploadConfig-index?: int-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## method

```TypeScript
method: string
```

HTTP请求方法：POST、PUT，缺省为POST。使用POST新增资源，使用PUT修改资源。

**类型：** string

**起始版本：** 6

<!--Device-UploadConfig-method: string--><!--Device-UploadConfig-method: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

## url

```TypeScript
url: string
```

资源地址。从API 6到API 14，最大长度为2048个字符；从API 15开始，最大长度为8192个字符。支持[HTTP拦截](../../../basic-services/request/app-file-upload-download.md#http拦截)功能。

**类型：** string

**起始版本：** 6

<!--Device-UploadConfig-url: string--><!--Device-UploadConfig-url: string-End-->

**系统能力：** SystemCapability.MiscServices.Upload

