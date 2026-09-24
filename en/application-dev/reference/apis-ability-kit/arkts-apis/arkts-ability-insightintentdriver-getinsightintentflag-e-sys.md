# GetInsightIntentFlag (System API)

```TypeScript
enum GetInsightIntentFlag
```

Enumerates the flags of intent information ([InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md)). It is used in [getAllInsightIntentInfo](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md), [getInsightIntentInfoByBundleName](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md), and [getInsightIntentInfoByIntentName](arkts-ability-insightintentdriver-getinsightintentinfobyintentname-f-sys.md).

> **NOTE:** 
> 
> - For intents developed using a configuration file, the full and brief information queried through the preceding APIs are the same.
> 
> - For intents developed using a decorator, the full and brief information queried through the preceding APIs are different, as described below.
> 
> Table 1 Differences between full intent information and brief intent information
> 
> | Name| Included in Full Intent Information| Included in Brief Intent Information|
> | -------- | -------- | -------- |
> | bundleName | Yes| Yes|
> | moduleName | Yes| Yes|
> | intentName | Yes| Yes|
> | domain | Yes| No|
> | intentVersion | Yes| No|
> | displayName | Yes| Yes|
> | displayDescription | Yes| No|
> | schema | Yes| No|
> | icon | Yes| No|
> | llmDescription | Yes| No|
> | keywords | Yes| No|
> | intentType | Yes| Yes|
> | subIntentInfo | Yes| Yes|
> | parameters | Yes| Yes|
> | entities | No| No|
> | developType&lt;sup&gt;23+&lt;/sup&gt; | Yes| Yes|
> | subIntentInfoForConfiguration&lt;sup&gt;23+&lt;/sup&gt; | No| No|

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## GET_FULL_INSIGHT_INTENT

```TypeScript
GET_FULL_INSIGHT_INTENT = 0x00000001
```

Used to query all intent information (except entities) in [InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md). To query entities information, use **GET_ENTITY_INFO**.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## GET_SUMMARY_INSIGHT_INTENT

```TypeScript
GET_SUMMARY_INSIGHT_INTENT = 0x00000002
```

Used to query brief intent information in [InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## GET_ENTITY_INFO

```TypeScript
GET_ENTITY_INFO = 0x00000004
```

Used to query [EntityInfo](arkts-ability-insightintentdriver-entityinfo-i-sys.md). It must be used together with **GET_FULL_INSIGHT_INTENT** or **GET_SUMMARY_INSIGHT_INTENT**. Example usage: `GET_FULL_INSIGHT_INTENT | GET_ENTITY_INFO`.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
