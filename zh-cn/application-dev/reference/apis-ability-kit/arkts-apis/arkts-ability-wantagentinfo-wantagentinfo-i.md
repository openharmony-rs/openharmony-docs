# WantAgentInfo

定义触发WantAgent所需要的信息，可以作为 getWantAgent的入参创建指定的 WantAgent对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface WantAgentInfo--><!--Device-unnamed-export interface WantAgentInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## actionFlags

```TypeScript
actionFlags?: Array<abilityWantAgent.WantAgentFlags>
```

动作执行属性。

**类型：** Array&lt;abilityWantAgent.WantAgentFlags&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentInfo-actionFlags?: Array<abilityWantAgent.WantAgentFlags>--><!--Device-WantAgentInfo-actionFlags?: Array<abilityWantAgent.WantAgentFlags>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## actionType

```TypeScript
actionType?: abilityWantAgent.OperationType
```

动作类型。

**类型：** abilityWantAgent.OperationType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentInfo-actionType?: abilityWantAgent.OperationType--><!--Device-WantAgentInfo-actionType?: abilityWantAgent.OperationType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extraInfo

```TypeScript
extraInfo?: Record<string, RecordData>
```

启动应用的额外信息。 如果没有需要设置的额外信息，此常量可以留空。

**类型：** Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-WantAgentInfo-extraInfo?: Record<string, RecordData>--><!--Device-WantAgentInfo-extraInfo?: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extraInfos

```TypeScript
extraInfos?: Record<string, RecordData>
```

额外数据。推荐使用该属性替代extraInfo，设置该属性后，extraInfo不再生效。

**类型：** Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-WantAgentInfo-extraInfos?: Record<string, RecordData>--><!--Device-WantAgentInfo-extraInfos?: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## operationType

```TypeScript
operationType?: wantAgent.OperationType
```

动作类型。 从API version 7 开始支持，从API version 11 开始废弃，建议使用actionType&lt;sup&gt;11+&lt;/sup&gt;替代。

**类型：** wantAgent.OperationType

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 11

**替代接口：** [actionType](#actionType)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentInfo-operationType?: wantAgent.OperationType--><!--Device-WantAgentInfo-operationType?: wantAgent.OperationType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## requestCode

```TypeScript
requestCode: int
```

开发者自定义的请求码，用于标识将被执行的动作。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentInfo-requestCode: int--><!--Device-WantAgentInfo-requestCode: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## wantAgentFlags

```TypeScript
wantAgentFlags?: Array<wantAgent.WantAgentFlags>
```

动作执行属性。 从API version 7 开始支持，从API version 11 开始废弃，建议使用actionFlags&lt;sup&gt;11+&lt;/sup&gt;替代。

**类型：** Array&lt;wantAgent.WantAgentFlags&gt;

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 11

**替代接口：** [actionFlags](#actionFlags)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentInfo-wantAgentFlags?: Array<wantAgent.WantAgentFlags>--><!--Device-WantAgentInfo-wantAgentFlags?: Array<wantAgent.WantAgentFlags>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## wants

```TypeScript
wants: Array<Want>
```

将被执行的动作列表。wants数组为预留能力，当前只支持一个want。传入多个时只取wants数组的第一个成员。

**类型：** Array&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentInfo-wants: Array<Want>--><!--Device-WantAgentInfo-wants: Array<Want>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

