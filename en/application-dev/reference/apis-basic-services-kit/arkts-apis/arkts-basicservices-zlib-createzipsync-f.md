# createZipSync

## Modules to Import

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## createZipSync

```TypeScript
function createZipSync(): Zip
```

Creates this **Zip** instance. A **Zip** instance is returned upon a success.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

**Return value:**

| Type | Description |
| --- | --- |
| [Zip](arkts-basicservices-zlib-zip-i.md) | The **Zip** instance created. |

**Examples**

```TypeScript
import { zlib } from '@kit.BasicServicesKit';

let zip = zlib.createZipSync();
```
