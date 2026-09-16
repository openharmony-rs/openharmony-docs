# ContinueResultInfo

注册或注销回调函数返回的快速拉起结果，包含操作状态码和结果说明信息，用于应用获取跨端迁移快速拉起的执行结果。

**起始版本：** 18

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## 导入模块

```TypeScript
import { continueManager } from '@kit.AbilityKit';
```

## resultInfo

```TypeScript
resultInfo?: string
```

操作结果的说明，提供操作成功或失败的详细描述信息。

此接口仅可在Stage模型下使用。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

## resultState

```TypeScript
resultState: ContinueStateCode
```

操作结果状态码。

**类型：** [ContinueStateCode](arkts-ability-continuemanager-continuestatecode-e.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission
