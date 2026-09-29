# getAccountManager

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## getAccountManager

```TypeScript
function getAccountManager(): AccountManager
```

Obtains an **AccountManager** instance.

**Since:** 7

<!--Device-osAccount-function getAccountManager(): AccountManager--><!--Device-osAccount-function getAccountManager(): AccountManager-End-->

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| [AccountManager](arkts-basicservices-osaccount-accountmanager-i.md) | **AccountManager** instance obtained. |

**Examples**

```TypeScript
let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
```
