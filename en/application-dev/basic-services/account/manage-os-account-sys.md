# Managing System Accounts (for System Applications Only)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

The system provides APIs for managing system accounts. After applying for required permissions for your system application, you can use the APIs to create, activate, modify, and delete system accounts. For third-party applications, you can use the APIs to query basic information about system accounts to develop service logic related to system accounts.

## Basic Concepts

### Account Type

Currently, only the following types of system accounts can be created:

| Name  | Value| Description        |
| ------ | ------ | ----------- |
| ADMIN  | 0      | Administrator account.|
| NORMAL | 1      | Normal account.  |
| GUEST  | 2      | Guest account.  |
| PRIVATE<sup>12+</sup> | 1024  | Private account.  |

### Account Information

For details about complete system account information, see [OsAccountInfo](../../reference/apis-basic-services-kit/js-apis-osAccount.md#osaccountinfo).

## Getting Started

1. Request the ohos.permission.MANAGE_LOCAL_ACCOUNTS permission. For details, see [Requesting Permissions for system_basic Applications](../../security/AccessToken/determine-application-mode.md#requesting-permissions-for-system_basic-applications).

2. Import the **osAccount** module.

   <!-- @[import_system_account_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/ManageSystemAccounts.ets) -->

``` TypeScript
import { osAccount, BusinessError } from '@kit.BasicServicesKit';
```

3. Obtain an **AccountManager** instance.

   <!-- @[obtain_account_management_single_instance_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/ManageSystemAccounts.ets) -->

``` TypeScript
let accountManager = osAccount.getAccountManager();
```


## Creating a System Account

The default system account is created during the system initialization. The user cal also create multiple system accounts as required.

**Procedure**

Use [createOsAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#createosaccount) to create a system account with the specified name and type.

<!-- @[specify_nickname_and_type_information_to_create_system_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/ManageSystemAccounts.ets) -->

``` TypeScript
    let name: string = 'Bob';
    let type: osAccount.OsAccountType = osAccount.OsAccountType.NORMAL;

    accountManager.createOsAccount(name, type, (err: BusinessError, osAccountInfo: osAccount.OsAccountInfo)=>{
      if (err) {
        console.error(`createOsAccount code is ${err.code}, message is ${err.message}`);
      } else {
        this.createLocalId = osAccountInfo.localId;
        console.info('createOsAccount osAccountInfo:' + JSON.stringify(osAccountInfo));
      }
    });
```

## Obtaining All System Accounts

The account management page may need to display information about all the system accounts.

**Procedure**

Use [queryAllCreatedOsAccounts](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#queryallcreatedosaccounts) to obtain informatory about all system accounts. 

<!-- @[query_the_full_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/ManageSystemAccounts.ets) -->

``` TypeScript
    accountManager.queryAllCreatedOsAccounts((err: BusinessError, accountArr: osAccount.OsAccountInfo[])=>{
      if (err) {
        console.info(`queryAllCreatedOsAccounts code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('queryAllCreatedOsAccounts accountArr:' + JSON.stringify(accountArr));
      }
    });
```

## Obtaining Information of a System Account

Detailed information about a system account can be obtained based on the account ID.

**Procedure**

Use [queryOsAccountById](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#queryosaccountbyid) to obtain detailed information about a system account.

<!-- @[query_information_of_the_specified_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/ManageSystemAccounts.ets) -->

``` TypeScript
    let localId: number = 100;
    accountManager.queryOsAccountById(localId, (err: BusinessError, accountInfo: osAccount.OsAccountInfo)=>{
      if (err) {
        console.error(`queryOsAccountById code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('queryOsAccountById accountInfo:' + JSON.stringify(accountInfo));
      }
    });
```

## Changing the ProfilePhoto and Nickname of a System Account

Change the profile photo and nickname of a system account as required.

**Procedure**

1. Use [setOsAccountProfilePhoto](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#setosaccountprofilephoto) to change the profile picture of a system account.

   <!-- @[change_system_account_avatar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/ManageSystemAccounts.ets) -->

``` TypeScript
    let localId: number = 100;
    let newPhoto: string = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAAPCAYAAAA/I0V3AAAAAXNSR0IArs4c6QAAAARnQU1BAA'+
      'Cxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAACwSURBVDhPvZLBDYMwDEV/ugsXRjAT0EHCOuFIBwkbdIRewi6unbiAyoGgSn1SFH85+Y'+
      'q/4ljARW62X+LHS8uIzjm4dXUYF+utzBikB52Jo5e5iEPKqpACk7R9NM2RvWm5tIkD2czLCUFNKLD6IjdMHFHDzws285MgGrT0xCtp3WOKHo'+
      '+7q0mP0DZW9pNmoEFUzrQjp5cCnaen2kSJXLFD8ghbXyZCMQf/8e8Ns1XVAG/XAgqKzVnJFAAAAABJRU5ErkJggg=='

    accountManager.setOsAccountProfilePhoto(localId, newPhoto, (err: BusinessError)=>{
      if(err) {
        console.error(`setOsAccountProfilePhoto code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('Successfully updated system account avatar');
      }
    });
```

2. Use [setOsAccountName](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#setosaccountname) to change the system account name.

   <!-- @[change_system_account_name](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/ManageSystemAccounts.ets) -->

``` TypeScript
    let localId: number = 100;
	// ···
    let newName: string = 'Tom';
    accountManager.setOsAccountName(localId, newName, (err: BusinessError) => {
      if (err) {
        console.error(`setOsAccountName failed, code is ${err.code}, message is ${err.message}`);
		// ···
      } else {
        console.info('setOsAccountName successfully');
		// ···
      }
    });
```


## Activating a System Account

System accounts are not activated by default. A system account can be used only after being activated. You can use [activateOsAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#activateosaccount) to activate a system account.

**Procedure**

Use [activateOsAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#activateosaccount) to activate a system account.

<!-- @[activate_system_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/ManageSystemAccounts.ets) -->

``` TypeScript
    let localId: number = 101;
	// ···
    accountManager.activateOsAccount(localId, (err: BusinessError)=>{
      if (err) {
        console.error(`activateOsAccount failed, code is ${err.code}, message is ${err.message}`);
		// ···
      } else {
        console.info('activateOsAccount successfully');
		// ···
      }
    });
```


## Removing a System Account

Remove a system account when it is no longer used.

**Procedure**

Use [removeOsAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#removeosaccount) to remove a system account.

<!-- @[delete_the_specified_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/SystemAccount/entry/src/main/ets/pages/SystemAccount/ManageSystemAccounts.ets) -->

``` TypeScript
    let localId: number = 101;
	// ···
    accountManager.removeOsAccount(localId, (err: BusinessError)=>{
      if (err) {
        console.error(`removeOsAccount failed, code is ${err.code}, message is ${err.message}`);
		// ···
      } else {
        console.info('removeOsAccount successfully');
		// ···
      }
    });
```
