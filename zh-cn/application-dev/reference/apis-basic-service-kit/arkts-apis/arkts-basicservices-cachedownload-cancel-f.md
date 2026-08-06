# cancel

## cancel

```TypeScript
function cancel(url: string): void
```

根据url移除一个正在执行的缓存下载任务，已保存的内存缓存和文件缓存不会受到影响。 - 当不存在对应url的任务时无其他效果。 - 使用该方法同步执行时，不阻塞调用线程。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-cacheDownload-function cancel(url: string): void--><!--Device-cacheDownload-function cancel(url: string): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 目标资源的地址。支持HTTP和HTTPS协议，长度不超过8192字节。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter error. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 1. Missing mandatory parameters.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 2. Incorrect parameter type.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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
  // 在不需要特定任务缓存时，移除缓存下载任务，已缓存的内容不受影响。
  cacheDownload.cancel("https://www.example.com");
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to cancel the task. err code: ${err.code}, err message: ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

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
  // 在不需要特定任务缓存时，移除缓存下载任务，已缓存的内容不受影响。
  cacheDownload.cancel("https://www.example.com");
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to cancel the task. err code: ${err.code}, err message: ${err.message}`);
}
```

