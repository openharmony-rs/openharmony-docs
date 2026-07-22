# WantAgentInfo

定义触发WantAgent所需要的信息，可以作为[getWantAgent](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#wantagentgetwantagent)的入参创建指定的WantAgent对象。

**起始版本：** 7

<!--Device-unnamed-export interface WantAgentInfo--><!--Device-unnamed-export interface WantAgentInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## userId

```TypeScript
userId?: number
```

用户ID。

取值范围：大于等于0。

默认值为调用方所在用户ID。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WantAgentInfo-userId?: int--><!--Device-WantAgentInfo-userId?: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

