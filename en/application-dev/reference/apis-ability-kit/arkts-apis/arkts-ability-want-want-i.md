# Want

Want is a carrier for information transfer between objects (application components). Want can be used as a parameter of [startAbility](arkts-ability-uiabilitycontext-c.md#startability) to specify a startup target and information that needs to be carried during startup, for example, **bundleName** and **abilityName**, which respectively indicate the bundle name of the target ability and the ability name in the bundle. When ability A needs to start ability B and transfer some data to ability B, it can use Want a carrier to transfer the data.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [Want](arkts-ability-app-ability-want-want-c.md)

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

**System capability:** SystemCapability.Ability.AbilityBase
