# ResourceInfo

预下载的资源信息。

**起始版本：** 20

<!--Device-cacheDownload-interface ResourceInfo--><!--Device-cacheDownload-interface ResourceInfo-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## size

```TypeScript
readonly size: number
```

预下载资源解压后的大小，单位为字节（B）。当值为正整数时表示资源下载成功，-1表示下载失败。

**类型：** number

**起始版本：** 20

<!--Device-ResourceInfo-readonly size: long--><!--Device-ResourceInfo-readonly size: long-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

