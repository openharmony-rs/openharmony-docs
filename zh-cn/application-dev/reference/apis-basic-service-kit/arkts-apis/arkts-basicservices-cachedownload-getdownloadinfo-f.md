# getDownloadInfo

## getDownloadInfo

```TypeScript
function getDownloadInfo(url: string): DownloadInfo | undefined
```

基于url获取预下载的下载信息。信息存储在内存中的下载信息列表，当应用程序退出时清除。 - 如果下载信息列表中能够找到指定url，返回该url对应的最新[DownloadInfo](arkts-basicservices-cachedownload-downloadinfo-i.md#DownloadInfo)。 - 如果下载信息列表中找不到指定url，返回undefined。 - 在缓存下载信息时，如果在该url下已存在缓存信息，新的缓存内容会覆盖旧缓存。 - 目标信息在存储到内存时，使用“LRU”（最近最少使用）方式替换已存在的缓存数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

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
| DownloadInfo | 返回对应url的下载信息，url未记录时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 设置下载信息列表大小。  
  cacheDownload.setDownloadInfoListSize(2048);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set download information list size. err code: ${err.code}, err message: ${err.message}`);
}

// 提供缓存下载任务的配置选项。
let options: cacheDownload.CacheDownloadOptions = {};

try {
  // 进行缓存下载，资源若下载成功会被缓存到应用内存或应用沙箱目录的特定文件中。  
  cacheDownload.download("https://www.example.com", options);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}

// 处理其他业务逻辑。

try {
  // 在缓存下载完成后，获取缓存下载的信息。
  let downloadInfo = cacheDownload.getDownloadInfo("https://www.example.com");
  if (downloadInfo == undefined) {
    console.error(`CacheDownload get download info undefined.`);
  } else {
    console.info(`CacheDownload get download info : ${JSON.stringify(downloadInfo)}`);
  }
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to get download info. err code: ${err.code}, err message: ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 设置下载信息列表大小。
  cacheDownload.setDownloadInfoListSize(2048);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set download information list size. err code: ${err.code}, err message: ${err.message}`);
}

// 提供缓存下载任务的配置选项。
let options: cacheDownload.CacheDownloadOptions = {};

try {
  // 进行缓存下载，资源若下载成功会被缓存到应用内存或应用沙箱目录的特定文件中。
  cacheDownload.download("https://www.example.com", options);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}

// 处理其他业务逻辑。
try {
  // 在缓存下载完成后，获取缓存下载的信息。
  let downloadInfo = cacheDownload.getDownloadInfo("https://www.example.com");
  if (downloadInfo == undefined) {
    console.info(`CacheDownload get download info undefined.`);
  } else {
    console.info(`CacheDownload get download info : ${JSON.stringify(downloadInfo)}`);
  }
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to get download info. err code: ${err.code}, err message: ${err.message}`);
}
```

