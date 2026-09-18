# uninit

## Modules to Import

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## uninit

```TypeScript
function uninit(): boolean
```

Uninitializes the active tag resources.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [uninitialize](arkts-connectivity-connectedtag-uninitialize-f.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [uninitialize](arkts-connectivity-connectedtag-uninitialize-f.md)

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.ConnectedTag

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true**: The uninstallation is successful.<br>**false**: The uninstallation fails. |
