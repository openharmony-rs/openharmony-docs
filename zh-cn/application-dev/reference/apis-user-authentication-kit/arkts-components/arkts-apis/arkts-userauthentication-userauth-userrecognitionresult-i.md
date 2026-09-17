# UserRecognitionResult

用户识别结果。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## authTrustLevel

```TypeScript
authTrustLevel?: AuthTrustLevel
```

认证信任级别。仅在状态为[MATCH](arkts-userauthentication-userauth-userrecognitionstatus-e.md#match)时有效。具体取值请参见[AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md)。

**类型：** [AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## status

```TypeScript
status: UserRecognitionStatus
```

识别状态。取值请参见[UserRecognitionStatus](arkts-userauthentication-userauth-userrecognitionstatus-e.md)。

**类型：** [UserRecognitionStatus](arkts-userauthentication-userauth-userrecognitionstatus-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## userId

```TypeScript
userId: number
```

识别出的用户ID，非负整数。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## userInfo

```TypeScript
userInfo: string
```

识别出的用户信息。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core
