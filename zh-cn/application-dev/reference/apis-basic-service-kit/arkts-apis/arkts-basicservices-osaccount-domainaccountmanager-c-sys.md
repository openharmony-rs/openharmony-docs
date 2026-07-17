# DomainAccountManager

域账号管理类。

**起始版本：** 18

<!--Device-osAccount-class DomainAccountManager--><!--Device-osAccount-class DomainAccountManager-End-->

**系统能力：** SystemCapability.Account.OsAccount

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## auth

```TypeScript
static auth(domainAccountInfo: DomainAccountInfo, credential: Uint8Array, callback: IUserAuthCallback): void
```

认证指定的域账号。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-DomainAccountManager-static auth(domainAccountInfo: DomainAccountInfo, credential: Uint8Array, callback: IUserAuthCallback): void--><!--Device-DomainAccountManager-static auth(domainAccountInfo: DomainAccountInfo, credential: Uint8Array, callback: IUserAuthCallback): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | 是 | 指示域账号信息。 |
| credential | [Uint8Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8array-c.md) | 是 | 指示域账号的凭据。 |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | 是 | 指示认证结果回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid domainAccountInfo or credential. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Domain account does not exist. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception. |
| [12300101](../../apis-basic-services-kit/errorcode-account.md#12300101-凭据不正确) | Authentication failed. |
| [12300109](../../apis-basic-services-kit/errorcode-account.md#12300109-认证凭据录入更新等操作被取消) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../../apis-basic-services-kit/errorcode-account.md#12300110-认证被锁定) | The authentication is locked. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The authentication time out. |
| [12300112](../../apis-basic-services-kit/errorcode-account.md#12300112-认证服务忙) | The authentication service is busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | The account authentication service does not exist. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The account authentication service works abnormally. |
| 12300211 | Server unreachable. |

**示例：**

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

## auth

```TypeScript
static auth(
      domainAccountInfo: DomainAccountInfo,
      credential: Uint8Array,
      options: DomainAccountAuthOptions,
      callback: IUserAuthCallback): void
```

认证指定的域账号，支持指定认证选项，如服务器参数。使用callback异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-DomainAccountManager-static auth(
      domainAccountInfo: DomainAccountInfo,
      credential: Uint8Array,
      options: DomainAccountAuthOptions,
      callback: IUserAuthCallback): void--><!--Device-DomainAccountManager-static auth(
      domainAccountInfo: DomainAccountInfo,
      credential: Uint8Array,
      options: DomainAccountAuthOptions,
      callback: IUserAuthCallback): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | 是 | 指示域账号信息。 |
| credential | [Uint8Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8array-c.md) | 是 | 指示域账号的凭据。 |
| options | [DomainAccountAuthOptions](arkts-basicservices-osaccount-domainaccountauthoptions-i-sys.md) | 是 | 表示域账号认证的选项。 |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | 是 | 指示认证结果回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid domainAccountInfo or credential. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Domain account does not exist. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception. |
| [12300101](../../apis-basic-services-kit/errorcode-account.md#12300101-凭据不正确) | Authentication failed. |
| [12300109](../../apis-basic-services-kit/errorcode-account.md#12300109-认证凭据录入更新等操作被取消) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../../apis-basic-services-kit/errorcode-account.md#12300110-认证被锁定) | The authentication is locked. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The authentication time out. |
| [12300112](../../apis-basic-services-kit/errorcode-account.md#12300112-认证服务忙) | The authentication service is busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | The account authentication service does not exist. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The account authentication service works abnormally. |
| 12300211 | Server unreachable. |

**示例：**

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

弹框认证指定的域账号。

**起始版本：** 10

**需要权限：** 
- API版本10：ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-DomainAccountManager-static authWithPopup(callback: IUserAuthCallback): void--><!--Device-DomainAccountManager-static authWithPopup(callback: IUserAuthCallback): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | 是 | 指示认证结果回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 10+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | No domain account is bound. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception. |
| [12300101](../../apis-basic-services-kit/errorcode-account.md#12300101-凭据不正确) | Authentication failed. |
| [12300109](../../apis-basic-services-kit/errorcode-account.md#12300109-认证凭据录入更新等操作被取消) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../../apis-basic-services-kit/errorcode-account.md#12300110-认证被锁定) | The authentication is locked. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The authentication time out. |
| [12300112](../../apis-basic-services-kit/errorcode-account.md#12300112-认证服务忙) | The authentication service is busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | The account authentication service does not exist. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The account authentication service works abnormally. |
| 12300211 | Server unreachable.<br>**适用版本：** 11+ |

**示例：**

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

## authWithPopup

```TypeScript
static authWithPopup(localId: number, callback: IUserAuthCallback): void
```

弹框认证指定的域账号。

**起始版本：** 10

**需要权限：** 
- API版本10：ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-DomainAccountManager-static authWithPopup(localId: int, callback: IUserAuthCallback): void--><!--Device-DomainAccountManager-static authWithPopup(localId: int, callback: IUserAuthCallback): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localId | number | 是 | 指示绑定域账号的系统账号的本地标识。 |
| callback | [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | 是 | 指示认证结果回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 10+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid localId. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | No domain account is bound. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception. |
| [12300101](../../apis-basic-services-kit/errorcode-account.md#12300101-凭据不正确) | Authentication failed. |
| [12300109](../../apis-basic-services-kit/errorcode-account.md#12300109-认证凭据录入更新等操作被取消) | The authentication, enrollment, or update operation is canceled. |
| [12300110](../../apis-basic-services-kit/errorcode-account.md#12300110-认证被锁定) | The authentication is locked. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The authentication time out. |
| [12300112](../../apis-basic-services-kit/errorcode-account.md#12300112-认证服务忙) | The authentication service is busy. |
| [12300113](../../apis-basic-services-kit/errorcode-account.md#12300113-认证服务不存在) | The account authentication service does not exist. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The account authentication service works abnormally. |
| 12300211 | Server unreachable.<br>**适用版本：** 11+ |

**示例：**

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

获取当前域账号的业务访问令牌。使用callback异步回调。

**起始版本：** 11

<!--Device-DomainAccountManager-static getAccessToken(businessParams: Record<string, Object>, callback: AsyncCallback<Uint8Array>): void--><!--Device-DomainAccountManager-static getAccessToken(businessParams: Record<string, Object>, callback: AsyncCallback<Uint8Array>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| businessParams | Record<string, Object> | 是 | 指示业务参数，具体格式取决于域插件的实现要求。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<Uint8Array> | 是 | 指示结果回调。如果获取成功，err返回null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid business parameters. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Domain account not found. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception. |
| [12300014](../../apis-basic-services-kit/errorcode-account.md#12300014-域账号未认证) | The domain account is not authenticated. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The operation time out. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**示例：**

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

## getAccessToken

```TypeScript
static getAccessToken(businessParams: Record<string, Object>): Promise<Uint8Array>
```

查询当前域账号的业务访问令牌。使用Promise异步回调。

**起始版本：** 11

<!--Device-DomainAccountManager-static getAccessToken(businessParams: Record<string, Object>): Promise<Uint8Array>--><!--Device-DomainAccountManager-static getAccessToken(businessParams: Record<string, Object>): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| businessParams | Record<string, Object> | 是 | 指示业务参数，具体格式取决于域插件的实现要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Uint8Array> | Promise对象，返回业务访问令牌。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid business parameters. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Domain account not found. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception. |
| [12300014](../../apis-basic-services-kit/errorcode-account.md#12300014-域账号未认证) | The domain account is not authenticated. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The operation time out. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**示例：**

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

查询指定的域账号信息。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.GET_DOMAIN_ACCOUNTS

<!--Device-DomainAccountManager-static getAccountInfo(options: GetDomainAccountInfoOptions, callback: AsyncCallback<DomainAccountInfo>): void--><!--Device-DomainAccountManager-static getAccountInfo(options: GetDomainAccountInfoOptions, callback: AsyncCallback<DomainAccountInfo>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetDomainAccountInfoOptions](arkts-basicservices-osaccount-getdomainaccountinfooptions-i-sys.md) | 是 | 指示域账号信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<DomainAccountInfo> | 是 | 指示查询结果回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception. |
| [12300014](../../apis-basic-services-kit/errorcode-account.md#12300014-域账号未认证) | Not authenticated. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The operation time out. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**示例：**

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

## getAccountInfo

```TypeScript
static getAccountInfo(options: GetDomainAccountInfoOptions): Promise<DomainAccountInfo>
```

查询指定的域账号信息。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.GET_DOMAIN_ACCOUNTS

<!--Device-DomainAccountManager-static getAccountInfo(options: GetDomainAccountInfoOptions): Promise<DomainAccountInfo>--><!--Device-DomainAccountManager-static getAccountInfo(options: GetDomainAccountInfoOptions): Promise<DomainAccountInfo>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetDomainAccountInfoOptions](arkts-basicservices-osaccount-getdomainaccountinfooptions-i-sys.md) | 是 | 指示域账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<DomainAccountInfo> | Promise对象，返回指定的域账号信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception. |
| [12300014](../../apis-basic-services-kit/errorcode-account.md#12300014-域账号未认证) | Not authenticated. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The operation time out. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**示例：**

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

检查是否存在指定的域账号。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-DomainAccountManager-static hasAccount(domainAccountInfo: DomainAccountInfo, callback: AsyncCallback<boolean>): void--><!--Device-DomainAccountManager-static hasAccount(domainAccountInfo: DomainAccountInfo, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | 是 | 指示域账号信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 指示检查结果回调。true表示指定的域账号已存在；false表示指定的域账号不存在。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid domainAccountInfo. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception. |
| [12300014](../../apis-basic-services-kit/errorcode-account.md#12300014-域账号未认证) | Not authenticated. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The operation time out. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**示例：**

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

## hasAccount

```TypeScript
static hasAccount(domainAccountInfo: DomainAccountInfo): Promise<boolean>
```

检查是否存在指定的域账号。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-DomainAccountManager-static hasAccount(domainAccountInfo: DomainAccountInfo): Promise<boolean>--><!--Device-DomainAccountManager-static hasAccount(domainAccountInfo: DomainAccountInfo): Promise<boolean>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | 是 | 指示域账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回true表示指定的域账号已存在；返回false表示指定的域账号不存在。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid domainAccountInfo. |
| [12300013](../../apis-basic-services-kit/errorcode-account.md#12300013-网络异常) | Network exception. |
| [12300014](../../apis-basic-services-kit/errorcode-account.md#12300014-域账号未认证) | Not authenticated. |
| [12300111](../../apis-basic-services-kit/errorcode-account.md#12300111-认证超时) | The operation time out. |
| [12300114](../../apis-basic-services-kit/errorcode-account.md#12300114-认证服务异常) | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**示例：**

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

判断指定域账号是否登录超期。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

<!--Device-DomainAccountManager-static isAuthenticationExpired(domainAccountInfo: DomainAccountInfo): Promise<boolean>--><!--Device-DomainAccountManager-static isAuthenticationExpired(domainAccountInfo: DomainAccountInfo): Promise<boolean>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | 是 | 指示域账号信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回true表示指定的域账号已登录超期；返回false表示指定的域账号未登录超期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Domain account not found. |

**示例：**

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

注册域插件。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-DomainAccountManager-static registerPlugin(plugin: DomainPlugin): void--><!--Device-DomainAccountManager-static registerPlugin(plugin: DomainPlugin): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| plugin | [DomainPlugin](arkts-basicservices-osaccount-domainplugin-i-sys.md) | 是 | 指示域插件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| 12300201 | The domain plugin has been registered. |

**示例：**

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

注销域插件。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-DomainAccountManager-static unregisterPlugin(): void--><!--Device-DomainAccountManager-static unregisterPlugin(): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

**示例：**

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

更新指定域账号的令牌，空令牌表示目标域账号的令牌失效。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-DomainAccountManager-static updateAccountToken(
      domainAccountInfo: DomainAccountInfo,
      token: Uint8Array,
      callback: AsyncCallback<void>
    ): void--><!--Device-DomainAccountManager-static updateAccountToken(
      domainAccountInfo: DomainAccountInfo,
      token: Uint8Array,
      callback: AsyncCallback<void>
    ): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | 是 | 指示域账号信息。 |
| token | [Uint8Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8array-c.md) | 是 | 指示域账号的令牌。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。如果更新成功，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid token. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

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

## updateAccountToken

```TypeScript
static updateAccountToken(domainAccountInfo: DomainAccountInfo, token: Uint8Array): Promise<void>
```

更新指定域账号的令牌，空令牌表示目标域账号的令牌失效。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_LOCAL_ACCOUNTS

<!--Device-DomainAccountManager-static updateAccountToken(domainAccountInfo: DomainAccountInfo, token: Uint8Array): Promise<void>--><!--Device-DomainAccountManager-static updateAccountToken(domainAccountInfo: DomainAccountInfo, token: Uint8Array): Promise<void>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainAccountInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | 是 | 指示域账号信息。 |
| token | [Uint8Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8array-c.md) | 是 | 指示域账号的令牌。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid token. |
| [12300003](../../apis-basic-services-kit/errorcode-account.md#12300003-账号不存在) | Account not found. |

**示例：**

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

