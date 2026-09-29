# AutoStartupInfo (System API)

```TypeScript
export interface AutoStartupInfo
```

The module defines information about the application component that automatically starts upon system boot.

**Since:** 11

<!--Device-unnamed-export interface AutoStartupInfo--><!--Device-unnamed-export interface AutoStartupInfo-End-->

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

<!--Device-AutoStartupInfo-abilityName: string--><!--Device-AutoStartupInfo-abilityName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## abilityTypeName

```TypeScript
abilityTypeName?: string
```

Ability type.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutoStartupInfo-abilityTypeName?: string--><!--Device-AutoStartupInfo-abilityTypeName?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## appCloneIndex

```TypeScript
appCloneIndex?: number
```

Index of an application clone.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutoStartupInfo-appCloneIndex?: int--><!--Device-AutoStartupInfo-appCloneIndex?: int-End-->

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

<!--Device-AutoStartupInfo-bundleName: string--><!--Device-AutoStartupInfo-bundleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## canUserModify

```TypeScript
readonly canUserModify?: boolean
```

Whether the developer is allowed to modify the auto-startup status of this application. The options include **true** (yes) and **false** (no).

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutoStartupInfo-readonly canUserModify?: boolean--><!--Device-AutoStartupInfo-readonly canUserModify?: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## moduleName

```TypeScript
moduleName?: string
```

Module name.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutoStartupInfo-moduleName?: string--><!--Device-AutoStartupInfo-moduleName?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## setterUserId

```TypeScript
readonly setterUserId?: number
```

User ID of the person who set the application to automatically start upon system boot.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutoStartupInfo-readonly setterUserId?: int--><!--Device-AutoStartupInfo-readonly setterUserId?: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## userId

```TypeScript
readonly userId?: number
```

User ID associated with the application, used to differentiate applications belonging to different user accounts on the same device.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-AutoStartupInfo-readonly userId?: int--><!--Device-AutoStartupInfo-readonly userId?: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
