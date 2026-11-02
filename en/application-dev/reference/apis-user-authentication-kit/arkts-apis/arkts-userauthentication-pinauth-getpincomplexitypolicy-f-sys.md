# getPinComplexityPolicy (System API)

## Modules to Import

```TypeScript
import { pinAuth } from '@kit.UserAuthenticationKit';
```

## getPinComplexityPolicy

```TypeScript
function getPinComplexityPolicy(userId: number): PinComplexityPolicy | undefined
```

Gets PIN complexity check policy and description.

**Since:** 26.1.0

**Required permissions:** ohos.permission.USE_USER_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

<!--Device-pinAuth-function getPinComplexityPolicy(userId: int): PinComplexityPolicy | undefined--><!--Device-pinAuth-function getPinComplexityPolicy(userId: int): PinComplexityPolicy | undefined-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. <br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinComplexityPolicy](arkts-userauthentication-pinauth-pincomplexitypolicy-i-sys.md) &#124; undefined | PIN complexity check policy and description. Returns undefined if no complexity policy has been set for the specified user or if both an empty regular expression and an empty regular expression description are set for the specified user. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |
| [12500008](../errorcode-useriam.md#12500008-parameter-verification-failed) | The parameter is out of range. |
