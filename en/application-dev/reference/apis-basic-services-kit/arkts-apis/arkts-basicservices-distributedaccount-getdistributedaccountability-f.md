# getDistributedAccountAbility

## Modules to Import

```TypeScript
import { distributedAccount } from '@kit.BasicServicesKit';
```

## getDistributedAccountAbility

```TypeScript
function getDistributedAccountAbility(): DistributedAccountAbility
```

Obtains a **DistributedAccountAbility** instance.

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| [DistributedAccountAbility](arkts-basicservices-distributedaccount-distributedaccountability-i.md) | **DistributedAccountAbility** instance obtained. This instance provides APIs for querying and updating the login state of a distributed account. |

**Examples**

```TypeScript
// Obtain a DistributedAccountAbility instance.
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
```
