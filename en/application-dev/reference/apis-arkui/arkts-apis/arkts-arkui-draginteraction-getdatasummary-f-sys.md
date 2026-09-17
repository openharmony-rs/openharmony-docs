# getDataSummary (System API)

## Modules to Import

```TypeScript
import { dragInteraction } from '@kit.ArkUI';
```

## getDataSummary

```TypeScript
function getDataSummary(): Array<Summary>
```

Obtains the data summary of all dragged objects.

**Since:** 11

**System capability:** SystemCapability.Msdp.DeviceStatus.Drag

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[Summary](../arkts-components/arkts-arkui-summary-t.md)&gt; | Data summary of all dragged objects, including their type and data length. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
let summary: Array<dragInteraction.Summary> = dragInteraction.getDataSummary();
console.info(`Drag interaction summary: ${summary}`);
```
