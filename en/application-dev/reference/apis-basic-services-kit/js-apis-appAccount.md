# @ohos.account.appAccount (Application Account Management)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

The **appAccount** module provides APIs for adding, deleting, modifying, and querying application account information, and supports inter-application authentication and distributed data synchronization.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { appAccount } from '@kit.BasicServicesKit';
```


## appAccount.createAppAccountManager

createAppAccountManager(): AppAccountManager

Creates an **AppAccountManager** object.

**System capability**: SystemCapability.Account.AppAccount

**Return value**

| Type               | Description          |
| ----------------- | ------------ |
| AppAccountManager | **AppAccountManager** object created.|

**Example**
  ```ts
  let appAccountManager: appAccount.AppAccountManager = appAccount.createAppAccountManager();
  ```

## AppAccountManager

Implements application account management.

### createAccount<sup>9+</sup>

createAccount(name: string, callback: AsyncCallback&lt;void&gt;): void

Creates an application account with the given name. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                   | Mandatory | Description              |
| -------- | ------------------------- | ----- | -------------------- |
| name     | string                    | Yes   | Name of the application account to create.         |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name. |
| 12300004 | Account already exists. |
| 12300007 | The number of accounts reaches the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.createAccount('WangWu', (err: BusinessError) => { 
      if (err) {
        console.error('createAccount code: ' + JSON.stringify(err));
      } else {
        console.log('createAccount successful.');
      }
    });
  } catch (err) {
    console.error('createAccount err: ' + JSON.stringify(err));
  }
  ```

### createAccount<sup>9+</sup>

createAccount(name: string, options: CreateAccountOptions, callback: AsyncCallback&lt;void&gt;): void

Creates an application account with custom data. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name      | Type                       | Mandatory  | Description                                      |
| --------- | ------------------------- | ---- | ---------------------------------------- |
| name      | string                    | Yes   | Name of the application account to create.                             |
| options | [CreateAccountOptions](#createaccountoptions9) | Yes   | Options for creating the application account. You can customize data based on service requirements, but do not add sensitive data (such as passwords and tokens).|
| callback  | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.            |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name or options. |
| 12300004 | Account already exists. |
| 12300007 | The number of accounts reaches the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  let options:appAccount.CreateAccountOptions  = {
    customData: {
      age: '10'
    }
  }
  try {
    appAccountManager.createAccount('LiSi', options, (err: BusinessError) => {
      if (err) {
        console.error('createAccount failed, error: ' + JSON.stringify(err));
      } else {
        console.log('createAccount successfully');
      }
    });
  } catch(err) {
    console.error('createAccount exception: ' + JSON.stringify(err));
  }
  ```

### createAccount<sup>9+</sup>

createAccount(name: string, options?: CreateAccountOptions): Promise&lt;void&gt;

Creates an application account with custom data. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name      | Type    | Mandatory  | Description                                      |
| --------- | ------ | ---- | ---------------------------------------- |
| name      | string | Yes   | Name of the application account to create.                             |
| options | [CreateAccountOptions](#createaccountoptions9) | No   | Options for creating the application account. You can customize data based on service requirements, but do not add sensitive data (such as passwords and tokens). <br>By default, no value is passed in, which means no additional information needs to be added for the account.|

**Return value**

| Type                 | Description                   |
| ------------------- | --------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name or options. |
| 12300004 | Account already exists. |
| 12300007 | The number of accounts reaches the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  let options: appAccount.CreateAccountOptions = {
    customData: {
      age: '10'
    }
  }
  try {
    appAccountManager.createAccount('LiSi', options).then(() => {
      console.log('createAccount successfully');
    }).catch((err: BusinessError) => {
      console.error('createAccount failed, error: ' + JSON.stringify(err));
    });
  } catch(err) {
    console.error('createAccount exception: ' + JSON.stringify(err));
  }
  ```

### createAccountImplicitly<sup>9+</sup>

createAccountImplicitly(owner: string, callback: AuthCallback): void

Creates an application account implicitly based on the specified account owner. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type               | Mandatory  | Description                     |
| -------- | --------------------- | ---- | ----------------------- |
| owner    | string                | Yes   | Owner of the application account. The value is the bundle name of the application.         |
| callback | [AuthCallback](#authcallback9) | Yes   | Authenticator callback used to return the result.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid owner. |
| 12300007 | The number of accounts reaches the upper limit. |
| 12300010 | Account service busy. |
| 12300113 | Authenticator service not found. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { Want, common } from '@kit.AbilityKit';

  @Entry
  @Component
  struct Index {
    context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

    onResultCallback(code: number, result?: appAccount.AuthResult): void {
      console.log('resultCode: ' + code);
      console.log('result: ' + JSON.stringify(result));
    }

    onRequestRedirectedCallback(request: Want): void {
      let wantInfo: Want = {
        deviceId: '',
        bundleName: 'com.example.accountjsdemo',
        action: 'ohos.want.action.viewData',
        entities: ['entity.system.default'],
      }
      this.context.startAbility(wantInfo).then(() => {
        console.log('startAbility successfully');
      }).catch((err: BusinessError) => {
        console.error('startAbility err: ' + JSON.stringify(err));
      })
    }

    aboutToAppear(): void {
      try {
        appAccountManager.createAccountImplicitly('com.example.accountjsdemo', {
          onResult: this.onResultCallback,
          onRequestRedirected: this.onRequestRedirectedCallback
        });
      } catch (err) {
        console.error('createAccountImplicitly exception: ' + JSON.stringify(err));
      }
    }
    build() {}
  }
  ```

### createAccountImplicitly<sup>9+</sup>

createAccountImplicitly(owner: string, options: CreateAccountImplicitlyOptions, callback: AuthCallback): void

Creates an application account implicitly based on the specified account owner and options. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                   | Mandatory  | Description                     |
| -------- | --------------------- | ---- | ----------------------- |
| owner    | string                | Yes   | Owner of the application account. The value is the bundle name of the application.         |
| options    | [CreateAccountImplicitlyOptions](#createaccountimplicitlyoptions9)   | Yes   | Options for implicitly creating the account.         |
| callback | [AuthCallback](#authcallback9) | Yes   | Authenticator callback used to return the result.        |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid owner or options. |
| 12300007 | The number of accounts reaches the upper limit. |
| 12300010 | Account service busy. |
| 12300113 | Authenticator service not found. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { Want, common } from '@kit.AbilityKit';

  @Entry
  @Component
  struct Index {
    context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

    onResultCallback(code: number, result?: appAccount.AuthResult): void {
      console.log('resultCode: ' + code);
      console.log('result: ' + JSON.stringify(result));
    }

    onRequestRedirectedCallback(request: Want): void {
      let wantInfo: Want = {
        deviceId: '',
        bundleName: 'com.example.accountjsdemo',
        action: 'ohos.want.action.viewData',
        entities: ['entity.system.default'],
      }
      this.context.startAbility(wantInfo).then(() => {
        console.log('startAbility successfully');
      }).catch((err: BusinessError) => {
        console.error('startAbility err: ' + JSON.stringify(err));
      })
    }

    aboutToAppear(): void {
      let options: appAccount.CreateAccountImplicitlyOptions = {
        authType: 'getSocialData',
        requiredLabels: [ 'student' ]
      };
      try {
        appAccountManager.createAccountImplicitly('com.example.accountjsdemo', options, {
          onResult: this.onResultCallback,
          onRequestRedirected: this.onRequestRedirectedCallback
        });
      } catch (err) {
        console.error('createAccountImplicitly exception: ' + JSON.stringify(err));
      }
    }
    build() {}
  }
  ```

### removeAccount<sup>9+</sup>

removeAccount(name: string, callback: AsyncCallback&lt;void&gt;): void

Removes an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description              |
| -------- | ------------------------- | ---- | ---------------- |
| name     | string                    | Yes   | Name of the target application account.     |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.removeAccount('ZhaoLiu', (err: BusinessError) => {
      if (err) {
        console.error('removeAccount failed, error: ' + JSON.stringify(err));
      } else {
        console.log('removeAccount successfully');
      }
   });
  } catch(err) {
    console.error('removeAccount exception: ' + JSON.stringify(err));
  }
  ```

### removeAccount<sup>9+</sup>

removeAccount(name: string): Promise&lt;void&gt;

Removes an application account. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name | Type    | Mandatory  | Description         |
| ---- | ------ | ---- | ----------- |
| name | string | Yes   | Name of the target application account.|

**Return value**

| Type                 | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    appAccountManager.removeAccount('Lisi').then(() => {
      console.log('removeAccount successfully');
    }).catch((err: BusinessError) => {
      console.error('removeAccount failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('removeAccount exception: ' + JSON.stringify(err));
  }
  ```

### setAppAccess<sup>9+</sup>

setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets the access to the data of an account for an application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type                     | Mandatory  | Description                               |
| ------------ | ------------------------- | ---- | --------------------------------- |
| name         | string                    | Yes   | Name of the target application account.                          |
| bundleName   | string                    | Yes   | Bundle name of the application.                        |
| isAccessible | boolean                   | Yes   | Whether the access is allowed. The value **true** means to allow the access; the value **false** means the opposite.|
| callback     | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name or bundleName. |
| 12300003 | Account not found. |
| 12400005 | The size of authorization list reaches the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.setAppAccess('ZhangSan', 'com.example.accountjsdemo', true, (err: BusinessError) => {
      if (err) {
        console.error('setAppAccess failed: ' + JSON.stringify(err));
      } else {
        console.log('setAppAccess successfully');
      }
    });
  } catch (err) {
    console.error('setAppAccess exception: ' + JSON.stringify(err));
  }
  ```

### setAppAccess<sup>9+</sup>

setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise&lt;void&gt;

Sets the access to the data of an account for an application. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type    | Mandatory  | Description       |
| ---------- | ------ | ---- | --------- |
| name       | string | Yes   | Name of the target application account.  |
| bundleName | string | Yes   | Bundle name of the application.|
| isAccessible | boolean | Yes   | Whether the access is allowed. The value **true** means to allow the access; the value **false** means the opposite.|

**Return value**

| Type                 | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name or bundleName. |
| 12300003 | Account not found. |
| 12400005 | The size of authorization list reaches the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    appAccountManager.setAppAccess('ZhangSan', 'com.example.accountjsdemo', true).then(() => {
      console.log('setAppAccess successfully');
    }).catch((err: BusinessError) => {
      console.error('setAppAccess failed: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('setAppAccess exception: ' + JSON.stringify(err));
  }
  ```

### checkAppAccess<sup>9+</sup>

checkAppAccess(name: string, bundleName: string, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether an application can access the data of an account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type                       | Mandatory  | Description                               |
| ---------- | ------------------------- | ---- | --------------------------------- |
| name       | string                    | Yes   | Name of the target application account.                          |
| bundleName | string                    | Yes   | Bundle name of the application.                        |
| callback   | AsyncCallback&lt;boolean&gt; | Yes   | Callback used to return the result. The value **true** means the application can access the account data; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name or bundleName. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.checkAppAccess('ZhangSan', 'com.example.accountjsdemo',
      (err: BusinessError, isAccessible: boolean) => {
        if (err) {
          console.error('checkAppAccess failed, error: ' + JSON.stringify(err));
        } else {
          console.log('checkAppAccess successfully');
        }
      });
  } catch (err) {
    console.error('checkAppAccess exception: ' + JSON.stringify(err));
  }
  ```

### checkAppAccess<sup>9+</sup>

checkAppAccess(name: string, bundleName: string): Promise&lt;boolean&gt;

Checks whether an application can access the data of an account. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type    | Mandatory  | Description       |
| ---------- | ------ | ---- | --------- |
| name       | string | Yes   | Name of the target application account.  |
| bundleName | string | Yes   | Bundle name of the application.|

**Return value**

| Type                 | Description                   |
| ------------------- | --------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the application can access the account data; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name or bundleName. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    appAccountManager.checkAppAccess('ZhangSan', 'com.example.accountjsdemo').then((isAccessible: boolean) => {
      console.log('checkAppAccess successfully, isAccessible: ' + isAccessible);
    }).catch((err: BusinessError) => {
      console.error('checkAppAccess failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('checkAppAccess exception: ' + JSON.stringify(err));
  }
  ```

### setDataSyncEnabled<sup>9+</sup>

setDataSyncEnabled(name: string, isEnabled: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets data synchronization for an application account. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.DISTRIBUTED_DATASYNC

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description                       |
| -------- | ------------------------- | ---- | ------------------------- |
| name     | string                    | Yes   | Name of the target application account.                  |
| isEnabled | boolean                   | Yes   | Whether to enable data synchronization. The value **true** means that data synchronization is enabled, and **false** means the opposite.      |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 201 | Permission denied.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
      appAccountManager.setDataSyncEnabled('ZhangSan', true, (err: BusinessError) => { 
          console.error('setDataSyncEnabled err: ' + JSON.stringify(err));
      });
  } catch (err) {
      console.error('setDataSyncEnabled err: ' + JSON.stringify(err));
  }
  ```

### setDataSyncEnabled<sup>9+</sup>

setDataSyncEnabled(name: string, isEnabled: boolean): Promise&lt;void&gt;

Sets data synchronization for an application account. This API uses a promise to return the result.

**Required permissions**: ohos.permission.DISTRIBUTED_DATASYNC

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type     | Mandatory  | Description         |
| -------- | ------- | ---- | ----------- |
| name     | string  | Yes   | Name of the target application account.    |
| isEnabled | boolean | Yes   | Whether to enable data synchronization. The value **true** means that data synchronization is enabled, and **false** means the opposite.|

**Return value**

| Type                 | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 201 | Permission denied.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
      appAccountManager.setDataSyncEnabled('ZhangSan', true).then(() => { 
          console.log('setDataSyncEnabled Success');
      }).catch((err: BusinessError) => {
          console.error('setDataSyncEnabled err: ' + JSON.stringify(err));
      });
  } catch (err) {
      console.error('setDataSyncEnabled err: ' + JSON.stringify(err));
  }
  ```

### checkDataSyncEnabled<sup>9+</sup>

checkDataSyncEnabled(name: string, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether data synchronization is enabled for an application account. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.DISTRIBUTED_DATASYNC

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                          | Mandatory  | Description                   |
| -------- | ---------------------------- | ---- | --------------------- |
| name     | string                       | Yes   | Name of the target application account.              |
| callback | AsyncCallback&lt;boolean&gt; | Yes   | Callback used to return the result. The value **true** means data synchronization is enabled for the application account; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 201 | Permission denied.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.checkDataSyncEnabled('ZhangSan', (err: BusinessError, isEnabled: boolean) => {
      if (err) {
        console.error('checkDataSyncEnabled failed, err: ' + JSON.stringify(err));
      } else {
        console.log('checkDataSyncEnabled successfully, isEnabled: ' + isEnabled);
      }
    });
  } catch (err) {
    console.error('checkDataSyncEnabled err: ' + JSON.stringify(err));
  }
  ```

### checkDataSyncEnabled<sup>9+</sup>

checkDataSyncEnabled(name: string): Promise&lt;boolean&gt;

Checks whether data synchronization is enabled for an application account. This API uses a promise to return the result.

**Required permissions**: ohos.permission.DISTRIBUTED_DATASYNC

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name | Type    | Mandatory  | Description     |
| ---- | ------ | ---- | ------- |
| name | string | Yes   | Name of the target application account.|

**Return value**

| Type                    | Description                   |
| :--------------------- | :-------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means data synchronization is enabled for the application account; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 201 | Permission denied.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    appAccountManager.checkDataSyncEnabled('ZhangSan').then((isEnabled: boolean) => {
        console.log('checkDataSyncEnabled successfully, isEnabled: ' + isEnabled);
    }).catch((err: BusinessError) => {
      console.error('checkDataSyncEnabled failed, err: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('checkDataSyncEnabled err: ' + JSON.stringify(err));
  }
  ```

### setCredential<sup>9+</sup>

setCredential(name: string, credentialType: string, credential: string,callback: AsyncCallback&lt;void&gt;): void

