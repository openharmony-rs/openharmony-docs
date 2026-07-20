# download

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

<a id="download"></a>
## download

```TypeScript
function download(url: string, options: CacheDownloadOptions): void
```

启动一个缓存下载任务，若传输成功，则将数据下载到内存缓存和文件缓存中。

- 目标资源经过HTTP传输自动解压后的大小不能超过20971520B（即20MB），否则不会保存到内存缓存或文件缓存中。  
- 在缓存下载数据时，如果在该url下已存在缓存内容，新的缓存内容会覆盖旧缓存内容。  
- 目标资源在存储到内存缓存或文件缓存中时，依照缓存下载组件的各类型缓存大小上限决定文件是否存储到指定位置，并默认使用“LRU”（最近最少使用）方式替换已有缓存内容。  
- 该方法为同步方法，不阻塞调用线程。

**起始版本：** 18

**需要权限：** ohos.permission.INTERNET

<!--Device-cacheDownload-function download(url: string, options: CacheDownloadOptions): void--><!--Device-cacheDownload-function download(url: string, options: CacheDownloadOptions): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 目标资源的地址。支持HTTP和HTTPS协议，长度不超过8192字节。 |
| options | [CacheDownloadOptions](arkts-basicservices-cachedownload-cachedownloadoptions-i.md) | 是 | 目标资源的缓存下载选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed. |

**示例：**

```TypeScript
import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';

// 提供缓存下载任务的配置选项。
let options: cacheDownload.CacheDownloadOptions = {
  headers: { 'Accept': 'application/json' },
  sslType: cacheDownload.SslType.TLS,
  caPath: '/path/to/ca.pem',
  cacheStrategy: cacheDownload.CacheStrategy.FORCE,
  retry: { maxRetryCount: 1 },
  timeout: {
    networkCheckTimeout: 20,
    httpTotalTimeout: 60,
  }
};

try {
  // 进行缓存下载，资源若下载成功会被缓存到应用内存或应用沙箱目录的特定文件中。
  cacheDownload.download("https://www.example.com", options);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}

```

