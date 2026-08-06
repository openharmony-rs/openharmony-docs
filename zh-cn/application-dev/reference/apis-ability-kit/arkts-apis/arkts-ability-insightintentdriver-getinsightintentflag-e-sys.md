# GetInsightIntentFlag（系统接口）

意图信息（[InsightIntentInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_）的标识，用于 [getAllInsightIntentInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [getInsightIntentInfoByBundleName]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_和 [getInsightIntentInfoByIntentName]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_接口查询意图信息。 > **说明：** > > - 对于使用配置文件开发的意图，通过上述接口查询的全量信息和简要信息完全一致。 > > - 对于使用装饰器开发的意图，通过上述接口查询的全量信息和简要信息存在差别，详见下表。 > > 表1 全量意图信息与简要意图信息差别 > > | 属性 | 全量意图信息是否包含 | 简要意图信息是否包含 | > | -------- | -------- | -------- | > | bundleName | 是 | 是 | > | moduleName | 是 | 是 | > | intentName | 是 | 是 | > | domain | 是 | 否 | > | intentVersion | 是 | 否 | > | displayName | 是 | 是 | > | displayDescription | 是 | 否 | > | schema | 是 | 否 | > | icon | 是 | 否 | > | llmDescription | 是 | 否 | > | keywords | 是 | 否 | > | intentType | 是 | 是 | > | subIntentInfo | 是 | 是 | > | parameters | 是 | 是 | > | entities | 否 | 否 | > | developType\_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_23+\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_ | 是 | 是 | > | subIntentInfoForConfiguration\_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_23+\_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_ | 否 | 否 |

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-insightIntentDriver-enum GetInsightIntentFlag--><!--Device-insightIntentDriver-enum GetInsightIntentFlag-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## GET_FULL_INSIGHT_INTENT

```TypeScript
GET_FULL_INSIGHT_INTENT = 0x00000001
```

查询[InsightIntentInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中的除entities以外的全量意图信息，详见下表。查询entities信息需要使用 GET\_ENTITY\_INFO。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetInsightIntentFlag-GET_FULL_INSIGHT_INTENT = 0x00000001--><!--Device-GetInsightIntentFlag-GET_FULL_INSIGHT_INTENT = 0x00000001-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## GET_SUMMARY_INSIGHT_INTENT

```TypeScript
GET_SUMMARY_INSIGHT_INTENT = 0x00000002
```

查询[InsightIntentInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中的简要意图信息，详见下表。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetInsightIntentFlag-GET_SUMMARY_INSIGHT_INTENT = 0x00000002--><!--Device-GetInsightIntentFlag-GET_SUMMARY_INSIGHT_INTENT = 0x00000002-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## GET_ENTITY_INFO

```TypeScript
GET_ENTITY_INFO = 0x00000004
```

查询[EntityInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的信息，不可单独使用，必选结合GET\_FULL\_INSIGHT\_INTENT或者 GET\_SUMMARY\_INSIGHT\_INTENT使用。例如\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GetInsightIntentFlag-GET_ENTITY_INFO = 0x00000004--><!--Device-GetInsightIntentFlag-GET_ENTITY_INFO = 0x00000004-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

