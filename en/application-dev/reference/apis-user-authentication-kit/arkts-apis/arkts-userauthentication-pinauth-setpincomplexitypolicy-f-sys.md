# setPinComplexityPolicy (System API)

## Modules to Import

```TypeScript
import { pinAuth } from '@kit.UserAuthenticationKit';
```

## setPinComplexityPolicy

```TypeScript
function setPinComplexityPolicy(userId: number, policy: PinComplexityPolicy): void
```

Set the PIN complexity check policy and description. After setting this policy, users must create or change their lock screen PIN to match the specified complexity regular expression.

**Since:** 26.1.0

**Required permissions:** ohos.permission.USE_USER_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

<!--Device-pinAuth-function setPinComplexityPolicy(userId: int, policy: PinComplexityPolicy): void--><!--Device-pinAuth-function setPinComplexityPolicy(userId: int, policy: PinComplexityPolicy): void-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. If the value is 0, the policy takes effect for all users; otherwise, the policy takes effect for the specified user. <br>The value should be an integer. |
| policy | [PinComplexityPolicy](arkts-userauthentication-pinauth-pincomplexitypolicy-i-sys.md) | Yes | PIN complexity check policy and description. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |
| [12500008](../errorcode-useriam.md#12500008-parameter-verification-failed) | The parameter is out of range. |
