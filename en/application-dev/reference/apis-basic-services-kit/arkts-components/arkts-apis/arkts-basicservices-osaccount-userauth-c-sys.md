# UserAuth (System API)

```TypeScript
class UserAuth
```

Provides APIs for user authentication.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## auth

```TypeScript
auth(
      challenge: Uint8Array,
      authType: AuthType,
      authTrustLevel: AuthTrustLevel,
      callback: IUserAuthCallback
    ): Uint8Array
```

Performs authentication of the current user.

**Since:** 8

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| challenge | Uint8Array | Yes | Challenge value, which is a random number used to improve security. |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | Yes | Authentication credential type. |
| authTrustLevel | [AuthTrustLevel](arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | Yes | Trust level of the authentication result. |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | Yes | Callback used to return the authentication result. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | ID of the context for canceling the authentication. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid challenge, authType or authTrustLevel. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception.<br>**Applicable version:** 12 and later |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 20 and later |
| 12300090 | Cross-device capability not supported.<br>**Applicable version:** 20 and later |
| 12300091 | Cross-device communication failed.<br>**Applicable version:** 20 and later |
| [12300101](../errorcode-account.md#12300101-incorrect-credential) | The credential is incorrect. |
| [12300102](../errorcode-account.md#12300102-credential-not-found) | The credential does not exist. |
| [12300105](../errorcode-account.md#12300105-trust-level-not-supported) | The trust level is not supported. |
| [12300106](../errorcode-account.md#12300106-authentication-type-not-supported) | The authentication type is not supported. |
| [12300109](../errorcode-account.md#12300109-authentication-credential-enrollment-or-update-canceled) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../errorcode-account.md#12300110-authentication-locked) | The authentication is locked. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The authentication time out. |
| [12300112](../errorcode-account.md#12300112-authentication-service-does-not-respond) | The authentication service is busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | The authentication service does not exist.<br>**Applicable version:** 12 and later |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The authentication service works abnormally.<br>**Applicable version:** 12 and later |
| [12300117](../errorcode-account.md#12300117-pin-expired) | PIN is expired.<br>**Applicable version:** 12 and later |
| 12300119 | Multi-factor authentication failed.<br>**Applicable version:** 20 and later |
| [12300120](../errorcode-account.md#12300120-credential-expired) | The credentials are no longer valid.<br>**Applicable version:** 23 and later |
| 12300211 | Server unreachable.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userAuth = new osAccount.UserAuth();
let challenge: Uint8Array = new Uint8Array([0]);
let authType: osAccount.AuthType = osAccount.AuthType.PIN;
let authTrustLevel: osAccount.AuthTrustLevel = osAccount.AuthTrustLevel.ATL1;
try {
  userAuth.auth(challenge, authType, authTrustLevel, {
    onResult: (result: number, extraInfo: osAccount.AuthResult) => {
      console.info('auth result = ' + result);
      console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
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
auth(
      challenge: Uint8Array,
      authType: AuthType,
      authTrustLevel: AuthTrustLevel,
      options: AuthOptions,
      callback: IUserAuthCallback
    ): Uint8Array
```

Starts user authentication based on the specified challenge value, authentication type (PIN, facial, or fingerprint authentication), authentication trust level, and optional parameters (such as the account ID and authentication intent).

**Since:** 12

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| challenge | Uint8Array | Yes | Challenge value, which is a random number used to prevent replay attacks and improve security. |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | Yes | Authentication credential type. |
| authTrustLevel | [AuthTrustLevel](arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | Yes | Trust level of the authentication result. |
| options | [AuthOptions](arkts-basicservices-osaccount-authoptions-i-sys.md) | Yes | Optional parameters for the authentication. |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | Yes | Callback used to return the authentication result. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | ID of the context for canceling the authentication. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid challenge, authType, authTrustLevel or options. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception. |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 20 and later |
| 12300090 | Cross-device capability not supported.<br>**Applicable version:** 20 and later |
| 12300091 | Cross-device communication failed.<br>**Applicable version:** 20 and later |
| [12300101](../errorcode-account.md#12300101-incorrect-credential) | The credential is incorrect. |
| [12300102](../errorcode-account.md#12300102-credential-not-found) | The credential does not exist. |
| [12300105](../errorcode-account.md#12300105-trust-level-not-supported) | The trust level is not supported. |
| [12300106](../errorcode-account.md#12300106-authentication-type-not-supported) | The authentication type is not supported. |
| [12300109](../errorcode-account.md#12300109-authentication-credential-enrollment-or-update-canceled) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../errorcode-account.md#12300110-authentication-locked) | The authentication is locked. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The authentication timeout. |
| [12300112](../errorcode-account.md#12300112-authentication-service-does-not-respond) | The authentication service is busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | The authentication service does not exist. |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The authentication service works abnormally. |
| [12300117](../errorcode-account.md#12300117-pin-expired) | PIN is expired. |
| 12300119 | Multi-factor authentication failed.<br>**Applicable version:** 20 and later |
| [12300120](../errorcode-account.md#12300120-credential-expired) | The credentials are no longer valid.<br>**Applicable version:** 23 and later |
| 12300211 | Server unreachable. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userAuth = new osAccount.UserAuth();
let challenge: Uint8Array = new Uint8Array([0]);
let authType: osAccount.AuthType = osAccount.AuthType.PIN;
let authTrustLevel: osAccount.AuthTrustLevel = osAccount.AuthTrustLevel.ATL1;
let options: osAccount.AuthOptions = {
  accountId: 100
};
try {
  userAuth.auth(challenge, authType, authTrustLevel, options, {
    onResult: (result: number, extraInfo: osAccount.AuthResult) => {
      console.info('auth result = ' + result);
      console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`auth exception = code is ${err.code}, message is ${err.message}`);
}
```

## authUser

```TypeScript
authUser(
      userId: number,
      challenge: Uint8Array,
      authType: AuthType,
      authTrustLevel: AuthTrustLevel,
      callback: IUserAuthCallback
    ): Uint8Array
```

Authenticates a specified user. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| challenge | Uint8Array | Yes | Challenge value, which is a random number used to improve security. |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | Yes | Authentication credential type. |
| authTrustLevel | [AuthTrustLevel](arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | Yes | Trust level of the authentication result. |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | Yes | Callback used to return the authentication result. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | ID of the authentication context, which can be used to cancel the authentication. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid challenge, authType or authTrustLevel. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found.<br>**Applicable version:** 12 and later |
| [12300013](../errorcode-account.md#12300013-network-exception) | Network exception.<br>**Applicable version:** 12 and later |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 20 and later |
| 12300090 | Cross-device capability not supported.<br>**Applicable version:** 20 and later |
| 12300091 | Cross-device communication failed.<br>**Applicable version:** 20 and later |
| [12300101](../errorcode-account.md#12300101-incorrect-credential) | The credential is incorrect. |
| [12300102](../errorcode-account.md#12300102-credential-not-found) | The credential does not exist. |
| [12300105](../errorcode-account.md#12300105-trust-level-not-supported) | The trust level is not supported. |
| [12300106](../errorcode-account.md#12300106-authentication-type-not-supported) | The authentication type is not supported. |
| [12300109](../errorcode-account.md#12300109-authentication-credential-enrollment-or-update-canceled) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../errorcode-account.md#12300110-authentication-locked) | The authentication is locked. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The authentication timeout. |
| [12300112](../errorcode-account.md#12300112-authentication-service-does-not-respond) | The authentication service is busy. |
| [12300113](../errorcode-account.md#12300113-authentication-service-not-found) | The authentication service does not exist.<br>**Applicable version:** 12 and later |
| [12300114](../errorcode-account.md#12300114-authentication-service-abnormal) | The authentication service works abnormally.<br>**Applicable version:** 12 and later |
| [12300117](../errorcode-account.md#12300117-pin-expired) | PIN is expired.<br>**Applicable version:** 12 and later |
| 12300119 | Multi-factor authentication failed.<br>**Applicable version:** 20 and later |
| [12300120](../errorcode-account.md#12300120-credential-expired) | The credentials are no longer valid.<br>**Applicable version:** 23 and later |
| 12300211 | Server unreachable.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userAuth = new osAccount.UserAuth();
let userID: number = 100;
let challenge: Uint8Array = new Uint8Array([0]);
let authType: osAccount.AuthType = osAccount.AuthType.PIN;
let authTrustLevel: osAccount.AuthTrustLevel = osAccount.AuthTrustLevel.ATL1;
try {
  userAuth.authUser(userID, challenge, authType, authTrustLevel, {
    onResult: (result,extraInfo) => {
      console.info('authUser result = ' + result);
      console.info('authUser extraInfo = ' + JSON.stringify(extraInfo));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`authUser exception = code is ${err.code}, message is ${err.message}`);
}
```

## cancelAuth

```TypeScript
cancelAuth(contextID: Uint8Array): void
```

Cancels an authentication.

**Since:** 8

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| contextID | Uint8Array | Yes | ID of the authentication context. The context ID is dynamically generated during the authentication process and is used to identify the authentication operation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid contextId. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userAuth = new osAccount.UserAuth();
let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
let challenge = new Uint8Array([0]);
let contextId: Uint8Array = userAuth.auth(challenge, osAccount.AuthType.PIN, osAccount.AuthTrustLevel.ATL1, {
  onResult: (result: number, extraInfo: osAccount.AuthResult) => {
    console.info('auth result = ' + result);
    console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
  }
});
try {
  userAuth.cancelAuth(contextId);
} catch (e) {
  const err = e as BusinessError;
  console.error(`cancelAuth exception = code is ${err.code}, message is ${err.message}`);
}
```

## constructor

```TypeScript
constructor()
```

A constructor used to create an instance for user authentication.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
let userAuth = new osAccount.UserAuth();
```

## getAvailableStatus

```TypeScript
getAvailableStatus(authType: AuthType, authTrustLevel: AuthTrustLevel): number
```

Obtains the available status of the authentication capability corresponding to the specified authentication type and trust level.

**Since:** 8

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | Yes | Authentication credential type. |
| authTrustLevel | [AuthTrustLevel](arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | Yes | Trust level of the authentication. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Available status of the authentication capability. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid authType or authTrustLevel. |
| [12300117](../errorcode-account.md#12300117-pin-expired) | PIN is expired. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userAuth = new osAccount.UserAuth();
let authType: osAccount.AuthType = osAccount.AuthType.PIN;
let authTrustLevel: osAccount.AuthTrustLevel = osAccount.AuthTrustLevel.ATL1;
try {
  let status: number = userAuth.getAvailableStatus(authType, authTrustLevel);
  console.info('getAvailableStatus status = ' + status);
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAvailableStatus exception = code is ${err.code}, message is ${err.message}`);
}
```

## getProperty

```TypeScript
getProperty(request: GetPropertyRequest, callback: AsyncCallback<ExecutorProperty>): void
```

Obtains the executor property based on the request. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [GetPropertyRequest](arkts-basicservices-osaccount-getpropertyrequest-i-sys.md) | Yes | Request information, including the authentication credential type and property list. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[ExecutorProperty](arkts-basicservices-osaccount-executorproperty-i-sys.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the executor property information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid request. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found.<br>**Applicable version:** 12 and later |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userAuth = new osAccount.UserAuth();
let keys: Array<osAccount.GetPropertyType>  = [
  osAccount.GetPropertyType.AUTH_SUB_TYPE,
  osAccount.GetPropertyType.REMAIN_TIMES,
  osAccount.GetPropertyType.FREEZING_TIME
];
let request: osAccount.GetPropertyRequest = {
  authType: osAccount.AuthType.PIN,
  keys: keys
};
try {
  userAuth.getProperty(request, (err: BusinessError, result: osAccount.ExecutorProperty) => {
    if (err) {
      console.error(`getProperty exception = code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getProperty result = ' + JSON.stringify(result));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getProperty exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="getproperty-1"></a>

## getProperty

```TypeScript
getProperty(request: GetPropertyRequest): Promise<ExecutorProperty>
```

Obtains the executor property based on the request. This API uses a promise to return the result.

**Since:** 8

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [GetPropertyRequest](arkts-basicservices-osaccount-getpropertyrequest-i-sys.md) | Yes | Request information, including the authentication credential type and property list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ExecutorProperty](arkts-basicservices-osaccount-executorproperty-i-sys.md)&gt; | Promise used to return the executor property. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid request. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found.<br>**Applicable version:** 12 and later |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userAuth = new osAccount.UserAuth();
let keys: Array<osAccount.GetPropertyType> = [
  osAccount.GetPropertyType.AUTH_SUB_TYPE,
  osAccount.GetPropertyType.REMAIN_TIMES,
  osAccount.GetPropertyType.FREEZING_TIME
];
let request: osAccount.GetPropertyRequest = {
  authType: osAccount.AuthType.PIN,
  keys: keys
};
try {
  userAuth.getProperty(request).then((result: osAccount.ExecutorProperty) => {
    console.info('getProperty result = ' + JSON.stringify(result));
  }).catch((err: BusinessError) => {
    console.error(`getProperty error = code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getProperty exception = code is ${err.code}, message is ${err.message}`);
}
```

## getPropertyByCredentialId

```TypeScript
getPropertyByCredentialId(credentialId: Uint8Array, keys: Array<GetPropertyType>): Promise<ExecutorProperty>
```

Obtains the specified property information of the associated executor based on the credential ID. This API uses a promise to return the result.

**Since:** 14

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| credentialId | Uint8Array | Yes | Credential ID. |
| keys | Array&lt;[GetPropertyType](arkts-basicservices-osaccount-getpropertytype-e-sys.md)&gt; | Yes | Property type array to be queried. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ExecutorProperty](arkts-basicservices-osaccount-executorproperty-i-sys.md)&gt; | Promise used to return the executor attributes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid keys. |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 23 and later |
| [12300102](../errorcode-account.md#12300102-credential-not-found) | The credential does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
let credInfo: osAccount.EnrolledCredInfo[] = [];
async function getProperty() {
  try {
    credInfo = await userIDM.getAuthInfo(osAccount.AuthType.PRIVATE_PIN);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
    return;
  }
  if (credInfo.length == 0) {
    console.info('no credential infos');
    return;
  }
  let testCredentialId: Uint8Array = credInfo[0].credentialId;
  let keys: Array<osAccount.GetPropertyType> = [
    osAccount.GetPropertyType.AUTH_SUB_TYPE,
    osAccount.GetPropertyType.REMAIN_TIMES,
    osAccount.GetPropertyType.FREEZING_TIME
  ];
  try {
    let userAuth = new osAccount.UserAuth();
    userAuth.getPropertyByCredentialId(testCredentialId, keys).then((result: osAccount.ExecutorProperty) => {
      console.info('getPropertyByCredentialId result = ' + JSON.stringify(result));
    }).catch((err: BusinessError) => {
      console.error(`getPropertyByCredentialId error = code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getPropertyByCredentialId exception = code is ${err.code}, message is ${err.message}`);
  }
}
```

## getVersion

```TypeScript
getVersion(): number
```

Obtains this version number.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Version number obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
let userAuth = new osAccount.UserAuth();
let version: number = userAuth.getVersion();
console.info('getVersion version = ' + version);
```

## prepareRemoteAuth

```TypeScript
prepareRemoteAuth(remoteNetworkId: string): Promise<void>
```

Prepares for remote authentication. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| remoteNetworkId | string | Yes | Remote network ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid remoteNetworkId. |
| 12300090 | Cross-device capability not supported.<br>**Applicable version:** 20 and later |
| 12300091 | Cross-device communication failed.<br>**Applicable version:** 20 and later |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | Operation timeout.<br>**Applicable version:** 20 and later |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userAuth = new osAccount.UserAuth();
let distributedDeviceMgr = distributedDeviceManager.createDeviceManager("com.example.bundleName");
distributedDeviceMgr.getAvailableDeviceList().then((data: Array<distributedDeviceManager.DeviceBasicInfo>) => {
    try {
      if (data.length > 0 && data[0].networkId != null) {
        userAuth.prepareRemoteAuth(data[0].networkId).then(() => {
          console.info('prepareRemoteAuth successfully');
        }).catch((err: BusinessError) => {
          console.error(`prepareRemoteAuth failed, error = code is ${err.code}, message is ${err.message}`);
        });
      }
    } catch (e) {
      const err = e as BusinessError;
      console.error(`prepareRemoteAuth exception = code is ${err.code}, message is ${err.message}`);
    }
  }
)
```

## setProperty

```TypeScript
setProperty(request: SetPropertyRequest, callback: AsyncCallback<void>): void
```

Sets the property for the initialization algorithm. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [SetPropertyRequest](arkts-basicservices-osaccount-setpropertyrequest-i-sys.md) | Yes | Request information, including the authentication credential type and the key value to set. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid request. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userAuth = new osAccount.UserAuth();
let request: osAccount.SetPropertyRequest = {
  authType: osAccount.AuthType.PIN,
  key: osAccount.SetPropertyType.INIT_ALGORITHM,
  setInfo: new Uint8Array([0])
};
try {
  userAuth.setProperty(request, (err: BusinessError) => {
    if (err) {
      console.error(`setProperty failed, error = code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setProperty successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setProperty exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="setproperty-1"></a>

## setProperty

```TypeScript
setProperty(request: SetPropertyRequest): Promise<void>
```

Sets the property for the initialization algorithm. This API uses a promise to return the result.

**Since:** 8

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [SetPropertyRequest](arkts-basicservices-osaccount-setpropertyrequest-i-sys.md) | Yes | Request information, including the authentication credential type and the key value to set. |

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
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid request. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userAuth = new osAccount.UserAuth();
let request: osAccount.SetPropertyRequest = {
  authType: osAccount.AuthType.PIN,
  key: osAccount.SetPropertyType.INIT_ALGORITHM,
  setInfo: new Uint8Array([0])
};
try {
  userAuth.setProperty(request).then(() => {
    console.info('setProperty successfully');
  }).catch((err: BusinessError) => {
    console.error(`setProperty failed, error = code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setProperty exception = code is ${err.code}, message is ${err.message}`);
}
```
