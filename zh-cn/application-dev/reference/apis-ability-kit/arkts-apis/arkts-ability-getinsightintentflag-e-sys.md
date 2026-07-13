# GetInsightIntentFlag（系统接口）

意图信息（[InsightIntentInfo](arkts-ability-insightintentinfo-i-sys.md)）的标识，用于
[getAllInsightIntentInfo](arkts-ability-getinsightintentinfobybundlename-f-sys.md#getinsightintentinfobybundlename-1)、
[getInsightIntentInfoByBundleName](arkts-ability-getinsightintentinfobybundlename-f-sys.md#getinsightintentinfobybundlename-1)和
[getInsightIntentInfoByIntentName](arkts-ability-getinsightintentinfobyintentname-f-sys.md#getinsightintentinfobyintentname-1)接口查询意图信息。

> **说明：**
>
> - 对于使用配置文件开发的意图，通过上述接口查询的全量信息和简要信息完全一致。
>
> - 对于使用装饰器开发的意图，通过上述接口查询的全量信息和简要信息存在差别，详见下表。
>
> 表1 全量意图信息与简要意图信息差别
>
> | 属性 | 全量意图信息是否包含 | 简要意图信息是否包含 |
> | -------- | -------- | -------- |
> | bundleName | 是 | 是 |
> | moduleName | 是 | 是 |
> | intentName | 是 | 是 |
> | domain | 是 | 否 |
> | intentVersion | 是 | 否 |
> | displayName | 是 | 是 |
> | displayDescription | 是 | 否 |
> | schema | 是 | 否 |
> | icon | 是 | 否 |
> | llmDescription | 是 | 否 |
> | keywords | 是 | 否 |
> | intentType | 是 | 是 |
> | subIntentInfo | 是 | 是 |
> | parameters | 是 | 是 |
> | entities | 否 | 否 |
> | developType<sup>23+</sup> | 是 | 是 |
> | subIntentInfoForConfiguration<sup>23+</sup> | 否 | 否 |

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## GET_FULL_INSIGHT_INTENT

```TypeScript
GET_FULL_INSIGHT_INTENT = 0x00000001
```

查询[InsightIntentInfo](arkts-ability-insightintentinfo-i-sys.md)中的除entities以外的全量意图信息，详见下表。查询entities信息需要使用
GET_ENTITY_INFO。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## GET_SUMMARY_INSIGHT_INTENT

```TypeScript
GET_SUMMARY_INSIGHT_INTENT = 0x00000002
```

查询[InsightIntentInfo](arkts-ability-insightintentinfo-i-sys.md)中的简要意图信息，详见下表。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## GET_ENTITY_INFO

```TypeScript
GET_ENTITY_INFO = 0x00000004
```

查询[EntityInfo](arkts-ability-entityinfo-i-sys.md)的信息，不可单独使用，必选结合GET_FULL_INSIGHT_INTENT或者
GET_SUMMARY_INSIGHT_INTENT使用。例如`GET_FULL_INSIGHT_INTENT | GET_ENTITY_INFO`。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

