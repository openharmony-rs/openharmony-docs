# UserAuth

认证器对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [AuthInstance](arkts-userauthentication-userauth-authinstance-i.md)

<!--Device-userAuth-class UserAuth--><!--Device-userAuth-class UserAuth-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## auth

```TypeScript
auth(
      challenge: Uint8Array,
      authType: UserAuthType,
      authTrustLevel: AuthTrustLevel,
      callback: IUserAuthCallback
    ): Uint8Array
```

执行用户认证，使用回调函数返回结果。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [start](arkts-userauthentication-userauth-authinstance-i.md#start)

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

<!--Device-UserAuth-auth(
      challenge: Uint8Array,
      authType: UserAuthType,
      authTrustLevel: AuthTrustLevel,
      callback: IUserAuthCallback
    ): Uint8Array--><!--Device-UserAuth-auth(
      challenge: Uint8Array,
      authType: UserAuthType,
      authTrustLevel: AuthTrustLevel,
      callback: IUserAuthCallback
    ): Uint8Array-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| challenge | [Uint8Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8array-c.md) | 是 | 挑战值，可以传Uint8Array([])。 |
| authType | [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md) | 是 | 认证类型，当前支持FACE和FINGERPRINT。 |
| authTrustLevel | [AuthTrustLevel](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | 是 | 认证信任等级。 |
| callback | [IUserAuthCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | 是 | 回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Uint8Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8array-c.md) | ContextId，作为取消认证[cancelAuth](arkts-userauthentication-userauth-userauth-c.md#cancelauth-1)接口的入参。 |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let challenge = new Uint8Array([]);
auth.auth(challenge, userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL1, {
  onResult: (result, extraInfo) => {
    try {
      console.info(`auth onResult result = ${result}`);
      if (result == userAuth.ResultCode.SUCCESS) {
        // 此处添加认证成功逻辑。
      } else {
        // 此处添加认证失败逻辑。
      }
    } catch (error) {
      console.error(`auth onResult failed. Code: ${error?.code}, message: ${error?.message}`);
    }
  }
});

```

## cancelAuth

```TypeScript
cancelAuth(contextID: Uint8Array): number
```

表示通过contextID取消本次认证。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [cancel](arkts-userauthentication-userauth-authinstance-i.md#cancel)

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

<!--Device-UserAuth-cancelAuth(contextID: Uint8Array): number--><!--Device-UserAuth-cancelAuth(contextID: Uint8Array): number-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contextID | [Uint8Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8array-c.md) | 是 | 上下文的标识，通过[auth](arkts-userauthentication-userauth-userauth-c.md#auth-1)接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 取消认证的结果，结果为SUCCESS时表示取消成功，其他返回值参见[ResultCode](arkts-userauthentication-userauth-resultcode-e.md)。 |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

// contextId可通过auth接口获取，此处直接定义。
let contextId = new Uint8Array([0, 1, 2, 3, 4, 5, 6, 7]);
let auth = new userAuth.UserAuth();
let cancelCode = auth.cancelAuth(contextId);
if (cancelCode == userAuth.ResultCode.SUCCESS) {
  console.info('cancel auth successfully.');
} else {
  console.error('cancel auth failed.');
}

```

## constructor

```TypeScript
constructor()
```

创建认证器对象。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getAuthInstance](arkts-userauthentication-userauth-getauthinstance-f.md#getauthinstance-1)

<!--Device-UserAuth-constructor()--><!--Device-UserAuth-constructor()-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();

```

## getAvailableStatus

```TypeScript
getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): number
```

查询指定类型和等级的认证能力是否支持。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getAvailableStatus](arkts-userauthentication-userauth-getavailablestatus-f.md#getavailablestatus-1)

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

<!--Device-UserAuth-getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): number--><!--Device-UserAuth-getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): number-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md) | 是 | 认证类型，当前支持FACE和FINGERPRINT。 |
| authTrustLevel | [AuthTrustLevel](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | 是 | 认证信任等级。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 查询结果，结果为SUCCESS时表示支持，其他返回值参见[ResultCode](arkts-userauthentication-userauth-resultcode-e.md)。 |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let checkCode = auth.getAvailableStatus(userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL1);
if (checkCode == userAuth.ResultCode.SUCCESS) {
  console.info('check auth support successfully.');
} else {
  console.error(`check auth support failed, code = ${checkCode}`);
}

```

## getVersion

```TypeScript
getVersion(): number
```

获取认证器的版本信息。

**起始版本：** 8

**废弃版本：** 9

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

<!--Device-UserAuth-getVersion(): number--><!--Device-UserAuth-getVersion(): number-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 认证器版本信息。 |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let auth = new userAuth.UserAuth();
let version = auth.getVersion();
console.info(`auth version = ${version}`);

```

