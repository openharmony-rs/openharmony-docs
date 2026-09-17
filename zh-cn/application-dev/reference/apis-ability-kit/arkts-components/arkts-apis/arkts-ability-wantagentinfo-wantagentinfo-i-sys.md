# WantAgentInfo

WantAgentInfo用于定义触发WantAgent所需要的信息，可以作为[getWantAgent](../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#wantagentgetwantagent)的入参创建指定的WantAgent对象。适用于需要延迟执行Ability启动、发送公共事件等场景，支持自定义请求码和动作执行属性，帮助开发者灵活控制WantAgent的行为。

**起始版本：** 7

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## userId

```TypeScript
userId?: number
```

用户ID。取值范围：大于等于0。当需要指定特定用户时传入此参数，适用于跨用户操作场景（如系统应用管理其他用户的应用）。不传入时默认为调用方所在用户ID。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。
