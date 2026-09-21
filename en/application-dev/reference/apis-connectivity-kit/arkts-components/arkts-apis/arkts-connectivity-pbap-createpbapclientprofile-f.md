# createPbapClientProfile

## Modules to Import

```TypeScript
import { pbap } from '@kit.ConnectivityKit';
```

## createPbapClientProfile

```TypeScript
function createPbapClientProfile(): PbapClientProfile
```

create the instance of PBAP client profile.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [PbapClientProfile](arkts-connectivity-pbap-pbapclientprofile-i-sys.md) | Returns the instance of pbap client profile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
