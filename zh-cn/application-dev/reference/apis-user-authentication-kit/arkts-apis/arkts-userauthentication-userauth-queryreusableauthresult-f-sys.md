# queryReusableAuthResult（系统接口）

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## queryReusableAuthResult

```TypeScript
function queryReusableAuthResult(authParam: AuthParam): Uint8Array
```

查询是否有可复用的身份认证结果。该接口用于在发起认证前查询是否存在满足复用条件的认证结果，若存在则直接返回可复用的AuthToken，无需用户再次进行认证交互。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL

<!--Device-userAuth-function queryReusableAuthResult(authParam: AuthParam): Uint8Array--><!--Device-userAuth-function queryReusableAuthResult(authParam: AuthParam): Uint8Array-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authParam | [AuthParam](arkts-userauthentication-userauth-authparam-i-sys.md) | 是 | 用户认证相关参数。包含挑战值（challenge）、认证类型列表（authType）、认证信任等级（authTrustLevel）以及认证结果复用配置（reuseUnlockResult）。系统会根据这些参数判断是否存在满足条件的可复用认证结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 可复用的认证令牌（AuthToken）。若存在满足条件的可复用认证结果，返回AuthToken数据，最大长度为1024字节；若不存在，则抛出相应错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. Called by non-system application. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |
| [12500008](../errorcode-useriam.md#12500008-参数校验失败) | The parameter is out of range. |
| [12500017](../errorcode-useriam.md#12500017-复用身份认证结果失败) | Failed to reuse authentication result. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  const rand = cryptoFramework.createRandom();
  const len: number = 16;
  const randData: Uint8Array = rand?.generateRandomSync(len)?.data;
  const reuseUnlockResult: userAuth.ReuseUnlockResult = {
    reuseMode: userAuth.ReuseMode.AUTH_TYPE_RELEVANT,
    reuseDuration: userAuth.MAX_ALLOWABLE_REUSE_DURATION,
  }
  const authParam: userAuth.AuthParam = {
    challenge: randData,
    authType: [userAuth.UserAuthType.PIN],
    authTrustLevel: userAuth.AuthTrustLevel.ATL3,
    reuseUnlockResult: reuseUnlockResult,
  };
  let authToken = userAuth.queryReusableAuthResult(authParam);
  console.info('query reuse auth result successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`query reuse auth result failed. Code is ${err?.code}, message is ${err?.message}`);
}

```

