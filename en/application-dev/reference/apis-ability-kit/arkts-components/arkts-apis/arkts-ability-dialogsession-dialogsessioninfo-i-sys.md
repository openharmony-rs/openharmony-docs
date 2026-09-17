# DialogSessionInfo (System API)

Provides session information, including the requester information, target ability information list, and other parameters.

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { dialogSession } from '@kit.AbilityKit';
```

## callerAbilityInfo

```TypeScript
callerAbilityInfo: DialogAbilityInfo
```

Ability information of the requester.

**Type:** [DialogAbilityInfo](arkts-ability-dialogsession-dialogabilityinfo-i-sys.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## parameters

```TypeScript
parameters?: Record<string, Object>
```

Other parameters.

**Type:** Record&lt;string, Object&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## targetAbilityInfos

```TypeScript
targetAbilityInfos: Array<DialogAbilityInfo>
```

List of target ability information.

**Type:** Array&lt;[DialogAbilityInfo](arkts-ability-dialogsession-dialogabilityinfo-i-sys.md)&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
