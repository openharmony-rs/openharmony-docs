# DomainAccountManager

```TypeScript
class DomainAccountManager
```

Provides APIs for domain account management.

**Since:** 18

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## auth

```TypeScript
static auth(domainAccountInfo: DomainAccountInfo, credential: Uint8Array, callback: IUserAuthCallback): void
```

Authenticates a domain account.

**Since:** 10

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Domain account information. |
| credential | Uint8Array | Yes | Credentials of the domain account. |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | Yes | Callback used to return the authentication result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid domainAccountInfo or credential. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Domain account does not exist. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception. |
| [12300101](../errorcode-account.md#12300101-incorrect-credential) | Authentication failed. |
| [12300109](../errorcode-account.md#12300109-authentication-credential-enrollment-or-update-canceled) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../errorcode-account.md#12300110-authentication-locked) | The authentication is locked. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The authentication time out. |
| [12300112](../errorcode-account.md#12300112-authentication-service-does-not-respond) | The authentication service is busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | The account authentication service does not exist. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The account authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainAccountInfo: osAccount.DomainAccountInfo = {
  domain: 'CHINA',
  accountName: 'zhangsan'
}
let credential = new Uint8Array([0])
try {
  osAccount.DomainAccountManager.auth(domainAccountInfo, credential, {
    onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
      console.info('auth resultCode = ' + resultCode);
      console.info('auth authResult = ' + JSON.stringify(authResult));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`auth exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="auth-1"></a>

## auth

```TypeScript
static auth(
      domainAccountInfo: DomainAccountInfo,
      credential: Uint8Array,
      options: DomainAccountAuthOptions,
      callback: IUserAuthCallback): void
```

Authenticates a specified domain account. You can specify authentication options, such as server parameters. This API uses an asynchronous callback to return the result.

**Since:** 24

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Domain account information. |
| credential | Uint8Array | Yes | Credentials of the domain account. |
| options | [DomainAccountAuthOptions](arkts-basicservices-osaccount-domainaccountauthoptions-i-sys.md) | Yes | Options for domain account authentication. |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | Yes | Callback used to return the authentication result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid domainAccountInfo or credential. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Domain account does not exist. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception. |
| [12300101](../errorcode-account.md#12300101-incorrect-credential) | Authentication failed. |
| [12300109](../errorcode-account.md#12300109-authentication-credential-enrollment-or-update-canceled) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../errorcode-account.md#12300110-authentication-locked) | The authentication is locked. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The authentication time out. |
| [12300112](../errorcode-account.md#12300112-authentication-service-does-not-respond) | The authentication service is busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | The account authentication service does not exist. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The account authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainAccountInfo: osAccount.DomainAccountInfo = {
  domain: 'CHINA',
  accountName: 'zhangsan'
}
let credential = new Uint8Array([0]);
try {
  let serverParams: Record<string, Object> = {
    "uri": "test.example.com",
    "port": 100
  }
  let authOptions: osAccount.DomainAccountAuthOptions = {
    serverParams: serverParams
  }
  osAccount.DomainAccountManager.auth(domainAccountInfo, credential, authOptions, {
    onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
      console.info('auth resultCode = ' + resultCode);
      console.info('auth authResult = ' + JSON.stringify(authResult));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`auth exception = code is ${err.code}, message is ${err.message}`);
}
```

## authWithPopup

```TypeScript
static authWithPopup(callback: IUserAuthCallback): void
```

Authenticates a domain account in a pop-up window.

**Since:** 10

**Required permissions:** 
- API version 11 and later: N/A
- API version 10: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | Yes | Callback used to return the authentication result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 10 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | No domain account is bound. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception. |
| [12300101](../errorcode-account.md#12300101-incorrect-credential) | Authentication failed. |
| [12300109](../errorcode-account.md#12300109-authentication-credential-enrollment-or-update-canceled) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../errorcode-account.md#12300110-authentication-locked) | The authentication is locked. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The authentication time out. |
| [12300112](../errorcode-account.md#12300112-authentication-service-does-not-respond) | The authentication service is busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | The account authentication service does not exist. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The account authentication service works abnormally. |
| 12300211 | Server unreachable.<br>**Applicable version:** 11 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  osAccount.DomainAccountManager.authWithPopup({
    onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
      console.info('auth resultCode = ' + resultCode);
      console.info('auth authResult = ' + JSON.stringify(authResult));
    }
  })
} catch (e) {
  const err = e as BusinessError;
  console.error(`auth exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="authwithpopup-1"></a>

## authWithPopup

```TypeScript
static authWithPopup(localId: number, callback: IUserAuthCallback): void
```

Authenticates a domain account in a pop-up window.

**Since:** 10

**Required permissions:** 
- API version 11 and later: N/A
- API version 10: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | Local ID of the OS account bound to the domain account. |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | Yes | Callback used to return the authentication result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 10 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | No domain account is bound. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception. |
| [12300101](../errorcode-account.md#12300101-incorrect-credential) | Authentication failed. |
| [12300109](../errorcode-account.md#12300109-authentication-credential-enrollment-or-update-canceled) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../errorcode-account.md#12300110-authentication-locked) | The authentication is locked. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The authentication time out. |
| [12300112](../errorcode-account.md#12300112-authentication-service-does-not-respond) | The authentication service is busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | The account authentication service does not exist. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The account authentication service works abnormally. |
| 12300211 | Server unreachable.<br>**Applicable version:** 11 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  osAccount.DomainAccountManager.authWithPopup(100, {
    onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
      console.info('authWithPopup resultCode = ' + resultCode);
      console.info('authWithPopup authResult = ' + JSON.stringify(authResult));
    }
  })
} catch (e) {
  const err = e as BusinessError;
  console.error(`authWithPopup exception = code is ${err.code}, message is ${err.message}`);
}
```

## getAccessToken

```TypeScript
static getAccessToken(businessParams: Record<string, Object>, callback: AsyncCallback<Uint8Array>): void
```

Obtains the business access token of a domain account. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| businessParams | Record&lt;string, Object&gt; | Yes | Business parameters. The specific formats vary depending on the domain plug-in. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Uint8Array&gt; | Yes | Callback used to return the result. If the business access token is obtained successfully, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid business parameters. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Domain account not found. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception. |
| [12300014](../errorcode-account.md#12300014-domain-account-not-authenticated) | The domain account is not authenticated. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The operation time out. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let businessParams: Record<string, Object> = {
  'clientId': 'xxx',
  'secretId': 'yyy'
};  // depends on the implementation of the domain plugin
try {
  osAccount.DomainAccountManager.getAccessToken(businessParams,
    (err: BusinessError, result: Uint8Array) => {
    if (err) {
      console.error(`getAccessToken failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAccessToken result: ' + result);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAccessToken exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="getaccesstoken-2"></a>

## getAccessToken

```TypeScript
static getAccessToken(businessParams: Record<string, Object>): Promise<Uint8Array>
```

Obtains the business access token of a domain account. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| businessParams | Record&lt;string, Object&gt; | Yes | Business parameters. The specific formats vary depending on the domain plug-in. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the business access token obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid business parameters. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Domain account not found. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception. |
| [12300014](../errorcode-account.md#12300014-domain-account-not-authenticated) | The domain account is not authenticated. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The operation time out. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let businessParams: Record<string, Object> = {
  'clientId': 'xxx',
  'secretId': 'yyy'
};  // depends on the implementation of the domain plugin
try {
  osAccount.DomainAccountManager.getAccessToken(businessParams)
    .then((result: Uint8Array) => {
    console.info('getAccessToken result: ' + result);
  }).catch((err: BusinessError) => {
    console.error(`getAccessToken failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAccessToken exception = code is ${err.code}, message is ${err.message}`);
}
```

## getAccountInfo

```TypeScript
static getAccountInfo(options: GetDomainAccountInfoOptions, callback: AsyncCallback<DomainAccountInfo>): void
```

Obtains information about a specified domain account. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.GET_DOMAIN_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GetDomainAccountInfoOptions](arkts-basicservices-osaccount-getdomainaccountinfooptions-i-sys.md) | Yes | Domain account information. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception. |
| [12300014](../errorcode-account.md#12300014-domain-account-not-authenticated) | Not authenticated. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The operation time out. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainAccountInfo: osAccount.GetDomainAccountInfoOptions = {
  domain: 'CHINA',
  accountName: 'zhangsan'
}
try {
  osAccount.DomainAccountManager.getAccountInfo(domainAccountInfo,
    (err: BusinessError, result: osAccount.DomainAccountInfo) => {
    if (err) {
      console.error(`call getAccountInfo failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAccountInfo result: ' + result);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAccountInfo exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="getaccountinfo-1"></a>

## getAccountInfo

```TypeScript
static getAccountInfo(options: GetDomainAccountInfoOptions): Promise<DomainAccountInfo>
```

Obtains information about a specified domain account. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.GET_DOMAIN_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GetDomainAccountInfoOptions](arkts-basicservices-osaccount-getdomainaccountinfooptions-i-sys.md) | Yes | Domain account information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md)&gt; | Promise used to return the domain account information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception. |
| [12300014](../errorcode-account.md#12300014-domain-account-not-authenticated) | Not authenticated. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The operation time out. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainAccountInfo: osAccount.GetDomainAccountInfoOptions = {
  domain: 'CHINA',
  accountName: 'zhangsan'
}
try {
  osAccount.DomainAccountManager.getAccountInfo(domainAccountInfo)
    .then((result: osAccount.DomainAccountInfo) => {
    console.info('getAccountInfo result: ' + result);
  }).catch((err: BusinessError) => {
    console.error(`call getAccountInfo failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAccountInfo exception = code is ${err.code}, message is ${err.message}`);
}
```

## hasAccount

```TypeScript
static hasAccount(domainAccountInfo: DomainAccountInfo, callback: AsyncCallback<boolean>): void
```

Checks whether a domain account exists. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Domain account information. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means that the specified domain account exists; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid domainAccountInfo. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception. |
| [12300014](../errorcode-account.md#12300014-domain-account-not-authenticated) | Not authenticated. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The operation time out. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainAccountInfo: osAccount.DomainAccountInfo = {
  domain: 'CHINA',
  accountName: 'zhangsan'
}
try {
  osAccount.DomainAccountManager.hasAccount(domainAccountInfo, (err: BusinessError, result: boolean) => {
    if (err) {
      console.error(`call hasAccount failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('hasAccount result: ' + result);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`hasAccount exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="hasaccount-1"></a>

## hasAccount

```TypeScript
static hasAccount(domainAccountInfo: DomainAccountInfo): Promise<boolean>
```

Checks whether a domain account exists. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Domain account information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the specified domain account exists; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid domainAccountInfo. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception. |
| [12300014](../errorcode-account.md#12300014-domain-account-not-authenticated) | Not authenticated. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The operation time out. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainAccountInfo: osAccount.DomainAccountInfo = {
  domain: 'CHINA',
  accountName: 'zhangsan'
}
try {
  osAccount.DomainAccountManager.hasAccount(domainAccountInfo).then((result: boolean) => {
    console.info('hasAccount result: ' + result);
  }).catch((err: BusinessError) => {
      console.error(`call hasAccount failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`hasAccount exception = code is ${err.code}, message is ${err.message}`);
}
```

## isAuthenticationExpired

```TypeScript
static isAuthenticationExpired(domainAccountInfo: DomainAccountInfo): Promise<boolean>
```

Checks whether the authentication of a domain account has expired. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Domain account information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the specified domain account has expired; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Domain account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainInfo: osAccount.DomainAccountInfo =
  {domain: 'testDomain', accountName: 'testAccountName'};
try {
  osAccount.DomainAccountManager.isAuthenticationExpired(domainInfo).then((result: boolean) => {
    console.info('isAuthenticationExpired, result: ' + result);
  }).catch((err: BusinessError) => {
    console.error('isAuthenticationExpired err: ' + err);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error('isAuthenticationExpired exception: ' + e);
}
```

## registerPlugin

```TypeScript
static registerPlugin(plugin: DomainPlugin): void
```

Registers a domain plug-in.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| plugin | [DomainPlugin](arkts-basicservices-osaccount-domainplugin-i-sys.md) | Yes | Domain plug-in to register. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| 12300201 | The domain plugin has been registered. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';

let plugin: osAccount.DomainPlugin = {
  auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
       callback: osAccount.IUserAuthCallback) => {},
  authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
                callback: osAccount.IUserAuthCallback) => {},
  authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                callback: osAccount.IUserAuthCallback) => {},
  getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
                 callback: AsyncCallback<osAccount.DomainAccountInfo>) => {},
  getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
                      callback: AsyncCallback<osAccount.AuthStatusInfo>) => {},
  bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
                callback: AsyncCallback<void>) => {},
  unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {},
  isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                      callback: AsyncCallback<boolean>) => {},
  getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {}
}
try {
  osAccount.DomainAccountManager.registerPlugin(plugin);
  console.info('registerPlugin success.');
} catch (e) {
  const err = e as BusinessError;
  console.error(`registerPlugin code is ${err.code}, message is ${err.message}`);
}
```

## unregisterPlugin

```TypeScript
static unregisterPlugin(): void
```

Unregisters this domain plug-in.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  osAccount.DomainAccountManager.unregisterPlugin();
  console.info('unregisterPlugin success.');
} catch (e) {
  const err = e as BusinessError;
  console.error(`unregisterPlugin code is ${err.code}, message is ${err.message}`);
}
```

## updateAccountToken

```TypeScript
static updateAccountToken(
      domainAccountInfo: DomainAccountInfo,
      token: Uint8Array,
      callback: AsyncCallback<void>
    ): void
```

Updates the token of a domain account. An empty token means an invalid token. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Domain account information. |
| token | Uint8Array | Yes | New domain account token. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid token. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainAccountInfo: osAccount.DomainAccountInfo = {
  domain: 'CHINA',
  accountName: 'zhangsan',
  accountId: '123456'
}
let token = new Uint8Array([0])
try {
  osAccount.DomainAccountManager.updateAccountToken(domainAccountInfo, token, (err: BusinessError) => {
    if (err != null) {
      console.error(`updateAccountToken failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('updateAccountToken successfully');
    }
  })
} catch (e) {
  const err = e as BusinessError;
  console.error(`updateAccountToken exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="updateaccounttoken-1"></a>

## updateAccountToken

```TypeScript
static updateAccountToken(domainAccountInfo: DomainAccountInfo, token: Uint8Array): Promise<void>
```

Updates the token of a domain account. An empty token means an invalid token. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Domain account information. |
| token | Uint8Array | Yes | New domain account token. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid token. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainAccountInfo: osAccount.DomainAccountInfo = {
  domain: 'CHINA',
  accountName: 'zhangsan',
  accountId: '123456'
}
let token = new Uint8Array([0])
try {
  osAccount.DomainAccountManager.updateAccountToken(domainAccountInfo, token).then(() => {
    console.info('updateAccountToken successfully');
  }).catch((err: BusinessError) => {
    console.error(`updateAccountToken failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`updateAccountToken exception = code is ${err.code}, message is ${err.message}`);
}
```
