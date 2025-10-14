# 管理域账号（仅对系统应用开放）

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

用户可以在系统中添加域账号，后续可以域账号身份登录、使用系统。

## 开发准备

1. 申请权限，申请流程请参考：[申请应用权限](../../security/AccessToken/determine-application-mode.md#system_basic等级应用申请权限的方式)。
   - ohos.permission.MANAGE_LOCAL_ACCOUNTS
   - ohos.permission.GET_DOMAIN_ACCOUNTS

2. 导入系统账号模块。

   <!-- @[import_the_system_account_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
import { osAccount, BusinessError } from '@kit.BasicServicesKit';
```


3. 获取系统账号管理对象。

   <!-- @[obtain_the_system_account_management_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
let osAccountMgr = osAccount.getAccountManager();
```


## 判断指定域账号是否存在

在添加域账号之前，应该先判断域账号是否存在。开发者可以使用[hasAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#hasaccount10)接口进行判断。

具体开发实例如下：

1. 定义待判断的域账号信息。

   <!-- @[define_the_domain_account_information_to_be_determined](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    let domainAccountInfo: osAccount.DomainAccountInfo = {
      accountName: 'testAccountName',
      domain: 'testDomain'
    }
```


2. 调用[hasAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#hasaccount10)接口。

   <!-- @[call_the_hasaccount_operation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    osAccount.DomainAccountManager.hasAccount(domainAccountInfo).then((isAccountExisted: boolean)=>{
      console.info('execute hasAccount successfully, isAccountExisted:' + JSON.stringify(isAccountExisted));
	// ···
    }).catch((err: BusinessError)=>{
      console.error(`execute hasAccount code is ${err.code}, message is ${err.message}`);
    });
```


## 添加域账号

用户在设置中添加其他域账号，允许其他域账号用户使用同一设备。开发者可以使用[createOsAccountForDomain](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#createosaccountfordomain8)完成此操作。

具体开发实例如下：

1. 定义域账号信息，指定域名、账号名、账号标识（可选）。

   <!-- @[define_the_domain_account_information](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    let domainInfo: osAccount.DomainAccountInfo = {
      domain: 'testDomain',
      accountName: 'testAccountName'
    };
```

2. 指定类型和域账号信息，调用[createOsAccountForDomain](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#createosaccountfordomain8)接口在设备上创建一个域账号。

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


## 删除域账号

用户可以删除不再使用的域账号。由于域账号和系统账号是一一绑定关系，开发者可以使用[removeOsAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#removeosaccount)接口删除与目标域账号绑定的系统账号，进而实现删除域账号。

具体开发实例如下：

1. 调用[getOsAccountLocalIdForDomain](../../reference/apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalidfordomain9)方法，根据域账号信息获取系统账号ID。

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


2. 调用[removeOsAccount](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#removeosaccount)方法删除域账号。

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


## 查询域账号信息

用户通过身份认证后，可以查询自己或他人的域账号信息。开发者可以使用[getAccountInfo](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#getaccountinfo10)接口完成此操作。

具体开发实例如下：

1. 定义查询选项，可以指定需要查询的域名和账号名。选项的类型为[GetDomainAccountInfoOptions](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#getdomainaccountinfooptions10)。

   <!-- @[define_query_options](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccounts.ets) -->

``` TypeScript
    let options: osAccount.GetDomainAccountInfoOptions = {
      domain: 'testDomain',
      accountName: 'testAccountName'
    }
```


2. 调用[getAccountInfo](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#getaccountinfo10)接口查询域账号信息。

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

