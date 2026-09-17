# CompleteData

Describes the data returned by the operation of proactive triggering a WantAgent object.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { wantAgent, WantAgent } from '@kit.AbilityKit';
```

## extraInfo

```TypeScript
extraInfo?: Record<string, Object>
```

Extra information.

**Type:** Record&lt;string, Object&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## finalCode

```TypeScript
finalCode: number
```

Request code that triggers the WantAgent object.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## finalData

```TypeScript
finalData: string
```

Final data collected by the common event.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## info

```TypeScript
info: WantAgent
```

WantAgent object that is triggered.

**Type:** [WantAgent](arkts-ability-wantagent-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want: Want
```

Existing Want that is triggered.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
