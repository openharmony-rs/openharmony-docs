# getDownloadInfo

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## getDownloadInfo

```TypeScript
function getDownloadInfo(url: string): DownloadInfo | undefined
```

基于url获取预下载的下载信息。信息存储在内存中的下载信息列表，当应用程序退出时清除。

- 如果下载信息列表中能够找到指定url，返回该url对应的最新[DownloadInfo](arkts-basicservices-cachedownload-downloadinfo-i.md)。  
- 如果下载信息列表中找不到指定url，返回undefined。  
- 在缓存下载信息时，如果在该url下已存在缓存信息，新的缓存内容会覆盖旧缓存。  
- 目标信息在存储到内存时，使用“LRU”（最近最少使用）方式替换已存在的缓存数据。

**起始版本：** 20

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-cacheDownload-function getDownloadInfo(url: string): DownloadInfo | undefined--><!--Device-cacheDownload-function getDownloadInfo(url: string): DownloadInfo | undefined-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 待查询的url，最大长度为8192字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DownloadInfo](arkts-basicservices-request-downloadinfo-i.md) | 返回对应url的下载信息，url未记录时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |

