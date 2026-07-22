# OnFileReadyBatch（系统接口）

```TypeScript
type OnFileReadyBatch = (error: BusinessError<void>, files: Array<File>) => void
```

一批文件准备好发送给客户端时触发的回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-backup-type OnFileReadyBatch = (error: BusinessError<void>, files: Array<File>) => void--><!--Device-backup-type OnFileReadyBatch = (error: BusinessError<void>, files: Array<File>) => void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | [BusinessError](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md)&lt;void&gt; | 是 | 获取文件句柄失败时返回的错误对象。  |
| files | Array&lt;File&gt; | 是 | 获取到的文件句柄数组。  |

