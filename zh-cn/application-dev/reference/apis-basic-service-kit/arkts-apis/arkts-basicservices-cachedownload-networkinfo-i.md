# NetworkInfo

预下载的网络信息。

**起始版本：** 20

<!--Device-cacheDownload-interface NetworkInfo--><!--Device-cacheDownload-interface NetworkInfo-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## dnsServers

```TypeScript
readonly dnsServers: string[]
```

下载资源时使用的dns服务器列表。

**类型：** string[]

**起始版本：** 20

<!--Device-NetworkInfo-readonly dnsServers: string[]--><!--Device-NetworkInfo-readonly dnsServers: string[]-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## ip

```TypeScript
readonly ip?: string
```

下载资源时url的ip地址。当dns解析失败时，ip为undefined。

**类型：** string

**起始版本：** 23

<!--Device-NetworkInfo-readonly ip?: string--><!--Device-NetworkInfo-readonly ip?: string-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

