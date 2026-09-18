# getCallStateSync

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## getCallStateSync

```TypeScript
function getCallStateSync(): CallState
```

Obtains the call status.

**Since:** 10

**System capability:** SystemCapability.Telephony.CallManager

**Return value:**

| Type | Description |
| --- | --- |
| [CallState](arkts-telephony-call-callstate-e.md) | Promise used to return the result. |

**Examples**

```TypeScript
let callState: call.CallState = call.getCallStateSync();
console.info(`the call state is:` + callState);
```