Sets a credential for an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name           | Type                       | Mandatory  | Description           |
| -------------- | ------------------------- | ---- | ------------- |
| name           | string                    | Yes   | Name of the target application account.    |
| credentialType | string                    | Yes   | Type of the credential to set.    |
| credential     | string                    | Yes   | Credential value.      |
| callback       | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the credential is set successfully, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name, credentialType or credential. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.setCredential('ZhangSan', 'PIN_SIX', 'xxxxxx', (err: BusinessError) => {
      if (err) {
        console.error('setCredential failed, error: ' + JSON.stringify(err));
      } else {
        console.log('setCredential successfully');
      }
    });
  } catch (err) {
    console.error('setCredential exception: ' + JSON.stringify(err));
  }
  ```

### setCredential<sup>9+</sup>

setCredential(name: string, credentialType: string, credential: string): Promise&lt;void&gt;

Sets a credential for an application account. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name           | Type    | Mandatory  | Description        |
| -------------- | ------ | ---- | ---------- |
| name           | string | Yes   | Name of the target application account.  |
| credentialType | string | Yes   | Type of the credential to set.|
| credential     | string | Yes   | Credential value.   |

**Return value**

| Type                | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name, credentialType or credential. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    appAccountManager.setCredential('ZhangSan', 'PIN_SIX', 'xxxxxx').then(() => {
      console.log('setCredential successfully');
    }).catch((err: BusinessError) => {
      console.error('setCredential failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('setCredential exception: ' + JSON.stringify(err));
  }
  ```

### getCredential<sup>9+</sup>

getCredential(name: string, credentialType: string, callback: AsyncCallback&lt;string&gt;): void

Obtains the credential of an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name           | Type                         | Mandatory  | Description            |
| -------------- | --------------------------- | ---- | -------------- |
| name           | string                      | Yes   | Name of the target application account.       |
| credentialType | string                      | Yes   | Type of the credential to obtain.|
| callback       | AsyncCallback&lt;string&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the credential obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name or credentialType. |
| 12300003 | Account not found. |
| 12300102 | Credential not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
      appAccountManager.getCredential('ZhangSan', 'PIN_SIX', (err: BusinessError, result: string) => { 
        if (err) {
          console.error('getCredential failed, error: ' + JSON.stringify(err));
        } else {
          console.log('getCredential successfully, result: ' + result);
        }
      });
  } catch (err) {
      console.error('getCredential err: ' + JSON.stringify(err));
  }
  ```

### getCredential<sup>9+</sup>

getCredential(name: string, credentialType: string): Promise&lt;string&gt;

Obtains the credential of an application account. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name         | Type    | Mandatory  | Description        |
| -------------- | ------ | ---- | ---------- |
| name           | string | Yes   | Name of the target application account.|
| credentialType | string | Yes   | Type of the credential to obtain.|

**Return value**

| Type                   | Description                   |
| :-------------------- | :-------------------- |
| Promise&lt;string&gt; | Promise used to return the credential obtained.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name or credentialType. |
| 12300003 | Account not found. |
| 12300102 | Credential not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    appAccountManager.getCredential('ZhangSan', 'PIN_SIX').then((credential: string) => {
        console.log('getCredential successfully, credential: ' + credential);
    }).catch((err: BusinessError) => {
        console.error('getCredential failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('getCredential exception: ' + JSON.stringify(err));
  }
  ```

### setCustomData<sup>9+</sup>

setCustomData(name: string, key: string, value: string, callback: AsyncCallback&lt;void&gt;): void

Sets custom data for an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description               |
| -------- | ------------------------- | ---- | ----------------- |
| name     | string                    | Yes   | Name of the target application account.|
| key      | string                    | Yes   | Key of the custom data to set.|
| value    | string                    | Yes   | Value of the custom data to set.|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name, key or value. |
| 12300003 | Account not found. |
| 12400003 | The number of custom data reaches the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.setCustomData('ZhangSan', 'age', '12', (err: BusinessError) => {
      if (err) {
        console.error('setCustomData failed, error: ' + JSON.stringify(err));
      } else {
        console.log('setCustomData successfully');
      }
    });
  } catch (err) {
    console.error('setCustomData exception: ' + JSON.stringify(err));
  }
  ```

### setCustomData<sup>9+</sup>

setCustomData(name: string, key: string, value: string): Promise&lt;void&gt;

Sets custom data for an application account. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name  | Type| Mandatory | Description             |
| ----- | ------ | ---- | ----------------- |
| name  | string | Yes   | Name of the target application account.  |
| key   | string | Yes   | Key of the custom data to set.|
| value | string | Yes   | Value of the custom data to set.|

**Return value**

| Type                 | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name, key or value. |
| 12300003 | Account not found. |
| 12400003 | The number of custom data reaches the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    appAccountManager.setCustomData('ZhangSan', 'age', '12').then(() => {
      console.log('setCustomData successfully');
    }).catch((err: BusinessError) => {
      console.error('setCustomData failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('setCustomData exception: ' + JSON.stringify(err));
  }
  ```

### getCustomData<sup>9+</sup>

getCustomData(name: string, key: string, callback: AsyncCallback&lt;string&gt;): void

Obtains the custom data of an application account based on the specified key. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name   | Type                       | Mandatory | Description                    |
| -------- | --------------------------- | ----- | ------------------------ |
| name     | string                      | Yes   | Name of the target application account.          |
| key      | string                      | Yes   | Key of the custom data to obtain.        |
| callback | AsyncCallback&lt;string&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the custom data value obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name or key. |
| 12300003 | Account not found. |
| 12400002 | Custom data not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.getCustomData('ZhangSan', 'age', (err: BusinessError, data: string) => {
      if (err) {
        console.error('getCustomData failed, error: ' + err);
      } else {
        console.log('getCustomData successfully, data: ' + data);
      }
    });
  } catch (err) {
    console.error('getCustomData exception: ' + JSON.stringify(err));
  }
  ```

### getCustomData<sup>9+</sup>

getCustomData(name: string, key: string): Promise&lt;string&gt;

Obtains the custom data of an application account based on the specified key. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name | Type    | Mandatory  | Description       |
| ---- | ------ | ---- | --------- |
| name | string | Yes   | Name of the target application account.  |
| key  | string | Yes   | Key of the custom data to obtain.|

**Return value**

| Type                  | Description                   |
| --------------------- | --------------------- |
| Promise&lt;string&gt; | Promise used to return the custom data value obtained.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name or key. |
| 12300003 | Account not found. |
| 12400002 | Custom data not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    appAccountManager.getCustomData('ZhangSan', 'age').then((data: string) => {
      console.log('getCustomData successfully, data: ' + data);
    }).catch((err: BusinessError) => {
      console.error('getCustomData failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('getCustomData exception: ' + JSON.stringify(err));
  }
  ```

### getCustomDataSync<sup>9+</sup>

getCustomDataSync(name: string, key: string): string;

Obtains the custom data of an application account based on the specified key. The API returns the result synchronously.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name | Type    | Mandatory  | Description       |
| ---- | ------ | ---- | --------- |
| name | string | Yes   | Name of the target application account.  |
| key  | string | Yes   | Key of the custom data to obtain.|

**Return value**

| Type                   | Description                   |
| --------------------- | --------------------- |
| string | Value of the custom data obtained.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid name or key. |
| 12300003 | Account not found. |
| 12400002 | Custom data not found. |

**Example**

  ```ts
  try {
      let value = appAccountManager.getCustomDataSync('ZhangSan', 'age');
      console.info('getCustomDataSync successfully, value: ' + value);
  } catch (err) {
    console.error('getCustomDataSync failed, error: ' + JSON.stringify(err));
  }
  ```

### getAllAccounts<sup>9+</sup>

getAllAccounts(callback: AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt;): void

Obtains information about all accessible application accounts. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                      | Mandatory  | Description       |
| -------- | ---------------------------------------- | ---- | --------- |
| callback | AsyncCallback&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of accessible application accounts. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.getAllAccounts((err: BusinessError, data: appAccount.AppAccountInfo[]) => {
      if (err) {
        console.error('getAllAccounts failed, error: ' + JSON.stringify(err));
      } else {
        console.debug('getAllAccounts successfully');
      }
    });
  } catch (err) {
      console.error('getAllAccounts exception: ' + JSON.stringify(err));
  }
  ```

### getAllAccounts<sup>9+</sup>

getAllAccounts(): Promise&lt;Array&lt;AppAccountInfo&gt;&gt;

Obtains information about all accessible application accounts. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | Promise used to return information about all accessible accounts.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md).

| ID| Error Message|
| ------- | -------|
| 12300001 | System service exception. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    appAccountManager.getAllAccounts().then((data: appAccount.AppAccountInfo[]) => {
      console.debug('getAllAccounts successfully');
    }).catch((err: BusinessError) => {
      console.error('getAllAccounts failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('getAllAccounts exception: ' + JSON.stringify(err));
  }
  ```

### getAccountsByOwner<sup>9+</sup>

getAccountsByOwner(owner: string, callback: AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt;): void

Obtains the application accounts that can be accessed by the invoker based on the application account owner. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                      | Mandatory  | Description       |
| -------- | ---------------------------------------- | ---- | --------- |
| owner    | string                                   | Yes   | Owner of the application account. The value is the bundle name of the application.   |
| callback | AsyncCallback&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is null and **data** is the application account information obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid owner. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.getAccountsByOwner('com.example.accountjsdemo2',
      (err: BusinessError, data: appAccount.AppAccountInfo[]) => {
        if (err) {
          console.error('getAccountsByOwner failed, error:' + JSON.stringify(err));
        } else {
          console.debug('getAccountsByOwner successfully, data:' + JSON.stringify(data));
        }
      });
  } catch (err) {
    console.error('getAccountsByOwner exception:' + JSON.stringify(err));
  }
  ```

### getAccountsByOwner<sup>9+</sup>

getAccountsByOwner(owner: string): Promise&lt;Array&lt;AppAccountInfo&gt;&gt;

Obtains the application accounts that can be accessed by the invoker based on the application account owner. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name  | Type    | Mandatory  | Description    |
| ----- | ------ | ---- | ------ |
| owner | string | Yes   | Owner of the application account. The value is the bundle name of the application.|

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | Promise used to return the application account information obtained.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid owner. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    appAccountManager.getAccountsByOwner('com.example.accountjsdemo2').then((
      data: appAccount.AppAccountInfo[]) => {
      console.debug('getAccountsByOwner successfully, data: ' + JSON.stringify(data));
    }).catch((err: BusinessError) => {
      console.error('getAccountsByOwner failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('getAccountsByOwner exception: ' + JSON.stringify(err));
  }
  ```

### on('accountChange')<sup>9+</sup>

on(type: 'accountChange', owners: Array&lt;string&gt;, callback: Callback&lt;Array&lt;AppAccountInfo&gt;&gt;): void

Subscribes to account information changes of apps.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                      | Mandatory  | Description                            |
| -------- | ---------------------------------------- | ---- | ------------------------------ |
| type     | 'accountChange'                          | Yes   | Event type to subscribe to. The value is **'accountChange'**. An event will be reported when the account information of the target application changes.|
| owners   | Array&lt;string&gt;                      | Yes   | Application bundle names of the account.                     |
| callback | Callback&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | Yes   | Callback registered to return the list of changed application accounts.          |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid type or owners. |

**Example**

  ```ts
  function changeOnCallback(data: appAccount.AppAccountInfo[]): void {
  	console.log('receive change data:' + JSON.stringify(data));
  }
  try{
  	appAccountManager.on('accountChange', ['com.example.actsaccounttest'], changeOnCallback);
  } catch(err) {
  	console.error('on accountChange failed, error:' + JSON.stringify(err));
  }
  ```

### off('accountChange')<sup>9+</sup>

off(type: 'accountChange', callback?: Callback&lt;Array&lt;AppAccountInfo&gt;&gt;): void

Unsubscribes from account information changes.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                              | Mandatory  | Description          |
| -------- | -------------------------------- | ---- | ------------ |
| type     | 'accountChange'                         | Yes   | Event type to unsubscribe from. The value is **'accountChange'**.   |
| callback | Callback&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | No   | Callback to unregister. By default, no value is passed, which means to unregister all callbacks for the specified event.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | System service exception. |
| 12300002 | Invalid type. |

**Example**

  ```ts
  function changeOnCallback(data: appAccount.AppAccountInfo[]): void {
  	console.log('receive change data:' + JSON.stringify(data));
  }
  try{
  	appAccountManager.on('accountChange', ['com.example.actsaccounttest'], changeOnCallback);
  } catch(err) {
  	console.error('on accountChange failed, error:' + JSON.stringify(err));
  }
  try{
  	appAccountManager.off('accountChange', changeOnCallback);
  }
  catch(err){
  	console.error('off accountChange failed, error:' + JSON.stringify(err));
  }
  ```

### auth<sup>9+</sup>

auth(name: string, owner: string, authType: string, callback: AuthCallback): void

Authenticates an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                   | Mandatory  | Description             |
| -------- | --------------------- | ---- | --------------- |
| name     | string                | Yes   | Name of the target application account.    |
| owner    | string                | Yes   | Owner of the application account. The value is the bundle name of the application. |
| authType | string                | Yes   | Authentication type.          |
| callback | [AuthCallback](#authcallback9) | Yes   | Authenticator callback used to return the result.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, owner or authType. |
| 12300003 | Account not found. |
| 12300010 | Account service busy. |
| 12300113 | Authenticator service not found. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { Want, common } from '@kit.AbilityKit';

  @Entry
  @Component
  struct Index {
    context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

    onResultCallback(code: number, authResult?: appAccount.AuthResult): void {
      console.log('resultCode: ' + code);
      console.log('authResult: ' + JSON.stringify(authResult));
    }

    onRequestRedirectedCallback(request: Want): void {
      let wantInfo: Want = {
        deviceId: '',
        bundleName: 'com.example.accountjsdemo',
        action: 'ohos.want.action.viewData',
        entities: ['entity.system.default'],
      }
      this.context.startAbility(wantInfo).then(() => {
        console.log('startAbility successfully');
      }).catch((err: BusinessError) => {
        console.error('startAbility err: ' + JSON.stringify(err));
      })
    }

    aboutToAppear(): void {
      try {
        appAccountManager.auth('LiSi', 'com.example.accountjsdemo', 'getSocialData', {
          onResult: this.onResultCallback,
          onRequestRedirected: this.onRequestRedirectedCallback
        });
      } catch (err) {
        console.error('auth exception: ' + JSON.stringify(err));
      }
    }
    build() {}
  }
  ```

### auth<sup>9+</sup>

auth(name: string, owner: string, authType: string, options: Record<string, Object>, callback: AuthCallback): void

Authenticates an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                   | Mandatory  | Description             |
| -------- | --------------------- | ---- | --------------- |
| name     | string                | Yes   | Name of the target application account.    |
| owner    | string                | Yes   | Owner of the application account. The value is the bundle name of the application. |
| authType | string                | Yes   | Authentication type.          |
| options  | Record<string, Object>  | Yes   | Options for the authentication.      |
| callback | [AuthCallback](#authcallback9) | Yes   | Authenticator callback used to return the result.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, owner, authType or options. |
| 12300003 | Account not found. |
| 12300010 | Account service busy. |
| 12300113 | Authenticator service not found. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { Want, common } from '@kit.AbilityKit';

  @Entry
  @Component
  struct Index {
    context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

    onResultCallback(code: number, authResult?: appAccount.AuthResult): void {
      console.log('resultCode: ' + code);
      console.log('authResult: ' + JSON.stringify(authResult));
    }

    onRequestRedirectedCallback(request: Want): void {
      let wantInfo: Want = {
        deviceId: '',
        bundleName: 'com.example.accountjsdemo',
        action: 'ohos.want.action.viewData',
        entities: ['entity.system.default'],
      }
      this.context.startAbility(wantInfo).then(() => {
        console.log('startAbility successfully');
      }).catch((err: BusinessError) => {
        console.error('startAbility err: ' + JSON.stringify(err));
      })
    }

    aboutToAppear(): void {
      let options: Record<string, Object> = {
        'password': 'xxxx',
      };
      try {
        appAccountManager.auth('LiSi', 'com.example.accountjsdemo', 'getSocialData', options, {
          onResult: this.onResultCallback,
          onRequestRedirected: this.onRequestRedirectedCallback
        });
      } catch (err) {
        console.error('auth exception: ' + JSON.stringify(err));
      }
    }
    build() {}
  }
  ```

### getAuthToken<sup>9+</sup>

getAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback&lt;string&gt;): void

