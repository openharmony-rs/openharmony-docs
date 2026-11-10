# getPinHistoryCheckRange (System API)

## Modules to Import

```TypeScript
import { pinAuth } from '@kit.UserAuthenticationKit';
```

## getPinHistoryCheckRange

```TypeScript
function getPinHistoryCheckRange(userId: number): number | undefined
```

Gets the number of recent historical PINs to check when the PIN is changed.

**Since:** 26.1.0

**Required permissions:** ohos.permission.USE_USER_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

<!--Device-pinAuth-function getPinHistoryCheckRange(userId: int): int | undefined--><!--Device-pinAuth-function getPinHistoryCheckRange(userId: int): int | undefined-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. <br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| number &#124; undefined | The number of recent historical PINs to check. Returns undefined if the history check range has not been set for the specified user. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |
| [12500008](../errorcode-useriam.md#12500008-parameter-verification-failed) | The parameter is out of range. |
