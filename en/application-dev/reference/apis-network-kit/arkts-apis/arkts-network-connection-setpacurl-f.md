# setPacUrl

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## setPacUrl

```TypeScript
function setPacUrl(pacUrl: string): void
```

Sets the URL of the system-level Proxy Auto Config (PAC) script.

> **NOTE:** 
> 
> Only the script address can be set. The proxy function cannot be parsed or enabled. To set the script and enable
> the proxy, call the [setPacFileUrl](arkts-network-connection-setpacfileurl-f.md) API.

**Since:** 15

**Required permissions:** ohos.permission.SET_PAC_URL

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pacUrl | string | Yes | URL of the PAC script. Note that this URL will not be verified by the API. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

let pacUrl = "xxx";
connection.setPacUrl(pacUrl);
```
