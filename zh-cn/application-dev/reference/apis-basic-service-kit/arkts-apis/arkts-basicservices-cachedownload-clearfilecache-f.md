# clearFileCache

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## clearFileCache

```TypeScript
function clearFileCache(): void
```

清除保存下载内容的文件缓存。

**起始版本：** 23

<!--Device-cacheDownload-function clearFileCache(): void--><!--Device-cacheDownload-function clearFileCache(): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**示例：**

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
  
cacheDownload.clearFileCache();

```

