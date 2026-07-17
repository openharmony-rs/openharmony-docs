# ContinueCallbackInfo（系统接口）

当前任务流转状态监听的回调信息，包含流转状态和流转信息。

**起始版本：** 11

<!--Device-distributedMissionManager-interface ContinueCallbackInfo--><!--Device-distributedMissionManager-interface ContinueCallbackInfo-End-->

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

<!--Device-ContinueCallbackInfo-info: ContinuableInfo--><!--Device-ContinueCallbackInfo-info: ContinuableInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: ContinueState
```

表示当前任务的流转状态。

**类型：** ContinueState

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinueCallbackInfo-state: ContinueState--><!--Device-ContinueCallbackInfo-state: ContinueState-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

