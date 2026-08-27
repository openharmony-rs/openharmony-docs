# ContinueCallbackInfo（系统接口）

任务流转状态监听回调时返回的信息对象，包含state（流转状态）和info（流转详细信息）两个字段。state为ACTIVE表示流转处于激活状态，INACTIVE表示流转处于未激活状态。模型约束：此接口仅可在Stage模型下使用。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## info

```TypeScript
info: ContinuableInfo
```

表示当前任务的流转信息。

**类型：** ContinuableInfo

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: ContinueState
```

表示当前任务的流转状态，取值为ACTIVE（激活）或INACTIVE（未激活），根据任务实际流转状态设置。

**类型：** ContinueState

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。
