# DialogAbilityInfo (System API)

Provides DialogAbility information, including the bundle name, module name, and ability name.

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { dialogSession } from '@kit.AbilityKit';
```

## abilityIconId

```TypeScript
abilityIconId: number
```

ID of the ability icon.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## abilityLabelId

```TypeScript
abilityLabelId: number
```

ID of the ability label.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## abilityName

```TypeScript
abilityName: string
```

Ability name.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## appIndex

```TypeScript
appIndex: number
```

Index of the application clone.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## bundleIconId

```TypeScript
bundleIconId: number
```

ID of the bundle icon.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## bundleLabelId

```TypeScript
bundleLabelId: number
```

ID of the bundle label.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

Bundle name.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## codePath

```TypeScript
codePath?: string
```

Installation directory of the application.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## installSource

```TypeScript
installSource?: string
```

Installation source of the application. The options are as follows:

- **pre-installed**: pre-installed application installed during the first boot.  
- **ota**: pre-installed application added during system upgrade.  
- **recovery**: pre-installed application manually restored by the user after uninstallation.  
- **bundleName**: installation by the application corresponding to this bundle name. **bundleName** represents a  
variable, subject to the actual value.  
- **unknown**: unknown application installation source.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## moduleName

```TypeScript
moduleName: string
```

Module name.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## multiAppMode

```TypeScript
multiAppMode: MultiAppMode
```

Multi-app mode.

**Type:** [MultiAppMode](arkts-ability-applicationinfo-multiappmode-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## visible

```TypeScript
visible: boolean
```

Whether the ability is visible. **true** if visible, **false** otherwise.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
