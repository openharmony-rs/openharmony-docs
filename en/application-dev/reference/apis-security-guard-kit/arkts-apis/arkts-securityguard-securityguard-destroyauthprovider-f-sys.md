# destroyAuthProvider (System API)

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## destroyAuthProvider

```TypeScript
function destroyAuthProvider(provider: AuthProvider): void
```

Destroys an **AuthProvider** session.

**Since:** 26.1.0

**Required permissions:** ohos.permission.AUTH_SERVICE_ACCESS

**Model restriction:** This API can be used only in the stage model.

<!--Device-securityGuard-function destroyAuthProvider(provider: AuthProvider): void--><!--Device-securityGuard-function destroyAuthProvider(provider: AuthProvider): void-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

**See also:** [createAuthProvider](arkts-securityguard-securityguard-createauthprovider-f-sys.md) Creates an **AuthProvider** session.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| provider | [AuthProvider](arkts-securityguard-securityguard-authprovider-i-sys.md) | Yes | **AuthProvider** instance to be destroyed. It cannot be used after being destroyed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system application attempted to use a system API. |
| 27000001 | Internal system error. <br>The possible causes are as follows: <br>1. The inter-process IPC call fails. <br>2. The system service process is faulty. |
