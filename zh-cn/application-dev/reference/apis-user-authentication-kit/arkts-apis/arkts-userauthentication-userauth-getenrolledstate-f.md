# getEnrolledState

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

<a id="getenrolledstate"></a>
## getEnrolledState

```TypeScript
function getEnrolledState(authType: UserAuthType): EnrolledState
```

查询凭据注册的状态，以检测用户注册凭据的变更。该接口用于获取指定认证类型的凭据注册信息，包括凭据摘要和数量。应用可通过对比当前查询结果与之前保存的结果，判断用户是否新增或删除了凭据，从而采取相应的业务处理。

**起始版本：** 12

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-userAuth-function getEnrolledState(authType: UserAuthType): EnrolledState--><!--Device-userAuth-function getEnrolledState(authType: UserAuthType): EnrolledState-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | [UserAuthType](arkts-userauthentication-userauth-userauthtype-e.md) | 是 | 认证类型。用于指定查询的凭据类型，支持FACE（人脸）、FINGERPRINT（指纹）、PIN（密码）、COMPANION_DEVICE（伴随设备）。查询PIN时返回的是密码的整体状态，而非单个密码的数量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EnrolledState](arkts-userauthentication-userauth-enrolledstate-i.md) | 当查询成功时，返回值为用户注册凭据的状态。包含credentialDigest（凭据摘要）和credentialCount（凭据数量）。应用可保存credentialDigest值，后续查询时对比以检测凭据变更。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified. |
| [12500002](../errorcode-useriam.md#12500002-身份认证系统通用错误码) | General operation error. |
| [12500005](../errorcode-useriam.md#12500005-认证类型不支持) | The authentication type is not supported. |
| [12500010](../errorcode-useriam.md#12500010-该类型的凭据没有录入) | The type of credential has not been enrolled. |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let enrolledState = userAuth.getEnrolledState(userAuth.UserAuthType.FACE);
  console.info('get current enrolled state successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`get current enrolled state failed, Code is ${err?.code}, message is ${err?.message}`);
}

```

