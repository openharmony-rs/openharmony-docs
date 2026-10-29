# getUserRecognitionMgr

## Modules to Import

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getUserRecognitionMgr

```TypeScript
function getUserRecognitionMgr(): UserRecognitionMgr | null
```

Obtains a [UserRecognitionMgr](arkts-userauthentication-userauth-userrecognitionmgr-i.md) instance for querying and subscribing to user recognition results. A new **UserRecognitionMgr** instance is returned each time this API is called.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ACCESS_USER_PASSIVE_RECOGNITION

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-userAuth-function getUserRecognitionMgr(): UserRecognitionMgr | null--><!--Device-userAuth-function getUserRecognitionMgr(): UserRecognitionMgr | null-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [UserRecognitionMgr](arkts-userauthentication-userauth-userrecognitionmgr-i.md) &#124; null | User recognition manager instance. If the device does not support this capability, null is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let mgr = userAuth.getUserRecognitionMgr();
if (mgr == null) {
  console.error('device does not support user recognition');
} else {
  console.info(`get user recognition mgr: ${mgr}`);
}
```
