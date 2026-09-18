# CompleteData

Describes the data returned by after wantAgent.trigger is called.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [CompleteData](arkts-ability-wantagent-completedata-i.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
```

## extraInfo

```TypeScript
extraInfo?: { [key: string]: any }
```

Extra data collected by the common event.

**Type:** { [key: string]: any }

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [extraInfo](arkts-ability-wantagent-completedata-i.md#extrainfo)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## finalCode

```TypeScript
finalCode: number
```

Request code used to trigger the WantAgent.

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [finalCode](arkts-ability-wantagent-completedata-i.md#finalcode)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## finalData

```TypeScript
finalData: string
```

Final data collected by the common event.

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [finalData](arkts-ability-wantagent-completedata-i.md#finaldata)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## info

```TypeScript
info: WantAgent
```

Triggered WantAgent.

**Type:** [WantAgent](arkts-ability-wantagent-depr-t.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [info](arkts-ability-wantagent-completedata-i.md#info)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want: Want
```

Existing Want that is triggered.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [want](arkts-ability-wantagent-completedata-i.md#want)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
