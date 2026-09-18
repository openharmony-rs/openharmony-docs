# FormInfo

Provides information about a form.

@typedef FormInfo

**Since:** 9

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## enableBlurBackground

```TypeScript
readonly enableBlurBackground?: boolean
```

Indicates whether the form uses a blur background provided by the form host.

**Type:** boolean

**Since:** 18

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## funInteractionParams

```TypeScript
readonly funInteractionParams?: FunInteractionParams
```

Indicates the fun interaction form params

**Type:** [FunInteractionParams](arkts-form-forminfo-funinteractionparams-i-sys.md)

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## groupId

```TypeScript
readonly groupId?: string
```

Obtains the group id of the form.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## isFontScaleFollowSystem

```TypeScript
isFontScaleFollowSystem?: boolean
```

Obtains whether the font scaling factor follows system settings. <br>Default value:The default value is true.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## isPrivacySensitive

```TypeScript
readonly isPrivacySensitive?: boolean
```

Obtains whether the form is privacy sensitive.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## isStandbyAdapted

```TypeScript
readonly isStandbyAdapted?: boolean
```

Obtains whether the form is adapted for standby.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## isStandbySupported

```TypeScript
readonly isStandbySupported?: boolean
```

Obtains whether the form supports standby.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## isTemplateForm

```TypeScript
readonly isTemplateForm?: boolean
```

Obtains whether the form is template form.

**Type:** boolean

**Since:** 23

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## previewImages

```TypeScript
readonly previewImages?: Array<number>
```

Indicates the form previewImage IDs map corresponds to the \"supportDimensions\". The maximum length is +∞, positive integer.

**Type:** Array&lt;number&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## renderingMode

```TypeScript
readonly renderingMode?: RenderingMode
```

Obtains the rendering mode of the form.

**Type:** [RenderingMode](arkts-form-forminfo-renderingmode-e-sys.md)

**Since:** 18

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## resizable

```TypeScript
readonly resizable?: boolean
```

Obtains the resizable of the form.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## sceneAnimationParams

```TypeScript
readonly sceneAnimationParams?: SceneAnimationParams
```

Indicates the scene animation form params

**Type:** [SceneAnimationParams](arkts-form-forminfo-sceneanimationparams-i-sys.md)

**Since:** 20

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.