Obtains the authorization token of the specified authentication type for an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                         | Mandatory  | Description         |
| -------- | --------------------------- | ---- | ----------- |
| name     | string                      | Yes   | Name of the target application account.   |
| owner    | string                      | Yes   | Owner of the application account. The value is the bundle name of the application.|
| authType | string                      | Yes   | Authentication type.      |
| callback | AsyncCallback&lt;string&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authorization token value obtained. Otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, owner or authType. |
| 12300003 | Account not found. |
| 12300107 | AuthType not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.getAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData',
      (err: BusinessError, token: string) => {
        if (err) {
          console.error('getAuthToken failed, error: ' + JSON.stringify(err));
        } else {
          console.log('getAuthToken successfully, token: ' + token);
        }
      });
  } catch (err) {
      console.error('getAuthToken exception: ' + JSON.stringify(err));
  }
  ```

### getAuthToken<sup>9+</sup>

getAuthToken(name: string, owner: string, authType: string): Promise&lt;string&gt;

Obtains the authorization token of the specified authentication type for an application account. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type    | Mandatory  | Description         |
| -------- | ------ | ---- | ----------- |
| name     | string | Yes   | Name of the target application account.   |
| owner    | string | Yes   | Owner of the application account. The value is the bundle name of the application.|
| authType | string | Yes   | Authentication type.      |

**Return value**

| Type                   | Description                |
| --------------------- | --------------------- |
| Promise&lt;string&gt; | Promise used to return the authorization token obtained.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, owner or authType. |
| 12300003 | Account not found. |
| 12300107 | AuthType not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.getAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData').then((token: string) => {
      console.log('getAuthToken successfully, token: ' + token);
    }).catch((err: BusinessError) => {
      console.error('getAuthToken failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
      console.error('getAuthToken exception: ' + JSON.stringify(err));
  }
  ```

### setAuthToken<sup>9+</sup>

setAuthToken(name: string, authType: string, token: string, callback: AsyncCallback&lt;void&gt;): void

Sets an authorization token of the specific authentication type for an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description      |
| -------- | ------------------------- | ---- | -------- |
| name     | string                    | Yes   | Name of the target application account.|
| authType | string                    | Yes   | Authentication type.   |
| token    | string                    | Yes   | Authorization token to set.|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, authType or token. |
| 12300003 | Account not found. |
| 12400004 | The number of tokens reaches the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.setAuthToken('LiSi', 'getSocialData', 'xxxx', (err: BusinessError) => {
      if (err) {
        console.error('setAuthToken failed, error: ' + JSON.stringify(err));
      } else {
        console.log('setAuthToken successfully');
      }
    });
  } catch (err) {
    console.error('setAuthToken exception: ' + JSON.stringify(err));
  }
  ```

### setAuthToken<sup>9+</sup>

setAuthToken(name: string, authType: string, token: string): Promise&lt;void&gt;

Sets an authorization token of the specific authentication type for an application account. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type    | Mandatory  | Description      |
| -------- | ------ | ---- | -------- |
| name     | string | Yes   | Name of the target application account.|
| authType | string | Yes   | Authentication type.   |
| token    | string | Yes   | Authorization token to set.|

**Return value**

| Type                 | Description                   |
| ------------------- | --------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, authType or token. |
| 12300003 | Account not found. |
| 12400004 | The number of tokens reaches the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.setAuthToken('LiSi', 'getSocialData', 'xxxx').then(() => {
        console.log('setAuthToken successfully');
    }).catch((err: BusinessError) => {
        console.error('setAuthToken failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('setAuthToken exception: ' + JSON.stringify(err));
  }
  ```

### deleteAuthToken<sup>9+</sup>

deleteAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback&lt;void&gt;): void

Deletes the authorization token of the specified authentication type for an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description          |
| -------- | ------------------------- | ---- | ------------ |
| name     | string                    | Yes   | Name of the target application account.    |
| owner    | string                    | Yes   | Owner of the application account. The value is the bundle name of the application. |
| authType | string                    | Yes   | Authentication type.       |
| token    | string                    | Yes   | Authorization token to delete. If the token does not exist, no operation is performed.|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, owner, authType or token. |
| 12300003 | Account not found. |
| 12300107 | AuthType not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.deleteAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx',
      (err: BusinessError) => {
        if (err) {
          console.error('deleteAuthToken failed, error: ' + JSON.stringify(err));
        } else {
          console.log('deleteAuthToken successfully');
        }
      });
  } catch (err) {
    console.error('deleteAuthToken exception: ' + JSON.stringify(err));
  }
  ```

### deleteAuthToken<sup>9+</sup>

deleteAuthToken(name: string, owner: string, authType: string, token: string): Promise&lt;void&gt;

Deletes the authorization token of the specified authentication type for an application account. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type    | Mandatory  | Description          |
| -------- | ------ | ---- | ------------ |
| name     | string | Yes   | Name of the target application account.    |
| owner    | string | Yes   | Owner of the application account. The value is the bundle name of the application. |
| authType | string | Yes   | Authentication type.       |
| token    | string | Yes   | Authorization token to delete. If the token does not exist, no operation is performed.|

**Return value**

| Type                 | Description                   |
| ------------------- | --------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, owner, authType or token. |
| 12300003 | Account not found. |
| 12300107 | AuthType not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.deleteAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx').then(() => {
      console.log('deleteAuthToken successfully');
    }).catch((err: BusinessError) => {
      console.error('deleteAuthToken failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('deleteAuthToken exception: ' + JSON.stringify(err));
  }
  ```

### setAuthTokenVisibility<sup>9+</sup>

setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets the visibility of an authorization token to an application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type                       | Mandatory  | Description                       |
| ---------- | ------------------------- | ---- | ------------------------- |
| name       | string                    | Yes   | Name of the target application account.                 |
| authType   | string                    | Yes   | Authentication type.                    |
| bundleName | string                    | Yes   | Bundle name of the application.             |
| isVisible  | boolean                   | Yes   | Whether the authorization token is visible to the application. The value **true** means the authorization token is visible to the application; the value **false** means the opposite.|
| callback   | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, authType or bundleName. |
| 12300003 | Account not found. |
| 12300107 | AuthType not found. |
| 12400005 | The size of authorization list reaches the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.setAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true,
      (err: BusinessError) => {
        if (err) {
          console.error('setAuthTokenVisibility failed, error: ' + JSON.stringify(err));
        } else {
          console.log('setAuthTokenVisibility successfully');
        }
      });
  } catch (err) {
      console.error('setAuthTokenVisibility exception: ' + JSON.stringify(err));
  }
  ```

### setAuthTokenVisibility<sup>9+</sup>

setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise&lt;void&gt;

Sets the visibility of an authorization token to an application. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description                       |
| ---------- | ------------------------- | ---- | ------------------------- |
| name       | string                    | Yes   | Name of the target application account.                 |
| authType   | string                    | Yes   | Authentication type.                    |
| bundleName | string                    | Yes   | Bundle name of the application.             |
| isVisible  | boolean                   | Yes   | Whether the authorization token is visible to the application. The value **true** means the authorization token is visible to the application; the value **false** means the opposite.|

**Return value**

| Type                 | Description                   |
| ------------------- | --------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, authType or bundleName. |
| 12300003 | Account not found. |
| 12300107 | AuthType not found. |
| 12400005 | The size of authorization list reaches the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.setAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true).then(() => {
      console.log('setAuthTokenVisibility successfully');
    }).catch((err: BusinessError) => {
      console.error('setAuthTokenVisibility failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('setAuthTokenVisibility exception: ' + JSON.stringify(err));
  }
  ```

### checkAuthTokenVisibility<sup>9+</sup>

checkAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback&lt;boolean&gt;): void

Checks the visibility of an authorization token of the specified authentication type to an application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type                          | Mandatory  | Description         |
| ---------- | ---------------------------- | ---- | ----------- |
| name       | string                       | Yes   | Name of the target application account.   |
| authType   | string                       | Yes   | Authentication type.      |
| bundleName | string                       | Yes   | Bundle name of the application.|
| callback   | AsyncCallback&lt;boolean&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** can be **true** (the authorization token is visible to the application) or **false** (the authorization token is not visible to the application). If the operation fails, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, authType or bundleName. |
| 12300003 | Account not found. |
| 12300107 | AuthType not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.checkAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo',
      (err: BusinessError, isVisible: boolean) => {
        if (err) {
          console.error('checkAuthTokenVisibility failed, error: ' + JSON.stringify(err));
        } else {
          console.log('checkAuthTokenVisibility successfully, isVisible: ' + isVisible);
        }
      });
  } catch (err) {
    console.error('checkAuthTokenVisibility exception: ' + JSON.stringify(err));
  }
  ```

### checkAuthTokenVisibility<sup>9+</sup>

checkAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise&lt;boolean&gt;

Checks the visibility of an authorization token of the specified authentication type to an application. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type    | Mandatory  | Description           |
| ---------- | ------ | ---- | ------------- |
| name       | string | Yes   | Name of the target application account.     |
| authType   | string | Yes   | Authentication type.        |
| bundleName | string | Yes   | Bundle name of the application.|

**Return value**

| Type                    | Description                   |
| ---------------------- | --------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the authorization token is visible to the application; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, authType or bundleName. |
| 12300003 | Account not found. |
| 12300107 | AuthType not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.checkAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo').then((
      isVisible: boolean) => {
      console.log('checkAuthTokenVisibility successfully, isVisible: ' + isVisible);
    }).catch((err: BusinessError) => {
      console.error('checkAuthTokenVisibility failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('checkAuthTokenVisibility exception: ' + JSON.stringify(err));
  }
  ```

### getAllAuthTokens<sup>9+</sup>

getAllAuthTokens(name: string, owner: string, callback: AsyncCallback&lt;Array&lt;AuthTokenInfo&gt;&gt;): void

Obtains all tokens visible to the invoker for an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                      | Mandatory  | Description         |
| -------- | ---------------------------------------- | ---- | ----------- |
| name     | string                                   | Yes   | Name of the target application account.   |
| owner    | string                                   | Yes   | Owner of the application account. The value is the bundle name of the application.|
| callback | AsyncCallback&lt;Array&lt;[AuthTokenInfo](#authtokeninfo9)&gt;&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of all tokens visible to the invoker. Otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name or owner. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.getAllAuthTokens('LiSi', 'com.example.accountjsdemo',
      (err: BusinessError, tokenArr: appAccount.AuthTokenInfo[]) => {
        if (err) {
          console.error('getAllAuthTokens failed, error: ' + JSON.stringify(err));
        } else {
          console.log('getAllAuthTokens successfully, tokenArr: ' + tokenArr);
        }
      });
  } catch (err) {
    console.error('getAllAuthTokens exception: ' + JSON.stringify(err));
  }
  ```

### getAllAuthTokens<sup>9+</sup>

getAllAuthTokens(name: string, owner: string): Promise&lt;Array&lt;AuthTokenInfo&gt;&gt;

Obtains all tokens visible to the invoker for an application account. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name  | Type    | Mandatory  | Description         |
| ----- | ------ | ---- | ----------- |
| name  | string | Yes   | Name of the target application account.   |
| owner | string | Yes   | Owner of the application account. The value is the bundle name of the application.|

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise&lt;Array&lt;[AuthTokenInfo](#authtokeninfo9)&gt;&gt; | Promise used to return the tokens obtained.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name or owner. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.getAllAuthTokens('LiSi', 'com.example.accountjsdemo').then((
      tokenArr: appAccount.AuthTokenInfo[]) => {
      console.log('getAllAuthTokens successfully, tokenArr: ' + JSON.stringify(tokenArr));
    }).catch((err: BusinessError) => {
      console.error('getAllAuthTokens failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('getAllAuthTokens exception: ' + JSON.stringify(err));
  }
  ```

### getAuthList<sup>9+</sup>

