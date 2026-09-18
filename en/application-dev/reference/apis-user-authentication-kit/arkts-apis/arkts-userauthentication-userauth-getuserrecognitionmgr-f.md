# getUserRecognitionMgr

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getUserRecognitionMgr

```TypeScript
function getUserRecognitionMgr(): UserRecognitionMgr | null
```

Obtains a [UserRecognitionMgr](arkts-userauthentication-userauth-userrecognitionmgr-i.md) instance, which is used to query and subscribe to the user recognition result.

> **NOTE:** 

> Each call returns a new **UserRecognitionMgr** instance. Keep the same instance for paired on/off calls.

> If the device does not support this capability, **null** is returned.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ACCESS_USER_PASSIVE_RECOGNITION

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [UserRecognitionMgr](arkts-userauthentication-userauth-userrecognitionmgr-i.md) &#124; null | User recognition manager instance. Returns **null** if the device does not support this capability. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
