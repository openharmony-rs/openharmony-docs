# Want

```TypeScript
export declare interface Want
```

Want is a carrier for information transfer between objects (application components). Want can be used as a parameter of [startAbility](arkts-ability-uiabilitycontext-c.md#startability1) to specify a startup target and information that needs to be carried during startup, for example, **bundleName** and **abilityName**, which respectively indicate the bundle name of the target ability and the ability name in the bundle. When ability A needs to start ability B and transfer some data to ability B, it can use Want a carrier to transfer the data.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [Want](arkts-ability-app-ability-want-want-c.md)

<!--Device-unnamed-export declare interface Want--><!--Device-unnamed-export declare interface Want-End-->

**System capability:** SystemCapability.Ability.AbilityBase

## abilityName

```TypeScript
abilityName?: string
```

ability name

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [abilityName](arkts-ability-app-ability-want-want-c.md#abilityname)

<!--Device-Want-abilityName?: string--><!--Device-Want-abilityName?: string-End-->

**System capability:** SystemCapability.Ability.AbilityBase

## action

```TypeScript
action?: string
```

The description of an action in an want.

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [action](arkts-ability-app-ability-want-want-c.md#action)

<!--Device-Want-action?: string--><!--Device-Want-action?: string-End-->

**System capability:** SystemCapability.Ability.AbilityBase

## bundleName

```TypeScript
bundleName?: string
```

bundle name

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [bundleName](arkts-ability-app-ability-want-want-c.md#bundlename)

<!--Device-Want-bundleName?: string--><!--Device-Want-bundleName?: string-End-->

**System capability:** SystemCapability.Ability.AbilityBase

## deviceId

```TypeScript
deviceId?: string
```

device id

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [deviceId](arkts-ability-app-ability-want-want-c.md#deviceid)

<!--Device-Want-deviceId?: string--><!--Device-Want-deviceId?: string-End-->

**System capability:** SystemCapability.Ability.AbilityBase

## entities

```TypeScript
entities?: Array<string>
```

The description of a entities in a Want.

**Type:** Array&lt;string&gt;

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [entities](arkts-ability-app-ability-want-want-c.md#entities)

<!--Device-Want-entities?: Array<string>--><!--Device-Want-entities?: Array<string>-End-->

**System capability:** SystemCapability.Ability.AbilityBase

## flags

```TypeScript
flags?: number
```

The options of the flags in this Want.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [flags](arkts-ability-app-ability-want-want-c.md#flags)

<!--Device-Want-flags?: number--><!--Device-Want-flags?: number-End-->

**System capability:** SystemCapability.Ability.AbilityBase

## parameters

```TypeScript
parameters?: { [key: string]: any }
```

The description of the WantParams object in an Want

**Type:** { [key: string]: any }

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [parameters](arkts-ability-app-ability-want-want-c.md#parameters)

<!--Device-Want-parameters?: { [key: string]: any }--><!--Device-Want-parameters?: { [key: string]: any }-End-->

**System capability:** SystemCapability.Ability.AbilityBase

## type

```TypeScript
type?: string
```

The description of the type in this Want.

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [type](arkts-ability-app-ability-want-want-c.md#type)

<!--Device-Want-type?: string--><!--Device-Want-type?: string-End-->

**System capability:** SystemCapability.Ability.AbilityBase

## uri

```TypeScript
uri?: string
```

The description of a URI in a Want.

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [uri](arkts-ability-app-ability-want-want-c.md#uri)

<!--Device-Want-uri?: string--><!--Device-Want-uri?: string-End-->

**System capability:** SystemCapability.Ability.AbilityBase
