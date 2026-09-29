# ContinueResultInfo

```TypeScript
interface ContinueResultInfo
```

Describes the quick start result returned by the callback.

**Since:** 18

<!--Device-continueManager-interface ContinueResultInfo--><!--Device-continueManager-interface ContinueResultInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

## Modules to Import

```TypeScript
import { continueManager } from '@kit.AbilityKit';
```

## resultInfo

```TypeScript
resultInfo?: string
```

Description of the operation result.

This API can be used only in the stage model.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinueResultInfo-resultInfo?: string--><!--Device-ContinueResultInfo-resultInfo?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

## resultState

```TypeScript
resultState: ContinueStateCode
```

Status code of the operation result.

**Type:** [ContinueStateCode](arkts-ability-continuemanager-continuestatecode-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContinueResultInfo-resultState: ContinueStateCode--><!--Device-ContinueResultInfo-resultState: ContinueStateCode-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission
