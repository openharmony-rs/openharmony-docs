# ArkTSScriptInfo

```TypeScript
interface ArkTSScriptInfo
```

arkTS script info.

**Since:** 26.0.0

<!--Device-scriptManager-interface ArkTSScriptInfo--><!--Device-scriptManager-interface ArkTSScriptInfo-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## Modules to Import

```TypeScript
import { scriptManager } from '@kit.AbilityKit';
```

## toolCallId

```TypeScript
readonly toolCallId?: string
```

Tool call ID passed by the caller, used to associate this arkTS script invocation with a test step. It is undefined when the caller does not pass a tool call ID or passes an empty string.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.1.0.

<!--Device-ArkTSScriptInfo-readonly toolCallId?: string--><!--Device-ArkTSScriptInfo-readonly toolCallId?: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.
