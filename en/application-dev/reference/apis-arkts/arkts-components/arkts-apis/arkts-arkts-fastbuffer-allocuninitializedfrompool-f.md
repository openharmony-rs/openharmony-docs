# allocUninitializedFromPool

## Modules to Import

```TypeScript
import { fastbuffer } from '@kit.ArkTS';
```

## allocUninitializedFromPool

```TypeScript
function allocUninitializedFromPool(size: number): FastBuffer
```

Allocates a new FastBuffer for a fixed size bytes. The FastBuffer will not be initially filled.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | The desired size (in bytes) of the new FastBuffer |

**Return value:**

| Type | Description |
| --- | --- |
| [FastBuffer](arkts-arkts-fastbuffer-fastbuffer-c.md) | Return a new allocated FastBuffer |

**Examples**

```TypeScript
import { fastbuffer } from '@kit.ArkTS';

let buf = fastbuffer.allocUninitializedFromPool(10);
buf.fill(0);
// "buf":[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
```
