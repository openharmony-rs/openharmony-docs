# createA2dpSnkProfile

## Modules to Import

```TypeScript
import { a2dp } from '@kit.ConnectivityKit';
```

## createA2dpSnkProfile

```TypeScript
function createA2dpSnkProfile(): A2dpSinkProfile
```

Create the instance of a2dp sink profile.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [A2dpSinkProfile](arkts-connectivity-a2dp-a2dpsinkprofile-i-sys.md) | Returns the instance of profile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
