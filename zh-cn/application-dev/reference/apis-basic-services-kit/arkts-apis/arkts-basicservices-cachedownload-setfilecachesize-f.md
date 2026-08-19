# setFileCacheSize

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## setFileCacheSize

```TypeScript
function setFileCacheSize(bytes: long): void
```

设置缓存下载组件能够保存的文件缓存的上限。 - 使用该接口调整缓存大小时，默认使用“LRU”（最近最少使用）方式清除多余的已缓存的文件缓存内容。 - 使用该接口时，若bytes设置为0，将会删除所有缓存文件。 - 该方法为同步方法，不会阻塞调用线程。

**起始版本：** 23

<!--Device-cacheDownload-function setFileCacheSize(bytes: long): void--><!--Device-cacheDownload-function setFileCacheSize(bytes: long): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bytes | long | 是 | 设置的缓存上限。默认值为104857600B（即100MB），最大值不超过4294967296B（即4GB）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter error. Possible causes: <br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 设置文件缓存大小上限。  
  cacheDownload.setFileCacheSize(100 * 1024 * 1024);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set file cache size. err code: ${err.code}, err message: ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 设置文件缓存大小上限。
  cacheDownload.setFileCacheSize(100 * 1024 * 1024);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set file cache size. err code: ${err.code}, err message: ${err.message}`);
}
```

