# getAuthLockState

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getAuthLockState

```TypeScript
function getAuthLockState(authType: UserAuthType): Promise<AuthLockState>
```

查询指定认证类型的冻结状态，使用Promise异步回调。

**起始版本：** 22

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md) | 是 | 认证类型，用于指定查询的凭据类型。支持FACE（人脸）、FINGERPRINT（指纹）、PIN（密码）等。根据业务场景安全需求选择合适的认证类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AuthLockState](arkts-userauthentication-userauth-authlockstate-i.md)&gt; | Promise对象，当查询成功时，返回值为指定认证类型的身份认证冻结状态。失败时报错。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |
| [12500005](../errorcode-useriam.md#12500005-认证类型不支持) | The authentication type is not supported. |
| [12500008](../errorcode-useriam.md#12500008-参数校验失败) | The parameter is out of range. |
| [12500010](../errorcode-useriam.md#12500010-该类型的凭据没有录入) | The type of credential has not been enrolled. |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let queryType = userAuth.UserAuthType.PIN;
let authLockState: userAuth.AuthLockState = {
  isLocked: false,
  remainingAuthAttempts: 0,
  lockoutDuration: 0
};

userAuth.getAuthLockState(queryType)
  .then((result: userAuth.AuthLockState) => {
    authLockState = result;
    console.info('get auth lock state successfully.');
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to get auth lock state. Code: ${err?.code}, message: ${err?.message}`);
  });
```
