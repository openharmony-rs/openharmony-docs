# NetworkInfo

Describes the pre-downloaded network information.

**Since:** 20

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

**System capability:** SystemCapability.Request.FileTransferAgent

## ip

```TypeScript
readonly ip?: string
```

IP address of the URL used for downloading resources. When the DNS resolution fails, the IP address is undefined.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.Request.FileTransferAgent
