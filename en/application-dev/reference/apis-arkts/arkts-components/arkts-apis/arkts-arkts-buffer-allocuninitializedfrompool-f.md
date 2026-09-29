# allocUninitializedFromPool

## Modules to Import

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## allocUninitializedFromPool

```TypeScript
function allocUninitializedFromPool(size: number): Buffer
```

Creates a **Buffer** object of the specified size from the buffer pool, without initializing it. You need to use [fill()](arkts-arkts-buffer-buffer-c.md#fill) to initialize the **Buffer** object created.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-buffer-function allocUninitializedFromPool(size: int): Buffer--><!--Device-buffer-function allocUninitializedFromPool(size: int): Buffer-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Size of the **Buffer** object to create, in bytes. |

**Return value:**

| Type | Description |
| --- | --- |
| Buffer | Uninitialized **Buffer** object. |

**Examples**

```TypeScript
import { buffer, JSON } from '@kit.ArkTS';

let buf = buffer.allocUninitializedFromPool(10);
buf.fill(0);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0,0,0,0,0,0,0,0,0]}
```
