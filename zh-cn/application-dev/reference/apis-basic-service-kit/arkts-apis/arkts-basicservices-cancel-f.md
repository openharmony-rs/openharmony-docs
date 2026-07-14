# cancel

## cancel

```TypeScript
function cancel(url: string): void
```

根据url移除一个正在执行的缓存下载任务，已保存的内存缓存和文件缓存不会受到影响。

- 当不存在对应url的任务时无其他效果。
- 使用该方法同步执行时，不阻塞调用线程。

**起始版本：** 18

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 目标资源的地址。支持HTTP和HTTPS协议，长度不超过8192字节。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed. |

**示例：**

```TypeScript
import { cacheDownload, BusinessError } from '@kit.BasicServicesKit';

// 提供缓存下载任务的配置选项。
let options: cacheDownload.CacheDownloadOptions = {};

try {
  // 进行缓存下载，资源若下载成功会被缓存到应用内存或应用沙箱目录的特定文件中。  
  cacheDownload.download("https://www.example.com", options);
} catch (err) {
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}

// 处理其他业务逻辑。

try {
  // 在不需要特定任务缓存时，移除缓存下载任务，已缓存的内容不受影响。
  cacheDownload.cancel("https://www.example.com");
} catch (err) {
  console.error(`Failed to cancel the task. err code: ${err.code}, err message: ${err.message}`);
}

```

