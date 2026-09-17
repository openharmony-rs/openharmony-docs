# init

## Modules to Import

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## init

```TypeScript
function init(): boolean
```

Initializes the active tag chip.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. Use
> [initialize](arkts-connectivity-connectedtag-initialize-f.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [initialize](arkts-connectivity-connectedtag-initialize-f.md)

**Required permissions:** ohos.permission.NFC_TAG

**System capability:** SystemCapability.Communication.ConnectedTag

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true**: The initialization is successful.<br>**false**: The initialization fails. |
