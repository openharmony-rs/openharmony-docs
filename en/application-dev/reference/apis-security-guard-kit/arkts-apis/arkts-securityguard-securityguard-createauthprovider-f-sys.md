# createAuthProvider (System API)

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## createAuthProvider

```TypeScript
function createAuthProvider(callback: AuthProviderCallback, serviceId: string): AuthProvider
```

Creates an **AuthProvider** session. A maximum of one **AuthProvider** instance is allowed in a process, and a maximum of 16 instances are allowed globally. After the creation succeeds, the **onClientStatusChanged** callback will be used to receive information about existing clients.

**Since:** 26.1.0

**Required permissions:** ohos.permission.AUTH_SERVICE_ACCESS

**Model restriction:** This API can be used only in the stage model.

<!--Device-securityGuard-function createAuthProvider(callback: AuthProviderCallback, serviceId: string): AuthProvider--><!--Device-securityGuard-function createAuthProvider(callback: AuthProviderCallback, serviceId: string): AuthProvider-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

**See also:** [destroyAuthProvider](arkts-securityguard-securityguard-destroyauthprovider-f-sys.md) Destroys an **AuthProvider** session.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AuthProviderCallback](arkts-securityguard-securityguard-authprovidercallback-i-sys.md) | Yes | **AuthProvider** callback. |
| serviceId | string | Yes | Service ID. |

**Return value:**

| Type | Description |
| --- | --- |
| [AuthProvider](arkts-securityguard-securityguard-authprovider-i-sys.md) | **AuthProvider** instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system application attempted to use a system API. |
| 27000001 | Internal system error. <br>The possible causes are as follows: <br>1. The inter-process IPC call fails. <br>2. The system service process is faulty. |
| 27000002 | Provider count of the current process has reached the upper limit. |
| 27000003 | Global provider count has reached the upper limit. |
