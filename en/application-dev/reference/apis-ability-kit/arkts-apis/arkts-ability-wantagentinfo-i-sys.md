# WantAgentInfo

```TypeScript
export interface WantAgentInfo
```

Defines the information required for triggering a WantAgent object. The information can be used as an input parameter in [getWantAgent](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#wantagentgetwantagent) to obtain a specified WantAgent object.

**Since:** 7

<!--Device-unnamed-export interface WantAgentInfo--><!--Device-unnamed-export interface WantAgentInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## userId

```TypeScript
userId?: number
```

User ID. Value range: greater than or equal to 0. Pass this parameter when a specific user needs to be specified. It applies to cross-user operation scenarios (for example, a system application manages applications of other users). If not passed, the default is the user ID of the caller.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-WantAgentInfo-userId?: int--><!--Device-WantAgentInfo-userId?: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
