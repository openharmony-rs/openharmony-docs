# getAuthLockState

## getAuthLockState

```TypeScript
function getAuthLockState(authType: UserAuthType): Promise<AuthLockState>
```

查询指定认证类型的冻结状态，使用Promise异步回调。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-userAuth-function getAuthLockState(authType: UserAuthType): Promise<AuthLockState>--><!--Device-userAuth-function getAuthLockState(authType: UserAuthType): Promise<AuthLockState>-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 认证类型，用于指定查询的凭据类型。支持FACE（人脸）、FINGERPRINT（指纹）、PIN（密码）等。根据业务场景安全需求选择合适的认证类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AuthLockState&gt; | Promise对象，当查询成功时，返回值为指定认证类型的身份认证冻结状态。失败时报错。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |
| [12500005](../errorcode-useriam.md#12500005-认证类型不支持) | The authentication type is not supported. |
| [12500008](../errorcode-useriam.md#12500008-参数校验失败) | The parameter is out of range. |
| [12500010](../errorcode-useriam.md#12500010-该类型的凭据没有录入) | The type of credential has not been enrolled. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let queryType = userAuth.UserAuthType.PIN;
let authLockState : userAuth.AuthLockState = {
  isLocked : false,
  remainingAuthAttempts : 0,
  lockoutDuration : 0
}

userAuth.getAuthLockState(queryType)
  .then((result: userAuth.AuthLockState) => {
    authLockState = result;
    console.info('get auth lock state successfully.');
  })
  .catch((err: BusinessError) => {
    console.error(`get auth lock state failed, err code is : ${err?.code}, err message is : ${err?.message}`);
  })
```

ArkTS-Sta示例：

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

let queryType = userAuth.UserAuthType.PIN;
let authLockState : userAuth.AuthLockState = {
  isLocked : false,
  remainingAuthAttempts : 0,
  lockoutDuration : 0
}

userAuth.getAuthLockState(queryType)
  .then((result: userAuth.AuthLockState) => {
    authLockState = result;
    console.info('get auth lock state successfully.');
  })
  .catch((err) => {
    console.error(`get auth lock state failed, err code is : ${err.code}, err message is : ${err.message}`);
  })
```

