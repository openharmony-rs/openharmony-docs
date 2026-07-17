# DialogSessionInfo（系统接口）

提供会话信息，包括请求方信息、目标组件信息列表、其他参数。

**起始版本：** 11

<!--Device-dialogSession-export interface DialogSessionInfo--><!--Device-dialogSession-export interface DialogSessionInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dialogSession } from '@kit.AbilityKit';
```

## callerAbilityInfo

```TypeScript
callerAbilityInfo: DialogAbilityInfo
```

表示请求方组件信息。

**类型：** DialogAbilityInfo

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DialogSessionInfo-callerAbilityInfo: DialogAbilityInfo--><!--Device-DialogSessionInfo-callerAbilityInfo: DialogAbilityInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## parameters

```TypeScript
parameters?: Record<string, Object>
```

表示其他参数。

**类型：** Record<string, Object>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DialogSessionInfo-parameters?: Record<string, Object>--><!--Device-DialogSessionInfo-parameters?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## targetAbilityInfos

```TypeScript
targetAbilityInfos: Array<DialogAbilityInfo>
```

表示目标组件信息列表。

**类型：** Array<DialogAbilityInfo>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DialogSessionInfo-targetAbilityInfos: Array<DialogAbilityInfo>--><!--Device-DialogSessionInfo-targetAbilityInfos: Array<DialogAbilityInfo>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

