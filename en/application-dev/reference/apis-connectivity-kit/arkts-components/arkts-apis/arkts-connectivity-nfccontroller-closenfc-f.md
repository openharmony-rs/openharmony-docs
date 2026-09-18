# closeNfc

## Modules to Import

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## closeNfc

```TypeScript
function closeNfc(): boolean
```

Closes NFC.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. Use
> [disableNfc](arkts-connectivity-nfccontroller-disablenfc-f.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [disableNfc](arkts-connectivity-nfccontroller-disablenfc-f.md)

**Required permissions:** ohos.permission.MANAGE_SECURE_SETTINGS

**System capability:** SystemCapability.Communication.NFC.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |
