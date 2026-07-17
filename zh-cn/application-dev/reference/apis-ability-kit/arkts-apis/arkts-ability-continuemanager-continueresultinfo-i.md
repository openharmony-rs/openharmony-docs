# ContinueResultInfo

注册或注销回调函数返回的快速拉起的结果。

**起始版本：** 18

<!--Device-continueManager-interface ContinueResultInfo--><!--Device-continueManager-interface ContinueResultInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## 导入模块

```TypeScript
import { continueManager } from '@kit.AbilityKit';
```

## resultInfo

```TypeScript
resultInfo?: string
```

操作结果的说明。

此接口仅可在Stage模型下使用。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinueResultInfo-resultInfo?: string--><!--Device-ContinueResultInfo-resultInfo?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## resultState

```TypeScript
resultState: ContinueStateCode
```

操作结果状态码。

**类型：** ContinueStateCode

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContinueResultInfo-resultState: ContinueStateCode--><!--Device-ContinueResultInfo-resultState: ContinueStateCode-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

