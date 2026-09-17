# getSdkVersion

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## getSdkVersion

```TypeScript
function getSdkVersion(options: HuksOptions): string
```

Obtains the SDK version of the current system.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 11.

**Since:** 8

**Deprecated since:** 11

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Empty object (leave this parameter empty). |

**Return value:**

| Type | Description |
| --- | --- |
| string | SDK version obtained. |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* Set options to emptyOptions. */
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.getSdkVersion(emptyOptions);
```
