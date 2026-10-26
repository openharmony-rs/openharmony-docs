# AuthProviderCallback (System API)

```TypeScript
interface AuthProviderCallback
```

Represents the **AuthProvider** callback, which is passed when **createAuthProvider** is called.

**Since:** 26.1.0

<!--Device-securityGuard-interface AuthProviderCallback--><!--Device-securityGuard-interface AuthProviderCallback-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## onClientStatusChanged

```TypeScript
onClientStatusChanged: (clientInfos: AuthClientInfo[]) => void
```

Callback triggered when the status of the associated client session changes.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthProviderCallback-onClientStatusChanged: (clientInfos: AuthClientInfo[]) => void--><!--Device-AuthProviderCallback-onClientStatusChanged: (clientInfos: AuthClientInfo[]) => void-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clientInfos | [AuthClientInfo](arkts-securityguard-securityguard-authclientinfo-i-sys.md)[] | Yes | List of all client session information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system application attempted to use a system API. |
