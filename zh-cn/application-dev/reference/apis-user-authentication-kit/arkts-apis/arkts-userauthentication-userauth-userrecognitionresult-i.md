# UserRecognitionResult

```TypeScript
interface UserRecognitionResult
```

用户识别结果。

**起始版本：** 26.0.1

<!--Device-userAuth-interface UserRecognitionResult--><!--Device-userAuth-interface UserRecognitionResult-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## authTrustLevel

```TypeScript
authTrustLevel?: AuthTrustLevel
```

认证信任等级。仅在status为MATCH时有效。

**类型：** [AuthTrustLevel](arkts-userauthentication-userauth-authtrustlevel-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-UserRecognitionResult-authTrustLevel?: AuthTrustLevel--><!--Device-UserRecognitionResult-authTrustLevel?: AuthTrustLevel-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## status

```TypeScript
status: UserRecognitionStatus
```

识别状态。

**类型：** [UserRecognitionStatus](arkts-userauthentication-userauth-userrecognitionstatus-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-UserRecognitionResult-status: UserRecognitionStatus--><!--Device-UserRecognitionResult-status: UserRecognitionStatus-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## userId

```TypeScript
userId: number
```

识别的系统用户ID，为非负整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-UserRecognitionResult-userId: int--><!--Device-UserRecognitionResult-userId: int-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## userInfo

```TypeScript
userInfo: string
```

识别用户的信息。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-UserRecognitionResult-userInfo: string--><!--Device-UserRecognitionResult-userInfo: string-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core
