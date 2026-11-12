# getAvailableStatus

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## getAvailableStatus

```TypeScript
function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void
```

查询指定类型和等级的认证能力是否支持。该接口用于检查当前设备是否支持指定的认证类型和认证可信等级，帮助应用在发起认证前判断认证能力是否可用，从而避免不必要的认证不通过。若查询通过（无错误抛出），表示认证能力可用；若抛出错误，应用应根据错误码判断具体原因并采取相应处理。

错误码返回顺序说明：

如果未注册对应执行器，系统不支持该认证能力，需返回12500005。

如果已注册对应执行器，功能未禁用，但认证安全等级低于业务指定时，需返回12500006。

如果已注册对应执行器，功能未禁用，但用户未注册凭据时，需返回12500010。

如果已注册对应执行器，功能未禁用，但密码过期时，需返回12500013。

注意：

若用户注册的锁屏口令是4位PIN时，其认证可信等级为ATL3，调用该接口查询是否支持ATL4级别的密码认证时，需返回12500010。

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-userAuth-function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void--><!--Device-userAuth-function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md) | 是 | 认证类型。用于指定查询的认证类型，支持FACE（人脸）、FINGERPRINT（指纹）、PIN（密码）、COMPANION_DEVICE（伴随设备）。<br>**说明：** <br>从API版本11开始支持PIN查询。<br>从API版本26.0.0开始支持COMPANION_DEVICE查询。 |
| authTrustLevel | [AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md) | 是 | 认证信任等级。用于指定查询的认证可信等级，有效值为ATL1(10000)、ATL2(20000)、ATL3(30000)、ATL4(40000)。等级越高，对认证方案的活体检测能力要求越高。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |
| [12500005](../errorcode-useriam.md#12500005-认证类型不支持) | The authentication type is not supported. |
| [12500006](../errorcode-useriam.md#12500006-认证信任等级不支持) | The authentication trust level is not supported. |
| [12500010](../errorcode-useriam.md#12500010-该类型的凭据没有录入) | The type of credential has not been enrolled. |
| [12500013](../errorcode-useriam.md#12500013-密码过期) | Operation failed because of PIN expired.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  userAuth.getAvailableStatus(userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL3);
  console.info('current auth trust level is supported');
} catch (error) {
  console.error(`Failed to check auth trust level. Code: ${error?.code}, message: ${error?.message}`);
}
```
