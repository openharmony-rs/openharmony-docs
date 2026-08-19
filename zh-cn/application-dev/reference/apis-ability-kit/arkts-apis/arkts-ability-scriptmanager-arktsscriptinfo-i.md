# ArkTSScriptInfo

应用的ArkTS脚本入口函数的第一个参数，用于接收系统传递的脚本上下文信息。

**起始版本：** 26.0.0

<!--Device-scriptManager-interface ArkTSScriptInfo--><!--Device-scriptManager-interface ArkTSScriptInfo-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## 导入模块

```TypeScript
import { scriptManager } from '@kit.AbilityKit';
```

## context

```TypeScript
readonly context: Context
```

绑定的Ability上下文。

**类型：** [Context](arkts-ability-context-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ArkTSScriptInfo-readonly context: Context--><!--Device-ArkTSScriptInfo-readonly context: Context-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## requestCode

```TypeScript
readonly requestCode: string
```

用于标识当前操作的请求码

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ArkTSScriptInfo-readonly requestCode: string--><!--Device-ArkTSScriptInfo-readonly requestCode: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

