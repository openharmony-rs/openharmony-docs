# createHfpHfProfile

## Modules to Import

```TypeScript
import { hfp } from '@kit.ConnectivityKit';
```

## createHfpHfProfile

```TypeScript
function createHfpHfProfile(): HandsFreeHfProfile
```

create the instance of HF(Hands-Free Unit) for HFP(Hands-Free Profile).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [HandsFreeHfProfile](arkts-connectivity-hfp-handsfreehfprofile-i-sys.md) | Returns the instance of profile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
