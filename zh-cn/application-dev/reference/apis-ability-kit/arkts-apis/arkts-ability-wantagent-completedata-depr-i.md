# CompleteData

表示主动触发WantAgent返回的数据。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [CompleteData](arkts-ability-wantagent-completedata-i.md#CompleteData)

<!--Device-wantAgent-export interface CompleteData--><!--Device-wantAgent-export interface CompleteData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extraInfo

```TypeScript
extraInfo?: { [key: string]: any }
```

额外数据。

**类型：** { [key: string]: any }

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [extraInfo](arkts-ability-wantagent-completedata-i.md#extraInfo)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompleteData-extraInfo?: { [key: string]: any }--><!--Device-CompleteData-extraInfo?: { [key: string]: any }-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## finalCode

```TypeScript
finalCode: number
```

触发wantAgent的请求代码。

**类型：** number

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [finalCode](arkts-ability-wantagent-completedata-i.md#finalCode)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompleteData-finalCode: number--><!--Device-CompleteData-finalCode: number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## finalData

```TypeScript
finalData: string
```

公共事件收集的最终数据。

**类型：** string

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [finalData](arkts-ability-wantagent-completedata-i.md#finalData)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompleteData-finalData: string--><!--Device-CompleteData-finalData: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## info

```TypeScript
info: WantAgent
```

触发的wantAgent。

**类型：** [WantAgent](arkts-ability-wantagent-depr-t.md)

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [info](arkts-ability-wantagent-completedata-i.md#info)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompleteData-info: WantAgent--><!--Device-CompleteData-info: WantAgent-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want: Want
```

存在的被触发的want。

**类型：** [Want](arkts-ability-app-ability-want-want-c.md)

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [want](arkts-ability-wantagent-completedata-i.md#want)

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CompleteData-want: Want--><!--Device-CompleteData-want: Want-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

