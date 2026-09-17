# getNfcState

## Modules to Import

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## getNfcState

```TypeScript
function getNfcState(): NfcState
```

Obtains the NFC state.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Core

**Return value:**

| Type | Description |
| --- | --- |
| [NfcState](arkts-connectivity-nfccontroller-nfcstate-e.md) | NFC state obtained. For details, see [NfcState](arkts-connectivity-nfccontroller-nfcstate-e.md). |

**Examples**

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';

// Obtain the NFC state.
let nfcState: nfcController.NfcState = nfcController.getNfcState();
console.info("nfcController on callback nfcstate: " + nfcState);
```
