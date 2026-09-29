# NetworkInfo

```TypeScript
interface NetworkInfo
```

Describes the pre-downloaded network information.

**Since:** 20

<!--Device-cacheDownload-interface NetworkInfo--><!--Device-cacheDownload-interface NetworkInfo-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## dnsServers

```TypeScript
readonly dnsServers: string[]
```

DNS servers used for downloading resources.

**Type:** string[]

**Since:** 20

<!--Device-NetworkInfo-readonly dnsServers: string[]--><!--Device-NetworkInfo-readonly dnsServers: string[]-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## ip

```TypeScript
readonly ip?: string
```

IP address of the URL used for downloading resources. When the DNS resolution fails, the IP address is undefined.

**Type:** string

**Since:** 23

<!--Device-NetworkInfo-readonly ip?: string--><!--Device-NetworkInfo-readonly ip?: string-End-->

**System capability:** SystemCapability.Request.FileTransferAgent
