# 认证域账号（仅对系统应用开放）

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

当需要验证域账号身份（比如屏幕解锁、登录会话失效等场景）时，可以使用系统提供的接口对域账号进行身份认证。

## 开发准备

导入系统账号模块。

<!-- @[import_the_system_account_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
import { osAccount, BusinessError } from '@kit.BasicServicesKit';
```


## 使用密码认证域账号

用户可以使用密码认证域账号。开发者可以使用[auth](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#auth10)接口完成此操作。此外使用该接口，应用还需要申请ohos.permission.ACCESS_USER_AUTH_INTERNAL权限。

具体开发实例如下：

1. 申请权限：ohos.permission.ACCESS_USER_AUTH_INTERNAL。申请流程请参考：[申请应用权限](../../security/AccessToken/determine-application-mode.md#system_basic等级应用申请权限的方式)。

2. 获取用户输入，包括域账号信息和域账号密码。

   <!-- @[get_user_input](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
    let domainAccountInfo: osAccount.DomainAccountInfo = {
      domain: 'CHINA',
      accountName: 'zhangsan'
    };
    let credential: Uint8Array = new Uint8Array([0]);
```


3. 定义认证结果回调。

   <!-- @[define_the_callback_for_the_authentication_result](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
    let callback: osAccount.IUserAuthCallback = {
      onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
        console.info('auth resultCode = ' + resultCode);
        console.info('auth authResult = ' + JSON.stringify(authResult));
		// ···

      }
    };
```


4. 调用[auth](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#auth10)接口进行密码认证。

   <!-- @[perform_password_authentication](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
    try {
      osAccount.DomainAccountManager.auth(domainAccountInfo, credential, callback);
    } catch (e) {
      const err = e as BusinessError;
      console.error(`auth exception = ${err.message}`);
    }
```


## 弹窗认证域账号

在无法获取用户密码的情况下，需要认证域账号时，可以请求系统弹窗验证域账号用户。开发者可以使用[authWithPopup](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#authwithpopup10)完成此操作。

具体开发实例如下：

1. 定义认证结果回调对象。

   <!-- @[define_the_callback_object_of_the_authentication_result](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
    let callback: osAccount.IUserAuthCallback = {
      onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
        console.info('authWithPopup resultCode = ' + resultCode);
        console.info('authWithPopup authResult = ' + JSON.stringify(authResult));
		// ···
      }
    }
```


2. 调用[authWithPopup](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#authwithpopup10)接口弹窗认证当前域账号。

   <!-- @[call_operation_to_authenticate_the_current_domain_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/AuthenticationDomainAccount.ets) -->

``` TypeScript
    try {
      osAccount.DomainAccountManager.authWithPopup(callback)
    } catch (e) {
      const err = e as BusinessError;
      console.error(`authWithPopup exception = ${err.message}`);
	// ···
    }
```

