# getState

## Modules to Import

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## getState

```TypeScript
function getState(): NearlinkState
```

Queries the NearLink status.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| [NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md) | NearLink status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the chip does not support it. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
