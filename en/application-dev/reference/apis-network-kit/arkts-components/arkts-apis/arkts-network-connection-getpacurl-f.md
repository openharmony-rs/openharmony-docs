# getPacUrl

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getPacUrl

```TypeScript
function getPacUrl(): string
```

Obtains the URL of the system-level PAC script.

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | URL of the PAC script. If the PAC script does not exist, error code 2100003 is reported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

let pacUrl = connection.getPacUrl();
```
