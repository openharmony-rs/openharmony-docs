# UserIdentityManager（系统接口）

获取用户身份管理类。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## addCredential

```TypeScript
addCredential(credentialInfo: CredentialInfo, callback: IIdmCallback): void
```

添加凭据，添加用户凭据信息，传入凭据添加方法和凭据信息（凭据类型，子类，如果添加用户的非密码凭据，则传入密码身份验证令牌），并获取结果/获取信息。

**起始版本：** 8

**需要权限：** ohos.permission.MANAGE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| credentialInfo | CredentialInfo | 是 | 指示凭据信息。 |
| callback | IIdmCallback | 是 | 回调对象，返回添加凭据的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid credentialInfo, i.e. authType or authSubType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found.<br>**适用版本：** 12+ |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted account.<br>**适用版本：** 12+ |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 23+ |
| 12300090 | Cross-device capability not supported.<br>**适用版本：** 23+ |
| 12300091 | Cross-device communication failed.<br>**适用版本：** 23+ |
| [12300101](../../apis-basic-services-kit/errorcode-account.md#12300101-凭据不正确) | The token is invalid. |
| [12300106](../../apis-basic-services-kit/errorcode-account.md#12300106-认证类型不支持) | The authentication type is not supported. |
| [12300109](../../apis-basic-services-kit/errorcode-account.md#12300109-认证凭据录入更新等操作被取消) | The authentication, enrollment, or update operation is canceled. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The operation timeout. |
| [12300115](../../apis-basic-services-kit/errorcode-account.md#12300115-用户认证密码个数达到上限) | The number of credentials reaches the upper limit. |
| [12300116](../../apis-basic-services-kit/errorcode-account.md#12300116-凭证复杂度验证失败) | Credential complexity verification failed.<br>**适用版本：** 12+ |

**示例：**

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

根据挑战值取消条目。

**起始版本：** 8

**需要权限：** ohos.permission.MANAGE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| challenge | Uint8Array | 是 | 挑战值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid challenge. |

**示例：**

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

关闭会话，结束IDM操作。

**起始版本：** 8

**需要权限：** ohos.permission.MANAGE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 否 | 系统账号标识，默认为空。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types.<br>**适用版本：** 12+ |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally.<br>**适用版本：** 12+ |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found.<br>**适用版本：** 12+ |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted account.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
let userIDM = new osAccount.UserIdentityManager();
let accountId = 100;
userIDM.closeSession(accountId);

```

## constructor

```TypeScript
constructor()
```

用户身份管理类的默认构造函数。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例：**

```TypeScript
let userIDM = new osAccount.UserIdentityManager();

```

## delCred

```TypeScript
delCred(credentialId: Uint8Array, token: Uint8Array, callback: IIdmCallback): void
```

删除用户凭据信息。

**起始版本：** 8

**需要权限：** ohos.permission.MANAGE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| credentialId | Uint8Array | 是 | 凭证索引。 |
| token | Uint8Array | 是 | 身份验证令牌。 |
| callback | IIdmCallback | 是 | 回调对象，返回删除凭据的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid credentialId. |
| [12300101](../../apis-basic-services-kit/errorcode-account.md#12300101-凭据不正确) | The token is invalid. |
| [12300102](../../apis-basic-services-kit/errorcode-account.md#12300102-凭据不存在) | The credential does not exist. |

**示例：**

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

删除具有身份验证令牌的用户。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.MANAGE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | Uint8Array | 是 | 身份验证令牌。 |
| callback | IIdmCallback | 是 | 回调对象，返回删除用户的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300101](../../apis-basic-services-kit/errorcode-account.md#12300101-凭据不正确) | The token is invalid. |

**示例：**

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

获取认证信息。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.USE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;EnrolledCredInfo&gt;&gt; | 是 | 回调函数。如果成功，err为null，data为当前用户的所有已注册凭据信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 23+ |

**示例：**

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

## getAuthInfo

```TypeScript
getAuthInfo(authType: AuthType, callback: AsyncCallback<Array<EnrolledCredInfo>>): void
```

获取指定类型的认证信息。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.USE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | AuthType | 是 | 认证类型。 |
| callback | AsyncCallback&lt;Array&lt;EnrolledCredInfo&gt;&gt; | 是 | 回调函数，如果获取成功，err为null，data为当前用户指定类型的所有已注册凭据信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid authType. |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 23+ |

**示例：**

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

## getAuthInfo

```TypeScript
getAuthInfo(authType: AuthType): Promise<Array<EnrolledCredInfo>>
```

获取认证信息。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.USE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | AuthType | 是 | 认证类型，表示查询所有认证类型的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;EnrolledCredInfo&gt;&gt; | Promise对象，返回当前用户指定类型的所有已注册凭据信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid authType. |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 23+ |

**示例：**

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

## getAuthInfo

```TypeScript
getAuthInfo(options?: GetAuthInfoOptions): Promise<Array<EnrolledCredInfo>>
```

依据提供的可选参数，获取认证信息。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.USE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | GetAuthInfoOptions | 否 | 获取认证信息的可选参数集合。默认为空，表示查询当前用户所有已注册凭据信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;EnrolledCredInfo&gt;&gt; | Promise对象，返回当前用户指定类型的所有已注册凭据信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid options. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 23+ |

**示例：**

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

基于凭据类型，以及可选的账号标识，获取已注册的凭据ID。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.USE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | AuthType | 是 | 认证凭据类型 |
| accountId | number | 否 | 系统账号标识，默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回已注册的凭据ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid authType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 23+ |
| [12300102](../../apis-basic-services-kit/errorcode-account.md#12300102-凭据不存在) | The credential does not exist. |
| [12300106](../../apis-basic-services-kit/errorcode-account.md#12300106-认证类型不支持) | The authentication type is not supported. |

**示例：**

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

取消与指定回调关联的订阅记录，若未指定回调，则取消所有订阅记录。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;CredentialChangeInfo&gt; | 否 | 表示用于接收凭据变更事件的回调函数。默认为undefined，表示清除所有订阅记录；非undefined时，表示清除与该回调函数关联的订阅记录。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

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

订阅一种或多种类型的凭据变更事件，通过回调函数获取凭据变更信息。

**起始版本：** 23

**需要权限：** ohos.permission.USE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| credentialTypes | AuthType[] | 是 | 表示订阅的凭据类型集合。 |
| callback | Callback&lt;CredentialChangeInfo&gt; | 是 | 表示用于接收凭据变更事件的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | One or more credential types are invalid. |
| [12300106](../../apis-basic-services-kit/errorcode-account.md#12300106-认证类型不支持) | One or more credential types are not supported. |

**示例：**

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

打开会话，获取挑战值。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.MANAGE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Uint8Array&gt; | 是 | 回调函数。如果打开会话成功，err为null，data为挑战值；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |

**示例：**

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

## openSession

```TypeScript
openSession(accountId?: number): Promise<Uint8Array>
```

打开会话，获取挑战值（用于判断后续的身份认证场景是否处于该会话下，防止重放攻击）。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.MANAGE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 否 | 系统账号标识，默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回挑战值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found.<br>**适用版本：** 12+ |
| [12300008](../../apis-basic-services-kit/errorcode-account.md#12300008-受限的账号) | Restricted account.<br>**适用版本：** 12+ |

**示例：**

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

更新凭据。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.MANAGE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| credentialInfo | CredentialInfo | 是 | 指示凭据信息。 |
| callback | IIdmCallback | 是 | 回调对象，返回更新凭据的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid credentialInfo, i.e. authType or authSubType. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found.<br>**适用版本：** 12+ |
| [12300101](../../apis-basic-services-kit/errorcode-account.md#12300101-凭据不正确) | The token is invalid. |
| [12300102](../../apis-basic-services-kit/errorcode-account.md#12300102-凭据不存在) | The credential does not exist. |
| [12300106](../../apis-basic-services-kit/errorcode-account.md#12300106-认证类型不支持) | The authentication type is not supported. |
| [12300109](../../apis-basic-services-kit/errorcode-account.md#12300109-认证凭据录入更新等操作被取消) | The authentication, enrollment, or update operation is canceled. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The operation time out. |
| [12300116](../../apis-basic-services-kit/errorcode-account.md#12300116-凭证复杂度验证失败) | Credential complexity verification failed.<br>**适用版本：** 12+ |

**示例：**

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

