# @ohos.account.distributedAccount(Distributed Account Management)

The distributedAccount module provides APIs for managing distributed accounts, including querying and updating account login states. This module is applicable to multi-device collaboration, improving the consistency and user experience of cross-device account management. Typical application scenarios include multi-device collaboration, distributed data synchronization, and cross-device capability calling.

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { distributedAccount } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getDistributedAccountAbility](arkts-basicservices-distributedaccount-getdistributedaccountability-f.md) | Obtains a **DistributedAccountAbility** instance. |

### Interfaces

| Name | Description |
| --- | --- |
| [DistributedAccountAbility](arkts-basicservices-distributedaccount-distributedaccountability-i.md) | Provides APIs for querying and updating the login state of a distributed account. You must obtain a **DistributedAccountAbility** instance first. |
| [DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md) | Represents the distributed account information about an OS account. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DistributedAccountAbility](arkts-basicservices-distributedaccount-distributedaccountability-i-sys.md) | Provides APIs for querying and updating the login state of a distributed account. You must obtain a **DistributedAccountAbility** instance first. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [DistributedAccountStatus](arkts-basicservices-distributedaccount-distributedaccountstatus-e.md) | Enumerates the statuses of a distributed account. |
