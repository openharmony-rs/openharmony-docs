# RunningFormInfo

```TypeScript
interface RunningFormInfo
```

The class of a running form information.

@typedef RunningFormInfo

**Since:** 20

<!--Device-formInfo-interface RunningFormInfo--><!--Device-formInfo-interface RunningFormInfo-End-->

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## abilityName

```TypeScript
readonly abilityName: string
```

Obtains the class name of the ability to which this form belongs.

**Type:** string

**Default:** -

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-RunningFormInfo-readonly abilityName: string--><!--Device-RunningFormInfo-readonly abilityName: string-End-->

**System capability:** SystemCapability.Ability.Form

## bundleName

```TypeScript
readonly bundleName: string
```

Obtains the bundle name of the application to which this form belongs.

**Type:** string

**Default:** -

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-RunningFormInfo-readonly bundleName: string--><!--Device-RunningFormInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.Ability.Form

## dimension

```TypeScript
readonly dimension: number
```

Obtains the grid style of this form. The value must be a positive integer, refer to [FormDimension](arkts-form-forminfo-formdimension-e.md).

**Type:** number

**Default:** -

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-RunningFormInfo-readonly dimension: int--><!--Device-RunningFormInfo-readonly dimension: int-End-->

**System capability:** SystemCapability.Ability.Form

## formId

```TypeScript
readonly formId: string
```

Obtains the id of the this form.

**Type:** string

**Default:** -

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-RunningFormInfo-readonly formId: string--><!--Device-RunningFormInfo-readonly formId: string-End-->

**System capability:** SystemCapability.Ability.Form

## formLocation

```TypeScript
readonly formLocation: FormLocation
```

The location of this form.

**Type:** [FormLocation](arkts-form-forminfo-formlocation-e.md)

**Default:** -

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-RunningFormInfo-readonly formLocation: FormLocation--><!--Device-RunningFormInfo-readonly formLocation: FormLocation-End-->

**System capability:** SystemCapability.Ability.Form

## formName

```TypeScript
readonly formName: string
```

Obtains the name of this form.

**Type:** string

**Default:** -

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-RunningFormInfo-readonly formName: string--><!--Device-RunningFormInfo-readonly formName: string-End-->

**System capability:** SystemCapability.Ability.Form

## moduleName

```TypeScript
readonly moduleName: string
```

Obtains the name of the application module to which this form belongs.

**Type:** string

**Default:** -

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-RunningFormInfo-readonly moduleName: string--><!--Device-RunningFormInfo-readonly moduleName: string-End-->

**System capability:** SystemCapability.Ability.Form
