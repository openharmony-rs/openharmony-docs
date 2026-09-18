# FunInteractionParams (System API)

The fun interaction form params.

@typedef { FunInteractionParams }

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## abilityName

```TypeScript
abilityName?: string
```

The ability name of the fun interaction form.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## keepStateDuration

```TypeScript
keepStateDuration?: number
```

duration of the fun interaction form will be paused if not operate. Unit: milliseconds, The value must be an integer within [0,60000]. Default value: 10000.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## subBundleName

```TypeScript
subBundleName: string
```

The sub bundle name used by game engine.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## targetBundleName

```TypeScript
targetBundleName: string
```

The bundle name used by game engine.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.
