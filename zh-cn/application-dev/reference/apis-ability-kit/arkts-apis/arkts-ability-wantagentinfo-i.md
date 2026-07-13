# WantAgentInfo

定义触发WantAgent所需要的信息，可以作为
[getWantAgent](../../../../reference/apis-ability-kit/js-apis-app-ability-wantAgent.md#wantagentgetwantagent)的入参创建指定的
WantAgent对象。

**起始版本：** 7

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## actionFlags

```TypeScript
actionFlags?: Array<abilityWantAgent.WantAgentFlags>
```

动作执行属性。

**类型：** Array<abilityWantAgent.WantAgentFlags>

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## actionType

```TypeScript
actionType?: abilityWantAgent.OperationType
```

动作类型。

**类型：** abilityWantAgent.OperationType

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extraInfo

```TypeScript
extraInfo?: { [key: string]: any }
```

额外数据。

**类型：** { [key: string]: any }

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extraInfos

```TypeScript
extraInfos?: Record<string, Object>
```

额外数据。推荐使用该属性替代extraInfo，设置该属性后，extraInfo不再生效。

**类型：** Record<string, Object>

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## operationType

```TypeScript
operationType?: wantAgent.OperationType
```

动作类型。

从API version 7 开始支持，从API version 11 开始废弃，建议使用actionType<sup>11+</sup>替代。

**类型：** wantAgent.OperationType

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [actionType](arkts-ability-wantagentinfo-i.md#actiontype)

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## requestCode

```TypeScript
requestCode: number
```

开发者自定义的请求码，用于标识将被执行的动作。

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## wantAgentFlags

```TypeScript
wantAgentFlags?: Array<wantAgent.WantAgentFlags>
```

动作执行属性。

从API version 7 开始支持，从API version 11 开始废弃，建议使用actionFlags<sup>11+</sup>替代。

**类型：** Array<wantAgent.WantAgentFlags>

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [actionFlags](arkts-ability-wantagentinfo-i.md#actionflags)

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## wants

```TypeScript
wants: Array<Want>
```

将被执行的动作列表。wants数组为预留能力，当前只支持一个want。传入多个时只取wants数组的第一个成员。

**类型：** Array<Want>

**起始版本：** 7

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

