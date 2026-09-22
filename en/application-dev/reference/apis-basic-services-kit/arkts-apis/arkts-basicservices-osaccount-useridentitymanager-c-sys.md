# UserIdentityManager (System API)

```TypeScript
class UserIdentityManager
```

Provides APIs for managing the user identity.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## addCredential

```TypeScript
addCredential(credentialInfo: CredentialInfo, callback: IIdmCallback): void
```

Adds credentials of specified types, including the credential type, subtype, and token (if a non-PIN credential is added).

**Since:** 8

**Required permissions:** ohos.permission.MANAGE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| credentialInfo | [CredentialInfo](arkts-basicservices-osaccount-credentialinfo-i-sys.md) | Yes | Credential information to add. |
| callback | [IIdmCallback](arkts-basicservices-osaccount-iidmcallback-i-sys.md) | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid credentialInfo, i.e. authType or authSubType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found.<br>**Applicable version:** 12 and later |
| [12300008](../errorcode-account.md#12300008-restricted-account) | Restricted account.<br>**Applicable version:** 12 and later |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 23 and later |
| 12300090 | Cross-device capability not supported.<br>**Applicable version:** 23 and later |
| 12300091 | Cross-device communication failed.<br>**Applicable version:** 23 and later |
| [12300101](../errorcode-account.md#12300101-incorrect-credential) | The token is invalid. |
| [12300106](../errorcode-account.md#12300106-authentication-type-not-supported) | The authentication type is not supported. |
| [12300109](../errorcode-account.md#12300109-authentication-credential-enrollment-or-update-canceled) | The authentication, enrollment, or update operation is canceled. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The operation timeout. |
| [12300115](../errorcode-account.md#12300115-user-authentication-passwords-reached-the-limit) | The number of credentials reaches the upper limit. |
| [12300116](../errorcode-account.md#12300116-failed-to-verify-the-credential-complexity) | Credential complexity verification failed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let password: Uint8Array = new Uint8Array([0, 0, 0, 0, 0, 0]);
let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
pinAuth.registerInputer({
  onGetData: (authSubType: osAccount.AuthSubType, callback: osAccount.IInputData) => {
    callback.onSetData(authSubType, password);
  }
});
let credentialInfo: osAccount.CredentialInfo = {
  credType: osAccount.AuthType.PIN,
  credSubType: osAccount.AuthSubType.PIN_SIX,
  token: new Uint8Array([]),
  additionalInfo: 'xxx'
};
let userIDM = new osAccount.UserIdentityManager();
userIDM.openSession((err: BusinessError, challenge: Uint8Array) => {
  try {
  userIDM.addCredential(credentialInfo, {
    onResult: (result: number, extraInfo: osAccount.RequestResult) => {
      console.info('addCredential result = ' + result);
      console.info('addCredential extraInfo = ' + extraInfo);
    }
  });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`addCredential exception = code is ${err.code}, message is ${err.message}`);
  }
});
```

## cancel

```TypeScript
cancel(challenge: Uint8Array): void
```

Cancels an entry based on the challenge value.

**Since:** 8

**Required permissions:** ohos.permission.MANAGE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| challenge | Uint8Array | Yes | Challenge value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid challenge. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
let challenge: Uint8Array = new Uint8Array([0]);
try {
  userIDM.cancel(challenge);
} catch (e) {
  const err = e as BusinessError;
  console.error(`cancel code is ${err.code}, message is ${err.message}`);
}
```

## closeSession

```TypeScript
closeSession(accountId?: number): void
```

Closes this session to terminate IDM.

**Since:** 8

**Required permissions:** ohos.permission.MANAGE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | number | No | OS account ID, which is left blank by default. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types.<br>**Applicable version:** 12 and later |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally.<br>**Applicable version:** 12 and later |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found.<br>**Applicable version:** 12 and later |
| [12300008](../errorcode-account.md#12300008-restricted-account) | Restricted account.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let userIDM = new osAccount.UserIdentityManager();
let accountId = 100;
userIDM.closeSession(accountId);
```

## constructor

```TypeScript
constructor()
```

A **constructor()** used to create an instance for managing the user identity.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
let userIDM = new osAccount.UserIdentityManager();
```

## delCred

```TypeScript
delCred(credentialId: Uint8Array, token: Uint8Array, callback: IIdmCallback): void
```

Deletes user credentials.

**Since:** 8

**Required permissions:** ohos.permission.MANAGE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| credentialId | Uint8Array | Yes | Credential ID. |
| token | Uint8Array | Yes | Authentication token. |
| callback | [IIdmCallback](arkts-basicservices-osaccount-iidmcallback-i-sys.md) | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid credentialId. |
| [12300101](../errorcode-account.md#12300101-incorrect-credential) | The token is invalid. |
| [12300102](../errorcode-account.md#12300102-credential-not-found) | The credential does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
let credentialId: Uint8Array = new Uint8Array([0, 0, 0, 0, 0, 0, 0, 0]);
let token: Uint8Array = new Uint8Array([0]);
try {
  userIDM.delCred(credentialId, token, {
    onResult: (result: number, extraInfo: osAccount.RequestResult) => {
        console.info('delCred result = ' + result);
        console.info('delCred extraInfo = ' + JSON.stringify(extraInfo));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`delCred exception = code is ${err.code}, message is ${err.message}`);
}
```

## delUser

```TypeScript
delUser(token: Uint8Array, callback: IIdmCallback): void
```

Deletes a user with an authentication token. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.MANAGE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| token | Uint8Array | Yes | Authentication token. |
| callback | [IIdmCallback](arkts-basicservices-osaccount-iidmcallback-i-sys.md) | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300101](../errorcode-account.md#12300101-incorrect-credential) | The token is invalid. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
let token: Uint8Array = new Uint8Array([0]);
try {
  userIDM.delUser(token, {
    onResult: (result: number, extraInfo: osAccount.RequestResult) => {
      console.info('delUser result = ' + result);
      console.info('delUser extraInfo = ' + JSON.stringify(extraInfo));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`delUser exception = code is ${err.code}, message is ${err.message}`);
}
```

## getAuthInfo

```TypeScript
getAuthInfo(callback: AsyncCallback<Array<EnrolledCredInfo>>): void
```

Obtains authentication information. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.USE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[EnrolledCredInfo](arkts-basicservices-osaccount-enrolledcredinfo-i-sys.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is information about all registered credentials of the user. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
try {
  userIDM.getAuthInfo((err: BusinessError, result: osAccount.EnrolledCredInfo[]) => {
    if (err) {
      console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAuthInfo result = ' + JSON.stringify(result));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="getauthinfo-1"></a>

## getAuthInfo

```TypeScript
getAuthInfo(authType: AuthType, callback: AsyncCallback<Array<EnrolledCredInfo>>): void
```

Obtains authentication information of the specified type. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.USE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | Yes | Authentication credential type. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[EnrolledCredInfo](arkts-basicservices-osaccount-enrolledcredinfo-i-sys.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the information about all enrolled credentials of the specified type. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid authType. |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
try {
  userIDM.getAuthInfo(osAccount.AuthType.PIN,
    (err: BusinessError, result: osAccount.EnrolledCredInfo[]) => {
    if (err) {
      console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getAuthInfo result = ' + JSON.stringify(result));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="getauthinfo-2"></a>

## getAuthInfo

```TypeScript
getAuthInfo(authType: AuthType): Promise<Array<EnrolledCredInfo>>
```

Obtains authentication information. This API uses a promise to return the result.

**Since:** 8

**Required permissions:** ohos.permission.USE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | Yes | Authentication type, which indicates that information about all authentication types is obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[EnrolledCredInfo](arkts-basicservices-osaccount-enrolledcredinfo-i-sys.md)&gt;&gt; | Promise used to return the information about all the enrolled credentials of the specified type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid authType. |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
try {
  userIDM.getAuthInfo(osAccount.AuthType.PIN).then((result: osAccount.EnrolledCredInfo[]) => {
    console.info('getAuthInfo result = ' + JSON.stringify(result))
  }).catch((err: BusinessError) => {
    console.error(`getAuthInfo error = code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="getauthinfo-3"></a>

## getAuthInfo

```TypeScript
getAuthInfo(options?: GetAuthInfoOptions): Promise<Array<EnrolledCredInfo>>
```

Obtains authentication information. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.USE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GetAuthInfoOptions](arkts-basicservices-osaccount-getauthinfooptions-i-sys.md) | No | Optional parameters for obtaining authentication information. This parameter is left empty by default, indicating that all enrolled credential information of the current user is obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[EnrolledCredInfo](arkts-basicservices-osaccount-enrolledcredinfo-i-sys.md)&gt;&gt; | Promise used to return the information about all the enrolled credentials of the specified type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid options. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
let options: osAccount.GetAuthInfoOptions = {
  authType: osAccount.AuthType.PIN,
  accountId: 100,
};
try {
  userIDM.getAuthInfo(options).then((result: osAccount.EnrolledCredInfo[]) => {
    console.info('getAuthInfo result = ' + JSON.stringify(result))
  }).catch((err: BusinessError) => {
    console.error(`getAuthInfo error = code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
}
```

## getEnrolledId

```TypeScript
getEnrolledId(authType: AuthType, accountId?: number): Promise<Uint8Array>
```

Obtains the ID of the enrolled credential based on the credential type and account ID (optional). This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.USE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | Yes | Credential type. |
| accountId | number | No | OS account ID, which is left blank by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the credential ID obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid authType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| 12300020 | Device hardware abnormal.<br>**Applicable version:** 23 and later |
| [12300102](../errorcode-account.md#12300102-credential-not-found) | The credential does not exist. |
| [12300106](../errorcode-account.md#12300106-authentication-type-not-supported) | The authentication type is not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
let authType: osAccount.AuthType = osAccount.AuthType.PIN;
let accountId = 100;
try {
  userIDM.getEnrolledId(authType, accountId).then((enrolledId: Uint8Array) => {
    console.info('getEnrolledId enrolledId = ' + JSON.stringify(enrolledId));
  }).catch((err: BusinessError) => {
    console.error(`getEnrolledId error = code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getEnrolledId exception = code is ${err.code}, message is ${err.message}`);
}
```

## offCredentialChanged

```TypeScript
offCredentialChanged(callback?: Callback<CredentialChangeInfo>): void
```

Unsubscribes from credential change events. If no callback is not specified, this API unsubscribes from all subscription records.

**Since:** 23

**Required permissions:** ohos.permission.USE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[CredentialChangeInfo](arkts-basicservices-osaccount-credentialchangeinfo-i-sys.md)&gt; | No | Callback used to listen for the credential change events. The default value is **undefined**, indicating that all subscription records are unregistered. If the value is not undefined, only the subscription records related to the specified callback are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let identityMgr: osAccount.UserIdentityManager = new osAccount.UserIdentityManager();

const callback: Callback<osAccount.CredentialChangeInfo> = (changeInfo: osAccount.CredentialChangeInfo): void => {
  console.info('credentialType: ' + changeInfo.credentialType
    + ', changeType: ' + changeInfo.changeType
    + ', accountId: ' + changeInfo.accountId
    + ', addedCredentialId: ' + changeInfo.addedCredentialId
    + ', deletedCredentialId: ' + changeInfo.deletedCredentialId
    + ', isSilent: ' + changeInfo.isSilent
  )
}

try {
  identityMgr.onCredentialChanged([osAccount.AuthType.PIN, osAccount.AuthType.FACE], callback);
  console.info('Subscribe to the credential changes successfully');
} catch (e) {
  const err = e as BusinessError;
  console.error(`Failed to subscribe to the credential changes, code is ${err.code}, message is ${err.message}`)
}

try {
  identityMgr.offCredentialChanged(callback);
  console.info('Unsubscribe from the credential changes successfully');
} catch (e) {
  const err = e as BusinessError;
  console.error(`Failed to unsubscribe from the credential changes, code is ${err.code}, message is ${err.message}`)
}
```

## onCredentialChanged

```TypeScript
onCredentialChanged(credentialTypes: AuthType[], callback: Callback<CredentialChangeInfo>): void
```

Subscribes to one or more types of credential change events. This API uses a callback to return the credential change information.

**Since:** 23

**Required permissions:** ohos.permission.USE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| credentialTypes | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md)[] | Yes | Credential types subscribed. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[CredentialChangeInfo](arkts-basicservices-osaccount-credentialchangeinfo-i-sys.md)&gt; | Yes | Callback used to listen for the credential change events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | One or more credential types are invalid. |
| [12300106](../errorcode-account.md#12300106-authentication-type-not-supported) | One or more credential types are not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let identityMgr: osAccount.UserIdentityManager = new osAccount.UserIdentityManager();

const callback: Callback<osAccount.CredentialChangeInfo> = (changeInfo: osAccount.CredentialChangeInfo): void => {
  console.info('credentialType: ' + changeInfo.credentialType
    + ', changeType: ' + changeInfo.changeType
    + ', accountId: ' + changeInfo.accountId
    + ', addedCredentialId: ' + changeInfo.addedCredentialId
    + ', deletedCredentialId: ' + changeInfo.deletedCredentialId
    + ', isSilent: ' + changeInfo.isSilent
  )
}

try {
  identityMgr.onCredentialChanged([osAccount.AuthType.PIN, osAccount.AuthType.FACE], callback);
  console.info('Subscribe to the credential changes successfully');
} catch (e) {
  const err = e as BusinessError;
  console.error(`Failed to subscribe to the credential changes, code is ${err.code}, message is ${err.message}`)
}
```

## openSession

```TypeScript
openSession(callback: AsyncCallback<Uint8Array>): void
```

Opens a session to obtain the challenge value. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.MANAGE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Uint8Array&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the challenge value obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
try {
  userIDM.openSession((err: BusinessError, challenge: Uint8Array) => {
    if (err) {
      console.error(`openSession exception = code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('openSession challenge = ' + JSON.stringify(challenge));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`openSession exception = code is ${err.code}, message is ${err.message}`);
}
```

<a id="opensession-1"></a>

## openSession

```TypeScript
openSession(accountId?: number): Promise<Uint8Array>
```

Opens a session. This API returns a challenge value, which can be used to determine whether the subsequent identity authentication is in this session. This can prevent replay attacks. This API uses a promise to return the result.

**Since:** 8

**Required permissions:** ohos.permission.MANAGE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountId | number | No | OS account ID, which is left blank by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the challenge value obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found.<br>**Applicable version:** 12 and later |
| [12300008](../errorcode-account.md#12300008-restricted-account) | Restricted account.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
let accountId = 100;
try {
  userIDM.openSession(accountId).then((challenge: Uint8Array) => {
    console.info('openSession challenge = ' + JSON.stringify(challenge));
  }).catch((err: BusinessError) => {
    console.error(`openSession error = code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`openSession exception = code is ${err.code}, message is ${err.message}`);
}
```

## updateCredential

```TypeScript
updateCredential(credentialInfo: CredentialInfo, callback: IIdmCallback): void
```

Updates credentials. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.MANAGE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| credentialInfo | [CredentialInfo](arkts-basicservices-osaccount-credentialinfo-i-sys.md) | Yes | Credential information to add. |
| callback | [IIdmCallback](arkts-basicservices-osaccount-iidmcallback-i-sys.md) | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid credentialInfo, i.e. authType or authSubType. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found.<br>**Applicable version:** 12 and later |
| [12300101](../errorcode-account.md#12300101-incorrect-credential) | The token is invalid. |
| [12300102](../errorcode-account.md#12300102-credential-not-found) | The credential does not exist. |
| [12300106](../errorcode-account.md#12300106-authentication-type-not-supported) | The authentication type is not supported. |
| [12300109](../errorcode-account.md#12300109-authentication-credential-enrollment-or-update-canceled) | The authentication, enrollment, or update operation is canceled. |
| [12300111](../errorcode-account.md#12300111-authentication-timed-out) | The operation time out. |
| [12300116](../errorcode-account.md#12300116-failed-to-verify-the-credential-complexity) | Credential complexity verification failed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let userIDM = new osAccount.UserIdentityManager();
let userAuth: osAccount.UserAuth = new osAccount.UserAuth();
let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
let password: Uint8Array = new Uint8Array([0, 0, 0, 0, 0, 0]);
let credentialInfo: osAccount.CredentialInfo = {
  credType: osAccount.AuthType.PIN,
  credSubType: osAccount.AuthSubType.PIN_SIX,
  token: new Uint8Array([]),
};
pinAuth.registerInputer({
  onGetData: (authSubType: osAccount.AuthSubType, callback: osAccount.IInputData) => {
    callback.onSetData(authSubType, password);
  }
});
userIDM.openSession((err: BusinessError, challenge: Uint8Array) => {
  userAuth.auth(challenge, credentialInfo.credType, osAccount.AuthTrustLevel.ATL1, {
    onResult: (result: number, extraInfo: osAccount.AuthResult) => {
      if (result != osAccount.ResultCode.SUCCESS) {
        return;
      }
      if (extraInfo.token != null) {
        credentialInfo.token = extraInfo.token;
      }
      try {
        userIDM.updateCredential(credentialInfo, {
          onResult: (result: number, extraInfo: osAccount.RequestResult) => {
            console.info('updateCredential result = ' + result);
            console.info('updateCredential extraInfo = ' + extraInfo);
          }
        });
      } catch (e) {
        const err = e as BusinessError;
        console.error(`updateCredential exception = code is ${err.code}, message is ${err.message}`);
      }
    }
  });
});
```
