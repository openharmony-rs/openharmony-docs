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

User ID.

The value must be greater than or equal to 0.

The default value is the user ID of the caller.

This API can be used only in the stage model.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-WantAgentInfo-userId?: int--><!--Device-WantAgentInfo-userId?: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
