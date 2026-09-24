# LocalWantAgentInfo (System API)

```TypeScript
export interface LocalWantAgentInfo
```

Defines the information required for triggering a local WantAgent object. The information can be used as an input parameter in [createLocalWantAgent](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent-sys.md#wantagentcreatelocalwantagent20) to obtain a local WantAgent object.

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## operationType

```TypeScript
operationType?: abilityWantAgent.OperationType
```

Type of the operation to execute.

**Type:** [abilityWantAgent.OperationType](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-wantagent.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## requestCode

```TypeScript
requestCode: number
```

Custom request code, which is used to identify the operation to execute.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## wants

```TypeScript
wants: Array<Want>
```

Array of all Want objects. Currently, only one Want object is supported. If multiple values are passed in, only the first member in the array is used.

**Type:** Array&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
