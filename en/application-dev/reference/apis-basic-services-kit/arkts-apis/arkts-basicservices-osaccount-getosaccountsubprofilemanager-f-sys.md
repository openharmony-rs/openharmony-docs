# getOsAccountSubProfileManager (System API)

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## getOsAccountSubProfileManager

```TypeScript
function getOsAccountSubProfileManager(): OsAccountSubProfileManager
```

Obtains the OS account sub-profile manager.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [OsAccountSubProfileManager](arkts-basicservices-osaccount-osaccountsubprofilemanager-i-sys.md) | Instance object of the OS account sub-profile manager. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
let subProfileManager: osAccount.OsAccountSubProfileManager = osAccount.getOsAccountSubProfileManager();
```
