# Authenticating Domain Accounts (for System Applications Only)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

Authenticate a domain account before unlocking the screen or when the login session fails.

## Getting Started

Import the **osAccount** module.

<!-- @[import_the_system_account_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
import { osAccount, BusinessError } from '@kit.BasicServicesKit';
```


## Domain Account Authentication by Password

The domain account can be authenticated by password. You can use [auth](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#auth10) to implement this operation. To call this API, the application must have the ohos.permission.ACCESS_USER_AUTH_INTERNAL permission.

**Procedure**

1. Request the ohos.permission.ACCESS_USER_AUTH_INTERNAL permission. For details, see [Requesting Permissions for system_basic Applications](../../security/AccessToken/determine-application-mode.md#requesting-permissions-for-system_basic-applications).

2. Obtain user input information, including the domain account and its password.

   <!-- @[get_user_input](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
    let domainAccountInfo: osAccount.DomainAccountInfo = {
      domain: 'CHINA',
      accountName: 'zhangsan'
    };
    let credential: Uint8Array = new Uint8Array([0]);
```


3. Define the callback used to return the authentication result.

   <!-- @[define_the_callback_for_the_authentication_result](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
    let callback: osAccount.IUserAuthCallback = {
      onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
        console.info('auth resultCode = ' + resultCode);
        console.info('auth authResult = ' + JSON.stringify(authResult));
		// ...

      }
    };
```


4. Use [auth](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#auth10) to authenticate the domain account by password.

   <!-- @[perform_password_authentication](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
    try {
      osAccount.DomainAccountManager.auth(domainAccountInfo, credential, callback);
    } catch (e) {
      const err = e as BusinessError;
      console.error(`auth exception = ${err.message}`);
    }
```


## Domain Account Authentication by Dialog

If the domain account password is unavailable, display a dialog box to authentication the domain account. You can use [authWithPopup](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#authwithpopup10) to implement this operation.

**Procedure**

1. Define the callback used to return the authentication result.

   <!-- @[define_the_callback_object_of_the_authentication_result](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
    let callback: osAccount.IUserAuthCallback = {
      onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
        console.info('authWithPopup resultCode = ' + resultCode);
        console.info('authWithPopup authResult = ' + JSON.stringify(authResult));
		// ...
      }
    }
```


2. Use [authWithPopup](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#authwithpopup10) to authenticate the domain account in a dialog box displayed.

   <!-- @[call_operation_to_authenticate_the_current_domain_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
    try {
      osAccount.DomainAccountManager.authWithPopup(callback)
    } catch (e) {
      const err = e as BusinessError;
      console.error(`authWithPopup exception = ${err.message}`);
	// ...
    }
```
