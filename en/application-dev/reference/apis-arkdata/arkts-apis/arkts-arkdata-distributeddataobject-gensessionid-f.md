# genSessionId

## Modules to Import

```TypeScript
import { distributedDataObject } from '@kit.ArkData';
```

## genSessionId

```TypeScript
function genSessionId(): string
```

Creates a random session ID.

**Since:** 8

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Return value:**

| Type | Description |
| --- | --- |
| string | Session ID created. |

**Examples**

```TypeScript
let sessionId: string = distributedDataObject.genSessionId();
```
