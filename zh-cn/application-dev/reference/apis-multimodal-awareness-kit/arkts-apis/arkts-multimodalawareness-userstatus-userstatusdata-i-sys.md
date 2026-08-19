# UserStatusData（系统接口）

表示用户状态数据。

**起始版本：** 26.0.0

<!--Device-userStatus-export interface UserStatusData--><!--Device-userStatus-export interface UserStatusData-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## errCode

```TypeScript
errCode: int
```

表示业务错误码。0表示成功，非0表示失败。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserStatusData-errCode: int--><!--Device-UserStatusData-errCode: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## feature

```TypeScript
feature: UserStatusFeature
```

表示用户状态检测功能类型。

**类型：** [UserStatusFeature](arkts-multimodalawareness-userstatus-userstatusfeature-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserStatusData-feature: UserStatusFeature--><!--Device-UserStatusData-feature: UserStatusFeature-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## result

```TypeScript
result: int
```

表示用户状态检测结果。0表示成功，非0表示失败。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserStatusData-result: int--><!--Device-UserStatusData-result: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: string
```

表示特定功能下的多阶段检测状态。该字符串取值已表明相应的检测状态，字符串最大长度是64。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserStatusData-status: string--><!--Device-UserStatusData-status: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

