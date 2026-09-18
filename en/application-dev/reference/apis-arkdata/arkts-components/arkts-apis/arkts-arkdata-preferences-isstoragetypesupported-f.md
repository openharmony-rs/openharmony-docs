# isStorageTypeSupported

## Modules to Import

```TypeScript
import { preferences } from '@kit.ArkData';
```

## isStorageTypeSupported

```TypeScript
function isStorageTypeSupported(type: StorageType): boolean
```

Checks whether the specified storage type is supported. This API returns the result synchronously. If the storage type is supported, **true** is returned. Otherwise, **false** is returned.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [StorageType](arkts-arkdata-preferences-storagetype-e.md) | Yes | Storage type to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the storage type is supported; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types |

**Examples**

```TypeScript
let xmlType = preferences.StorageType.XML;
let gskvType = preferences.StorageType.GSKV;
let isXmlSupported = preferences.isStorageTypeSupported(xmlType);
let isGskvSupported = preferences.isStorageTypeSupported(gskvType);
console.info("Is xml supported in current platform: " + isXmlSupported);
console.info("Is gskv supported in current platform: " + isGskvSupported);
```
