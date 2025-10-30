# Managing Domain Account Plugins (for System Applications Only)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

The system provides APIs for registering and unregistering a domain account plugin, which is used to customize domain account management.

## Getting Started

1. Request the following permissions. For details, see [Requesting Permissions for system_basic Applications](../../security/AccessToken/determine-application-mode.md#requesting-permissions-for-system_basic-applications).
   - ohos.permission.MANAGE_LOCAL_ACCOUNTS
   - ohos.permission.GET_DOMAIN_ACCOUNTS

2. Import the **osAccount** module.

   <!-- @[import_the_system_account_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccountsPlugin.ets) -->

``` TypeScript
import { osAccount, AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
```


3. Obtain an **AccountManager** instance.

   ```ts
   let accountMgr = osAccount.getAccountManager()
   ```

## Registering a Domain Account Plugin

The domain account plugin prototype is [DomainPlugin](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#domainplugin9). The domain account plugin must inherit and implement the **DomainPlugin** APIs. You can use [registerPlugin](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#registerplugin9) to register a plugin.

**Procedure**

1. Define the plugin.

   <!-- @[define_the_plug_in](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccountsPlugin.ets) -->

``` TypeScript
let plugin: osAccount.DomainPlugin = {
  auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
    callback: osAccount.IUserAuthCallback) => {
    console.info('plugin auth domain' + domainAccountInfo.domain);
    console.info('plugin auth accountName' + domainAccountInfo.accountName);
    console.info('plugin auth accountId' + domainAccountInfo.accountId);

    let result: osAccount.AuthResult = {
      token: new Uint8Array([0]),
      remainTimes: 5,
      freezingTime: 0
    };
    callback.onResult(0, result);
  },
  authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
    callback: osAccount.IUserAuthCallback) => {
    console.info('plugin authWithPopup domain' + domainAccountInfo.domain);
    console.info('plugin authWithPopup accountName' + domainAccountInfo.accountName);
    console.info('plugin authWithPopup accountId' + domainAccountInfo.accountId);

    let result: osAccount.AuthResult = {
      token: new Uint8Array([0]),
      remainTimes: 5,
      freezingTime: 0
    };
    callback.onResult(0, result);
  },
  authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo,
    token: Uint8Array, callback: osAccount.IUserAuthCallback) => {
    console.info('plugin authWithToken domain' + domainAccountInfo.domain);
    console.info('plugin authWithToken accountName' + domainAccountInfo.accountName);
    console.info('plugin authWithToken accountId' + domainAccountInfo.accountId);
    let result: osAccount.AuthResult = {
      token: new Uint8Array([0]),
      remainTimes: 5,
      freezingTime: 0
    };
    callback.onResult(0, result);
  },
  getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
    callback: AsyncCallback<osAccount.DomainAccountInfo>) => {
    console.info('plugin getAccountInfo domain');
    let domainAccountId = Date.now().toString();
    let code: BusinessError = {
      code: 0,
      name: 'mock_name',
      message: 'mock_message'
    };
    let domainStr: string = '';
    if (options.domain != undefined) {
      domainStr = options.domain
    }
    let accountInfo: osAccount.DomainAccountInfo = {
      domain: domainStr,
      accountName: options.accountName,
      accountId: domainAccountId,
      isAuthenticated: false
    };
    callback(code, accountInfo);
  },
  getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
    callback: AsyncCallback<osAccount.AuthStatusInfo>) => {

    console.info('plugin getAuthStatusInfo domain' + domainAccountInfo.domain);
    console.info('plugin getAuthStatusInfo accountName' + domainAccountInfo.accountName);
    console.info('plugin getAuthStatusInfo accountId' + domainAccountInfo.accountId);

    let code: BusinessError = {
      code: 0,
      name: 'mock_name',
      message: 'mock_message'
    };
    let statusInfo: osAccount.AuthStatusInfo = {
      remainTimes: 5,
      freezingTime: 0
    };
    callback(code, statusInfo);
  },
  bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
    callback: AsyncCallback<void>) => {
    console.info('plugin bindAccount domain' + domainAccountInfo.domain);
    console.info('plugin bindAccount accountName' + domainAccountInfo.accountName);
    console.info('plugin bindAccount accountId' + domainAccountInfo.accountId);
    let code: BusinessError = {
      code: 0,
      name: 'mock_name',
      message: 'mock_message'
    };
    callback(code);
  },
  unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {
    console.info('plugin unbindAccount domain' + domainAccountInfo.domain);
    console.info('plugin unbindAccount accountName' + domainAccountInfo.accountName);
    console.info('plugin unbindAccount accountId' + domainAccountInfo.accountId);
  },
  isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
    callback: AsyncCallback<boolean>) => {
    console.info('plugin isAccountTokenValid domain' + domainAccountInfo.domain);
    console.info('plugin isAccountTokenValid accountName' + domainAccountInfo.accountName);
    console.info('plugin isAccountTokenValid accountId' + domainAccountInfo.accountId);
    let code: BusinessError = {
      code: 0,
      name: 'mock_name',
      message: 'mock_message'
    };
    callback(code, true);
  },
  getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {
    console.info('plugin getAccessToken domain')
    let code: BusinessError = {
      code: 0,
      name: 'mock_name',
      message: 'mock_message'
    };
    let token: Uint8Array = new Uint8Array([0]);
    callback(code, token);
  }
}
```


2. Use [registerPlugin](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#registerplugin9) to register the plug-in.

   <!-- @[call_the_api_to_register_the_plug_in](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccountsPlugin.ets) -->

``` TypeScript
    try {
      osAccount.DomainAccountManager.registerPlugin(plugin)
      console.info('registerPlugin success');
	// ···
    } catch (e) {
      const err = e as BusinessError;
      console.error(`registerPlugin err: code is ${err.code}, message is ${err.message}`);
	// ···
    }
```


## Unregistering a Domain Account Plugin

Use [unregisterPlugin](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#unregisterplugin9) to unregister a domain account plugin that is not required.

**Procedure**

<!-- @[call_the_api_to_log_out_the_plug_in](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccountsPlugin.ets) -->

``` TypeScript
    try {
      osAccount.DomainAccountManager.unregisterPlugin();
      console.info('unregisterPlugin success.');
	// ···
    } catch (e) {
      const err = e as BusinessError;
      console.error(`unregisterPlugin failed, code is ${err.code}, message is ${err.message}`);
	// ···
    }
```
