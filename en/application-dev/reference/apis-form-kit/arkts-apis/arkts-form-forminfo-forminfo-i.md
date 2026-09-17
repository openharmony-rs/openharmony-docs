# FormInfo

Provides information about a form.

@typedef FormInfo

**Since:** 9

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

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## bundleName

```TypeScript
bundleName: string
```

Obtains the bundle name of the application to which this form belongs.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.Ability.Form

## customizeData

```TypeScript
customizeData: Record<string, string>
```

Obtains the custom data defined in this form.

**Type:** Record&lt;string, string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## defaultDimension

```TypeScript
defaultDimension: number
```

Obtains the default grid style of this form. The value must be a positive integer, refer to [FormDimension](arkts-form-forminfo-formdimension-e.md).

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## description

```TypeScript
description: string
```

Obtains the description of this form.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## descriptionId

```TypeScript
descriptionId: number
```

Obtains the description id of this form. The value must be a positive integer.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## displayName

```TypeScript
displayName: string
```

Obtains the display name of this form.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## displayNameId

```TypeScript
displayNameId: number
```

Obtains the displayName resource id of this form. The value must be a positive integer.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## formConfigAbility

```TypeScript
formConfigAbility: string
```

Obtains the form config ability about this form.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## formVisibleNotify

```TypeScript
formVisibleNotify: boolean
```

Obtains whether notify visible of this form.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## isDefault

```TypeScript
isDefault: boolean
```

Checks whether this form is a default form.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## isDynamic

```TypeScript
isDynamic: boolean
```

Obtains whether this form is a dynamic form.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## jsComponentName

```TypeScript
jsComponentName: string
```

Obtains the JS component name of this JS form.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## moduleName

```TypeScript
moduleName: string
```

Obtains the name of the application module to which this form belongs.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## name

```TypeScript
name: string
```

Obtains the name of this form.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## scheduledUpdateTime

```TypeScript
scheduledUpdateTime: string
```

Obtains the scheduledUpdateTime.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## supportDimensions

```TypeScript
supportDimensions: Array<number>
```

Obtains the grid styles supported by this form. The minimum length is 1, refer to [FormDimension](arkts-form-forminfo-formdimension-e.md).

**Type:** Array&lt;number&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## supportedShapes

```TypeScript
supportedShapes: Array<number>
```

Obtains the shape supported by this form. The minimum length is 1, refer to [FormShape](arkts-form-forminfo-formshape-e.md).

**Type:** Array&lt;number&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.Form

## transparencyEnabled

```TypeScript
transparencyEnabled: boolean
```

Indicates whether the form can be set as a transparent background

**Type:** boolean

**Default:** false

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## type

```TypeScript
type: FormType
```

Obtains the type of this form. Currently, JS forms are supported.

**Type:** [FormType](arkts-form-forminfo-formtype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## updateDuration

```TypeScript
updateDuration: number
```

Obtains the updateDuration. The value must be an integer within [0,336].

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## updateEnabled

```TypeScript
updateEnabled: boolean
```

Obtains the updateEnabled.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form
