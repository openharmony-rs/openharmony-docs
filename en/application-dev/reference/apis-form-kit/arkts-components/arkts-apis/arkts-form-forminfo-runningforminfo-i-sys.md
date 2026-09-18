# RunningFormInfo

The class of a running form information.

@typedef RunningFormInfo

**Since:** 20

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## extraData

```TypeScript
readonly extraData?: Record<string, Object>
```

Obtains the extra data of the this form.

**Type:** Record&lt;string, Object&gt;

**Default:** -

**Since:** 12

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## formDescription

```TypeScript
readonly formDescription: string
```

Obtains the description of this form.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## formUsageState

```TypeScript
readonly formUsageState: FormUsageState
```

Obtains the stage of form use.

**Type:** [FormUsageState](arkts-form-forminfo-formusagestate-e-sys.md)

**Default:** FormUsageState.USED

**Since:** 11

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## hostBundleName

```TypeScript
readonly hostBundleName: string
```

Obtains the bundle name of the form host application.

**Type:** string

**Default:** -

**Since:** 10

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## visibilityType

```TypeScript
readonly visibilityType: VisibilityType
```

Obtains the visibility of this form.

**Type:** [VisibilityType](arkts-form-forminfo-visibilitytype-e.md)

**Default:** -

**Since:** 10

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.
