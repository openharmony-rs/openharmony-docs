# isBasSupported (System API)

## Modules to Import

```TypeScript
import { bas } from '@kit.ConnectivityKit';
```

## isBasSupported

```TypeScript
function isBasSupported(): boolean
```

Determine whether the local device can obtain the battery level of the remote device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the battery service is enabled; returns false otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |
| 2900099 | Operation failed. |
