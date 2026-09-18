# @ohos.enterprise.accountManager(Account Management)

This module provides device account management capabilities, including forbidding the creation of local accounts.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { accountManager } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [activateOsAccount](arkts-mdm-accountmanager-activateosaccount-f.md) | Switches the system account. Currently, this API is supported only on phones and tablets, and can only switch between normal system accounts created via [createNormalOsAccount](arkts-mdm-accountmanager-createnormalosaccount-f.md) and the default system account (ID: 100). |
| [addOsAccountAsync](arkts-mdm-accountmanager-addosaccountasync-f.md) | Adds an account in the background. This API uses a promise to return the result. This API is applicable to scenarios where enterprises need to create accounts in batches or remotely manage accounts. Accounts can be created without user interaction, improving management efficiency. |
| [createNormalOsAccount](arkts-mdm-accountmanager-createnormalosaccount-f.md) | Creates a normal system account. A maximum of two normal system accounts ([osAccount.OsAccountType](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-osaccounttype-e.md)) can be created. |
| [disallowOsAccountAddition](arkts-mdm-accountmanager-disallowosaccountaddition-f.md) | Users are not allowed to add accounts. After the API is successfully called, the system forbids the specified user or all users from adding new accounts. This API is applicable to enterprise device management scenarios, such as preventing employees from creating local accounts and enhancing device security management. |
| [getDomainAccountPolicy](arkts-mdm-accountmanager-getdomainaccountpolicy-f.md) | Obtains the domain account policy. This API is applicable to enterprise management scenarios, such as querying the current domain account policy configuration and auditing policy compliance. |
| [isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md) | Queries whether a user is not allowed to add an account. |
| [isOsAccountAdditionDisallowed](arkts-mdm-accountmanager-isosaccountadditiondisallowed-f.md) | Queries whether a user is not allowed to add an account. This API is applicable to enterprise audit and compliance check scenarios, helping administrators confirm the execution of account policies. |
| [removeOsAccount](arkts-mdm-accountmanager-removeosaccount-f.md) | Removes a system account. Currently, this API is supported only on phones and tablets. It can remove normal system accounts (of the normal type) created via [createNormalOsAccount](arkts-mdm-accountmanager-createnormalosaccount-f.md) and system accounts (of the admin, normal, and guest types) created via [addOsAccountAsync](arkts-mdm-accountmanager-addosaccountasync-f.md). The default system account (ID: 100) cannot be removed. |
| [setDomainAccountPolicy](arkts-mdm-accountmanager-setdomainaccountpolicy-f.md) | Sets the domain account policy. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addOsAccount](arkts-mdm-accountmanager-addosaccount-f-sys.md) | Adds an account in the background. |
| [disallowAddLocalAccount](arkts-mdm-accountmanager-disallowaddlocalaccount-f-sys.md) | Forbids the creation of local accounts on the device. This API uses an asynchronous callback to return the result. |
| [disallowAddLocalAccount](arkts-mdm-accountmanager-disallowaddlocalaccount-f-sys.md) | Forbids the creation of local accounts on the device. This API uses a promise to return the result. |
| [disallowAddOsAccountByUser](arkts-mdm-accountmanager-disallowaddosaccountbyuser-f-sys.md) | Disallows a user to add accounts. |
| [isAddOsAccountByUserDisallowed](arkts-mdm-accountmanager-isaddosaccountbyuserdisallowed-f-sys.md) | Queries whether to disallow a user to add accounts. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [DomainAccountPolicy](arkts-mdm-accountmanager-domainaccountpolicy-i.md) | Domain account policy. |
