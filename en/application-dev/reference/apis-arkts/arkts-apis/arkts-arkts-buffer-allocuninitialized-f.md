# allocUninitialized

## Modules to Import

```TypeScript
import { buffer } from '@kit.ArkTS';
```

## allocUninitialized

```TypeScript
function allocUninitialized(size: number): Buffer
```

Creates a **Buffer** object of the specified size, without initializing it. This API does not allocate memory from the buffer pool. You need to use [fill()](arkts-arkts-buffer-buffer-c.md#fill) to initialize the **Buffer** object created.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

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

let buf = buffer.allocUninitialized(10);
buf.fill(0);
console.info(JSON.stringify(buf)); // {"type":"Buffer","data":[0,0,0,0,0,0,0,0,0,0]}
```
