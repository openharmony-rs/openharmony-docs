# openNfc

## Modules to Import

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## openNfc

```TypeScript
function openNfc(): boolean
```

Opens NFC.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. Use
> [enableNfc](arkts-connectivity-nfccontroller-enablenfc-f.md) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [enableNfc](arkts-connectivity-nfccontroller-enablenfc-f.md)

**Required permissions:** ohos.permission.MANAGE_SECURE_SETTINGS

**System capability:** SystemCapability.Communication.NFC.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |
