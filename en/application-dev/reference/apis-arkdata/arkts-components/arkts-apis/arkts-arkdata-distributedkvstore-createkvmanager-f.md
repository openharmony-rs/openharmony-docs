# createKVManager

## Modules to Import

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## createKVManager

```TypeScript
function createKVManager(config: KVManagerConfig): KVManager
```

Creates a **KVManager** instance for KV store management.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [KVManagerConfig](arkts-arkdata-distributedkvstore-kvmanagerconfig-i.md) | Yes | Configuration of the **KVManager** instance, including the bundle name (cannot be empty) of the caller and user information. |

**Return value:**

| Type | Description |
| --- | --- |
| [KVManager](arkts-arkdata-distributedkvstore-kvmanager-i.md) | **KVManager** instance created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
Stage model:
```

```TypeScript
FA model:
```
