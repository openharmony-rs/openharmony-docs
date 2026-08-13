# setMemoryCacheSize

## setMemoryCacheSize

```TypeScript
function setMemoryCacheSize(bytes: long): void
```

设置缓存下载组件能够保存的内存缓存上限。 - 使用该接口调整缓存大小时，默认使用“LRU”（最近最少使用）方式清除多余的已缓存的内存缓存内容。 - 该方法为同步方法，不阻塞调用线程。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cacheDownload-function setMemoryCacheSize(bytes: long): void--><!--Device-cacheDownload-function setMemoryCacheSize(bytes: long): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bytes | long | 是 | 设置的缓存上限。默认值为0B，最大值不超过1073741824B（即1GB）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter error. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 设置内存缓存大小上限。  
  cacheDownload.setMemoryCacheSize(10 * 1024 * 1024);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set memory cache size. err code: ${err.code}, err message: ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 设置内存缓存大小上限。
  cacheDownload.setMemoryCacheSize(10 * 1024 * 1024);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to set memory cache size. err code: ${err.code}, err message: ${err.message}`);
}
```

