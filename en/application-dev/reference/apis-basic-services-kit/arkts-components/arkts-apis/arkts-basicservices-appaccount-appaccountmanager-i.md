# AppAccountManager

Defines the application account manager, which is used to manage account information of applications.

**Since:** 7

**System capability:** SystemCapability.Account.AppAccount

## Modules to Import

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## addAccount

```TypeScript
addAccount(name: string, callback: AsyncCallback<void>): void
```

Adds an application account with the given name. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [createAccount](#createaccount)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [createAccount](#createaccount)(name: string, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.addAccount('WangWu', (err: BusinessError) => { 
  console.error(`addAccount err: code is ${err.code}, message is ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.addAccount('LiSi', 'token101', (err: BusinessError) => { 
  console.error(`addAccount err: code is ${err.code}, message is ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.addAccount('LiSi', 'token101').then(()=> { 
  console.info('addAccount Success');
}).catch((err: BusinessError) => {
  console.error(`addAccount err: code is ${err.code}, message is ${err.message}`);
});
```

## addAccount

```TypeScript
addAccount(name: string, extraInfo: string, callback: AsyncCallback<void>): void
```

Adds an application account name and additional information. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [createAccount](#createaccount-1)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [createAccount](#createaccount-1)(name: string, options: CreateAccountOptions, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| extraInfo | string | Yes | Additional information (information that can be converted to the string type). It cannot contain sensitive information, such as the application account password and token. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

See [addAccount](#addaccount)

## addAccount

```TypeScript
addAccount(name: string, extraInfo?: string): Promise<void>
```

Adds an application account name and additional information. This API uses a promise to return the result.

> **NOTE:** 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [createAccount](#createaccount-2)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [createAccount](#createaccount-2)(name: string, options?: CreateAccountOptions)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| extraInfo | string | No | Additional information (information that can be converted to the string type).<br>The additional information cannot be sensitive information (such as the password and token) of the application account. <br>By default, no value is passed, which means no additional information needs to be added for the account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [addAccount](#addaccount)

## addAccountImplicitly

```TypeScript
addAccountImplicitly(
      owner: string,
      authType: string,
      options: { [key: string]: any },
      callback: AuthenticatorCallback
    ): void
```

Adds an application account implicitly based on the specified owner. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [createAccountImplicitly](#createaccountimplicitly)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [createAccountImplicitly](#createaccountimplicitly)(owner: string, callback: AuthCallback)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| options | { [key: string]: any } | Yes | Options for the authentication, which can be set as required. |
| callback | [AuthenticatorCallback](arkts-basicservices-appaccount-authenticatorcallback-i.md) | Yes | Authenticator callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, result: Record<string, Object>): void {
    console.info('resultCode: ' + code);
    console.info('result: ' + JSON.stringify(result));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
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

## auth

```TypeScript
auth(name: string, owner: string, authType: string, callback: AuthCallback): void
```

Authenticates an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Authenticator callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, owner or authType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, authResult?: appAccount.AuthResult): void {
    console.info('resultCode: ' + code);
    console.info('authResult: ' + JSON.stringify(authResult));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
    })
  }

  aboutToAppear(): void {
    try {
      appAccountManager.auth('LiSi', 'com.example.accountjsdemo', 'getSocialData', {
        onResult: this.onResultCallback,
        onRequestRedirected: this.onRequestRedirectedCallback
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`auth exception: code is ${err.code}, message is ${err.message}`);
    }
  }

  build() {}
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, authResult?: appAccount.AuthResult): void {
    console.info('resultCode: ' + code);
    console.info('authResult: ' + JSON.stringify(authResult));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
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
    } catch (e) {
      const err = e as BusinessError;
      console.error(`auth exception: code is ${err.code}, message is ${err.message}`);
    }
  }

  build() {}
}
```

## auth

```TypeScript
auth(
      name: string,
      owner: string,
      authType: string,
      options: Record<string, Object>,
      callback: AuthCallback
    ): void
```

Authenticates an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| options | Record&lt;string, Object&gt; | Yes | Options for the authentication. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Authenticator callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, owner, authType or options. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

See [auth](#auth)

## authenticate

```TypeScript
authenticate(
      name: string,
      owner: string,
      authType: string,
      options: { [key: string]: any },
      callback: AuthenticatorCallback
    ): void
```

Authenticates an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [auth](#auth)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [auth](#auth)(name: string, owner: string, authType: string, callback: AuthCallback)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| options | { [key: string]: any } | Yes | Options for the authentication. |
| callback | [AuthenticatorCallback](arkts-basicservices-appaccount-authenticatorcallback-i.md) | Yes | Authenticator callback used to return the result. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, result: Record<string, Object>): void {
    console.info('resultCode: ' + code);
    console.info('result: ' + JSON.stringify(result));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
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

## checkAccountLabels

```TypeScript
checkAccountLabels(name: string, owner: string, labels: Array<string>, callback: AsyncCallback<boolean>): void
```

Checks whether an application account has specific labels. This API uses an asynchronous callback to return the result. The labels are checked by the authenticator of the target application.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| labels | Array&lt;string&gt; | Yes | Labels to check. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** can be **true** or **false**. The value **true** means the application account has the labels; the value **false** means the opposite. If the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, owner or labels. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let labels = ['student'];
try {
  appAccountManager.checkAccountLabels('zhangsan', 'com.example.accountjsdemo', labels,
    (err: BusinessError, hasAllLabels: boolean) => {
      if (err) {
        console.error(`checkAccountLabels failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('checkAccountLabels successfully, hasAllLabels: ' + hasAllLabels);
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAccountLabels exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let labels = ['student'];
try {
  appAccountManager.checkAccountLabels('zhangsan', 'com.example.accountjsdemo', labels).then((
    hasAllLabels: boolean) => {
    console.info('checkAccountLabels successfully: ' + hasAllLabels);
  }).catch((err: BusinessError) => {
    console.error(`checkAccountLabels failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAccountLabels exception: code is ${err.code}, message is ${err.message}`);
}
```

## checkAccountLabels

```TypeScript
checkAccountLabels(name: string, owner: string, labels: Array<string>): Promise<boolean>
```

Checks whether an application account has specific labels. This API uses a promise to return the result. The labels are checked by the authenticator of the target application.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| labels | Array&lt;string&gt; | Yes | Labels to check. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the application account has the labels; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, owner or labels. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let labels = ['student'];
try {
  appAccountManager.checkAccountLabels('zhangsan', 'com.example.accountjsdemo', labels,
    (err: BusinessError, hasAllLabels: boolean) => {
      if (err) {
        console.error(`checkAccountLabels failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('checkAccountLabels successfully, hasAllLabels: ' + hasAllLabels);
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAccountLabels exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let labels = ['student'];
try {
  appAccountManager.checkAccountLabels('zhangsan', 'com.example.accountjsdemo', labels).then((
    hasAllLabels: boolean) => {
    console.info('checkAccountLabels successfully: ' + hasAllLabels);
  }).catch((err: BusinessError) => {
    console.error(`checkAccountLabels failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAccountLabels exception: code is ${err.code}, message is ${err.message}`);
}
```

## checkAppAccess

```TypeScript
checkAppAccess(name: string, bundleName: string, callback: AsyncCallback<boolean>): void
```

Checks whether the caller can access the account data that belongs to the target application. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the application can access the account data; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or bundleName. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkAppAccess('ZhangSan', 'com.example.accountjsdemo',
    (err: BusinessError, isAccessible: boolean) => {
      if (err) {
        console.error(`checkAppAccess failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('checkAppAccess successfully');
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAppAccess exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkAppAccess('ZhangSan', 'com.example.accountjsdemo').then((isAccessible: boolean) => {
    console.info('checkAppAccess successfully, isAccessible: ' + isAccessible);
  }).catch((err: BusinessError) => {
    console.error(`checkAppAccess failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAppAccess exception: code is ${err.code}, message is ${err.message}`);
}
```

## checkAppAccess

```TypeScript
checkAppAccess(name: string, bundleName: string): Promise<boolean>
```

Checks whether the caller can access the account data that belongs to the target application. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the application can access the account data; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or bundleName. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

See [checkAppAccess](#checkappaccess)

## checkAppAccountSyncEnable

```TypeScript
checkAppAccountSyncEnable(name: string, callback: AsyncCallback<boolean>): void
```

Checks whether data synchronization is enabled for an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [checkDataSyncEnabled](#checkdatasyncenabled)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [checkDataSyncEnabled](#checkdatasyncenabled)(name: string, callback: AsyncCallback&lt;boolean&gt;)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means data synchronization is enabled for the application account; the value **false** means the opposite. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.checkAppAccountSyncEnable('ZhangSan', (err: BusinessError, result: boolean) => { 
  if (err) {
    console.error(`checkAppAccountSyncEnable code: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('checkAppAccountSyncEnable result: ' + result);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.checkAppAccountSyncEnable('ZhangSan').then((data: boolean) => { 
  console.info('checkAppAccountSyncEnable, result: ' + data);
}).catch((err: BusinessError) => {
  console.error(`checkAppAccountSyncEnable err: code is ${err.code}, message is ${err.message}`);
});
```

## checkAppAccountSyncEnable

```TypeScript
checkAppAccountSyncEnable(name: string): Promise<boolean>
```

Checks whether data synchronization is enabled for an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [checkDataSyncEnabled](#checkdatasyncenabled-1) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [checkDataSyncEnabled](#checkdatasyncenabled-1)(name: string)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means data synchronization is enabled for the application account; the value **false** means the opposite. |

**Examples**

See [checkAppAccountSyncEnable](#checkappaccountsyncenable)

## checkAuthTokenVisibility

```TypeScript
checkAuthTokenVisibility(name: string, authType: string, bundleName: string, callback: AsyncCallback<boolean>): void
```

Checks the visibility of an authorization token of the specified authentication type to an application. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** can be **true** (the authorization token is visible to the application) or **false** (the authorization token is not visible to the application). If the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, authType or bundleName. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300107](../errorcode-account.md#12300107-authentication-type-not-found) | AuthType not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo',
    (err: BusinessError, isVisible: boolean) => {
      if (err) {
        console.error(`checkAuthTokenVisibility failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('checkAuthTokenVisibility successfully, isVisible: ' + isVisible);
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAuthTokenVisibility exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo').then((
    isVisible: boolean) => {
    console.info('checkAuthTokenVisibility successfully, isVisible: ' + isVisible);
  }).catch((err: BusinessError) => {
    console.error(`checkAuthTokenVisibility failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkAuthTokenVisibility exception: code is ${err.code}, message is ${err.message}`);
}
```

## checkAuthTokenVisibility

```TypeScript
checkAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise<boolean>
```

Checks the visibility of an authorization token of the specified authentication type to an application. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the authorization token is visible to the application; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, authType or bundleName. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300107](../errorcode-account.md#12300107-authentication-type-not-found) | AuthType not found. |

**Examples**

See [checkAuthTokenVisibility](#checkauthtokenvisibility)

## checkDataSyncEnabled

```TypeScript
checkDataSyncEnabled(name: string, callback: AsyncCallback<boolean>): void
```

Checks whether data synchronization is enabled for an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means data synchronization is enabled for the application account; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkDataSyncEnabled('ZhangSan', (err: BusinessError, isEnabled: boolean) => {
    if (err) {
      console.error(`checkDataSyncEnabled failed, err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkDataSyncEnabled successfully, isEnabled: ' + isEnabled);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.checkDataSyncEnabled('ZhangSan').then((isEnabled: boolean) => {
      console.info('checkDataSyncEnabled successfully, isEnabled: ' + isEnabled);
  }).catch((err: BusinessError) => {
    console.error(`checkDataSyncEnabled failed, err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
}
```

## checkDataSyncEnabled

```TypeScript
checkDataSyncEnabled(name: string): Promise<boolean>
```

Checks whether data synchronization is enabled for an application account. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means data synchronization is enabled for the application account; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

See [checkDataSyncEnabled](#checkdatasyncenabled)

## checkOAuthTokenVisibility

```TypeScript
checkOAuthTokenVisibility(
      name: string,
      authType: string,
      bundleName: string,
      callback: AsyncCallback<boolean>
    ): void
```

Checks the visibility of an authorization token of the specified authentication type to an application. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [checkAuthTokenVisibility](#checkauthtokenvisibility)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [checkAuthTokenVisibility](#checkauthtokenvisibility)(name: string, authType: string, bundleName: string, callback: AsyncCallback&lt;boolean&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** can be **true** (the authorization token is visible to the application) or **false** (the authorization token is not visible to the application). If the operation fails, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.checkOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo',
  (err: BusinessError, data: boolean) => {
    if (err) {
      console.error(`checkOAuthTokenVisibility err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkOAuthTokenVisibility isVisible: ' + data);
    }
  });
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.checkOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo').then((
  data: boolean) => {
  console.info('checkOAuthTokenVisibility isVisible: ' + data);
}).catch((err: BusinessError) => {
  console.error(`checkOAuthTokenVisibility err: code is ${err.code}, message is ${err.message}`);
});
```

## checkOAuthTokenVisibility

```TypeScript
checkOAuthTokenVisibility(name: string, authType: string, bundleName: string): Promise<boolean>
```

Checks the visibility of an authorization token of the specified authentication type to an application. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [checkAuthTokenVisibility](#checkauthtokenvisibility-1)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [checkAuthTokenVisibility](#checkauthtokenvisibility-1)(name: string, authType: string, bundleName: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the authorization token is visible to the application; the value **false** means the opposite. |

**Examples**

See [checkOAuthTokenVisibility](#checkoauthtokenvisibility)

## createAccount

```TypeScript
createAccount(name: string, callback: AsyncCallback<void>): void
```

Creates an application account with the given name. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name. |
| [12300004](../errorcode-account.md#12300004-account-already-exists) | Account already exists. |
| [12300007](../errorcode-account.md#12300007-account-count-reached-the-limit) | The number of accounts reaches the upper limit. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.createAccount('WangWu', (err: BusinessError) => { 
    if (err) {
      console.error(`createAccount code: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('createAccount successful.');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`createAccount err: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.CreateAccountOptions = {
  customData: {
    age: '10'
  }
}
try {
  appAccountManager.createAccount('LiSi', options, (err: BusinessError) => {
    if (err) {
      console.error(`createAccount failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('createAccount successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`createAccount exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.CreateAccountOptions = {
  customData: {
    age: '10'
  }
}
try {
  appAccountManager.createAccount('LiSi', options).then(() => {
    console.info('createAccount successfully');
  }).catch((err: BusinessError) => {
    console.error(`createAccount failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`createAccount exception: code is ${err.code}, message is ${err.message}`);
}
```

## createAccount

```TypeScript
createAccount(name: string, options: CreateAccountOptions, callback: AsyncCallback<void>): void
```

Creates an application account with custom data. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| options | [CreateAccountOptions](arkts-basicservices-appaccount-createaccountoptions-i.md) | Yes | Options for creating the application account. You can customize data based on service requirements, but do not add sensitive data (such as passwords and tokens). |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or options. |
| [12300004](../errorcode-account.md#12300004-account-already-exists) | Account already exists. |
| [12300007](../errorcode-account.md#12300007-account-count-reached-the-limit) | The number of accounts reaches the upper limit. |

**Examples**

See [createAccount](#createaccount)

## createAccount

```TypeScript
createAccount(name: string, options?: CreateAccountOptions): Promise<void>
```

Creates an application account with custom data. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| options | [CreateAccountOptions](arkts-basicservices-appaccount-createaccountoptions-i.md) | No | Options for creating the application account. You can customize data based on service requirements, but do not add sensitive data (such as passwords and tokens).<br>By default, no value is passed in, which means no additional information needs to be added for the account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or options. |
| [12300004](../errorcode-account.md#12300004-account-already-exists) | Account already exists. |
| [12300007](../errorcode-account.md#12300007-account-count-reached-the-limit) | The number of accounts reaches the upper limit. |

**Examples**

See [createAccount](#createaccount)

## createAccountImplicitly

```TypeScript
createAccountImplicitly(owner: string, callback: AuthCallback): void
```

Creates an application account automatically by the authenticator based on the specified owner. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Authenticator callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid owner. |
| [12300007](../errorcode-account.md#12300007-account-count-reached-the-limit) | The number of accounts reaches the upper limit. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, result?: appAccount.AuthResult): void {
    console.info('resultCode: ' + code);
    console.info('result: ' + JSON.stringify(result));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
    })
  }

  aboutToAppear(): void {
    try {
      appAccountManager.createAccountImplicitly('com.example.accountjsdemo', {
        onResult: this.onResultCallback,
        onRequestRedirected: this.onRequestRedirectedCallback
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`createAccountImplicitly exception: code is ${err.code}, message is ${err.message}`);
    }
  }
  build() {}
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  context = this.getUIContext().getHostContext() as common.UIAbilityContext; // UIAbilityContext

  onResultCallback(code: number, result?: appAccount.AuthResult): void {
    console.info('resultCode: ' + code);
    console.info('result: ' + JSON.stringify(result));
  }

  onRequestRedirectedCallback(request: Want): void {
    let wantInfo: Want = {
      deviceId: '',
      bundleName: 'com.example.accountjsdemo',
      action: 'ohos.want.action.viewData',
      entities: ['entity.system.default'],
    }
    this.context.startAbility(wantInfo).then(() => {
      console.info('startAbility successfully');
    }).catch((err: BusinessError) => {
      console.error(`startAbility err: code is ${err.code}, message is ${err.message}`);
    })
  }

  aboutToAppear(): void {
    let options: appAccount.CreateAccountImplicitlyOptions = {
      authType: 'getSocialData',
      requiredLabels: ['student']
    };
    try {
      appAccountManager.createAccountImplicitly('com.example.accountjsdemo', options, {
        onResult: this.onResultCallback,
        onRequestRedirected: this.onRequestRedirectedCallback
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`createAccountImplicitly exception: code is ${err.code}, message is ${err.message}`);
    }
  }
  build() {}
}
```

## createAccountImplicitly

```TypeScript
createAccountImplicitly(owner: string, options: CreateAccountImplicitlyOptions, callback: AuthCallback): void
```

Creates an application account automatically by the authenticator based on the specified account owner and options. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| options | [CreateAccountImplicitlyOptions](arkts-basicservices-appaccount-createaccountimplicitlyoptions-i.md) | Yes | Options for implicitly creating the account. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Authenticator callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid owner or options. |
| [12300007](../errorcode-account.md#12300007-account-count-reached-the-limit) | The number of accounts reaches the upper limit. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

See [createAccountImplicitly](#createaccountimplicitly)

## deleteAccount

```TypeScript
deleteAccount(name: string, callback: AsyncCallback<void>): void
```

Deletes an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [removeAccount](#removeaccount)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [removeAccount](#removeaccount)(name: string, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.deleteAccount('ZhaoLiu', (err: BusinessError) => { 
  console.error(`deleteAccount err: code is ${err.code}, message is ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.deleteAccount('ZhaoLiu').then(() => { 
  console.info('deleteAccount Success');
}).catch((err: BusinessError) => {
  console.error(`deleteAccount err: code is ${err.code}, message is ${err.message}`);
});
```

## deleteAccount

```TypeScript
deleteAccount(name: string): Promise<void>
```

Deletes an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [removeAccount](#removeaccount-1)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [removeAccount](#removeaccount-1)(name: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [deleteAccount](#deleteaccount)

## deleteAuthToken

```TypeScript
deleteAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback<void>): void
```

Deletes the authorization token of the specified authentication type for an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| token | string | Yes | Authorization token. The value contains a maximum of 1024 characters. If the token does not exist, no operation is performed. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, owner, authType or token. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300107](../errorcode-account.md#12300107-authentication-type-not-found) | AuthType not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.deleteAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx',
    (err: BusinessError) => {
      if (err) {
        console.error(`deleteAuthToken failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('deleteAuthToken successfully');
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`deleteAuthToken exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.deleteAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx').then(() => {
    console.info('deleteAuthToken successfully');
  }).catch((err: BusinessError) => {
    console.error(`deleteAuthToken failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`deleteAuthToken exception: code is ${err.code}, message is ${err.message}`);
}
```

## deleteAuthToken

```TypeScript
deleteAuthToken(name: string, owner: string, authType: string, token: string): Promise<void>
```

Deletes the authorization token of the specified authentication type for an application account. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| token | string | Yes | Authorization token. The value contains a maximum of 1024 characters. If the token does not exist, no operation is performed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, owner, authType or token. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300107](../errorcode-account.md#12300107-authentication-type-not-found) | AuthType not found. |

**Examples**

See [deleteAuthToken](#deleteauthtoken)

## deleteCredential

```TypeScript
deleteCredential(name: string, credentialType: string, callback: AsyncCallback<void>): void
```

Deletes the credential for the specified type of an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| credentialType | string | Yes | Credential type. The value is user-defined and contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or credentialType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300102](../errorcode-account.md#12300102-credential-not-found) | Credential not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.deleteCredential('zhangsan', 'PIN_SIX', (err: BusinessError) => {
    if (err) {
      console.error(`deleteCredential failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('deleteCredential successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`deleteCredential exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.deleteCredential('zhangsan', 'PIN_SIX').then(() => {
    console.info('deleteCredential successfully');
  }).catch((err: BusinessError) => {
    console.error(`deleteCredential failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`deleteCredential exception: code is ${err.code}, message is ${err.message}`);
}
```

## deleteCredential

```TypeScript
deleteCredential(name: string, credentialType: string): Promise<void>
```

Deletes the credential for the specified type of an application account. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| credentialType | string | Yes | Credential type. The value is user-defined and contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or credentialType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300102](../errorcode-account.md#12300102-credential-not-found) | Credential not found. |

**Examples**

See [deleteCredential](#deletecredential)

## deleteOAuthToken

```TypeScript
deleteOAuthToken(name: string, owner: string, authType: string, token: string, callback: AsyncCallback<void>): void
```

Deletes the authorization token of the specified authentication type for an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [deleteAuthToken](#deleteauthtoken)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deleteAuthToken](#deleteauthtoken)(name: string, owner: string, authType: string, token: string, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| token | string | Yes | Authorization token. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.deleteOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx',
  (err: BusinessError) => {
    if (err) {
      console.error(`deleteOAuthToken err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('deleteOAuthToken successful.');
    }
  });
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.deleteOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData', 'xxxxx').then(() => {
  console.info('deleteOAuthToken successfully');
}).catch((err: BusinessError) => {
  console.error(`deleteOAuthToken err: code is ${err.code}, message is ${err.message}`);
});
```

## deleteOAuthToken

```TypeScript
deleteOAuthToken(name: string, owner: string, authType: string, token: string): Promise<void>
```

Deletes the authorization token of the specified authentication type for an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [deleteAuthToken](#deleteauthtoken-1)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deleteAuthToken](#deleteauthtoken-1)(name: string, owner: string, authType: string, token: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| token | string | Yes | Authorization token. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [deleteOAuthToken](#deleteoauthtoken)

## disableAppAccess

```TypeScript
disableAppAccess(name: string, bundleName: string, callback: AsyncCallback<void>): void
```

Disables access to the third-party application with the specified package name using the specified third-party application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setAppAccess](#setappaccess)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setAppAccess](#setappaccess)(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If access to the third-party application with the specified package name using the specified third-party application account is disabled successfully, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.disableAppAccess('ZhangSan', 'com.example.accountjsdemo', (err: BusinessError) => { 
  console.error(`disableAppAccess err: code is ${err.code}, message is ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.disableAppAccess('ZhangSan', 'com.example.accountjsdemo').then(() => { 
  console.info('disableAppAccess Success');
}).catch((err: BusinessError) => {
  console.error(`disableAppAccess err: code is ${err.code}, message is ${err.message}`);
});
```

## disableAppAccess

```TypeScript
disableAppAccess(name: string, bundleName: string): Promise<void>
```

Disables an application account from accessing an application. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setAppAccess](#setappaccess-1)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setAppAccess](#setappaccess-1)(name: string, bundleName: string, isAccessible: boolean)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the target application account. The value contains a maximum of 512 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [disableAppAccess](#disableappaccess)

## enableAppAccess

```TypeScript
enableAppAccess(name: string, bundleName: string, callback: AsyncCallback<void>): void
```

Enables an application to access an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setAppAccess](#setappaccess)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setAppAccess](#setappaccess)(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.enableAppAccess('ZhangSan', 'com.example.accountjsdemo', (err: BusinessError) => {
  if (err) {
    console.error(`enableAppAccess err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('enableAppAccess successful.');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.enableAppAccess('ZhangSan', 'com.example.accountjsdemo').then(() => { 
  console.info('enableAppAccess Success');
}).catch((err: BusinessError) => {
  console.error(`enableAppAccess err: code is ${err.code}, message is ${err.message}`);
});
```

## enableAppAccess

```TypeScript
enableAppAccess(name: string, bundleName: string): Promise<void>
```

Enables an application to access an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setAppAccess](#setappaccess-1)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setAppAccess](#setappaccess-1)(name: string, bundleName: string, isAccessible: boolean)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [enableAppAccess](#enableappaccess)

## getAccountCredential

```TypeScript
getAccountCredential(name: string, credentialType: string, callback: AsyncCallback<string>): void
```

Obtains the credential of an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getCredential](#getcredential)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getCredential](#getcredential)(name: string, credentialType: string, callback: AsyncCallback&lt;string&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| credentialType | string | Yes | Credential type. The value is user-defined and contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the credential obtained. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAccountCredential('ZhangSan', 'credentialType001', (err: BusinessError, result: string) => { 
  if (err) {
    console.error(`getAccountCredential err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getAccountCredential result: ' + result);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAccountCredential('ZhangSan', 'credentialType001').then((data: string) => { 
  console.info('getAccountCredential, result: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getAccountCredential err: code is ${err.code}, message is ${err.message}`);
});
```

## getAccountCredential

```TypeScript
getAccountCredential(name: string, credentialType: string): Promise<string>
```

Obtains the credential of an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getCredential](#getcredential-1)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getCredential](#getcredential-1)(name: string, credentialType: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| credentialType | string | Yes | Credential type. The value is user-defined and contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the credential obtained. |

**Examples**

See [getAccountCredential](#getaccountcredential)

## getAccountExtraInfo

```TypeScript
getAccountExtraInfo(name: string, callback: AsyncCallback<string>): void
```

Obtains additional information of an application account. Additional information refers to other information that can be converted to the string type. It cannot contain sensitive information, such as the application account password and token. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getCustomData](#getcustomdata)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getCustomData](#getcustomdata)(name: string, key: string, callback: AsyncCallback&lt;string&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the additional information obtained. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAccountExtraInfo('ZhangSan', (err: BusinessError, result: string) => { 
  if (err) {
    console.error(`getAccountExtraInfo err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getAccountExtraInfo result: ' + result);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAccountExtraInfo('ZhangSan').then((data: string) => { 
  console.info('getAccountExtraInfo, result: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getAccountExtraInfo err: code is ${err.code}, message is ${err.message}`);
});
```

## getAccountExtraInfo

```TypeScript
getAccountExtraInfo(name: string): Promise<string>
```

Obtains additional information of an application account. Additional information refers to other information that can be converted to the string type. It cannot contain sensitive information, such as the application account password and token. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getCustomData](#getcustomdata-1) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getCustomData](#getcustomdata-1)(name: string, key: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the additional information of the application account. |

**Examples**

See [getAccountExtraInfo](#getaccountextrainfo)

## getAccountsByOwner

```TypeScript
getAccountsByOwner(owner: string, callback: AsyncCallback<Array<AppAccountInfo>>): void
```

Obtains the application accounts that can be accessed by the invoker based on the application account owner. This API uses an asynchronous callback to return the result. This method applies to the following accounts: <br> Accounts of this application. <br> Accounts of third-party applications. To obtain such information, <br> your application must have gained authorization from the third-party applications or <br> have gained the ohos.permission.GET_ALL_APP_ACCOUNTS permission.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is null and **data** is the application account information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid owner. |
| [12400001](../errorcode-account.md#12400001-application-not-found) | Application not found.<br>**Applicable version:** 9 - 13 |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAccountsByOwner('com.example.accountjsdemo2',
    (err: BusinessError, data: appAccount.AppAccountInfo[]) => {
      if (err) {
        console.error(`getAccountsByOwner failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getAccountsByOwner successfully, data:' + JSON.stringify(data));
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAccountsByOwner exception:code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAccountsByOwner('com.example.accountjsdemo2').then((
    data: appAccount.AppAccountInfo[]) => {
    console.info('getAccountsByOwner successfully, data: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`getAccountsByOwner failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAccountsByOwner exception: code is ${err.code}, message is ${err.message}`);
}
```

## getAccountsByOwner

```TypeScript
getAccountsByOwner(owner: string): Promise<Array<AppAccountInfo>>
```

Obtains the application accounts that can be accessed by the invoker based on the application account owner. This API uses a promise to return the result. This method applies to the following accounts: <br> Accounts of this application. <br> Accounts of third-party applications. To obtain such information, <br> your application must have gained authorization from the third-party applications or <br> have gained the ohos.permission.GET_ALL_APP_ACCOUNTS permission.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Promise used to return the application account information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid owner. |
| [12400001](../errorcode-account.md#12400001-application-not-found) | Application not found.<br>**Applicable version:** 9 - 13 |

**Examples**

See [getAccountsByOwner](#getaccountsbyowner)

## getAllAccessibleAccounts

```TypeScript
getAllAccessibleAccounts(callback: AsyncCallback<Array<AppAccountInfo>>): void
```

Obtains information about all accessible application accounts. This API uses an asynchronous callback to return the result. This method applies to the following accounts: <br> Accounts of this application. <br> Accounts of third-party applications. To obtain such information, <br> your application must have gained authorization from the third-party applications.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getAllAccounts](#getallaccounts)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAllAccounts](#getallaccounts)(callback: AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt;)

**Required permissions:** ohos.permission.GET_ALL_APP_ACCOUNTS

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of accessible application accounts. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAllAccessibleAccounts((err: BusinessError, data: appAccount.AppAccountInfo[])=>{
  if (err) {
    console.error(`getAllAccessibleAccounts err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getAllAccessibleAccounts data: ' + JSON.stringify(data));
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAllAccessibleAccounts().then((data: appAccount.AppAccountInfo[]) => { 
  console.info('getAllAccessibleAccounts: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getAllAccessibleAccounts err: code is ${err.code}, message is ${err.message}`);
});
```

## getAllAccessibleAccounts

```TypeScript
getAllAccessibleAccounts(): Promise<Array<AppAccountInfo>>
```

Obtains information about all accessible application accounts. This API uses a promise to return the result. This method applies to the following accounts: <br> Accounts of this application. <br> Accounts of third-party applications. To obtain such information, <br> your application must have gained authorization from the third-party applications.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getAllAccounts](#getallaccounts) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAllAccounts](#getallaccounts)()

**Required permissions:** ohos.permission.GET_ALL_APP_ACCOUNTS

**System capability:** SystemCapability.Account.AppAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Promise used to return information about all accessible accounts. |

**Examples**

See [getAllAccessibleAccounts](#getallaccessibleaccounts)

## getAllAccounts

```TypeScript
getAllAccounts(callback: AsyncCallback<Array<AppAccountInfo>>): void
```

Obtains information about all accessible application accounts. This API uses an asynchronous callback to return the result. This method applies to the following accounts: <br> Accounts of this application. <br> Accounts of third-party applications. To obtain such information, <br> your application must have gained authorization from the third-party applications or <br> have gained the ohos.permission.GET_ALL_APP_ACCOUNTS permission.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of accessible application accounts. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAllAccounts((err: BusinessError, data: appAccount.AppAccountInfo[]) => {
    if (err) {
      console.error(`getAllAccounts failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAllAccounts successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAllAccounts exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAllAccounts().then((data: appAccount.AppAccountInfo[]) => {
    console.info('getAllAccounts successfully');
  }).catch((err: BusinessError) => {
    console.error(`getAllAccounts failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAllAccounts exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const selfBundle = 'com.example.actsgetallaaccounts';
appAccountManager.getAllAccounts(selfBundle, (err: BusinessError, data: appAccount.AppAccountInfo[])=>{
  if (err) {
    console.error(`getAllAccounts err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getAllAccounts data:' + JSON.stringify(data));
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const selfBundle = 'com.example.actsgetallaaccounts';
appAccountManager.getAllAccounts(selfBundle).then((data: appAccount.AppAccountInfo[]) => { 
  console.info('getAllAccounts: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getAllAccounts err: code is ${err.code}, message is ${err.message}`);
});
```

## getAllAccounts

```TypeScript
getAllAccounts(): Promise<Array<AppAccountInfo>>
```

Obtains information about all accessible application accounts. This API uses a promise to return the result. This method applies to the following accounts: <br> Accounts of this application. <br> Accounts of third-party applications. To obtain such information, <br> your application must have gained authorization from the third-party applications or <br> have gained the ohos.permission.GET_ALL_APP_ACCOUNTS permission.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Promise used to return information about all accessible accounts. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |

**Examples**

See [getAllAccounts](#getallaccounts)

## getAllAccounts

```TypeScript
getAllAccounts(owner: string, callback: AsyncCallback<Array<AppAccountInfo>>): void
```

Obtains the application accounts that can be accessed by the invoker based on the application account owner. This API uses an asynchronous callback to return the result. This method applies to the following accounts: <br> Accounts of this application. <br> Accounts of third-party applications. To obtain such information, <br> your application must have gained authorization from the third-party applications.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getAccountsByOwner](#getaccountsbyowner)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAccountsByOwner](#getaccountsbyowner)(owner: string, callback: AsyncCallback&lt;Array&lt;AppAccountInfo&gt;&gt;)

**Required permissions:** ohos.permission.GET_ALL_APP_ACCOUNTS

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the application accounts are obtained successfully, **err** is **null** and **data** is a list of application accounts obtained. Otherwise, **err** is an error object. |

**Examples**

See [getAllAccounts](#getallaccounts)

## getAllAccounts

```TypeScript
getAllAccounts(owner: string): Promise<Array<AppAccountInfo>>
```

Obtains the application accounts that can be accessed by the invoker based on the application account owner. This API uses a promise to return the result. This method applies to the following accounts: <br> Accounts of this application. <br> Accounts of third-party applications. To obtain such information, <br> your application must have gained authorization from the third-party applications.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getAccountsByOwner](#getaccountsbyowner-1) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAccountsByOwner](#getaccountsbyowner-1)(owner: string)

**Required permissions:** ohos.permission.GET_ALL_APP_ACCOUNTS

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Promise used to return the application accounts that can be accessed by the invoker. |

**Examples**

See [getAllAccounts](#getallaccounts)

## getAllAuthTokens

```TypeScript
getAllAuthTokens(name: string, owner: string, callback: AsyncCallback<Array<AuthTokenInfo>>): void
```

Obtains all tokens visible to the invoker for an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AuthTokenInfo](arkts-basicservices-appaccount-authtokeninfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of all tokens visible to the invoker. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or owner. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAllAuthTokens('LiSi', 'com.example.accountjsdemo',
    (err: BusinessError, tokenArr: appAccount.AuthTokenInfo[]) => {
      if (err) {
        console.error(`getAllAuthTokens failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getAllAuthTokens successfully, tokenArr: ' + tokenArr);
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAllAuthTokens exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAllAuthTokens('LiSi', 'com.example.accountjsdemo').then((
    tokenArr: appAccount.AuthTokenInfo[]) => {
    console.info('getAllAuthTokens successfully, tokenArr: ' + JSON.stringify(tokenArr));
  }).catch((err: BusinessError) => {
    console.error(`getAllAuthTokens failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAllAuthTokens exception: code is ${err.code}, message is ${err.message}`);
}
```

## getAllAuthTokens

```TypeScript
getAllAuthTokens(name: string, owner: string): Promise<Array<AuthTokenInfo>>
```

Obtains all tokens visible to the invoker for an application account. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AuthTokenInfo](arkts-basicservices-appaccount-authtokeninfo-i.md)&gt;&gt; | Promise used to return the tokens obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or owner. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

See [getAllAuthTokens](#getallauthtokens)

## getAllOAuthTokens

```TypeScript
getAllOAuthTokens(name: string, owner: string, callback: AsyncCallback<Array<OAuthTokenInfo>>): void
```

Obtains all tokens visible to the invoker for an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getAllAuthTokens](#getallauthtokens)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAllAuthTokens](#getallauthtokens)(name: string, owner: string, callback: AsyncCallback&lt;Array&lt;AuthTokenInfo&gt;&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[OAuthTokenInfo](arkts-basicservices-appaccount-oauthtokeninfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of all tokens visible to the invoker. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAllOAuthTokens('LiSi', 'com.example.accountjsdemo',
  (err: BusinessError, data: appAccount.OAuthTokenInfo[]) => {
    if (err) {
      console.error(`getAllOAuthTokens err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAllOAuthTokens data: ' + JSON.stringify(data));
    }
  });
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAllOAuthTokens('LiSi', 'com.example.accountjsdemo').then((
  data: appAccount.OAuthTokenInfo[]) => {
  console.info('getAllOAuthTokens data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`getAllOAuthTokens err: code is ${err.code}, message is ${err.message}`);
});
```

## getAllOAuthTokens

```TypeScript
getAllOAuthTokens(name: string, owner: string): Promise<Array<OAuthTokenInfo>>
```

Obtains all tokens visible to the invoker for an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getAllAuthTokens](#getallauthtokens-1) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAllAuthTokens](#getallauthtokens-1)(name: string, owner: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[OAuthTokenInfo](arkts-basicservices-appaccount-oauthtokeninfo-i.md)&gt;&gt; | Promise used to return the tokens obtained. |

**Examples**

See [getAllOAuthTokens](#getalloauthtokens)

## getAssociatedData

```TypeScript
getAssociatedData(name: string, key: string, callback: AsyncCallback<string>): void
```

Obtains the associated data of an application account based on the specified key. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getCustomData](#getcustomdata)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getCustomData](#getcustomdata)(name: string, key: string, callback: AsyncCallback&lt;string&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| key | string | Yes | Key of the associated data. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the data obtained. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAssociatedData('ZhangSan', 'k001', (err: BusinessError, result: string) => { 
  if (err) {
    console.error(`getAssociatedData err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getAssociatedData result: ' + result);
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAssociatedData('ZhangSan', 'k001').then((data: string) => { 
  console.info('getAssociatedData: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getAssociatedData err: code is ${err.code}, message is ${err.message}`);
});
```

## getAssociatedData

```TypeScript
getAssociatedData(name: string, key: string): Promise<string>
```

Obtains data to be associated with an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getCustomData](#getcustomdata-1) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getCustomData](#getcustomdata-1)(name: string, key: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| key | string | Yes | Key of the associated data. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the data obtained. |

**Examples**

See [getAssociatedData](#getassociateddata)

## getAuthCallback

```TypeScript
getAuthCallback(sessionId: string, callback: AsyncCallback<AuthCallback>): void
```

Obtains the authenticator callback for an authentication session. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | ID of the authentication session. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[AuthCallback](arkts-basicservices-appaccount-authcallback-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authenticator callback object obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid sessionId. |
| [12300108](../errorcode-account.md#12300108-authentication-session-not-found) | Session not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, param: AbilityConstant.LaunchParam) { // Ability lifecycle function.
    let sessionId: string = want.parameters![appAccount.Constants.KEY_SESSION_ID] as string;
    try {
      appAccountManager.getAuthCallback(sessionId, (err: BusinessError, callback: appAccount.AuthCallback) => {
        if (err != null) {
          console.error(`getAuthCallback err: code is ${err.code}, message is ${err.message}`);
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
    } catch (e) {
      const err = e as BusinessError;
      console.error(`getAuthCallback exception: code is ${err.code}, message is ${err.message}`);
    }
  }
}
```

```TypeScript
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
        console.error(`getAuthCallback err: code is ${err.code}, message is ${err.message}`);
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`getAuthCallback exception: code is ${err.code}, message is ${err.message}`);
    }
  }
}
```

## getAuthCallback

```TypeScript
getAuthCallback(sessionId: string): Promise<AuthCallback>
```

Obtains the authenticator callback for an authentication session. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | ID of the authentication session. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AuthCallback](arkts-basicservices-appaccount-authcallback-i.md)&gt; | Promise used to return the authenticator callback obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid sessionId. |
| [12300108](../errorcode-account.md#12300108-authentication-session-not-found) | Session not found. |

**Examples**

See [getAuthCallback](#getauthcallback)

## getAuthenticatorCallback

```TypeScript
getAuthenticatorCallback(sessionId: string, callback: AsyncCallback<AuthenticatorCallback>): void
```

Obtains the authenticator callback for an authentication session. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getAuthCallback](#getauthcallback)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAuthCallback](#getauthcallback)(sessionId: string, callback: AsyncCallback&lt;AuthCallback&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | ID of the authentication session. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[AuthenticatorCallback](arkts-basicservices-appaccount-authenticatorcallback-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authenticator callback obtained. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, param: AbilityConstant.LaunchParam) { // Ability lifecycle function.
    let sessionId: string = want.parameters![appAccount.Constants.KEY_SESSION_ID] as string;
    appAccountManager.getAuthenticatorCallback(sessionId,
        (err: BusinessError, callback: appAccount.AuthenticatorCallback) => {
        if (err.code != appAccount.ResultCode.SUCCESS) {
            console.error(`getAuthenticatorCallback err: code is ${err.code}, message is ${err.message}`);
            return;
        }
        callback.onResult(appAccount.ResultCode.SUCCESS, {
          name: 'LiSi',
          owner: 'com.example.accountjsdemo',
          authType: 'getSocialData',
          token: 'xxxxxx'
        });
      });
  }
}
```

```TypeScript
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
        token: 'xxxxxx'
      });
    }).catch((err: BusinessError) => {
      console.error(`getAuthenticatorCallback err: code is ${err.code}, message is ${err.message}`);
    });
  }
}
```

## getAuthenticatorCallback

```TypeScript
getAuthenticatorCallback(sessionId: string): Promise<AuthenticatorCallback>
```

Obtains the authenticator callback for an authentication session. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getAuthCallback](#getauthcallback-1) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAuthCallback](#getauthcallback-1)(sessionId: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | ID of the authentication session. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AuthenticatorCallback](arkts-basicservices-appaccount-authenticatorcallback-i.md)&gt; | Promise used to return the authenticator callback obtained. |

**Examples**

See [getAuthenticatorCallback](#getauthenticatorcallback)

## getAuthenticatorInfo

```TypeScript
getAuthenticatorInfo(owner: string, callback: AsyncCallback<AuthenticatorInfo>): void
```

Obtains the authenticator information of an application. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [queryAuthenticatorInfo](#queryauthenticatorinfo)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [queryAuthenticatorInfo](#queryauthenticatorinfo)(owner: string, callback: AsyncCallback&lt;AuthenticatorInfo&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[AuthenticatorInfo](arkts-basicservices-appaccount-authenticatorinfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authenticator information obtained. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAuthenticatorInfo('com.example.accountjsdemo',
  (err: BusinessError, data: appAccount.AuthenticatorInfo) => {
    if (err) {
      console.error(`getAuthenticatorInfo err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAuthenticatorInfo data: ' + JSON.stringify(data));
    }
  });
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getAuthenticatorInfo('com.example.accountjsdemo').then((
  data: appAccount.AuthenticatorInfo) => { 
  console.info('getAuthenticatorInfo: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`getAuthenticatorInfo err: code is ${err.code}, message is ${err.message}`);
});
```

## getAuthenticatorInfo

```TypeScript
getAuthenticatorInfo(owner: string): Promise<AuthenticatorInfo>
```

Obtains the authenticator information of an application. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [queryAuthenticatorInfo](#queryauthenticatorinfo-1) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [queryAuthenticatorInfo](#queryauthenticatorinfo-1)(owner: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AuthenticatorInfo](arkts-basicservices-appaccount-authenticatorinfo-i.md)&gt; | Promise used to return the authenticator information obtained. |

**Examples**

See [getAuthenticatorInfo](#getauthenticatorinfo)

## getAuthList

```TypeScript
getAuthList(name: string, authType: string, callback: AsyncCallback<Array<string>>): void
```

Obtains the authorization list of the specified authentication type for an application account. The authorization list contains all authorized bundles. The token authorization list is set by [setAuthTokenVisibility](#setauthtokenvisibility). This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of authorized bundles obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or authType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300107](../errorcode-account.md#12300107-authentication-type-not-found) | AuthType not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAuthList('LiSi', 'getSocialData', (err: BusinessError, authList: string[]) => {
    if (err) {
      console.error(`getAuthList failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAuthList successfully, authList: ' + authList);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthList exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAuthList('LiSi', 'getSocialData').then((authList: string[]) => {
    console.info('getAuthList successfully, authList: ' + authList);
  }).catch((err: BusinessError) => {
    console.error(`getAuthList failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthList exception: code is ${err.code}, message is ${err.message}`);
}
```

## getAuthList

```TypeScript
getAuthList(name: string, authType: string): Promise<Array<string>>
```

Obtains the authorization list of the specified authentication type for an application account. The authorization list contains all authorized bundles. The token authorization list is set by [setAuthTokenVisibility](#setauthtokenvisibility). This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return a list of authorized bundles. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or authType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300107](../errorcode-account.md#12300107-authentication-type-not-found) | AuthType not found. |

**Examples**

See [getAuthList](#getauthlist)

## getAuthToken

```TypeScript
getAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback<string>): void
```

Obtains the authorization token of the specified authentication type for an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authorization token value obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, owner or authType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300107](../errorcode-account.md#12300107-authentication-type-not-found) | AuthType not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData',
    (err: BusinessError, token: string) => {
      if (err) {
        console.error(`getAuthToken failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getAuthToken successfully, token: ' + token);
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthToken exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData').then((token: string) => {
    console.info('getAuthToken successfully, token: ' + token);
  }).catch((err: BusinessError) => {
    console.error(`getAuthToken failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthToken exception: code is ${err.code}, message is ${err.message}`);
}
```

## getAuthToken

```TypeScript
getAuthToken(name: string, owner: string, authType: string): Promise<string>
```

Obtains the authorization token of the specified authentication type for an application account. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the authorization token obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, owner or authType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300107](../errorcode-account.md#12300107-authentication-type-not-found) | AuthType not found. |

**Examples**

See [getAuthToken](#getauthtoken)

## getCredential

```TypeScript
getCredential(name: string, credentialType: string, callback: AsyncCallback<string>): void
```

Obtains the credential of an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| credentialType | string | Yes | Credential type. The value is user-defined and contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the credential obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or credentialType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300102](../errorcode-account.md#12300102-credential-not-found) | Credential not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getCredential('ZhangSan', 'PIN_SIX', (err: BusinessError, result: string) => {
    if (err) {
      console.error(`getCredential failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getCredential successfully, result: ' + result);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCredential err: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getCredential('ZhangSan', 'PIN_SIX').then((credential: string) => {
    console.info('getCredential successfully, credential: ' + credential);
  }).catch((err: BusinessError) => {
    console.error(`getCredential failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCredential exception: code is ${err.code}, message is ${err.message}`);
}
```

## getCredential

```TypeScript
getCredential(name: string, credentialType: string): Promise<string>
```

Obtains the credential of an application account. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| credentialType | string | Yes | Credential type. The value is user-defined and contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the credential obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or credentialType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300102](../errorcode-account.md#12300102-credential-not-found) | Credential not found. |

**Examples**

See [getCredential](#getcredential)

## getCustomData

```TypeScript
getCustomData(name: string, key: string, callback: AsyncCallback<string>): void
```

Obtains the custom data of an application account based on the specified key. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| key | string | Yes | Key of the custom data. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the custom data value obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or key. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12400002](../errorcode-account.md#12400002-custom-data-not-found) | Custom data not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getCustomData('ZhangSan', 'age', (err: BusinessError, data: string) => {
    if (err) {
      console.error('getCustomData failed, error: ' + err);
    } else {
      console.info('getCustomData successfully, data: ' + data);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCustomData exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.getCustomData('ZhangSan', 'age').then((data: string) => {
    console.info('getCustomData successfully, data: ' + data);
  }).catch((err: BusinessError) => {
    console.error(`getCustomData failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCustomData exception: code is ${err.code}, message is ${err.message}`);
}
```

## getCustomData

```TypeScript
getCustomData(name: string, key: string): Promise<string>
```

Obtains the custom data of an application account based on the specified key. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| key | string | Yes | Key of the custom data. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the custom data value obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or key. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12400002](../errorcode-account.md#12400002-custom-data-not-found) | Custom data not found. |

**Examples**

See [getCustomData](#getcustomdata)

## getCustomDataSync

```TypeScript
getCustomDataSync(name: string, key: string): string
```

Obtains the custom data of an application account based on the specified key. The API returns the result synchronously.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| key | string | Yes | Key of the custom data. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Value of the custom data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or key. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12400002](../errorcode-account.md#12400002-custom-data-not-found) | Custom data not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let value = appAccountManager.getCustomDataSync('ZhangSan', 'age');
  console.info('getCustomDataSync successfully, value: ' + value);
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCustomDataSync failed, code is ${err.code}, message is ${err.message}`);
}
```

## getOAuthList

```TypeScript
getOAuthList(name: string, authType: string, callback: AsyncCallback<Array<string>>): void
```

Obtains the authorization list of the specified authentication type for an application account. The authorization list contains all authorized bundles. The token authorization list is set by [setOAuthTokenVisibility](#setoauthtokenvisibility). This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getAuthList](#getauthlist)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAuthList](#getauthlist)(name: string, authType: string, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of authorized bundles obtained. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getOAuthList('LiSi', 'getSocialData', (err: BusinessError, data: string[]) => {
  if (err) {
    console.error(`getOAuthList err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getOAuthList data: ' + JSON.stringify(data));
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getOAuthList('LiSi', 'getSocialData').then((data: string[]) => {
  console.info('getOAuthList data: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`getOAuthList err: code is ${err.code}, message is ${err.message}`);
});
```

## getOAuthList

```TypeScript
getOAuthList(name: string, authType: string): Promise<Array<string>>
```

Obtains the authorization list of the specified authentication type for an application account. The authorization list contains all authorized bundles. The token authorization list is set by [setOAuthTokenVisibility](#setoauthtokenvisibility). This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getAuthList](#getauthlist-1) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAuthList](#getauthlist-1)(name: string, authType: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return a list of authorized bundles. |

**Examples**

See [getOAuthList](#getoauthlist)

## getOAuthToken

```TypeScript
getOAuthToken(name: string, owner: string, authType: string, callback: AsyncCallback<string>): void
```

Obtains the authorization token of the specified authentication type for an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getAuthToken](#getauthtoken)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAuthToken](#getauthtoken)(name: string, owner: string, authType: string, callback: AsyncCallback&lt;string&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authorization token value obtained. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData',
  (err: BusinessError, data: string) => {
    if (err) {
      console.error(`getOAuthToken err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOAuthToken token: ' + data);
    }
  });
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.getOAuthToken('LiSi', 'com.example.accountjsdemo', 'getSocialData').then((data: string) => {
  console.info('getOAuthToken token: ' + data);
}).catch((err: BusinessError) => {
  console.error(`getOAuthToken err: code is ${err.code}, message is ${err.message}`);
});
```

## getOAuthToken

```TypeScript
getOAuthToken(name: string, owner: string, authType: string): Promise<string>
```

Obtains the authorization token of the specified authentication type for an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getAuthToken](#getauthtoken-1)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAuthToken](#getauthtoken-1)(name: string, owner: string, authType: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the authorization token obtained. |

**Examples**

See [getOAuthToken](#getoauthtoken)

## off('change')

```TypeScript
off(type: 'change', callback?: Callback<Array<AppAccountInfo>>): void
```

Unsubscribes from account information changes.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [off('accountChange')](#offaccountchange)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [off](#offaccountchange)(type: 'accountChange', callback?: Callback&lt;Array&lt;AppAccountInfo&gt;&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type to Unsubscribe to. The value is **'change'**. An event will be reported when the account information changes. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | No | Callback to unregister. By default, no value is passed, which means to unregister all callbacks for the specified event. |

## off('accountChange')

```TypeScript
off(type: 'accountChange', callback?: Callback<Array<AppAccountInfo>>): void
```

Unsubscribes from account information changes.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'accountChange' | Yes | Event type to unsubscribe from. The value is **'accountChange'**. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | No | Callback to unregister. By default, no value is passed, which means to unregister all callbacks for the specified event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid type. |

## on('change')

```TypeScript
on(type: 'change', owners: Array<string>, callback: Callback<Array<AppAccountInfo>>): void
```

Subscribes to account information changes of apps.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [on('accountChange')](#onaccountchange)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [on](#onaccountchange)(type: 'accountChange', owners: Array&lt;string&gt;, callback: Callback&lt;Array&lt;AppAccountInfo&gt;&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'change' | Yes | Event type to subscribe to. The value is **'change'**. An event will be reported when the account information changes. |
| owners | Array&lt;string&gt; | Yes | Application bundle names of the account. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Yes | Callback registered to return the list of changed application accounts. |

## on('accountChange')

```TypeScript
on(type: 'accountChange', owners: Array<string>, callback: Callback<Array<AppAccountInfo>>): void
```

Subscribes to account information changes of apps.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'accountChange' | Yes | Event type to subscribe to. The value is **'accountChange'**. |
| owners | Array&lt;string&gt; | Yes | Application bundle names of the account. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Yes | Callback registered to return the list of changed application accounts. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid type or owners. |
| [12400001](../errorcode-account.md#12400001-application-not-found) | Application not found.<br>**Applicable version:** 9 - 13 |

## queryAuthenticatorInfo

```TypeScript
queryAuthenticatorInfo(owner: string, callback: AsyncCallback<AuthenticatorInfo>): void
```

Obtains the authenticator information of an application. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[AuthenticatorInfo](arkts-basicservices-appaccount-authenticatorinfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the authenticator information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid owner. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.queryAuthenticatorInfo('com.example.accountjsdemo',
    (err: BusinessError, info: appAccount.AuthenticatorInfo) => {
      if (err) {
        console.error(`queryAuthenticatorInfo failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('queryAuthenticatorInfo successfully, info: ' + JSON.stringify(info));
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryAuthenticatorInfo exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.queryAuthenticatorInfo('com.example.accountjsdemo').then((
    info: appAccount.AuthenticatorInfo) => { 
    console.info('queryAuthenticatorInfo successfully, info: ' + JSON.stringify(info));
  }).catch((err: BusinessError) => {
    console.error(`queryAuthenticatorInfo failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryAuthenticatorInfo exception: code is ${err.code}, message is ${err.message}`);
}
```

## queryAuthenticatorInfo

```TypeScript
queryAuthenticatorInfo(owner: string): Promise<AuthenticatorInfo>
```

Obtains the authenticator information of an application. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AuthenticatorInfo](arkts-basicservices-appaccount-authenticatorinfo-i.md)&gt; | Promise used to return the authenticator information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid owner. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |

**Examples**

See [queryAuthenticatorInfo](#queryauthenticatorinfo)

## removeAccount

```TypeScript
removeAccount(name: string, callback: AsyncCallback<void>): void
```

Removes an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.removeAccount('ZhaoLiu', (err: BusinessError) => {
    if (err) {
      console.error(`removeAccount failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('removeAccount successfully');
    }
 });
} catch (e) {
  const err = e as BusinessError;
  console.error(`removeAccount exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.removeAccount('Lisi').then(() => {
    console.info('removeAccount successfully');
  }).catch((err: BusinessError) => {
    console.error(`removeAccount failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`removeAccount exception: code is ${err.code}, message is ${err.message}`);
}
```

## removeAccount

```TypeScript
removeAccount(name: string): Promise<void>
```

Removes an application account. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

See [removeAccount](#removeaccount)

## selectAccountsByOptions

```TypeScript
selectAccountsByOptions(options: SelectAccountsOptions, callback: AsyncCallback<Array<AppAccountInfo>>): void
```

Selects the accounts that can be accessed by the invoker based on the options. This API uses an asynchronous callback to return the result. If the options contain label constraints, the authenticator of the target application provides the capability of checking the labels.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SelectAccountsOptions](arkts-basicservices-appaccount-selectaccountsoptions-i.md) | Yes | Options for selecting accounts. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of accounts selected. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid options. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.SelectAccountsOptions = {
  allowedOwners: ['com.example.accountjsdemo'],
  requiredLabels: ['student']
};
try {
  appAccountManager.selectAccountsByOptions(options,
    (err: BusinessError, accountArr: appAccount.AppAccountInfo[]) => {
      if (err) {
        console.error(`selectAccountsByOptions failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('selectAccountsByOptions successfully, accountArr: ' + JSON.stringify(accountArr));
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`selectAccountsByOptions exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.SelectAccountsOptions = {
  allowedOwners: ['com.example.accountjsdemo']
};
try {
  appAccountManager.selectAccountsByOptions(options).then((accountArr: appAccount.AppAccountInfo[]) => {
    console.info('selectAccountsByOptions successfully, accountArr: ' + JSON.stringify(accountArr));
  }).catch((err: BusinessError) => {
    console.error(`selectAccountsByOptions failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`selectAccountsByOptions exception: code is ${err.code}, message is ${err.message}`);
}
```

## selectAccountsByOptions

```TypeScript
selectAccountsByOptions(options: SelectAccountsOptions): Promise<Array<AppAccountInfo>>
```

Selects the accounts that can be accessed by the invoker based on the options. This API uses a promise to return the result. If the options contain label constraints, the authenticator of the target application provides the capability of checking the labels.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SelectAccountsOptions](arkts-basicservices-appaccount-selectaccountsoptions-i.md) | Yes | Options for selecting accounts. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md)&gt;&gt; | Promise used to return the accounts selected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid options. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

See [selectAccountsByOptions](#selectaccountsbyoptions)

## setAccountCredential

```TypeScript
setAccountCredential(name: string, credentialType: string, credential: string, callback: AsyncCallback<void>): void
```

Sets a credential for an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setCredential](#setcredential)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setCredential](#setcredential)(name: string, credentialType: string, credential: string, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| credentialType | string | Yes | Credential type. The value is user-defined and contains a maximum of 1024 characters. |
| credential | string | Yes | Credential value. The value is user-defined and contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If a credential is successfully set for an application account, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAccountCredential('ZhangSan', 'credentialType001', 'credential001', (err: BusinessError) => { 
  if (err) {
    console.error(`setAccountCredential err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('setAccountCredential successful.');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAccountCredential('ZhangSan', 'credentialType001', 'credential001').then(() => { 
  console.info('setAccountCredential Success');
}).catch((err: BusinessError) => {
  console.error(`setAccountCredential err: code is ${err.code}, message is ${err.message}`);
});
```

## setAccountCredential

```TypeScript
setAccountCredential(name: string, credentialType: string, credential: string): Promise<void>
```

Sets a credential for an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setCredential](#setcredential-1)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setCredential](#setcredential-1)(name: string, credentialType: string, credential: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| credentialType | string | Yes | Credential type. The value is user-defined and contains a maximum of 1024 characters. |
| credential | string | Yes | Credential value. The value is user-defined and contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [setAccountCredential](#setaccountcredential)

## setAccountExtraInfo

```TypeScript
setAccountExtraInfo(name: string, extraInfo: string, callback: AsyncCallback<void>): void
```

Sets additional information for an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setCustomData](#setcustomdata)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setCustomData](#setcustomdata)(name: string, key: string, value: string, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| extraInfo | string | Yes | Additional information (information that can be converted to the string type). It cannot contain sensitive information, such as the application account password and token. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAccountExtraInfo('ZhangSan', 'Tk002', (err: BusinessError) => { 
  if (err) {
    console.error(`setAccountExtraInfo err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('setAccountExtraInfo successful.');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAccountExtraInfo('ZhangSan', 'Tk002').then(() => { 
  console.info('setAccountExtraInfo Success');
}).catch((err: BusinessError) => {
  console.error(`setAccountExtraInfo err: code is ${err.code}, message is ${err.message}`);
});
```

## setAccountExtraInfo

```TypeScript
setAccountExtraInfo(name: string, extraInfo: string): Promise<void>
```

Sets additional information for an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setCustomData](#setcustomdata-1)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setCustomData](#setcustomdata-1)(name: string, key: string, value: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| extraInfo | string | Yes | Additional information (information that can be converted to the string type). It cannot contain sensitive information, such as the application account password and token. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [setAccountExtraInfo](#setaccountextrainfo)

## setAppAccess

```TypeScript
setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback<void>): void
```

Sets the access to the data of an account for an application. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |
| isAccessible | boolean | Yes | Whether the access is allowed. The value **true** means to allow the access; the value **false** means the opposite. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or bundleName. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12400001](../errorcode-account.md#12400001-application-not-found) | Application not found.<br>**Applicable version:** 9 - 13 |
| [12400005](../errorcode-account.md#12400005-bundles-in-the-oauth-list-reached-the-limit) | The size of authorization list reaches the upper limit.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAppAccess('ZhangSan', 'com.example.accountjsdemo', true, (err: BusinessError) => {
    if (err) {
      console.error(`setAppAccess failed: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setAppAccess successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAppAccess exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAppAccess('ZhangSan', 'com.example.accountjsdemo', true).then(() => {
    console.info('setAppAccess successfully');
  }).catch((err: BusinessError) => {
    console.error(`setAppAccess failed: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAppAccess exception: code is ${err.code}, message is ${err.message}`);
}
```

## setAppAccess

```TypeScript
setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise<void>
```

Sets the access to the data of an account for an application. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |
| isAccessible | boolean | Yes | Whether the access is allowed. The value **true** means to allow the access; the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or bundleName. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12400001](../errorcode-account.md#12400001-application-not-found) | Application not found.<br>**Applicable version:** 9 - 13 |
| [12400005](../errorcode-account.md#12400005-bundles-in-the-oauth-list-reached-the-limit) | The size of authorization list reaches the upper limit.<br>**Applicable version:** 14 and later |

**Examples**

See [setAppAccess](#setappaccess)

## setAppAccountSyncEnable

```TypeScript
setAppAccountSyncEnable(name: string, isEnable: boolean, callback: AsyncCallback<void>): void
```

Sets data synchronization for an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setDataSyncEnabled](#setdatasyncenabled)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setDataSyncEnabled](#setdatasyncenabled)(name: string, isEnabled: boolean, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| isEnable | boolean | Yes | Whether to enable data synchronization. The value **true** means that data synchronization is enabled, and **false** means the opposite. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAppAccountSyncEnable('ZhangSan', true, (err: BusinessError) => {
  if (err) {
    console.error(`setAppAccountSyncEnable err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('setAppAccountSyncEnable successful.');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAppAccountSyncEnable('ZhangSan', true).then(() => { 
  console.info('setAppAccountSyncEnable Success');
}).catch((err: BusinessError) => {
  console.error(`setAppAccountSyncEnable err: code is ${err.code}, message is ${err.message}`);
});
```

## setAppAccountSyncEnable

```TypeScript
setAppAccountSyncEnable(name: string, isEnable: boolean): Promise<void>
```

Sets data synchronization for an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setDataSyncEnabled](#setdatasyncenabled-1)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setDataSyncEnabled](#setdatasyncenabled-1)(name: string, isEnabled: boolean)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| isEnable | boolean | Yes | Whether to enable data synchronization. The value **true** means that data synchronization is enabled, and **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [setAppAccountSyncEnable](#setappaccountsyncenable)

## setAssociatedData

```TypeScript
setAssociatedData(name: string, key: string, value: string, callback: AsyncCallback<void>): void
```

Sets data to be associated with an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setCustomData](#setcustomdata)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setCustomData](#setcustomdata)(name: string, key: string, value: string, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| key | string | Yes | Key of the associated data. The value contains a maximum of 1024 characters. |
| value | string | Yes | Value of the data to set. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAssociatedData('ZhangSan', 'k001', 'v001', (err: BusinessError) => {
  if (err) {
    console.error(`setAssociatedData err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('setAssociatedData successful.');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setAssociatedData('ZhangSan', 'k001', 'v001').then(() => { 
  console.info('setAssociatedData Success');
}).catch((err: BusinessError) => {
  console.error(`setAssociatedData err: code is ${err.code}, message is ${err.message}`);
});
```

## setAssociatedData

```TypeScript
setAssociatedData(name: string, key: string, value: string): Promise<void>
```

Sets data to be associated with an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setCustomData](#setcustomdata-1)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setCustomData](#setcustomdata-1)(name: string, key: string, value: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| key | string | Yes | Key of the associated data. The value contains a maximum of 1024 characters. |
| value | string | Yes | Value of the data to set. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [setAssociatedData](#setassociateddata)

## setAuthenticatorProperties

```TypeScript
setAuthenticatorProperties(owner: string, callback: AuthCallback): void
```

Sets the authenticator attributes of an application. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the authenticator. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid owner. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAuthenticatorProperties('com.example.accountjsdemo', {
    onResult: (resultCode: number, result?: appAccount.AuthResult) => {
      console.info('setAuthenticatorProperties onResult, resultCode: ' + JSON.stringify(resultCode));
      console.info('setAuthenticatorProperties onResult, result: ' + JSON.stringify(result));
    },
    onRequestRedirected: (request: Want) => {
      console.info('setAuthenticatorProperties onRequestRedirected, request: ' + JSON.stringify(request));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthenticatorProperties err: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.SetPropertiesOptions = {
  properties: { prop1: 'value1' }
};
try {
  appAccountManager.setAuthenticatorProperties('com.example.accountjsdemo', options, {
    onResult: (resultCode: number, result?: appAccount.AuthResult) => {
      console.info('setAuthenticatorProperties onResult, resultCode: ' + JSON.stringify(resultCode));
      console.info('setAuthenticatorProperties onResult, result: ' + JSON.stringify(result));
    },
    onRequestRedirected: (request: Want) => {
      console.info('setAuthenticatorProperties onRequestRedirected, request: ' + JSON.stringify(request));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthenticatorProperties err: code is ${err.code}, message is ${err.message}`);
}
```

## setAuthenticatorProperties

```TypeScript
setAuthenticatorProperties(owner: string, options: SetPropertiesOptions, callback: AuthCallback): void
```

Sets the authenticator attributes of an application. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | Owner of the authenticator. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| options | [SetPropertiesOptions](arkts-basicservices-appaccount-setpropertiesoptions-i.md) | Yes | Authenticator properties to set. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Authenticator callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid owner or options. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

See [setAuthenticatorProperties](#setauthenticatorproperties)

## setAuthToken

```TypeScript
setAuthToken(name: string, authType: string, token: string, callback: AsyncCallback<void>): void
```

Sets an authorization token of the specific authentication type for an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| token | string | Yes | Authorization token. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, authType or token. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12400004](../errorcode-account.md#12400004-token-count-reached-the-limit) | The number of tokens reaches the upper limit. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAuthToken('LiSi', 'getSocialData', 'xxxx', (err: BusinessError) => {
    if (err) {
      console.error(`setAuthToken failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setAuthToken successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthToken exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAuthToken('LiSi', 'getSocialData', 'xxxx').then(() => {
    console.info('setAuthToken successfully');
  }).catch((err: BusinessError) => {
    console.error(`setAuthToken failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthToken exception: code is ${err.code}, message is ${err.message}`);
}
```

## setAuthToken

```TypeScript
setAuthToken(name: string, authType: string, token: string): Promise<void>
```

Sets an authorization token of the specific authentication type for an application account. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| token | string | Yes | Authorization token. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, authType or token. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12400004](../errorcode-account.md#12400004-token-count-reached-the-limit) | The number of tokens reaches the upper limit. |

**Examples**

See [setAuthToken](#setauthtoken)

## setAuthTokenVisibility

```TypeScript
setAuthTokenVisibility(
      name: string,
      authType: string,
      bundleName: string,
      isVisible: boolean,
      callback: AsyncCallback<void>
    ): void
```

Sets the visibility of an authorization token to an application. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |
| isVisible | boolean | Yes | Whether the authorization token is visible to the application. The value **true** means the authorization token is visible to the application; the value **false** means the opposite. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, authType or bundleName. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300107](../errorcode-account.md#12300107-authentication-type-not-found) | AuthType not found. |
| [12400001](../errorcode-account.md#12400001-application-not-found) | Application not found.<br>**Applicable version:** 9 - 13 |
| [12400005](../errorcode-account.md#12400005-bundles-in-the-oauth-list-reached-the-limit) | The size of authorization list reaches the upper limit. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true,
    (err: BusinessError) => {
      if (err) {
        console.error(`setAuthTokenVisibility failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('setAuthTokenVisibility successfully');
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthTokenVisibility exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true).then(() => {
    console.info('setAuthTokenVisibility successfully');
  }).catch((err: BusinessError) => {
    console.error(`setAuthTokenVisibility failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setAuthTokenVisibility exception: code is ${err.code}, message is ${err.message}`);
}
```

## setAuthTokenVisibility

```TypeScript
setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise<void>
```

Sets the visibility of an authorization token to an application. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |
| isVisible | boolean | Yes | Whether the authorization token is visible to the application. The value **true** means the authorization token is visible to the application; the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, authType or bundleName. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300107](../errorcode-account.md#12300107-authentication-type-not-found) | AuthType not found. |
| [12400001](../errorcode-account.md#12400001-application-not-found) | Application not found.<br>**Applicable version:** 9 - 13 |
| [12400005](../errorcode-account.md#12400005-bundles-in-the-oauth-list-reached-the-limit) | The size of authorization list reaches the upper limit. |

**Examples**

See [setAuthTokenVisibility](#setauthtokenvisibility)

## setCredential

```TypeScript
setCredential(name: string, credentialType: string, credential: string,
                             callback: AsyncCallback<void>): void
```

Sets a credential for an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| credentialType | string | Yes | Credential type. The value is user-defined and contains a maximum of 1024 characters. |
| credential | string | Yes | Credential value. The value is user-defined and contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the credential is set successfully, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, credentialType or credential. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setCredential('ZhangSan', 'PIN_SIX', 'xxxxxx', (err: BusinessError) => {
    if (err) {
      console.error(`setCredential failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setCredential successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setCredential exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setCredential('ZhangSan', 'PIN_SIX', 'xxxxxx').then(() => {
    console.info('setCredential successfully');
  }).catch((err: BusinessError) => {
    console.error(`setCredential failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setCredential exception: code is ${err.code}, message is ${err.message}`);
}
```

## setCredential

```TypeScript
setCredential(name: string, credentialType: string, credential: string): Promise<void>
```

Sets a credential for an application account. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| credentialType | string | Yes | Credential type. The value is user-defined and contains a maximum of 1024 characters. |
| credential | string | Yes | Credential value. The value is user-defined and contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, credentialType or credential. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

See [setCredential](#setcredential)

## setCustomData

```TypeScript
setCustomData(name: string, key: string, value: string, callback: AsyncCallback<void>): void
```

Sets custom data for an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| key | string | Yes | Key of the custom data. The value contains a maximum of 1024 characters. |
| value | string | Yes | Value of the custom data. Do not include sensitive data. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, key or value. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12400003](../errorcode-account.md#12400003-custom-data-records-reached-the-limit) | The number of custom data reaches the upper limit. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setCustomData('ZhangSan', 'age', '12', (err: BusinessError) => {
    if (err) {
      console.error(`setCustomData failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setCustomData successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setCustomData exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.setCustomData('ZhangSan', 'age', '12').then(() => {
    console.info('setCustomData successfully');
  }).catch((err: BusinessError) => {
    console.error(`setCustomData failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setCustomData exception: code is ${err.code}, message is ${err.message}`);
}
```

## setCustomData

```TypeScript
setCustomData(name: string, key: string, value: string): Promise<void>
```

Sets custom data for an application account. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| key | string | Yes | Key of the custom data. The value contains a maximum of 1024 characters. |
| value | string | Yes | Value of the custom data. Do not include sensitive data. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, key or value. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12400003](../errorcode-account.md#12400003-custom-data-records-reached-the-limit) | The number of custom data reaches the upper limit. |

**Examples**

See [setCustomData](#setcustomdata)

## setDataSyncEnabled

```TypeScript
setDataSyncEnabled(name: string, isEnabled: boolean, callback: AsyncCallback<void>): void
```

Sets data synchronization for an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| isEnabled | boolean | Yes | Whether to enable data synchronization. The value **true** means that data synchronization is enabled, and **false** means the opposite. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    appAccountManager.setDataSyncEnabled('ZhangSan', true, (err: BusinessError) => { 
        console.error(`setDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
    });
} catch (e) {
    const err = e as BusinessError;
    console.error(`setDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    appAccountManager.setDataSyncEnabled('ZhangSan', true).then(() => { 
        console.info('setDataSyncEnabled Success');
    }).catch((err: BusinessError) => {
        console.error(`setDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
    });
} catch (e) {
    const err = e as BusinessError;
    console.error(`setDataSyncEnabled err: code is ${err.code}, message is ${err.message}`);
}
```

## setDataSyncEnabled

```TypeScript
setDataSyncEnabled(name: string, isEnabled: boolean): Promise<void>
```

Sets data synchronization for an application account. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| isEnabled | boolean | Yes | Whether to enable data synchronization. The value **true** means that data synchronization is enabled, and **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

See [setDataSyncEnabled](#setdatasyncenabled)

## setOAuthToken

```TypeScript
setOAuthToken(name: string, authType: string, token: string, callback: AsyncCallback<void>): void
```

Sets an authorization token of the specific authentication type for an application account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [setAuthToken](#setauthtoken)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setAuthToken](#setauthtoken)(name: string, authType: string, token: string, callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| token | string | Yes | Authorization token. The value contains a maximum of 1024 characters. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setOAuthToken('LiSi', 'getSocialData', 'xxxx', (err: BusinessError) => {
  if (err) {
    console.error(`setOAuthToken err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('setOAuthToken successful.');
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setOAuthToken('LiSi', 'getSocialData', 'xxxx').then(() => {
  console.info('setOAuthToken successfully');
}).catch((err: BusinessError) => {
  console.error(`setOAuthToken err: code is ${err.code}, message is ${err.message}`);
});
```

## setOAuthToken

```TypeScript
setOAuthToken(name: string, authType: string, token: string): Promise<void>
```

Sets an authorization token of the specific authentication type for an application account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [setAuthToken](#setauthtoken-1)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setAuthToken](#setauthtoken-1)(name: string, authType: string, token: string)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| token | string | Yes | Authorization token. The value contains a maximum of 1024 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [setOAuthToken](#setoauthtoken)

## setOAuthTokenVisibility

```TypeScript
setOAuthTokenVisibility(
      name: string,
      authType: string,
      bundleName: string,
      isVisible: boolean,
      callback: AsyncCallback<void>
    ): void
```

Sets the visibility of an authorization token to an application. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [setAuthTokenVisibility](#setauthtokenvisibility)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setAuthTokenVisibility](#setauthtokenvisibility)( name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback&lt;void&gt; )

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |
| isVisible | boolean | Yes | Whether the authorization token is visible to the application. The value **true** means the authorization token is visible to the application; the value **false** means the opposite. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true,
  (err: BusinessError) => {
    if (err) {
      console.error(`setOAuthTokenVisibility err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setOAuthTokenVisibility successful.');
    }
  });
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

appAccountManager.setOAuthTokenVisibility('LiSi', 'getSocialData', 'com.example.accountjsdemo', true).then(() => {
  console.info('setOAuthTokenVisibility successfully');
}).catch((err: BusinessError) => {
  console.error(`setOAuthTokenVisibility err: code is ${err.code}, message is ${err.message}`);
});
```

## setOAuthTokenVisibility

```TypeScript
setOAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean): Promise<void>
```

Sets the visibility of an authorization token to an application. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [setAuthTokenVisibility](#setauthtokenvisibility-1)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setAuthTokenVisibility](#setauthtokenvisibility-1)(name: string, authType: string, bundleName: string, isVisible: boolean)

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| authType | string | Yes | Authentication type. The value is user-defined and contains a maximum of 1024 characters. |
| bundleName | string | Yes | Bundle name of the application. The value contains a maximum of 512 characters. |
| isVisible | boolean | Yes | Whether the authorization token is visible to the application. The value **true** means the authorization token is visible to the application; the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [setOAuthTokenVisibility](#setoauthtokenvisibility)

## verifyCredential

```TypeScript
verifyCredential(name: string, owner: string, callback: AuthCallback): void
```

Verifies the validity of a specified account credential. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name or owner. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.verifyCredential('zhangsan', 'com.example.accountjsdemo', {
    onResult: (resultCode: number, result?: appAccount.AuthResult) => {
      console.info('verifyCredential onResult, resultCode: ' + JSON.stringify(resultCode));
      console.info('verifyCredential onResult, result: ' + JSON.stringify(result));
    },
    onRequestRedirected: (request: Want) => {
      console.info('verifyCredential onRequestRedirected, request: ' + JSON.stringify(request));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`verifyCredential err: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.VerifyCredentialOptions = {
  credentialType: 'pin',
  credential: '123456'
};
try {
  appAccountManager.verifyCredential('zhangsan', 'com.example.accountjsdemo', options, {
    onResult: (resultCode: number, result?: appAccount.AuthResult) => {
      console.info('verifyCredential onResult, resultCode: ' + JSON.stringify(resultCode));
      console.info('verifyCredential onResult, result: ' + JSON.stringify(result));
    },
    onRequestRedirected: (request: Want) => {
      console.info('verifyCredential onRequestRedirected, request: ' + JSON.stringify(request));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`verifyCredential err: code is ${err.code}, message is ${err.message}`);
}
```

## verifyCredential

```TypeScript
verifyCredential(name: string, owner: string, options: VerifyCredentialOptions, callback: AuthCallback): void
```

Verifies the credential of an application account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.AppAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the application account. The value contains a maximum of 512 characters. |
| owner | string | Yes | Owner of the application account. The value is the bundle name of the application. The value contains a maximum of 1024 characters. |
| options | [VerifyCredentialOptions](arkts-basicservices-appaccount-verifycredentialoptions-i.md) | Yes | Options for credential verification. |
| callback | [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid name, owner or options. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300010](../errorcode-account.md#12300010-account-service-not-respond) | Account service busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | Authenticator service not found. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | Authenticator service exception. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appAccountManager.verifyCredential('zhangsan', 'com.example.accountjsdemo', {
    onResult: (resultCode: number, result?: appAccount.AuthResult) => {
      console.info('verifyCredential onResult, resultCode: ' + JSON.stringify(resultCode));
      console.info('verifyCredential onResult, result: ' + JSON.stringify(result));
    },
    onRequestRedirected: (request: Want) => {
      console.info('verifyCredential onRequestRedirected, request: ' + JSON.stringify(request));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`verifyCredential err: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let options: appAccount.VerifyCredentialOptions = {
  credentialType: 'pin',
  credential: '123456'
};
try {
  appAccountManager.verifyCredential('zhangsan', 'com.example.accountjsdemo', options, {
    onResult: (resultCode: number, result?: appAccount.AuthResult) => {
      console.info('verifyCredential onResult, resultCode: ' + JSON.stringify(resultCode));
      console.info('verifyCredential onResult, result: ' + JSON.stringify(result));
    },
    onRequestRedirected: (request: Want) => {
      console.info('verifyCredential onRequestRedirected, request: ' + JSON.stringify(request));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`verifyCredential err: code is ${err.code}, message is ${err.message}`);
}
```
