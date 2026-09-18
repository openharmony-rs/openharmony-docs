# FormParam

Enumerates widget parameters.

**Since:** 9

**System capability:** SystemCapability.Ability.Form

## IDENTITY_KEY

```TypeScript
IDENTITY_KEY = "ohos.extra.param.key.form_identity"
```

Indicates the key specifying the ID of the form to be obtained, which is represented as want: {"parameters": {IDENTITY_KEY: "119476135"}}.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## DIMENSION_KEY

```TypeScript
DIMENSION_KEY = "ohos.extra.param.key.form_dimension"
```

Indicates the key specifying the grid style of the form to be obtained, which is represented as want: {"parameters": {DIMENSION_KEY: FormDimension.Dimension_1_2}}.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## NAME_KEY

```TypeScript
NAME_KEY = "ohos.extra.param.key.form_name"
```

Indicates the key specifying the name of the form to be obtained, which is represented as want: {"parameters": {NAME_KEY: "formName"}}.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## MODULE_NAME_KEY

```TypeScript
MODULE_NAME_KEY = "ohos.extra.param.key.module_name"
```

Indicates the key specifying the name of the module to which the form to be obtained belongs, which is represented as want: {"parameters": {MODULE_NAME_KEY: "formEntry"}}. This constant is mandatory.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## WIDTH_KEY

```TypeScript
WIDTH_KEY = "ohos.extra.param.key.form_width"
```

Indicates the key specifying the width of the form to be obtained, which is represented as want: {"parameters": {WIDTH_KEY: 800}}.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## HEIGHT_KEY

```TypeScript
HEIGHT_KEY = "ohos.extra.param.key.form_height"
```

Indicates the key specifying the height of the form to be obtained, which is represented as want: {"parameters": {HEIGHT_KEY: 400}}.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## TEMPORARY_KEY

```TypeScript
TEMPORARY_KEY = "ohos.extra.param.key.form_temporary"
```

Indicates the key specifying whether a form is temporary, which is represented as want: {"parameters": {TEMPORARY_KEY: true}}.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## BUNDLE_NAME_KEY

```TypeScript
BUNDLE_NAME_KEY = "ohos.extra.param.key.bundle_name"
```

Indicates the key specifying the name of the bundle to be obtained, which is represented as want: {"parameters": {BUNDLE_NAME_KEY: "bundleName"}}.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## ABILITY_NAME_KEY

```TypeScript
ABILITY_NAME_KEY = "ohos.extra.param.key.ability_name"
```

Indicates the key specifying the name of the ability to be obtained, which is represented as want: {"parameters": {ABILITY_NAME_KEY: "abilityName"}}.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## LAUNCH_REASON_KEY

```TypeScript
LAUNCH_REASON_KEY = "ohos.extra.param.key.form_launch_reason"
```

Indicates the key specifying the launch reason of the form to be obtained, which is represented as want: {"parameters": {LAUNCH_REASON_KEY: LaunchReason.FORM_DEFAULT}}.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## PARAM_FORM_CUSTOMIZE_KEY

```TypeScript
PARAM_FORM_CUSTOMIZE_KEY = "ohos.extra.param.key.form_customize"
```

Indicates the key specifying the custom data of the form to be obtained, which is represented as want: {"parameters": {PARAM_FORM_CUSTOMIZE_KEY: {"key": "userData"}}}.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.Form

## FORM_LOCATION_KEY

```TypeScript
FORM_LOCATION_KEY = 'ohos.extra.param.key.form_location'
```

Indicates the key specifying the form location, which is represented as want: {"parameters": {FORM_LOCATION_KEY: FormLocation.DESKTOP}}.

**Since:** 12

**System capability:** SystemCapability.Ability.Form

## FORM_RENDERING_MODE_KEY

```TypeScript
FORM_RENDERING_MODE_KEY = 'ohos.extra.param.key.form_rendering_mode'
```

Indicates the key specifying the form rendering mode, which is represented as want: {"parameters": {FORM_RENDERING_MODE_KEY: FormRenderingMode.SINGLE_COLOR}}.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.Form

## HOST_BG_INVERSE_COLOR_KEY

```TypeScript
HOST_BG_INVERSE_COLOR_KEY = 'ohos.extra.param.key.host_bg_inverse_color'
```

Indicates the key specifying the inverse of the host background color, which is represented as want: {"parameters": {HOST_BG_INVERSE_COLOR_KEY: "#FF000000"}}.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.Form

## FORM_PERMISSION_NAME_KEY

```TypeScript
FORM_PERMISSION_NAME_KEY = 'ohos.extra.param.key.permission_name'
```

Indicates the key specifying the user granted permission name, which is represented as want: {"parameters": {FORM_PERMISSION_NAME_KEY: "permissionName"}}.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.Form

## FORM_PERMISSION_GRANTED_KEY

```TypeScript
FORM_PERMISSION_GRANTED_KEY = 'ohos.extra.param.key.permission_granted'
```

Indicates the key specifying whether the user granted, which is represented as want: {"parameters": {FORM_PERMISSION_GRANTED_KEY: true}}.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.Form

## ORIGINAL_FORM_KEY

```TypeScript
ORIGINAL_FORM_KEY = 'ohos.extra.param.key.original_form_id'
```

Indicates the key specifying the original form id, used in conjunction with LaunchReason.FORM_SIZE_CHANGE. which is represented as want: {"parameters": {ORIGINAL_FORM_KEY: "119476135"}}.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.Form

## EDIT_FORM_KEY

```TypeScript
EDIT_FORM_KEY = 'ohos.extra.param.key.edit_form_id'
```

Indicates the key specifying the edit form id, used in conjunction with LaunchReason.FORM_EDIT_PREVIEW. which is represented as want: {"parameters": {EDIT_FORM_KEY: "119476135"}}.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Ability.Form

## UPDATE_FORM_REASON_KEY

```TypeScript
UPDATE_FORM_REASON_KEY = 'ohos.extra.param.key.update_form_reason'
```

Indicates the key specifying the reason for the form update. which is represented as want: {"parameters": {UPDATE_FORM_REASON_KEY: FormUpdateReason.FORM_NODE_REUSE}}.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.Form
