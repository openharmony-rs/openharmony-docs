# 管理域账号插件（仅对系统应用开放）

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

OEM厂商可以采用插件方式定制化域账号管理能力，系统提供了域账号插件注册和注销能力。

## 开发准备

1. 申请权限，申请流程请参考：[申请应用权限](../../security/AccessToken/determine-application-mode.md#system_basic等级应用申请权限的方式)。
   - ohos.permission.MANAGE_LOCAL_ACCOUNTS
   - ohos.permission.GET_DOMAIN_ACCOUNTS

2. 导入系统账号模块。

   <!-- @[import_the_system_account_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccountsPlugin.ets) -->

3. 获取系统账号管理对象。

   ```ts
   let accountMgr = osAccount.getAccountManager()
   ```

## 注册插件

域插件原型为[DomainPlugin](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#domainplugin9)，域插件开发者需要继承并实现插件原型中定义的接口。开发者可以使用[registerPlugin](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#registerplugin9)接口完成插件注册操作。

具体开发实例如下：

1. 定义插件。

   <!-- @[define_the_plug_in](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccountsPlugin.ets) -->

2. 调用[registerPlugin](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#registerplugin9)注册插件。

   <!-- @[call_the_api_to_register_the_plug_in](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccountsPlugin.ets) -->

## 注销插件

当插件不再使用时，开发者可以使用[unregisterPlugin](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#unregisterplugin9)接口注销插件。

具体开发实例如下：

<!-- @[call_the_api_to_log_out_the_plug_in](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/DomainAccount/entry/src/main/ets/pages/DomainAccount/ManageDomainAccountsPlugin.ets) -->
