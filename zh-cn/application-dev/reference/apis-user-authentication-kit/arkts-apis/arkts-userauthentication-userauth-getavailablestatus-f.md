# getAvailableStatus

## getAvailableStatus

```TypeScript
function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void
```

查询指定类型和等级的认证能力是否支持。该接口用于检查当前设备是否支持指定的认证类型和认证可信等级，帮助应用在发起认证前判断认证能力是否可用，从而避免不必要的认证不通过。若查询通过（无错误抛出），表示认证能力可用；若抛出错误，应用应 根据错误码判断具体原因并采取相应处理。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-userAuth-function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void--><!--Device-userAuth-function getAvailableStatus(authType: UserAuthType, authTrustLevel: AuthTrustLevel): void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 认证类型。用于指定查询的认证类型，支持FACE（人脸）、FINGERPRINT（指纹）、PIN（密码）、COMPANION\_\_\_ESCAPED\_UNDERSCORE\_\_\_DEVICE（伴随设备）。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明**：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_从API版本11开始支持PIN查询。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_从API版本26.0.0开始支持COMPANION\_\_\_ESCAPED\_UNDERSCORE\_\_\_DEVICE查询。 |
| authTrustLevel | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 认证信任等级。用于指定查询的认证可信等级，有效值为ATL1(10000)、ATL2(20000)、ATL3(30000)、ATL4(40000)。等级越高，对认证方案的活体检测能力要求越高。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_1. Mandatory parameters are left unspecified. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |
| [12500005](../errorcode-useriam.md#12500005-认证类型不支持) | The authentication type is not supported. |
| [12500006](../errorcode-useriam.md#12500006-认证信任等级不支持) | The authentication trust level is not supported. |
| [12500010](../errorcode-useriam.md#12500010-该类型的凭据没有录入) | The type of credential has not been enrolled. |
| [12500013](../errorcode-useriam.md#12500013-密码过期) | Operation failed because of PIN expired.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';

try {
  userAuth.getAvailableStatus(userAuth.UserAuthType.FACE, userAuth.AuthTrustLevel.ATL3);
  console.info('current auth trust level is supported');
} catch (error) {
  console.error(`current auth trust level is not supported. Code: ${error?.code}, message: ${error?.message}`);
}
```

