# AuthProvider (System API)

```TypeScript
interface AuthProvider
```

Authorization service provider class, which is created by the **createAuthProvider** factory function.

**Since:** 26.1.0

<!--Device-securityGuard-interface AuthProvider--><!--Device-securityGuard-interface AuthProvider-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## requestAuthResult

```TypeScript
requestAuthResult(event: AuthEventInfo): Promise<AuthResult>
```

Authorization result of a request event.

**Since:** 26.1.0

**Required permissions:** ohos.permission.AUTH_SERVICE_ACCESS

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthProvider-requestAuthResult(event: AuthEventInfo): Promise<AuthResult>--><!--Device-AuthProvider-requestAuthResult(event: AuthEventInfo): Promise<AuthResult>-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [AuthEventInfo](arkts-securityguard-securityguard-autheventinfo-i-sys.md) | Yes | Authorization event information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AuthResult](arkts-securityguard-securityguard-authresult-i-sys.md)&gt; | Promise used to return the authorization result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system application attempted to use a system API. |
| 27000001 | Internal system error. <br>The possible causes are as follows: <br>1. The inter-process IPC call fails. <br>2. The system service process is faulty. |
| 27000004 | Concurrent request count has reached the upper limit. |
