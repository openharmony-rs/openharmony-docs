# ArkTSScriptInfo

```TypeScript
interface ArkTSScriptInfo
```

The first parameter of the ArkTS script entry function of an app, used to receive the script context information passed by the system.

**Since:** 26.0.0

<!--Device-scriptManager-interface ArkTSScriptInfo--><!--Device-scriptManager-interface ArkTSScriptInfo-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## Modules to Import

```TypeScript
import { scriptManager } from '@kit.AbilityKit';
```

## context

```TypeScript
readonly context: Context
```

Context of the bound ability.

**Type:** [Context](arkts-ability-context-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ArkTSScriptInfo-readonly context: Context--><!--Device-ArkTSScriptInfo-readonly context: Context-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## requestCode

```TypeScript
readonly requestCode: string
```

Request code used to identify the current operation.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ArkTSScriptInfo-readonly requestCode: string--><!--Device-ArkTSScriptInfo-readonly requestCode: string-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core
