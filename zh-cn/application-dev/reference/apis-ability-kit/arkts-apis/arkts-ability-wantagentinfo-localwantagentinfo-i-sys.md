# LocalWantAgentInfo（系统接口）

定义触发本地WantAgent所需要的信息，可以作为[createLocalWantAgent](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent-sys.md#wantagentcreatelocalwantagent20)的入参创建指定的本地WantAgent对象。

**起始版本：** 20

<!--Device-unnamed-export interface LocalWantAgentInfo--><!--Device-unnamed-export interface LocalWantAgentInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## operationType

```TypeScript
operationType?: abilityWantAgent.OperationType
```

将被执行的动作类型。

**类型：** abilityWantAgent.OperationType

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalWantAgentInfo-operationType?: abilityWantAgent.OperationType--><!--Device-LocalWantAgentInfo-operationType?: abilityWantAgent.OperationType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## requestCode

```TypeScript
requestCode: number
```

开发者自定义的请求码，用于标识将被执行的动作。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalWantAgentInfo-requestCode: int--><!--Device-LocalWantAgentInfo-requestCode: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## wants

```TypeScript
wants: Array<Want>
```

将被执行的动作列表。当前只支持一个want。传入多个时只取wants数组的第一个成员。

**类型：** Array&lt;Want&gt;

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LocalWantAgentInfo-wants: Array<Want>--><!--Device-LocalWantAgentInfo-wants: Array<Want>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

