# Managing Application Accounts

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

You can use the [application account SDK](../../reference/apis-basic-services-kit/js-apis-appAccount.md) to manage application accounts.

When an application is uninstalled, the account data of the application will be automatically deleted. When a local account is deleted, the account data of all applications of the local account will be automatically deleted.

## Before You Start

1. Import the **appAccount** module.

   <!-- @[import_the_application_account_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { appAccount, BusinessError } from '@kit.BasicServicesKit';
```


2. Obtain an **AppAccountManager** instance.

   <!-- @[obtain_the_instance_object_of_the_application_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
const appAccountManager = appAccount.createAppAccountManager();
```


## Creating an Application Account

Create an application account for an application user.

**Procedure**

1. Specify the account name and optional parameters.

    <!-- @[parameter_preparation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    let name: string = 'ZhangSan';
    let options: appAccount.CreateAccountOptions = {
      customData: {
        age: '10'
      }
    };
```


2. Use [createAccount](../../reference/apis-basic-services-kit/js-apis-appAccount.md#createaccount9) to create an application account based on the specified parameters.

   <!-- @[create_an_app_account_based_on_the_name_and_options](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    appAccountManager.createAccount(name, options).then(()=>{
      console.info('createAccount successfully');
	// ···
    }).catch((err: BusinessError)=>{
       console.error(`createAccount failed, error: code is ${err.code}, message is ${err.message}`);
	// ···
    });
```


## Obtaining Application Account List

**Procedure**


Use [getAllAccounts](../../reference/apis-basic-services-kit/js-apis-appAccount.md#getallaccounts9) to obtain the application account list.

   <!-- @[query_the_account_list](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    appAccountManager.getAllAccounts().then((data: appAccount.AppAccountInfo[]) => {
      console.info('getAllAccounts successfully, data: ' + JSON.stringify(data));
	// ···
    }).catch((err: BusinessError) => {
      console.error(`getAllAccounts failed, code is ${err.code}, message is ${err.message}`);
	// ···
    });
```


## Accessing Account Credentials

**Procedure**

1. Specify the account name, credential type, and credential.

   <!-- @[prepare_parameters_to_specify_the_account_name_credential_type_and_credential](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    let name: string = 'ZhangSan';
    let credentialType: string = 'PIN_SIX';
    let credential: string = 'xxxxxx';
```


2. Use [getCredential](../../reference/apis-basic-services-kit/js-apis-appAccount.md#getcredential9) to obtain the account credential.

   <!-- @[obtain_the_credentials_for_your_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    appAccountManager.getCredential(name, credentialType).then((data: string) => {
      console.info('getCredential successfully, data: ' + data);
	// ···
    }).catch((err: BusinessError) => {
      console.error(`getCredential failed, code is ${err.code}, message is ${err.message}`);
	// ···
    });
```


3. Use [setCredential](../../reference/apis-basic-services-kit/js-apis-appAccount.md#setcredential9) to set the account credential.

   <!-- @[set_the_credentials_for_your_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    await appAccountManager.setCredential(name, credentialType, credential).then(() => {
      console.info('setCredential successfully');
    }).catch((err: BusinessError) => {
      console.error(`setCredential failed: code is ${err.code}, message is ${err.message}`);
	// ···
    });
```


## Accessing Custom Account Data

**Procedure**

1. Specify the account name and custom data.

   <!-- @[prepare_parameters_specify_the_account_name_and_custom_key_values](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    let name: string = 'ZhangSan';
    let key: string = 'age';
    let value: string = '12';
```


2. Use [setCustomData](../../reference/apis-basic-services-kit/js-apis-appAccount.md#setcustomdata9) to customize account data.

   <!-- @[set_up_custom_data_for_your_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    await appAccountManager.setCustomData(name, key, value).then(() => {
      console.info('setCustomData successfully');
    }).catch((err: BusinessError) => {
      console.error(`setCustomData failed: code is ${err.code}, message is ${err.message}`);
	// ···
    });
```


3. Use [getCustomData](../../reference/apis-basic-services-kit/js-apis-appAccount.md#getcustomdata9) to obtain the custom account data.

   <!-- @[obtain_the_custom_data_of_the_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    appAccountManager.getCustomData(name, key).then((data: string) => {
      console.info('getCustomData successfully, data: ' + data);
	// ···
    }).catch((err: BusinessError) => {
      console.error(`getCustomData failed, code is ${err.code}, message is ${err.message}`);
	// ···
    });
```


## Accessing the Account Authentication Token

**Procedure**

1. Specify the account name, account owner, authorization type, and authentication token.

   <!-- @[prepare_parameters_to_specify_the_account_name_account_owner_authorization_type_and_authorization_token](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    let name: string = 'ZhangSan';
    let owner: string = 'com.samples.managerapplicationaccount';
    let authType: string = 'getSocialData';
    let token: string = 'xxxxxx';
```


2. Use [setAuthToken](../../reference/apis-basic-services-kit/js-apis-appAccount.md#setauthtoken9) to set an authorization token for the specified authentication type.

   <!-- @[set_the_authorization_token_for_the_specified_authorization_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    await appAccountManager.setAuthToken(name, authType, token).then(() => {
      console.info('setAuthToken successfully');
    }).catch((err: BusinessError) => {
      console.error(`setAuthToken failed: code is ${err.code}, message is ${err.message}`);
	// ···
    });
```


3. Use [getAuthToken](../../reference/apis-basic-services-kit/js-apis-appAccount.md#getauthtoken9) to obtain the authentication token of the specified authentication type.

   <!-- @[obtain_an_authorization_token_for_the_specified_authorization_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    await appAccountManager.getAuthToken(name, owner, authType).then((data: string) => {
      console.info('getAuthToken successfully, data: ' + data);
	// ···
    }).catch((err: BusinessError) => {
      console.error(`getAuthToken failed, code is ${err.code}, message is ${err.message}`);
	// ···
    });
```


## Removing an Application Account

Remove the application account after the user logs out of the system.

**Procedure**

Use [removeAccount](../../reference/apis-basic-services-kit/js-apis-appAccount.md#removeaccount9) to remove the application account.

   <!-- @[delete_account](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManagerApplicationAccount/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    let name: string = 'ZhangSan';
    appAccountManager.removeAccount(name).then(() => {
      console.info('removeAccount successfully');
	// ···
    }).catch((err: BusinessError) => {
      console.error(`removeAccount failed, code is ${err.code}, message is ${err.message}`);
	// ···
    });
```


<!--RP1-->
<!--RP1End-->
