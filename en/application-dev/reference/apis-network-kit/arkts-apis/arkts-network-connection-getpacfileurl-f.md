# getPacFileUrl

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getPacFileUrl

```TypeScript
function getPacFileUrl(): string
```

Obtains the URL of the current PAC script.

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | URL of the current PAC script. If no PAC script is available, an empty string is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

let pacFileUrl = connection.getPacFileUrl();
console.info(pacFileUrl);
```
