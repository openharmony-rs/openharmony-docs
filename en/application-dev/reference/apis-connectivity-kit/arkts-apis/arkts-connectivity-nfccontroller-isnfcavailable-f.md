# isNfcAvailable

## Modules to Import

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## isNfcAvailable

```TypeScript
function isNfcAvailable(): boolean
```

Checks whether the device supports NFC.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. Use
> [canIUse("SystemCapability.Communication.NFC.Core")](../../../reference/common/init.md#caniuse) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** canIUse("SystemCapability.Communication.NFC.Core")

**System capability:** SystemCapability.Communication.NFC.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the device supports NFC; returns **false** otherwise. |
