# LocalWantAgentInfo (System API)

```TypeScript
export interface LocalWantAgentInfo
```

Defines the information required for triggering a local WantAgent object. The information can be used as an input parameter in [createLocalWantAgent](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent-sys.md#wantagentcreatelocalwantagent20) to obtain a local WantAgent object.

**Since:** 20

<!--Device-unnamed-export interface LocalWantAgentInfo--><!--Device-unnamed-export interface LocalWantAgentInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## operationType

```TypeScript
operationType?: abilityWantAgent.OperationType
```

Type of the action that will be executed, used to specify the trigger mode of the WantAgent (for example, starting an ability or sending an event). For details about the values, see the OperationType enum description.

**Type:** [abilityWantAgent.OperationType](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-wantagent.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-LocalWantAgentInfo-operationType?: abilityWantAgent.OperationType--><!--Device-LocalWantAgentInfo-operationType?: abilityWantAgent.OperationType-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## requestCode

```TypeScript
requestCode: number
```

Request code defined by the developer, used to identify the action that will be executed, so that the corresponding action can be identified and matched by this request code later. A unique value is recommended to avoid confusion.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-LocalWantAgentInfo-requestCode: int--><!--Device-LocalWantAgentInfo-requestCode: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## wants

```TypeScript
wants: Array<Want>
```

List of actions that will be executed. Currently, only one Want is supported. When multiple Wants are passed in, the system uses only the first member of the wants array and ignores the others.

**Type:** Array&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-LocalWantAgentInfo-wants: Array<Want>--><!--Device-LocalWantAgentInfo-wants: Array<Want>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
