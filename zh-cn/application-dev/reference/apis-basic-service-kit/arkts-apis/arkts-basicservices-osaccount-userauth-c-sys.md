# UserAuth（系统接口）

用户认证类。

**起始版本：** 8

<!--Device-osAccount-class UserAuth--><!--Device-osAccount-class UserAuth-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

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

认证当前用户。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-UserAuth-auth(      challenge: Uint8Array,      authType: AuthType,      authTrustLevel: AuthTrustLevel,      callback: IUserAuthCallback    ): Uint8Array--><!--Device-UserAuth-auth(      challenge: Uint8Array,      authType: AuthType,      authTrustLevel: AuthTrustLevel,      callback: IUserAuthCallback    ): Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| challenge | Uint8Array | 是 | 指示挑战值，挑战值为一个随机数，用于提升安全性。 |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | 是 | 指示认证类型。 |
| authTrustLevel | [AuthTrustLevel](arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | 是 | 指示认证结果的信任级别。 |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | 是 | 回调对象，返回认证结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回取消的上下文ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid challenge, authType or authTrustLevel. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception.<br>**适用版本：** 12+ |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 20+ |
| 12300090 | Cross-device capability not supported.<br>**适用版本：** 20+ |
| 12300091 | Cross-device communication failed.<br>**适用版本：** 20+ |
| [12300101](../../apis-basic-services-kit/errorcode-account.md#12300101-凭据不正确) | The credential is incorrect. |
| [12300102](../../apis-basic-services-kit/errorcode-account.md#12300102-凭据不存在) | The credential does not exist. |
| [12300105](../../apis-basic-services-kit/errorcode-account.md#12300105-可信等级不支持) | The trust level is not supported. |
| [12300106](../../apis-basic-services-kit/errorcode-account.md#12300106-认证类型不支持) | The authentication type is not supported. |
| [12300109](../../apis-basic-services-kit/errorcode-account.md#12300109-认证凭据录入更新等操作被取消) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../../apis-basic-services-kit/errorcode-account.md#12300110-认证被锁定) | The authentication is locked. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The authentication time out. |
| [12300112](../../apis-basic-services-kit/errorcode-account.md#12300112-认证服务忙) | The authentication service is busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | The authentication service does not exist.<br>**适用版本：** 12+ |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The authentication service works abnormally.<br>**适用版本：** 12+ |
| [12300117](../../apis-basic-services-kit/errorcode-account.md#12300117-pin码过期) | PIN is expired.<br>**适用版本：** 12+ |
| 12300119 | Multi-factor authentication failed.<br>**适用版本：** 20+ |
| [12300120](../../apis-basic-services-kit/errorcode-account.md#12300120-凭据已失效) | The credentials are no longer valid.<br>**适用版本：** 23+ |
| 12300211 | Server unreachable.<br>**适用版本：** 12+ |

**示例：**

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

基于指定的挑战值、认证类型（如口令、人脸、指纹等）、认证可信等级以及可选参数（如账号标识、认证意图等）进行身份认证。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-UserAuth-auth(      challenge: Uint8Array,      authType: AuthType,      authTrustLevel: AuthTrustLevel,      options: AuthOptions,      callback: IUserAuthCallback    ): Uint8Array--><!--Device-UserAuth-auth(      challenge: Uint8Array,      authType: AuthType,      authTrustLevel: AuthTrustLevel,      options: AuthOptions,      callback: IUserAuthCallback    ): Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| challenge | Uint8Array | 是 | 指示挑战值，挑战值为一个随机数，用于防止重放攻击，提升安全性。 |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | 是 | 指示认证类型。 |
| authTrustLevel | [AuthTrustLevel](arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | 是 | 指示认证结果的信任级别。 |
| options | [AuthOptions](arkts-basicservices-osaccount-authoptions-i-sys.md) | 是 | 指示认证用户的可选参数集合。 |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | 是 | 回调对象，返回认证结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回取消的上下文ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid challenge, authType, authTrustLevel or options. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception. |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 20+ |
| 12300090 | Cross-device capability not supported.<br>**适用版本：** 20+ |
| 12300091 | Cross-device communication failed.<br>**适用版本：** 20+ |
| [12300101](../../apis-basic-services-kit/errorcode-account.md#12300101-凭据不正确) | The credential is incorrect. |
| [12300102](../../apis-basic-services-kit/errorcode-account.md#12300102-凭据不存在) | The credential does not exist. |
| [12300105](../../apis-basic-services-kit/errorcode-account.md#12300105-可信等级不支持) | The trust level is not supported. |
| [12300106](../../apis-basic-services-kit/errorcode-account.md#12300106-认证类型不支持) | The authentication type is not supported. |
| [12300109](../../apis-basic-services-kit/errorcode-account.md#12300109-认证凭据录入更新等操作被取消) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../../apis-basic-services-kit/errorcode-account.md#12300110-认证被锁定) | The authentication is locked. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The authentication timeout. |
| [12300112](../../apis-basic-services-kit/errorcode-account.md#12300112-认证服务忙) | The authentication service is busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | The authentication service does not exist. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The authentication service works abnormally. |
| [12300117](../../apis-basic-services-kit/errorcode-account.md#12300117-pin码过期) | PIN is expired. |
| 12300119 | Multi-factor authentication failed.<br>**适用版本：** 20+ |
| [12300120](../../apis-basic-services-kit/errorcode-account.md#12300120-凭据已失效) | The credentials are no longer valid.<br>**适用版本：** 23+ |
| 12300211 | Server unreachable. |

**示例：**

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

认证指定用户。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-UserAuth-authUser(      userId: int,      challenge: Uint8Array,      authType: AuthType,      authTrustLevel: AuthTrustLevel,      callback: IUserAuthCallback    ): Uint8Array--><!--Device-UserAuth-authUser(      userId: int,      challenge: Uint8Array,      authType: AuthType,      authTrustLevel: AuthTrustLevel,      callback: IUserAuthCallback    ): Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 指示用户身份。 |
| challenge | Uint8Array | 是 | 指示挑战值，挑战值为一个随机数，用于提升安全性。 |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | 是 | 指示认证类型。 |
| authTrustLevel | [AuthTrustLevel](arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | 是 | 指示认证结果的信任级别。 |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | 是 | 回调对象，返回认证结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回取消的上下文ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid challenge, authType or authTrustLevel. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found.<br>**适用版本：** 12+ |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception.<br>**适用版本：** 12+ |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 20+ |
| 12300090 | Cross-device capability not supported.<br>**适用版本：** 20+ |
| 12300091 | Cross-device communication failed.<br>**适用版本：** 20+ |
| [12300101](../../apis-basic-services-kit/errorcode-account.md#12300101-凭据不正确) | The credential is incorrect. |
| [12300102](../../apis-basic-services-kit/errorcode-account.md#12300102-凭据不存在) | The credential does not exist. |
| [12300105](../../apis-basic-services-kit/errorcode-account.md#12300105-可信等级不支持) | The trust level is not supported. |
| [12300106](../../apis-basic-services-kit/errorcode-account.md#12300106-认证类型不支持) | The authentication type is not supported. |
| [12300109](../../apis-basic-services-kit/errorcode-account.md#12300109-认证凭据录入更新等操作被取消) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../../apis-basic-services-kit/errorcode-account.md#12300110-认证被锁定) | The authentication is locked. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The authentication timeout. |
| [12300112](../../apis-basic-services-kit/errorcode-account.md#12300112-认证服务忙) | The authentication service is busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | The authentication service does not exist.<br>**适用版本：** 12+ |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The authentication service works abnormally.<br>**适用版本：** 12+ |
| [12300117](../../apis-basic-services-kit/errorcode-account.md#12300117-pin码过期) | PIN is expired.<br>**适用版本：** 12+ |
| 12300119 | Multi-factor authentication failed.<br>**适用版本：** 20+ |
| [12300120](../../apis-basic-services-kit/errorcode-account.md#12300120-凭据已失效) | The credentials are no longer valid.<br>**适用版本：** 23+ |
| 12300211 | Server unreachable.<br>**适用版本：** 12+ |

**示例：**

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

取消指定的认证操作。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-UserAuth-cancelAuth(contextID: Uint8Array): void--><!--Device-UserAuth-cancelAuth(contextID: Uint8Array): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contextID | Uint8Array | 是 | 指示身份验证上下文ID，此ID动态生成没有具体值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid contextId. |

**示例：**

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

创建用户认证的实例。

**起始版本：** 8

<!--Device-UserAuth-constructor()--><!--Device-UserAuth-constructor()-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例：**

```TypeScript
let userAuth = new osAccount.UserAuth();

```

## getAvailableStatus

```TypeScript
getAvailableStatus(authType: AuthType, authTrustLevel: AuthTrustLevel): number
```

获取指定认证类型和认证可信等级的认证能力的可用状态。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-UserAuth-getAvailableStatus(authType: AuthType, authTrustLevel: AuthTrustLevel): int--><!--Device-UserAuth-getAvailableStatus(authType: AuthType, authTrustLevel: AuthTrustLevel): int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | 是 | 认证类型。 |
| authTrustLevel | [AuthTrustLevel](arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | 是 | 认证的可信等级。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回认证能力的可用状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid authType or authTrustLevel. |
| [12300117](../../apis-basic-services-kit/errorcode-account.md#12300117-pin码过期) | PIN is expired. |

**示例：**

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

基于指定的请求信息获取属性。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-UserAuth-getProperty(request: GetPropertyRequest, callback: AsyncCallback<ExecutorProperty>): void--><!--Device-UserAuth-getProperty(request: GetPropertyRequest, callback: AsyncCallback<ExecutorProperty>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [GetPropertyRequest](arkts-basicservices-osaccount-getpropertyrequest-i-sys.md) | 是 | 请求信息，包括认证类型和属性类型列表。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;ExecutorProperty&gt; | 是 | 回调函数。如果获取成功，err为null，data为执行器属性信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid request. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found.<br>**适用版本：** 12+ |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 23+ |

**示例：**

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

## getProperty

```TypeScript
getProperty(request: GetPropertyRequest): Promise<ExecutorProperty>
```

基于指定的请求信息获取属性。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-UserAuth-getProperty(request: GetPropertyRequest): Promise<ExecutorProperty>--><!--Device-UserAuth-getProperty(request: GetPropertyRequest): Promise<ExecutorProperty>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [GetPropertyRequest](arkts-basicservices-osaccount-getpropertyrequest-i-sys.md) | 是 | 请求信息，包括认证类型和属性类型列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ExecutorProperty&gt; | Promise对象，返回执行器属性信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid request. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found.<br>**适用版本：** 12+ |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 23+ |

**示例：**

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

基于凭据id获取关联执行器的指定属性信息。使用Promise异步回调。

**起始版本：** 14

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-UserAuth-getPropertyByCredentialId(credentialId: Uint8Array, keys: Array<GetPropertyType>): Promise<ExecutorProperty>--><!--Device-UserAuth-getPropertyByCredentialId(credentialId: Uint8Array, keys: Array<GetPropertyType>): Promise<ExecutorProperty>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| credentialId | Uint8Array | 是 | 指示凭据索引。 |
| keys | Array&lt;GetPropertyType&gt; | 是 | 指示要查询的属性类型数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ExecutorProperty&gt; | Promise对象，返回执行器的属性信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid keys. |
| 12300020 | Device hardware abnormal.<br>**适用版本：** 23+ |
| [12300102](../../apis-basic-services-kit/errorcode-account.md#12300102-凭据不存在) | The credential does not exist. |

**示例：**

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

返回版本信息。

**起始版本：** 8

<!--Device-UserAuth-getVersion(): int--><!--Device-UserAuth-getVersion(): int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回版本信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例：**

```TypeScript
let userAuth = new osAccount.UserAuth();
let version: number = userAuth.getVersion();
console.info('getVersion version = ' + version);

```

## prepareRemoteAuth

```TypeScript
prepareRemoteAuth(remoteNetworkId: string): Promise<void>
```

准备远端认证。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-UserAuth-prepareRemoteAuth(remoteNetworkId: string): Promise<void>--><!--Device-UserAuth-prepareRemoteAuth(remoteNetworkId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| remoteNetworkId | string | 是 | 远端网络Id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | System service exception. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid remoteNetworkId. |
| 12300090 | Cross-device capability not supported.<br>**适用版本：** 20+ |
| 12300091 | Cross-device communication failed.<br>**适用版本：** 20+ |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | Operation timeout.<br>**适用版本：** 20+ |

**示例：**

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

设置可用于初始化算法的属性。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-UserAuth-setProperty(request: SetPropertyRequest, callback: AsyncCallback<void>): void--><!--Device-UserAuth-setProperty(request: SetPropertyRequest, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [SetPropertyRequest](arkts-basicservices-osaccount-setpropertyrequest-i-sys.md) | 是 | 请求信息，包括认证类型和要设置的密钥值。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。如果设置成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid request. |

**示例：**

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

## setProperty

```TypeScript
setProperty(request: SetPropertyRequest): Promise<void>
```

设置可用于初始化算法的属性。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-UserAuth-setProperty(request: SetPropertyRequest): Promise<void>--><!--Device-UserAuth-setProperty(request: SetPropertyRequest): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [SetPropertyRequest](arkts-basicservices-osaccount-setpropertyrequest-i-sys.md) | 是 | 请求信息，包括身份验证类型和要设置的密钥值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid request. |

**示例：**

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