getAuthList(name: string, authType: string, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Obtains the authorization list of the specified authentication type for an application account. The authorization list contains all authorized bundles. The token authorization list is set by [setAuthTokenVisibility](#setauthtokenvisibility9). This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                      | Mandatory  | Description                     |
| -------- | ---------------------------------------- | ---- | ----------------------- |
| name     | string                                   | Yes   | Name of the target application account.               |
| authType | string                                   | Yes   | Authentication type.|
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of authorized bundles obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name or authType. |
| 12300003 | Account not found. |
| 12300107 | AuthType not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.getAuthList('LiSi', 'getSocialData', (err: BusinessError, authList: string[]) => {
      if (err) {
        console.error('getAuthList failed, error: ' + JSON.stringify(err));
      } else {
        console.log('getAuthList successfully, authList: ' + authList);
      }
    });
  } catch (err) {
    console.error('getAuthList exception: ' + JSON.stringify(err));
  }
  ```

### getAuthList<sup>9+</sup>

getAuthList(name: string, authType: string): Promise&lt;Array&lt;string&gt;&gt;

Obtains the authorization list of the specified authentication type for an application account. The authorization list contains all authorized bundles. The token authorization list is set by [setAuthTokenVisibility](#setauthtokenvisibility9). This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type    | Mandatory  | Description                     |
| -------- | ------ | ---- | ------------------------------ |
| name     | string | Yes   | Name of the target application account.               |
| authType | string | Yes   | Authentication type.|

**Return value**

| Type                                | Description                   |
| ---------------------------------- | --------------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return a list of authorized bundles.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name or authType. |
| 12300003 | Account not found. |
| 12300107 | AuthType not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.getAuthList('LiSi', 'getSocialData').then((authList: string[]) => {
        console.log('getAuthList successfully, authList: ' + authList);
    }).catch((err: BusinessError) => {
        console.error('getAuthList failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('getAuthList exception: ' + JSON.stringify(err));
  }
  ```

### getAuthCallback<sup>9+</sup>

getAuthCallback(sessionId: string, callback: AsyncCallback&lt;AuthCallback&gt;): void

Obtains the authenticator callback for an authentication session. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| sessionId | string                                   | Yes   | ID of the authentication session.|
| callback  | AsyncCallback&lt;[AuthCallback](#authcallback9)&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authenticator callback object obtained. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid sessionId. |
| 12300108 | Session not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';

  export default class EntryAbility extends UIAbility {
    onCreate(want: Want, param: AbilityConstant.LaunchParam) { // Ability lifecycle function.
      let sessionId: string = want.parameters![appAccount.Constants.KEY_SESSION_ID] as string;
      try {
        appAccountManager.getAuthCallback(sessionId, (err: BusinessError, callback: appAccount.AuthCallback) => {
          if (err != null) {
              console.error('getAuthCallback err: ' + JSON.stringify(err));
              return;
          }
          let result: appAccount.AuthResult = {
            account: {
              name: 'Lisi',
              owner: 'com.example.accountjsdemo',
            },
            tokenInfo: {
              token: 'xxxxxx',
              authType: 'getSocialData'
            }
          }; 
          callback.onResult(0, result);
        });
      } catch (err) {
          console.error('getAuthCallback exception: ' + JSON.stringify(err));
      }
    }
  }
  ```

### getAuthCallback<sup>9+</sup>

getAuthCallback(sessionId: string): Promise&lt;AuthCallback&gt;

Obtains the authenticator callback for an authentication session. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name      | Type    | Mandatory  | Description      |
| --------- | ------ | ---- | -------- |
| sessionId | string | Yes   | ID of the authentication session.|

**Return value**

| Type                                  | Description                   |
| ------------------------------------ | --------------------- |
| Promise&lt;[AuthCallback](#authcallback9)&gt; | Promise used to return the authenticator callback obtained.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid sessionId. |
| 12300108 | Session not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';

  export default class EntryAbility extends UIAbility {
    onCreate(want: Want, param: AbilityConstant.LaunchParam) { // Ability lifecycle function.
      let sessionId: string = want.parameters![appAccount.Constants.KEY_SESSION_ID] as string;
      try {
        appAccountManager.getAuthCallback(sessionId).then((callback: appAccount.AuthCallback) => {
        let result: appAccount.AuthResult = {
          account: {
            name: 'Lisi',
            owner: 'com.example.accountjsdemo',
          },
          tokenInfo: {
            token: 'xxxxxx',
            authType: 'getSocialData'
          }
        };
        callback.onResult(0, result);
        }).catch((err: BusinessError) => {
          console.error('getAuthCallback err: ' + JSON.stringify(err));
        });
      } catch (err) {
        console.error('getAuthCallback exception: ' + JSON.stringify(err));
      }
    }
  }
  ```

### queryAuthenticatorInfo<sup>9+</sup>

queryAuthenticatorInfo(owner: string, callback: AsyncCallback&lt;AuthenticatorInfo&gt;): void

Obtains the authenticator information of an application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                    | Mandatory  | Description         |
| -------- | -------------------------------------- | ---- | ----------- |
| owner    | string                                 | Yes   | Owner of the application account. The value is the bundle name of the application.|
| callback | AsyncCallback&lt;[AuthenticatorInfo](#authenticatorinfo8)&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authenticator information obtained. Otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid owner. |
| 12300113 | Authenticator service not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.queryAuthenticatorInfo('com.example.accountjsdemo',
      (err: BusinessError, info: appAccount.AuthenticatorInfo) => {
        if (err) {
          console.error('queryAuthenticatorInfo failed, error: ' + JSON.stringify(err));
        } else {
          console.log('queryAuthenticatorInfo successfully, info: ' + JSON.stringify(info));
        }
      });
  } catch (err) {
    console.error('queryAuthenticatorInfo exception: ' + JSON.stringify(err));
  }
  ```

### queryAuthenticatorInfo<sup>9+</sup>

queryAuthenticatorInfo(owner: string): Promise&lt;AuthenticatorInfo&gt;

Obtains the authenticator information of an application. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name  | Type    | Mandatory  | Description         |
| ----- | ------ | ---- | ----------- |
| owner | string | Yes   | Owner of the application account. The value is the bundle name of the application.|

**Return value**

| Type                              | Description                   |
| -------------------------------- | --------------------- |
| Promise&lt;[AuthenticatorInfo](#authenticatorinfo8)&gt; | Promise used to return the authenticator information obtained.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid owner. |
| 12300113 | Authenticator service not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.queryAuthenticatorInfo('com.example.accountjsdemo').then((
      info: appAccount.AuthenticatorInfo) => { 
      console.log('queryAuthenticatorInfo successfully, info: ' + JSON.stringify(info));
    }).catch((err: BusinessError) => {
      console.error('queryAuthenticatorInfo failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('queryAuthenticatorInfo exception: ' + JSON.stringify(err));
  }
  ```

### checkAccountLabels<sup>9+</sup>

checkAccountLabels(name: string, owner: string, labels: Array&lt;string&gt;, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether an application account has specific labels. This API uses an asynchronous callback to return the result. The labels are checked by the authenticator of the target application.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name        | Type                      | Mandatory | Description            |
| -------------- | ------------------------- | ----- | --------------- |
| name           | string                    | Yes   | Name of the target application account. |
| owner          | string                    | Yes   | Owner of the application account. The value is the bundle name of the application.|
| labels         | Array&lt;string&gt;       | Yes   | Labels to check.      |
| callback       | AsyncCallback&lt;boolean&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** can be **true** or **false**. The value **true** means the application account has the labels; the value **false** means the opposite. If the operation fails, **err** is an error object. |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, owner or labels. |
| 12300003 | Account not found. |
| 12300010 | Account service busy. |
| 12300113 | Authenticator service not found. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  let labels = ['student'];
  try {
    appAccountManager.checkAccountLabels('zhangsan', 'com.example.accountjsdemo', labels,
      (err: BusinessError, hasAllLabels: boolean) => {
        if (err) {
          console.error('checkAccountLabels failed, error: ' + JSON.stringify(err));
        } else {
          console.log('checkAccountLabels successfully, hasAllLabels: ' + hasAllLabels);
        }
      });
  } catch (err) {
    console.error('checkAccountLabels exception: ' + JSON.stringify(err));
  }
  ```

### checkAccountLabels<sup>9+</sup>

checkAccountLabels(name: string, owner: string, labels: Array&lt;string&gt;): Promise&lt;boolean&gt;

Checks whether an application account has specific labels. This API uses a promise to return the result. The labels are checked by the authenticator of the target application.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name        | Type                      | Mandatory | Description            |
| -------------- | ------------------------- | ----- | --------------- |
| name           | string                    | Yes   | Name of the target application account. |
| owner          | string                    | Yes   | Owner of the application account. The value is the bundle name of the application.|
| labels         | Array&lt;string&gt;       | Yes   | Labels to check.      |

**Return value**

| Type               | Description                             |
| ------------------- | -------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the application account has the labels; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, owner or labels. |
| 12300003 | Account not found. |
| 12300010 | Account service busy. |
| 12300113 | Authenticator service not found. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  let labels = ['student'];
  try {
    appAccountManager.checkAccountLabels('zhangsan', 'com.example.accountjsdemo', labels).then((
      hasAllLabels: boolean) => {
      console.log('checkAccountLabels successfully: ' + hasAllLabels);
    }).catch((err: BusinessError) => {
      console.error('checkAccountLabels failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('checkAccountLabels exception: ' + JSON.stringify(err));
  }
  ```

### deleteCredential<sup>9+</sup>

deleteCredential(name: string, credentialType: string, callback: AsyncCallback&lt;void&gt;): void

Deletes the credential of the specified type from an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name        | Type                      | Mandatory | Description           |
| -------------- | ------------------------- | ----- | -------------- |
| name           | string                    | Yes   | Name of the target application account.|
| credentialType | string                    | Yes   | Type of the credential to delete.     |
| callback       | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name or credentialType. |
| 12300003 | Account not found. |
| 12300102 | Credential not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.deleteCredential('zhangsan', 'PIN_SIX', (err: BusinessError) => {
      if (err) {
        console.error('deleteCredential failed, error: ' + JSON.stringify(err));
      } else {
        console.log('deleteCredential successfully');
      }
    });
  } catch (err) {
    console.error('deleteCredential exception: ' + JSON.stringify(err));
  }
  ```

### deleteCredential<sup>9+</sup>

deleteCredential(name: string, credentialType: string): Promise&lt;void&gt;

Deletes the credential of the specified type from an application account. This API uses a promise to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name        | Type  | Mandatory  | Description           |
| -------------- | ------ | ----- | --------------- |
| name           | string | Yes   | Name of the target application account.|
| credentialType | string | Yes   | Type of the credential to delete.      |

**Return value**

| Type               | Description                             |
| ------------------- | -------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name or credentialType. |
| 12300003 | Account not found. |
| 12300102 | Credential not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  try {
    appAccountManager.deleteCredential('zhangsan', 'PIN_SIX').then(() => {
      console.log('deleteCredential successfully');
    }).catch((err: BusinessError) => {
      console.error('deleteCredential failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('deleteCredential exception: ' + JSON.stringify(err));
  }
  ```

### selectAccountsByOptions<sup>9+</sup>

selectAccountsByOptions(options: SelectAccountsOptions, callback: AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt;): void

Selects the accounts that can be accessed by the invoker based on the options. This API uses an asynchronous callback to return the result. If the options contain label constraints, the authenticator of the target application provides the capability of checking the labels.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name        | Type                                | Mandatory | Description            |
| -------------- | ----------------------------------- | ----- | --------------- |
| options        | [SelectAccountsOptions](#selectaccountsoptions9)               | Yes   | Options for selecting accounts. |
| callback       | AsyncCallback&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of accounts selected. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid options. |
| 12300010 | Account service busy. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  let options: appAccount.SelectAccountsOptions = {
    allowedOwners: [ 'com.example.accountjsdemo' ],
    requiredLabels: [ 'student' ]
  };
  try {
    appAccountManager.selectAccountsByOptions(options,
      (err: BusinessError, accountArr: appAccount.AppAccountInfo[]) => {
        if (err) {
          console.error('selectAccountsByOptions failed, error: ' + JSON.stringify(err));
        } else {
          console.log('selectAccountsByOptions successfully, accountArr: ' + JSON.stringify(accountArr));
        }
      });
  } catch (err) {
    console.error('selectAccountsByOptions exception: ' + JSON.stringify(err));
  }
  ```

### selectAccountsByOptions<sup>9+</sup>

selectAccountsByOptions(options: SelectAccountsOptions): Promise&lt;Array&lt;AppAccountInfo&gt;&gt;

Selects the accounts that can be accessed by the invoker based on the options. This API uses a promise to return the result. If the options contain label constraints, the authenticator of the target application provides the capability of checking the labels.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name        | Type                      | Mandatory | Description            |
| -------------- | ------------------------- | ----- | --------------- |
| options        | [SelectAccountsOptions](#selectaccountsoptions9)     | Yes   | Options for selecting accounts. |

**Return value**

| Type               | Description                             |
| ------------------- | -------------------------------- |
| Promise&lt;[AppAccountInfo](#appaccountinfo)&gt; | Promise used to return the accounts selected.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid options. |
| 12300010 | Account service busy. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  let options: appAccount.SelectAccountsOptions = {
    allowedOwners: ['com.example.accountjsdemo']
  };
  try {
    appAccountManager.selectAccountsByOptions(options).then((accountArr: appAccount.AppAccountInfo[]) => {
      console.log('selectAccountsByOptions successfully, accountArr: ' + JSON.stringify(accountArr));
    }).catch((err: BusinessError) => {
      console.error('selectAccountsByOptions failed, error: ' + JSON.stringify(err));
    });
  } catch (err) {
    console.error('selectAccountsByOptions exception: ' + JSON.stringify(err));
  }
  ```

### verifyCredential<sup>9+</sup>

verifyCredential(name: string, owner: string, callback: AuthCallback): void

Verifies the credential of an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name   | Type                 | Mandatory | Description                    |
| -------- | --------------------- | ----- | ----------------------- |
| name     | string                | Yes   | Name of the target application account.         |
| owner    | string                | Yes   | Owner of the application account. The value is the bundle name of the application.       |
| callback | [AuthCallback](#authcallback9) | Yes   | Callback used to return the result.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name or owner. |
| 12300003 | Account not found. |
| 12300010 | Account service busy. |
| 12300113 | Authenticator service not found. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { Want } from '@kit.AbilityKit';

  try {
      appAccountManager.verifyCredential('zhangsan', 'com.example.accountjsdemo', {
          onResult: (resultCode: number, result?: appAccount.AuthResult) => {
              console.log('verifyCredential onResult, resultCode: ' + JSON.stringify(resultCode));
              console.log('verifyCredential onResult, result: ' + JSON.stringify(result));
          },
          onRequestRedirected: (request: Want) => {
              console.log('verifyCredential onRequestRedirected, request: ' + JSON.stringify(request));
          }
      });
  } catch (err) {
      console.error('verifyCredential err: ' + JSON.stringify(err));
  }
  ```

### verifyCredential<sup>9+</sup>

verifyCredential(name: string, owner: string, options: VerifyCredentialOptions, callback: AuthCallback): void

Verifies the user credential. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name   | Type                   | Mandatory | Description                    |
| -------- | ----------------------- | ----- | ----------------------- |
| name     | string                  | Yes   | Name of the target application account.         |
| owner    | string                  | Yes   | Owner of the application account. The value is the bundle name of the application.       |
| options  | [VerifyCredentialOptions](#verifycredentialoptions9) | Yes   | Options for verifying the user credential.         |
| callback | [AuthCallback](#authcallback9)   | Yes   | Callback used to return the result.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid name, owner or options. |
| 12300003 | Account not found. |
| 12300010 | Account service busy. |
| 12300113 | Authenticator service not found. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { Want } from '@kit.AbilityKit';

  let options: appAccount.VerifyCredentialOptions = {
    credentialType: 'pin',
    credential: '123456'
  };
  try {
    appAccountManager.verifyCredential('zhangsan', 'com.example.accountjsdemo', options, {
      onResult: (resultCode: number, result?: appAccount.AuthResult) => {
        console.log('verifyCredential onResult, resultCode: ' + JSON.stringify(resultCode));
        console.log('verifyCredential onResult, result: ' + JSON.stringify(result));
      },
      onRequestRedirected: (request: Want) => {
        console.log('verifyCredential onRequestRedirected, request: ' + JSON.stringify(request));
      }
    });
  } catch (err) {
    console.error('verifyCredential err: ' + JSON.stringify(err));
  }
  ```

### setAuthenticatorProperties<sup>9+</sup>

setAuthenticatorProperties(owner: string, callback: AuthCallback): void

Sets the authenticator attributes of an application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name   | Type                 | Mandatory | Description                    |
| -------- | --------------------- | ----- | ----------------------- |
| owner    | string                | Yes   | Owner of the authenticator. The value is the bundle name of the application.         |
| callback | [AuthCallback](#authcallback9) | Yes   | Callback used to return the result.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid owner. |
| 12300010 | Account service busy. |
| 12300113 | Authenticator service not found. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { Want } from '@kit.AbilityKit';

  try {
    appAccountManager.setAuthenticatorProperties('com.example.accountjsdemo', {
      onResult: (resultCode: number, result?: appAccount.AuthResult) => {
        console.log('setAuthenticatorProperties onResult, resultCode: ' + JSON.stringify(resultCode));
        console.log('setAuthenticatorProperties onResult, result: ' + JSON.stringify(result));
      },
      onRequestRedirected: (request: Want) => {
        console.log('setAuthenticatorProperties onRequestRedirected, request: ' + JSON.stringify(request));
      }
    });
  } catch (err) {
    console.error('setAuthenticatorProperties err: ' + JSON.stringify(err));
  }
  ```

### setAuthenticatorProperties<sup>9+</sup>

setAuthenticatorProperties(owner: string, options: SetPropertiesOptions, callback: AuthCallback): void

Sets the authenticator properties. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name   | Type                 | Mandatory | Description                    |
| -------- | --------------------- | ----- | ----------------------- |
| owner    | string                | Yes   | Owner of the authenticator. The value is the bundle name of the application.         |
| options  | [SetPropertiesOptions](#setpropertiesoptions9)  | Yes   | Authenticator properties to set.         |
| callback | [AuthCallback](#authcallback9) | Yes   | Authenticator callback used to return the result.|

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid owner or options. |
| 12300010 | Account service busy. |
| 12300113 | Authenticator service not found. |
| 12300114 | Authenticator service exception. |

**Example**

  ```ts
  import { Want } from '@kit.AbilityKit';

  let options: appAccount.SetPropertiesOptions = {
    properties: {prop1: 'value1'}
  };
  try {
    appAccountManager.setAuthenticatorProperties('com.example.accountjsdemo', options, {
      onResult: (resultCode: number, result?: appAccount.AuthResult) => {
        console.log('setAuthenticatorProperties onResult, resultCode: ' + JSON.stringify(resultCode));
        console.log('setAuthenticatorProperties onResult, result: ' + JSON.stringify(result));
      },
      onRequestRedirected: (request: Want) => {
        console.log('setAuthenticatorProperties onRequestRedirected, request: ' + JSON.stringify(request));
      }
    });
  } catch (err) {
    console.error('setAuthenticatorProperties err: ' + JSON.stringify(err));
  } 

  ```

### addAccount<sup>(deprecated)</sup>

addAccount(name: string, callback: AsyncCallback&lt;void&gt;): void

Adds an application account with the given name. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
>This API is supported since API version 7 and deprecated since API version 9. Use [createAccount](#createaccount9) instead.


**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description                  |
| -------- | ------------------------- | ---- | -------------------- |
| name     | string                    | Yes   | Name of the application account to create.         |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.addAccount('WangWu', (err: BusinessError) => { 
      console.error('addAccount err: ' + JSON.stringify(err));
  });
  ```

### addAccount<sup>(deprecated)</sup>

addAccount(name: string, extraInfo: string, callback: AsyncCallback&lt;void&gt;): void

Adds an application account name and additional information. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [createAccount](#createaccount9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name      | Type                       | Mandatory  | Description                                      |
| --------- | ------------------------- | ---- | ---------------------------------------- |
| name      | string                    | Yes   | Name of the application account to create.                             |
| extraInfo | string                    | Yes   | Additional information (information that can be converted to the string type). It cannot contain sensitive information, such as the application account password and token.|
| callback  | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.            |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.addAccount('LiSi', 'token101', (err: BusinessError) => { 
    console.error('addAccount err: ' + JSON.stringify(err));
  });
  ```

### addAccount<sup>(deprecated)</sup>

addAccount(name: string, extraInfo?: string): Promise&lt;void&gt;

Adds an application account name and additional information. This API uses an asynchronous callback to return the result. This API uses a promise to return the result.

> **NOTE** 
> This API is supported since API version 7 and deprecated since API version 9. Use [createAccount](#createaccount9-2) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name      | Type    | Mandatory  | Description                                      |
| --------- | ------ | ---- | ---------------------------------------- |
| name      | string | Yes   | Name of the application account to create.                           |
| extraInfo | string | No   | Additional information (information that can be converted to the string type). <br>The additional information cannot be sensitive information (such as the password and token) of the application account.<br>By default, no value is passed, which means no additional information needs to be added for the account.|

**Return value**

| Type                 | Description                   |
| ------------------- | --------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.addAccount('LiSi', 'token101').then(()=> { 
    console.log('addAccount Success');
  }).catch((err: BusinessError) => {
    console.error('addAccount err: ' + JSON.stringify(err));
  });
  ```

### addAccountImplicitly<sup>(deprecated)</sup>

addAccountImplicitly(owner: string, authType: string, options: {[key: string]: any;}, callback: AuthenticatorCallback): void

Adds an application account implicitly based on the specified owner. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [createAccountImplicitly](#createaccountimplicitly9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                   | Mandatory  | Description                     |
| -------- | --------------------- | ---- | ----------------------- |
| owner    | string                | Yes   | Owner of the application account. The value is the bundle name of the application.         |
| authType | string                | Yes   | Authentication type. The authentication type is customized. |
| options  | {[key: string]: any}  | Yes   | Authentication options, which can be set as required.|
| callback | [AuthenticatorCallback](#authenticatorcallbackdeprecated) | Yes   | Authenticator callback used to return the result.        |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { Want, common } from '@kit.AbilityKit';

  @Entry
  @Component
  struct Index {
    context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

    onResultCallback(code: number, result: Record<string, Object>): void {
      console.log('resultCode: ' + code);
      console.log('result: ' + JSON.stringify(result));
    }

    onRequestRedirectedCallback(request: Want): void {
      let wantInfo: Want = {
        deviceId: '',
        bundleName: 'com.example.accountjsdemo',
        action: 'ohos.want.action.viewData',
        entities: ['entity.system.default'],
      }
      this.context.startAbility(wantInfo).then(() => {
        console.log('startAbility successfully');
      }).catch((err: BusinessError) => {
        console.error('startAbility err: ' + JSON.stringify(err));
      })
    }

    aboutToAppear(): void {
      appAccountManager.addAccountImplicitly('com.example.accountjsdemo', 'getSocialData', {}, {
        onResult: this.onResultCallback,
        onRequestRedirected: this.onRequestRedirectedCallback
      });
    }
    build() {}
  }
  ```

### deleteAccount<sup>(deprecated)</sup>

deleteAccount(name: string, callback: AsyncCallback&lt;void&gt;): void

Deletes an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [removeAccount](#removeaccount9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description              |
| -------- | ------------------------- | ---- | ---------------- |
| name     | string                    | Yes   | Name of the target application account.     |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.deleteAccount('ZhaoLiu', (err: BusinessError) => { 
      console.error('deleteAccount err: ' + JSON.stringify(err));
   });
  ```

### deleteAccount<sup>(deprecated)</sup>

deleteAccount(name: string): Promise&lt;void&gt;

Deletes an application account. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [removeAccount](#removeaccount9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name | Type    | Mandatory  | Description         |
| ---- | ------ | ---- | ----------- |
| name | string | Yes   | Name of the target application account.|

**Return value**

| Type                 | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  appAccountManager.deleteAccount('ZhaoLiu').then(() => { 
        console.log('deleteAccount Success');
   }).catch((err: BusinessError) => {
      console.error('deleteAccount err: ' + JSON.stringify(err));
  });
  ```
### disableAppAccess<sup>(deprecated)</sup>

disableAppAccess(name: string, bundleName: string, callback: AsyncCallback&lt;void&gt;): void

Disables an application account from accessing an application. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setAppAccess](#setappaccess9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type                       | Mandatory  | Description                               |
| ---------- | ------------------------- | ---- | --------------------------------- |
| name       | string                    | Yes   | Name of the target application account.                 |
| bundleName | string                    | Yes   | Bundle name of the application.                        |
| callback   | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  appAccountManager.disableAppAccess('ZhangSan', 'com.example.accountjsdemo', (err: BusinessError) => { 
      console.error('disableAppAccess err: ' + JSON.stringify(err));
  });
  ```

### disableAppAccess<sup>(deprecated)</sup>

disableAppAccess(name: string, bundleName: string): Promise&lt;void&gt;

Disables an application account from accessing an application. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setAppAccess](#setappaccess9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type    | Mandatory  | Description              |
| ---------- | ------ | ---- | ---------------- |
| name       | string | Yes   | Name of the target application account.|
| bundleName | string | Yes   | Bundle name of the application.       |

**Return value**

| Type                 | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  appAccountManager.disableAppAccess('ZhangSan', 'com.example.accountjsdemo').then(() => { 
      console.log('disableAppAccess Success');
  }).catch((err: BusinessError) => {
      console.error('disableAppAccess err: ' + JSON.stringify(err));
  });
  ```

### enableAppAccess<sup>(deprecated)</sup>

enableAppAccess(name: string, bundleName: string, callback: AsyncCallback&lt;void&gt;): void

Enables an application account to access an application. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setAppAccess](#setappaccess9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type                       | Mandatory  | Description                               |
| ---------- | ------------------------- | ---- | --------------------------------- |
| name       | string                    | Yes   | Name of the target application account.                          |
| bundleName | string                    | Yes   | Bundle name of the application.                        |
| callback   | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.enableAppAccess('ZhangSan', 'com.example.accountjsdemo', (err: BusinessError) => {
      if (err) {
        console.error('enableAppAccess err: ' + JSON.stringify(err));
      } else {
        console.log('enableAppAccess successful.');
      }
   });
  ```

### enableAppAccess<sup>(deprecated)</sup>

enableAppAccess(name: string, bundleName: string): Promise&lt;void&gt;

Enables an application account to access an application. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setAppAccess](#setappaccess9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type    | Mandatory  | Description       |
| ---------- | ------ | ---- | --------- |
| name       | string | Yes   | Name of the target application account.  |
| bundleName | string | Yes   | Bundle name of the application.|

**Return value**

| Type                 | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.enableAppAccess('ZhangSan', 'com.example.accountjsdemo').then(() => { 
       console.log('enableAppAccess Success');
  }).catch((err: BusinessError) => {
      console.error('enableAppAccess err: ' + JSON.stringify(err));
  });
  ```

### checkAppAccountSyncEnable<sup>(deprecated)</sup>

checkAppAccountSyncEnable(name: string, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether data synchronization is enabled for an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [checkDataSyncEnabled](#checkdatasyncenabled9) instead.

**Required permissions**: ohos.permission.DISTRIBUTED_DATASYNC

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                          | Mandatory  | Description                   |
| -------- | ---------------------------- | ---- | --------------------- |
| name     | string                       | Yes   | Name of the target application account.              |
| callback | AsyncCallback&lt;boolean&gt; | Yes   | Callback used to return the result. The value **true** means data synchronization is enabled for the application account; the value **false** means the opposite.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.checkAppAccountSyncEnable('ZhangSan', (err: BusinessError, result: boolean) => { 
    if (err) {
      console.error('checkAppAccountSyncEnable code: ' + JSON.stringify(err));
    } else {
      console.log('checkAppAccountSyncEnable result: ' + result);
    }
  });
  ```

### checkAppAccountSyncEnable<sup>(deprecated)</sup>

checkAppAccountSyncEnable(name: string): Promise&lt;boolean&gt;

Checks whether data synchronization is enabled for an application account. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [checkDataSyncEnabled](#checkdatasyncenabled9-1) instead.

**Required permissions**: ohos.permission.DISTRIBUTED_DATASYNC

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name | Type    | Mandatory  | Description     |
| ---- | ------ | ---- | ------- |
| name | string | Yes   | Name of the target application account.|

**Return value**

| Type                    | Description                   |
| ---------------------- | --------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means data synchronization is enabled for the application account; the value **false** means the opposite.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.checkAppAccountSyncEnable('ZhangSan').then((data: boolean) => { 
      console.log('checkAppAccountSyncEnable, result: ' + data);
  }).catch((err: BusinessError) => {
      console.error('checkAppAccountSyncEnable err: ' + JSON.stringify(err));
  });
  ```

### setAccountCredential<sup>(deprecated)</sup>

setAccountCredential(name: string, credentialType: string, credential: string,callback: AsyncCallback&lt;void&gt;): void

Sets a credential for an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [setCredential](#setcredential9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name           | Type                       | Mandatory  | Description           |
| -------------- | ------------------------- | ---- | ------------- |
| name           | string                    | Yes   | Name of the target application account.    |
| credentialType | string                    | Yes   | Type of the credential to set.    |
| credential     | string                    | Yes   | Credential value.     |
| callback       | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setAccountCredential('ZhangSan', 'credentialType001', 'credential001', (err: BusinessError) => { 
    if (err) {
      console.error('setAccountCredential err: ' + JSON.stringify(err));
    } else {
      console.log('setAccountCredential successful.');
    }
  });
  ```

### setAccountCredential<sup>(deprecated)</sup>

setAccountCredential(name: string, credentialType: string, credential: string): Promise&lt;void&gt;

Sets a credential for an application account. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [setCredential](#setcredential9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name           | Type    | Mandatory  | Description        |
| -------------- | ------ | ---- | ---------- |
| name           | string | Yes   | Name of the target application account.  |
| credentialType | string | Yes   | Type of the credential to set.|
| credential     | string | Yes   | Credential value.|

**Return value**

| Type                 | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setAccountCredential('ZhangSan', 'credentialType001', 'credential001').then(() => { 
      console.log('setAccountCredential Success');
  }).catch((err: BusinessError) => {
      console.error('setAccountCredential err: ' + JSON.stringify(err));
  });
  ```

### setAccountExtraInfo<sup>(deprecated)</sup>

setAccountExtraInfo(name: string, extraInfo: string, callback: AsyncCallback&lt;void&gt;): void

Sets additional information for an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setCustomData](#setcustomdata9) instead.


**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name      | Type                       | Mandatory  | Description             |
| --------- | ------------------------- | ---- | --------------- |
| name      | string                    | Yes   | Name of the application account to create.        |
| extraInfo | string                    | Yes   | Additional information (information that can be converted to the string type). It cannot contain sensitive information, such as the application account password and token.      |
| callback  | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setAccountExtraInfo('ZhangSan', 'Tk002', (err: BusinessError) => { 
    if (err) {
      console.error('setAccountExtraInfo err: ' + JSON.stringify(err));
    } else {
      console.log('setAccountExtraInfo successful.');
    }
  });
  ```

### setAccountExtraInfo<sup>(deprecated)</sup>

setAccountExtraInfo(name: string, extraInfo: string): Promise&lt;void&gt;

Sets additional information for an application account. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setCustomData](#setcustomdata9-1) instead.


**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name      | Type    | Mandatory  | Description       |
| --------- | ------ | ---- | --------- |
| name      | string | Yes   | Name of the target application account.  |
| extraInfo | string | Yes   | Additional information (information that can be converted to the string type). It cannot contain sensitive information, such as the application account password and token.|

**Return value**

| Type                 | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setAccountExtraInfo('ZhangSan', 'Tk002').then(() => { 
      console.log('setAccountExtraInfo Success');
  }).catch((err: BusinessError) => {
      console.error('setAccountExtraInfo err: ' + JSON.stringify(err));
  });
  ```

### setAppAccountSyncEnable<sup>(deprecated)</sup>

setAppAccountSyncEnable(name: string, isEnable: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets data synchronization for an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setDataSyncEnabled](#setdatasyncenabled9) instead.

**Required permissions**: ohos.permission.DISTRIBUTED_DATASYNC

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description                       |
| -------- | ------------------------- | ---- | ------------------------- |
| name     | string                    | Yes   | Name of the target application account.                 |
| isEnable | boolean                   | Yes   | Whether to enable data synchronization. The value **true** means that data synchronization is enabled, and **false** means the opposite.  |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setAppAccountSyncEnable('ZhangSan', true, (err: BusinessError) => {
    if (err) {
      console.error('setAppAccountSyncEnable err: ' + JSON.stringify(err));
    } else {
      console.log('setAppAccountSyncEnable successful.');
    }
  });
  ```

### setAppAccountSyncEnable<sup>(deprecated)</sup>

setAppAccountSyncEnable(name: string, isEnable: boolean): Promise&lt;void&gt;

Sets data synchronization for an application account. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setDataSyncEnabled](#setdatasyncenabled9-1) instead.

**Required permissions**: ohos.permission.DISTRIBUTED_DATASYNC

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type     | Mandatory  | Description         |
| -------- | ------- | ---- | ----------- |
| name     | string  | Yes   | Name of the target application account.    |
| isEnable | boolean | Yes   | Whether to enable data synchronization. The value **true** means that data synchronization is enabled, and **false** means the opposite.|

**Return value**

| Type                 | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setAppAccountSyncEnable('ZhangSan', true).then(() => { 
      console.log('setAppAccountSyncEnable Success');
  }).catch((err: BusinessError) => {
      console.error('setAppAccountSyncEnable err: ' + JSON.stringify(err));
  });
  ```

### setAssociatedData<sup>(deprecated)</sup>

setAssociatedData(name: string, key: string, value: string, callback: AsyncCallback&lt;void&gt;): void

Sets data to be associated with an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setCustomData](#setcustomdata9) instead.


**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description               |
| -------- | ------------------------- | ---- | ----------------- |
| name     | string                    | Yes   | Name of the target application account.          |
| key      | string                    | Yes   | Key of the data to set.|
| value    | string                    | Yes   | Value of the data to set.        |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setAssociatedData('ZhangSan', 'k001', 'v001', (err: BusinessError) => {
    if (err) {
      console.error('setAssociatedData err: ' + JSON.stringify(err));
    } else {
      console.log('setAssociatedData successful.');
    }
  });
  ```

### setAssociatedData<sup>(deprecated)</sup>

setAssociatedData(name: string, key: string, value: string): Promise&lt;void&gt;

Sets data to be associated with an application account. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [setCustomData](#setcustomdata9-1) instead.


**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name  | Type    | Mandatory  | Description               |
| ----- | ------ | ---- | ----------------- |
| name  | string | Yes   | Name of the target application account.          |
| key      | string | Yes   | Key of the data to set.|
| value    | string | Yes   | Value of the data to set.|

**Return value**

| Type                 | Description                   |
| :------------------ | :-------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setAssociatedData('ZhangSan', 'k001', 'v001').then(() => { 
      console.log('setAssociatedData Success');
  }).catch((err: BusinessError) => {
      console.error('setAssociatedData err: ' + JSON.stringify(err));
  });
  ```

### getAllAccessibleAccounts<sup>(deprecated)</sup>

getAllAccessibleAccounts(callback: AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt;): void

Obtains information about all accessible application accounts. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getAllAccounts](#getallaccounts9) instead.

**Required permissions**: ohos.permission.GET_ALL_APP_ACCOUNTS (available only for system applications)

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                      | Mandatory  | Description       |
| -------- | ---------------------------------------- | ---- | --------- |
| callback | AsyncCallback&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of accessible application accounts. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAllAccessibleAccounts((err: BusinessError, data: appAccount.AppAccountInfo[])=>{
  	console.debug('getAllAccessibleAccounts err: ' + JSON.stringify(err));
  	console.debug('getAllAccessibleAccounts data: ' + JSON.stringify(data));
  });
  ```

### getAllAccessibleAccounts<sup>(deprecated)</sup>

getAllAccessibleAccounts(): Promise&lt;Array&lt;AppAccountInfo&gt;&gt;

Obtains information about all accessible application accounts. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getAllAccounts](#getallaccounts9-1) instead.

**Required permissions**: ohos.permission.GET_ALL_APP_ACCOUNTS (available only for system applications)

**System capability**: SystemCapability.Account.AppAccount

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | Promise used to return information about all accessible accounts.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAllAccessibleAccounts().then((data: appAccount.AppAccountInfo[]) => { 
       console.log('getAllAccessibleAccounts: ' + data);
  }).catch((err: BusinessError) => {
      console.error('getAllAccessibleAccounts err: ' + JSON.stringify(err));
  });
  ```

### getAllAccounts<sup>(deprecated)</sup>

getAllAccounts(owner: string, callback: AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt;): void

Obtains the application accounts that can be accessed by the invoker based on the application account owner. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getAccountsByOwner](#getaccountsbyowner9) instead.

**Required permissions**: ohos.permission.GET_ALL_APP_ACCOUNTS (available only for system applications)

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                      | Mandatory  | Description       |
| -------- | ---------------------------------------- | ---- | --------- |
| owner    | string                                   | Yes   | Owner of the application account. The value is the bundle name of the application.   |
| callback | AsyncCallback&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | Yes   | Callback used to return information about all accessible application accounts.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  const selfBundle = 'com.example.actsgetallaaccounts';
  appAccountManager.getAllAccounts(selfBundle, (err: BusinessError, data: appAccount.AppAccountInfo[])=>{
  	console.debug('getAllAccounts err: ' + JSON.stringify(err));
  	console.debug('getAllAccounts data:' + JSON.stringify(data));
  });
  ```

### getAllAccounts<sup>(deprecated)</sup>

getAllAccounts(owner: string): Promise&lt;Array&lt;AppAccountInfo&gt;&gt;

Obtains the application accounts that can be accessed by the invoker based on the application account owner. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getAccountsByOwner](#getaccountsbyowner9-1) instead.

**Required permissions**: ohos.permission.GET_ALL_APP_ACCOUNTS (available only for system applications)

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name  | Type    | Mandatory  | Description    |
| ----- | ------ | ---- | ------ |
| owner | string | Yes   | Owner of the application account. The value is the bundle name of the application.|

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | Promise used to return the application accounts that can be accessed by the invoker.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  const selfBundle = 'com.example.actsgetallaaccounts';
  appAccountManager.getAllAccounts(selfBundle).then((data: appAccount.AppAccountInfo[]) => { 
       console.log('getAllAccounts: ' + data);
  }).catch((err: BusinessError) => {
      console.error('getAllAccounts err: ' + JSON.stringify(err));
  });
  ```

### getAccountCredential<sup>(deprecated)</sup>

getAccountCredential(name: string, credentialType: string, callback: AsyncCallback&lt;string&gt;): void

Obtains the credential of an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getCredential](#getcredential9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name           | Type                         | Mandatory  | Description            |
| -------------- | --------------------------- | ---- | -------------- |
| name           | string                      | Yes   | Name of the target application account.       |
| credentialType | string                      | Yes   | Type of the credential to obtain.|
| callback       | AsyncCallback&lt;string&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the credential obtained. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAccountCredential('ZhangSan', 'credentialType001', (err: BusinessError, result: string) => { 
    if (err) {
      console.error('getAccountCredential err: ' + JSON.stringify(err));
    } else {
      console.log('getAccountCredential result: ' + result);
    }
  });
  ```

### getAccountCredential<sup>(deprecated)</sup>

getAccountCredential(name: string, credentialType: string): Promise&lt;string&gt;

Obtains the credential of an application account. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getCredential](#getcredential9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name           | Type    | Mandatory  | Description        |
| -------------- | ------ | ---- | ---------- |
| name           | string | Yes   | Name of the target application account.   |
| credentialType | string | Yes   | Type of the credential to obtain.|

**Return value**

| Type                   | Description                   |
| :-------------------- | :-------------------- |
| Promise&lt;string&gt; | Promise used to return the credential obtained.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAccountCredential('ZhangSan', 'credentialType001').then((data: string) => { 
      console.log('getAccountCredential, result: ' + data);
  }).catch((err: BusinessError) => {
      console.error('getAccountCredential err: ' + JSON.stringify(err));
  });
  ```

### getAccountExtraInfo<sup>(deprecated)</sup>

getAccountExtraInfo(name: string, callback: AsyncCallback&lt;string&gt;): void

Obtains additional information of an application account. Additional information refers to other information that can be converted to the string type. It cannot contain sensitive information, such as the application account password and token. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getCustomData](#getcustomdata9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                         | Mandatory  | Description             |
| -------- | --------------------------- | ---- | --------------- |
| name     | string                      | Yes   | Name of the target application account.        |
| callback | AsyncCallback&lt;string&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the additional information obtained. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAccountExtraInfo('ZhangSan', (err: BusinessError, result: string) => { 
    if (err) {
      console.error('getAccountExtraInfo err: ' + JSON.stringify(err));
    } else {
      console.log('getAccountExtraInfo result: ' + result);
    }
  });
  ```

### getAccountExtraInfo<sup>(deprecated)</sup>

getAccountExtraInfo(name: string): Promise&lt;string&gt;

Obtains additional information of an application account. Additional information refers to other information that can be converted to the string type. It cannot contain sensitive information, such as the application account password and token. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getCustomData](#getcustomdata9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name | Type    | Mandatory  | Description     |
| ---- | ------ | ---- | ------- |
| name | string | Yes   | Name of the target application account.|

**Return value**

| Type                   | Description                   |
| :-------------------- | :-------------------- |
| Promise&lt;string&gt; | Promise used to return the additional information obtained.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAccountExtraInfo('ZhangSan').then((data: string) => { 
      console.log('getAccountExtraInfo, result: ' + data);
  }).catch((err: BusinessError) => {
      console.error('getAccountExtraInfo err: ' + JSON.stringify(err));
  });
  ```

### getAssociatedData<sup>(deprecated)</sup>

getAssociatedData(name: string, key: string, callback: AsyncCallback&lt;string&gt;): void

Obtains data associated with an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getCustomData](#getcustomdata9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                         | Mandatory  | Description               |
| -------- | --------------------------- | ---- | ----------------- |
| name     | string                      | Yes   | Name of the target application account.          |
| key      | string                      | Yes   | Key of the data to obtain.        |
| callback | AsyncCallback&lt;string&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the data obtained. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAssociatedData('ZhangSan', 'k001', (err: BusinessError, result: string) => { 
    if (err) {
      console.error('getAssociatedData err: ' + JSON.stringify(err));
    } else {
      console.log('getAssociatedData result: ' + result);
    }
  });
  ```

### getAssociatedData<sup>(deprecated)</sup>

getAssociatedData(name: string, key: string): Promise&lt;string&gt;

Obtains data associated with an application account. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [getCustomData](#getcustomdata9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name | Type    | Mandatory  | Description       |
| ---- | ------ | ---- | --------- |
| name | string | Yes   | Name of the target application account.  |
| key  | string | Yes   | Key of the data to obtain.|

**Return value**

| Type                   | Description                   |
| :-------------------- | :-------------------- |
| Promise&lt;string&gt; | Promise used to return the data obtained.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAssociatedData('ZhangSan', 'k001').then((data: string) => { 
       console.log('getAssociatedData: ' + data);
  }).catch((err: BusinessError) => {
      console.error('getAssociatedData err: ' + JSON.stringify(err));
  });
  ```

### on('change')<sup>(deprecated)</sup>

on(type: 'change', owners: Array&lt;string&gt;, callback: Callback&lt;Array&lt;AppAccountInfo&gt;&gt;): void

Subscribes to account information changes of apps.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [on('accountChange')](#onaccountchange9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                      | Mandatory  | Description                            |
| -------- | ---------------------------------------- | ---- | ------------------------------ |
| type     | 'change'                                 | Yes   | Event type to subscribe to. The value is **'change'**. An event will be reported when the account information changes.|
| owners   | Array&lt;string&gt;                      | Yes   | Application bundle names of the account.                     |
| callback | Callback&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | Yes   | Callback registered to return the list of changed application accounts.          |

**Example**

  ```ts
  function changeOnCallback(data: appAccount.AppAccountInfo[]): void {
  	console.debug('receive change data:' + JSON.stringify(data));
  }
  try{
  	appAccountManager.on('change', ['com.example.actsaccounttest'], changeOnCallback);
  }
  catch(err){
  	console.error('on accountOnOffDemo err:' + JSON.stringify(err));
  }
  ```

### off('change')<sup>(deprecated)</sup>

off(type: 'change', callback?: Callback&lt;Array&lt;AppAccountInfo&gt;&gt;): void

Unsubscribes from account information changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. Use [off('accountChange')](#offaccountchange9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                              | Mandatory  | Description          |
| -------- | -------------------------------- | ---- | ------------ |
| type     | 'change'                         | Yes   | Event type to subscribe to. The value is **'change'**. An event will be reported when the account information changes.   |
| callback | Callback&lt;Array&lt;[AppAccountInfo](#appaccountinfo)&gt;&gt; | No   | Callback to unregister. By default, no value is passed, which means to unregister all callbacks for the specified event.|

**Example**

  ```ts
  function changeOnCallback(data: appAccount.AppAccountInfo[]): void {
  	console.debug('receive change data: ' + JSON.stringify(data));
  	appAccountManager.off('change', () => {
  		console.debug('off finish');
  	})
  }
  try{
  	appAccountManager.on('change', ['com.example.actsaccounttest'], changeOnCallback);
  }
  catch(err){
  	console.error('on accountOnOffDemo err: ' + JSON.stringify(err));
  }
  ```

### authenticate<sup>(deprecated)</sup>

authenticate(name: string, owner: string, authType: string, options: {[key: string]: any;}, callback: AuthenticatorCallback): void

Authenticates an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [auth](#auth9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                   | Mandatory  | Description             |
| -------- | --------------------- | ---- | --------------- |
| name     | string                | Yes   | Name of the target application account.    |
| owner    | string                | Yes   | Owner of the application account. The value is the bundle name of the application. |
| authType | string                | Yes   | Authentication type.          |
| options  | {[key: string]: any}  | Yes   | Options for the authentication.      |
| callback | [AuthenticatorCallback](#authenticatorcallbackdeprecated) | Yes   | Authenticator callback used to return the result.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { Want, common } from '@kit.AbilityKit';

  @Entry
  @Component
  struct Index {
    context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

    onResultCallback(code: number, result: Record<string, Object>): void {
      console.log('resultCode: ' + code);
      console.log('result: ' + JSON.stringify(result));
    }

    onRequestRedirectedCallback(request: Want): void {
      let wantInfo: Want = {
        deviceId: '',
        bundleName: 'com.example.accountjsdemo',
        action: 'ohos.want.action.viewData',
        entities: ['entity.system.default'],
      }
      this.context.startAbility(wantInfo).then(() => {
        console.log('startAbility successfully');
      }).catch((err: BusinessError) => {
        console.error('startAbility err: ' + JSON.stringify(err));
      })
    }

    aboutToAppear(): void {
      appAccountManager.authenticate('LiSi', 'com.example.accountjsdemo', 'getSocialData', {}, {
        onResult: this.onResultCallback,
        onRequestRedirected: this.onRequestRedirectedCallback
      });
    }
    build() {}
  }
  ```

### getOAuthToken<sup>(deprecated)</sup>

getOAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback&lt;string&gt;): void

Obtains the authorization token of the specified authentication type for an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [getAuthToken](#getauthtoken9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                         | Mandatory  | Description         |
| -------- | --------------------------- | ---- | ----------- |
| name     | string                      | Yes   | Name of the target application account.   |
| owner    | string                      | Yes   | Owner of the application account. The value is the bundle name of the application.|
| authType | string                      | Yes   | Authentication type.      |
| callback | AsyncCallback&lt;string&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authorization token value obtained. Otherwise, **err** is an error object.  |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData',
    (err: BusinessError, data: string) => {
      if (err) {
        console.error('getOAuthToken err: ' + JSON.stringify(err));
      } else {
        console.log('getOAuthToken token: ' + data);
      }
    });
  ```

### getOAuthToken<sup>(deprecated)</sup>

getOAuthToken(name: string, owner: string, authType: string): Promise&lt;string&gt;

Obtains the authorization token of the specified authentication type for an application account. This API uses a promise to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [getAuthToken](#getauthtoken9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type    | Mandatory  | Description         |
| -------- | ------ | ---- | ----------- |
| name     | string | Yes   | Name of the target application account.   |
| owner    | string | Yes   | Owner of the application account. The value is the bundle name of the application.|
| authType | string | Yes   | Authentication type.      |

**Return value**

| Type                   | Description                   |
| --------------------- | --------------------- |
| Promise&lt;string&gt; | Promise used to return the authorization token obtained.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData').then((data: string) => {
       console.log('getOAuthToken token: ' + data);
  }).catch((err: BusinessError) => {
      console.error('getOAuthToken err: ' + JSON.stringify(err));
  });
  ```

### setOAuthToken<sup>(deprecated)</sup>

setOAuthToken(name: string, authType: string, token: string, callback: AsyncCallback&lt;void&gt;): void

Sets an authorization token of the specific authentication type for an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [setAuthToken](#setauthtoken9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description      |
| -------- | ------------------------- | ---- | -------- |
| name     | string                    | Yes   | Name of the target application account.|
| authType | string                    | Yes   | Authentication type.   |
| token    | string                    | Yes   | Authorization token to set.|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setOAuthToken('LiSi', 'getSocialData', 'xxxx', (err: BusinessError) => {
    if (err) {
      console.error('setOAuthToken err: ' + JSON.stringify(err));
    } else {
      console.log('setOAuthToken successful.');
    }
  });
  ```

### setOAuthToken<sup>(deprecated)</sup>

setOAuthToken(name: string, authType: string, token: string): Promise&lt;void&gt;

Sets an authorization token of the specific authentication type for an application account. This API uses a promise to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [setAuthToken](#setauthtoken9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type    | Mandatory  | Description      |
| -------- | ------ | ---- | -------- |
| name     | string | Yes   | Name of the target application account.|
| authType | string | Yes   | Authentication type.   |
| token    | string | Yes   | Authorization token to set.|

**Return value**

| Type                 | Description                   |
| ------------------- | --------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setOAuthToken('LiSi', 'getSocialData', 'xxxx').then(() => {
      console.log('setOAuthToken successfully');
  }).catch((err: BusinessError) => {
      console.error('setOAuthToken err: ' + JSON.stringify(err));
  });
  ```

### deleteOAuthToken<sup>(deprecated)</sup>

deleteOAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback&lt;void&gt;): void

Deletes the authorization token of the specified authentication type for an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [deleteAuthToken](#deleteauthtoken9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                       | Mandatory  | Description          |
| -------- | ------------------------- | ---- | ------------ |
| name     | string                    | Yes   | Name of the target application account.    |
| owner    | string                    | Yes   | Owner of the application account. The value is the bundle name of the application. |
| authType | string                    | Yes   | Authentication type.       |
| token    | string                    | Yes   | Authorization token to delete.|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.    |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.deleteOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx',
    (err: BusinessError) => {
      if (err) {
        console.error('deleteOAuthToken err: ' + JSON.stringify(err));
      } else {
        console.log('deleteOAuthToken successful.');
      }
    });
  ```

### deleteOAuthToken<sup>(deprecated)</sup>

deleteOAuthToken(name: string, owner: string, authType: string, token: string): Promise&lt;void&gt;

Deletes the authorization token of the specified authentication type for an application account. This API uses a promise to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [deleteAuthToken](#deleteauthtoken9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type    | Mandatory  | Description          |
| -------- | ------ | ---- | ------------ |
| name     | string | Yes   | Name of the target application account.    |
| owner    | string | Yes   | Owner of the application account. The value is the bundle name of the application. |
| authType | string | Yes   | Authentication type.       |
| token    | string | Yes   | Authorization token to delete.|

**Return value**

| Type                 | Description                   |
| ------------------- | --------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.deleteOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx').then(() => {
       console.log('deleteOAuthToken successfully');
  }).catch((err: BusinessError) => {
      console.error('deleteOAuthToken err: ' + JSON.stringify(err));
  });
  ```

### setOAuthTokenVisibility<sup>(deprecated)</sup>

setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets the visibility of an authorization token to an application. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [setAuthTokenVisibility](#setauthtokenvisibility9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type                       | Mandatory  | Description                       |
| ---------- | ------------------------- | ---- | ------------------------- |
| name       | string                    | Yes   | Name of the target application account.                 |
| authType   | string                    | Yes   | Authentication type.                    |
| bundleName | string                    | Yes   | Bundle name of the application.             |
| isVisible  | boolean                   | Yes   | Whether the authorization token is visible to the application. The value **true** means the authorization token is visible to the application; the value **false** means the opposite.|
| callback   | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.                 |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true,
    (err: BusinessError) => {
      if (err) {
        console.error('setOAuthTokenVisibility err: ' + JSON.stringify(err));
      } else {
        console.log('setOAuthTokenVisibility successful.');
      }
    });
  ```

### setOAuthTokenVisibility<sup>(deprecated)</sup>

setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise&lt;void&gt;

Sets the visibility of an authorization token to an application. This API uses a promise to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [setAuthTokenVisibility](#setauthtokenvisibility9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type     | Mandatory  | Description          |
| ---------- | ------- | ---- | ------------ |
| name       | string  | Yes   | Name of the target application account.    |
| authType   | string  | Yes   | Authentication type.       |
| bundleName | string  | Yes   | Bundle name of the application.|
| isVisible  | boolean | Yes   | Whether the authorization token is visible to the application. The value **true** means the authorization token is visible to the application; the value **false** means the opposite.       |

**Return value**

| Type                 | Description                   |
| ------------------- | --------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.setOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true).then(() => {
      console.log('setOAuthTokenVisibility successfully');
  }).catch((err: BusinessError) => {
      console.error('setOAuthTokenVisibility err: ' + JSON.stringify(err));
  });
  ```

### checkOAuthTokenVisibility<sup>(deprecated)</sup>

checkOAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback&lt;boolean&gt;): void

Checks the visibility of an authorization token of the specified authentication type to an application. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [checkAuthTokenVisibility](#checkauthtokenvisibility9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type                          | Mandatory  | Description         |
| ---------- | ---------------------------- | ---- | ----------- |
| name       | string                       | Yes   | Name of the target application account.   |
| authType   | string                       | Yes   | Authentication type.      |
| bundleName | string                       | Yes   | Bundle name of the application.|
| callback   | AsyncCallback&lt;boolean&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** can be **true** (the authorization token is visible to the application) or **false** (the authorization token is not visible to the application). If the operation fails, **err** is an error object.   |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.checkOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo',
    (err: BusinessError, data: boolean) => {
      if (err) {
        console.error('checkOAuthTokenVisibility err: ' + JSON.stringify(err));
      } else {
        console.log('checkOAuthTokenVisibility isVisible: ' + data);
      }
    });
  ```

### checkOAuthTokenVisibility<sup>(deprecated)</sup>

checkOAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise&lt;boolean&gt;

Checks the visibility of an authorization token of the specified authentication type to an application. This API uses a promise to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [checkAuthTokenVisibility](#checkauthtokenvisibility9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name       | Type    | Mandatory  | Description           |
| ---------- | ------ | ---- | ------------- |
| name       | string | Yes   | Name of the target application account.     |
| authType   | string | Yes   | Authentication type.        |
| bundleName | string | Yes   | Bundle name of the application.|

**Return value**

| Type                    | Description                   |
| ---------------------- | --------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the authorization token is visible to the application; the value **false** means the opposite.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.checkOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo').then((
    data: boolean) => {
    console.log('checkOAuthTokenVisibility isVisible: ' + data);
  }).catch((err: BusinessError) => {
    console.error('checkOAuthTokenVisibility err: ' + JSON.stringify(err));
  });
  ```

### getAllOAuthTokens<sup>(deprecated)</sup>

getAllOAuthTokens(name: string, owner: string, callback: AsyncCallback&lt;Array&lt;OAuthTokenInfo&gt;&gt;): void

Obtains all tokens visible to the invoker for an application account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [getAllAuthTokens](#getallauthtokens9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                      | Mandatory  | Description         |
| -------- | ---------------------------------------- | ---- | ----------- |
| name     | string                                   | Yes   | Name of the target application account.   |
| owner    | string                                   | Yes   | Owner of the application account. The value is the bundle name of the application.|
| callback | AsyncCallback&lt;Array&lt;[OAuthTokenInfo](#oauthtokeninfodeprecated)&gt;&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of all tokens visible to the invoker. Otherwise, **err** is an error object.   |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAllOAuthTokens('LiSi', 'com.example.accountjsdemo',
    (err: BusinessError, data: appAccount.OAuthTokenInfo[]) => {
      if (err) {
        console.error('getAllOAuthTokens err: ' + JSON.stringify(err));
      } else {
        console.log('getAllOAuthTokens data: ' + JSON.stringify(data));
      }
    });
  ```

### getAllOAuthTokens<sup>(deprecated)</sup>

getAllOAuthTokens(name: string, owner: string): Promise&lt;Array&lt;OAuthTokenInfo&gt;&gt;

Obtains all tokens visible to the invoker for an application account. This API uses a promise to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [getAllAuthTokens](#getallauthtokens9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name  | Type    | Mandatory  | Description         |
| ----- | ------ | ---- | ----------- |
| name  | string | Yes   | Name of the target application account.   |
| owner | string | Yes   | Owner of the application account. The value is the bundle name of the application.|

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise&lt;Array&lt; [OAuthTokenInfo](#oauthtokeninfodeprecated)&gt;&gt; | Promise used to return the tokens obtained.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAllOAuthTokens('LiSi', 'com.example.accountjsdemo').then((
    data: appAccount.OAuthTokenInfo[]) => {
    console.log('getAllOAuthTokens data: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error('getAllOAuthTokens err: ' + JSON.stringify(err));
  });
  ```

### getOAuthList<sup>(deprecated)</sup>

getOAuthList(name: string, authType: string, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Obtains the authorization list of the specified authentication type for an application account. The authorization list contains all authorized bundles. The token authorization list is set by setOAuthTokenVisibility(#setoauthtokenvisibilitydeprecated). This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [getAuthList](#getauthlist9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                      | Mandatory  | Description                     |
| -------- | ---------------------------------------- | ---- | ----------------------- |
| name     | string                                   | Yes   | Name of the target application account.               |
| authType | string                                   | Yes   | Authentication type.|
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of authorized bundles obtained. Otherwise, **err** is an error object.              |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getOAuthList('LiSi', 'getSocialData', (err: BusinessError, data: string[]) => {
    if (err) {
      console.error('getOAuthList err: ' + JSON.stringify(err));
    } else {
      console.log('getOAuthList data: ' + JSON.stringify(data));
    }
  });
  ```

### getOAuthList<sup>(deprecated)</sup>

getOAuthList(name: string, authType: string): Promise&lt;Array&lt;string&gt;&gt;

Obtains the authorization list of the specified authentication type for an application account. The authorization list contains all authorized bundles. The token authorization list is set by setOAuthTokenVisibility(#setoauthtokenvisibilitydeprecated). This API uses a promise to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [getAuthList](#getauthlist9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type    | Mandatory  | Description                     |
| -------- | ------ | ---- | ----------------------- |
| name     | string | Yes   | Name of the target application account.               |
| authType | string | Yes   | Authentication type.|

**Return value**

| Type                                | Description                   |
| ---------------------------------- | --------------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return a list of authorized bundles.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getOAuthList('LiSi', 'getSocialData').then((data: string[]) => {
       console.log('getOAuthList data: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
      console.error('getOAuthList err: ' + JSON.stringify(err));
  });
  ```

### getAuthenticatorCallback<sup>(deprecated)</sup>

getAuthenticatorCallback(sessionId: string, callback: AsyncCallback&lt;AuthenticatorCallback&gt;): void

Obtains the authenticator callback for an authentication session. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [getAuthCallback](#getauthcallback9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| sessionId | string                                   | Yes   | ID of the authentication session.|
| callback  | AsyncCallback&lt;[AuthenticatorCallback](#authenticatorcallbackdeprecated)&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authenticator callback obtained. Otherwise, **err** is an error object.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';

  export default class EntryAbility extends UIAbility {
    onCreate(want: Want, param: AbilityConstant.LaunchParam) { // Ability lifecycle function.
      let sessionId: string = want.parameters![appAccount.Constants.KEY_SESSION_ID] as string;
      appAccountManager.getAuthenticatorCallback(sessionId,
          (err: BusinessError, callback: appAccount.AuthenticatorCallback) => {
          if (err.code != appAccount.ResultCode.SUCCESS) {
              console.error('getAuthenticatorCallback err: ' + JSON.stringify(err));
              return;
          }
          callback.onResult(appAccount.ResultCode.SUCCESS, {
            name: 'LiSi',
            owner: 'com.example.accountjsdemo',
            authType: 'getSocialData',
            token: 'xxxxxx'}
          );
        });
    }
  }
  ```

### getAuthenticatorCallback<sup>(deprecated)</sup>

getAuthenticatorCallback(sessionId: string): Promise&lt;AuthenticatorCallback&gt;

Obtains the authenticator callback for an authentication session. This API uses a promise to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [getAuthCallback](#getauthcallback9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name      | Type    | Mandatory  | Description      |
| --------- | ------ | ---- | -------- |
| sessionId | string | Yes   | ID of the authentication session.|

**Return value**

| Type                                  | Description                   |
| ------------------------------------ | --------------------- |
| Promise&lt;[AuthenticatorCallback](#authenticatorcallbackdeprecated)&gt; | Promise used to return the authenticator callback obtained.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';

  export default class EntryAbility extends UIAbility {
    onCreate(want: Want, param: AbilityConstant.LaunchParam) { // Ability lifecycle function.
      let sessionId: string = want.parameters![appAccount.Constants.KEY_SESSION_ID] as string;
      appAccountManager.getAuthenticatorCallback(sessionId).then((
        callback: appAccount.AuthenticatorCallback) => {
        callback.onResult(appAccount.ResultCode.SUCCESS, {
          name: 'LiSi',
          owner: 'com.example.accountjsdemo',
          authType: 'getSocialData',
          token: 'xxxxxx'}
        );
      }).catch((err: BusinessError) => {
        console.error('getAuthenticatorCallback err: ' + JSON.stringify(err));
      });
    }
  }
  ```

### getAuthenticatorInfo<sup>(deprecated)</sup>

getAuthenticatorInfo(owner: string, callback: AsyncCallback&lt;AuthenticatorInfo&gt;): void

Obtains the authenticator information of an application. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [queryAuthenticatorInfo](#queryauthenticatorinfo9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name     | Type                                    | Mandatory  | Description         |
| -------- | -------------------------------------- | ---- | ----------- |
| owner    | string                                 | Yes   | Owner of the application account. The value is the bundle name of the application.|
| callback | AsyncCallback&lt;[AuthenticatorInfo](#authenticatorinfo8)&gt; | Yes   | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authenticator information obtained. Otherwise, **err** is an error object.   |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAuthenticatorInfo('com.example.accountjsdemo',
    (err: BusinessError, data: appAccount.AuthenticatorInfo) => {
      if (err) {
        console.error('getAuthenticatorInfo err: ' + JSON.stringify(err));
      } else {
        console.log('getAuthenticatorInfo data: ' + JSON.stringify(data));
      }
    });
  ```

### getAuthenticatorInfo<sup>(deprecated)</sup>

getAuthenticatorInfo(owner: string): Promise&lt;AuthenticatorInfo&gt;

Obtains the authenticator information of an application. This API uses a promise to return the result.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [queryAuthenticatorInfo](#queryauthenticatorinfo9-1) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name  | Type    | Mandatory  | Description         |
| ----- | ------ | ---- | ----------- |
| owner | string | Yes   | Owner of the application account. The value is the bundle name of the application.|

**Return value**

| Type                              | Description                   |
| -------------------------------- | --------------------- |
| Promise&lt;[AuthenticatorInfo](#authenticatorinfo8)&gt; | Promise used to return the authenticator information obtained.|

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  appAccountManager.getAuthenticatorInfo('com.example.accountjsdemo').then((
    data: appAccount.AuthenticatorInfo) => { 
    console.log('getAuthenticatorInfo: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error('getAuthenticatorInfo err: ' + JSON.stringify(err));
  });
  ```

## AppAccountInfo

Defines application account information.

**System capability**: SystemCapability.Account.AppAccount

| Name  | Type    | Mandatory  | Description         |
| ----- | ------ | ---- | ----------- |
| owner | string | Yes   | Owner of the application account. The value is the bundle name of the application.|
| name  | string | Yes   | Name of the application account.   |

## AuthTokenInfo<sup>9+</sup>

Defines authorization token information.

**System capability**: SystemCapability.Account.AppAccount

| Name              | Type           | Mandatory | Description             |
| -------------------- | -------------- | ----- | ---------------- |
| authType<sup>9+</sup>             | string         | Yes   | Authentication type.  |
| token<sup>9+</sup>                | string         | Yes   | Value of the authorization token.      |
| account<sup>9+</sup> | [AppAccountInfo](#appaccountinfo) | No   | Information about the account to which the token belongs. By default, no value is passed in.|

## OAuthTokenInfo<sup>(deprecated)</sup>

Defines authorization token information.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [AuthTokenInfo](#authtokeninfo9) instead.

**System capability**: SystemCapability.Account.AppAccount

| Name              | Type           | Mandatory | Description             |
| -------------------- | -------------- | ----- | ---------------- |
| authType             | string         | Yes   | Authentication type.  |
| token                | string         | Yes   | Value of the authorization token.      |

## AuthenticatorInfo<sup>8+</sup>

Defines OAuth authenticator information.

**System capability**: SystemCapability.Account.AppAccount

| Name    | Type    | Mandatory  | Description        |
| ------- | ------ | ---- | ---------- |
| owner   | string | Yes   | Owner of the authenticator. The value is the bundle name of the application.|
| iconId  | number | Yes   | ID of the authenticator icon. |
| labelId | number | Yes   | ID of the authenticator label. |

## AuthResult<sup>9+</sup>

Defines the authentication result.

**System capability**: SystemCapability.Account.AppAccount

| Name    | Type    | Mandatory  | Description        |
| ------- | ------ | ---- | ---------- |
| account   | [AppAccountInfo](#appaccountinfo) | No   | Information about the account to which the token belongs. By default, no value is passed in.|
| tokenInfo  | [AuthTokenInfo](#authtokeninfo9) | No   | Token information. By default, no value is passed in. |

## CreateAccountOptions<sup>9+</sup>

Defines the options for creating an application account.

**System capability**: SystemCapability.Account.AppAccount

| Name    | Type    | Mandatory  | Description        |
| ------- | ------ | ---- | ---------- |
| customData   | Record<string, string> | No   | Custom data. By default, no value is passed in.|

## CreateAccountImplicitlyOptions<sup>9+</sup>

Defines the options for implicitly creating an application account.

**System capability**: SystemCapability.Account.AppAccount

| Name    | Type    | Mandatory  | Description        |
| ------- | ------ | ---- | ---------- |
| requiredLabels   | Array&lt;string&gt; | No   | Required labels. By default, no value is passed in.|
| authType   | string | No   | Authentication type. By default, no value is passed in.|
| parameters   | Record<string, Object> | No   | Custom parameter object. By default, no value is passed in.|
## SelectAccountsOptions<sup>9+</sup>

Defines the options for selecting accounts.

**System capability**: SystemCapability.Account.AppAccount

| Name         | Type                        | Mandatory | Description               |
| --------------- | --------------------------- | ----- | ------------------- |
| allowedAccounts | Array&lt;[AppAccountInfo](#appaccountinfo)&gt; | No   | Array of allowed accounts. By default, no value is passed in.    |
| allowedOwners   | Array&lt;string&gt;         | No   | Array of the owners of the allowed accounts. By default, no value is passed in.|
| requiredLabels  | Array&lt;string&gt;         | No   | Labels of the authenticator. By default, no value is passed in. |

## VerifyCredentialOptions<sup>9+</sup>

Represents the options for verifying the user credential.

**System capability**: SystemCapability.Account.AppAccount

| Name         | Type                  | Mandatory | Description          |
| -------------- | ---------------------- | ----- | -------------- |
| credentialType | string                 | No   | Credential type. By default, no value is passed in.     |
| credential     | string                 | No   | Credential value. By default, no value is passed in.     |
| parameters     | Record<string, Object> | No   | Custom parameter object. By default, no value is passed in.|


## SetPropertiesOptions<sup>9+</sup>

Represents the options for setting authenticator properties.

**System capability**: SystemCapability.Account.AppAccount

| Name    | Type                   | Mandatory | Description          |
| ---------- | ---------------------- | ----- | -------------- |
| properties | Record<string, Object> | No   | Property object. By default, no value is passed in.     |
| parameters | Record<string, Object> | No   | Custom parameter object. By default, no value is passed in.|

## Constants<sup>8+</sup>

Enumerates the constants.

**System capability**: SystemCapability.Account.AppAccount

| Name                           | Value                   | Description                  |
| -------------------------------- | ---------------------- | ----------------------- |
| ACTION_ADD_ACCOUNT_IMPLICITLY<sup>(deprecated)</sup>    | 'addAccountImplicitly' | Operation of adding an account implicitly. |
| ACTION_AUTHENTICATE<sup>(deprecated)</sup>              | 'authenticate'         | Authentication operation.        |
| ACTION_CREATE_ACCOUNT_IMPLICITLY<sup>9+</sup>    | 'createAccountImplicitly' | Operation of creating an account implicitly. |
| ACTION_AUTH<sup>9+</sup>              | 'auth'         | Authentication operation.        |
| ACTION_VERIFY_CREDENTIAL<sup>9+</sup>    | 'verifyCredential' | Operation of verifying credentials. |
| ACTION_SET_AUTHENTICATOR_PROPERTIES<sup>9+</sup> | 'setAuthenticatorProperties' | Operation of setting authenticator properties.     |
| KEY_NAME                         | 'name'                 | Name of the application account. |
| KEY_OWNER                        | 'owner'                | Bundle name of the application account owner.|
| KEY_TOKEN                        | 'token'                | Token.        |
| KEY_ACTION                       | 'action'               | Operation.        |
| KEY_AUTH_TYPE                    | 'authType'             | Authentication type.    |
| KEY_SESSION_ID                   | 'sessionId'            | Session ID.    |
| KEY_CALLER_PID                   | 'callerPid'            | PID of the caller.   |
| KEY_CALLER_UID                   | 'callerUid'            | UID of the caller.   |
| KEY_CALLER_BUNDLE_NAME           | 'callerBundleName'     | Bundle name of the caller.   |
| KEY_REQUIRED_LABELS<sup>9+</sup> | 'requiredLabels'       | Required labels.   |
| KEY_BOOLEAN_RESULT<sup>9+</sup>  | 'booleanResult'        | Return value of the Boolean type.   |

## ResultCode<sup>(deprecated)</sup>

Enumerates the result codes.

> **NOTE**<br>
> This enum is supported since API version 8 and deprecated since API version 9. For details, see [Account Management Error Codes](errorcode-account.md).

**System capability**: SystemCapability.Account.AppAccount

| Name                                 | Value  | Description          |
| ----------------------------------- | ----- | ------------ |
| SUCCESS                             | 0     | The operation is successful.     |
| ERROR_ACCOUNT_NOT_EXIST             | 10001 | The application account does not exist.  |
| ERROR_APP_ACCOUNT_SERVICE_EXCEPTION | 10002 | The **AppAccountManager** service is abnormal. |
| ERROR_INVALID_PASSWORD              | 10003 | The password is invalid.     |
| ERROR_INVALID_REQUEST               | 10004 | The request is invalid.     |
| ERROR_INVALID_RESPONSE              | 10005 | The response is invalid.     |
| ERROR_NETWORK_EXCEPTION             | 10006 | The network is abnormal.     |
| ERROR_OAUTH_AUTHENTICATOR_NOT_EXIST | 10007 | The authenticator does not exist.   |
| ERROR_OAUTH_CANCELED                | 10008 | The authentication is canceled.     |
| ERROR_OAUTH_LIST_TOO_LARGE          | 10009 | The size of the OAuth list exceeds the limit. |
| ERROR_OAUTH_SERVICE_BUSY            | 10010 | The OAuth service is busy. |
| ERROR_OAUTH_SERVICE_EXCEPTION       | 10011 | The OAuth service is abnormal. |
| ERROR_OAUTH_SESSION_NOT_EXIST       | 10012 | The session to be authenticated does not exist.  |
| ERROR_OAUTH_TIMEOUT                 | 10013 | The authentication timed out.     |
| ERROR_OAUTH_TOKEN_NOT_EXIST         | 10014 | The authorization token does not exist.|
| ERROR_OAUTH_TOKEN_TOO_MANY          | 10015 | The number of OAuth tokens reaches the limit. |
| ERROR_OAUTH_UNSUPPORT_ACTION        | 10016 | The authentication operation is not supported. |
| ERROR_OAUTH_UNSUPPORT_AUTH_TYPE     | 10017 | The authentication type is not supported. |
| ERROR_PERMISSION_DENIED             | 10018 | The required permission is missing.     |

## AuthCallback<sup>9+</sup>

Implements authenticator callbacks.

### onResult<sup>9+</sup>

onResult: (code: number, result?: AuthResult) =&gt; void

Called to return the result of an authentication request.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name   | Type                  | Mandatory  | Description    |
| ------ | -------------------- | ---- | ------ |
| code   | number               | Yes   | Authentication result code.|
| result | [AuthResult](#authresult9) | No   | Authentication result. By default, no value is passed, which means the authentication result is not received. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  let appAccountManager: appAccount.AppAccountManager = appAccount.createAppAccountManager();
  let sessionId = '1234';
  appAccountManager.getAuthCallback(sessionId).then((callback: appAccount.AuthCallback) => {
      let result: appAccount.AuthResult = {
          account: {
            name: 'Lisi',
            owner: 'com.example.accountjsdemo',
          },
          tokenInfo: {
            token: 'xxxxxx',
            authType: 'getSocialData'
          }
      };
      callback.onResult(appAccount.ResultCode.SUCCESS, result);
  }).catch((err: BusinessError) => {
      console.error('getAuthCallback err: ' + JSON.stringify(err));
  });
  ```

### onRequestRedirected<sup>9+</sup>

onRequestRedirected: (request: Want) =&gt; void

Called to redirect a request.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name    | Type  | Mandatory  | Description        |
| ------- | ---- | ---- | ---------- |
| request | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Request to be redirected.|

**Example**

  ```ts
  import { Want } from '@kit.AbilityKit';

  class MyAuthenticator extends appAccount.Authenticator {
      createAccountImplicitly(
        options: appAccount.CreateAccountImplicitlyOptions, callback: appAccount.AuthCallback) {
          let want: Want = {
            bundleName: 'com.example.accountjsdemo',
            abilityName: 'com.example.accountjsdemo.LoginAbility',
          };
          callback.onRequestRedirected(want);
      }

      auth(name: string, authType: string,
        options: Record<string, Object>, callback: appAccount.AuthCallback) {
          let result: appAccount.AuthResult = {
            account: {
              name: 'Lisi',
              owner: 'com.example.accountjsdemo',
            },
            tokenInfo: {
              token: 'xxxxxx',
              authType: 'getSocialData'
            }
          };
          callback.onResult(appAccount.ResultCode.SUCCESS, result);
      }
  }
  ```

### onRequestContinued<sup>9+</sup>

onRequestContinued?: () =&gt; void

Called to continue to process the request.

**System capability**: SystemCapability.Account.AppAccount

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  let appAccountManager: appAccount.AppAccountManager = appAccount.createAppAccountManager();
  let sessionId = '1234';
  appAccountManager.getAuthCallback(sessionId).then((callback: appAccount.AuthCallback) => {
    if (callback.onRequestContinued != undefined) {
      callback.onRequestContinued();
    }
  }).catch((err: BusinessError) => {
    console.error('getAuthCallback err: ' + JSON.stringify(err));
  });
  ```

## AuthenticatorCallback<sup>(deprecated)</sup>

Provides OAuth authenticator callbacks.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. Use [AuthCallback](#authcallback9) instead.

### onResult<sup>(deprecated)</sup>

onResult: (code: number, result: {[key: string]: any;}) =&gt; void

Called to return the result of an authentication request.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. You are advised to use [onResult](#onresult9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name   | Type                  | Mandatory  | Description    |
| ------ | -------------------- | ---- | ------ |
| code   | number               | Yes   | Authentication result code.|
| result | {[key: string]: any} | Yes   | Authentication result. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  let appAccountManager: appAccount.AppAccountManager = appAccount.createAppAccountManager();
  let sessionId = '1234';
  appAccountManager.getAuthenticatorCallback(sessionId).then((callback: appAccount.AuthenticatorCallback) => {
      callback.onResult(appAccount.ResultCode.SUCCESS, {
        name: 'LiSi',
        owner: 'com.example.accountjsdemo',
        authType: 'getSocialData',
        token: 'xxxxxx'}
      );
  }).catch((err: BusinessError) => {
      console.error('getAuthenticatorCallback err: ' + JSON.stringify(err));
  });
  ```

### onRequestRedirected<sup>(deprecated)</sup>

onRequestRedirected: (request: Want) =&gt; void

Called to redirect a request.

> **NOTE**
>
> This enum is supported since API version 8 and deprecated since API version 9. You are advised to use [onRequestRedirected](#onrequestredirected9) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name    | Type  | Mandatory  | Description        |
| ------- | ---- | ---- | ---------- |
| request | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Request to be redirected.|

**Example**

  ```ts
  import { Want } from '@kit.AbilityKit';

  class MyAuthenticator extends appAccount.Authenticator {
      addAccountImplicitly(authType: string, callerBundleName: string,
        options: Record<string, Object>, callback: appAccount.AuthenticatorCallback) {
          let want: Want = {
            bundleName: 'com.example.accountjsdemo',
            abilityName: 'com.example.accountjsdemo.LoginAbility',
          };
          callback.onRequestRedirected(want);
      }

      authenticate(name: string, authType: string, callerBundleName: string,
        options: Record<string, Object>, callback: appAccount.AuthenticatorCallback) {
          callback.onResult(appAccount.ResultCode.SUCCESS, {
            name: name,
            authType: authType,
            token: 'xxxxxx'}
          );
      }
  }
  ```

## Authenticator<sup>8+</sup>

Provides APIs to operate the authenticator.

### createAccountImplicitly<sup>9+</sup>

createAccountImplicitly(options: CreateAccountImplicitlyOptions, callback: AuthCallback): void

Creates an application account implicitly based on the specified account owner. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name             | Type                   | Mandatory  | Description             |
| ---------------- | --------------------- | ---- | --------------- |
| options          | [CreateAccountImplicitlyOptions](#createaccountimplicitlyoptions9)  | Yes   | Options for implicitly creating the account.     |
| callback         | [AuthCallback](#authcallback9) | Yes   | Authenticator callback used to return the result.|

### addAccountImplicitly<sup>(deprecated)</sup>

addAccountImplicitly(authType: string, callerBundleName: string, options: {[key: string]: any;}, callback: AuthenticatorCallback): void

Adds an application account implicitly based on the specified authentication type and options. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [createAccountImplicitly](#createaccountimplicitly9-2) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name             | Type                   | Mandatory  | Description             |
| ---------------- | --------------------- | ---- | --------------- |
| authType         | string                | Yes   | Authentication type.     |
| callerBundleName | string                | Yes   | Bundle name of the authentication requester.      |
| options          | {[key: string]: any}  | Yes   | Options for the authentication.     |
| callback         | [AuthenticatorCallback](#authenticatorcallbackdeprecated) | Yes   | Authenticator callback used to return the result.|

### auth<sup>9+</sup>

auth(name: string, authType: string, options: Record<string, Object>, callback: AuthCallback): void

Authenticates an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name             | Type                   | Mandatory  | Description             |
| ---------------- | --------------------- | ---- | --------------- |
| name             | string                | Yes   | Name of the target application account.       |
| authType         | string                | Yes   | Authentication type.     |
| options          | Record<string, Object>  | Yes   | Options for the authentication.     |
| callback         | [AuthCallback](#authcallback9) | Yes   | Authenticator callback used to return the result.|

### authenticate<sup>(deprecated)</sup>

authenticate(name: string, authType: string, callerBundleName: string, options: {[key: string]: any;}, callback: AuthenticatorCallback): void

Authenticates an application account to obtain the OAuth token. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. Use [auth](#auth9-2) instead.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name             | Type                   | Mandatory  | Description             |
| ---------------- | --------------------- | ---- | --------------- |
| name             | string                | Yes   | Name of the target application account.       |
| authType         | string                | Yes   | Authentication type.     |
| callerBundleName | string                | Yes   | Bundle name of the authentication requester.      |
| options          | {[key: string]: any}  | Yes   | Options for the authentication.     |
| callback         | [AuthenticatorCallback](#authenticatorcallbackdeprecated) | Yes   | Authenticator callback used to return the result.|

### verifyCredential<sup>9+</sup>

verifyCredential(name: string, options: VerifyCredentialOptions, callback: AuthCallback): void

Verifies the credential of an application account. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name             | Type                   | Mandatory  | Description             |
| ---------------- | --------------------- | ---- | --------------- |
| name      | string                   | Yes   | Name of the target application account.             |
| options   | [VerifyCredentialOptions](#verifycredentialoptions9)  | Yes   | Options for credential verification.           |
| callback  | [AuthCallback](#authcallback9)    | Yes   | Authenticator callback used to return the result.|

### setProperties<sup>9+</sup>

setProperties(options: SetPropertiesOptions, callback: AuthCallback): void

Sets the authenticator properties. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name             | Type                   | Mandatory  | Description             |
| ---------------- | --------------------- | ---- | --------------- |
| options   | [SetPropertiesOptions](#setpropertiesoptions9)  | Yes   | Authenticator properties to set.           |
| callback  | [AuthCallback](#authcallback9) | Yes   | Authenticator callback used to return the result.|

### checkAccountLabels<sup>9+</sup>

checkAccountLabels(name: string, labels: Array&lt;string&gt;, callback: AuthCallback): void

Checks the account labels. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name             | Type                   | Mandatory  | Description             |
| ---------------- | --------------------- | ---- | --------------- |
| name      | string                | Yes   | Name of the target application account.             |
| labels    | Array&lt;string&gt;          | Yes   | Labels to check.                  |
| callback  | [AuthCallback](#authcallback9) | Yes   | Authenticator callback used to return the result.|

### checkAccountRemovable<sup>9+</sup>

checkAccountRemovable(name: string, callback: AuthCallback): void

Checks whether an application account can be deleted. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Account.AppAccount

**Parameters**

| Name             | Type                   | Mandatory  | Description             |
| ---------------- | --------------------- | ---- | --------------- |
| name      | string                | Yes   | Name of the target application account.             |
| callback  | [AuthCallback](#authcallback9) | Yes   | Authenticator callback used to return the result.|

### getRemoteObject<sup>9+</sup>

getRemoteObject(): rpc.RemoteObject;

Obtains the remote object of an authenticator. This API cannot be overloaded.

**System capability**: SystemCapability.Account.AppAccount

**Return value**

| Type            | Description                                                  |
| ---------------- | ----------------------------------------------------- |
| rpc.RemoteObject | Remote object of the authenticator, which is used for inter-process communication.         |

**Example**

  <!--code_no_check-->
  ```ts
  import { rpc } from '@kit.IPCKit';
  import { Want } from '@kit.AbilityKit';
  
  class MyAuthenticator extends appAccount.Authenticator {
    verifyCredential(name: string,
      options: appAccount.VerifyCredentialOptions, callback: appAccount.AuthCallback) {
        let want: Want = {
          bundleName: 'com.example.accountjsdemo',
          abilityName: 'com.example.accountjsdemo.VerifyAbility',
          parameters: {
            name: name
          }
        };
        callback.onRequestRedirected(want);
    }

    setProperties(options: appAccount.SetPropertiesOptions, callback: appAccount.AuthCallback) {
      let want: Want = {
          bundleName: 'com.example.accountjsdemo',
          abilityName: 'com.example.accountjsdemo.SetPropertiesAbility',
          parameters: {
            options: options
          }
        };
        callback.onRequestRedirected(want);
    }

    checkAccountLabels(name: string, labels: string[], callback: appAccount.AuthCallback) {
      callback.onResult(0);
    }
  
    checkAccountRemovable(name: string, callback: appAccount.AuthCallback) {
      callback.onResult(0);
    }
  }

  export default {
    onConnect(want: Want): rpc.RemoteObject { // serviceAbility lifecycle function, which needs to be placed in serviceAbility.
      let authenticator = new MyAuthenticator();
      return authenticator.getRemoteObject();
    }
  }
  ```
