# getPeerInfoById

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## getPeerInfoById

```TypeScript
function getPeerInfoById(sessionId: number): PeerInfo | undefined
```

Obtains information about the peer application in the specified session.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | number | Yes | ID of the collaboration session. |

**Return value:**

| Type | Description |
| --- | --- |
| [PeerInfo](arkts-distributedservice-abilityconnectionmanager-peerinfo-i.md) &#124; undefined | Information about the peer application if the corresponding **peerInfo** exists; **undefined** if the session ID is not found. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hilog.info(0x0000, 'testTag', 'getPeerInfoById called');
let sessionId = 100;
const peerInfo = abilityConnectionManager.getPeerInfoById(sessionId);
```
