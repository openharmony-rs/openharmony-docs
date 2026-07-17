# clearMemoryCache

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## clearMemoryCache

```TypeScript
function clearMemoryCache(): void
```

清除缓存下载内容的内存缓存。

**起始版本：** 23

<!--Device-cacheDownload-function clearMemoryCache(): void--><!--Device-cacheDownload-function clearMemoryCache(): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**示例：**

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
  
cacheDownload.clearMemoryCache();

```

