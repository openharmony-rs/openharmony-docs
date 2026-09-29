# ViewData

```TypeScript
export default interface ViewData
```

The module defines the view data used for auto-fill.

**Since:** 26.0.0

<!--Device-unnamed-export default interface ViewData--><!--Device-unnamed-export default interface ViewData-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## abilityName

```TypeScript
abilityName: string
```

Ability name, used to specify the Ability to which the auto-fill data belongs.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-ViewData-abilityName: string--><!--Device-ViewData-abilityName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## isOtherAccount

```TypeScript
isOtherAccount: boolean
```

Whether to display other account information saved in the password box for the user to select. **true** to display, **false** otherwise.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-ViewData-isOtherAccount: boolean--><!--Device-ViewData-isOtherAccount: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## isUserSelected

```TypeScript
isUserSelected: boolean
```

Whether the content to be filled is selected by the user. **true** if the content is selected by the user, and **false** otherwise.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-ViewData-isUserSelected: boolean--><!--Device-ViewData-isUserSelected: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## moduleName

```TypeScript
moduleName: string
```

Module name, used to specify the module to which the auto-fill data belongs.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-ViewData-moduleName: string--><!--Device-ViewData-moduleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.
