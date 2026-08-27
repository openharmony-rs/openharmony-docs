# AuthInstance

执行用户认证的对象。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [UserAuthInstance](arkts-userauthentication-userauth-userauthinstance-i.md)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## cancel

```TypeScript
cancel: () => void
```

取消认证。

> **说明：**
> 
> 使用获取到的[AuthInstance](#authinstance)对象调用该接口进行取消认证，此[AuthInstance](#authinstance)需要是正
> 在进行认证的对象。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [cancel](arkts-userauthentication-userauth-userauthinstance-i.md#cancel)

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;

try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  auth.cancel();
  console.info('cancel auth successfully.');
} catch (error) {
  console.error(`Failed to cancel auth. Code: ${error?.code}, message: ${error?.message}`);
}
```

## off

```TypeScript
off: (name: AuthEventKey) => void
```

取消订阅特定类型的认证事件。  
- **name**: 表示认证事件类型，取值为"result"时，取消订阅认证结果；取值为"tip"时，取消订阅认证过程中的提示信息，类型为  
[AuthEventKey](arkts-userauthentication-userauth-autheventkey-t.md)。

> **说明：**
> 
> 需要使用已经成功订阅事件的[AuthInstance](#authinstance)对象调用该接口进行取消订阅。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [off](arkts-userauthentication-userauth-userauthinstance-i.md#offresult)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | [AuthEventKey](arkts-userauthentication-userauth-autheventkey-t.md) | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  // 订阅认证结果。
  auth.on('result', {
    callback: (result: userAuth.AuthResultInfo) => {
      console.info(`result: ${result.result}`);
    }
  });
  // 取消订阅结果。
  auth.off('result');
  console.info('cancel subscribe authentication event successfully.');
} catch (error) {
  console.error(`Failed to cancel subscribe authentication event. Code: ${error?.code}, message: ${error?.message}`);
  // do error.
}
```

## on

```TypeScript
on: (name: AuthEventKey, callback: AuthEvent) => void
```

订阅指定类型的用户认证事件。  
- **name**: 表示认证事件类型，取值为"result"时，回调函数返回认证结果；取值为"tip"时，回调函数返回认证过程中的提示信息，类型为  
[AuthEventKey](arkts-userauthentication-userauth-autheventkey-t.md)。  
- **callback**: 认证接口的回调函数，用于返回认证结果或认证过程中的提示信息，类型为[AuthEvent](arkts-userauthentication-userauth-authevent-i.md)。

> **说明：**
> 
> 使用获取到的[AuthInstance](#authinstance)对象调用该接口进行订阅。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [on](arkts-userauthentication-userauth-userauthinstance-i.md#onresult)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | [AuthEventKey](arkts-userauthentication-userauth-autheventkey-t.md) | 是 |  |
| callback | [AuthEvent](arkts-userauthentication-userauth-authevent-i.md) | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;
try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  // 订阅认证结果。
  auth.on('result', {
    callback: (result: userAuth.AuthResultInfo) => {
      console.info(`result: ${result.result}`);
    }
  });
  // 订阅认证过程中的提示信息。
  auth.on('tip', {
    callback: (result: userAuth.TipInfo) => {
      switch (result.tip) {
        case userAuth.FaceTips.FACE_AUTH_TIP_TOO_BRIGHT:
          // do something;
          break;
        case userAuth.FaceTips.FACE_AUTH_TIP_TOO_DARK:
          // do something;
          break;
        default:
          // do others.
      }
    }
  } as userAuth.AuthEvent);
  auth.start();
  console.info('auth start successfully.');
} catch (error) {
  console.error(`Failed to auth. Code: ${error?.code}, message: ${error?.message}`);
  // do error.
}
```

## start

```TypeScript
start: () => void
```

开始认证。

> **说明：**
> 
> 使用获取到的[AuthInstance](#authinstance)对象调用该接口进行认证。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [start](arkts-userauthentication-userauth-userauthinstance-i.md#start)

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [12500001](../errorcode-useriam.md#12500001-认证不通过) | Authentication failed. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |
| [12500003](../errorcode-useriam.md#12500003-认证被取消) | The operation is canceled. |
| [12500004](../errorcode-useriam.md#12500004-认证操作超时) | The operation is time-out. |
| [12500005](../errorcode-useriam.md#12500005-认证类型不支持) | The authentication type is not supported. |
| [12500006](../errorcode-useriam.md#12500006-认证信任等级不支持) | The authentication trust level is not supported. |
| [12500007](../errorcode-useriam.md#12500007-认证服务繁忙) | The authentication task is busy. |
| [12500009](../errorcode-useriam.md#12500009-认证被锁定) | The authenticator is locked. |
| [12500010](../errorcode-useriam.md#12500010-该类型的凭据没有录入) | The type of credential has not been enrolled. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let challenge = new Uint8Array([1, 2, 3, 4, 5, 6, 7, 8]);
let authType = userAuth.UserAuthType.FACE;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;

try {
  let auth = userAuth.getAuthInstance(challenge, authType, authTrustLevel);
  auth.start();
  console.info('auth start successfully.');
} catch (error) {
  console.error(`Failed to auth. Code: ${error?.code}, message: ${error?.message}`);
}
```
