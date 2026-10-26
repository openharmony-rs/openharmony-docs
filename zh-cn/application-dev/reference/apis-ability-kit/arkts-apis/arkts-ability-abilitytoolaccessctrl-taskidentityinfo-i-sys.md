# TaskIdentityInfo（系统接口）

```TypeScript
interface TaskIdentityInfo
```

用于生成任务标识的任务标识输入信息。

**起始版本：** 26.1.0

<!--Device-abilityToolAccessCtrl-interface TaskIdentityInfo--><!--Device-abilityToolAccessCtrl-interface TaskIdentityInfo-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## allowableDuration

```TypeScript
allowableDuration?: number
```

可信持有物认证凭据的有效时长。单位为：秒。取值范围：(0,60]。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-TaskIdentityInfo-allowableDuration?: number--><!--Device-TaskIdentityInfo-allowableDuration?: number-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## allowScreenLockExecution

```TypeScript
allowScreenLockExecution: boolean
```

任务是否允许在锁屏下执行。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-TaskIdentityInfo-allowScreenLockExecution: boolean--><!--Device-TaskIdentityInfo-allowScreenLockExecution: boolean-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## authToken

```TypeScript
authToken?: Uint8Array
```

可信持有物的认证凭据。

**类型：** Uint8Array

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-TaskIdentityInfo-authToken?: Uint8Array--><!--Device-TaskIdentityInfo-authToken?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## executeType

```TypeScript
executeType: ExecuteType
```

任务执行类别。

**类型：** [ExecuteType](arkts-ability-abilitytoolaccessctrl-executetype-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-TaskIdentityInfo-executeType: ExecuteType--><!--Device-TaskIdentityInfo-executeType: ExecuteType-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## taskExpireTime

```TypeScript
taskExpireTime: number
```

任务过期时间。单位为：秒。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-TaskIdentityInfo-taskExpireTime: number--><!--Device-TaskIdentityInfo-taskExpireTime: number-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## taskId

```TypeScript
taskId: string
```

任务ID。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-TaskIdentityInfo-taskId: string--><!--Device-TaskIdentityInfo-taskId: string-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。
