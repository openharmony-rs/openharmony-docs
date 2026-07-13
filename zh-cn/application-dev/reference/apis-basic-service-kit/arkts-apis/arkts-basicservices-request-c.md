# Request

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [request:request](arkts-basicservices-request-n.md)

**系统能力：** SystemCapability.MiscServices.Download

## download

```TypeScript
static download(options: DownloadRequestOptions): void
```

下载文件，无返回值。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** downloadFile(context:

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | DownloadRequestOptions | 是 | 下载的配置信息。 |

## onDownloadComplete

```TypeScript
static onDownloadComplete(options: OnDownloadCompleteOptions): void
```

获取下载任务状态，无返回值。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** show(id:

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | OnDownloadCompleteOptions | 是 | 监听下载任务的配置信息。 |

## upload

```TypeScript
static upload(options: UploadRequestOptions): void
```

上传文件，无返回值。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** uploadFile(context:

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | UploadRequestOptions | 是 | 上传的配置信息。 |

