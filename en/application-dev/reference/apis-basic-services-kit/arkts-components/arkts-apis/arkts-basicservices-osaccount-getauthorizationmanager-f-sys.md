# getAuthorizationManager (System API)

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## getAuthorizationManager

```TypeScript
function getAuthorizationManager(): AuthorizationManager
```

Obtains the current OS account authorization manager.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [AuthorizationManager](arkts-basicservices-authorization-authorizationmanager-i.md) | Instance object of the OS account authorization manager. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
let authorizationManager: osAccount.AuthorizationManager = osAccount.getAuthorizationManager();
```
