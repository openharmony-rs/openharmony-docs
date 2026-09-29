# createAppAccountManager

## Modules to Import

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## createAppAccountManager

```TypeScript
function createAppAccountManager(): AppAccountManager
```

Creates an **AppAccountManager** object.

**Since:** 7

<!--Device-appAccount-function createAppAccountManager(): AppAccountManager--><!--Device-appAccount-function createAppAccountManager(): AppAccountManager-End-->

**System capability:** SystemCapability.Account.AppAccount

**Return value:**

| Type | Description |
| --- | --- |
| [AppAccountManager](arkts-basicservices-appaccount-appaccountmanager-i.md) | **AppAccountManager** object created. |

**Examples**

```TypeScript
let appAccountManager: appAccount.AppAccountManager = appAccount.createAppAccountManager();
```
