# getPinValidityPeriod (System API)

## Modules to Import

```TypeScript
import { pinAuth } from '@kit.UserAuthenticationKit';
```

## getPinValidityPeriod

```TypeScript
function getPinValidityPeriod(userId: number): number | undefined
```

Get PIN validity period.

**Since:** 26.1.0

**Required permissions:** ohos.permission.USE_USER_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

<!--Device-pinAuth-function getPinValidityPeriod(userId: int): long | undefined--><!--Device-pinAuth-function getPinValidityPeriod(userId: int): long | undefined-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. <br>The value should be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| number &#124; undefined | Validity period of a PIN, in milliseconds. If no validity period or zero is set for the specified userId, or if the validity period is set to 0, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [12500002](../errorcode-useriam.md#12500002-common-error-code-of-the-identity-authentication-system) | General operation error. |
| [12500008](../errorcode-useriam.md#12500008-parameter-verification-failed) | The parameter is out of range. |
