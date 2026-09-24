# InsightIntentInfo (System API)

```TypeScript
interface InsightIntentInfo
```

Defines the intent information, which is the specific parameter configuration of the intent in the device.

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## developType

```TypeScript
readonly developType?: DevelopType
```

Development mode of the intent.

**Type:** [DevelopType](arkts-ability-insightintentdriver-developtype-e-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## displayDescription

```TypeScript
readonly displayDescription: string
```

Description of the intent displayed in the InsightIntent framework.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## displayName

```TypeScript
readonly displayName: string
```

Name of the intent displayed in the InsightIntent framework.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## domain

```TypeScript
readonly domain: string
```

Vertical domain of the intent. It is used to categorize intents by vertical fields (for example, video, music, and games). For details about the value range, see the vertical domain fields in [smart distribution features in different vertical domains](https://developer.huawei.com/consumer/en/doc/service/intents-ai-distribution-characteristic-0000001901922213#section2656133582215).

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## entities

```TypeScript
readonly entities: Array<EntityInfo>
```

Entity information contained in the intent.

**Type:** Array&lt;[EntityInfo](arkts-ability-insightintentdriver-entityinfo-i-sys.md)&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## icon

```TypeScript
readonly icon: string
```

Icon of the intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## intentName

```TypeScript
readonly intentName: string
```

Intent name.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## intentType

```TypeScript
readonly intentType: InsightIntentType
```

Type of intent defined by the intent decorator.

**NOTE:** 

For intents developed using a configuration file, the return value of this field is @InsightIntentEntry by default.

**Type:** [InsightIntentType](arkts-ability-insightintentdriver-insightintenttype-e-sys.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## intentVersion

```TypeScript
readonly intentVersion: string
```

Version number of the intent. It is used to distinguish and manage intents when their capabilities evolve.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## keywords

```TypeScript
readonly keywords: string[]
```

Search keywords for the intent.

**Type:** string[]

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## llmDescription

```TypeScript
readonly llmDescription: string
```

Function of an intent, which helps large language models understand the intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## moduleName

```TypeScript
readonly moduleName: string
```

Module name.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## parameters

```TypeScript
readonly parameters: Record<string, Object>
```

Data format of intent parameters, which is used to define the input data format during intent calls.

**Type:** Record&lt;string, Object&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## result

```TypeScript
readonly result: Record<string, Object>
```

Execution result returned.

**Type:** Record&lt;string, Object&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## schema

```TypeScript
readonly schema: string
```

Standard intent name. If an intent in the standard intent list matches both the **schema** and **intentVersion** fields, it is processed as a standard intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## subIntentInfo

```TypeScript
readonly subIntentInfo: LinkIntentInfo | PageIntentInfo | FunctionIntentInfo | FormIntentInfo | EntryIntentInfo
```

Intent information for specific intent decorators.

**NOTE:** 

For intents developed using a configuration file, the return value of this field is [EntryIntentInfo](arkts-ability-insightintentdriver-entryintentinfo-i-sys.md) by default.

**Type:** [LinkIntentInfo](arkts-ability-insightintentdriver-linkintentinfo-i-sys.md) &#124; [PageIntentInfo](arkts-ability-insightintentdriver-pageintentinfo-i-sys.md) &#124; [FunctionIntentInfo](arkts-ability-insightintentdriver-functionintentinfo-i-sys.md) &#124; [FormIntentInfo](arkts-ability-insightintentdriver-formintentinfo-i-sys.md) &#124; [EntryIntentInfo](arkts-ability-insightintentdriver-entryintentinfo-i-sys.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## subIntentInfoForConfiguration

```TypeScript
readonly subIntentInfoForConfiguration?: SubIntentInfoForConfiguration
```

Unique information about the intent developed using a configuration file.

**Type:** [SubIntentInfoForConfiguration](arkts-ability-insightintentdriver-subintentinfoforconfiguration-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
