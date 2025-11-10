# Managing Domain Accounts (for System Applications Only)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

The user can add a domain account to a device so that the domain account user can log in to the system and use the device.

## Getting Started

1. Request the following permissions. For details, see [Requesting Permissions for system_basic Applications](../../security/AccessToken/determine-application-mode.md#requesting-permissions-for-system_basic-applications).
   - ohos.permission.MANAGE_LOCAL_ACCOUNTS
   - ohos.permission.GET_DOMAIN_ACCOUNTS

2. Import the **osAccount** module.

   <!-- @[import_the_system_account_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
import { osAccount, BusinessError } from '@kit.BasicServicesKit';
```


3. Obtain an **AccountManager** instance.

   <!-- @[obtain_the_system_account_management_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
let osAccountMgr = osAccount.getAccountManager();
```


## Checking for a Domain Account

Before adding a domain account, the user may need to check whether the domain account exists. You can use [hasAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#hasaccount10) to check whether a domain account exists.

**Procedure**

1. Define the domain account to check.

   <!-- @[define_the_domain_account_information_to_be_determined](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    let domainAccountInfo: osAccount.DomainAccountInfo = {
      accountName: 'testAccountName',
      domain: 'testDomain'
    }
```


2. Use [hasAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#hasaccount10) to check whether the domain account exists.

   <!-- @[call_the_hasaccount_operation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    osAccount.DomainAccountManager.hasAccount(domainAccountInfo).then((isAccountExisted: boolean)=>{
      console.info('execute hasAccount successfully, isAccountExisted:' + JSON.stringify(isAccountExisted));
	// ···
    }).catch((err: BusinessError)=>{
      console.error(`execute hasAccount code is ${err.code}, message is ${err.message}`);
    });
```


## Adding a Domain Account

The user can add a domain account in **Settings** to allow the domain account user to log in to and use the device. You can use [createOsAccountForDomain](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#createosaccountfordomain8) to implement this operation.

**Procedure**

1. Define domain account information, including the domain name, account name, and account ID (optional).

   <!-- @[define_the_domain_account_information](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    let domainInfo: osAccount.DomainAccountInfo = {
      domain: 'testDomain',
      accountName: 'testAccountName'
    };
```

2. Use [createOsAccountForDomain](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#createosaccountfordomain8) to create a domain account on the device.

   <!-- @[create_a_domain_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    try {
      osAccountMgr.createOsAccountForDomain(osAccount.OsAccountType.NORMAL, domainInfo,
        (err: BusinessError, osAccountInfo: osAccount.OsAccountInfo)=>{
          console.error(`createOsAccountForDomain exception: code is ${err.code}, message is ${err.message}`);
          console.info('createOsAccountForDomain osAccountInfo:' + JSON.stringify(osAccountInfo));
		// ···
        });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`createOsAccountForDomain exception: code is ${e.code}, message is ${e.message}`);
	// ···
    }
```


## Removing a Domain Account

The user can remove the domain account that is not required. Since a domain account is in one-to-one relationship with a system account, you can use [removeOsAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#removeosaccount) to delete the system account. The domain account is deleted as well.

**Procedure**

1. Use [getOsAccountLocalIdForDomain](../../reference/apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalidfordomain9) to obtain the system account ID based on the domain account information.

   <!-- @[obtain_the_system_account_id_based_on_the_domain_account_information](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    let domainInfo: osAccount.DomainAccountInfo = {
      domain: 'testDomain',
      accountName: 'testAccountName'
    };
    let localId: number = 0;
    try {
      localId = await osAccountMgr.getOsAccountLocalIdForDomain(domainInfo);
    } catch (e) {
      const err = e as BusinessError;
      console.error(`getOsAccountLocalIdForDomain exception: code is ${err.code}, message is ${err.message}`);
	// ···
    }
```


2. Use [removeOsAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#removeosaccount) to remove the system account.

   <!-- @[delete_the_domain_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    try {
      osAccountMgr.removeOsAccount(localId, (err: BusinessError)=>{
        if (err) {
          console.error(`removeOsAccount failed, code is ${err.code}, message is ${err.message}`);
		// ···
        } else {
          console.info('removeOsAccount successfully');
		// ···
        }
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`removeOsAccount exception: code is ${err.code}, message is ${err.message}`);
    }
```


## Obtaining Domain Account Information

After passing the authentication, the user can query their own or others' domain account information. You can use [getAccountInfo](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#getaccountinfo10) to implement this operation.

**Procedure**

1. Specify the query options, including the domain name and account name. The option type is [GetDomainAccountInfoOptions](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#getdomainaccountinfooptions10).

   <!-- @[define_query_options](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    let options: osAccount.GetDomainAccountInfoOptions = {
      domain: 'testDomain',
      accountName: 'testAccountName'
    }
```


2. Use [getAccountInfo](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#getaccountinfo10) to obtain domain account information.

   <!-- @[query_the_domain_account_information](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    try {
      osAccount.DomainAccountManager.getAccountInfo(options,
        (err: BusinessError, result: osAccount.DomainAccountInfo) => {
          if (err) {
            console.error(`call getAccountInfo failed, code is ${err.code}, message is ${err.message}`);
			// ···
          } else {
            console.info('getAccountInfo result: ' + result);
			// ···
          }
        });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`getAccountInfo exception = code is ${err.code}, message is ${err.message}`);
	// ···
    }
```
