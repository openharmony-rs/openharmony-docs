# FormInfo

```TypeScript
interface FormInfo
```

Provides information about a form.

@typedef FormInfo

**Since:** 9

<!--Device-formInfo-interface FormInfo--><!--Device-formInfo-interface FormInfo-End-->

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## abilityName

```TypeScript
abilityName: string
```

Obtains the class name of the ability to which this form belongs.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-abilityName: string--><!--Device-FormInfo-abilityName: string-End-->

**System capability:** SystemCapability.Ability.Form

## bundleName

```TypeScript
bundleName: string
```

Obtains the bundle name of the application to which this form belongs.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-bundleName: string--><!--Device-FormInfo-bundleName: string-End-->

**System capability:** SystemCapability.Ability.Form

## customizeData

```TypeScript
customizeData: Record<string, string>
```

Obtains the custom data defined in this form.

**Type:** Record&lt;string, string&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-customizeData: Record<string, string>--><!--Device-FormInfo-customizeData: Record<string, string>-End-->

**System capability:** SystemCapability.Ability.Form

## defaultDimension

```TypeScript
defaultDimension: number
```

Obtains the default grid style of this form. The value must be a positive integer, refer to [FormDimension](arkts-form-forminfo-formdimension-e.md).

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-defaultDimension: int--><!--Device-FormInfo-defaultDimension: int-End-->

**System capability:** SystemCapability.Ability.Form

## description

```TypeScript
description: string
```

Obtains the description of this form.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-description: string--><!--Device-FormInfo-description: string-End-->

**System capability:** SystemCapability.Ability.Form

## descriptionId

```TypeScript
descriptionId: number
```

Obtains the description id of this form. The value must be a positive integer.

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-descriptionId: int--><!--Device-FormInfo-descriptionId: int-End-->

**System capability:** SystemCapability.Ability.Form

## displayName

```TypeScript
displayName: string
```

Obtains the display name of this form.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-displayName: string--><!--Device-FormInfo-displayName: string-End-->

**System capability:** SystemCapability.Ability.Form

## displayNameId

```TypeScript
displayNameId: number
```

Obtains the displayName resource id of this form. The value must be a positive integer.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-displayNameId: int--><!--Device-FormInfo-displayNameId: int-End-->

**System capability:** SystemCapability.Ability.Form

## formConfigAbility

```TypeScript
formConfigAbility: string
```

Obtains the form config ability about this form.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-formConfigAbility: string--><!--Device-FormInfo-formConfigAbility: string-End-->

**System capability:** SystemCapability.Ability.Form

## formVisibleNotify

```TypeScript
formVisibleNotify: boolean
```

Obtains whether notify visible of this form.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-formVisibleNotify: boolean--><!--Device-FormInfo-formVisibleNotify: boolean-End-->

**System capability:** SystemCapability.Ability.Form

## isDefault

```TypeScript
isDefault: boolean
```

Checks whether this form is a default form.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-isDefault: boolean--><!--Device-FormInfo-isDefault: boolean-End-->

**System capability:** SystemCapability.Ability.Form

## isDynamic

```TypeScript
isDynamic: boolean
```

Obtains whether this form is a dynamic form.

**Type:** boolean

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-isDynamic: boolean--><!--Device-FormInfo-isDynamic: boolean-End-->

**System capability:** SystemCapability.Ability.Form

## jsComponentName

```TypeScript
jsComponentName: string
```

Obtains the JS component name of this JS form.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-jsComponentName: string--><!--Device-FormInfo-jsComponentName: string-End-->

**System capability:** SystemCapability.Ability.Form

## moduleName

```TypeScript
moduleName: string
```

Obtains the name of the application module to which this form belongs.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-moduleName: string--><!--Device-FormInfo-moduleName: string-End-->

**System capability:** SystemCapability.Ability.Form

## name

```TypeScript
name: string
```

Obtains the name of this form.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-name: string--><!--Device-FormInfo-name: string-End-->

**System capability:** SystemCapability.Ability.Form

## scheduledUpdateTime

```TypeScript
scheduledUpdateTime: string
```

Obtains the scheduledUpdateTime.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-scheduledUpdateTime: string--><!--Device-FormInfo-scheduledUpdateTime: string-End-->

**System capability:** SystemCapability.Ability.Form

## supportDimensions

```TypeScript
supportDimensions: Array<number>
```

Obtains the grid styles supported by this form. The minimum length is 1, refer to [FormDimension](arkts-form-forminfo-formdimension-e.md).

**Type:** Array&lt;number&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-supportDimensions: Array<int>--><!--Device-FormInfo-supportDimensions: Array<int>-End-->

**System capability:** SystemCapability.Ability.Form

## supportedShapes

```TypeScript
supportedShapes: Array<number>
```

Obtains the shape supported by this form. The minimum length is 1, refer to [FormShape](arkts-form-forminfo-formshape-e.md).

**Type:** Array&lt;number&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-FormInfo-supportedShapes: Array<int>--><!--Device-FormInfo-supportedShapes: Array<int>-End-->

**System capability:** SystemCapability.Ability.Form

## transparencyEnabled

```TypeScript
transparencyEnabled: boolean
```

Indicates whether the form can be set as a transparent background

**Type:** boolean

**Default:** false

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-transparencyEnabled: boolean--><!--Device-FormInfo-transparencyEnabled: boolean-End-->

**System capability:** SystemCapability.Ability.Form

## type

```TypeScript
type: FormType
```

Obtains the type of this form. Currently, JS forms are supported.

**Type:** [FormType](arkts-form-forminfo-formtype-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-type: FormType--><!--Device-FormInfo-type: FormType-End-->

**System capability:** SystemCapability.Ability.Form

## updateDuration

```TypeScript
updateDuration: number
```

Obtains the updateDuration. The value must be an integer within [0,336].

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-updateDuration: int--><!--Device-FormInfo-updateDuration: int-End-->

**System capability:** SystemCapability.Ability.Form

## updateEnabled

```TypeScript
updateEnabled: boolean
```

Obtains the updateEnabled.

**Type:** boolean

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormInfo-updateEnabled: boolean--><!--Device-FormInfo-updateEnabled: boolean-End-->

**System capability:** SystemCapability.Ability.Form

## colorMode

```TypeScript
colorMode: ColorMode
```

Obtains the color mode of this form.

**Type:** [ColorMode](arkts-form-forminfo-colormode-e.md)

**Since:** 9

**Deprecated since:** 20

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FormInfo-colorMode: ColorMode--><!--Device-FormInfo-colorMode: ColorMode-End-->

**System capability:** SystemCapability.Ability.Form
